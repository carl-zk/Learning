# IO

- [Cmd 新建文件及文件夹](https://blog.csdn.net/disanempire/article/details/79421979)

## 1. 建立文件

### 1. 建立空文件的几种方法

```c#
1、cd.>a.txt
// cd.表示改变当前目录为当前目录，即等于没改变；而且此命令不会有输出。
// >表示把命令输出写入到文件。后面跟着a.txt，就表示写入到a.txt。
// 而此例中命令不会有输出，所以就创建了没有内容的空文件。

2、copy nul a.txt
// nul表示空设备，从概念上讲，它不可见，存在于每个目录中，可以把它看成一个特殊的“文件”，它没有内容；一般可把输出写入到nul，来达到屏蔽输出的目的，如pause>nul，此命令执行效果是暂停，并且不会显示“请按任意键继续. . .”。
// 此例子表示将空设备复制到a.txt，同样创建了没有内容的空文件。

3、type nul>a.txt
此例子表示显示空设备的内容，并写入到a.txt。

4、echo a 2>a.txt
// “2”表示错误输出的句柄，此例中没有错误输出，所以创建了没有内容的空文件。
// 其实>默认都是重定向了句柄1，即标准输出句柄。比如cd.>a.txt，其实就是cd. 1>a.txt。
// 同样，句柄3到9也可以使用在本例中，它们是未经定义的句柄，也不会有输出，如
echo a 3>a.txt。

5、fsutil file createnew d:\a.txt 0
// 使用fsutil创建了一个空文件。

6、copy con a.txt 回车 Ctrl+Z

7、其他命令
// 只要没有输出，并重定向到文件就可以了
```

### 2. 建立非空文件的几种方法

```c#
1、echo a>a.txt
// 最常用的是echo命令，此例子表示把字母a和回车换行覆盖输出到a.txt（如果a.txt原来已有内容则覆盖掉原来的内容），如果追加内容，可以使用>>，如echo b>>a.txt，表示把b和回车换行追加到文件末尾。

2、其他命令的重定向输出，如
type a.txt > b.txt
copy a.txt b.txt
fsutil file createnew d:\a.txt 1
```

## 2. 建立文件夹

```c#
// 建文件夹使用的是md命令，它的另一个写法为mkdir（由MakeDirectory演变而来），格式为：md 文件夹名，其中，文件夹名可以使用带路径的格式。

// 例如：
md d:\test，

// 也可以用
md test

// 在当前路径下建立test文件夹。

// 如果要创建的文件夹带有空格或&，需要用引号把文件夹名括起来，例如：md "test abc"、md "abc&xyz"。如果不使用引号，又会带来什么后果呢？

// 测试的结果是：
// 1、如果文件夹名带空格，那么，md test abc 语句会在当前目录下创建test和abc这两个文件夹；
// 利用这个特点，我们有时候可以收到化繁为简的奇效：

// 如果要创建abc def xyz这三个文件夹，直接使用

md abc def xyz

// 就行了，而无需连写三条md语句。

// 当然，md abc;def;xyz或者md abc,def,xyz 这样的写法也是可以的。
// 2、如果文件夹名中含有&，那么，md abc&xyz 会创建abc这个文件夹，并提示说：'xyz'不是内部或外部命令，也不是可运行的程序或批处理文件，这是因为，&是复合语句的连接符号，它把前后两部分视为两条子语句了。
// 忠告：如果文件夹名含有特殊符号，请不要忘记使用双引号！
// md还有一个比较方便的功能：创建中级目录。也就是说，md a\b\c这样的命令，可以在当前目录下建立文件夹a，然后，在a下建立文件夹b，b之下再建立文件夹c，一气呵成，而无需先md a之后，再cd a，然后md b，再cd b，接着cd b，然后md c。
```