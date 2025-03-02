#  STL容器算法  
## `array` 
`array` 是 C++11 引入的一个模板类，提供了比 C 风格数组更多的功能。它的大小是固定的，并且在编译时就确定。

```cpp
#include <array>
#include <iostream>

int main() {
    array<int, 5> arr = {1, 2, 3, 4, 5};

    // 使用 at() 安全地访问数组元素
    cout << "Element at index 2: " << arr.at(2) << endl;

    // 使用 size() 获取数组大小
    cout << "Size of array: " << arr.size() << endl;

    // 使用范围 for 循环遍历数组
    for (int i : arr) {
        cout << i << " ";
    }
    return 0;
}
```

---













## vector 
### 特点：
1. **动态大小**：vector 能根据需要动态调整大小。

2. **自动内存管理**：vector 自动处理内存的分配和释放，不需要手动管理内存。

3. **随机访问**：与数组类似，vector 也支持常量时间的随机访问操作。

4. **支持**** STL ****算法**：vector 与许多标准算法（如sort）无缝兼容。

### vector常用操作和函数:
##### 1. 声明 vector
```cpp
#include <vector>
vector<int> vec;          // 创建一个存储 int 类型的空向量
vector<int> vec(10);      // 创建一个包含 10 个元素的向量，默认初始化为 0
vector<int> vec(10, 5);   // 包含 10 个元素，每个元素初始化为 5
```

##### 2. 添加元素
· push_back：在vector 的末尾添加一个元素。

```cpp
vec.push_back(20);  // 向量末尾添加 20
```

##### 3. 访问元素
· []** ****和**at()：[] 提供类似数组的访问，at() 提供边界检查的访问方式。

```cpp
int value = vec[0];       // 获取第一个元素
int value = vec.at(0);    // 获取第一个元素（有边界检查，超出范围会抛异常）
```

##### 4. 获取大小
· size()：返回向量中当前元素的个数。

```cpp
int size = vec.size();  // 获取向量大小
```

##### 5. 删除元素
· pop_back()：删除vector 中最后一个元素。

```cpp
vec.pop_back();  // 删除最后一个元素
```

##### 6. 插入和删除
· insert()：在向量的某个位置插入元素。

· erase()：删除指定位置的元素。

```cpp
vec.insert(vec.begin(), 10);  // 在向量开头插入 10
vec.erase(vec.begin());       // 删除向量的第一个元素
```

##### 7. 清空向量
· clear()：删除所有元素，size() 将变为 0。

```cpp
vec.clear();  // 清空向量
```

##### 8. 检查是否为空
· empty()：检查向量是否为空。

```cpp
bool isEmpty = vec.empty();  // 如果向量为空，返回 true
```

##### 9. 迭代遍历
```cpp
for (int i = 0; i < vec.size(); ++i) 
    cout << vec[i] << " ";  // 使用索引遍历

for (auto it = vec.begin(); it != vec.end(); ++it) 
    cout << *it << " ";  // 使用迭代器遍历

for (int x : vec) 
    cout << x << " ";  // 使用范围 for 循环遍历
```

















  


## queue
### 1. 包含头文件
```cpp
#include <iostream>
#include <queue>
```

### 2. 创建队列
```cpp
queue<int> q;
```

### 3. 入队（push）
使用push()方法将元素添加到队列的末尾：

```cpp
q.push(10);
q.push(20);
q.push(30);
```

### 4. 出队（pop）
使用pop()方法从队列的前面移除元素：

```cpp
q.pop();   // 移除队首元素（10）
```

### 5. 访问队首元素
使用front()方法访问队首元素，但不移除它：

```cpp
int frontElement = q.front();   // frontElement 现在是20
```

### 6. 检查队列是否为空
使用empty()方法检查队列是否为空：

```cpp
if (q.empty()) std::cout << "队列为空" << std::endl;
```

### 7. 获取队列大小
使用size()方法获取队列中元素的数量：

```cpp
std::cout << "队列大小: " << q.size() << std::endl;
```

### 示例代码
```cpp
#include <iostream>
#include <queue>
int main() {
queen<int> q;
// 入队
q.push(10);
q.push(20);
q.push(30);

// 访问队首元素
cout << "队首元素: " << q.front() << endl; // 输出 10

// 出队
q.pop();

cout << "队首元素: " << q.front() << endl; // 输出 20

// 队列大小
cout << "队列大小: " << q.size() << endl; // 输出 2

return 0;
}
```























  


## STL 容器（如 vector，string ）相关用法：
### 1. pop_back()
pop_back() 用于<font style="color:rgb(0,0,255);">删除</font>字符串或容器的最后一个元素。

```cpp
string str = "Hello!";
str.pop_back(); // 删除最后一个字符
                // str = "Hello"
```

### 2. push_back()
push_back() 用于在字符串或容器的末尾<font style="color:rgb(0,0,255);">添加</font>一个元素。

```cpp
string str = "Hello";
str.push_back('!'); // 在末尾添加字符 '!'  str = "Hello!"
```

### 3. back()
back() 方法返回字符串或容器最后一个元素的引用，但不删除它。

```cpp
string str = "Hello!";
char lastChar = str.back();  // lastChar = '!'
```

### 4. front()
front() 方法返回字符串或容器第一个元素的引用，但不删除它。

```cpp
string str = "Hello!";
char firstChar = str.front();  // firstChar = 'H'
```

### 5. begin()
begin() 方法返回一个迭代器，指向字符串或容器的第一个元素。

```cpp
string str = "Hello";
auto it = str.begin();  // it 指向 'H'
cout << *it << endl;  // 输出: H
```

### 6. getline()
getline() 用于从输入流中读取一整行字符串，<font style="color:rgb(0,0,255);">包括空格</font>，<font style="color:rgb(0,0,255);">直到遇到换行符。</font>

```cpp
#include <iostream>
#include <string>
int main() {
    string input;
    cout << "Enter a line of text: ";
    getline(cin, input);   // 读取整行输入,注意前面"cin,"
    cout << "You entered: " << input << endl;
    return 0;
}
```

### 7.`begin()` 和` end()` 
begin(),end()用于获取容器中第一个元素的开始和容器中最后一个元素**之后**的**位置**，可以用于stl容器和传统数组。

```cpp
vector<int> vec = {10, 20, 30, 40, 50};

// 使用 begin() 和 end() 手动遍历容器
for (auto it = vec.begin(); it != vec.end(); ++it) {
    cout << *it << " ";   //因为返还的是位置，所以需要用 * 解引用
    //输出：10 20 30 40 50
}

```

---











## Range-based `for` loop
适用于传统数组、stl容器和C++11 之后的其他容器。

### 1. **基本语法**
```cpp
for (declaration : container) {
    // code to process each element
}
```

+ **declaration**：用于声明遍历容器中每个元素的类型。
+ **container**：你要遍历的容器，例如数组、`vector`、`list` 等。

### 2. **执行流程**
假设`vec`是一个包含整数的数组或容器，假设`vec`包含 `{10, 20, 30, 40, 50}`，则在 `for (int i : vec)` 中：

1. 循环开始时，`i` 会依次被赋值为容器 `arr` 中的每个元素。
2. 在每次循环中，`i` 会输出到控制台，直到容器中的所有元素都被遍历一遍。

```cpp
#include <iostream>
#include <vector>
using namespace std;

int main() {
    vector<int> vec = {10, 20, 30, 40, 50};
    
    // 使用range-based for 循环遍历并输出元素
    for (int i : vec) {
        cout << i << " ";  // 输出每个元素并加一个空格
    }
    // 输出：10 20 30 40 50

    for (auto i : vec) {   // 使用 auto 来自动推导元素的类型
        cout << i << " ";
    }

    for (int& i : vec) {   // 修改元素（使用引用）
        i *= 2;  // 将每个元素的值翻倍
    }

    for (const int& i : vec) {   // 不修改元素（使用常量引用）,避免复制开销
        cout << i << " ";  // 输出每个元素，不修改
    }
    return 0;
}
```

---



















# 数据操作
## `sort` 
位于  `<algorithm>` 头文件中，适用于多种容器类型，比如数组、`vector` 等。、

### `sort` 接受的三个参数：
+ 第一个参数是容器的起始迭代器（`nums.begin()`）。
+ 第二个参数是容器的结束迭代器（`nums.end()`）。
+ 第三个参数是一个**函数**（或**可调用对象**），用来定义如何比较容器中的元素。这个函数决定了元素排序的顺序。

### 使用自定义比较函数
`sort()` 默认按升序排序，但你可以提供一个自定义的比较函数来改变排序的规则，例如降序排序或根据特定的条件进行排序。

#### 1.使用自定义比较函数（降序排序）
```cpp
// 自定义比较函数：降序排序
bool compare(int a, int b) {
    return a > b;  
    // 如果 a > b 返回 true，就将 a 排在前面
    // 这里的 a , b 就相当于相邻的元素
}

int main() {
    vector<int> vec = {5, 2, 8, 1, 3};

    // 使用自定义比较函数进行降序排序
    sort(vec.begin(), vec.end(), compare);
    
    return 0;
}
```

#### 2.使用 lambda 表达式作为比较函数
使用 C++11 引入的 lambda 表达式来快速定义一个排序规则，而无需单独编写一个函数：

```cpp
vector<int> vec = {5, 2, 8, 1, 3};

// 使用 lambda 表达式进行降序排序
sort(vec.begin(), vec.end(), [](int a, int b) {
        return a > b;  // 降序
});
```

### 排序对象（结构体、类）的示例
如果要排序的元素是自定义类型，比如结构体或类对象，可以根据某个字段进行排序。

#### 按结构体字段排序
```cpp
struct Person {
    string name;
    int age;
};

int main() {
    vector<Person> people = {
    {"Alice", 30},
    {"Bob", 25},
    {"Charlie", 35}
};

    // 按照年龄进行升序排序
    sort(people.begin(), people.end(), [](const Person& a, const Person& b) {
        return a.age < b.age;
    });

    // 输出排序后的结果
    for (const auto& person : people) {
        cout << person.name << ": " << person.age << endl;
    }

    return 0;
}
```

### 排序数组
你也可以对原生数组进行排序，只需传入数组的开始和结束**指针**：

```cpp
int arr[] = {5, 2, 8, 1, 3};
int n = sizeof(arr) / sizeof(arr[0]);  // 计算数组长度
//这里的sizeof返回的是总字节数，所以还要除一个单个元素的字节数

sort(arr, arr + n);  //注意下标表示
```

当我们需要对两个（甚至更多）数组联动的时候：

```cpp
struct node {
    int x, y;
};

int main() {
  int n;
  node arr[20];
  cin >> n;
  for (int i = 1; i <= n; i++) 
    cin >> arr[i].x >> arr[i].y;  //要习惯直接使用结构体

  // 使用 lambda 表达式对 arr 数组进行排序
  sort(arr, arr + n, [](node const& a, node const& b) {
    if (a.x != b.x) {
      return a.x < b.x;  // 根据 x 排序
    }
    return a.y < b.y;  // 如果 x 相同，再根据 y 排序
  });  //这里就要很自然地理解a,b是相邻的两个元素

  return 0;
}
```

### `sort()` 的其他特点
+ **稳定性**：`sort()` 是**不稳定**的排序算法。可以使用 `**stable_sort()作为稳定排序算法**`。
+ **空容器**：如果容器为空，`sort()` 不会进行任何操作，程序也不会报错。























  


## switch
### 基本语法：
```cpp
switch (expression) {
    case constant1:
        // 如果 expression == constant1, 执行这部分代码
        break;  //break不可轻易省略；如果break消失了，就无条件继续下一个case
    case constant2:
        // 如果 expression == constant2, 执行这部分代码
        break;
    default:
    // 如果没有匹配到任何 case，执行这部分代码
}
```

