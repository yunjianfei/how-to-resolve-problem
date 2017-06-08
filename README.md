**关于架构的思考（一）**
=====


# 1. 背景


很早就想写这么一篇文章总结一下这些年学习、思考、解决问题的方法，但是又怕自己水平有限。后来想想，不管对与错，能引发一些思考也是好的。
    
文章标题虽然是《关于架构的思考》，实际上本文是在阐述关于“问题”的一些思考和总结。相信很多同学都会有一些相同的感悟和思考。

---
电影《教父》中有这么一句台词：
 >花半秒钟就看透事物本质的人，和花一辈子都看不清事物本质的人，注定是截然不同的命运。

这句话我赞同、也不赞同。赞同的是看透事物本质的能力确实比较重要，不赞同的是“注定是截然不同的命运“这句话，太过绝对。

用这句话作为引子，主要是强调看透事物本质能力的重要性。



# 2. 架构的本质


*注意：本文提到的架构，如无特殊说明，一律都指“软件架构”。*

对于技术人员来说，一提到架构，可能很多人想到的就是高可用、高并发、容错性、高内聚低耦合或者是各种框架、开源等等。在引子中，我们谈到了看透事物本质的重要性，那么架构的本质是什么呢？

从需求或者解决问题的角度来看：

**架构的目的是为了解决“一个”核心需求、痛点或者问题**

例子：我们要做一套高性能秒杀系统的架构。（核心问题/需求是秒杀系统）

*注意：核心问题只能有一个，如果出现了多个，就必须找到最核心的一个*

架构贯穿于软件的整个生命周期(需求分析、概要设计、详细设计、编码、测试、上线、运维)，在这个生命周期中，我们可能会遇到无数问题，但是这些问题始终是围绕着架构的最终目的（*架构是为了解决一个核心需求、痛点或者问题*），以问题的角度来看架构：

**架构本质上是挖掘问题本质、解决问题的过程。**

例子：秒杀系统架构，在需求分析阶段是要弄清秒杀系统是给谁用的？有哪些功能要求（业务需求）？有哪些非功能要求（性能、稳定性、扩展性等等）？业务流程是什么样（输入、输出）等等。需求分析其实就是挖掘“秒杀系统”这个问题本质的过程，后面的流程就是在解决需求分析中挖掘出来的问题。

我们生活、工作中会遇到各种各样的问题，如果有意识的去思考、总结，那么就会发现一些解决问题的规律和方法，能帮助我们更好的解决各类问题。当然，也能运用在架构中。


# 3. 什么是问题


前面的章节多次提到了一个词"问题"，那么到底什么是问题呢？有很多人可能会说，你这问题真奇怪，你提的难道不是问题吗？

好吧，我确实是提了一个问题。中国的文字真是博大精深，一个词可能有N个意思。我们今天要讨论的并不是疑问句式的问题(Question is not problem. 我们要讨论的其实是problem)。先看一下维基百科中对于"问题"的定义：
>问题很难有一个确定的、无异议的定义，但是，一般来说都问题包含有以下三个基本成分：

>1.  上下文－和问题相关的场景，指一组已经是明确已知的，关于问题的条件的描述。

>2.  目标－指关于构成问题的结论的明确的描述。

>3.  障碍－指问题的正确解决方法不是显而易见的，必须通过一定的思维活动，才能找到答案。

>一般而言，问题是由于某些导致不能达到目的或者实现目标的认识障碍。它是指不期待的现状没有被解决或者事态出现意外。

上面的描述还是有点抽象，这里谈一下我对问题的理解：
>**问题 = 现状和目标有差距**

举两个例子：

1. 我负责的系统又不能访问了。
        
     目标：系统可以正常访问
     
     现状：系统不能访问

2. 明年我要结婚。
        
     目标：明年结婚
     
     现状：现在还没有结婚

   
这两个例子虽然都不是疑问句式，但是他们实实在在的是问题。如果仔细思考，两个例子有很大差别，具体请看“问题的分类”。



# 4. 问题的分类


我们遇到的问题有很多，按照不同的分类方式可以分成不同的类型，比如按照问题内容分类，可以是生活问题、工作问题、学习问题等。按照难易程度，有可以分为简单问题、困难问题等。

这里我们结合时间维度与问题现状、目标的关系，分为两类：

## **异常型问题**
    -目标是现在就应该达到的
    -现状没有达到目标
    -解决方式偏重于寻找原因

例子：我负责的系统又不能访问了。

1.  目标：系统现在是可以访问的（目标是现在就应该达到的）
2.  现状：系统现在不能访问（现状没有达到目标）

这是一个典型的异常型问题。

