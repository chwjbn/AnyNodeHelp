# Anynode虚拟机编程语法-002
## 虚拟机内置库函数列表
1. 应用
```
//获取当前应用运行目录
string System.Application.BaseDirectory()

//获取当前应用文件名称
string System.Application.FileName()

//获取当前应用安装目录
string System.Application.GetAppInstallDirectory()

```
2. 文件目录

```
//指定path的目录是否存在
bool System.Directory.DirectoryExists(string path)

//创建指定的path路径的目录,如果父目录不存在也会一并创建
bool System.Directory.DirectoryCreate(string path)

//删除指定的path路径的目录，不是强制删除
bool System.Directory.DirectoryDelete(string path)

```

3. 文件

```
//指定path的文件是否存在
bool System.File.FileExists(string path)


//删除指定的path路径的文件
bool System.File.FileDelete(string path)

//重命名文件
bool System.File.FileRename(string oldPath,string newPath)


//复制文件
bool System.File.FileCopy(string srcPath,string desPath)


//一次性读取指定path文件的全部文本内容
string System.File.FileReadAllText(string path)

//一次性写入文本到指定path的文件中
string System.File.FileWriteAllText(string path,string content)

```

4. 字符串

```
//查找第二个字符串在第一个字符中第一出现的位置，位置从0开始，如果不存在，返回-1
int System.String.IndexOf(string strData,string subStrData)


//查找第二个字符串在第一个字符中最后一次出现的位置，位置从0开始，如果不存在，返回-1
int System.String.LastIndexOf(string strData,string subStrData)

//第一个字符串是否包含第二个字符串
bool System.String.Contains(string strData,string subStrData)


//截取字符串从fromIndex到toIndex索引的子字符串，索引从0开始
string System.String.SubString(string strData,int fromIndex,int toIndex)

//去除第一个字符串头尾为第二个字符串的内容
string System.String.Trim(string strData,string subStrData)

//字符串替换，在第一个参数字符串中用把第二个参数字符串内容替换成第三个参数字符串内容
string System.String.RelaceAll(string strData,string oldStr,string newStr)

//字符串长度
int System.String.Length(string strData)

//数字转换为字符串
string System.String.NumberToString(number data)

//字符串转换为数字
number System.String.StringToNumber(string data)

//json格式的字符串反序列化为lua的table类型
table System.String.JsonToTable(string jsonData)

```

5. 进程

```
//运行一个文件并带上参数创建一个进程，返回错误信息和进程ID
(string ResultErr,string ResultPid) System.Process.RunProcess(string filepath,string runArg)


//运行命令行，传入命令行和最大允许运行时间(单位秒),返回命令行错误和标准输出，如果命令行超过最大允许时间会被主动kill
(string xResultErr,string xResultData)System.Process.RunCommandWithTimeOut(int timeout,string cmdLine)


```
举例:

```
local errData,retData=System.Process.RunCommandWithTimeOut('ps aux',60)
print(errData)
print(retData)

```


6. 网络

```

string System.Net.HttpGet(string url)
string System.Net.HttpPostJson(string url,string jsonData)
string System.Net.HttpPostForm(string url,string data)
(int fileSize) System.Net.HttpDownloadFile(string url,string filePath)

```

7. 操作系统

```

//以json格式返回当前操作系统信息
string System.Os.SystemInfo()


//以json格式返回当前操作系统负载
string System.Os.SystemStat()

//获取操作系统名称,windows/linux
string System.Os.GetOsName()

//sleep
string System.Os.Sleep(int millSec)

```

8. 时间

```
//当前系统时间，字符串格式2021-09-06 12:11:12
string System.Time.Now()

//返回当前系统时间秒级unix时间戳
number System.Time.Unix()

//返回UTC时间秒级unix时间戳
number System.Time.UtcUnix()
```

9. 日志

```

//Info级别日志
void System.Log.Info(string logData)

//Error级别日志
void System.Log.Error(string logData)

```

10. 加密

```
//文本md5
string System.Encrypt.Md5(string data)

//文件md5
string System.Encrypt.FileMd5(string filePath)

//base64编码与解码
string System.Encrypt.Base64Encode(string data)
string System.Encrypt.Base64Decode(string data)

//url编码与解码
string System.Encrypt.UrlEncode(string)
string System.Encrypt.UrlDecode(string)

```
