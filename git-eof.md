
`遇到了过早的文件结束符EOF时不要着急，我们来看看怎么解决`
### 导言

近期使用git拉取仓库的时候，拉取了好几次都不行，总是反馈说过早的文件结束符

```javascript
fatal: 过早的文件结束符(EOF)
fatal: 无效的index-pack输出
```
总是这样，当然我的报错信息并没有描述完整，因为在我检索此类问题的时候，我发现有好多种所谓的`过早的文件结束符`这样的报错，但是细节部分描述不太一致。

### 问题情景1
比如说，我的完整报错信息是这样的：

```shell
client_loop: send disconnect: Broken pipe | 9.00 KiB/s
fetch-pack: unexpected disconnect while reading sideband packet
fatal: 过早的文件结束符(EOF)
fatal: fetch-pack: 无效的 index-pack 输出
```

关键信息在前两行，前两行告诉我们`发生了某种断开连接， 9.00 KiB/s应该是表示网络速率`，因此可以确定，发生这个问题的原因属于网络部分，**本机连接仓库服务器时网络不稳定** 我把无线网络更换为手机分享的热点之后，再次尝试，问题解决。所以遇到这个问题的时候，要么切换成4G热点或者其他网络，要么可以等待一段时间再尝试。

### 问题情景2
我还看到另一种，我们来看完整的报错信息：

```shell
error: RPC failed; curl 12 tranfer closed with outstanding read data remaining.
fatal: The remote end hung up unexpectedly
fatal: 过早的文件结束符（EOF）
fatal: index-pack失败
```

关键信息是第一行的**curl**,出现这个关键词，基本可以确定是由于远程仓库中存在过大的文件，我们可以扩大一下传输限制

开启`git bash`,然后输入 `git config --global http.postBuffer 1048576 * 10`。当然了，你在设置http的postBuffer值时要参考你的仓库文件大小，我上面 `10485760`是`10MB`的大小限制，满足最大文件的大小即可，除此之外还有另一种方法，可以在`资源管理器 > 用户 > $YOUR_NAME > .gitconfig` 中右键编辑此文件，添加如下内容：
```
[http]（如果没有http这个分类需要添加此行，有的话直接在分类下追加）
     postBuffer = 10485760
```

然后保存，重新拉取，问题解决。

### 总结

由此可见，出现报错时，仔细阅读、分析并理解报错信息是极为重要的，如果你没看明白，一定要**多读几次**，只有读懂了关键信息，才能在下次遇到的时候，得知你们曾经见过面。


