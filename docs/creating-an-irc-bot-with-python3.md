# 用 Python 3 |云专家创建一个 IRC 机器人

> 原文：<https://acloudguru.com/blog/engineering/creating-an-irc-bot-with-python3>

我们之前已经在博客上发表过一些关于 IRC 的文章，也讨论过 Freenode IRC 网络上的#LinuxAcademy 频道。我们的学生已经多次明确表示，他们也非常希望我们提供更多的 Python。正如我们之前宣布的，更多的是来自我们的新教练，设拉子。然而，在他准备好发布他的新 Python 内容之前，我想我可以用一个我喜欢的有趣的 Python 项目来帮你度过难关:制作一个 IRC 机器人。在这篇博文中，我将讲述如何用 Python 3 创建一个基本的 IRC 机器人。在这篇文章中，我们假设你对 Python 和函数有基本的了解，如果你上过我们的[Linux 上的 Python 入门](https://linuxacademy.com/cp/modules/view/id/14)课程，你应该已经掌握了这个基础 IRC 机器人教程所需的所有知识。如果您有任何问题或需要任何帮助，欢迎在下面发表评论或在 Freenode 上的#LinuxAcademy 频道上跳转。我在 IRC(和大多数其他地方)上用 OrderChaos，所以找找那个名字！

## IRC 机器人

