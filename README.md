## 汇总报告 👋

**尊敬的老师与助教老师们，你们好！**

最终提交的是本账号的网站地址，该账号将每个project作为一个单独的仓库进行说明和呈现，每个project的报告和代码一并放在仓库中，仓库名即为对应的项目名。
（若项目错序，可在右上方Sort处按Name排序即可按顺序查看每个project）

**人员分工表**

第87组

小组成员：

梁育彬（本人） 202100180118 完成所有项目（除重复的project20）



## Project实现方式及效果

### Project1 implement the naïve birthday attack of reduced SM3

使用了多线程优化提高攻击速度。  
（运行结果及时间截图见仓库内截图）  
加入多线程优化前运行时间：32bit-14.63s  
加入多线程优化后运行时间：32bit-10.5s  
优化效果：提速40%  

### Project2 implement the Rho method of reduced SM3

用hash_buf将初值的一次哈希值存储下来，然后用hash_buf2存储二次哈希值  
之后不断循环对hash_buf和hash_buf2中的值进行哈希，直到找到和一次哈希值相等的值  
（运行结果及时间截图见仓库内截图）  
8比特的碰撞运行时间：9ms  
16比特的碰撞运行时间：769ms

### Project3 implement length extension attack for SM3, SHA256, etc

按照常规长度扩展攻击方法进行攻击  
代码将多步操作集成到了length_extend_attack函数中便于调用和调试  
实验结果输出伪造的消息和时间  
（运行结果及时间截图见仓库内截图）
sm3长度扩展攻击需要0.5ms  
sha256长度扩展攻击需要3ms  

### Project4 do your best to optimize SM3 implementation (software)

报告中用文字和图片给出了四个优化方向并详细阐述了原理  
方向一：消息扩展的快速实现  
方向二：预计算常数  
方向三：优化压缩函数中间变量的生成过程  
方向四：对压缩函数进行结构性调整  
（运行结果及时间截图见仓库内截图）  
加密2^10KB文件用时115.266ms  
最后对比了初始实现方案、优化后实现方案和openssl中的sm3库的运行效率  
<img src="https://github.com/1-14/Project04/blob/main/%E6%88%AA%E5%9B%BE/2.png" width="400"  /><br/>

### Project5 Impl Merkle Tree following RFC6962

实现了默克尔树  
参考多篇论文、博客，在报告中详细介绍了存在性证明和不存在性证明的原理  
参考多篇论文、博客，用代码验证了存在性证明（验证一个节点在树中）、验证了不存在性证明（验证一个节点不在树中）  
（运行结果及时间截图见仓库内截图）  

### Project6 impl this protocol with actual network communication

报告中详细介绍了"Range Proofs from Hash Functions" 这一方案的原理  
按照方案原理使用Java代码实现了"Range Proofs from Hash Functions" 

### Project7 Try to Implement this scheme

报告中使用图文详细阐述了Generalizing Hash Chains的原理  
代码按以下步骤实现了Generalizing Hash Chains：  
1.哈希链结构，定义哈希函数（SHA256），然后构建多级哈希链和分层哈希链；  
2.哈希链部分完成后构建Merkle Tree， 为每个Merkle Tree节点附加Generalizing Hash Chains的特性。  
3.最后每个节点上构建Generalizing Hash Chains，形成多级哈希链。  

### Project8 AES impl with ARM instruction

通过网上查阅资料，给出了三种基于ARM64指令的AES软件实现  
1.基于标量实现的aes_scalar.cpp  
2.使用ARMv8的NEON SIMD指令实现的aes_neon.cpp  
3.使用位切片算法实现的aes_bitslice.cpp  
报告中给出了是三种实现方法的原理和关键步详细解释  
实现效果：  
使用 gcc 11.3.0 for Ubuntu 编译，使用 -O3 优化级别。 在 11代Intel Core i7 CPU上执行。 每个基准测试包括在 100 个数据块上完成的**8000000**轮加密。  
aes_scalar：22 秒  
aes_neon：16 秒  
aes_bitslice：12 秒

### Project9 AES / SM4 software implementation

**SM4**  
报告中图文并用详细介绍了SM4的工作标准、原理、加解密流程、密钥扩展算法及各个部件  
在代码中对各个部件进行集成，实现了统一的加解密函数  
加解密时间均在63ms左右  
**AES**  
报告中图文并用详细介绍了SM4的工作标准、原理、加解密流程、密钥扩展算法及各个部件  
在代码中对各个部件进行集成，实现了统一的加解密函数并且可以自由选择工作模式    
详细展示了雪崩效应  
图文并用详细说明了各工作模式  
代码实现了各工作模式的加解密  
加密时间在2ms左右  
解密时间在9ms左右  

### Project10 report on the application of this deduce technique in Ethereum with ECDSA

详细介绍了ECDSA的标准、原理、应用  
对签名过程和验证过程分别进行了数学原理的阐述  
对ECDSA的安全性进行了讨论  
列举了ECDSA在以太坊中的四个应用：  
1.交易签名  
2.账户地址  
3.智能合约  
4.代币交易  

### Project11 impl sm2 with RFC6979

