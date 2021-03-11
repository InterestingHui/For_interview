<h1>C++</h1>
1.<details><summary>什么是<b>段错误</b></summary>
  <li>段错误就是程序访问受保护或者不存在的内存的时候引发的错误
  <li>引发段错误原因有：访问受保护的内存、访问不存在的内存、访问只读的内存、访问空指针的值、堆栈溢出、内存溢出等
</br>
</details>
<h2>笔记</h2>
<h5>1.声明一个结构体指针：</h5>
<pre>
    (i)node *Begin=(node *)malloc(sizeof(node)),*another=(node *)malloc(sizeof(node));</br>
    (ii)node *Begin=new node(3),*another=new node(5);
</pre>
</P>
<h5>2.设计一个二叉树类</h5>
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
