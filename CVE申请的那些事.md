# CVE申请的那些事
在上一篇分享`《安全小白面试的那些坑》`中和大家提到面试的时候可以在简历中附上提交过的原创漏洞如`CVE`、`CNVD`编号等信息，以证明自己在漏洞挖掘方面的技术经验和能力。


## 什么是CVE
对于新手来说申请`CVE`总是摸不清门道，总觉得像这种国际化的高大上漏洞很难申请到，其实则不然，`CVE`的全称是`“Common Vulnerabilities and Exposures”`翻译成中文就是`“公共漏洞和披露”`可以把它理解成一个被安全从业者认可的漏洞字典，大家可以通过编号在这里查找不同应用或系统的漏洞信息。当然很多安全企业或国家机构也都会引用CVE作为其漏洞库，比如美国国家漏洞数据库（NVD）。

## 什么是CNA
`CNA`的全称是`“CVE Numbering Authority”`中文可以理解为`“CVE编号授权机构”`顾名思义就是这些`CNA`有权限分配和管理`CVE编号`，截止目前为止，共有`85`个`CNA`，覆盖`14`个国家。`CNA`包括供应商（比如苹果、谷歌等公司）和项目发起机构，漏洞研究人员、国家和行业`CERT`以及漏洞奖励计划组织。这些`CNA`可以构建`CVE列表`，并分配列表中的`CVE编号`和录入相关信息。

## 我们应该怎么申请CVE
通过上面的说明，你应该能猜到了，想要申请`CVE`编号那当然要去找`CNA`了，因为`CVE编号`都是`CNA`创建和维护的嘛。

虽然找到找谁了，但是`85`个`CNA`呢，咱们应该找哪个呢？

那要看我们发现的是上面漏洞了，申请`CVE`大致可以分为`3`种情况，这`3`种情况套哥我都尝试并成功过，下面给大家一一讲解下：

第一种：找`Participating CNA`要`CVE编号`

第二种：找`Primary CNA`要`CVE编号`

第三种：找`Distributed Weakness Filing Project CNA`要`CVE编号`

### 第一种：找`Participating CNA`要`CVE编号`

首先来说说这第一种找`Participating CNA`要`CVE编号`，`Participating CNA`的意思就是`参与CNA`，你可以把他们理解为参与`CVE计划`的公司或项目发起者，总之就是有产品拿出来让大家挖漏洞的，这些`CNA`有一个列表在`http://cve.mitre.org/cve/request_id.html#cna_participants`

![1.png][1]

如上图所示，这个列表主要有`4`个部分，分别是`名称（Product, Vendor, or Product Category Name）`、`范围（Scope）`、`联系方式（CNA Contact Email and/or Webpage (if applicable)）`、`CNA类型（CNA Type）`。我们关注的主要是`范围`和`联系方式`。

![2.png][2]

比如你发现了`Adobe产品`的漏洞并且在`Adobe issues`的范围内，那么就可以发送邮件到`psirt@adobe.com`申请CVE编号，或者访问`Adobe公司`的安全中心页面`https://helpx.adobe.com/security/alertus.html`进行反馈。

### 第二种：找`Primary CNA`要`CVE编号`
这个第二种方式是找`主CNA`要编号，什么是`主CNA呢`？其实就是`MITRE官方`，细心的你可以会发现其实`MITRE`也是在`参与CNA`里面而且是第一个，区别在于如果你找到的漏洞不在`参与CNA`那些公司里面，但是漏洞又确实存在，那么就可以找`MITRE官方`来申请编号。

![3.png][3]

方法很简单通过`MITRE CVE Request web form`页面进行提交即可，地址是`https://cveform.mitre.org/`，这个页面还是很友好的，不过是英文的，我们提交漏洞也需要使用英文。在实战章节会给大家详细讲解。

### 第三种：找`Distributed Weakness Filing Project CNA`要`CVE编号`
这个第三种方式翻译过来是“分布式弱点申报项目”，其实主要是指不在`参与CNA`那些公司里面并且是开源软件或系统的漏洞，可以通过这种方式提交，可以看到联系方式有`3`种，第一个是`邮箱`、第二个是`页面`、第三个是`github地址`。

![4.png][4]

比如你在`github`上发现某个`开源项目`存在漏洞，就可以通过发邮件给`cve-assign@distributedweaknessfiling.org`或者通过`https://iwantacve.org/ `页面表单提交或者访问`DWF GitHub page`页面提交。当然你会发现访问`https://iwantacve.org/`是需要`梯子`的。

而且。`这种方式审批极慢！！！这种方式审批极慢！！！这种方式审批极慢！！！`

