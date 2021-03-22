<h1>Redis</h1>
<h3>数据结构</h3>
<details><summary>1.字符串</summary>
<li>redis中的字符串是动态字符串，叫SDS
  <li><b>redis中用到sds的地方</b>：1.字符串对象：除了字符串值对象外，所有的键值对的键都是字符串对象；2.AOF持久化的输入缓冲区是用SDS实现的
  <li><b>SDS的内部结构</b>：<br>(i) buf数组，是一个char类型数组，记录字符串内容。<br>(ii) free属性，int类型，记录buf数组中没有使用的字节的数量。<br>(iii) len属性记录已经使用的字节数量。
  <li><b>SDS和C字符串的区别</b>：
    <br>(i) C字符串需要<b>O（n）</b>获取字符串<b>长度</b>；而SDS只需要<b>O（1）</b>获取字符串<b>长度</b>。
    <br>(ii) C字符串API操作<b>不安全</b>，可能会造成缓冲区溢出；而SDS API操作<b>安全</b>，因为在修改字符串前，会先判断会不会造成字符串缓冲区溢出，如果会的话就会先扩展字符串再修改。
    <br>(iii) SDS的<b>内存重分配</b>次数比C字符串<b>少</b>，这个得益于两个策略——<br>
     &nbsp&nbsp&nbsp&nbsp &nbsp&nbsp(1) 第一个是空间预分配策略，就是API对字符串进行扩展的时候，会分配额外的未使用空间，分配空间的大小取决于SDS的长度：如果SDS的长度小于1MB，那么分配的大小就是同样长度的字符串len属性的长度；如果SDS的长度大于1MB，那么分配的大小就是1MB。
      <br>&nbsp&nbsp&nbsp&nbsp&nbsp&nbsp(2) 第二个是惰性空间释放策略，API在对字符串进行缩短操作的时候，不会释放空闲的未使用空间，而是通过free属性记录未保存的空间长度，以便进行扩展的时候就不用再重分配空间了。（当然API也支持手动释放未保存空间的操作）
    <br>(iv) SDS buf数组保存的<b>数据类型</b>比C字符串<b>更丰富</b>。C字符串只能保存ASCII数据，且不能保存空字符，C字符串遇到的第一个空字符会被视作字符串的结束标志；而SDS不仅能保存ASCII数据，还能保存空字符，以及图片、音频等二进制数据，更加丰富。
    <br>(v) C字符串相较于SDS字符串的唯一好处是，C字符串能使用<b>全部</b>的<b><string.h></b>库中的函数，而SDS只能兼容<b部分</b><string.h>库中的函数。
</details>
    <details><summary>2.链表</summary>
      <li>Redis中的链表是list结构体，里面有指向表头的指针head，和指向表尾的指针tail，类型是listnode类型。然后还有一个记录所含节点数的len属性，是unsigned long类型的，以及三个成员函数：dup复制结点函数、free释放结点函数和match对比结点函数，类型都是void*无类型指针，目的是为了实现链表的多态。
       <li>然后链表的每个结点listnode串联成链表，然后这链表是双端无环，也就是每个结点都有指向前一个结点的prev指针和指向后一个结点的next指针。最后结点存储是值是void*无类型指针，指向存储的值对象，也是为了实现多态。
</details>
<details><summary>3.字典</summary>
  <li>Redis中的字典的实现从最低层往上讲就是：首先由单向链表构成单个哈希表结点，再有一个个哈希表结点构成数组形成一个哈希表，最后由两个哈希表形成一个字典。
  <li>然后在添加一个键值对的时候，字典通过哈希算法往哈希表中添加结点。期间根据字典维护的负载因子判断是否进行rehash，也就是重新散列。
    <br><b>下面我可以来为刚刚提到的每个概念进行展开讲解包括rehash的方式和使用哈希算法插入键值对的一些关键点</b>:
    <li>首先是最外层的字典，他是一个dict结构体：<br>&nbsp&nbsp&nbsp&nbsp（1）其中type属性是一个指向dictType结构的指针，这个dictType结构封装了各种操作特定类型的键值对的函数。<br>&nbsp&nbsp&nbsp&nbsp（2）dict结构体中还有一个private属性，这个属性保存了需要传给dictType结构中特定类型函数的可选参数。<br>&nbsp&nbsp&nbsp&nbsp（3）另外dict结构体中还含有一个rehashidx属性，记录rehash进行时的当前索引，当没有进行rehash时，它的值是-1
      
</details>
    
