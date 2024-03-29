# 期末复习

## 1 选择题

需要注意，这部分题目顺序是期中之后的内容在前，期中之前的看情况，大概率期中考过的可能不会再考了（猜的）

### 1.1 下面关于 TCP 滑动窗口机制的描述正确的是 ( )

A. 是 3 位的滑动窗口
B. 仅用于流量控制
C. 传输过程中窗口大小不调整
D. 窗口大小为 0 是合法的

解析：可以直接做出答案的。因为在课件的示例中，可以知道，在传输过程中，可以根据网络环境的变化，对窗口的大小进行 **动态调整**，可以变大，也可以变小甚至小到为 0. 因此选项 D 的说法正确，故答案为 D.

> 用排除法做：
> * 传输过程中，窗口的大小可以调整，是动态变化的，不是一成不变的
> * TCP 滑动窗口机制除了可以用于实现流量控制，还能用于可靠传输
> * 滑动窗口的大小是以字节为单位，并且是可以动态调整其大小的

### 1.2 电子邮件应用程序利用 POP3 协议来做什么？( )

A. 创建邮件
B. 加密邮件
C. 发送邮件
D. 接收邮件

解析：POP3 协议是在接收邮件时使用的协议，所以选 D. 接收邮件还可以使用 IMAP 协议。**使用 SMTP 协议来发送邮件**

### 1.3 下列有关 ASP 和 Javascript 的表述正确是 ( )

A. 两者都能够在 WEB 浏览器上运行
B. ASP 在服务器端执行，而 Javas cript 一般在客户端执行
C. Javas cript 在服务器端执行，而 ASP 一般在客户端执行
D. 它们是两种不同的网页制作语言，在制作网页时一般选择其一

解析：ASP 是网页的一种格式,ASP是「Active Server Page」的缩写，意为「动态服务器页面」；Javascript是一种面向对象的动态类型的区分大小写的 **客户端脚本语言**，主要目的是为了解决服务器端语言。因此，从名称上可以判断，ASP 是服务器端的，而 JavaScript 是客户端的。故选 B.

### 1.4 甲方和乙方采用公钥密码体制实现数据文件加密传送，甲方用乙方的公钥加密数据文件，请问乙方使用什么来对数据文件进行解密？（ ）

A. 甲的公钥
B. 甲的私钥
C. 乙的公钥
D. 乙的私钥

解析：由题可知，采用的是 **公钥密码体制**。甲方使用 **乙方** 的公钥来加密数据文件，则乙方在解密数据文件是就要采用自己的私钥即 **乙的私钥**。故答案选 D.

### 1.5 关于防火墙的功能，下列说法哪项是错误的？( )

A. 防火墙可以检查进出内部网的通信量
B. 防火墙可以使用应用网关技术在应用层上建立协议过滤和转发功能
C. 防火墙可以使用过滤技术在网络层对数据包进行选择
D. 防火墙可以阻止来自内部的威胁和攻击

解析：需要明确一个事实，防火墙试图在入侵行为发生之前阻止所有可疑的通信，但事实是不可能阻止所有的入侵行为。同样，防火墙不能解决来自内部网络的攻击和安全问题。例如,通过发送带木马的邮件、带木马的URL等方式,然后由中木马的机器主动对攻击者连接,将瞬间破坏象铁壁一样的防火墙。因此答案选 D.

> 防火墙技术一般有两类：分组过滤路由器和应用网关
> 分组过滤路由器的过滤规则是基于分组的 **网络层或运输层** 首部的信息，根据过滤规则对进出内部网络的分组执行转发或者丢弃（即过滤），故选项 C 正确
> 在应用网关中，可以实现基于应用层数据的过滤和高层用户鉴别，故选项 B 正确

## 2 名词解释

### 2.1 VPN、VLAN

