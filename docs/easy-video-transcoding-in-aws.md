# AWS 中的轻松视频转码

> 原文：<https://acloudguru.com/blog/engineering/easy-video-transcoding-in-aws>

自然，我们尝试了各种工作，以获得对弹性代码转换器的良好感觉，但我们的最终目标是完全自动化。

弹性转码器是一种媒体服务，旨在提供一种高度可扩展、易于使用且经济高效的方式，将媒体文件从其源格式转换(或“转码”)为可在智能手机、平板电脑和 PC 等设备上播放的版本。想了解更多关于转码的知识吗？查看我们的实践实验室，了解如何使用 S3 和 Elastic Transcode 对视频进行转码，并获得更多知识和经验。

### 输入λ

在无服务器方法中，运行定制代码的一种方式是使用 AWS Lambda。目前，无法通过将文件上传到存储桶来自动运行弹性代码转换器作业。然而，从 S3 事件调用 Lambda 和从 Lambda 函数调用弹性代码转换器更容易。

![The whole process: S3 invokes Lambda and Lambda invokes Elastic Transcoder. ](img/6f70f28ac4bf7a4548c712d2ae6f00de.png)

This is the whole process: S3 invokes Lambda and Lambda invokes Elastic Transcoder

从 S3 存储桶中调用 Lambda 函数非常简单——在 S3 打开所需的存储桶，然后单击*属性*。从那里点击*事件*、*λ*，并从下拉菜单中选择您想要执行的相关λ功能。最后，选择将触发流程的事件( *ObjectCreated (All))* 。

### 深入研究 lambda

之前我提到过，您可以使用弹性转码器控制台创建和执行作业。这很好，但我们也需要能够从我们的 Lambda 函数创建和运行弹性代码转换器作业。谢天谢地，使用 AWS JavaScript SDK 很容易做到这一点。以下是您将经历的主要步骤:

1.  创建一个基本的 Lambda 函数，并向其中添加 AWS SDK。
2.  从传递给*处理程序*函数的*事件*对象中提取上传文件的桶和文件名。
3.  创建作业并指定所需的输出以及任何其他设置。
4.  开始工作，享受在弹性转码器控制台中看到的进展。如果你注册了一个 SNS 主题(当你创建了弹性转码器管道时)并配置了你的电子邮件，你将会收到工作各个阶段的通知。

![Monitor your jobs from the Elastic Transcoder console.](img/095a4ccc67826d6228d8c7e5dc2d2d70.png)

Monitor your jobs from the Elastic Transcoder console

下面给出了一个满足我们要求的 Lambda 函数示例。请注意，它创建了一个具有 3 个输出的作业— generic 720p、webm 和 hlsv3。

```
‘use strict’;
var AWS = require(‘aws-sdk’);
var s3 = new AWS.S3({
 apiVersion: ‘2012–09–25’
});
var eltr = new AWS.ElasticTranscoder({
 apiVersion: ‘2012–09–25’,
 region: ‘us-east-1’
});
exports.handler = function(event, context) {
 console.log(‘Executing Elastic Transcoder Orchestrator’);
 var bucket = event.Records[0].s3.bucket.name;
 var key = event.Records[0].s3.object.key;
 var pipelineId = ‘112321321343–2abcc1’;
 if (bucket !== ‘acloud-video-input’) {
  context.fail(‘Incorrect Video Input Bucket’);
  return;
 }
 var srcKey =  decodeURIComponent(event.Records[0].s3.object.key.replace(/\+/g, " ")); //the object may have spaces  
 var newKey = key.split('.')[0];
 var params = {
  PipelineId: pipelineId,
  OutputKeyPrefix: newKey + ‘/’,
  Input: {
   Key: srcKey,
   FrameRate: ‘auto’,
   Resolution: ‘auto’,
   AspectRatio: ‘auto’,
   Interlaced: ‘auto’,
   Container: ‘auto’
  },
  Outputs: [{
   Key: ‘mp4-’ + newKey + ‘.mp4’,
   ThumbnailPattern: ‘thumbs-’ + newKey + ‘-{count}’,
   PresetId: ‘1351620000001–000010’, //Generic 720p
   Watermarks: [{
    InputKey: ‘watermarks/logo-horiz-large.png’,
    PresetWatermarkId: ‘BottomRight’
   }],
  },{
   Key: ‘webm-’ + newKey + ‘.webm’,
   ThumbnailPattern: ‘’,
   PresetId: ‘1351620000001–100240’, //Webm 720p
   Watermarks: [{
    InputKey: ‘watermarks/logo-horiz-large.png’,
    PresetWatermarkId: ‘BottomRight’
   }],
  },{
   Key: ‘hls-’ + newKey + ‘.ts’,
   ThumbnailPattern: ‘’,
   PresetId: ‘1351620000001–200010’, //HLS v3 2mb/s
   Watermarks: [{
    InputKey: ‘watermarks/logo-horiz-large.png’,
    PresetWatermarkId: ‘BottomRight’
   }],
  }]
 };
 console.log(‘Starting Job’);
 eltr.createJob(params, function(err, data){
  if (err){
   console.log(err);
  } else {
   console.log(data);
  }
  context.succeed(‘Job well done’);
 });
};
```

### 事先调整

在上面的 Lambda 函数中，你可能会注意到一个细节，那就是预设的使用(例如 13516200000001–000010)。预设描述如何编码给定的文件。可用预设的完整列表可在 [AWS 文档](http://docs.aws.amazon.com/elastictranscoder/latest/developerguide/system-presets.html)中找到。

也可以创建自己的预设。你可以通过点击弹性转码器控制台中的*预设*链接来实现。您将在那里看到系统预置的完整列表，并且您可以通过点击*创建新预置*按钮来创建自己的预置。

预设允许对文件编码方式进行大量的精细控制。自然，您可以在适当的 [AWS 文档](http://docs.aws.amazon.com/elastictranscoder/latest/developerguide/preset-settings.html)中找到很多细节。

### 后续步骤

弹性代码转换器还能做更多我们还没有触及的事情。字幕和数字版权管理立即浮现在脑海中，两者对平台都非常重要。A Cloud Guru 团队对无服务器媒体编码和服务系统有很大的计划，所以请关注这个领域。

你用过弹性转码器吗，印象如何？我很想听听你的经历，以及你对[平台](https://acloud.guru/)的看法。

* * *

## 获得更好职业所需的技能。

掌握现代技术技能，获得认证，提升您的职业生涯。无论您是新手还是经验丰富的专业人士，您都可以通过实践来学习，并在 ACG 的帮助下推进您的云计算职业生涯。

* * *

## 云专家

云专家的使命是通过提供世界领先的教育内容，让个人参与到提升云计算技能的旅程中来，这些教育内容旨在促进思维模式和职业发展。

> “不要让世界上的任何人生活在错觉中。没有上师，谁也不能渡到彼岸。”——古鲁·那纳克

我们的[课程](https://acloudguru.com/browse-training)由对云计算有着共同热情的行业专家讲授。我们努力为我们日益壮大的云专家社区服务，他们在我们的[论坛](https://acloud.guru/forums/home)、研讨会、见面会和[会议](https://acloud.guru/serverless)上慷慨地贡献他们的见解。

*跟上一个云宗师剧组* [*@acloudguru*](https://twitter.com/acloudguru)