### 主要组成部分：
1. **expression**：通常是一个**整型**、**字符型**或**枚举类型**的值，**不能是****<font style="color:#DF2A3F;">浮点型</font>****或****<font style="color:#DF2A3F;">字符串</font>**。
2. **case constant**：每个`case`后面跟一个**常量值**，如果`expression`的值与某个`case`的常量值匹配，则执行该`case`下的代码。注意ASCII产生潜在的影响。
3. **break**：用于退出`switch`语句。如果没有`break`语句，程序会继续无条件执行下一个`case`中的代码，即“穿透现象”，通常会导致错误，除非有特殊需求。
4. **default**：如果没有任何`case`匹配`expression`的值，`default`中的代码会被执行。`default`可以放在**任意位置**，但通常放在最后。

### 示例代码：
```cpp
int day = 3;
switch (day) {
    case 1:
        cout << "Monday" << endl;
        break;
    case 2:
        cout << "Tuesday" << endl;
        break;
    case 3:
        cout << "Wednesday" << endl;
        break;
    default:
        cout << "Invalid day" << endl;
        break;
} 
```

---





















## `atoi` 
`atoi` 是一个标准库函数，需要引用 **#include <cstdlib>** ，用于将 **C 风格**的字符串（即以 `\0` 结尾的字符数组）转换为整数类型 `int`。

### 语法
```cpp
int atoi(const char* str);
```

### 特点
1. **忽略前导空格**：`atoi` 会忽略字符串开头的空格字符。
2. **处理符号**：可以识别正负号（`+` 或 `-`）。
3. **无错误处理**：`atoi` 并不会提供详细的错误信息。如果字符串不能转换为整数，它将返回 `0`，但不能区分字符串是否真的表示 `0`，还是无法转换的情况。

### 示例
```cpp
#include <iostream>
#include <cstdlib>  // 引入atoi

int main() {
    const char* str1 = "12345";    // 正常的数字字符串
    const char* str2 = "-678";   // 带负号的数字字符串
    const char* str3 = "abc123";   // 无效的字符串
    const char* str4 = "";         // 空字符串

    std::cout << "str1: " << atoi(str1) << std::endl;  // 输出 12345
    std::cout << "str2: " << atoi(str2) << std::endl;  // 输出 -678
    std::cout << "str3: " << atoi(str3) << std::endl;  // 输出 0
    std::cout << "str4: " << atoi(str4) << std::endl;  // 输出 0

    return 0;
}
```

### 注意事项
+ `atoi` 只适用于 C 风格字符串。如果你使用 `std::string`，可以先调用 `std::string::c_str()` 将其转换为 C 风格字符串，或者直接使用 `std::stoi`。
+ `atoi` 不会检测溢出。如果输入值超出了 `int` 类型的表示范围，结果会是未定义的行为。

### `用stoi` 替代
`stoi`（在 `<string>` 头文件中）不仅支持**字符串**转换为整数，还能抛出**异常**（例如 `invalid_argument` 或 `out_of_range`）以便更好地处理错误。

```cpp
#include <iostream>
#include <string>

int main() {
    std::string str = "12345";
    try {
        int num = std::stoi(str);
        std::cout << "Converted number: " << num << std::endl;
    } catch (const std::invalid_argument& e) {
        std::cout << "Invalid argument: " << e.what() << std::endl;
    } catch (const std::out_of_range& e) {
        std::cout << "Out of range: " << e.what() << std::endl;
    }

    return 0;
}
```

---















## 映射（map）
### `**<font style="background-color:rgb(252, 252, 252);">map</font>**`
#### **<font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);">1. 核心特性</font>**
+ **<font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);">有序性</font>**<font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);">：元素按</font>**<font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);">键（Key）</font>**<font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);">自动排序（默认升序，可自定义排序规则）。</font>
+ **<font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);">唯一键</font>**<font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);">：每个键在容器中唯一，不能重复。</font>
+ **<font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);">高效操作</font>**<font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);">：插入、删除和查找操作的时间复杂度为 </font>**<font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);">O(log n)</font>**<font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);">。</font>
+ **<font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);">底层结构</font>**<font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);">：基于红黑树（自平衡二叉搜索树），保证动态操作的高效性。</font>

#### **<font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);">2. 常用操作</font>**
##### **<font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);">头文件与声明</font>**
```cpp
#include <map>
using namespace std;

// 声明一个键为 string，值为 int 的 map
map<string, int> myMap;

// 自定义排序规则（按键降序）
map<string, int, greater<string>> myDescMap;
```

##### **<font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);">插入元素</font>**
+ `**<font style="background-color:rgb(252, 252, 252);">insert()</font>**`<font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);">：返回一个 </font>`<font style="background-color:rgb(252, 252, 252);">pair<iterator, bool></font>`<font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);">，指示插入是否成功。</font>
+ `**<font style="background-color:rgb(252, 252, 252);">operator[]</font>**`<font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);">：若键不存在，插入默认值；若存在，直接修改值。</font>

```cpp
myMap.insert({"apple", 5});         // 插入键值对
myMap.insert(make_pair("banana", 3));
myMap["orange"] = 7;               // 使用 [] 插入或修改
```

##### **<font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);">查找元素</font>**
+ `**<font style="background-color:rgb(252, 252, 252);">find(key)</font>**`<font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);">：返回指向键的迭代器，未找到则返回 </font>`<font style="background-color:rgb(252, 252, 252);">end()</font>`<font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);">。</font>
+ `**<font style="background-color:rgb(252, 252, 252);">count(key)</font>**`<font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);">：返回键的数量（0 或 1）。</font>

```cpp
auto it = myMap.find("apple");
if (it != myMap.end()) {
    cout << "Found: " << it->second << endl; // 输出值
}

if (myMap.count("banana") > 0) {
    cout << "Key exists!" << endl;
}
```

##### **<font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);">删除元素</font>**
+ `**<font style="background-color:rgb(252, 252, 252);">erase(key)</font>**`<font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);">：删除指定键的元素。</font>
+ `**<font style="background-color:rgb(252, 252, 252);">erase(iterator)</font>**`<font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);">：通过迭代器删除。</font>

```cpp
myMap.erase("apple");            // 删除键为 "apple" 的元素
auto it = myMap.find("banana");
if (it != myMap.end()) {
    myMap.erase(it);             // 通过迭代器删除
}
```

##### **<font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);">遍历元素</font>**
```cpp
// 使用迭代器
for (auto it = myMap.begin(); it != myMap.end(); ++it) {
    cout << it->first << ": " << it->second << endl;
}

// 使用 C++11 范围 for 循环
for (const auto& pair : myMap) {
    cout << pair.first << ": " << pair.second << endl;
}
```

#### **<font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);">3. 自定义键类型</font>**
<font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);">若键是自定义类型（如类或结构体），需提供</font>**<font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);">比较规则</font>**<font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);">：</font>

+ <font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);">重载</font><font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);"> </font>`<font style="background-color:rgb(252, 252, 252);"><</font>`<font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);"> </font><font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);">运算符。</font>
+ <font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);">或在模板参数中指定自定义比较器。</font>

```cpp
struct Point {
    int x, y;
    // 重载 < 运算符
    bool operator<(const Point& other) const {
        return (x < other.x) || (x == other.x && y < other.y);
    }
};

// 使用自定义比较器
struct ComparePoint {
bool operator()(const Point& a, const Point& b) const {
    return a.x < b.x;
}
};
map<Point, string, ComparePoint> pointMap;
```

#### **<font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);">4. 性能与适用场景</font>**
+ **<font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);">适用场景</font>**<font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);">：需要有序键、频繁查找/插入/删除且键唯一的场景。</font>
+ **<font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);">对比</font>****<font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);"> </font>**`**<font style="background-color:rgb(252, 252, 252);">unordered_map</font>**`<font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);">：</font>
    - `<font style="background-color:rgb(252, 252, 252);">map</font>`<font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);"> </font><font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);">有序，但性能略低（O(log n)）。</font>
    - `<font style="background-color:rgb(252, 252, 252);">unordered_map</font>`<font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);"> </font><font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);">无序，但平均查找时间为 O(1)（基于哈希表）。</font>

**<font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);">5. 示例代码</font>**

```cpp
#include <iostream>
#include <map>
using namespace std;

int main() {
    map<string, int> fruits;

    // 插入元素
    fruits["apple"] = 5;
    fruits.insert({"banana", 3});
    fruits.emplace("orange", 7);  // 更高效的插入方式

    // 修改值
    fruits["apple"] = 10;

    // 遍历
    for (const auto& [key, value] : fruits) { // C++17 结构化绑定
        cout << key << ": " << value << endl;
    }

    // 删除元素
    fruits.erase("banana");

    return 0;
}
```



### **<font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);">2. </font>**`**<font style="background-color:rgb(252, 252, 252);">unordered_map</font>**`
#### **<font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);">基本特性</font>**
+ **<font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);">无序性</font>**<font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);">：键的顺序不确定（取决于哈希函数和桶分布）。</font>
+ **<font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);">底层实现</font>**<font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);">：哈希表（数组 + 链表/红黑树）。</font>
+ **<font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);">时间复杂度</font>**<font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);">：</font>
    - <font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);">平均情况：插入、删除、查找为</font><font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);"> </font>`<font style="background-color:rgb(252, 252, 252);">O(1)</font>`<font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);">。</font>
    - <font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);">最坏情况：哈希冲突严重时退化为</font><font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);"> </font>`<font style="background-color:rgb(252, 252, 252);">O(n)</font>`<font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);">。</font>
+ **<font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);">内存占用</font>**<font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);">：较低（但需预留桶空间）。</font>
+ **<font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);">是否需要哈希函数</font>**<font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);">：需要键的哈希函数（默认支持基本类型，自定义类型需手动实现）。</font>

#### 操作用法
与map几乎一致。























## <font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);">并查集</font>
<font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);">并查集是一种用于管理元素分组关系的数据结构，支持以下两种核心操作：</font>

+ **<font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);">Find</font>**<font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);">：查询元素所属的集合（通常返回集合的“代表元素”）。</font>
+ **<font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);">Union</font>**<font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);">：合并两个元素所在的集合。</font>

<font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);">常用于解决 </font>**<font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);">动态连通性问题</font>**<font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);">，例如：</font>

+ <font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);">网络中的节点连接状态判断</font>
+ <font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);">图的连通分量统计</font>
+ <font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);">元素分组去重（如题目中的数组去重问题）</font>

### <font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);">一、核心操作实现</font>
#### <font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);">1. 数据结构初始化</font>
<font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);">每个元素初始指向自己，表示自己是独立的集合。</font>

```cpp
int parent[N];  // N为元素数量
void init() {
    for (int i = 0; i < N; i++) parent[i] = i;
}
```

#### <font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);">2. Find操作（查找代表元素）</font>
<font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);">查找元素所属集合的根节点（代表元素）。</font>

```cpp
int find(int x) {
    if (x == fa[x])      // 如果x是根节点
        return x;
    return fa[x] = find(fa[x]); // 递归+路径压缩
}
```

#### <font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);">3. Union操作（合并集合）</font>
<font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);">合并两个元素所在的集合。</font>

```cpp
void unionSet(int x, int y) {
    int rootX = find(x),rootY = find(y);
    if (rootX != rootY) {
        parent[rootY] = rootX;  // 可结合按秩合并优化
    }
}
```

---

### <font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);">二、优化方法</font>
#### <font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);">1. 路径压缩（Path Compression）</font>
<font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);">在</font><font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);"> </font>`<font style="background-color:rgb(252, 252, 252);">Find</font>`<font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);"> </font><font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);">过程中将树的路径扁平化，使得后续查询更快。  
</font><font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);">https://i.imgur.com/5kU3lqC.gif</font>

