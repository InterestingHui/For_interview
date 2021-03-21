<h1>Redis</h1>
<h3>数据结构</h3>
<details><summary>1.字符串</summary></details>
<li>redis中的字符串是动态字符串，叫SDS
  <li>redis中用到sds的地方：1.字符串对象：除了字符串值对象外，所有的键值对的键都是字符串对象；2.AOF持久化的输入缓冲区是用SDS实现的
    <li>SDS的内部结构：(i)buf数组，是一个char类型数组，记录字符串内容。<br>(ii)free属性，int类型，记录buf数组中没有使用的字节的数量。<br>(iii)记录已经使用的字节数量。
      <li>SDS和C字符串的区别：
        
      
