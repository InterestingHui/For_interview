<h1>C++</h1>
<details><summary>1.什么是<b>段错误</b>?</summary>
  <li>段错误就是程序访问受保护或者不存在的内存的时候引发的错误
  <li>引发段错误原因有：访问受保护的内存、访问不存在的内存、访问只读的内存、访问空指针的值、堆栈溢出、内存溢出等
</details>
<details><summary>2.<b>extern</b>关键字有什么用?</summary>
  主要有两个作用
  <li>第一个作用是放在变量名和函数面前，表示声明这个变量或者是函数，而这个变量或者函数是在其它文件中定义的，所以这里只有声明并拿来引用，而非定义，所以也不分配空间
  <li>第二个作用是和C双引号字符连用，这样让后面的函数在C++程序编译时还是按C编译的规则，就是不改变函数的名字，而如果不加的话，C++编译时会改变函数的名字，通过将函数的名字和参数联合生成一个新的函数名，C++这样做是为了适用于函数多态服务。
</details>
<hr>
<h2>算法题笔记</h2>
<details><summary>
  1.声明一个结构体指针</summary>
<pre>
    (i)node *Begin=(node *)malloc(sizeof(node)),*another=(node *)malloc(sizeof(node));</br>
    (ii)node *Begin=new node(3),*another=new node(5);
</pre>
</details>
<details><summary>2.设计一个二叉树类</summary>
<pre>
struct TreeNode {
    int val;
    TreeNode *left;
    TreeNode *right;
    TreeNode() : val(0), left(nullptr), right(nullptr) {}
    TreeNode(int x) : val(x), left(nullptr), right(nullptr) {}
    TreeNode(int x, TreeNode *left, TreeNode *right) : val(x), left(left), right(right) {}
};
</pre>
</details>