详细介绍了ECDSA的标准、原理、应用  
详细介绍了SM2加密和签名认证的标准、原理、应用  
图文并用对SM2加解密、签名过程和验证过程分别进行了理论依据的阐述  
由于代码过长，根据功能对代码进行了分割并分块提交，提供了代码运行指导  
代码文件如下：  
ECC_class.py  
ECDSA.py  
Main_Part.py  
SM2_class.py  
complete submission.py  
key_Enc_test.py  
security_parameter.py  
complete submission是所有工作量的集合版  

对于SM体系下的椭圆曲线加解密体系，实现了一个ECC—class,椭圆曲线密码类（实现一般椭圆曲线的运算，不局限于SM2）  
对于SM2-class，则是调用了ECC—class作为底层运算部件，根据RFC6979协议标准实现。该方案进行了基础性的ECDH正确性测试，SM2密钥协商测试，SM2数字签名与验证测试，测试过程均在key-Enc-test文件中可运行。  
最后main_part运行结果，可复现RFC6979，SM2文档中的示例结果（达到要求）  
实现效果：  
ECDH密钥协商耗时7.54ms  
SM2密钥协商耗时21.04ms  
SM2签名、验证耗时7.03ms
SM2加解密耗时6.80ms  

### Project12  verify the above pitfalls with proof-of-concept code

报告阐述了泄漏随机数k导致私钥d的泄漏的原理、并使用代码实现了攻击  
报告阐述了随机数k重用导致私钥d泄漏的原理、并使用代码实现了攻击  
报告阐述了两名用户使用同样的随机数k，导致用户之间可以互推出对方使用的私钥d的原理、并使用代码实现了攻击  
报告阐述了在ECDSA签名和SM2签名中使用相同的私钥d和随机数k，导致私钥d泄漏的原理、并使用代码实现了攻击  
最后展示了实现的效果，四种情况均可以求解出随机生成的私钥d  

### Project13 Implement the above ECMH scheme

给出了实现ECMH方案的思路  
给出了UTXO Commitment的两种实现方式、并对安全性进行了讨论  
给出了ECMH实现的具体过程  
使用代码实现了ECMH方案  

### Project14 Implement a PGP scheme with SM2

图文并用介绍了PGP  
具体算法由SM2和SM4共同实现  
代码使用gmssl库中的SM2和SM4，实现SM2和SM4加密解密，并定义PGP_enc和PGP_dec直接实现整个系统的加密解密  
最终成功解密出密钥和密文  

### Project15 implement sm2 2P sign with real network communication

图文并用详细介绍了SM2 2P sign签名方案、结构及原理  
对关键代码进行了展示  
代码实现了该方案、并给出了Alice.py和Bob.py的代码各部分的解释（如：交换公钥、签名）
展示了实现结果的截图  

### Project16 implement sm2 2P decrypt with real network communication

图文并用详细介绍了sm2 2P decrypt解密方案、结构及原理  
对关键代码、参数进行了展示  
代码实现了该方案、并给出了Alice.py和Bob.py的代码各部分的解释（如：交换公钥、签名）  
展示了实现结果的截图 

### Project17 比较Firefox和谷歌的记住密码插件的实现区别

从两个浏览器的密码插件记住密码、填充密码、存在的问题三个部分进行了讨论，分别给出了具体实现原理和问题解释  
对具体实现的原理进行了分别阐述  

### Project18 send a tx on Bitcoin testnet, and parse the tx data down to every bit, better write script yourself

参照网上资料和自己摸索，在报告中按步骤给出了比特币交易（测试版）的实现流程及当时实现的截图  
给出了测试网站的收款地址及测试方法  
给出了查看交易信息的方法  
给出了在查看交易信息时查看API接口的具体方法，由API接口中的交易数据可对交易进行更深入的分析  

### Project19 forge a signature to pretend that you are Satoshi

给出了ECDSA未检查签名邮件时，伪造合法签名的原理和实现代码  
给出了代码运行指导  
对代码中关键部分进行了展示：  
1. ECDSA——sign  
2. ECDSA——vrfy
3. 泄露k导致密钥泄露  
4. 重用k导致密钥泄露  
5. 使用相同k，可互相计算密钥   
6.不验证m的验证算法   
7.伪装攻击者身份，被认定为Satoshi   
8.Schnorr_Sign签名   
9.Schnorr_Sign签名、ecdsa签名使用相同的d，k，导致密钥泄露
最终给出了运行结果的截图

### Project20 ECMH PoC

（重复项目）  
参考Project13  

### Project21 Schnorr Bacth

给出了Schnorr签名的数学原理介绍  
展示了Schnorr签名算法的可视图、并介绍了 Schnorr 签名的好处  
给出了Schnorr签名的签名流程、批量验证的原理  
代码实现了签名验证流程、批量验签流程  
截图展示了实现效果

### Project22 research report on MPT

给出了Merkle Patricia Trie方案研究报告  
图文并用详细介绍了Merkle Tree原理和Merkle Patricia Trie原理  
阐述了Merkle Patricia Trie不同Trie路径所对应的key类型
参考其他论文和文章，给出了构建思路和详细解释  
详细介绍了Child Trie的数据结构、状态保存方式、以及在智能合约中的作用
通过代码实现了Merkle Tree和Merkle Patricia Trie  
代码文件如下：  
Basic_test.py  
Branch_node.py  
Extention_node.py  
Leaf_node.py  
MPT_class.py  
Node_class.py  
代码作用如名称所示  

## 汇总报告结束，感谢您的耐心阅读！！