**解决异常型问题的关键点在于找到现状没有达到目标的原因。**

## **改善型问题**
    -目标是将来去达到的
    -现状没有达到目标
    -解决方式偏重于如何达到目标

例如：明年年我要结婚。

1.   目标：明年结婚（目标是将来去达到的）
2.   现状：没有结婚（现状没有达到目标）

这是典型的改善型问题。

**解决改善型问题的关键点在于如何达到目标。**

我们遇到的所有问题，都可以分为这两类，大家可以尝试对自己遇到的问题分个类。

---
*PS:   经常看到关于架构演进的讨论，从问题分类的角度来看架构演进，可以认为是现有架构发生了异常型问题，在解决的过程中，发现不能通过优化现有架构来解决。于是提高目标，新设计架构来解决**老问题的新目标**，异常型问题转变为改善型问题。也就是说，架构都是在解决改善型问题。*

举个例子：有一套秒杀系统，现有架构设计的目标是解决5万并发秒杀请求这个问题。运行过程中，发现3万并发请求就无法支撑了（发生了异常问题），在追查问题原因、解决问题的过程中，通过优化手段只能把并发提升至4万左右。且预计未来一年业务会快速增长，并发秒杀会提升至20-30万。再考虑到要未来的增长，架构设计目标变成了解决50万-100万并发秒杀请求这个问题（异常型问题升级为改善型问题）。



# 5. 问题的视角


我们认知世界的过程中，存在很多视角，从不同的视角去认知，可能得到完全不一样的结论（比如换位思考其实就是一个视角的转换）。这里我们以问题作为视角来看观察，先从一个小故事开始。

时间：新石器时代

人物：一个皮糙肉厚的原始人，我们称之为MM

故事：MM在回山洞的路上发现了一只膘肥肉厚的兔子，想到烤兔子的美味，MM就口水横流。于是他就开始为了丰盛的晚餐开始狂追兔子。狡猾的兔子跑的飞快，而且专挑有着尖头的石头堆跑。MM很倒霉，踩到了一块儿锋利的石头，脚被割破了。疼的嗷嗷叫的MM心想：回头儿我要弄个东西裹住脚，以后再也不让石头割破脚。于是，第一双鞋就这么诞生了。

上面的故事纯属杜撰，务必别当真。故事中，MM在脚受伤时产生了一个改善型问题：要弄个东西裹住脚，不让脚被石头割破。解决这个改善型问题的过程中，鞋子诞生了。也就是说，鞋子可以定义为：*解决光脚走路容易受伤的问题。*

随着生产力和生活条件的提高，人们对于鞋子也出现了更多的改善型需求，于是出现了各种各样的鞋子。比如现在我们生活中的皮鞋＆高跟鞋（美观、正式场合）、拖鞋（居家、浴室）、运动鞋（舒适、运动）、钉鞋（踢球）、登山鞋（爬山）等等。


**从问题的视角来看，我们日常生活中接触的绝大多数东西，都是为了解决特定问题（需求）而存在，可以按照解决的问题来定义。**

举几个例子，

- 鞋子的定义：为了解决光脚走路容易受伤的问题
- 梳子的定义：为了解决头发乱糟糟不好整理的问题
- 被子的定义：为了解决睡觉保暖的问题

*注意：事物的定义必须以事物所处时期的面临的改善型问题为准，比如衣服在原始社会可能只是为了解决取暖的问题，但是在现代社会，就要解决更多的改善型问题，比如美观、舒适、轻便等等。*

如果深入去思考，我们身边随便的一个东西，都可能会牵扯到一个古老的年代和若干改善型问题和异常型问题。

>**人类社会的发展史，伴随的是解决无数问题的过程。**


- 对人类社会而言，解决的问题越多、层次越高，人类社会的发展水平就越好。
- 对个人而言，解决问题能提升个人能力，能解决的问题层次越高、个人的发展就越好。（稍后会有章节详细说明）

***PS：从问题的视角来看架构的定义：架构是为了解决将现实需求转换为软件实现的问题。再回过头去看前面提到的架构的本质，就会好理解很多。***

# 6. 总结

总结一下，本文主要阐述了以下观点：

- 问题的定义：目标和现状有差异
- 问题的分类：异常型问题和改善型问题
- 问题的视角：生活中绝大多数东西都是为了解决特定问题（需求）而存在，可以按照解决的问题来定义
- 问题的重要性：人类社会和个人的发展都是伴随着无数问题的解决，解决问题的层次越高，发展越好
- 问题视角的架构定义：架构是为了解决将现实需求转换为软件实现的问题

《关于架构的思考(二)》中会详细阐述如何解决问题。

