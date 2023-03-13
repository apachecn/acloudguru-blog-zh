# 如何建造自动驾驶机器人赛车

> 原文：<https://acloudguru.com/blog/engineering/how-i-built-an-autonomous-car-to-drive-awareness-for-women-who-code>

> “当你戴上头盔时，你是女人还是男人并不重要……重要的是你的能力、你的智慧和你的决心。”
> —米尔卡·达诺，职业赛车手

在最近的 AWS re:Invent 会议期间，我有机会在我们的展厅展位上展示威瑞森的云工程成果，并分享我对我们如何在 AWS 上开发和部署大规模解决方案的见解。

作为会议体验的一部分，我们在 [A Cloud Guru](https://acloudguru.com/) 的朋友邀请我参加 Robocar 集会，这是一个为期两天的黑客马拉松，专注于深度学习、物联网和人工智能，以制造和比赛 1/16 比例的自动驾驶汽车。

在两天的时间里，我作为唯一的女性参与者与来自 [Capital One Tech](https://medium.com/u/73d9ee9c08c8?source=post_page-----bec91f94da91--------------------------------) 的 [Anne-Jeanette](https://medium.com/u/38d39dd90fdc?source=post_page-----bec91f94da91--------------------------------) 合作——定制并训练一辆比例模型自动驾驶汽车，以参加 re:Invent 赛道上的计时赛。

经过几天 12 个小时的黑客攻击，我们制造了一辆具有竞争力的无人驾驶模型赛车，提高了对编码女性和 AWS“我们动力技术”多样性项目的认识。

## 让你的机器人汽车启动并运行的步骤

“驴车”是大多数新手使用的初始套件模型——它大约需要 200 美元，需要几个小时才能组装好。Donkey 是支持自动驾驶汽车的 Python 库的名字。

> **为什么叫驴？**
> 驴是最早驯化的驮畜之一，它们的倔强是出了名的，而且它们是安全的。在汽车能够从城市的一边行驶到另一边之前，我们会推迟用某个天体来命名它。

### 第一步:制造汽车

你将需要建立汽车底盘，然后配备树莓皮和相机。在 [donkeycar 网站](http://docs.donkeycar.com/guide/build_hardware/)上可以找到零件清单和说明——你可以打印零件，也可以选择购买。

制造一辆汽车——驴车——安装摄像头有点棘手，M2 螺丝可以拧进塑料里，但有点难。我—docs.donkeycar.com

### 步骤 2:设置软件环境

首先，你需要在你选择的主机操作系统上安装 64 位版本的 [git](https://www.atlassian.com/git/tutorials/install-git) 和 [miniconda Python 3.6](https://conda.io/miniconda.html) 。

[wroscoe/驴子—驴子—自动驾驶汽车—github.com](https://github.com/wroscoe/donkey/blob/master/docs/guide/install_software.md#install-donkeycar-on-mac)

*   首先，您需要 git 将 repo 和 cd 克隆到根文件夹中。

```
git clone https://github.com/wroscoe/donkey
cd donkey
```

*   接下来，启动 Anaconda 管理系统。

```
conda env create -f envs/mac.yml
source activate donkey
```

*   下面的`pip`命令用于安装 Python 包。在这种情况下，我们将使用它来安装 TensorFlow 一个由谷歌创建的开源机器学习库，用于分析从我们汽车的摄像头收集的图像和数据。

```
pip install https://storage.googleapis.com/tensorflow/mac/cpu/tensorflow-1.3.0-py3-none-any.whl
```

*   我们还将使用`pip`来安装剩余的包。

```
pip install -e .
```

*   最后，你需要创建汽车的数据路径。

```
donkey createcar — path ~/d2
```

恭喜你！设置完成。

### 步骤 3:配置树莓 Pi

在第一步中，您将树莓派和摄像头连接到汽车底盘上。此时，您的 robocar 应该已经完全组装好了。

在“ssh”到我们的 pi 之前，我们需要将 SD 卡制作成启动盘，这样它可以帮助启动 pi。对于简单版本，您可以安装 Etcher 或 Noobs——它们都提供了用于写入 SD 卡的图形界面实用程序。

对于像我这样喜欢命令行的开发人员，打开终端窗口并键入:

```
diskutil list
```

*   找到你的 SD 卡的分区——它可能叫做`disk4`
*   用您的 SD 卡磁盘名称替换<name of="" disk=""></name>

```
diskutil unmountDisk /dev/<name of disk>
```

现在我们需要[下载 donkeycar 团队创建的方便的磁盘映像](https://www.dropbox.com/s/wiudnm2dcsvoquu/donkey_v22.img.zip?dl=0)。当前的版本是 22，但是我建议查看 donkeycar 站点上的文档以获得最新版本。

*   接下来，将下载映像安装到 SD 卡上。这可能需要一些时间，请耐心等待。

```
sudo dd bs=1m if=<image/path/image.img> of=/dev/rdisk<disk# from diskutil> conv=sync
```

*   如果您的映像放在下载文件夹中，并且您的 SD 卡是 disk4，则命令应该是:

```
sudo dd bs=1m if=~/Downloads/donkey_v22/donkey_v22.img of=/dev/rdisk4 conv=sync
```

### ProTip

> 可以喝酒，可以自主驾驶！

### 步骤 4:将您的 pi 连接到 wifi

为了将从 Raspberry Pi 收集的驾驶数据传输到您的本地主机上进行培训，我们需要确保这些设备在同一个 wifi 网络上。

要设置 wifi，需要在启动分区中安装一个文件，其中包含启动时连接网络所用的配置参数。

*   确保您的 SD 卡仍处于连接状态。
*   在您的 SD 上，应该有一个/boot/目录。
*   在 boot 里面，会有一个 wpa_supplicant.conf 文件。
*   打开您最喜欢的文本编辑器并添加您的网络设置。
*   我们在黑客马拉松中使用了下面的代码。确保添加您的网络名称和网络密码，并保留引号！

```
country=US
ctrl_interface=DIR=/var/run/wpa_supplicant GROUP=netdev
update_config=1
network={
 ssid=”<your network name>”
 psk=”<your password>”
}
```

*   现在你可以把 SD 卡取出来插在你的树莓 Pi 上了。如果网络上只有一个树莓派，可以尝试用`ping raspberrypi.local`找到它的 ip 地址
*   在 robocar 拉力赛黑客马拉松上，这不是我们团队的最佳选择。我们必须将 pi 连接到外部监视器来找到它的 ip 地址。
*   如果您需要这样做，您在 donkeycar 映像文件版本 22 上的用户名和密码将是:

```
Username: pi
Password: asdfasdf
```

*   登录后，输入`ifconfig wlan0`查看 ip 地址信息。
*   一旦你有了你的 Raspberry Pi 的 IP 地址，我们现在就可以 ssh 到我们的 Pi。耶！

```
ssh pi@<your_pi_ip_address>
```

### 步骤 5:配置 pi

一旦您登录到您的 Raspberry Pi，您就可以使用提供的模板，使用 donkey CLI 创建您的汽车了。

```
donkey createcar — template donkey2 — path ~/d2
```

*   将目录更改为您刚才指定的路径——在本例中是`/d2/`

```
cd ~/d2
```

*   最后，启动您的 web 服务器！

```
python manage.py drive
```

*   如果成功，服务器将在`<your car’s IP’s address>:8887`运行，其中 8887 是我们的端口号。
*   为了让驾驶更容易，我们用手机连接到网络服务器。只要确保你的手机和你的树莓派连接在同一个 wifi 网络上。

### 步骤 6:获取数据并训练模型

恭喜你。robocar 现已安装完毕，您可以开始为您的汽车记录一些驾驶数据了——数据越多越好！一定要慢行；出于训练的目的，你想把最好的模型推到汽车上。

记录的数据由一个 JPEG 图像和一个相应的带有转向和油门信息的 JSON 文件组成。一旦您收集了数据，您将把数据传输到您的主机操作系统，以使用 TensorFlow 创建一个模型。

*   从你的覆盆子里复制数据。

```
rsync -r pi@<your_pi_ip_address>:~/d2/data/ ~/d2/data/
```

```
python ~/d2/manage.py train — model ~/d2/models/myPilotName
```

*   完成后，将新的试点文件推送到您的车上。

```
rsync -r ~/d2/models/ pi@<your_ip_address>:~/d2/models/
```

*   进入您的 pi，用闪亮的新 pilot 文件启动您的服务器。

```
python manage.py drive — model ~/d2/models/myPilotName
```

*   连接到您的 web 服务器，并通过从下拉列表中选择“本地角度”来开始使用试点文件。这将允许你控制速度和飞行员控制转向。

### 最后一步:庆祝！

恭喜你。你现在有了一辆自动驾驶汽车——尽管可能还不是很连贯。每次尝试后收集的数据越多，模型和自动驾驶就越好。

对于更强大的模型训练，您可以使用部署为 Docker 容器的深度学习虚拟机在 [AWS 上训练您的模型——这是一种训练更高性能模型的更高级方法。](https://acloudguru.com/course/aws-certified-machine-learning-specialty)

如果你去了 AWS re:Invent 并参加了机器人汽车拉力赛 hackathon——你还会从沃纳·威格尔那里得到这个令人敬畏的奖品！

### 我们支持科技

在 Robocar Rally hackathon 的一个挤满了 100 多名工程师的房间里，Anne-Jeanette 和我是仅有的两位女性开发人员。我很感激我们有机会[代表编写](https://acloudguru.com/blog/news/a-cloud-guru-women-who-code-extend-partnership)代码的女性，这要感谢一位云专家以及她们与 AWS We Power Tech 的合作——谢谢！

在参加了黑客马拉松和会议之后，前进的道路看起来非常清晰。那些在技术领域代表性不足的人需要更多像 Robocar 拉力赛这样的机会——获得培训、会议和黑客马拉松的机会，这些机会提供了克服职业进入和发展障碍所需的高级技能。

[We Power Tech ——一位云专家正在与 AWS We Power Tech 合作，希望看到一个各种肤色、性别、信仰、起源的技术未来…——info . A Cloud . Guru](https://acloudguru.com/blog)

AWS re:invent 大会是一个与众多引领云计算未来的女性联系、交流和学习的绝佳机会。我很幸运能在像威瑞森这样的公司工作，领导们积极支持技术的多样性和包容性——看到这么多其他公司加入对话令人鼓舞。

一起，#WePowerTech！

* * *

## 获得更好职业所需的技能。

掌握现代技术技能，获得认证，提升您的职业生涯。无论您是新手还是经验丰富的专业人士，您都可以通过实践来学习，并在 ACG 的帮助下推进您的云计算职业生涯。

* * *