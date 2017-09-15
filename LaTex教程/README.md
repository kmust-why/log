#### LaTex文档的基本结构、编译和调试、命令符号的输入（如%，{..}等等）

1. 用于选择调用那个模板，比如article（用于文章），book（用于书籍），report（用于学术报告），letter（用于信件）:

```latex
\documentclass{article}
```

2. 宏包（类似于C语言中的头文件包含）：

```latex
\usepackage{amsmath} %宏包，美国数学协会
```

3. 正文部分 ：

```latex
\begin{document}
% 正文部分
\end{document}
```

4. 文档中的换行通过空行来实现
5. LaTex中的%号表示注释，若确实需要输出%，则需要在%号前加\进行转移即可。
6. 行间公式需要用两个\$符号，行内公式只需要一个\$符号即可
7. 其中要输出\的是时候，需要输入如下的命令

```latex
$\backslash$
```

#### 文档的层次结构（以book为例）

1. 标题：

```latex
\title{this is my book}
```

2. 书的作者：

```latex
\author{wanghaiyun}
```

3. 在设置完标题和作者之后，还需要执行一行代码才可以显示标题和作者：

```latex
\maketitle
```

4. 其中如果不希望显示日期，可以加上如下的代码：

```latex
\date{}
```

5. 对于书来说，其的层次比较多，part表示部分，chapter表示章节，section表示节，subsection表示节下面的节（注意在{}里面写的内容应该为英文的），其中会自带页眉的信息，可以先不用理会，需要用到后面的宏包：

```latex
\part{第一部分}
\chapter{第一章}
\section{第一节}
\subsection{I like latex}
\section{第二节}

\part{diyibufen}
\chapter{diyizhang}
\section{diyijie}
\subsection{I like latex}
\section{dierjie}
```

6. 添加目录：

```latex
\tableofcontents
```

7. 其中，发现页码并不是从正文部分开始，这个时候只需添加一行代码：

```latex
\mainmatter
```

#### LaTex的列表与表格环境，如何快速导出Excel表格至Latex源文件，enumerate宏包使用（setcounter），tabular，table等

1. 无序列表（其中列表支持嵌套，类似与markdown中的无序列表）：

```latex
\begin{itemize}
	\item this is item1
	\begin{itemize}
		\item this is item1
		\begin{itemize}
			\item this is item1
			\begin{itemize}
				\item this is item1
				\item this is item2
				\item this is item3
			\end{itemize}
			\item this is item2
			\item this is item3
		\end{itemize}
		\item this is item2
		\item this is item3
	\end{itemize}
	\item this is item2
	\item this is item3
\end{itemize}
```

2. 有序列表（其中列表支持嵌套，类似与markdown中的有序列表）：

```latex
\begin{enumerate}
	\item this is item1
	\begin{enumerate}
		\item this is item1
		\begin{enumerate}
			\item this is item1
			\item this is item2
			\item this is item3 
		\end{enumerate}
		\item this is item2
		\item this is item3 
	\end{enumerate}
	\item this is item2
	\item this is item3 
\end{enumerate}
```

3. 如果需要修改有序列表前面的数字，并加粗，改变字体，需要先导入宏包`enumerate`，然后执行以下的代码：

```latex
\begin{enumerate}[\bfseries A.]
	\item this is item1
	\begin{enumerate}[\sffamily a.]
		\item this is item1
		\begin{enumerate}[i.]
			\item this is item1
			\item this is item2
			\item this is item3 
		\end{enumerate}
		\item this is item2
		\item this is item3 
	\end{enumerate}
	\item this is item2
	\item this is item3 
\end{enumerate}
```

4. 如果希望有序列表的第一个字母不是从A开始，而是从C开始，可以执行下面的代码：

```latex
\setcounter{enumi}{4}
```

5. 表格的定义：（其中的{clr}分别表示中间对齐，左对齐，右对齐，\\\是为了区分表格的两行数据，$是为了对单元格内的内容进行区分）

```latex
\begin{tabular}{clr}
223&112&333\\
23&12&33\\
\end{tabular}
```

6. 为表格添加边框：（{|c|l|r|}中的|表示表格的竖线，\hline表示为表格添加横线）

```latex
\begin{tabular}{|c|l|r|}
\hline
223&112&333\\
\hline
23&12&33\\
\hline
\end{tabular}
```

7. 从Excel文件中导入数据到latex中