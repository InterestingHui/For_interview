<h3>编译原理</h3>
<details><summary>1.源代码是怎么变成可执行文件的，每一步的作用是什么？</summary>
  <li>通过四步:预编译、编译、汇编、链接四个步骤
  <li>预编译主要做6件事:<br>&nbsp&nbsp&nbsp&nbsp(i)将所有的#define删除，并展开所有的宏定义<br>&nbsp&nbsp&nbsp&nbsp(ii)处理所有的<b>条件预编译指令</b>比如#if、#endif、#elif、#else等
  <br>&nbsp&nbsp&nbsp&nbsp(iii)处理<b>#include预编译指令</b>,并将被包含的文件插入到对应的预编译指令的位置<br>&nbsp&nbsp&nbsp&nbsp(iv)删除所有的注释<br>&nbsp&nbsp&nbsp&nbsp(v)添加行号和文件标识，以便为编译时调试用的行号和编译出错时警告用的行号服务
<br>&nbsp&nbsp&nbsp&nbsp(vi)最后将.c文件变成.i文件<br>&nbsp&nbsp&nbsp&nbsp要注意的是#pragma指令会被保留，因为编译的时候需要使用它们。
