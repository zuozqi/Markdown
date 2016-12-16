---
title: A Latex Project
date: 2016年9月1日12:04:47
categories: 工具
tags: [Latex,模板]  
---

这是在暑假整理的低温等离子体的说明书的latex版，里面用到的东西比较全，可以以后用作参考。

可以在这里获取[源代码](https://github.com/zuozqi/NonThermalPlasma/blob/master/intro.tex)

这是生成的[效果](https://github.com/zuozqi/NonThermalPlasma/blob/master/intro.pdf)

<!--more-->


```Latex
\documentclass[UTF8]{ctexart}
\usepackage{dcolumn}
\usepackage{geometry}
\usepackage{amsmath}
\usepackage{multirow}
\usepackage{graphicx}
\geometry{left=2cm, right=2cm,top=3cm,bottom=4cm}
\title{基于低温等离子体技术的新型高效室内空气净化器的设计说明书}
\author{袁旭东，聂圻春，潘悦 ，左忠琪，王晔，杨恒业， 袁旭君， 陈佳乐 \\ 指导老师： 孙路石 ，王贲 \\ 华中科技大学能源与动力工程学院 \@ 湖北\@ 武汉\@ 430074}
\begin{document}
\maketitle
\newcounter{RomanNumber}
\newcommand{\MyRoman}[1]{\setcounter{RomanNumber}{#1}\Roman{RomanNumber}}
\bibliographystyle{unsrt}
\abstract{本作品主要利用低温等离子体对空气中杂质颗粒的净化功能，来实现对室内空气的高效净化。通过创新性的设计解决了低温等离子体技术局限于电源要求高，会产生臭氧及设备较大致空间利用率低等原因未能在家用空气净化领域得到应用的问题。本产品具有成本相对低廉，效果突出，技术先进的优势。}\\
\noindent{\bf\zihao{-5} [关键词]}低温等离子体 \@ 空气净化 \@ 除尘 \@ 除臭氧 
\section*{\centering{作品内容简介}}
\paragraph{}
空气净化器是指能够吸附、分解或转化各种空气污染物（一般包括粉尘、PM2.5、花粉、异味、甲醛之类的装修污染、细菌、过敏原等），有效提高空气清洁度的产品。与工业废气相比，室内污染物的无处理排放越来越成为大气污染的又一大危害，人们对室内污染物的排放长期处于忽视状态。室内空气净化器净化方法有过滤法、静电法或多者组合等，这些传统的室内空气净化器能够单独去除各种粉尘或有机物，但是几乎都只能脱除健康性污染物，而对室内生活污染物中大气污染物没有脱除能力，功能存在局限。
\paragraph{}
本作品在一般空气净化器的预处理过滤模块、核心污染物去除模块，尾气处理或在重过滤的基本环节上，采用预处理模块，低温等离子体发生和作用模块，尾气处理模块，尝试将低温等离子体技术引入室内空气净化领域，利用低温等离子在外加电场的作用下，介质放电产生的等离子体中大量的活性电子、离子等轰击污染物分子使其电离、解离和激发，引发了一系列复杂的物理、化学反应，打开污染物分子之间的分子键，使复杂大分子污染物转变为简单小分子安全物质（如二氧化碳和水），或使有毒有害物质转变为无毒无害或低毒低害物质，并能有效地清除病毒和细菌，从而使污染物得以降解去。该方法去除效率高，去除彻底；同时在尾气处理部分安装风机，方便控制出风速度。
\paragraph{}
当今低温等离子体技术除尘范围广，效率高，这片未被开垦的处女地无疑会为室内空气净化领域指导新的方向。\\
\noindent{\bf\zihao{-5} 联系人：} 袁旭东 \\
\noindent{\bf\zihao{-5} 联系方式：} 15927240820 \\
\noindent{\bf\zihao{-5} E-mail：} 975388030@qq.com\\
\bigskip
\section{背景介绍}
\paragraph{}
近年来，室内空气污染物对人体健康的危害已经越来越多的得到了广大群众的关注，PM2.5、甲醛、$NO_x$、$SO_2$等名词已经与健康问题挂勾。媒体也报道了大量因室内空气污染物导致的恶性事件，室内空气污染物的危害已经成为不可忽视的问题。
\paragraph{}
与越来越火热的健康问题相比，室内生活污染物排放几乎没有受到任何重视。\cite{ZLX2008}
\begin{table}[htbp]
\centering
\caption{上海地区民用建筑甲醛与TVOC污染现状调查}
\begin{tabular}{cccccccccc}
\hline
地点 & 样品数 & 甲醛范围 & 甲醛浓度 & 超标份数 & 超标率 & TVOC范围 & TVOC浓度 & 超标份数 & 超标率 \\
\hline
住宅 & 215 & 0.01-0.32 & 0.71 & 43 & 20.0\% & 0.1-6.6 & 0.40-0.69 & 23 & 10.7\% \\
酒店公寓 & 43 & 0.05-0.15 & 0.096 & 16 & 37.2\% & 0.1-1.5 & 0.50-0.34 & 19 & 39.5\% \\
幼儿园 & 18 & 0.05-0.15 & 0.082-0.035 & 5 &27.8\% & 0.1-0.5 & 0.24-0.12 & 0 & 0 \\
医院 & 13 & 0.03-0.18 & 0.087-0.045 & 4 & 30.8\% & 0.1-0.4 & 0.26-0.07 & 0 & 0 \\
\hline
 \end{tabular}
 \end{table}
\paragraph{}
当今市场上的室内空气净化器几乎都只能脱除健康性污染物，而对室内生活污染物中大气污染物没有脱除能力。
\paragraph{}
利用低温等离子体中的高能电子（0—10 eV）参与形成的物理、化学反应过程，通过这些物理化学过程可以达到对大多数污染物的脱除。其具体过程为：低温等离子体中高能电子，通过非弹性碰撞使分子激发、离解和电离产生许多高活性的自由基或基态原子等活性基团，从而为各类反应提供有利条件，实现在室温条件下化学反应和能量的有效利用。
\paragraph{}
本作品就是在这样的背景下设计的，类比于低温等离子体脱除工厂烟气中污染物的效率保守计算，无疑低温等离子体技术脱除烟气中污染物适合世界环境治理现状，将在世界污染治理研究领域占有重要地位。然而局限于电源要求高，会产生臭氧及设备较大致空间利用率低等原因未能在家用空气净化领域得到应用。本产品利用通过创新性的方法尝试解决了上述问题，并转化为产品将低温等离子体技术引入家居空气污染物净化领域，在解决传统净化器缺陷问题的同时提出新的空气净化手段。\cite{HMH2013}
\section{系统结构设计原理}
\paragraph{}
该空气净化器按照空气流动顺序划分为预处理模块、低温等离子体发生器模块、尾气处理模块。预处理模块作用是将室内空气中的大颗粒物，某些细菌和部分小颗粒分子污染物脱除；低温等离子体发生器模块通过产生的低温等离子体将空气中甲醛、$NO_x$、$SO_2$和异味等有机物进行分解；尾气处理模块去除低温等离子装置产生的臭氧，同时对经过前面两次处理后的产物进行再过滤。如图1所示。
\begin{figure}
\centering
\includegraphics[scale=0.45]{zhengtim.png} \qquad
\includegraphics[width=0.4\textwidth]{zhengtip.png}
\caption{低温等离子体装置的整体框架}
\end{figure}
\subsection{预处理模块}
\paragraph{}
预处理模块主要由底座环网状进风口、活性炭过滤网、HEPA过滤网组成。通过将底座全部设计成网状环形进气口大大的增加了进风面积，从而提高了进风效率；活性炭网可进行基础的物理与化学吸附，在一定风量下，活性炭过滤网可以除臭、除异味，以及大颗粒物；而HEPA可除去0.3mm以上的颗粒物作为最后一层预处理网，HEPA过滤网去除活性炭过滤网未去除的小颗粒物，如烟雾、灰尘以及细菌等污染物，去除率达99.7\%。其结构示意图如图2所示。
\begin{figure}
\centering
\includegraphics[scale=0.6]{prem.png}
\qquad
\includegraphics[width=0.4\textwidth]{prep.png}
\caption{低温等离子体装置的预处理模块}
\end{figure}
\subsection{低温等离子发生器模块}
\paragraph{}
本部分是设备的核心部分，主要由低温等离子体产生装置，电源模块组成。本项目采用介质阻挡放电方法产生大量低温等离子体，将未处理的核心污染物NOx、SO2及某些性质不太活泼的有害有机物去除掉。该低温等离子去除污染物的基本过程主要有以下四点：
\begin{enumerate}
 \item 高能电子的直接轰击
 \item 氧原子或臭氧的氧化
 \item OH自由基的氧化
 \item 分子碎片+氧气的反应
\end{enumerate}
\paragraph{}
这些产生的高能电子、离子、自由基和激发态分子等，可以与污染气体大部分物质发生反应，使污染物质在极短的时间内发生分解，并发生后续的各种反应以达到降解污染物的目的。
\paragraph{}
为了更高效率的产生低温等离子体，项目组将管式发生器创造性的设计成六边形，相对于以往研究中的平板式和圆筒式，六边形管较大的提高了空间利用率，从而提高了低温等离子体的产生效率。其结构示意图3如下：
\begin{figure}
\centering
\includegraphics[scale=0.45]{genm.png}
\qquad
\includegraphics[width=0.4\textwidth]{genp.png}
\caption{低温等离子体装置的发生器模块}
\end{figure}
\subsection{尾气处理模块}
\paragraph{}
该模块的作用是臭氧的处理与污染物的再次处理。由风机、臭氧脱除装置组成。风机安装尾部，气流下进上抽保证了进风的高效性；臭氧脱除装置去除臭氧，同时增加过滤网对去除气体进行二次处理。如图4所示。
\begin{figure}
\centering
\includegraphics[scale=0.55]{exhp.png}
\qquad
\includegraphics[scale=0.75]{exhm.png}
\caption{低温等离子体装置的尾气处理块}
\end{figure}
\section{计算与实验}
\subsection{风机的选型}
\subsubsection{出风风量计算}
\paragraph{}
本空气净化器适用房间面积为,高度为，根据国际标准，空气净化器需要内在其使用面积内换气次，可以计算出风量.
\[ Q = 40 \times \frac{2.8}{\frac{12}{60}} \]
\subsubsection{风道压降计算}
\paragraph{}
风道中的阻力主要由管道阻力、局部压损、滤网阻力三部分构成，计算公式为\cite{YWS2005}
\begin{equation}
   \delta P = \delta P_m + \delta P_j + \delta P_g
\end{equation}
$\delta P_m$,管道压力，单位$P_aa$；$\delta P_j$，局部压力，单位$P_a$；$\delta P_g$，滤网压降，单位$P_a$。
管道压降计算公式为
\begin{equation}
\delta P_m = y h_m l
\end{equation}
\begin{equation}
h_m= \lambda d \frac{u^2}{2}
\end{equation}
式中$y$为修正系数，取1.4；$h_m$为单位长度管道阻力；$l$为管道长度；$\lambda$为摩擦系数；\\
代入数据可计算得： $\delta P_m = 10.4 P_a$
\begin{figure}
\centering
\includegraphics[width=0.3\textwidth]{fengdao.png}
\caption{风道及风机示意图}
\end{figure}
局部压损主要包括管道的分流、弯头、管道变径等，局部的压损计算公式为
\begin{equation}
P_j = \xi \frac{\rho \nu^2}{2}
\end{equation}
式中，$\xi$为局部阻力系数；$\rho$为空气密度；$nu$为风俗；\\
由于设计的风道中无分流、弯头等部分，此部分压损可忽略；查阅资料可得各滤网的风阻,代入公式可计算$\delta P_g = 92 P_a$。根据公式(1),可计算得
\[ \delta P = 92 + 10.1 = 102.4 P_a \]
\subsubsection{风机相关参数计算}
风机的风量计算公式
\begin{equation}
Q_f = k_1 Q
\end{equation}
$k_1$为风量附加系数，$Q$为系统风量。
风机的风压计算公式
\begin{equation}
P_f = k_1 P
\end{equation}
$k_2$为风压附加系数，$P$为风道内总压力。
风压计算误差较大，$k_1$取1.05,$k_2$取1.3
\[ Q_f = 560 \times 1.05 = 735 m^3 \slash h 
\]
 \[  P_f = 102.4 \times 1.3= 133.12 P_a \]
综合考虑风机的风量与风压，选择使用最大风量为$ 750 m^3 \slash h$,最大压力超过135$Pa$的风机，由于在室内使用，还需考虑风机的大小以及噪音。
\subsubsection{电源功率计算}
U-Q Lissajous 图形法：
\begin{equation}
I= \frac{dQ}{dt}= \frac{dC_M V_M}{C_M} \frac{dV_M}{dt}
\end{equation}
式中，$C_M$ 为附加电容，$V_M$ 为附加电容两端的电压。
\begin{equation}
P = \frac{1T} \oint_0^T VIdt = \frac{C_M}{T} \oint_0^T V \frac{dV_M}{dt} dt = f C_M \oint V d V_M
\end{equation}
式中，$f$ 为电源频率， $\oint V d V_M$ 为电压-电荷李萨如图中对闭合曲线的积分。\\
可将对闭合曲线的积分变换为求其面积比例如下式：
\begin{equation}
P = f C_M k_x k_y k A
\end{equation}
式中，$f$ 为电源输出频率，取8.1$kHz$, $C_M$取0.47 $\mu F$ ，$k_x$,$k_y$为$x$,$y$对应的灵敏度，$k$为分压比， 取1000， $A$为闭合曲线在图形中所占的格数，取最佳电压参数计算功率有：
\begin{align*} 
P = {} &f C_M k_x k_y k A \notag \\
={} & 8.1 kHz \times 0.47 \mu F \times 2 V \times 200 mV \times 1000 \times 220.44 \slash 7.1^2 \notag \\
={} &6.67W \notag
\end{align*}
\subsection{臭氧过滤网的选择}
\paragraph{}
根据 $GB/T 18202-2000$中华人民共和国国家标准室内空气中臭氧卫生标准，室内空气中臭氧浓度不允许超过$0.1 mg \slash m^3$.
\paragraph{}
DBD等离子体发生器产生臭氧的量与放电电压、放电时间长短、介质材料、放电间隙宽度等因素.查阅相关的论文资料(如下表)\cite{CYM2005}\cite{ZHS2005}
\begin{table}[htbp]
\centering
\caption{臭氧产生量与风速、时间的关系}
\begin{tabular}{|c|c|c|c|c|c|c|}
\hline
\multirow{2}*{时间 (h)} & \multicolumn{2}{c|}{强风} & \multicolumn{2}{c|}{中风} & \multicolumn{2}{c|}{弱风} \\
\cline{2-7}
& \MyRoman{1} 档 & \MyRoman{2} 档 & \MyRoman{1} 档 & \MyRoman{2} 档 & \MyRoman{1} 档 & \MyRoman{2} 档 \\
\hline
0.5 &0.13 &0.06 &0.13 &0.17 &0.11 &0.11 \\
1 &0.11 &0.09 &0.11 &0.21 &0.09 &0.13 \\
2 &0.13 &0.06 &0.13 &0.19 &0.11 &0.13 \\
4 &0.09 &0.09 &0.11 &0.17 &0.09 &0.15 \\
6 &0.11 &0.11 &0.13 &0.17 &0.09 &0.17 \\
8 &0.13 &0.11 &0.13 &0.17 &0.09 &0.09 \\
10 &0.12 &0.09 &0.12 &0.18 &0.10 &0.13 \\
\hline
出风口处  &0.88 &0.86 &0.77 &1.05 &0.58 &0.90 \\
\hline 
\end{tabular}
\end{table}
\paragraph{}
结果表明,在8 $h$内$O_3$浓度波动只有1\%～2\%,变化幅度不大,说明$O_3$浓度并不随净化时间的延长而增加,而是保持在一个相对稳定的数值上;在出风口处测得的$O_3$浓度较高, $0.58 mg \slash m^3  \sim  1.05mg \slash m^3$,高出室内浓度的$7 \sim 10$倍。
考虑实验中使用的参数与此空气净化器使用的参数有些不同，取$C=1.5mg\slash m^3$；
所以选择臭氧过滤网的过滤效率$\eta = \frac {1.5-0.1}{1.5}=93.3\%$.




\section{创新点分析}
\paragraph{}
本产品所使用的该技术现已在工业烟气中污染物脱除上得到较广泛的应用，但因电源要求高，会产生臭氧及设备较大导致空间利用率低等原因迟迟未能在家用空气净化领域得到应用。本作品通过对电源创新性的组装与设计，采取模块电源，使得较为廉价的电源通过转换便可作为产生低温等离子体的高能电源使用；结合使用高效催化剂及臭氧脱除网，解决了现阶段在工厂中较难解决的臭氧产生问题；而团队首创的将低温等离子体发生器做成六边形管状结构（低温等离子体发生器一般设计成平板式或圆柱管式）的创意，在不牺牲效率的前提下极大的提高了空间利用率。
\paragraph{}
低温等离子体技术是近年来才被引入空气污染物脱除领域的，在对低温等离子体研究所的老师实地访问后我们了解到：即使专门从事低温等离子体技术研究的研究人员也对这一方面的应用了解甚少。由于低温等离子体的作用，使得本作品不仅仅像以往除尘器只能除去甲醛、飞灰等污染物，低温等离子体除尘器将适于除去总悬浮颗粒、飘尘,$PM2.5$,$NO_x$,$SO_2$,汞和有机物。
\section{效益分析}
\begin{table}[htbp]
\centering
\caption{成本分析}
\begin{tabular}{|c|c|c|c|c|c|}
\hline
除尘器类型 & $SO_2 $\@ $NO_2$ & 使用面积 & 保养成本 & 功率 & 价格 \\
\hline
小米净化器 & - & 30 $m^2$ & 149 ￥ \slash 100 天 & 75 W & 899 \\
\hline
Philips AC4076 & - & 40 $m^2 $& 330 ￥ \slash 120 天 &50 W & 2499\\
\hline
SAMSUNG AC505 & - & 40$ m^2 $& 359 ￥ \slash 120 天 & 55 W & 3999 \\
\hline
低温等离子体& √ & 40 $m^2$ & 75 ￥ \slash 120 天 & 77 W & 2200\\
\hline
\end{tabular}
\end{table}
\paragraph{}
对比目前市场上主要售卖的机型，与使用滤芯型技术的小米空气净化器相比虽然本产品价格较小米空气净化器高，但是本产品有明显的效果优势。和同样使用滤芯型技术的菲利普净化器相比，本产品虽然脱除效率与其脱除效率相近，但由于本产品的核心发生器模块不需要替换，故保养成本远小于菲利普净化器。而与三星净化器相比，本产品低廉的价格和对$NO_x$、$SO_2$更高的脱除率成为了本产品的优势。
\section{应用前景}
\paragraph{}
当今世界家居人口数量巨大，室内空气污染物排放量逐年增加，其中大部分家庭都未使用空气净化器或使用的是脱除效率较低的空气净化器，类比低温等离子体技术在工业烟气污染物脱除中的效率，本产品具有惊人市场的潜能。
\paragraph{}
现今空气质量问题逐渐受到广泛关注，特别是在发展中国家，公民的环保健康意识较之前几年有了跨越式的发展，故可以合理推测，空气净化器的市场在未来几年会急剧扩大，国际市场对技术新颖有效价格低廉实惠的空气净化器的需求会呈井喷态势。
\paragraph{}
本作品易于制作，适用范围广，家居、店铺和电梯等空间的空气净化均能胜任。
\bibliography{essay}
\end{document}

\end{letter}
\end{document}
```