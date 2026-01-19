# CppNote

## 模版

### 完美转发（Perfect Forwarding）
- 代码示例:
  ```cpp
  template<typename T>
  constexpr class forward(T&& x) noexcept { return static_cast<T&&>(x); }
  ```
- 作用：
  保持参数左值、右值语义不变。
> constexpr
  函数或变量可以在编译期求值。  
>  noexcept
  保证不抛出异常。
  
--- 
### 类型包：...
C++ 语法符号，称为“ 参数包展开运算符（pack expansion operator）”。
