# PKUAutoSubmit
更新试运行
跑一下试试
再跑一次
重新copy
shihih
我要放假我要放假我要放假我要回家
手动更新
**UPDATE 2021/10/26**
百京吉利大学
现在使用时会报错`ImportError: cannot import name 'PhantomJS' from 'selenium.webdriver' `，估计是selenium版本更新后去除了PhantomJS，我修复了一下，每次都只使用3.141.0版本的selenium，现在可以正常用了。

**UPDATE 2021/4/3**

两次忘了报备后，我打算把原来的自动填报的功能加上。用XPath迅速上线了这个功能。代码极其丑陋，见谅。 

现在将名字改回了**PKUAutoSubmit**，因为目前它具有填报云战疫和学生出入校两种功能。

在之前[使用方法](https://haysc.tech/2020/10/17/pku-auto-beian/)的基础上，**将main.py第18行的CONFIGCODE改成0则是云战疫，改成1就是学生出入校**。

**UPDARTE 2021/1/23**

感谢之前所有为本项目提供代码以及撰写文档的同学。本项目原为[PKUAutoSubmit](https://github.com/YOUSIKI/PKUAutoSubmit)，用于学生出入校的自动填报，但现在已是寒假，很多回家的同学不再需要填写出入校信息，而是要每天填写燕园云战“疫”。因此我将其稍作修改，变成了燕园云战“疫”的自动填报程序。项目名称改为了`PKUAutoSubmit_yzy`（yzy就是云战疫的缩写），用来和之前的项目做区分（毕竟这个只在寒假用，返校后可能又回到了原来的出入校模式）

使用之前请务必手动填写一次，保证访问到燕园云战疫页面时，有必要的缺省值，只有“是否存在以下症状 （发热、咳嗽、腹泻）”和“疫情诊断”两个必填项

## 适用人群
本项目适合满足以下全部条件的同学：  
1.寒假未留校  
2.居住地固定，且在低风险区  
3.健康  

如果发生以下事件，请您停止自动填报，向学校如实填报您的信息：  
1.您所在的地方出现疫情  
2.您出现发热、咳嗽等症状  
3.您的居住地发生了改变  
4.您与确诊病例密接，或与确诊病例密接者密接，尚未解除观察  

## 我的工作
仅仅对参数以及参数的读取方式进行了修改，然后将action的触发改在了北京时间9:15和10:45（但实际运行时间实测是10:55和11:50，好奇怪，求大佬解答） 
具体的使用方法直接看下方原项目Readme中的[hayschan](https://github.com/hayschan) 撰写的[使用文档](https://haysc.tech/2020/10/17/pku-auto-beian/)，以及[What did I do](#jump)部分

# 以下是[原项目](https://github.com/YOUSIKI/PKUAutoSubmit)Readme

**UPDATE 2020/10/18**

感谢 [hayschan](https://github.com/hayschan) 撰写的[使用文档](https://haysc.tech/2020/10/17/pku-auto-beian/)，强烈推荐在使用本项目前阅读。

<span id="jump"></span>
## What did I do

没做什么工作，只是合并为一个 main.py 然后改了改参数读取方式。然后写了个 Github Actions 的配置文件，每天自动执行两次。你可以 fork 本仓库然后在自己仓库的 Settings/Secrets 中设置 USERNAME 和 PASSWORD 两项，一劳永逸。如果你想使用其他填报参数，请自行修改 `.github/workflows/main.yml`，参数名称参见 `main.py`。

感谢原作者！

---

以下为原作者 README

---

PKU一键出入校备案小工具 v1.9.1 (2020.10.10)

为作者的第一个 `selenium` 练手小项目，完善程度较低，欢迎任意类型的使用与改进

**P.S.** 由于作者水平与精力所限，暂时仅提供 win x64 版本（ x86 请自行测试），mac OS 版本可能会在之后推出，也欢迎自行修改开发（理论上只需要更换 `PhantomJS` 版本即可）

**Update:** 现已支持 mac OS（感谢 JuiAnHsu 的 contribution），欢迎各使用 mac OS 系统的小伙伴们参与使用与开发升级

**Note:** 由于 `run.bat` 和 `autoRun.bat` 为 Windows 批处理程序，无法在 mac OS 上运行，故 mac OS 中的定时运行功能仍在开发中

**Note:** 本项目已上传至[北大网盘](https://disk.pku.edu.cn/#/link/238B48AD673833F65A9EE34181654B07)

**Update:** 修复填报入校备案时可能出现的会话失效导致填报失败的问题

## 说明

- 本工具采用 Python3 搭配 `selenium` 完成自动化操作，实现全自动填报学生出入校备案，为频繁出入校的 PKU 学子（不频繁也行）提供较为便捷的解决方案
- 采用 `PhantomJS` 无头浏览器作为 `driver` ，相较 `Chrome` 、`Firefox` 等浏览器更为轻量化，且运行快速
- 支持设置在运行结束后返回历史备案页面截图，无需自行登录查看备案结果
- 搭配 Windows 定时任务，可实现定时（如每日）免打扰填报并在指定位置返回结果截图
- 第三方依赖包几乎只有 `selenium` 一个，从下到用贼jr快

## 安装与需求

### Python 3

本项目至少需要 Python 3，可以从[Python 官网](https://www.python.org/)下载安装

本项目采用 Python 3.7.4 开发，由于含有 `f-string` ，请至少使用 Python 3.6 及以上版本，建议使用 Python 3.7 及以上版本

### Packages

#### selenium

采用如下语句安装 `selenium`，支持 2.48.0 及以上版本：
`这里时jiang13021的注释：由于高版本的selenium不支持selenium.webdriver.PhantomJS，因此我建议，使用3.141.0版本的selenium`

```
pip3 install selenium==3.141.0
```

然后就没了。惊喜吧！

## 基本用法

1. 将 `config.sample.ini` 文件重命名为 `config.ini` ，请不要新建文件，不然自己搞定编码问题
2. 用文本编辑器（建议代码编辑器）打开 `config.ini` 文件
3. 配置 `[login]` 、`[common]` 、`[out]`、`[in]`、`[capture]` 这几个 Section 下的变量，在 `config.ini` 文件内有详细注释
4. 进入项目根目录，以命令 `python main.py` 运行主程序即可
   - 亦可双击 `run.bat` 运行
   - 亦可用代码编辑器打开 `main.py` 并运行（并不推荐）

## 定时运行

本项目中的 `autoRun.bat` 文件可提供在静默免打扰情况下运行程序的选择，配合 Windows 任务计划管理可实现定期自动填报，具体请参考[Win10下定时启动程序或脚本](https://blog.csdn.net/xielifu/article/details/81016220)

**Note:** 静默运行的弊端为无法看到任何报错信息，若程序运行有错误，使用者很难得知。故建议采用定时静默运行时，设置备案历史截图功能并定期查看截图，若截图生成说明已成功运行，并可通过查看截图进一步确认。

## 补充说明

1. 本项目主要为校内日常出入的同学提供便捷解决方案，会同时填报出校与入校备案，不支持单独填报，也不支持京外返校填报。若有此类特殊需求，烦请手动填报。
2. `PhantomJS` 作为经典的轻量级无头浏览器，相较 `Chrome` 等大型浏览器体量小的多，不占空间且运行快速。但是由于其本身属性也可能造成一系列问题，如：
   - `driver` 启动后第一次通过 iaaa 认证必触发一次 500 错误，通过 `headers` 设置也无法改善问题，故在运行中有所标注，一般仅需 Retry 一次即可。限于作者水平，还未找出具体原因，若有发现的欢迎 report（已修复，感谢 RainshawGao 的 contribution）
   - 由于仅为练手项目，对于学校土豆服务器造成的各类玄学问题作者只能尽力避免，但并无完善的 Exception 处理机制，若遇到报错欢迎 report，且万能的重来一次大法可以解决绝大多数问题
3. 当前看来，无论出不出学校都可以填报备案，所以每天定时运行一次并没有什么问题（事实上，作者在测试阶段每天填几十次，希望人没事.jpg）
4. 项目中的 `\phantomjs\bin\` 目录下有两个应用程序 `phantomjs` 和 `phantomjs.exe`，分别对应 mac OS 和 Windows 的版本，为节省空间，可在确保运行无差错后删除另一个

## 责任须知

- 本项目仅供参考学习，造成的一切后果由使用者自行承担
- 本项目敏感性不比 skj，利人利己，私以为还是可以合理扩散一下的，吧？

## 证书

[Apache License 2.0](https://github.com/Bruuuuuuce/PKUAutoSubmit/blob/main/LICENSE)

