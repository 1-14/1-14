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
