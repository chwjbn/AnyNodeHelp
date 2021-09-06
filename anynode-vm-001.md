# Anynode虚拟机编程语法-001
## 前言
Anynode客户端内置Lua语言虚拟机，并封装了一系列库函数，具备对操作系统以及远程网络应用的读写的能力。
## 编程语法
### Lua语言编程
Lua 是一种轻量小巧的脚本语言，用标准C语言编写并以源代码形式开放， 其设计目的是为了嵌入应用程序中，从而为应用程序提供灵活的扩展和定制功能。
#### Lua 基本语法
我们可以将 Lua 程序代码保存到一个以 lua 结尾的文件，并执行，该模式称为脚本式编程，如我们将如下代码存储在名为 hello.lua 的脚本文件中：

```
local function doTask()    --定义一个局部函数
  local data=System.Os.SystemInfo()   --获取操作系统信息
  print(data)    --打印
end

doTask()   --运行函数

```

使用 anynode_win.exe/anynode_linux 名执行以上脚本

```
// anynode nodevm [脚本路径] [脚本最长运行时间(秒)]
anynode_win.exe nodevm hello.lua 60
```

输出结果为：

```

[2021-09-06 20:16:09][Info][clientapp.go:68]=======================================anynode client app nodevm begin=======================================
{"app_ver":"202108311532","os_type":"windows","os_arch":"amd64","os_ver":"Microsoft Windows 10 专业版(Version:10.0.18363|CodeSet:936)","host_name":"Cheergo-PC","user_name":"Cheergo-PC\cheergo","cpu_count":4,"cpu_v_count":8,"ram_size":16938340352,"storage_size":511432450048,"network":"(192.168.112.1/24)|(192.168.211.1/24)|(172.16.1.8/24)"}
[2021-09-06 20:16:09][Info][clientapp.go:75]=======================================anynode client app nodevm end=======================================

```

#### 注释
##### 单行注释
两个减号是单行注释:

```
--
```
##### 多行注释

```
--[[
 多行注释
 多行注释
 --]]
```

#### 标示符
- Lua 标示符用于定义一个变量，函数获取其他用户定义的项。标示符以一个字母 A 到 Z 或 a 到 z 或下划线 _ 开头后加上 0 个或多个字母，下划线，数字（0 到 9）
- 最好不要使用下划线加大写字母的标示符，因为Lua的保留字也是这样的

Lua 不允许使用特殊字符如 @, $, 和 % 来定义标示符。 Lua 是一个区分大小写的编程语言。因此在 Lua 中 Anynode 与 anynode 是两个不同的标示符。以下列出了一些正确的标示符：

```
mohd         zara      abc     move_name    a_123
myname50     _temp     j       a23b9        retVal
```
#### 关键词
以下列出了 Lua 的保留关键词。保留关键字不能作为常量或变量或其他用户自定义标示符：

1 | 2 | 3 | 4
--- | --- | --- | ---
and | break | do | else 
elseif | end | false | for
function | if | in | local
nil | not | or | repeat
return | then | true | until
while | goto | | 

一般约定，以下划线开头连接一串大写字母的名字（比如 _VERSION）被保留用于 Lua 内部全局变量。

#### 全局变量
在默认情况下，变量总是认为是全局的。

全局变量不需要声明，给一个变量赋值后即创建了这个全局变量，访问一个没有初始化的全局变量也不会出错，只不过得到的结果是：nil。


```
> print(b)
nil
> b=10
> print(b)
10
>
```

如果你想删除一个全局变量，只需要将变量赋值为nil。

```
b = nil
print(b)      --> nil
```
这样变量b就好像从没被使用过一样。换句话说, 当且仅当一个变量不等于nil时，这个变量即存在。




