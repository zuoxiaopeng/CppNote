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
<br>
  
### 类型包：...
C++ 语法符号，称为“ 参数包展开运算符（pack expansion operator）”。  
<br>

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
<br>


## 构造函数
### 深/浅拷贝
- 深拷贝
  - 拷贝对象成员指针变量指向的对象
- 浅拷贝
  - 拷贝对象成员指针变量指针
<br>

## 设计模式
### 单例
```cpp
class Singleton
{
public:
	Singleton(const Singleton&) = delete;
	Singleton& operator=(const Singleton&) = delete;

	static Singleton& GetInstance()
	{
		static Singleton Instance;
		return Instance;
	}

private:
	Singleton() = default;
	~Singleton() = default;
};
```
- 注意点
  - 删除拷贝/赋值构造
  - 私有构造/析构
  - 静态成员函数，静态局部变量
  - c++11起 保证静态局部变量线程安全，c++17 可以使用inline static Singleton instance 作为私有成员变量
