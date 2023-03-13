# 以同样的方式裁剪多个图像(简短教程)

> 原文：<https://acloudguru.com/blog/engineering/cropping-multiple-images-the-same-way-short-tutorial>

有时，您会希望从多个图像中裁剪出相同的区域(想象一下从一堆截图中截取同一个窗口的内容)。当然，你可以启动你最喜欢的图片编辑器，一遍又一遍地选择和裁剪，但是，像往常一样，还有一个更好的方法。这个简短的教程描述了一种有效的方法来处理理论上无限数量的图像。难度: ***基本–中等*** ***注意:我强烈建议在弄乱这些图像之前，先把它们备份一下。本教程中的一些操作将覆盖图像文件，因此如果您犯了一个错误，您可能会丢失宝贵的数据。本教程假设了基本的 Linux 知识，比如启动程序、打开终端和使用终端。我们将使用的工具是 [<acronym title="GNU Image Manipulation Program">GIMP</acronym>](https://www.gimp.org/) 和 [mogrify](https://www.imagemagick.org/script/mogrify.php "Go") (来自 [ImageMagick](https://www.imagemagick.org/ "Go") 套件)，所以请确保您已经安装了它们。我们将使用 GIMP 来图形化地选择要裁剪的区域，并使用 mogrify 工具来自动化裁剪，这样可以节省我们很多工作。让我们从选择开始:***

现在我们开始在候机楼工作。打开你最喜欢的一个和 cd 到图像所在的目录。请注意，我强烈建议只让*在目录中裁剪*图像，别无其他。这给你省了很多麻烦。那么，让我们从 mogrify 命令开始。裁剪的语法如下:

> [rechosen @ localhost ~]$ mogrify-crop { Width } X { Height }+{ X }+{ Y } image.png

现在不要害怕，{Width}、{Height}等等只是你应该把从 GIMP 得到的值放在那里的地方！请注意，我使用 png 文件作为例子，而 mogrify 能够处理超过 100 种图像文件类型。你不必使用 png 文件。无论如何，如果我填写截图中的值，mogrify 命令将如下所示:

> [rechosen @ localhost ~]$ mogrify-crop 643×393+7+83 image.png

这个系统背后的逻辑如下:裁剪一个 643×393 像素的区域，从图像左边的 7 个像素和顶部的 83 个像素开始。明白了吗？那好吧。上面的命令会用一个裁剪过的版本覆盖 image.png。但是这仍然只能处理一张图片。让 mogrify 修改所有图像的最简单方法就是这样:

> [rechosen @ localhost ~]$ mogrify-crop 643×393+7+83 *。png

星号让 bash 填充当前目录下的所有 png 文件，mogrify 会愉快地全部处理。经过一段时间(希望很短)的等待后，所有的图像都会被裁剪掉。如果您想要裁剪其他格式的图像，只需更改“*”。png "到，例如，" *。jpg "或" *。gif”。您可能想要为裁剪后的图像指定其他名称，这样原始图像就不会被覆盖，并且可以清楚地看到哪些图像已被裁剪，哪些图像未被裁剪。这更复杂，但是，嘿，我们正在开发 Linux！如果你花时间去写，一切皆有可能。

为了给裁剪后的图像起其他名字，我们将使用 bash 循环。这一次，我们将使用[转换](https://www.imagemagick.org/script/convert.php "Go")实用程序。它和 mogrify 来自同一个家族，但是它让我们更容易输出到另一个文件名。我不会解释整个循环，因为大部分都是 bash 知识，但是我会告诉你哪些事情你可以/应该改变以获得正确的结果。有两种情况下的循环，只需选择你最喜欢的文件命名方式。

*   **Case 1:** You want the output files to be named like this: originalfile.png => cropped_originalfile.png (again, you can insert any of the over 100 supported image formats here, I just like png). The loop should be like this:

    > [re chosen @ localhost ~]$ for file in *。pngdo convert-crop { Width } X { Height }+{ X }+{ Y } $ file cropped _ $ file；完成的

    你应该把“png”替换成你想要的扩展名(想想 jpg、gif、png(当然)等等)，把“{Width}”、“{Height}”等等替换成你从 GIMP 得到的值。您也可以将“cropped_”替换为您喜欢的任何前缀。

*   **Case 2:** You want the output files to be named like this: originalfile.png => originalfile_cropped.png (or originalfile.jpg => originalfile_cropped.jpg, you name it). In that case, you should use the following loop:

    > [re chosen @ localhost ~]$ for file in *。pngdo convert-crop { Width } X { Height }+{ X }+{ Y } $ file $ { file %。png } _ cropped.png 完成的

    再次，用你想要的扩展名替换“png”(注意，有它的 ***3*** 实例)，用你从 GIMP 得到的值替换“{Width}”、“{Height}”等。您也可以用您喜欢的任何后缀替换“_cropped”。请注意，在这种情况下，您可以轻松地修改输出格式:如果您想以 jpg 格式输出裁剪后的图像，您只需将第三个“png”实例替换为“jpg ”,无论您的输入文件是什么格式。转换实用程序将检测到它并自动更改图像格式。

好了，希望这个小教程对你有帮助。如果你想在这些事情上得到更多的帮助，欢迎发表评论。感谢阅读，上帝保佑！