在我们开始之前，你可能想知道，“什么是 IRC 机器人？”非常有用和精彩的维基百科将 IRC 机器人定义为“一组脚本或一个独立的程序，作为客户端连接到互联网中继聊天，因此对其他 IRC 用户来说是另一个用户。IRC 机器人与普通客户端的不同之处在于，它不是为人类用户提供交互式的 IRC 访问，而是执行自动化功能。([来源](https://en.wikipedia.org/wiki/IRC_bot))所以基本上，IRC 机器人对其他人来说是另一个用户，而是根据它的脚本执行设定的动作来响应预定的事件(通常是聊天中的特定消息)。它们可以有多种用途:从保存聊天记录，到管理工具，再到任何数量的其他愚蠢、有用或有时奇怪的功能。有一些机器人可以读取 Twitter feeds，执行网络搜索，甚至可以做`sed`——比如查找和替换(我为此写了一个并在 GitHub 上分享了它！有关详细信息，请参见下面的总结部分)。IRC 机器人可以用多种语言编写。PHP 和 Python 是两种常见的语言，但在许多其他语言中也有，包括 C、Java，甚至 Haskell。维基百科有一页列出了许多 IRC 机器人的[对比。他们中的许多人现在已经死了，不再开发或使用，但他们可以作为灵感和有趣的阅读。好了，背景够了。让我们开始最酷的部分:创建你自己的 IRC 机器人。](https://en.wikipedia.org/wiki/Comparison_of_Internet_Relay_Chat_bots)

## 准备机器人

在我们开始为我们的机器人写所有有趣又酷的东西之前，首先我们必须准备好机器人本身。我们需要确保我们已经设置了 Python，分配了一些变量，并确保我们可以连接到 IRC 网络。在我们开始之前的最后一个注意事项，附在这篇文章之后，我将包括我们所经历的全部代码——如果你在编码时迷路了，只需对照示例查看你应该在哪里。所有代码的解释都包含在附加 bot 的注释中，因此您可以在该文件中获得所需的所有信息。

### Python 设置

首先，确保您安装了 Python 3。我们将假设您在这篇文章之前已经安装并配置了它。打开你最喜欢的 [Python IDE](https://wiki.python.org/moin/IntegratedDevelopmentEnvironments) (如果你没有的话，一个纯文本编辑器，甚至一个终端中的 vim 也行)。首先，我们应该确保指定我们使用的是 Python 3。对于 Windows，这意味着将文件命名为以*结尾的东西。py* 。对于 Linux/Mac，在文件的顶部包含这一行:`#!/usr/bin/python3`。指定 Python3 后，我们需要导入“套接字”库。套接字库用于通过网络端口进行连接和通信。我们用它来连接 IRC 服务器并与之通信。在 Python 中导入库非常容易，因为套接字库是内置的，所以您不需要安装任何东西。只需在`#!/usr/bin/python3`线下添加`import socket`。因此，现在您的文件应该只包含这两行:

```
#!/usr/bin/python3import socket
```

### 全局变量

既然我们已经指定我们在 Python3 中工作，并且导入了套接字库，我们需要定义一些变量。这些变量在整个机器人中使用，所以我们希望在编写任何函数之前定义它们。第一个变量是我们用来与 IRC 服务器连接和通信的套接字。套接字很复杂，可以以多种方式用于多种任务。如果你想了解更多关于插座的信息，请看这里:【https://docs.python.org/3/howto/sockets.html】T2。现在，只需要知道这是用来在机器人运行时建立与 IRC 服务器的持续连接，以发送和接收信息。接下来是我们要连接的服务器和通道的名称。我们可以对这些进行硬编码，但是有一个变量可以简化一些步骤。例如，如果我们想要连接到一个频道列表(而不是像本例中那样只有一个频道)或更改到不同的服务器或频道，我们不必找到每个实例，只需编辑这个变量即可。在这个例子中，我用的是 chat.freenode.net 的*。对于其他 IRC 网络，只需在相同的位置输入名称。之后，我们定义我们最终要加入的渠道。在我们进行测试时，我们不想使用官方/已建立的渠道。除了粗鲁之外，许多频道对机器人有特定的规则，或者根本不允许它们。请确保在将您的机器人添加到频道之前，您已经咨询了频道的版主。在我们的测试中，我们使用了一个定制的、未注册的房间(在 Freenode 上，由频道名称前的“##”表示)。这样，在我们进行测试时，我们将是唯一一个与机器人保持联系的人。我们给这个机器人起名叫*机器人尼克*。这是其他用户在频道中看到机器人的方式。确保这是一个未使用和未注册的昵称，因为如果它已经在使用中，你的机器人将无法连接，而如果它是一个注册和受保护的昵称，它将被分配一个随机名称。[查看这里](https://en.wikipedia.org/wiki/Wikipedia:IRC/Tutorial#Nickname_registration)关于昵称注册的更多信息最后两个变量将在我们的主函数中使用。IRC 机器人不需要它，但是我们将要使用的函数需要它。我们所做的就是定义一个昵称，它可以向 bot 发送管理命令，并定义一个退出代码来结束 bot 脚本。我们在主函数的最后讨论了如何做到这一点。*

```
*ircsock = socket.socket(socket.AF_INET, socket.SOCK_STREAM)server = "chat.freenode.net" # Serverchannel = "##bot-testing" # Channelbotnick = "IamaPythonBot" # Your bots nickadminname = "OrderChaos" #Your IRC nickname. On IRC (and most other places) I go by OrderChaos so that’s what I am using for this example.exitcode = "bye " + botnick*
```

### *连接到 IRC*

*现在我们已经准备好了机器人，并建立了一些我们正在使用的变量，让我们进入实际的连接部分。要连接到 IRC，我们需要使用我们的套接字变量(ircsock)并连接到服务器。IRC 通常在端口 6667 或 6697 上(6697 通常用于带 SSL 的 IRC，这样更安全)。在我们的例子中，我们使用 6667。我们需要将服务器名(在全局变量中建立)和端口号放在括号中，这样它就可以作为一个单独的项传递给连接。一旦我们建立了连接，我们需要向服务器发送一些信息，让服务器知道我们是谁。我们这样做是通过发送我们的用户信息，然后设置我们想要的昵称。通常这些都是相同的，但是注册用户有时会有几个昵称绑定到他们的帐户上，并且可以选择其中的任何一个。*

```
*ircsock.connect((server, 6667)) # Here we connect to the server using the port 6667ircsock.send(bytes("USER "+ botnick +" "+ botnick +" "+ botnick + " " + botnick + "n", "UTF-8")) #We are basically filling out a form with this line and saying to set all the fields to the bot nickname.ircsock.send(bytes("NICK "+ botnick +"n", "UTF-8")) # assign the nick to the bot*
```

## *定义函数*

*这里我们定义了机器人使用的各种函数。这些是可能需要多次调用的代码段。*

### *渠道连接*

*连接到 IRC 是好的，但是除非我们和其他用户在一个频道，否则它没有多大用处！我们把它放在一个函数中，而不是像上面的 ircsock.connect 部分那样硬编码，因为你可以用一个连接在多个通道中。我们在这个例子中只使用一个，所以它可以被硬编码，但是这样你可以看到它是如何完成的，并且如果你愿意的话，可以很容易地为多个通道修改它。在这里，我们接受通道名，作为函数的一部分，然后向 IRC 网络发送 join 命令。“字节”部分让我们指定发送编码为 UTF-8 的消息。这是为了明确地向 IRC 服务器发送正确的编码。在 Python 2 中，这是不必要的，但是 Python 3 中对字符串编码的更改使得这成为一项要求。每当我们向 IRC 服务器发送数据时，您都会看到这种情况。另外需要注意的是，消息末尾的“n”是一个新的行字符。这相当于在聊天窗口中按回车键。它让服务器知道我们已经完成了这个命令，而不是把所有的命令都串在同一行上。在发送 join 命令之后，我们希望开始一个循环，不断地检查和接收来自服务器的新消息，直到我们得到一个带有“End of /NAMES list”的消息。这表明我们已经成功加入渠道。下面的主要功能部分详细描述了每个功能的工作原理。*

```
*def joinchan(chan): # join channel(s).  ircsock.send(bytes("JOIN "+ chan +"n", "UTF-8"))   ircmsg = ""  while ircmsg.find("End of /NAMES list.") == -1:      ircmsg = ircsock.recv(2048).decode("UTF-8")    ircmsg = ircmsg.strip('nr')    print(ircmsg)*
```

### *乒乓球*

*不，我不是指桌面游戏。IRC 服务器定期向连接的用户发送“PING”信号以确保他们仍然连接，这是很常见的。我们必须响应这些消息，让服务器知道我们还在那里。如果我们不响应这些信号，我们可能会与服务器断开连接，因为它认为我们已经断开了连接。这个函数不需要任何参数，因为响应总是相同的。只需用 PONG 响应任何 PING。不同的服务器对 PING 的响应有不同的要求，因此您可能需要根据您的服务器来调整/更新。我在 Freenode 上用过这个例子，从来没有遇到过任何问题。*

```
*def ping(): # respond to server Pings.  ircsock.send(bytes("PONG :pingisn", "UTF-8"))*
```

### *表达重要意思*

*我们已经做了所有主要的准备工作，现在让我们写一些函数，这样我们的机器人实际上就有事可做了。该功能将让我们向频道或用户发送消息。对于这个函数，我们只需要接受一个变量，该变量包含我们要发送的消息以及我们要发送给谁。在参数部分使用 target=channel 将“target”变量的默认值设置为 channel 全局变量。如果只有一个参数 msg 被传递给函数，它将使用默认值“target”。目标和消息之间的“:”让服务器将目标和消息分开。*

```
*def sendmsg(msg, target=channel): # sends messages to the target.  ircsock.send(bytes("PRIVMSG "+ target +" :"+ msg +"n", "UTF-8"))*
```

### *主要功能*

*好了，现在我们已经得到了我们的活动函数并准备好了所有的连接信息，是时候写机器人的连续部分了。这是机器人的主要功能。它将根据需要调用其他函数，处理从 IRC 收到的信息，并决定如何处理它。*

#### *启动*

*我们首先加入我们在全局变量部分定义的通道。之后，我们开始一个无限循环，不断检查和接收来自服务器的新信息。这确保了我们的连接保持开放。我们不想再次调用 main()，因为除了不断尝试重新加入通道之外，当连续多次递归调用一个函数时会遇到问题。在这种情况下，无限 while 循环效果更好。*

```
*def main():  joinchan(channel)  while 1:*
```

#### *接收信息*

*在这里，我们接收从 IRC 服务器发送给我们的信息。IRC 发送以 UTF 8 字符编码的信息，所以我们告诉我们的套接字连接接收多达 2048 字节，并将其解码为 UTF 8 字符。然后我们将它分配给 *ircmsg* 变量进行处理。之后，从字符串中移除任何换行符。如果有人在频道中键入“n ”,它仍然会很好地将它包含在消息中。这只是剔除了可能导致处理问题的特殊字符。我们还将接收到的信息打印到终端上。如果您不想看到它，可以跳过它，但它有助于调试和确保机器人正在工作。*

```
*    ircmsg = ircsock.recv(2048).decode("UTF-8")    ircmsg = ircmsg.strip('nr')    print(ircmsg)*
```

#### *拆分收到的邮件*

*接下来，检查我们收到的信息是否在文本中包含 PRIVMSG。PRIVMSG 是通道中的标准消息(以及指向 bot 的直接消息)进入的方式。大部分消息的处理都在这个部分进行。如果它是一个 PRIVMSG，我们希望获得发送消息的人的 nick，并将其从消息中分离出来。来自 IRC 的消息格式为“:[Nick]！~[hostname]@[IP Address]priv msg[channel]:[message]"所以我们把它拆分为不同的部分，把它们赋给单独的变量。*

```
*    if ircmsg.find("PRIVMSG") != -1:      name = ircmsg.split('!',1)[0][1:]      message = ircmsg.split('PRIVMSG',1)[1].split(':',1)[1]*
```

#### *选择一个操作*

*现在我们已经在它自己的变量中有了名称信息，我们检查名称是否少于 17 个字符。用户名(至少对于 Freenode)被限制在 16 个字符以内。因此，通过这种检查，我们可以确保我们不会响应无效用户或其他恰好包含“PRIVMSG”的消息。之后，我们使用一个检测块来查看它是否包含机器人应该采取行动的特定文本。在第一节中，我们将查看是否有人在消息中的任何地方向机器人问好，然后回复。因为我们没有定义目标，所以它将被发送到通道。第二个例子展示了如何在消息的开头寻找“命令”并解析它来完成复杂的任务。在这种情况下，我们要查找以“”开头的消息。tell”并使用它作为代码来查找要发送的消息和特定目标。整个信息应该看起来像。告诉[目标][消息]"正常工作。附加的 bot 文件中有注释，详细解释了它是如何工作的。*

```
*      if len(name) < 17:        if message.find('Hi ' + botnick) != -1:          sendmsg("Hello " + name + "!")        if message[:5].find('.tell') != -1:          target = message.split(' ', 1)[1]          if target.find(' ') != -1:              message = target.split(' ', 1)[1]              target = target.split(' ')[0]          else:              target = name              message = "Could not parse. The message should be in the format of ‘.tell [target] [message]’ to work properly."          sendmsg(message, target)*
```

#### *阻止机器人*

*因为我们在这个函数中创建了一个无限循环，所以没有自然结束。相反，我们将检查一些文本，并使用它们来结束函数(这将自动结束循环)。我们要做的是查看发送消息的人的名字是否与我们之前定义的管理员名字相匹配。我们让两者都小写，以防管理员在加入时输入的名字略有不同。在 IRC 上，‘order chaos’和‘order chaos’是同一个昵称，但是 Python 会把它们解释成不同的字符串，除非我们先把它全部转换成小写。我们还确保消息与上面的退出代码匹配。退出代码和消息必须完全相同。通过这种方式，管理员仍然可以键入带有额外文本的退出代码来解释它或向其他用户谈论它，而不会导致机器人退出。我们所做的唯一调整是去掉消息末尾的任何空白。因此，如果消息匹配，但在末尾有一个额外的空格，它仍然有效。如果退出代码是由管理员发送的，该函数会点击“return”行，该行会自动中断任何循环和 If 语句，并转到调用该函数的行。通常情况下，它会继续运行额外的代码行，但是我们将在调用 main()时结束脚本，这样就不会再有代码需要运行，bot 将会关闭。*

```
*        if name.lower() == adminname.lower() and message.rstrip() == exitcode:          sendmsg("oh...okay. :'(")          ircsock.send(bytes("QUIT n", "UTF-8"))          return    else:*
```

#### *响应 Pings*

*如果消息不是 PRIVMSG，它可能仍然需要一些响应。如果我们收到的信息是一个 ping 请求，我们调用之前定义的 PING()函数，用 PONG 响应。这让服务器知道我们仍然在线和连接。*

```
*      if ircmsg.find("PING :") != -1:        ping()*
```

#### *启动主功能*

*最后，既然已经定义了主函数，我们需要一些代码来启动它。它不需要任何参数，就像这行代码一样简单。*

```
*main()*
```

## *包裹*

*现在你知道了。一个基本的，可以与 IRC 连接的机器人。它不是最有效或防错的机器人，但它是一个好的开始，会给你一些东西来建立。如果你对更复杂和更高级的 IRC 机器人感兴趣，可以看看维基百科上提到的许多流行的 IRC 机器人的比较。特别是， [Sopel](https://github.com/sopel-irc/sopel) IRC 机器人是一个非常复杂和深入的 IRC 机器人，具有众多的功能和插件。它正由许多贡献者积极开发中。我有时也开发我自己的 Python IRC 机器人，它没有太多的特性(还没有！).您可以找到原始版本(用 Python 版本 2！)这里:【https://github.com/Orderchaos/ircbot】T4。它记录最近的聊天，并可以使用类似 sed 的命令进行查找/替换。开发分支有一个 Python 3 版本，我正在进行一次大的重写，将展示一些复杂的 sqlite3 数据库日志功能。~~附上我们刚刚经历的 [bot](https://linuxacademy.com/blog/geek/creating-an-irc-bot-with-python3/attachment/bot-2/) 。你可以用它来检查你的工作，或者把它保存到你自己的脚本中，然后开始使用它。编辑:附件似乎没有正常工作。我们将把这个机器人上传到我们的 GitHub，并尽快发布。今天晚些时候回来查看完整的代码和注释！与此同时，请随意复制这篇文章中的代码并编译您自己的代码！编辑 2:你现在可以在一个地方找到所有的代码:https://github.com/Orderchaos/LinuxAcademy-IRC-Bot 今天晚些时候将添加额外的评论，这是原始代码，正如这篇博文中所示。如果你想聊天或有任何问题，请随时跳上 Freenode，加入我们的#LinuxAcademy 或给我发消息(我的 Freenode 昵称是 OrderChaos)。~~*