VPN：虚拟专用网（(Virtual Private Network），利用公用的互联网作为本机构各专用网之间的通信载体，这样的专用网又称为虚拟专用网VPN

> 称为「专用网」是因为这种网络是**为本机构的主机用于机构内部的通信**，而不是用于和网络外非本机构的主机通信
> 「虚拟」是因为并没有真正使用通信专线，而VPN只是在效果上和真正的专用网一样

VLAN：虚拟局域网（Virtual LAN），是由一些局域网网段构成的与物理位置无关的逻辑组，而这些网段具有某些共同的需求

### 2.2 DoS、DDoS

DoS：拒绝服务(Denial of Service)，是指攻击者向互联网上的某个服务器不停地发送大量分组，使该服务器无法提供正常服务，甚至完全瘫痪

DDoS：分布式拒绝服务(Distributed Denial of Service)，从互联网上的成百上千个网站集中攻击一个网站

## 3 简答题

### 3.1 简述在 TCP 协议中连接建立时进行三次握手的应答过程

TCP协议连接建立时的三次握手过程如下：

* 第一次握手，客户端向服务器发送一个SYN包，请求建立连接，并进入 SYN_SENT 状态
* 第二次握手，服务器收到客户端发来的SYN包后，发送ACK确认收到客户端的连接请求，并向客户端发起SYN连接请求，此时服务器进入 SYN_RECV 状态；
* 第三次握手，客户端收到服务器的SYN+ACK包后，发送ACK确认收到服务器的连接请求，此时客户端进入ESTABLISHED状态，当服务器收到客户端的确认后，也进入 ESTABLISHED 状态，完成三次握手

![三次握手](images/2023-06-27-11-08-03.png)

> 补充：为何是「三」次握手？因为三次是保证 `client` 和 `server` 端均让对方知道自己具备发送和接收能力的最小次数
>* client > server：client具备发送能力
>* server > client：server具备接收和发送能力
>* client > server：client具备接收能力

### 3.2 万维网必须解决哪 4 个问题？简述解决这 4 个问题的思路

1. 怎样标志分布在整个互联网上的万维网文档？ 
   
   思路：使用 **统一资源定位符 URL** (Uniform Resource Locator) 来标志万维网上的各种文档，并使每一个文档在 **整个互联网** 的范围内具有 **唯一** 的标识符 URL

2. 用什么样的协议实现万维网上的各种链接？

   思路：在万维网客户程序与万维网服务器程序之间进行交互所使用的协议是 **超文本传送协议 HTTP (HyperText Transfer Protocol)** 。HTTP 是一个应用层协议，它使用 TCP 连接进行可靠的传送

3. 怎样使各种万维网文档都能在互联网上的各种计算机上显示出来，同时使用户清楚地知道在什么地方存在着超链？ 
   
   **超文本标记语言** HTML (HyperText Markup Language) 使得万维网页面的设计者可以很方便地用一个超链从本页面的某处链接到互联网上的任何一个万维网页面，并且能够在自己的计算机屏幕上将这些页面显示出来

4. 怎样使用户能够很方便地找到所需的信息？ 
   
   为了在万维网上方便地查找信息，用户可使用各种 **搜索工具** 即 **搜索引擎**

## 4 解答题

### 4.1 假定 TCP 在开始建立连接时，发送方设定超时重传时间 RTO=7.5 秒

(**提示：诸系数均采用推荐或典型值，即：α=1/8；β=1/4；γ=2**)

(1) 当发送方收到对方的连接确认报文段时，测量出 RTT 样本值为 2 秒。试计算现在的RTO 值

因为是第一次，所以有：

$RTT_S = RTT_1 = 2 s$

$RTT_D = \frac{1}{2} RTT = 1 s $

因此，有 $RTO = RTT_S + 4 RTT_D = 2 + 4 = 6 s$

(2) 当发送方发送数据报文段并收到确认时，测量出 RTT 样本值为 3.5 秒。试计算现在的RTO 值

由公式：$ RTT_S = (1 - \alpha) \times $ (旧的 $RTT_S$) + α × (新的 RTT 样本值) , 得 : $RTT_S$ = 2.1875 s

由公式 : 新的 $RTT_D$ = (1 - β) × (旧的 $RTT_D$ ) + β × | $RTT_S$ - 新的 RTT 样本 | , 得 : $RTT_D$ = 1.078125 s

最后 : RTO = $RTT_S$ + 4 × $RTT_D$ = 6.5 s

(3) 发送方发送数据报文，超时后又重新发送了一次，2.5 秒后收到了确认。试计算现在的RTO 值

因为报文重传了，所以采用公式 : 新的 RTO = γ × ( 旧的 RTO )

所以 新的 RTO = γ × ( 旧的 RTO ) = 13 s

---

补充：利用到的公式如下

$RTT_S$ : 加权平均往返时间，又称为平滑的往返时间，S 表示 Smoothed。每当第一次测量 RTT 样本时， $RTT_S = RTT$. 之后每测量到一个新的 RTT 样本，就用下式更新 $RTT_S$ 

**$ RTT_S = (1 - \alpha) \times $ (旧的 $RTT_S$) + α × (新的 RTT 样本值)**

超时重传时间 RTO 应略大于上面的 加权平均往返时间 $RTT_S$. 使用下式计算 RTO:

**RTO = $RTT_S$ + 4 × $RTT_D$**

而 $RTT_D$ 是 RTT 的偏差的加权平均值，第一次测量时，$RTT_D$ 值取为测量到的 RTT 样本值的一半。在以后的测量中，则使用下式计算加权平均的 $RTT_D$:

**新的 $RTT_D$ = (1 - β) × (旧的 $RTT_D$ ) + β × | $RTT_S$ - 新的 RTT 样本 |**

报文段每重传一次，就把 RTO 增大一些：

**新的 RTO = γ × ( 旧的 RTO )**

当不再发生报文段的重传时，才根据报文段的往返时延更新平均往返时延 RTT 和超时重传时间 RTO 的数值

## 5 作业题

### 第五章 运输层

#### 5-01 试说明运输层在协议栈中的地位和作用。运输层的通信和网络层的通信有什么重要区别？为什么运输层是必不可少的？

地位和作用：运输层处于 **面向通信** 部分的最高层，同时也是 **用户功能** 中的最低层，向它上面的应用层提供服务

重要区别：网络层是为 **主机之间** 提供 **逻辑通信**，而运输层为应用 **进程之间** 提供 **端到端** 的逻辑通信

为何必不可少：各种应用进程之间通信需要「可靠或尽力而为」的两类服务质量，**必须由运输层以复用和分用的形式加载到网络层**

#### 5-08 为什么说UDP是面向报文的，而TCP是面向字节流的？

UDP 是面向报文的：发送方 UDP 对应用程序交下来的报文，在**添加首部**后就向下交付 IP 层。UDP 对应用层交下来的报文，**既不合并，也不拆分**，而是**保留这些报文的边界**。接收方 UDP 对 IP 层交上来的 UDP 用户数据报，在**去除首部**后就原封不动地交付上层的应用进程，**一次交付一个完整的报文**

TCP 是面向字节流的：TCP把应用程序交下来的数据视为一连串无结构的字节流

#### 5-23 主机 A 向主机 B 连续发送了两个 TCP 报文段，其序号分别为 70 和 100。试问：

##### （1）第一个报文段携带了多少个字节的数据？

省流：99 - 70 + 1 = 30

由所学知识可知，序号是指本报文段所发送数据的第一个字节的序号

由题可知，两个报文段的序号分别为 70 和 100，则第一个报文段中的数据是 70 - 99 (100 - 1), 所以第一个报文段携带了 **99 - 70 + 1 = 30** 个字节的数据

##### （2）主机 B 收到第一个报文段后发回的确认中的确认号应当是多少？

省流：100

由所学知识可知，确认号字段是指期望收到对方的下一个报文段的数据的第一个字节的序号，代表在该确认号之前的数据都已经收到了

B 期望收到下一个报文段的第一个数据字节的序号为 100，因此确认号为 100

##### （3）如果主机 B 收到第二个报文段后发回的确认中的确认号是 180，试问 A 发送的第二个报文段中的数据有多少字节？

##### （4）如果 A 发送的第一个报文段丢失了，但第二个报文段到达了 B。B 在第二个报文段到达后向 A 发送确认。试问这个确认号应为多少？

#### 5-33

#### 5-45 解释为什么突然释放运输连接就可能会丢失用户数据，而使用 TCP 的连接释放方法就可保证不丢失数据

当主机 1 和主机 2 之间连接建立后，主机 1 发送了一个 TCP 数据段并正确抵达主机 2，接着主机 1 发送另一个TCP数据段，这次很不幸，主机 2 在收到第二个 TCP 数据段之前发出了释放连接请求，如果就这样突然释放连接，显然主机 1 发送的第二个 TCP 报文段会丢失

而使用 TCP 的连接释放方法，主机 2 发出了释放连接的请求，那么即使收到主机 1 的确认后，只会释放主机 2 到主机 1 方向的连接，即主机 2 不再向主机 1 发送数据，而仍然可接收主机 1 发来的数据，所以可保证不丢失数据

#### 5-46 试用具体例子说明为什么在运输连接建立时要使用三次握手。说明如不这样做可能会出现什么情况

3 次握手完成两个重要的功能，既要双方做好发送数据的准备工作（双方都知道彼此已准备好），也要允许双方就初始序列号进行协商，这个序列号在握手过程中被发送和确认

假定 B 给 A 发送一个连接请求分组，A 收到了这个分组，并发送了确认应答分组。按照两次握手的协定，A 认为连接已经成功地建立了，可以开始发送数据分组。可是，B 在 A 的应答分组在传输中被丢失的情况下，将不知道 A 是否已准备好，不知道 A 建议什么样的序列号，B 甚至怀疑 A 是否收到自己的连接请求分组，在这种情况下，B 认为连接还未建立成功，将忽略 A 发来的任何数据分组，只等待连接确认应答分组。而 A 发出的分组超时后，重复发送同样的分组。这样就形成了死锁

### 第六章 应用层

#### 6-02 域名系统的主要功能是什么？域名系统中的本地域名服务器、根域名服务器、顶级域名服务器以及权限域名权服务器有何区别？

主要功能：将域名解析为主机能够识别的 IP 地址

区别：

* 本地域名服务器：本地域名服务器离用户较近，当一个主机发出 DNS 查询请求时，该查询请求报文就发送给本地域名服务器，若查询的主机属于同一个本地 ISP 时，本地域名服务器就能立即将主机名转换为相应的 IP 地址
* 根域名服务器：根域名服务器是最高层次的域名服务器，管理着顶级域名服务器的域名和 IP 地址
* 顶级域名服务器：负责管理在该顶级域名服务器注册的所有二级域名
* 权限域名服务器：一个服务器所负责管辖的（或有权限的）范围叫做区。各单位根据具体情况来划分自己管辖范围的区，每一个区设置相应的权限域名服务器，用来保存该区中所有主机的域名到 IP 地址的映射。简言之，权限域名服务器是负责一个区的域名服务器

#### 6-05 文件传送协议FTP的主要工作过程是怎样的？为什么说FTP是带外传送控制信息？主进程和从属进程各起什么作用？

主进程和从属进程的作用：一个主进程，负责接受新的请求；另外有若干个从属进程，负责处理单个请求

主要工作过程：FTP 使用客户服务器方式。一个FTP 服务器进程可同时为多个客户进程提供服务。主进程的工作步骤如下：

* 打开熟知端口（端口号为21），使客户进程能够连接上。
* 等待客户进程发出连接请求。
* 启动从属进程来处理客户进程发来的请求。从属进程对客户进程的请求处理完毕后即终止，但从属进程在运行期间根据需要还可能创建其他一些子进程。
* 回到等待状态，继续接受其他客户进程发来的请求。主进程与从属进程的处理是并发地进行

为什么是带外传送控制信息：因为在进行文件传输时，FTP 需要建立两个并行的 TCP 连接即「控制连接」和「数据连接」。控制连接在整个会话期间一直保持打开，FTP 客户发出的传送请求通过控制连接发送给服务器端的控制进程，但控制连接不用来传送文件；实际用于传输文件的是「数据连接」。服务器端的控制进程在接收到FTP 客户发送来的文件传输请求后就创建「数据传送进程」和「数据连接」，用来连接客户端和服务器端的数据传送进程。数据传送进程实际完成文件的传送，在传送完毕后关闭“数据传送连接”并结束运行

#### 6-10 假定要从已知的URL 获得一个万维网文档。若该万维网服务器的Ip 地址开始时并不知道。试问：除HTTP 外，还需要什么应用层协议和运输层协议？

应用层协议：DNS

运输层协议：UDP (由 DNS 使用)、TCP (由 HTTP 使用)

#### 6-23 试简述 SMTP 通信的三个阶段的过程

* 连接建立：连接是在发送主机的 SMTP 客户和接收主机的 SMTP 服务器之间建立的。SMTP不使用中间的邮件服务器
* 邮件传送
* 连接释放：邮件发送完毕后，SMTP 释放 TCP 连接

### 第七章 网络安全

#### 7-01 计算机网络都面临哪几种威胁？主动攻击和被动攻击的区别是什么？对于计算机网络，其安全措施都有哪些？

威胁：计算机网络面临两种威胁分别是**被动攻击** 和 **主动攻击**

区别：主要区别在于攻击者与目标系统交互的方式和对系统资源的影响程度。在被动攻击中，攻击者从网络上截获数据，并不干扰信息流，通常难以被察觉，因为它们对目标系统没有直接的破坏性影响；在主动攻击中，攻击者直接与目标系统交互，试图更改或破坏系统资源、数据或服务，往往会对目标系统产生直接和显著的影响

安全措施：对付被动攻击可采用各种数据加密技术，对付主动攻击则需将加密技术与适当的鉴别技术相结合。具体措施有密钥体制、数字签名、防火墙等

#### 7-07 对称密钥体制与公钥密码体制的特点各是什么？各有何优缺点？

特点：对称密钥体制的加密密钥与解密密钥是相同的密码体制；公钥密码体制使用不同的加密密钥与解密密钥，加密密钥是公开信息，而解密密钥需要保密

优缺点：

公钥密码体制不仅可以用来加密，还可以很方便的用于鉴别和数字签名。但加密解密处理速度慢

对称密钥体制的加解密速度快且安全强度高，但密钥难以管理和传送，不适于在网络中单独使用

#### 7-10 试述数字签名的原理

数字签名技术是将原文通过特定HASH函数得到的摘要信息用发送者的私钥加密，与原文一起传送给接收者。接收者只有用发送者的公钥才能解密被加密的摘要信息，然后用HASH函数对收到的原文提炼出一个摘要信息，与解密得到的摘要进行对比。如果比对结果一致，则说明收到的信息是完整的，在传输过程中没有被修改，否则信息一定被修改过，因此数字签名能够验证信息的完整性