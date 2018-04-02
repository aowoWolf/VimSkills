# gitSkills
## 寄存器
### :reg
查看当前各个寄存器中的内容
> vim中没有所谓删除，实际上都是剪切，黑洞寄存器除外
### 无名寄存器（""）
x、s、d{motion}、c{motion}和y{motion}指令都会覆盖无名寄存器中的内容
### 复制专用寄存器（"0）
使用y{motion}指令时，复制的数据不仅会保存到无名寄存器中，还会在==复制专用寄存器==值保留一份。
> 使用：普通模式下```"0p```，插入模式下```<C-r>0```
### 有名寄存器（"a-"z）
vim提供了一组一26个英文字母命名的有名寄存器

con==t==ent，当前光标在t位置上，使用```"ayiw```可以复制到a寄存器中
> 如果换成大写字母引用的有名寄存器的话，表示对与之对应的小写有名寄存器的内容上的追加

例如：insu==r==ance，执行```"Ayiw```,再执行```:reg```查看寄存器中的内容，可以看到a寄存器中的内容变成了content insurance

### 黑洞寄存器("_)
执行```"_d{motion}```表示vim将删除该文本
### 系统剪贴板("+)与选择专用寄存器("*)
在外部程序中用剪切或复制获取的文本可以通过```"+p```（插入模式下用```<C-r>+```）粘贴到vim内部中。相反地，如果再vim中复制或剪切指令想在外部程序使用，可以在之前加入```"+```。
> 鉴于Windows与Mac OS X操作系统没有主剪贴板的概念，所以```"+```和```"*```可以混合使用，更推荐使用```"+```寄存器。
# 文件
### 分割窗口
普通命令|Ex命令|用途
|:---:|:---:|:---:|
 ```<C-w>s``` | ```:split```、```:sp```|水平切割
 ```<C-w>v``` | ```:vsplit```、```:vsp```、```:vs```|垂直切割

### 窗口切换
命令|用途
|:---:|:---:|
 ```<C-w>w``` | 在窗口键循环切换
 ```<C-w>h``` | 切换到左边的窗口
 ```<C-w>j``` | 切换到下边的窗口
 ```<C-w>k``` | 切换到上面的窗口
 ```<C-w>l``` | 切换到右边的窗口

### 关闭窗口
普通命令|Ex命令|用途
|:---:|:---:|---|
 ```<C-w>c``` | ```:clo[se]```|关闭活动窗口
 ```<C-w>o``` | ```:on[ly]```|只保留活动窗口，关闭其他所有窗口

### 标签打开及移动
普通命令|Ex命令|用途
|:---:|:---:|---|
   ||```:tabe[dit]{filename}```|在新标签页中打开{filename}
 ```<C-w>T``` ||把当前窗口移到一个新标签页
   ||```:tabc[lose]```|关闭当前标签页及其他的所有窗口
   ||```:tabo[nly]```|只保留活动标签页，关闭所有其他标签页
 ```gt``` | ```:tabn[ext]```|切换到下一标签页
 ```gT``` | ```:tabp[revious]```|切换到上一标签页
 ```{N}gt``` | ```:tabn[ext]{N}```|切换到编号为{N}的标签页

# 动作命令

 ### 实际行和屏幕行间的移动
 命令|用途
|:---:|:---:|
 ```gj``` | 向下移动一个屏幕行
 ```gk``` | 向上移动一个屏幕行
 ```g0``` | 移动到屏幕行的行首
 ```g^``` | 移动到屏幕行的行首
 ```g$``` | 移动到屏幕行的行尾
 ```
//下面实际上只有三行，但是因为屏幕宽度不够所以变成了9行，所以9就是屏幕行
 1  This is where the devil goes walking, looking with interest in at
    the window of Dr. Guillotin, who works night and day to perfect 
    his humane killing machine, sharpening his angled blade on the
    innocent necks of sheep.
 2  Little does the earnest doctor know that his new design will be
    center stage, a bloody altarpiece in the drama that is about to
    unfold.
 3  But wait, not so fast. King Louis XVI and his queen, Marie
    Antoinette, are still outside Paris, at Versailles.
 ```
 ### 单词移动
 命令|用途
 |:---:|:---:|
 ge|反向移动到上一单词的结尾
 ==W==|==正向==移动到下一字符串的开头
 ==E==|==正向==移动到当前字符串/下一字符串的结尾
 ==B==|==反向==移动到当前字符串/上一字符串的开头