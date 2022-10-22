# Invoke-Ladon
Invoke-Ladon





## 前言：

之前使用Ladon的Powershell版本的时候似乎不能把扫描内容输出到txt文本中，因此我对它做了一点小小的修改。

使用Gzip-compress 和 base64-Encode 转换Ladon的二进制文件然后base64编码解码 并通过[System.Reflection.Assembly]::Load($DecompressedDecodedBinary)在powershell中加载Ladon的二进制文件



## 使用方法：

注意参数中需要加双引号



#### 1.扫描在线主机

```
iex(iwr -UseBasicParsing https://raw.githubusercontent.com/INotGreen/Invoke-Ladon/main/Invoke-Ladon.ps1);
invoke-ladon "192.168.1.8/24 OnlinePC" > OnlinePC.txt
```

![image-20221022163749096](C:\Users\Old Green\AppData\Roaming\Typora\typora-user-images\image-20221022163749096.png)



#### 2.扫描漏洞MS17017



```
iex(iwr -UseBasicParsing https://raw.githubusercontent.com/INotGreen/Invoke-Ladon/main/Invoke-Ladon.ps1);
invoke-ladon "192.168.1.8/24 MS17010" > MS17010.txt
```

![image-20221022164026849](C:\Users\Old Green\AppData\Roaming\Typora\typora-user-images\image-20221022164026849.png)



具体使用方法请参考：https://github.com/k8gege/Ladon

或者直接把调用命令放在脚本最后一行

![image-20221022164515686](C:\Users\Old Green\AppData\Roaming\Typora\typora-user-images\image-20221022164515686.png)

### 总结

使用某些方法可以封装powershell的脚本，让powershell在内存中运行，以此规避一些防病毒软件的查杀，这样就防止从Ladon的源码进行免杀处理的操作
