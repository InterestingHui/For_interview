<h1>C++</h1>
<details><summary>1.什么是<b>段错误</b>?</summary>
  <li>段错误就是程序访问受保护或者不存在的内存的时候引发的错误
  <li>引发段错误原因有：访问受保护的内存、访问不存在的内存、访问只读的内存、访问空指针的值、堆栈溢出、内存溢出等
</details>
<details><summary>2.<b>extern</b>关键字有什么用?</summary>
  主要有两个作用
  <li>第一个作用是放在变量名和函数面前，表示声明这个变量或者是函数，而这个变量或者函数是在其它文件中定义的，所以这里只有声明并拿来引用，而非定义，所以也不分配空间
  <li>第二个作用是和C双引号字符连用，这样让后面的函数在C++程序编译时还是按C编译的规则，就是不改变函数的名字，而如果不加的话，C++编译时会改变函数的名字，通过将函数的名字和参数联合生成一个新的函数名，C++之所以编译会改变函数名字，是为了适用于函数多态服务。而如果在C++文件中使用C语言的头文件，可能因为没有加extern "C"而找不到这个函数。所以extern "C"也常常用于C语言的头文件中。
</details>
<details><summary>3.<b>static</b>关键字有什么用?</summary>
  static用于声明用于内部连接的变量或函数，和extern相反。
  <li>首先static可以用在局部变量的声明前，这样的话，这个局部变量将是存储在程序的静态存储区，而非内存栈中。这样一来，这个局部变量的生命周期就会跟整个程序一样，在main函数运行前就会创建，在程序退出时才会销毁。所以当包含局部变量的函数再次调用的时候，这个局部变量依然是上一次退出时的值，也并不会重新创建。
  <li>第二个是static可以用于全局变量和函数前，这两个作用类似，就是让这个全局变量和函数只能在这个文件内使用，外部文件无法调用。这个通常用在工程项目中防止多个文件内用重名的全局变量和函数，而作用不同发生混淆
  <li>第三个的话，static可以用在类的成员变量前，这类似于用在局部变量前，这样一来，成员变量存储在静态存储区，然后不依赖与类的对象而存在，也就是创建类的对象时，并不会再分配这个变量空间，因为都是共享这个静态存储区的这个成员变量，这样也能提高速度和优化空间。
  <li>最后还有，static可以用在成员函数前，这样的话，这个函数没有指向类的this指针，所以也无法访问类的其它成员，除了类内的其它静态成员
  <li>另外static声明的变量会默认初始化为0
 </details>
<details><summary>4.<b>volatile</b>[ˈvɒlətaɪl]关键字有什么事用？</summary>
  <li>volatile用于声明一个易变的变量，在定义前加volatile，就让这个程序每次使用这个变量的时候都要从内存也就是变量的地址空间中读取变量，而不能到CPU寄存器里读取
  <li>volatile经常用于多线程中，使得一个线程对该变量的改变，等同于能马上让所有其它线程获悉这个改变，保持数据一致性。
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
