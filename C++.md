<h>C++</h>
* 什么是**段错误**
  - 段错误就是程序访问受保护或者不存在的内存的时候引发的错误
  - 引发段错误原因有：访问受保护的内存、访问不存在的内存、访问只读的内存、访问空指针的值、堆栈溢出、内存溢出等

---------
<h>笔记</h>
<p>声明一个结构体指针：</br>
    (i)node *Begin=(node *)malloc(sizeof(node)),*another=(node *)malloc(sizeof(node));</br>
    (ii)node *Begin=new node(3),*another=new node(5);
</P>
<h1>设计一个二叉树类</h1>
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

