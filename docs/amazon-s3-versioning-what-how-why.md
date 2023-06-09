# 亚马逊 S3 版本控制:什么，如何，为什么

> 原文：<https://acloudguru.com/blog/engineering/amazon-s3-versioning-what-how-why>

使用亚马逊 S3 时，如何保护重要的资产和数据？一个叫做版本控制的特性很好地回答了这个问题。默认情况下，当您将对象上传到 S3 时，该对象会被冗余存储，以提供 99.999999999%的持久性。这意味着，对于存储在 S3 上的 10，000 个物体，平均每 10，000，000 年就会丢失一个物体。这些都是很好的机会，那么我们为什么还要回答这个问题呢？因为尽管支持 S3 的底层基础设施提供了很高的耐用性，但它不能保护您不覆盖您的对象，甚至不能删除这些对象。是吗？默认情况下不会，但如果我们启用版本控制，它就会。

## 什么是版本控制？

版本控制会自动跟上同一对象的不同版本。例如，假设您有一个对象(object1)当前存储在一个存储桶中。使用默认设置时，如果您将 object1 的新版本上传到该存储桶，object1 将被新版本替换。然后，如果你意识到你搞砸了，想要回以前的版本，那你就倒霉了，除非你在本地计算机上有备份。启用版本控制后，旧版本仍然存储在您的 bucket 中，它有一个惟一的版本 ID，因此您仍然可以看到它、下载它或者在您的应用程序中使用它。![blog-post-image-versioning@1x](img/15569a5d4c93bc7325e572efd83ea97a.png)

## 如何启用版本控制？

当我们设置版本控制时，我们是在存储桶级别进行的。因此，我们不是为单个对象启用它，而是在一个存储桶中打开它，该存储桶中的所有对象从该点开始自动使用版本控制。我们可以从 AWS 控制台，或者从 SDK 和 API 调用在存储桶级别启用版本控制。一旦我们启用了版本控制，任何上传到该存储桶的新对象都会收到一个版本 ID。这个 ID 用来唯一地标识那个版本，并且它是我们可以用来在任何时间点检索那个对象的东西。如果在启用版本控制之前，我们已经在这个桶中有了对象，那么这些对象的版本 ID 将简单地为“null”![S3 bucket with versioning enabled](img/3f3c7e9756a7b0dfc53abf1d887686da.png)删除一个对象怎么办？当我们在版本控制中这样做时会发生什么？如果我们尝试删除该对象，所有版本都将保留在桶中，但是 S3 将在该对象的最新版本处插入一个删除标记。这意味着如果我们试图检索对象，我们将得到一个 404 Not Found 错误。然而，我们仍然可以通过指定它们的 id 来检索以前的版本，所以它们不会完全丢失。如果我们愿意，我们可以通过指定版本 ID 来删除特定的版本。如果我们对最新版本(默认版本)这样做，那么 S3 会自动将下一个版本设置为默认版本，而不是给我们一个 404 错误。这只是恢复对象以前版本的一个选项。假设您将一个已经存在的对象上传(即放置)到 S3。该新版本将成为默认版本。然后说你想把之前的版本设为默认。您可以删除最新版本的特定版本 ID(因为，请记住，这不会给我们一个 404，而删除对象本身会)。或者，您也可以将想要的版本复制回同一个存储桶。复制对象会执行 GET 请求，然后是 PUT 请求。每当您在启用了版本控制的 S3 存储桶中有一个 PUT 请求时，它都会触发该对象成为最新版本，因为它为其提供了一个新的版本 ID。这就是我们通过启用版本控制可以获得的一些好处。我们可以保护我们的数据不被删除，也不被意外覆盖。我们也可以用它来为我们自己的记录保存不同版本的日志。

## 还有什么？

在启用版本控制之前，您应该知道一些事情。首先，一旦启用了版本控制，就不能完全禁用它。但是，您可以将存储桶置于“版本控制暂停”状态。如果这样做，那么新对象将收到 null 版本 id。已经有版本的其他对象将继续拥有这些版本。其次，因为您存储同一对象的多个版本，您的账单可能会增加。这些版本占用空间，S3 目前每 GB 收取一定的费用。有一种方法有助于抵消这一点。这是另一个叫做生命周期管理的特性。生命周期管理让您决定在一定时间后版本会发生什么。例如，如果您正在存储重要的日志，并且这些日志有多个版本，这取决于这些日志中存储了多少数据，这可能会占用大量空间。您可以将日志保存到某个日期，然后将它们转移到 Amazon Glacier，而不是存储所有这些版本(其中一些版本可能已有数月之久)。亚马逊冰川便宜得多，但限制了你访问数据的速度，所以它最适合用于你可能不会实际使用，但仍然需要存储的数据，以防你有一天需要它。通过实施这种政策，如果你有很多对象，你可以真正地削减成本。此外，同一对象的不同版本可以有不同的属性。例如，通过指定一个版本 ID，我们可以使互联网上的任何人都可以公开访问该版本，但是其他版本仍然是私有的。现在，如果你对 S3 版本有任何疑问，欢迎在评论中提问。如果你想玩玩亚马逊 S3 版本管理，并且你是其中的一员，那就来看看这个动手实验室吧。这对你来说没有额外的成本，你也不必担心弄乱任何东西，因为实验室总是可以清理和重新启动。如果你有兴趣了解更多关于 S3 的知识，比如如何优化性能，如何使用桶策略，如何加密数据，等等，请查看 [AWS 认证开发者课程](https://linuxacademy.com/cp/modules/view/id/11)。如果你现在不是会员呢？我很乐意[邀请你](https://linuxacademy.com/join/pricing)去 Linux 学院！