那正确快捷的方法是上面呢？当然是选择前两种方法啦，其实细心的你也会发现，通过前两种方法可以完全覆盖所有的漏洞，简单来说`“第一种呢是列表里的厂家的漏洞，第二种呢是除了第一种以外的所有漏洞”`。下面实战讲解下具体申请流程吧，套路是`“找开源CMS漏洞，用第二种方法申请CVE编号！”`

## 实战获取CVE编号

思路：

1、在`github`上寻找目标找漏洞

2、在`github`上提交`Issues`

3、通过`https://cveform.mitre.org/`提交

下面就具体实战演示。首先在`github`上用关键字`cms`进行搜索，然后找你熟悉的编程语言（套哥我喜欢php）然后找一个看上去不那么复杂的`cms`作为目标。

![5.png][5]

套哥找的是一个叫`“五指CMS”`的`php`开源项目，看这个`cms`官网上介绍还说的是`“高性能、强安全”`……

确定目标后下载程序、搭建环境、上扫描器、代码审计……你们的方法肯定比我多，毕竟套哥我已经老了，跟不上现在的圈子了^_^!!!

很简单，在后台发现两个`csrf`，可以通过2步添加管理员，第一步`csrf`添加一个普通用户并激活，第二步`csrf`把添加的普通用户提升为管理员。你们是不是觉得没营养，其实也不完全没营养，这里面遇到一个问题，就是`post`包的`data`里有一个`"submit=提交"`，这个在构造自动提交`form`的`html`页面时是与提交`js`中的`"submit()"`重名的，导致`js`中的`"submit()"`不会执行，开始的时候想着直接去掉这个参数应该不会有影响，但是提交后回显`“参数错误”`。网上百度了不少也没找到好的方法，最后群里问了下大表哥找到了方法。把这个`"submit=提交"`放到URL里，其他数据放在`post`的`data`里。结果当然`OK`啦。
`csrf`的`poc`如下：

![6.png][6]

![7.png][7]

效果如下：

![8.png][8]

漏洞找到了，第二步就是到`github`上提交`Issues`。没有`github`账号的小伙伴请自行申请，套哥也没有`github`的账号，于是发大表哥帮忙提交到了`wuzhicms`的官方`Issues`，地址如下：

`https://github.com/wuzhicms/wuzhicms/issues/128`

把漏洞和触发条件说清楚即可，因为要提交`CVE`就让大表哥用英文写的`Issues`。

准备工作基本完毕，下面是第三步提交到`mitre`官方平台，页面在`https://cveform.mitre.org/`，按照下图填写：

![9.png][9]

![10.png][10]

![11.png][11]

填好后，填写验证码提交即可。提交后一般马上会收到官方的确认邮件。大概意思就是感谢你提交漏洞，将有`CVE`团队成员进行审核，如要更改、添加信息可以直接回复邮件，不要更改邮件标题等等。

![12.png][12]

可以不用理会，一般过`1-2`天就会有审核的结果邮件，邮件里会有你提交漏洞的信息和分配的编号。

![13.png][13]

到这里基本就已经申请完成了，漏洞将在`24`小时内发布到`CVE官网`，可以通过`https://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2018-9926`访问

![14.png][14]

有一起组团刷`CVE`的小伙伴可以加套哥微信一起交流（微信号：`anquanquantao`）


  [1]: http://www.5ecurity.cn/usr/uploads/2018/04/781695346.png
  [2]: http://www.5ecurity.cn/usr/uploads/2018/04/3576005639.png
  [3]: http://www.5ecurity.cn/usr/uploads/2018/04/573061566.png
  [4]: http://www.5ecurity.cn/usr/uploads/2018/04/791226771.png
  [5]: http://www.5ecurity.cn/usr/uploads/2018/04/255991175.png
  [6]: http://www.5ecurity.cn/usr/uploads/2018/04/2634253588.png
  [7]: http://www.5ecurity.cn/usr/uploads/2018/04/4065169619.png
  [8]: http://www.5ecurity.cn/usr/uploads/2018/04/424950814.png
  [9]: http://www.5ecurity.cn/usr/uploads/2018/04/117305779.png
  [10]: http://www.5ecurity.cn/usr/uploads/2018/04/3751966975.png
  [11]: http://www.5ecurity.cn/usr/uploads/2018/04/1978482505.png
  [12]: http://www.5ecurity.cn/usr/uploads/2018/04/560425497.png
  [13]: http://www.5ecurity.cn/usr/uploads/2018/04/955551437.png
  [14]: http://www.5ecurity.cn/usr/uploads/2018/04/296224555.png