#### <font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);">2. 按秩合并（Union by Rank）</font>
<font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);">在</font><font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);"> </font>`<font style="background-color:rgb(252, 252, 252);">Union</font>`<font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);"> </font><font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);">时让小树合并到大树中，降低树的高度。</font>

```cpp
int rank[N];  // 记录树的深度
void init() {
    for (int i = 0; i < N; i++) {
        parent[i] = i;
        rank[i] = 1;  // 初始高度为1
    }
}

void unionSet(int x, int y) {
    int rootX = find(x), rootY = find(y);
    if (rootX != rootY) {
        if (rank[rootX] > rank[rootY]) {
            parent[rootY] = rootX;
        } else {
            parent[rootX] = rootY;
            if (rank[rootX] == rank[rootY]) rank[rootY]++;
        }
    }
}
```

### <font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);">三、时间复杂度</font>
| **<font style="background-color:rgb(252, 252, 252);">操作</font>** | **<font style="background-color:rgb(252, 252, 252);">平均时间复杂度</font>** | **<font style="background-color:rgb(252, 252, 252);">最坏时间复杂度</font>** |
| :---: | :---: | :---: |
| <font style="background-color:rgb(252, 252, 252);">未优化</font> | <font style="background-color:rgb(252, 252, 252);">O(N)</font> | <font style="background-color:rgb(252, 252, 252);">O(N)</font> |
| <font style="background-color:rgb(252, 252, 252);">路径压缩</font> | <font style="background-color:rgb(252, 252, 252);">O(α(N))</font> | <font style="background-color:rgb(252, 252, 252);">O(logN)</font> |
| <font style="background-color:rgb(252, 252, 252);">路径压缩+按秩合并</font> | <font style="background-color:rgb(252, 252, 252);">O(α(N))</font> | <font style="background-color:rgb(252, 252, 252);">O(α(N))</font> |


<font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);">其中 α(N) 是阿克曼函数的反函数，增长极其缓慢，可视为常数。</font>

