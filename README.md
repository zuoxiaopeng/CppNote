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

### 模版类型推导
- 示例函数模版：
```cpp
template<typename T>
void f(ParamType param);
f(param);
```

- 保持constness
  - 形参：T& param
    - 入参：const int&/const int -> T: const int, param: const int& 
    - 入参：int/int& -> T: int, param: int&
  - 形参： const T& param
    - 入参： int/int&/const int/const int& -> T: const int, param: const int&


