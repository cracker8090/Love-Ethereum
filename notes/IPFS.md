## IPFS

星际文件系统IPFS（InterPlanetary File System）是一个面向全球的、点对点的分布式版本文件系统，目标是为了补充（甚至是取代）目前统治互联网的超文本传输协议（HTTP），将所有具有相同文件系统的计算设备连接在一起。原理用基于内容的地址替代基于域名的地址，也就是用户寻找的不是某个地址而是储存在某个地方的内容，不需要验证发送者的身份，而只需要验证内容的哈希，通过这样可以让网页的速度更快、更安全、更健壮、更持久。

## IPFS如何工作

### 身份验证

　IPFS中，每个节点都会由NodeId（公钥的hash）来标识，节点存储着公钥和加密过的私钥。__首次连接时，节点间交换公钥__，并检查 other.PublicKey　hash运算后的值是否等于other.NodeId。如果不等于，则终止连接。

### 网络

每个节点与网络中的相连的其它数百个节点进行定期通信。

IPFS的网络传输具有如下特性：

* 传输：IPFS可以使用任何传输协议，如WebRTC　和 uTP
* 可靠性：如果底层网络不能保证可靠性，IPFS可以使用uTP或SCTP来保证
* 连接：IPFS　还可以使用ICE NAT穿越技术
* 完整性：使用哈希校验和检查消息的完整性
* 真实性：可以使用发送者的公钥和HMAC来检查消息的真实性

同时IPFS不仅仅是通过IP来连接节点，还支持很多其他协议。IPFS内部使用不同的地址格式来选择不同的网络协议。

### 路由

IPFS　通过基于S/Kademlia 和　Coral 的DSHT来寻找匹配的节点和特定节点的地址信息，IPFS的对象和使用模式的大小类似于Coral 和　Mainline ，因此IPFS DHT 根据其大小对存储的值进行区分。

### 块交换

在IPFS中，通过使用BitSwap 协议与其他节点进行块交换来实现数据分发。BitSwap维持两个列表，分别为想要获得的块和已保存的块。但与BitTorrent 不同的是，BitSwap不限于一个torrent中的块BitSwap节点可以从整个IPFS网络获取所需的块，而不管这些块属于哪些文件，这大大提高了下载效率。

同时，网络中还存在一些激励节点主动缓存和传播稀有的文件片段。

未完......
