### <font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);">四、应用示例</font>
#### <font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);">题目：修改数组</font>
[https://www.luogu.com.cn/problem/P8686](https://www.luogu.com.cn/problem/P8686)

```cpp
#include <iostream>
#include <unordered_map>
using namespace std;

unordered_map<int, int> parent;

int find(int x) {
    if (!parent.count(x)) parent[x] = x;  // 动态初始化
    if (parent[x] != x) parent[x] = find(parent[x]);
    return parent[x];
}

int main() {
    int n, a;
    cin >> n;
    while (n--) {
        cin >> a;
        int root = find(a);      // 找到可用位置
        cout << root << " ";
        parent[root] = root + 1; // 指向下一个可用位置
    }
    return 0;
}
```























# 数据类型与变量
## 数据类型大小
+ **int**：4字节，表示范围为 −2^31 到 2^31−1。
+ **unsigned int**：4字节，表示范围为 000 到 2^32−1。
+ **short**：2字节，表示范围为 −2^15 到 2^15−1。
+ **unsigned short**：2字节，表示范围为 00 到 2^16。
+ **long**：4字节（在某些系统上为8字节），通常范围为 −2^31 到 2^31−1。
+ **unsigned long**：4字节（在某些系统上为8字节），通常范围为 0到 2^32。
+ **long long**：8字节，范围为 −2^63 到 2^63−1。
+ **unsigned long long**：8字节，范围为 0 到 2^64-1。
+ **float**：4字节，表示单精度浮点数。
+ **double**：8字节，表示双精度浮点数。
+ **long double**：通常为8、10或16字节，具体取决于编译器和平台。
+ **char**：1字节，表示范围为−128 到 127或 0 到 255（取决于是否为有符号char）。

要确定在你的系统上的具体大小，可以使用 `**sizeof**` 运算符来检查：

```cpp
cout << "Size of int: " << sizeof(int) << " bytes" << endl;
```

注：2^31~2e10,2^63~2e19















  




## 数据类型后缀
### 1. `**f**`** 和 **`**F**`
表示 `**float**` 类型：

+ `1.23f` 或 `1.23F` 是 `float` 类型字面量。
+ 默认情况下，浮点数字面量是 `double` 类型，加上 `f` 后缀表示单精度浮点数。

### 2. `**l**`** 和 **`**L**`
表示 `**long double**` 类型：

+ `1.23l` 或 `1.23L` 是 `long double` 类型字面量。
+ 如果没有后缀，浮点数字面量默认是 `double` 类型，而加上 `l` 或 `L` 后缀表示扩展精度的浮点数。

### 3. `**u**`** 和 **`**U**`
表示 `**unsigned**` 类型：

+ `10u` 或 `10U` 是 `unsigned int` 类型的字面量。
+ 用 `u` 后缀来指定一个无符号整数。

### 4. `**l**`** 和 **`**L**`
表示 `**long**` 类型：

+ `100L` 或 `100l` 是 `long` 类型的字面量。
+ `l` 后缀可以与 `u` 或 `U` 组合，表示 `unsigned long` 类型（`100UL`）。

### 5. `**ul**`**、**`**UL**`**、**`**lu**`** 和 **`**LU**`
表示 `**unsigned long**` 类型：

+ `100ul` 或 `100UL` 是 `unsigned long` 类型字面量。

### 6. `**ll**`** 和 **`**LL**`
表示 `**long long**` 类型：

+ `100LL` 或 `100ll` 是 `long long` 类型的字面量。
+ 用于表示比 `long` 类型更大的整数。

### 7. `**ull**`** 和 **`**ULL**`
表示 `**unsigned long long**` 类型：

+ `100ULL` 或 `100ull` 是 `unsigned long long` 类型字面量。

### 示例代码：
```cpp
int a = 100;           // 默认为 int 类型
unsigned int b = 100u; // 使用 u 后缀表示 unsigned int
long c = 100L;         // 使用 L 后缀表示 long 类型
unsigned long d = 100UL; // 使用 UL 后缀表示 unsigned long 类型
long long e = 100LL;   // 使用 LL 后缀表示 long long 类型
unsigned long long f = 100ULL; // 使用 ULL 后缀表示 unsigned long long 类型
float g = 1.23f;        // 使用 f 后缀表示 float 类型
double h = 1.23;        // 默认为 double 类型
long double i = 1.23L; // 使用 L 后缀表示 long double 类型

cout << "int: " << a << endl;
cout << "unsigned int: " << b << endl;
cout << "long: " << c << endl;
cout << "unsigned long: " << d << endl;
cout << "long long: " << e << endl;
cout << "unsigned long long: " << f << endl;
cout << "float: " << g << endl;
cout << "double: " << h << endl;
cout << "long double: " << i << endl;
```

### 8. `**z**`（用于指针类型）
在一些平台上，`z` 后缀被用于表示特定指针类型的字面量，通常用于一些底层库中。

























## 数据类型转换
### 1. 隐式转换
隐式转换是指编译器自动完成的类型转换，不需要显式指定。常见的隐式转换包括：

+ **算术类型提升**：如 `char`、`short` 等类型在算术运算中会自动提升为 `int` 类型。
+ **整型到浮点型转换**：当整数和浮点数一起运算时，整数会自动转换为浮点型。例如：`int` 转 `float`。如a=b*1.0。
+ **小范围到大范围类型转换**：如 `int` 到 `double` 的转换，因为不会丢失数据。

**示例**：

```cpp
int a = 10;
double b = a;  // a 自动转换为 double 类型，b = 10.0
```

虽然隐式转换在大多数情况下很方便，但有时会产生精度丢失或编译警告。因此，复杂的转换通常通过显式转换来完成。

### 2. 显式转换
显式转换需要明确指定类型转换。C++ 中有四种类型的显式转换方式，分别是 `static_cast`、`dynamic_cast`、`const_cast` 和 `reinterpret_cast`，其中 `static_cast` 是最常用的。

#### 2.1 `static_cast`
`static_cast` 用于大多数基本类型之间的转换，也是最安全的显式转换方式，主要用于：

+ 基本数据类型之间的转换，例如 `int` 到 `float`、`double` 到 `int`。
+ 指针的上行和下行转换，但通常只用于具有继承关系的类。

**示例**：

```cpp
int a = 10;
double b = 2/static_cast<double>(a);  // a 转换为 double 类型，b = 10.0
double c = 9.8;
int d = static_cast<int>(c);  // c 转换为 int 类型，d = 9
```

#### 2.2 `dynamic_cast`
`dynamic_cast` 主要用于**具有继承关系的指针或引用之间的转换**，并且通常用于将父类指针安全地转换为子类指针。`dynamic_cast` 需要类具有虚函数，以支持运行时类型检查（RTTI）。如果转换失败，会返回 `nullptr`（指针转换）或抛出异常（引用转换）。

**示例**：

```cpp
class Base {
    virtual void func() {}  // 虚函数，支持 RTTI
};

class Derived : public Base {};

Base* basePtr = new Derived();
Derived* derivedPtr = dynamic_cast<Derived*>(basePtr);  // 成功转换
```

#### 2.3 `const_cast`
`const_cast` 用于移除 `const` 或 `volatile` 属性，主要应用于需要对 `const` 对象进行修改的情况，但必须保证移除后不会违反常量性。

**示例**：

```cpp
const int a = 10;
int* b = const_cast<int*>(&a);  // 移除 const 属性
*b = 20;  // 可能会导致未定义行为
```

#### 2.4 `reinterpret_cast`
`reinterpret_cast` 是一种强制类型转换，可以用于任意指针类型之间的转换或整数和指针之间的转换，但很危险。通常用于底层操作，比如处理底层字节、设备地址等，不建议在普通代码中使用。

**示例**：

```cpp
int a = 10;
int* p = &a;
char* pChar = reinterpret_cast<char*>(p);  // 将 int* 转换为 char*
```



















## 字符（char）与 字符串（string）
### 字符与字符串之间的转换
· string --> 字符数组：

```cpp
string str = "Hello";
const char* cstr = str.c_str(); // 转换为字符数组，用法为c_str()
```

· 字符数组 --> string：

```cpp
char cstr[] = "Hello";
string str(cstr);  // 从字符数组构造字符串,直接str()
```

### 字符串操作函数：
#### 1. substr
用于提取子字符串。

```cpp
std::string str = "Hello, World!";
std::string sub = str.substr(0, 5); 
// 从索引0开始，长度为5
// sub = "Hello"
```

#### 2. empty
检查字符串是否为空。

```cpp
if (str.empty()) std::cout << "String is empty." << std::endl; 
```

#### 3. size
返回字符串中的字符数（与length 等效）。

```cpp
string str = "Hello";
size_t len = str.size();   // len = 5
```

#### 4. erase
删除字符串中的字符或子字符串。

```cpp
string str = "Hello, World!";
str.erase(5, 7); // 从索引5开始删除7个字符
// str = "Hello!"
```

#### 5. `size()` 或 `length()`
`size()`和`length()`作用是相同，返回字符串中的字符数。

```cpp
string str = "Hello, World!";
cout << "Length: " << str.size(); // 或者 str.length()
```

#### 6. `char *strncpy(char *s1, const char *s2, size_t n);`
**功能**：将最多 `n` 个字符从 `s2` 复制到 `s1`。（如果省去n，则默认全部复制，这时候函数名为strcpy）

**用法**：

+ `strncpy` 会复制 `s2` 的最多 `n` 个字符到 `s1`，如果 `s2` 的长度小于 `n`，则会用 `\0` 填充 `s1`。
+ 如果 `s2` 长度大于 `n`，则只会复制前 `n` 个字符。

**注意事项**：

+ 如果 `s2` 的长度小于 `n`，需要注意 `s1` 会被填充 `\0`，因此有可能在目标字符串中留下多余的 `\0`。
+ 如果 `s2` 长度超过 `n`，目标字符串不会被正确终止。

**例子**：

```cpp
char s1[20];
char s2[] = "Hello, World!";
strncpy(s1, s2, 5);  // 只复制前5个字符 "Hello"
```

#### 7. `char *strncat(char *s1, const char *s2, size_t n);`
**功能**：将最多 `n` 个字符从 `s2` 追加到 `s1` 的末尾。（如果省去n，则默认全部追加，这时候函数名为strcat）

**用法**：

+ `strncat` 会将 `s2` 中最多 `n` 个字符追加到 `s1`，并在末尾加上 `\0`。
+ `s1` 必须有足够的空间来容纳追加的内容。

**注意事项**：

+ 和 `strcat` 一样，如果 `s1` 没有足够空间，会导致缓冲区溢出。
+ 不会追加超过 `n` 个字符。

**例子**：

```cpp
char s1[20] = "Hello, ";
char s2[] = "World!";
strncat(s1, s2, 3);  // s1 变成 "Hello, Wor"
```

#### 8. `int strncmp(const char *s1, const char *s2, size_t n);`
**功能**：比较 `s1` 和 `s2` 的前 `n` 个字符。“默认”s1>s2，对了就是1，错了就是-1，一样就是 0 。（如果省去n，则默认逐个比较直至结束，这时候函数名为strcmp）

**注意事项**：

+ 如果比较到 `n` 个字符或遇到 `'\0'`，就停止比较。
+ 需要确保不会超出 `s1` 和 `s2` 的长度。
+ `'\0'`可视为最小的。

**例子**：

```cpp
char s1[] = "Hello";
char s2[] = "Hell";
int result = strncmp(s1, s2, 4);  // result == 0，前四个字符相同
```

#### 9. `size_t strlen(const char *s);`
**功能**：计算字符串 `s` 的长度，**不包括**字符串的终止符 `\0`。

**返回值**：

+ 返回 `s` 中字符的数量。

**注意事项**：

+ `strlen` 遇到字符串结束标志 `\0` 时停止，计算的是字符数，不包括 `\0`。
+ 如果传入的字符串没有正确终止，会导致未定义行为。

**与 **`**sizeof**`** 的区别：**

+ `sizeof` 返回变量或类型的大小（以**字节**为单位），对于字符串常量，它返回的是字符串所占的内存大小，包括字符串结束符 `\0`。
+ `strlen` 返回字符串的长度（不包括 `\0`），它只计算字符串中实际的字符数量。

**例子**：

```cpp
char s[] = "Hello";
printf("%lu\n", sizeof(s));    // 6 (包括 '\0')
printf("%lu\n", strlen(s));    // 5 (不包括 '\0')
```

#### 10. `char *strtok(char *s1, const char *s2);`
**功能**：将字符串 `s1` 分割成一系列的子字符串，分隔符为 `s2`。

**用法**：

+ 第一次调用时，传入待分割的字符串 `s1`，后续调用时，传入 `NULL` 来继续分割上次剩余的字符串。
+ 每次调用会返回指向下一个子字符串的指针。

**注意事项**：

+ `strtok` 会修改原始字符串，将分隔符替换为 `\0`。
+ 不适合多线程程序，因为它会使用静态内部状态。
+ 假如vs表示不安全，可以添加 **#define _CRT_SECURE_NO_WARNINGS** 在开头（宏不用;）

**例子**：

```cpp
char s[] = "Hello, World!";
char *token = strtok(s, ", ");  // token = "Hello"，token必须定义为指针
token = strtok(NULL, ", ");     // token = "World!"
```

















### 输入
#### 1.cin
```cpp
char a[50];
cin >> a;
cout << a;
//直接输入字符串，遇到空格停止
//输入：12 23
//输出：12
```

#### 2.cin.get()
```cpp
char ch;
cin.get(ch);  // 读取一个字符，包括空格、换行符等所有字符
cout << "You entered: " << ch << endl;
//若 int ch;
//输入：1
//输出：49

char str[100];
cout << "Enter a line of text: ";
cin.get(str, 100);  // 读取一行最多100个字符
cout << "You entered: " << str << endl;
//到换行符为止，数量不够也就算了
//如果输入超过了数量，只会读取前 n-1 个字符，并在结尾加上'\0'表示字符串的结束
```

#### 3.`cin.getline()`
`cin.getline()` 用于读取一行**字符**，包括空格，但不会读取换行符。它会将换行符替换为字符串结束符 `'\0'`。`cin.getline()` 可以防止缓冲区溢出，通过指定最大字符数来限制读取的长度。

```cpp
char str[100];

cout << "Enter a line of text: ";
cin.getline(str, 100);  // 读取一行文本（最多n-1个字符）

cout << "You entered: " << str << endl;
```

#### 4.`getline()`
getline(cin,string) 用于从输入流中读取一整行**字符串**，<font style="color:rgb(0,0,255);">包括空格</font>，<font style="color:rgb(0,0,255);">直到遇到换行符。</font>

```cpp
string input;
cout << "Enter a line of text: ";
getline(cin, input);   // 读取整行输入,注意前面"cin,"
cout << "You entered: " << input << endl;
return 0;
```

#### 5.`cin.ignore()`
```cpp
cin.ignore(int n = 1, int delim = '\n')
```

+ `**n**`（可选，默认为 1）：表示要忽略的字符数。
+ `**delim**`（可选，默认为 `'\n'`）：指定忽略直到遇到的字符（包括该字符）。

**便捷写法:**

```cpp
cin.ignour(10,)
```

**作用举例：**

```cpp
int num;
char ch;

cout << "Enter an integer: ";
cin >> num;  

cin.ignore();  // 默认忽略输入中的一个字符
//假如没有ignour(),输入num时携带'\n'残留，在下一次cin.get(ch)时进入ch

cout << "Enter a character: ";
cin.get(ch);  // 读取一个字符，包括换行符

cout << "You entered: " << num << " and " << ch << endl;
```

















## 枚举类型（`enum`）
### 1. 基本的枚举类型
一个最简单的枚举类型定义如下：

```cpp
enum Color {Red,Green,Blue};
Color color = Green;  //通过枚举类型来声明变量
```

这段代码定义了一个名为 `Color` 的枚举类型，并为它定义了三个枚举常量：`Red`、`Green` 和 `Blue`。这些常量会自动赋予一个整数值，从 0 开始（依次递增）。即：

+ `Red = 0`
+ `Green = 1`
+ `Blue = 2`

### 2. 指定枚举常量的值
```cpp
enum Color {Red = 10,Green = 20,Blue = 30};   //显式地指定枚举常量的值
```

### 3. 枚举底层类型
默认情况下，枚举常量的底层类型是 `int`。但可以指定枚举的底层类型.

```cpp
enum Color : unsigned char {Red,Green,Blue};
```

在这个例子中，`Color` 枚举的底层类型是 `unsigned char`，而不是默认的 `int`。

### 4. 枚举和数组的结合
可以用枚举作为数组的索引：

```cpp
enum Color {Red,Green,Blue,ColorCount};

int colorValues[ColorCount] = {255, 0, 0};  // 数组大小等于枚举常量数量
```

### 举例：
```cpp
#include<iostream>
using namespace std;
int main() {
  enum Test { AA = 2, BB, CC = 3, DD = 1, EE };
  Test haha=BB;
  //这里BB顺着AA递增，即为3；同理，EE为2；
    
  if(haha==3)cout<<"win!"<<endl;  //3换成BB结果不变
  else cout<<"lose!"<<endl;
  //输出：win! 

  int my=AA;
  cout<<my<<endl;
  //输出：2

  return 0;
}
```



### 5.`enum class` 
C++11 引入的一个强类型枚举，相对于传统的 `enum` 提供了更强的类型安全和作用域控制`enum class` 可以避免名称冲突，并且不自动将枚举值转换为整数。

### 特性
1. **作用域控制**：
    - 在 `enum class` 中，枚举值不会自动放入外部作用域，而是需要通过 `EnumName::Value1` 这种方式来访问。
    - 这样可以避免与其他变量或枚举值产生命名冲突。
2. **强类型**：
    - `enum class` 的值不能隐式转换为整数类型。也就是说，`EnumName::Value1` 不能直接赋值给一个整数，除非你显式进行类型转换。
    - 这增强了类型安全，避免了可能的错误。
3. **显式指定底层类型**：
    - 可以通过 `: underlying_type` 来指定 `enum class` 的底层类型（默认是 `int`）。

### 示例代码
```cpp
#include <iostream>

enum class Color {Red,Green,Blue};

int main() {
    Color color = Color::Red;

    // 编译错误: 不能将 Color 直接赋给 int
    // int color_value = color;

    // 显式转换为整数
    int color_value = static_cast<int>(color);

    std::cout << "Color as integer: " << color_value << std::endl;
    return 0;
}
```

### `enum class` 的优势
+ **避免名称冲突**：传统的 `enum` 会将所有枚举值放在全局作用域，而 `enum class` 会将它们封装在指定的枚举类型作用域中。
+ **类型安全**：由于 `enum class` 是强类型的，它不能隐式转换为其他类型，因此更加安全。
+ **可选的底层类型**：可以自定义底层类型来节省内存，尤其在处理较大枚举时。

### 
### 












## 引用（Reference）
引用是 C++ 中的一种数据类型，它是某个变量的**别名**。引用变量与原始变量**共享**相同的内存地址，因此修改引用变量的值，也会修改原始变量的值。注：引用变量不能作为**数组**大小。

### 1. 引用的基本语法
声明一个引用变量时，在类型和变量名之间使用 `&` 符号。例如：

```cpp
int a = 10;
int& ref = a;  // ref 是 a 的引用
```

### 2. 引用的特点：
+ **必须初始化**：引用变量必须在声明时被初始化。
+ **不可更改指向**：引用一旦绑定，就不能指向其他变量。引用永远指向它**最初**绑定的变量。

```cpp
int x = 5;
int y = 10;
int& ref = x; // ref现在是x的别名，对ref的修改将直接影响x
ref = y;       
// 修改ref，由于ref就是x的别名，相当于x也发生了变化
// 即此时 x=10, y=10, ref=10
```

### 3. 引用作为函数参数
引用允许函数直接修改调用者的参数，而无需复制数据。

```cpp
void increment(int& n) {
    n++;  // 修改传入的变量
}

int main() {
    int a = 5;
    increment(a);  // 传入 a 的引用
    cout << a;  // 输出 6
}
```

### 4. 引用返回值
引用也可以作为函数的返回值，允许修改调用者传入的变量。

```cpp
int& getElement(int arr[], int index) {  // 关键是函数名前面有 &
    return arr[index];  // 返回数组元素的引用 
}

int main() {
    int arr[] = {1, 2, 3};
    getElement(arr, 1) = 10;  // 修改数组元素
    cout << arr[1];  // 输出 10
}
```

+ `getElement` 返回数组元素的引用，可以直接修改数组中的数据。



















## 符号常量（`constant`）
符号产量是指在程序执行过程中其值不会改变的量。

### 1. `#define` 宏常量
`#define` 用于定义符号常量，它在预处理阶段进行替换。宏常量通常没有类型，且没有作用域限制。

```cpp
#define PI 3.14159
```

在代码中，`PI` 会被替换为 `3.14159`，这在编译阶段完成。注意，`#define` 是一个预处理指令，不会进行类型检查，因此不能直接用在复杂的计算中，容易出现错误。

### 2. `const` 常量
`const` 关键字可以用来定义类型安全的常量。通过 `const` 声明的常量具有指定类型，并且只能赋值一次。

```cpp
const double PI = 3.14159;
```

这种方式与 `#define` 不同，`const` 常量有明确的类型，并且可以在代码中像变量一样使用。`const` 常量的作用域是局部或全局，取决于它的位置。















## **自动存储类别**和**静态存储类别**
### 1. **自动存储类别（**`**auto**`**）**
+ **生命周期**：变量的生命周期从其定义的作用域开始，到作用域结束时自动销毁。
+ **存储位置**：通常存储在栈区。
+ **初始化**：每次进入作用域时，变量会被重新初始化。
+ **特点**：大多数局部变量默认具有自动存储类别，内存管理由编译器自动处理。

```cpp
void func() {
    int x = 10;  // 自动存储类别
}  // x 在函数结束时销毁
```

### 2. **静态存储类别（**`**static**`**）**
+ **生命周期**：变量的生命周期从程序启动到程序结束。即使在作用域之外，也会一直存在。
+ **存储位置**：通常存储在静态存储区。
+ **初始化**：变量**只**会在第一次调用时初始化**一次**，之后保持其值。数值变量默认初始化为**0**。
+ **特点**：通过 `static` 关键字声明的变量或全局变量具有静态存储类别，生命周期贯穿程序的整个运行过程。

**示例**：

```cpp
void func() {
    static int x = 10;  // 静态存储类别
    x++;
    std::cout << x << std::endl;  // 保持上次值
}
```

---

## 左值（Lvalue）和右值（Rvalue）
**值类别**定义了表达式的结果是**可以被修改的**还是**临时的**。左值和右值描述了对象在内存中的**存在方式**和**生命周期**，并决定了它们如何与引用、赋值等操作交互。

**左值（Lvalue）**：

表示一个持久的对象，它有一个明确的内存地址。可以出现在**赋值语句的左边**，也就是可以**被修改**的对象。

**右值（Rvalue）**：

表示一个临时的、没有名称的对象，它没有明确的内存地址，通常用于计算表达式的结果、返回临时对象等场景。右值不能出现在赋值语句的左边。

---

## 


# 位运算与表达式
## 位运算
### 1. 位与运算符  &
功能：对两个二进制数的每一位进行与运算，只有当两位都是1时结果才为1。

示例：

```cpp
int a = 5;  // 二进制 0101
int b = 3;  // 二进制 0011
int result = a & b; // 结果为 1，二进制 0001
```

### 2. 位或运算符  |
功能：对两个二进制数的每一位进行或运算，只要有一位为1，结果就为1。

示例：

```cpp
int a = 5;  // 二进制 0101
int b = 3;  // 二进制 0011
int result = a | b; // 结果为 7，二进制 0111
```

### 3. 位异或运算符  ^
功能：对两个二进制数的每一位进行异或运算，当两位不同（一个为1一个为0）时结果为1。

示例：

```cpp
int a = 5;  // 二进制 0101
int b = 3;  // 二进制 0011
int result = a ^ b; // 结果为 6，二进制 0110
```

### 4. 取反运算符  ~
功能：对一个二进制数的每一位进行取反运算，0变为1，1变为0。

示例：

```cpp
int a = 5;  // 二进制 0101
int result = ~a; // 结果为 -6，二进制 1010（补码表示）
```

### 5. 左移运算符  <<
功能：将一个数的二进制位向左移动指定的位数，左移一位相当于乘以2。

示例：

```cpp
int a = 5;  // 二进制 0101
int result = a << 1; // 结果为 10，二进制 1010
```

### 6. 右移运算符  >>
功能：将一个数的二进制位向右移动指定的位数，右移一位相当于整除2。

示例：

```cpp
int a = 5;  // 二进制 0101
int result = a >> 1; // 结果为 2，二进制 0010
```

















## **Lambda 表达式**
Lambda 表达式是一种简洁的方式来定义匿名函数对象（函数指针）。Lambda 表达式允许你在代码中内联定义和使用函数，而无需显式定义一个命名函数。这使得代码更加简洁、灵活，尤其适用于那些需要将短小的函数传递给其他函数的场景，即一种**简化函数**。

### Lambda 表达式的基本语法
```cpp
[捕获列表](参数列表) -> 返回类型 {函数体}
```

+ **捕获列表（Capture List）**：指定 Lambda 可以使用外部作用域中的哪些变量。可以按值捕获、按引用捕获，或者不捕获任何外部变量。
+ **参数列表（Parameter List）**：指定 Lambda 接受的参数（和普通函数一样）。如果没有参数，可以省略。例如：(node const& a, node const& b)
+ **返回类型（Return Type）**：指定 Lambda 返回值的类型。如果 Lambda 不返回任何值，可以省略。
+ **函数体（Body）**：Lambda 的实际代码，表示要执行的操作。

### 1. 基本示例
```cpp
int main() {
    // 定义一个没有参数的 Lambda，返回常数 10
    auto lambda = []() { return 10; };
    
    cout << "Lambda result: " << lambda() << endl;
    //输出：Lambda result: 10
    return 0;
}
```

### 2. 带参数的 Lambda
Lambda 表达式也可以接受参数，就像普通函数一样：

```cpp
// 定义一个带参数的 Lambda
auto sum = [](int a, int b) { return a + b; };
    
cout << "Sum: " << sum(5, 10) << endl;
//输出：Sum: 15
```

### 3. 捕获外部变量
#### 3.1 按值捕获
```cpp
int x = 10;
int y = 20;
    
// 按值捕获变量 x 和 y
auto sum = [x, y]() { return x + y; };
    
cout << "Captured sum: " << sum() << endl;  // x 和 y 按值捕获
//输出：Captured sum: 30

// 修改原始变量 x 和 y
x = 30;
y = 40;

// 再次调用 Lambda
cout << "Captured sum after modification: " << sum() << endl;  
// 依然输出： Captured sum after modification:30
```

在这个例子中，`x` 和 `y` 被按值捕获，意味着它们的拷贝被传递给 Lambda，即使 `x` 或 `y` 后续发生变化，Lambda 中的值也不会改变。

#### 3.2 按引用捕获
```cpp
int x = 10;
int y = 20;
    
// 按引用捕获变量 x 和 y
auto sum = [&x, &y]() { return x + y; };
//即 & 的区别

// 修改外部变量
x = 30;
y = 40;
    
// x 和 y 按引用捕获
cout << "Captured sum after modification: " << sum() << endl;
//输出：Captured sum after modification: 70
```

在这个例子中，`x` 和 `y` 是按引用捕获的，因此 Lambda 表达式会直接操作外部变量的原始值，而不是它们的副本。

#### 3.3 捕获所有变量
+ 按**值**捕获所有变量：`[=]`
+ 按**引用**捕获所有变量：`[&]`
+ 这样是会捕获**无关变量**的。

```cpp
int x = 10, y = 20;
    
// 按值捕获所有变量
auto sum_by_value = [=]() { return x + y; };
    
// 按引用捕获所有变量
auto sum_by_reference = [&]() { return x + y; };
    
x = 50;
y = 60;

// 捕获时按值
cout << "Sum by value: " << sum_by_value() << endl; 
//输出：Sum by value: 30

// 捕获时按引用	
cout << "Sum by reference: " << sum_by_reference() << endl;
//输出：Sum by reference: 110
```

### 4. Lambda 的返回类型
C++11 中，如果 Lambda 的返回类型可以推导，则可以省略返回类型，C++ 会自动推导。你也可以显式指定返回类型。

#### 4.1 自动推导返回类型
```cpp
// 返回类型自动推导为 int
auto multiply = [](int a, int b) { return a * b; };

cout << "Product: " << multiply(5, 6) << endl;
```

#### 4.2 显式指定返回类型
```cpp
// 显式指定返回类型为 long
auto multiply = [](int a, int b) -> long { return a * b; };
    
cout << "Product: " << multiply(5, 6) << endl;
```

### 5. Lambda 表达式的实际应用
Lambda 表达式常用于以下几种场景：

1. **作为回调函数**：很多 STL 算法（如 `std::sort`, `std::for_each`）都可以接受 Lambda 表达式作为回调函数。（可参见章节 sort ）
2. **短小的函数**：当你需要一个简单的函数，不想为其单独定义一个命名函数时，可以使用 Lambda 表达式。
3. **多线程编程**：在并发编程中，Lambda 表达式可以非常方便地作为线程的任务传递给 `std::thread`。



























## ASCII码表
### 分区记忆
#### A. **控制字符（0-31）**
+ **0**: `NUL`（空字符）
+ **9**: `TAB`（制表符）
+ **10**: `LF`（换行）
+ **13**: `CR`（回车）
+ **27**: `ESC`（转义符）
+ **32**: `SPACE`（空格）

#### B. **数字字符（48-57）**
#### C. **大写字母（65-90）**
#### D. **小写字母（97-122）**
#### E. **标点符号和其他可打印字符（32-47, 58-64, 91-96, 123-126）**
+ **标点符号**:
    - `'!'` = 33, `'"'` = 34, `'#'` = 35, ...
    - `'('` = 40, `')'` = 41, `'*'` = 42, `'+'` = 43, ...
    - `';'` = 59, `':'` = 58, `'<'` = 60, `'>'` = 62, `'?'` = 63, ...

### **关键值和偏移量**
+ `'**0**'` = **48**，`'**9**'` = **57**，`'**A**'` = **65**，`'**a**'` = **97**
+ 大写字母和小写字母之间的 ASCII 值有固定差距：大写字母的 ASCII 值比小写字母小 **<font style="color:#df2a3f;">32</font>**。

![](https://cdn.nlark.com/yuque/0/2024/jpeg/50259711/1732069472374-1cadf216-f613-42e0-8ccf-bf3107f1c7a4.jpeg)





















## <font style="color:rgb(6, 6, 7);">逻辑运算符的短路行为</font>
1. **<font style="color:rgb(6, 6, 7);">逻辑与（</font>**`**&&**`**<font style="color:rgb(6, 6, 7);">）</font>**<font style="color:rgb(6, 6, 7);">：</font>
    - <font style="color:rgb(6, 6, 7);">如果第一个操作数为</font>`false`<font style="color:rgb(6, 6, 7);">，则整个表达式的结果为</font>`false`<font style="color:rgb(6, 6, 7);">，因此第二个操作数不会被计算（因为结果已经确定）。</font>
2. **<font style="color:rgb(6, 6, 7);">逻辑或（</font>**`**||**`**<font style="color:rgb(6, 6, 7);">）</font>**<font style="color:rgb(6, 6, 7);">：</font>
    - <font style="color:rgb(6, 6, 7);">如果第一个操作数为</font>`true`<font style="color:rgb(6, 6, 7);">，则整个表达式的结果为</font>`true`<font style="color:rgb(6, 6, 7);">，因此第二个操作数不会被计算（因为结果已经确定）。</font>
3. **<font style="color:rgb(6, 6, 7);">逻辑非（</font>**`**!**`**<font style="color:rgb(6, 6, 7);">）</font>**<font style="color:rgb(6, 6, 7);">：</font>
    - `!`<font style="color:rgb(6, 6, 7);">运算符没有短路行为，因为它只作用于单个操作数。</font>

### <font style="color:rgb(6, 6, 7);">应用示例：</font>
```cpp
int a = 1, b = 1;
if (a == 2 && ++b == 2) cout << "true" ;  //a==2返回false，判断结束，轮不到++b
else cout << "false" ;
cout << a << " " << b << endl;
//输出 false 1 1

a = 1, b = 1;
if (a == 1 || ++b == 10) cout << "true" ;  //a==1返回true，判断结束，轮不到++b
else cout << "false" ;
cout << a << " " << b << endl;
//输出 true 1 1

a = 1;
if (a++ == 2) cout << "true" ;  //这里a先判断 ==2，再++
else cout << "false" ;
cout << a << endl;
//输出 false 2

a = 1;
if (++a == 2) cout << "true" ;  //这里a先++，再判断 ==2
else cout << "false" ;
cout << a << endl;
//输出 true 2
```

























# 指针与内存管理
## 指针
### 1. **指针的本质**
指针存储的是另一个变量的**内存地址**，通过指针可以访问和操作该位置的数据。

+ **指针类型**：指针有类型，指针的类型决定了它指向的变量的类型。例如，`int*`类型的指针指向的是一个整数类型的变量，`char*`类型的指针指向的是一个字符类型的变量。

### 2. **指针的声明和初始化**
指针的声明方式为：`数据类型* 指针名称;``*`表示这是一个指针变量。

```cpp
int* ptr;  // 指向整数类型的指针
```

在声明指针时，通常需要将它**初始化**为一个有效的内存地址。如果没有初始化，指针会指向一个不确定的地址，可能导致程序出错。

```cpp
int x = 10;
int* ptr = &x;  // &x表示取变量x的内存地址
```

此时，`ptr`就是一个指向`x`的指针，`*ptr`则可以访问到`x`的值。

### 3. **指针的操作**
+ **取地址操作符（&）**：获取变量的内存地址。

```cpp
int x = 10;
int* ptr = &x;  // ptr保存的是x的地址
```

+ **解引用操作符（*）**：通过指针访问指针所指向的内存位置的值。

```cpp
int x = 10;
int* ptr = &x;
cout << *ptr;  // 输出10，*ptr是解引用操作，得到ptr指向的值
```

### 4. **指针的用途**
+ **动态内存分配**：在C++中，通过指针可以动态地申请和释放内存。常用的操作包括`new`和`delete`。

```cpp
int* ptr = new int;  // 动态分配内存
*ptr = 20;           // 给指针指向的内存赋值
cout << *ptr;        // 输出20
delete ptr;          // 释放动态分配的内存
```

+ **函数参数传递**：指针可以作为函数参数传递，**允许**函数**修改**调用者提供的变量的值。

```cpp
void modify(int* ptr) {
    *ptr = 20;  // 修改指针指向的值
}

int x = 10;
modify(&x);  // 传递x的地址
cout << x;   // 输出20
```

+ **实现复杂数据结构**：指针是实现链表、树等复杂数据结构的基础。在这些数据结构中，节点之间通过指针连接。

### 5. **指针的常见陷阱**
+ **野指针**：如果指针没有被初始化，或者指向一个已经释放的内存地址，它就会成为“野指针”，访问这种指针会导致未定义行为。

```cpp
int* ptr;  // ptr没有初始化，指向一个未知地址
cout << *ptr;  // 这是危险的，可能导致崩溃
```

+ **空指针（Null Pointer）**：空指针是一个不指向任何有效内存地址的指针。在使用指针之前，最好检查它是否为空。

```cpp
int* ptr = nullptr;  // 空指针
if (ptr != nullptr) {
    // 使用ptr之前先检查
}
```

+ **内存泄漏**：在使用动态内存分配时，如果忘记释放内存，可能会导致内存泄漏。要确保使用`delete`释放`new`分配的内存。

```cpp
int* ptr = new int(10);
// 使用完ptr后要释放内存
delete ptr;
```

+ **指针算术**：指针不仅可以存储内存地址，还可以进行加减运算。指针算术允许你通过指针操作数组元素等。

```cpp
int arr[] = {10, 20, 30};
int* ptr = arr;  // ptr指向arr[0]
cout << *(ptr + 1);  // 输出20，ptr + 1指向arr[1]
```

### 6. **指针与数组的关系**
数组名本身就是一个常量指针，指向数组的第一个元素。因此，你可以用指针访问数组元素，或者通过数组名来实现指针的功能。

```cpp
int arr[] = {10, 20, 30};
int* ptr = arr;  // ptr指向arr[0]
cout << *ptr;    // 输出10
cout << *(ptr + 1);  // 输出20
```

### 7. **多级指针**
指针还可以指向其他指针。多级指针的声明方式为`数据类型** 指针名称`。

```cpp
int x = 10;
int* ptr = &x;
int** ptr2 = &ptr;
int*** ptr3 = &ptr2;
cout << ***ptr3;// 输出10，***ptr3解引用三次，获取ptr指向的值
```

### 8. `&a++`与 &++a
`a++` 是后置递增，它先返回`a`当前的**值**（此时即**右值**），然后递增 `a`。因此，`&a++` 会导致编译错误，因为 `a++` 是一个表达式，而不能直接取它的地址。

`++a` 是前置递增，它先递增 `a` 的值，然后返回递增后的值（递增结束后，此时为**左值**），所以可以通过 `&` 运算符取 `a` 的地址。

---

## 通用指针
### 1. `**void***`** 指针的定义**
`void*` 是一种特殊的指针类型，可以指向任何类型的对象或数据，但是它不直接关联任何具体类型。因此，`void*` 被称为“通用指针”或“空指针”。

```cpp
void* ptr;  // 声明一个 void 指针
```

### 2. `**void***`** 的基本用法**
+ **指向任何类型的数据**  
`void*` 指针能够指向任意类型的数据，可以通过将任意类型的指针转换为 `void*`，或者将 `void*` 转换回具体类型的指针。

```cpp
int a = 10;
float b = 3.14f;
char c = 'A';

void* ptr;  // 声明一个通用指针

ptr = &a;    // ptr 指向 int 类型变量
ptr = &b;    // ptr 现在指向 float 类型变量
ptr = &c;    // ptr 现在指向 char 类型变量
```

### 3. **使用 **`**void***`** 指针访问数据**
`void*` 本身不能直接进行解引用，因为它没有类型信息。因此，在使用 `void*` 时，必须先将它转换为正确的类型指针（即通过类型转换）。

```cpp
int a = 10;
void* ptr = &a;

// 将 void* 转换回 int* 来解引用
int* int_ptr = static_cast<int*>(ptr);
cout << *int_ptr << endl;  // 输出 10
```

### 4. **与 **`**void***`** 的类型转换**
+ **将其他指针转换为 **`**void***`：任何类型的指针都可以隐式转换为 `void*`，因为 `void*` 是一个通用指针类型。

```cpp
int x = 10;
float y = 5.5f;

void* ptr1 = &x;  // int* 隐式转换为 void*
void* ptr2 = &y;  // float* 隐式转换为 void*
```

+ **将 **`**void***`** 转换为具体类型的指针**：从 `void*` 转换回具体类型时，需要显式转换（使用 `static_cast` 或 `reinterpret_cast`）。因为 `void*` 不包含类型信息，编译器不知道它实际指向什么类型的数据。

```cpp
void* ptr = &x;
int* int_ptr = static_cast<int*>(ptr);  // 将 void* 转换为 int*
```

---

## **常量指针（constant pointer）和 指针常量（pointer to constant）**
### 1. **常量指针 (Constant Pointer)**
常量指针是指**指针本身**的值是**常量**，不能改变。也就是说，常量指针不能再指向其他位置，但它可以修改所指向地址的内容。

#### 示例：
```cpp
int a = 10;
int b = 20;
int* const ptr = &a;  // ptr 是一个常量指针，指向 int 类型

*ptr = 30;  // 可以修改 ptr 指向的值
// ptr = &b;  // 错误：常量指针 ptr 不能修改指向的地址
```

### 2. **指针常量 (Pointer to Constant)**
指针常量是指指针**指向的数据**是**常量**，不能修改，但指针本身可以改变，指向其他的内存地址。

#### 示例：
```cpp
int a = 10;
int b = 20;
const int* ptr = &a;  // ptr 是一个指向常量 int 的指针

// *ptr = 30;  // 错误：无法通过 ptr 修改所指向的数据
ptr = &b;   // 可以修改 ptr 指向的地址
```

### 3. **同时使用常量指针和指针常量**
可以同时使用常量指针和指针常量，这样既限制指针不能指向其他地址，也限制指针指向的数据不能修改。定义方式如下：

```cpp
const int* const ptr = &a;  // ptr 是一个常量指针，指向常量数据
```

---

## `**.**` 和 `**->**`
`**.**` 和 `**->**`都用于访问对象的成员（属性或方法）。`**.**` 用于通过对象**直接访问**其成员；`**->**` 用于**通过指针**访问对象的成员。

#### 1. `**.**`** 的使用：**
`dot` 操作符（`.`）直接应用于对象（不是指针）。

```cpp
class MyClass {
public:
int x;
};

int main() {
    MyClass obj;
    obj.x = 10;

    // 使用 . 直接访问对象的成员
    cout << obj.x << endl;  // 输出: 10
    return 0;
}
```

#### 2. `**->**`** 的使用：**
`arrow` 操作符（`->`）用于通过指针访问对象的成员。指针指向对象时，我们使用 `->` 来访问该对象的成员。

```cpp
class MyClass {
public:
    int x;
    void print() {
        cout << "x = " << x << endl;
    }
};

int main() {
    MyClass obj;
    obj.x = 10;

    // 使用指针来访问对象
    MyClass* ptr = &obj;

    // 使用 -> 访问成员
    cout << ptr->x << endl;  // 输出: 10
    ptr->print();  // 调用成员函数 print()
    return 0;
}
```

---

## 
# 函数与作用域
## **默认参数（Default Arguments）**
默认参数是指在函数定义时为参数指定一个默认值，当调用该函数时，如果没有提供相应的参数值，则使用这个默认值。

```cpp
// 函数定义，参数a和b有默认值
// 默认实参设置之后，其右侧的变量必须也要设置。
// 即(int a=1,int b) 是不正确的
// 注意点二：不要重复设置默认参数
void printNumbers(int a = 1, int b = 2) {  
    cout << "a: " << a << ", b: " << b << endl;
}

int main() {
    printNumbers();          // 使用默认值，输出: a: 1, b: 2
    printNumbers(10);        // 使用a=10，b使用默认值，输出: a: 10, b: 2
    printNumbers(10, 20);    // 使用a=10，b=20，输出: a: 10, b: 20
    return 0;
}
```





















## **作用域解析运算符   `**::**` **
：：用于指定某个标识符（如变量、函数、类等）属于哪个作用域或命名空间。

### 1. **访问全局变量或函数**
当局部作用域和全局作用域中有同名的变量或函数时，可以使用 `::` 来访问**全局作用域**中的变量或函数。

**例子：**

```cpp
int x = 10;  // 全局变量

int main() {
    int x = 5;  // 局部变量
    cout << "Local x: " << x << endl;        
    cout << "Global x: " << ::x << endl;    // 使用 :: 访问全局变量 x 
    //输出 ： Local x: 5         
    //       Global x: 10
    return 0;
}
```

### 2. **定义类外的类成员函数**
在类的外部定义成员函数时，需要使用 `::` 来指定这个函数是哪个类的成员函数。

**例子：**

```cpp
#include <iostream>
using namespace std;

class MyClass {
public:
    void printMessage();
};

void MyClass::printMessage() {
    cout << "Hello from MyClass!" << endl;
}

int main() {
    MyClass obj;
    obj.printMessage();  // 调用成员函数
    return 0;
}
```

### 3. **访问命名空间中的成员**
`::` 也用于访问命名空间中的元素。当函数、变量或类定义在特定的命名空间中时，使用 `::` 来访问它们。

**例子：**

```cpp
namespace MyNamespace {
    int x = 100;
}

int main() {
    cout << "Value of x in MyNamespace: " << MyNamespace::x << endl;
    return 0;
}
```

### 4. **访问类的静态成员**
对于类的静态成员（例如静态变量或静态函数），可以使用 `::` 来访问。

**例子：**

```cpp
class MyClass {
public:
    static int count;          // 静态成员变量
    static void showCount() {  // 静态成员函数
        cout << "Count: " << count << endl;
    }
};

int MyClass::count = 0;  // 静态成员变量的初始化

int main() {
    MyClass::count = 10;  // 访问静态成员变量
    MyClass::showCount();  // 访问静态成员函数
    return 0;
}
```

### 5. **类的继承中的作用域**
如果派生类重写了基类的函数或成员，但你希望在派生类中调用基类的版本，可以使用 `::` 来指定基类的成员。

**例子：**

```cpp
class Base {
public:
    void show() {
        cout << "Base class show()" << endl;
    }
};

class Derived : public Base {
public:
    void show() {
        cout << "Derived class show()" << endl;
        Base::show();  // 使用 Base:: 调用基类的 show()
    }
};

int main() {
    Derived obj;
    obj.show();
    return 0;
}

//输出： Derived class show()
//       Base class show()
```



















## 内联函数（inline function）
内联函数是一种通过在编译时将函数的**代码直接插入**调用处来提高程序执行效率的机制。内联函数的调用不经过常规的函数调用过程，而是直接替换为函数体的代码，这样可以避免函数调用的开销，如栈操作和跳转。

### 内联函数的优点
1. **提高性能**
2. **减少栈空间的使用**
3. **代码简洁**

### 内联函数的限制
1. **不能内联太复杂的函数**
2. **增加代码体积**
3. **编译器的优化：** 最终是否内联函数还是由编译器决定。即使你标记了`inline`，编译器可能根据优化策略选择不内联。

### 使用场景
+ **简单的访问器和设置器（getters and setters）：** 比如返回类成员值的函数。
+ **数学运算或小函数：** 对于计算密集型的小函数，如加法、乘法等。

### 示例
```cpp
inline int square(int x) {  //内联函数的使用就是在函数开头加上 inline
    return x * x;
}

int main() {
    int result = square(5);  // 编译器会将 square(5) 替换为 5 * 5
    cout << "The square of 5 is: " << result << endl;
    return 0;
}
```























## 函数重载
函数重载（Function Overloading）是指在同一个作用域中，允许定义**多个同名**的函数，只要它们的**参数列表不同**（即参数的个数、类型或顺序不同）。函数的返回类型不影响重载，因为编译器是通过参数来区分不同的函数调用。

### 1. **函数重载的规则**
+ **函数名相同**：所有重载函数的名字必须相同。
+ **参数列表不同**：参数的个数、类型或顺序必须不同。
+ **返回类型无关**：仅仅改变函数的返回类型不能构成函数重载。

### 2. **函数重载的示例**
```cpp
void print(int i) {
    cout << "Printing integer: " << i << endl;
}

// 打印浮点数
void print(double d) {
    cout << "Printing double: " << d << endl;
}

// 打印字符串
void print(string s) {
    cout << "Printing string: " << s << endl;
}

int main() {
    print(42);         // 调用 print(int)
    print(3.14);       // 调用 print(double)
    print("Hello");    // 调用 print(string)
    //输出：Printing integer: 42
    //      Printing double: 3.14
    //      Printing string: Hello
    return 0;
}
```

### 3. **重载函数的选择**
编译器会根据传递给函数的**参数类型**来决定调用哪个重载版本。如果传递的参数类型与某个重载版本完全匹配，编译器就会选择该版本。如果没有完全匹配，编译器会尝试将参数**转换**为可接受的类型，若仍然没有匹配项，则会报错。

### 4. **重载的注意事项**
+ **参数个数差异**：参数个数不同是最常见的重载形式。

```cpp
void func(int a) {
    cout << "Function with one integer: " << a << endl;
}

void func(int a, int b) {
    cout << "Function with two integers: " << a << ", " << b << endl;
}
```

+ **参数类型差异**：可以通过参数类型的不同来区分重载函数。

```cpp
void func(double d) {
    cout << "Function with a double: " << d << endl;
}

void func(int i) {
    cout << "Function with an integer: " << i << endl;
}
```

+ **参数顺序差异**：当参数（类型）顺序不同，编译器也能够区分。

```cpp
void func(int a, double b) {
    cout << "Function with an int and a double: " << a << ", " << b << endl;
}

void func(double b, int a) {
    cout << "Function with a double and an int: " << b << ", " << a << endl;
}
```

+ **默认参数与重载**：如果在函数重载中使用了默认参数，可能会导致重载不明确的问题。例如：

```cpp
void func(int a, int b = 10) {
    cout << "a: " << a << ", b: " << b << endl;
}

void func(double a) {
    cout << "a: " << a << endl;
}
```

调用 `func(5)` 时，编译器就会感到困惑，因为它不确定是调用 `func(int, int)` 还是 `func(double)`，因此会报错。

















## 函数模版
函数模板（Function Template） 允许编写一个函数的模板，而不需要指定具体的数据类型。函数模板可以用于创建一个函数，该函数可以处理多种数据类型，避免了为每个数据类型编写重复的代码。

### 1. **函数模板的定义**
函数模板通过使用 `template` 关键字来定义，通常在函数名之前声明一个模板参数。

```cpp
template <typename T>
T add(T a, T b) {
    return a + b;
}
```

在这个例子中，`T` 是一个**模板参数**，表示一个**类型占位符**，`T` 可以是任何数据类型，T 可以在C++标识符的命名规则下任意发挥，如取名：Judy。

`add` 函数的返回类型和参数类型都是 `T`，这样就可以在调用时传递不同的数据类型。

### 2. **如何使用函数模板**
当你调用一个函数模板时，编译器会自动根据传递给模板的实参来推导出类型。例如：

```cpp
template <typename judy>
judy add(judy a, judy b) {
  return a + b;
}

int main() {
    cout << add(10, 20) << endl;         // T推导为 int
    cout << add(3.14, 1.59) << endl;     // T推导为 double
    cout << add(1.5f, 2.5f) << endl;     // T推导为 float
    //输出：30
    //     4.73
    //     4
    return 0;
}
```

### 3. **模板参数的类型**
你可以定义多个模板参数，允许函数**接受多种类型**的参数。例如：

```cpp
template <typename judy, typename fox>
auto add(fox a, judy b) {    //注意，如果返回不明确，函数返回值就写 auto
    return a + b;
}
```

在这个例子中，`T1` 和 `T2` 可以是不同的数据类型，返回类型由 `auto` 推导。这里的 `auto` 让编译器自动推导返回值的类型。

```cpp
cout << add(10, 3.14) << endl;    // T1是int，T2是double
```

### 4. **显式指定模板参数**
虽然编译器可以根据参数自动推导模板参数的类型，但你也可以显式**指定**模板参数（是指定，即告诉编译器类型是什么，而不是强制转化输出）。

```cpp
cout << add<int,double>(10, 2.5) << endl;   
```

### 5. **函数模板的特化（Template Specialization）**
函数模板可以针对特定类型进行特化。这意味着可以为某些数据类型提供一个特定的实现，而不是使用通用模板。（如果差别比较大，那我们为什么不用单纯的函数重载）

```cpp
// 普通模板（用于处理任意类型的单个参数）
template <typename judy>
void print(judy value) {
  cout << "Template version: " << value << endl;
}

// 完全特化（针对 int 类型）
template <>
void print(int value) {
  cout << "Specialized version for int: " << value << endl;
}

// 完全特化（针对 double 类型）
template <>
void print(double value) {
  cout << "Specialized version for double: " << value << endl;
}

// 偏特化（针对第一个参数为 int 类型的情况）
template <typename judy>
void print(int t, judy u) {
  cout << "Specialized version for int and second type: " << t << ", " << u << endl;
}


int main() {
  print(42);             // 使用完全特化，输出：Specialized version for int: 42
  print(3.14);           // 使用完全特化，输出：Specialized version for double: 3.14
  print(42, "hello");    // 使用偏特化，输出：Specialized version for int and second type: 42, hello
  return 0;
}
```

### 7. **注意事项**
+ **函数模板和普通函数的重载**：如果函数模板与普通函数重载存在冲突，编译器可能会产生错误。例如，如果你有一个普通函数与模板函数名字相同，且参数类型不完全匹配，编译器可能无法决定调用哪个函数。

```cpp
void print(int x) {
    cout << "int: " << x << endl;
}

template <typename T>
void print(T x) {
    cout << "Generic: " << x << endl;
}

int main() {
    print(5);  // 会调用 void print(int) 而不是模板函数
}
```

+ **模板实例化**：模板只有在你调用时才会被实例化，编译器会根据实际传入的类型生成特定的函数代码。





















## **函数调用堆栈**
### 1. **代码区（Text Segment）**
+ **用途**：存储程序的机器码，即程序的可执行指令。
+ **特点**：只读、不可修改，多个进程共享，执行效率高。

#### 示例：
```cpp
void foo() {
    int a = 5;
    cout << a << endl;
}

int main() {
    foo();  // 这里 foo() 的机器代码存储在代码区
    return 0;
}
```

### 2. **全局数据区（Data Segment）**
+ **用途**：存储全局变量和静态变量。
+ **特点**：全局变量和静态变量的生命周期是程序运行期间，分为已初始化区和未初始化区（BSS区）。

#### 示例：
```cpp
int globalVar = 10;  // 存储在全局数据区（初始化区）

void foo() {
    static int staticVar = 20;  // 存储在全局数据区（初始化区）
}
```

### 3. **堆区（Heap）**
+ **用途**：用于动态分配内存，通常通过 `new` 或 `malloc()` 分配。
+ **特点**：程序员手动管理内存，分配大小灵活，但容易导致内存泄漏和碎片化。

#### 示例：
```cpp
int* ptr = new int(10);  // 在堆区分配内存
cout << *ptr << endl;  // 输出堆区中的值
delete ptr;  // 释放堆区内存
```

在这个例子中，`new` 操作符为变量 `ptr` 分配了堆区内存，`delete` 操作符用于释放该内存。 

### 4. **栈区（Stack）**
+ **用途**：存储局部变量和函数调用的临时信息（如返回地址）。
+ **特点**：由操作系统自动管理，内存分配和释放迅速，但空间有限，递归调用过多可能导致栈溢出。

#### 示例：
```cpp
void foo() {
    int localVar = 10;  // 存储在栈区
    cout << localVar << endl;
}

int main() {
    foo();  // 在调用 foo() 时，foo 的栈帧会被压入栈中
    return 0;
}
```

在这个例子中，`localVar` 存储在栈区。当 `foo()` 被调用时，它的栈帧会被压入栈中，执行完后栈帧会被弹出。



















# 其他
## 生成随机数
```cpp
#include <iostream>
#include <ctime>    // 时间
#include <random>   // 引入标准库中的随机数相关头文件
using namespace std;

int main() {
    // 使用random_device来生成随机种子
    random_device rd;
    //这时候rd已经可以拿来用了，如：cout<<rd();
    
    default_random_engine generator(rd());
    //或者 default_random_engine generator(static_cast<unsigned int>(time(0)));

    //均匀实数分布，用于生成范围内的浮点数,可以用float，double 或者仅 <>
    uniform_real_distribution<float> distribution1(0.0, 1.0); 

    //均匀整数分布，用于生成范围内的整数,可以用int ,ll 或者仅 <>
    uniform_int_distribution<int> distribution2(0,10);
    
    //正态分布，用于生成符合高斯分布的浮点数。
    normal_distribution<float> distribution3(0,10);

    //伯努利分布，用于生成0或1的随机布尔值。
    bernoulli_distribution distribution4;

    // 生成并打印10个随机数
    for (int i = 0; i < 10; ++i) 
        cout << distribution1(generator) << " ";  
        //11行定义的generator就会在这里使用

    return 0;
}}
```



















## 格式化操作
出了特定指出的，这里的操作都要调用，这个头文件提供格式化相关操作。

### <font style="background-color:rgb(243, 245, 250);">1.</font>`<font style="background-color:rgb(243, 245, 250);">left</font>`<font style="background-color:rgb(243, 245, 250);"> 和 </font>`<font style="background-color:rgb(243, 245, 250);">right</font>`
<font style="background-color:rgb(243, 245, 250);">这两个操作符用于设置输出流的对齐方式。默认情况下，</font>`<font style="background-color:rgb(243, 245, 250);">iostream</font>`<font style="background-color:rgb(243, 245, 250);"> 是右对齐的。特点：都是</font>**<font style="background-color:rgb(243, 245, 250);">粘性设置</font>**<font style="background-color:rgb(243, 245, 250);">。</font>

+ `<font style="background-color:rgb(243, 245, 250);">left</font>`<font style="background-color:rgb(243, 245, 250);">：设置输出流为左对齐。</font>
+ `<font style="background-color:rgb(243, 245, 250);">right</font>`<font style="background-color:rgb(243, 245, 250);">：设置输出流为右对齐（</font>**<font style="background-color:rgb(243, 245, 250);">默认</font>**<font style="background-color:rgb(243, 245, 250);">）。</font>

### <font style="background-color:rgb(243, 245, 250);">2.</font>`<font style="background-color:rgb(243, 245, 250);">setw(int width)</font>`
<font style="background-color:rgb(243, 245, 250);">这个操作符用于设置输出的宽度。如果输出的字段宽度小于指定的宽度，</font>`<font style="background-color:rgb(243, 245, 250);">setw</font>`<font style="background-color:rgb(243, 245, 250);"> 会在字段前填充空格（默认），或者根据对齐方式填充。如果输出字段宽度大于指定的宽度，setw失效，无事发生。</font>

### <font style="background-color:rgb(243, 245, 250);">3.</font>`<font style="background-color:rgb(243, 245, 250);">setfill(char fill)</font>`
<font style="background-color:rgb(243, 245, 250);">这个操作符用于设置</font>**<font style="background-color:rgb(243, 245, 250);">填充</font>**<font style="background-color:rgb(243, 245, 250);">字符。默认的填充字符是空格。</font>

```cpp
int a = 5;
int b = 10;

// 左对齐
cout << left;
cout << "左对齐: " << setw(10) << a << endl;
cout << "左对齐: " << setw(10) << b << endl;
//输出 左对齐:    5       
//     左对齐:    10     

// 右对齐
cout << right;
cout << "右对齐: " << setw(10) << a << endl;
cout << "右对齐: " << setw(10) << b << endl;
//输出  右对齐:     5
//      右对齐:    10

cout << setw(10) << setfill('*') << "" << endl;
//输出  **********
```

### <font style="background-color:rgb(243, 245, 250);">4.</font>`<font style="background-color:rgb(243, 245, 250);">fixed</font>`<font style="color:rgb(6, 6, 7);"> </font>
`fixed`<font style="color:rgb(6, 6, 7);"> 操纵算子用于设置浮点数的输出格式为</font>**<font style="color:rgb(6, 6, 7);">固定小数点</font>**<font style="color:rgb(6, 6, 7);">表示法。当使用 </font>`fixed`<font style="color:rgb(6, 6, 7);"> 时，浮点数将被格式化为小数形式，即使这个数可以表示为一个整数或者科学记数法形式。当使用 </font>`std::fixed`<font style="color:rgb(6, 6, 7);"> 时，通常配合使用 </font>`setprecision`<font style="color:rgb(6, 6, 7);"> 来指定</font>**<font style="color:rgb(6, 6, 7);">小数点后的位数</font>**<font style="color:rgb(6, 6, 7);">，</font>**<font style="color:rgb(6, 6, 7);">多去少补</font>**<font style="color:rgb(6, 6, 7);">。</font>

```cpp
double pi = 3.141592653589793;
// 使用 fixed 和 setprecision 来设置输出格式
cout << fixed << setprecision(2) << pi << endl; 
// 输出: 3.14

double pi = 3.1;
cout << fixed << setprecision(2) << pi << endl;
// 输出：3.10
```

### 5.`showpoint`
`showpoint`输出强制显示小数点后面的零，即使数字的值是整数。

```cpp
double number = 12.0;
    
cout << "Without showpoint: " << number << endl;
//输出   Without showpoint: 12      系统自动省略了小数点和零
    
cout << "With showpoint: " << showpoint << number << endl;
//输出   With showpoint: 12.0000

cout << fixed << showpoint << 12.0 << endl;   
// 输出：12.000000

cout << scientific << showpoint << 12.0 << endl; 
// 输出：1.200000e+01
```

### 6.`<font style="background-color:rgb(243, 245, 250);">scientific</font>`
`scientific`<font style="color:rgb(6, 6, 7);"> 操纵算子用于设置浮点数的输出格式为科学记数法。使用 </font>`scientific`<font style="color:rgb(6, 6, 7);"> 时，也可以配合使用 </font>`setprecision`<font style="color:rgb(6, 6, 7);"> 来指定有效数字的位数，这通常包括小数点后的位数。</font>

```cpp
double largeNumber = 12345678901234567890;
// 使用 scientific 和 setprecision 来设置输出格式
cout << scientific << setprecision(3) << largeNumber << endl; 
// 输出: 1.235e+19
```



+ <font style="color:rgb(6, 6, 7);">当使用 </font>`fixed`<font style="color:rgb(6, 6, 7);"> 或 </font>`scientific`<font style="color:rgb(6, 6, 7);"> 时，它们会影响后续所有浮点数的输出，直到被改变或重置。</font>
+ `setprecision`<font style="color:rgb(6, 6, 7);"> 指定的是</font>**<font style="color:rgb(6, 6, 7);">有效数字</font>**<font style="color:rgb(6, 6, 7);">的位数，而不是小数点后的位数。这意味着如果数字小于 1，指定的精度也包括小数点前的数字。</font>

### 7.<font style="color:rgb(6, 6, 7);">setprecision</font>
`setprecision`<font style="color:rgb(6, 6, 7);"> 用于设置浮点数输出时的</font>**<font style="color:rgb(6, 6, 7);">有效数字的总数</font>**<font style="color:rgb(6, 6, 7);">，包括小数点前的数字和小数点后的数字。若与fixed或scientific同时使用，则改为表示小数点后精度。</font>

### 8.设置bool
这里的可以不使用

+ `boolalpha`<font style="color:rgb(6, 6, 7);">：输出布尔值时使用 </font>`true`<font style="color:rgb(6, 6, 7);"> 和 </font>`false`<font style="color:rgb(6, 6, 7);"> 而不是 </font>`1`<font style="color:rgb(6, 6, 7);"> 和 </font>`0`<font style="color:rgb(6, 6, 7);">。</font>
+ `noboolalpha`<font style="color:rgb(6, 6, 7);">：输出布尔值时使用 </font>`1`<font style="color:rgb(6, 6, 7);"> 和 </font>`0`<font style="color:rgb(6, 6, 7);">。</font>

### **<font style="color:rgb(6, 6, 7);">9.设置数值的基数</font>**
这里的可以不使用

+ `dec`<font style="color:rgb(6, 6, 7);">：设置数值以十进制形式输出。</font>
+ `hex`<font style="color:rgb(6, 6, 7);">：设置数值以十六进制形式输出。</font>
+ `oct`<font style="color:rgb(6, 6, 7);">：设置数值以八进制形式输出。</font>

### **<font style="color:rgb(6, 6, 7);">10.设置精度</font>**
+ `fixed`<font style="color:rgb(6, 6, 7);">：设置浮点数以固定小数点形式输出。</font>
+ `setprecision(int precision)`<font style="color:rgb(6, 6, 7);">：设置浮点数输出时的精度（小数点后的位数）。</font>
+ `scientific`<font style="color:rgb(6, 6, 7);">：设置浮点数以科学记数法形式输出。</font>

### <font style="color:#e4495b;">特别注意</font>
+ **黏性设置**：`left`, `right`, `fixed`, `scientific`, `showpoint`, `boolalpha`, `noboolalpha`, `dec`, `hex`, `oct`, `setfill`
+ **一次性设置**：`setw`, `setprecision`（如果没有与 `fixed` 或 `scientific` 配合使用，则是一次性设置）















---

## **类与接口分离**
源文件包含客户端，例子为WX2.cpp

```cpp
#include <iostream>
#include <string>
#include"Employee.h"  //调用头文件
using namespace std;
int main() {
    Employee employee1("Bob", 34500);  //这里的Employee就相当于一种结构体

    cout << "Employee 1: " << employee1.getName() <<endl;  //操作对象.成员函数（）
    cout << "Yearly Salary: " << employee1.getSalary() << endl;
    
    cout << "Increasing employee salaries by 10%" << endl;
    employee1.setSalary(employee1.getSalary()*1.1);

    return 0;
}
```

头文件包含接口，实现,

接口Employee.h

```cpp
class Employee {
private:  
    std::string Name;  //避免污染不用using，记得要std::
    int salary;
public:
    Employee(std::string, int);  //在接口的函数调用中，只用指明各个参数的类型，不用具体的参数名
    void setName(const std::string );  //const在内部说明该参数值在函数内部不能被修改
    std::string getName() const;  //const在外部说明函数返回的值是常量，不能被修改
    void setSalary(int );
    int getSalary() const;
};  // class 大括号结尾是有‘；’的
```



实现employee.cpp

```cpp
#include<string>
#include<iostream>
#include"Employee.h"  //在实现中也要调用头文件
//这里就不用再提示 class了，我们直接写函数，包括构造函数
Employee::Employee(std::string name, int sal) {  //这是构造函数，作用是在创建类的对象时初始化对象 
    Name = name;                                 //这里的函数都要有Employee::,是来说明这个函数Employee这个类里面
    if (sal < 0)sal = 0;
    salary = sal / 12;
}

void Employee::setName(const std::string name) {
    Name = name;
}

std::string Employee::getName() const {
    return Name;
}

void Employee::setSalary(int sal) {
    if (sal < 0)sal = 0;
    salary = sal / 12;
}

int Employee::getSalary() const {
    return salary * 12;
}
```

---

---

---

---

---

---

---

## 




## 




## 


## 逗号表达式
### 1.逗号表达式结合性优先级最低
```cpp
int value = 0;
cout << value, ++value << value;
//输出： 0
//由于优先级最低, 可以直接将 , 改为 ; 进行理解
//即 cout << value; ++value << value;
//而后面的++value<<value就是一种位运算，但是没赋值
```

### 2.左边子表达式的计算和副作用均先于右边子表达式
```cpp
#include <iostream>
int value = 1;

void f() {
  value += 1;
  std::cout << value;
}

void g() {
  value *= 10;
  std::cout << value;
}

int main() {
  f(), g();
  //输出：220 注意 没有空格
}
```

### 3.整个表达式的值是最右边子表达式的值
```cpp
#include <iostream>

int function() {
  int value = 0;
  return value++, value;
}

int main() {
  std::cout << function();
  //输出： 1
}
```

**部分总结**

```cpp
int x,y,z;
x=y=1;   //y先赋值1，然后y的值赋值给x，本质来讲就是=从右往左的顺序
z=x++,y++,++y;   //由于x++操作在后面，所以先是z=x,然后x++,y++,++y,这里可以把逗号当做；来理解
cout<<x<<" "<<y<<" "<<z;   //输出：2 3 1
// 若z=(x++,y++,++y);  则输出： 2 3 2
```

