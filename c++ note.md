#  STL容器算法  
## `array` 
`array` 是 C++11 引入的一个**模板类**，它的大小是固定的，并且在编译时就确定。

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

### 常用操作和函数:
##### 1. 声明
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

##### 5 插入
· insert()：在向量的某个位置插入元素。

```cpp
vec.insert(vec.begin(), 10);  // 在向量开头插入 10
```

##### 6. 删除元素
· pop_back()：删除vector 中最后一个元素。

· erase()：删除指定位置的元素。

```cpp
vec.pop_back();            // 删除最后一个元素
vec.erase(vec.begin());    // 删除向量的第一个元素
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

### 二维vector
#### <font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);">定义二维vector</font>
1. **<font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);">指定行数和列数初始化</font>**<font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);">  
</font><font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);">创建一个3行4列的二维</font>`<font style="background-color:rgb(252, 252, 252);">vector</font>`<font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);">，初始值为0：</font>

```cpp
vector<vector<int>> mat(3, vector<int>(4, 0));  
vector<vector<vector<int>>> cube(2, vector<vector<int>>(3, vector<int>(4, 0)));
//三维的定义，可以发现多维就是迭代，这是模版类的使用方法
```

2. **<font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);">逐行动态添加</font>**<font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);">  
</font><font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);">创建空二维</font>`<font style="background-color:rgb(252, 252, 252);">vector</font>`<font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);">，然后逐行添加：</font>

```cpp
vector<vector<int>> mat;
mat.push_back({1, 2, 3});       // 添加一行 {1,2,3}
mat.push_back(vector<int>(4,5)); // 添加一行四个5
```

#### <font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);">访问元素</font>
+ <font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);">使用双重下标访问元素（注意索引有效性）：</font>

```cpp
int value = mat[i][j]; // 访问第i行第j列
mat[i][j] = 10;        // 修改元素
```

#### <font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);">遍历二维vector</font>
+ **<font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);">使用范围for循环</font>**<font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);">：</font>

```cpp
for (const auto& row : mat) {      // 遍历每一行
    for (int elem : row) {         // 遍历行内元素
        cout << elem << " ";
    }
    cout << endl;
}
```

+ **<font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);">使用下标遍历</font>**<font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);">：</font>

```cpp
for (size_t i = 0; i < mat.size(); ++i) {
    for (size_t j = 0; j < mat[i].size(); ++j) {
        cout << mat[i][j] << " ";
    }
    cout << endl;
}
```

### <font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);">动态调整大小</font>
+ **<font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);">调整行数</font>**<font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);">：</font>

```cpp
mat.resize(5); // 将行数改为5，新增的行默认是空vector
```

+ **<font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);">调整某一行的大小</font>**<font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);">：</font>

```cpp
mat[0].resize(5); // 将第一行的列数改为5
```

### <font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);">注意事项</font>
1. **<font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);">不规则二维结构</font>**<font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);">：各行长度可以不同，适用于类似邻接表的场景。</font>
2. **<font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);">深拷贝问题</font>**<font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);">：直接赋值会复制所有元素，大二维结构需谨慎操作。</font>
3. **<font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);">函数传参</font>**<font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);">：建议使用</font>`<font style="background-color:rgb(252, 252, 252);">const vector<vector<int>>&</font>`<font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);">传递以避免拷贝。</font>











  


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









## map
`<font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);">map</font>`<font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);"> 用于存储键值对（key-value pairs），并基于键自动排序元素。</font>

### <font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);">核心特性</font>
1. **<font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);">有序性</font>**
    - <font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);">元素按</font>**<font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);">键的升序排列</font>**<font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);">（默认使用</font><font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);"> </font>`<font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);"><</font>`<font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);"> </font><font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);">运算符比较键）。</font>
    - <font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);">支持自定义排序规则，通过提供比较函数或函数对象实现。</font>
2. **<font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);">底层实现</font>**
    - <font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);">基于</font>**<font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);">红黑树</font>**<font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);">（自平衡二叉搜索树），保证插入、删除和查找操作的时间复杂度为 </font>**<font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);">O(log n)</font>**<font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);">。</font>
3. **<font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);">唯一键</font>**
    - <font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);">每个键在</font><font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);"> </font>`<font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);">map</font>`<font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);"> </font><font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);">中</font>**<font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);">唯一</font>**<font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);">，不可重复。若需允许重复键，应使用</font><font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);"> </font>`<font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);">std::multimap</font>`<font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);">。</font>
4. **<font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);">键的类型要求</font>**
    - <font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);">键必须支持</font>**<font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);">严格弱序比较</font>**<font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);">（默认通过</font><font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);"> </font>`<font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);"><</font>`<font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);"> </font><font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);">运算符），或提供自定义比较函数。</font>

### <font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);">常见成员函数</font>
#### <font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);">1. 插入/修改</font>
`**<font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);">insert</font>**`

+ **<font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);">功能</font>**<font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);">：插入键值对。若键已存在，</font>**<font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);">不覆盖原有值</font>**<font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);">。</font>
+ **<font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);">参数</font>**<font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);">：可以是</font><font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);"> </font>`<font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);">pair</font>`<font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);"> </font><font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);">对象或使用</font><font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);"> </font>`<font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);">make_pair</font>`<font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);">。</font>
+ **<font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);">返回值</font>**<font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);">：返回一个</font><font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);"> </font>`<font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);">pair<iterator, bool></font>`<font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);">，其中：</font>
    - `<font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);">iterator</font>`<font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);">：指向插入位置的迭代器。</font>
    - `<font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);">bool</font>`<font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);">：表示是否插入成功（</font>`<font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);">true</font>`<font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);"> </font><font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);">表示插入新键，</font>`<font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);">false</font>`<font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);"> </font><font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);">表示键已存在）。</font>

```cpp
std::map<int, std::string> m;
auto ret = m.insert(std::make_pair(1, "one"));
if (ret.second) {
    std::cout << "Inserted: " << ret.first->second << std::endl;
}
```

`**<font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);">emplace</font>**`

+ **<font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);">功能</font>**<font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);">：直接在容器内构造键值对，</font>**<font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);">避免临时对象拷贝</font>**<font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);">（比</font><font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);"> </font>`<font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);">insert</font>`<font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);"> </font><font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);">更高效）。</font>
+ **<font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);">参数</font>**<font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);">：构造键值对所需的参数。</font>

```cpp
auto ret = m.emplace(2, "two");  // 无需手动创建pair
if (ret.second) {
    std::cout << "Emplaced: " << ret.first->second << std::endl;
}
```

`**<font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);">operator[]</font>**`

+ **<font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);">功能</font>**<font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);">：通过键访问值。若键不存在，</font>**<font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);">自动插入默认值</font>**<font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);">（如</font><font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);"> </font>`<font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);">std::string()</font>`<font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);">）。</font>
+ **<font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);">注意</font>**<font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);">：可能导致意外插入默认值，需谨慎使用。</font>

```cpp
m[3] = "three";         // 插入键3的值
std::cout << m[4];      // 键4不存在，自动插入空字符串！
```

#### <font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);">2. 访问</font>
`**<font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);">at</font>**`

+ **<font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);">功能</font>**<font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);">：安全访问值。若键不存在，</font>**<font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);">抛出</font>****<font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);"> </font>**`**<font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);">std::out_of_range</font>**`**<font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);"> </font>****<font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);">异常</font>**<font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);">。</font>
+ **<font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);">适用场景</font>**<font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);">：需要严格检查键是否存在时使用。</font>

```cpp
try {
    std::cout << m.at(5);  // 若键5不存在，抛出异常
} catch (const std::out_of_range& e) {
    std::cerr << "Key not found!" << std::endl;
}
```

`**<font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);">operator[]</font>**`

+ **<font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);">功能</font>**<font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);">：通过键访问值。若键不存在，自动插入默认值（如</font><font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);"> </font>`<font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);">int()</font>`<font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);">、</font>`<font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);">std::string()</font>`<font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);">）。</font>
+ **<font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);">注意</font>**<font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);">：可能意外修改容器内容，需确保键存在时使用。</font>

`**<font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);">find</font>**`

+ **<font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);">功能</font>**<font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);">：查找键，返回指向该键值对的迭代器。若键不存在，返回</font><font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);"> </font>`<font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);">end()</font>`<font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);">。</font>
+ **<font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);">适用场景</font>**<font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);">：需要判断键是否存在并获取值。</font>

```cpp
auto it = m.find(2);
if (it != m.end()) {
    std::cout << "Found: " << it->second << std::endl;
}
```

`**<font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);">count</font>**`

+ **<font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);">功能</font>**<font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);">：返回键的数量（对</font><font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);"> </font>`<font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);">std::map</font>`<font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);"> </font><font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);">始终是</font><font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);"> </font>`<font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);">0</font>`<font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);"> </font><font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);">或</font><font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);"> </font>`<font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);">1</font>`<font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);">）。</font>
+ **<font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);">适用场景</font>**<font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);">：仅需判断键是否存在，无需获取值。</font>

```cpp
if (m.count(3) > 0) {
    std::cout << "Key 3 exists" << std::endl;
}
```

#### <font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);">3. 删除</font>
`**<font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);">erase</font>**`

+ **<font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);">功能</font>**<font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);">：删除元素。支持通过键、迭代器或迭代器范围删除。</font>
+ **<font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);">返回值</font>**<font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);">：返回删除的元素数量（对</font><font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);"> </font>`<font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);">map</font>`<font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);"> </font><font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);">是</font><font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);"> </font>`<font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);">0</font>`<font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);"> </font><font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);">或</font><font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);"> </font>`<font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);">1</font>`<font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);">）。</font>

```cpp
m.erase(1);                   // 删除键为1的元素（返回1）
auto it = m.find(2);
if (it != m.end()) {
    m.erase(it);              // 通过迭代器删除（无返回值）
}
```

#### <font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);">4. 容量</font>
`**<font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);">size</font>**`

+ **<font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);">功能</font>**<font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);">：返回容器中元素的数量。</font>

```cpp
std::cout << "Size: " << m.size() << std::endl;  // 输出元素总数
```

`**<font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);">empty</font>**`

+ **<font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);">功能</font>**<font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);">：判断容器是否为空。</font>

```cpp
if (m.empty()) {
    std::cout << "Map is empty" << std::endl;
}
```

#### <font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);">5. 迭代器</font>
`**<font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);">begin</font>**`**<font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);"> / </font>**`**<font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);">end</font>**`

+ **<font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);">功能</font>**<font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);">：返回指向容器</font>**<font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);">第一个元素</font>**<font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);">和</font>**<font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);">尾后位置</font>**<font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);">的迭代器（正向遍历）。</font>

```cpp
for (auto it = m.begin(); it != m.end(); ++it) {
    std::cout << it->first << ": " << it->second << std::endl;
}
```

`**<font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);">rbegin</font>**`**<font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);"> / </font>**`**<font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);">rend</font>**`

+ **<font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);">功能</font>**<font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);">：返回</font>**<font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);">反向</font>**<font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);">迭代器，用于</font>**<font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);">逆序遍历</font>**<font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);">（从最后一个元素到第一个）。</font>

```cpp
for (auto rit = m.rbegin(); rit != m.rend(); ++rit) {
    std::cout << rit->first << ": " << rit->second << std::endl;  // 逆序输出
}
```

### <font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);">基本操作示例</font>
```cpp
#include <iostream>
#include <map>
#include <string>

int main() {
    // 定义map，键为int，值为string
    std::map<int, std::string> m;

    // 插入元素
    m.insert(std::make_pair(3, "three"));  // 使用insert
    m[1] = "one";                          // 使用operator[]
    m[5] = "five";
    m[2] = "two";

    // 遍历（有序输出）
    for (const auto& pair : m) {
        std::cout << pair.first << ": " << pair.second << std::endl;
    }
    // 输出顺序：1: one, 2: two, 3: three, 5: five

    // 查找元素
    auto it = m.find(3);
    if (it != m.end()) {
        std::cout << "Found: " << it->second << std::endl;  // 输出: Found: three
    }

    // 删除元素
    m.erase(2);  // 删除键为2的元素

    // 使用at访问（键不存在时抛出异常）
    try {
        std::cout << m.at(4) << std::endl;  // 抛出std::out_of_range
    } catch (const std::out_of_range& e) {
        std::cerr << "Key not found." << std::endl;
    }

    return 0;
}
```

### <font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);">与</font><font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);"> </font>`<font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);">unordered_map</font>`<font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);"> </font><font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);">对比</font>
| <font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);">特性</font> | `<font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);">std::map</font>` | `<font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);">std::unordered_map</font>` |
| :---: | :---: | :---: |
| **<font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);">底层结构</font>** | <font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);">红黑树（有序）</font> | <font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);">哈希表（无序）</font> |
| **<font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);">查找复杂度</font>** | <font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);">O(log n)</font> | <font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);">平均O(1)，最差O(n)</font> |
| **<font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);">插入/删除复杂度</font>** | <font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);">O(log n)</font> | <font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);">平均O(1)，最差O(n)</font> |
| **<font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);">内存占用</font>** | <font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);">较高（树结构额外开销）</font> | <font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);">较低（哈希表可能需扩容）</font> |
| **<font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);">键类型要求</font>** | <font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);">支持比较（如</font><font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);"> </font>`<font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);"><</font>`<br/><font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);"> </font><font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);">运算符）</font> | <font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);">支持哈希函数和相等比较</font> |
| **<font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);">遍历顺序</font>** | <font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);">按键升序</font> | <font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);">无特定顺序</font> |


---

### <font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);">适用场景</font>
+ <font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);">需要</font>**<font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);">有序键</font>**<font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);">或</font>**<font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);">范围查询</font>**<font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);">（如遍历某区间内的键）。</font>
+ <font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);">对插入/删除/查找的</font>**<font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);">稳定性要求较高</font>**<font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);">（避免哈希冲突的最坏情况）。</font>
+ <font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);">键类型天然有序且无需自定义哈希函数时。</font>

<font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);">若无需顺序且追求更高性能，优先选择 </font>`<font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);">std::unordered_map</font>`<font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);">。</font>

### 例题
旋转九宫格

[https://www.luogu.com.cn/problem/P10578](https://www.luogu.com.cn/problem/P10578)

**题目：**

给定一个 ![image](https://cdn.nlark.com/yuque/__latex/07437c61d66b86947272a3fb5bc3e16e.svg) 的九宫格，每个格子内分别含有一个数字，每个格子里的数字互不相同。每步我们可以选择任意一个 ![image](https://cdn.nlark.com/yuque/__latex/10aa54bbdcae60bea1c1e8bcc141bf37.svg) 的区域将其顺时针旋转，例如：

例如

```plain
1 2 3
4 5 6
7 8 9
```

将其旋转右上角，可得：

```plain
1 5 2
4 6 3
7 8 9
```

问最少需要几步才能将给定的状态旋转为

```plain
1 2 3
4 5 6
7 8 9
```

**代码：**

```cpp
#include <iostream>
#include <queue>
#include <unordered_map>
#include <string>
#include <vector>

using namespace std;

const string target = "123456789";
unordered_map<string, int> dist; // 步数

vector<string> generate_new_states(const string &s) {
    vector<string> new_states;

    // 左上区域：0,1,3,4
    string s1 = s;
    s1[0] = s[1];
    s1[1] = s[4];
    s1[3] = s[0];
    s1[4] = s[3];
    new_states.push_back(s1);

    // 右上区域：1,2,4,5
    string s2 = s;
    s2[1] = s[2];
    s2[2] = s[5];
    s2[4] = s[1];
    s2[5] = s[4];
    new_states.push_back(s2);

    // 左下区域：3,4,6,7
    string s3 = s;
    s3[3] = s[4];
    s3[4] = s[7];
    s3[6] = s[3];
    s3[7] = s[6];
    new_states.push_back(s3);

    // 右下区域：4,5,7,8
    string s4 = s;
    s4[4] = s[5];
    s4[5] = s[8];
    s4[7] = s[4];
    s4[8] = s[7];
    new_states.push_back(s4);

    return new_states;
}

void preprocess() {
    queue<string> q;
    q.push(target);
    dist[target] = 0;

    while (!q.empty()) {
        string current = q.front();
        q.pop();

        int current_dist = dist[current];

        vector<string> next_states = generate_new_states(current);

        for (const string &next : next_states) {
            if (dist.find(next) == dist.end()) {
                dist[next] = current_dist + 1;
                q.push(next);
            }
        }
    }
}

int main() {
    ios::sync_with_stdio(false);
    cin.tie(nullptr);

    preprocess();

    int T;
    cin >> T;
    while (T--) {
        string s;
        for (int i = 0; i < 3; ++i) {
            int a, b, c;
            cin >> a >> b >> c;
            s += (char)('0' + a);
            s += (char)('0' + b);
            s += (char)('0' + c);
        }
        cout << dist[s] << '\n';
    }

    return 0;
}
```





  


## STL 容器（如 vector，string ）相关用法：
### 1. pop_back()
pop_back() 用于<font style="color:rgb(0,0,255);">删除</font>字符串或容器的最后一个元素。

```cpp
string str = "Hello!";
str.pop_back(); // 删除最后一个字符 str = "Hello"
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

### `begin()` 和` end()` 
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
`sort()` **默认按升序排序**，但可以提供一个自定义的比较函数来改变排序的规则。

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

### 排序与并查集的例题
[https://www.luogu.com.cn/problem/P10577](https://www.luogu.com.cn/problem/P10577)

**题目描述**

在一条数轴上有n个点，点i的初始位置为![image](https://cdn.nlark.com/yuque/__latex/39c69fbad0041c1d5caa9acf313cb0e6.svg)。每个点会选择距离自己最近的另一个点作为目标，并开始向目标移动。

+ 如果最近的点有两个（即左边和右边距离相等），则选择左边的那个。
+ 每次移动只能向左或向右移动 1个单位。
+ 当两个点之间的距离为1，且它们是彼此的目标时，靠右的点会跳到左边点的位置，左边的点保持不动，它们就完成了“集结”。
+ 每个点会不断朝自己的目标移动，直到与目标完成集结后停止。

请你输出所有点最终的位置。

**输入格式**

第一行一个整数 n，表示点的个数。  
第二行n个整数![image](https://cdn.nlark.com/yuque/__latex/cdd5844ca2df38c7b8e68e5b609ecb13.svg)，表示每个点的初始位置。

**输出格式**

一行n个整数，表示每个点完成集结后的最终位置。

**代码：**

```cpp
#include <iostream>
#include <algorithm>
using namespace std;
int const N = 1e5 + 5;
int fa[N];

struct stu {
  int pos, id;
} s[N]; //等效 stu s[N];

int get(int x) {
  if (fa[x] == x) return x;
  return fa[x] = get(fa[x]);
}

bool cmp1(stu x, stu y) {
  return x.pos < y.pos;
}
bool cmp2(stu x, stu y) {
  return x.id < y.id;
}

int main() {
  int n;
  cin >> n;
  for (int i = 1; i <= n; i++) {
    cin >> s[i].pos;
    s[i].id = i;
  }
  sort(s + 1, s + n + 1, cmp1);
  fa[1] = 2;
  fa[n] = n - 1;  //边界优化
  for (int i = 2; i <= n - 1; i++) {
    int lp = s[i - 1].pos, p = s[i].pos, rp = s[i + 1].pos;
    if (p - lp <= rp - p) fa[i] = i - 1; //判断左右哪一个更近
    else fa[i] = i + 1;
  }
  for (int i = 1; i <= n - 1; i++) {
    if (fa[i] == i + 1 && fa[i + 1] == i) {
      fa[i] = i;
      fa[i + 1] = i + 1;
      int p = (s[i].pos + s[i + 1].pos) / 2;
      s[i].pos = s[i + 1].pos = p;
    } // 如果互为节点，向中靠拢
  }
  for (int i = 1; i <= n; i++) {
    if (fa[i] != i) {
      int root = get(i);
      s[i].pos = s[root].pos;
    }// 更新节点位置
  }
  sort(s + 1, s + n + 1, cmp2); //结构体的作用，逆向回去 
  for (int i = 1; i <= n; i++) {
    cout << s[i].pos << " ";
  }
  return 0;
}
```





















  


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

















## <font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);">并查集</font>
<font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);">并查集是一种用于管理元素分组关系的数据结构，支持以下两种核心操作：</font>

+ **<font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);">Find</font>**<font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);">：查询元素所属的集合（通常返回集合的“代表元素”）。</font>
+ **<font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);">Union</font>**<font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);">：合并两个元素所在的集合。</font>

<font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);">常用于解决 </font>**<font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);">动态连通性问题</font>**<font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);">，例如：</font>

+ <font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);">网络中的节点连接状态判断</font>
+ <font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);">图的连通分量统计</font>

### <font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);">一、核心操作实现</font>
#### <font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);">1. 初始化</font>
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
    x = findroot(x);
	y = findroot(y);
	fa[x] = y;
}
```

### <font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);">二、优化方法</font>
#### <font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);">1. 按秩合并（Union by Rank）</font>
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

// 这里parent的含义就是下一个可用位置
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

注：2^31~2e10  ,2^63~2e19















  




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
### 1. **自动存储类别（**`auto`**）**
+ **生命周期**：变量的生命周期从其定义的作用域开始，到作用域结束时自动销毁。
+ **存储位置**：通常存储在栈区。
+ **初始化**：每次进入作用域时，变量会被重新初始化。
+ **特点**：大多数局部变量默认具有自动存储类别，内存管理由编译器自动处理。

```cpp
void func() {
    int x = 10;  // 自动存储类别
}  // x 在函数结束时销毁
```

### 2. **静态存储类别（**`static`**）**
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
+ `'0'` = **48**，`'9'` = **57**，`'A'` = **65**，`'a'` = **97**
+ 大写字母和小写字母之间的 ASCII 值有固定差距：大写字母的 ASCII 值比小写字母小 **<font style="color:#df2a3f;">32</font>**。

![](https://cdn.nlark.com/yuque/0/2024/jpeg/50259711/1732069472374-1cadf216-f613-42e0-8ccf-bf3107f1c7a4.jpeg)





















## <font style="color:rgb(6, 6, 7);">逻辑运算符的短路行为</font>
1. **<font style="color:rgb(6, 6, 7);">逻辑与（</font>**`&&`**<font style="color:rgb(6, 6, 7);">）</font>**<font style="color:rgb(6, 6, 7);">：</font>
    - <font style="color:rgb(6, 6, 7);">如果第一个操作数为</font>`false`<font style="color:rgb(6, 6, 7);">，则整个表达式的结果为</font>`false`<font style="color:rgb(6, 6, 7);">，因此第二个操作数不会被计算（因为结果已经确定）。</font>
2. **<font style="color:rgb(6, 6, 7);">逻辑或（</font>**`||`**<font style="color:rgb(6, 6, 7);">）</font>**<font style="color:rgb(6, 6, 7);">：</font>
    - <font style="color:rgb(6, 6, 7);">如果第一个操作数为</font>`true`<font style="color:rgb(6, 6, 7);">，则整个表达式的结果为</font>`true`<font style="color:rgb(6, 6, 7);">，因此第二个操作数不会被计算（因为结果已经确定）。</font>
3. **<font style="color:rgb(6, 6, 7);">逻辑非（</font>**`!`**<font style="color:rgb(6, 6, 7);">）</font>**<font style="color:rgb(6, 6, 7);">：</font>
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





## 通用指针
### 1. `void`*指针的定义
`void*` 是一种特殊的指针类型，可以指向任何类型的对象或数据，但是它不直接关联任何具体类型。因此，`void*` 被称为“通用指针”或“空指针”。

```cpp
void* ptr;  // 声明一个 void 指针
```

### 2. `void*`的基本用法
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

### 3. **使用**`void*`**指针访问数据**
`void*` 本身不能直接进行解引用，因为它没有类型信息。因此，在使用 `void*` 时，必须先将它转换为正确的类型指针（即通过类型转换）。

```cpp
int a = 10;
void* ptr = &a;

// 将 void* 转换回 int* 来解引用
int* int_ptr = static_cast<int*>(ptr);
cout << *int_ptr << endl;  // 输出 10
```

### 4. **与**`void*`** 的类型转换**
+ 将其他指针转换为`void*`：任何类型的指针都可以隐式转换为 `void*`，因为 `void*` 是一个通用指针类型。

```cpp
int x = 10;
float y = 5.5f;

void* ptr1 = &x;  // int* 隐式转换为 void*
void* ptr2 = &y;  // float* 隐式转换为 void*
```

+ **将**`void`** 转换为具体类型的指针**：从 `void*` 转换回具体类型时，需要显式转换（使用 `static_cast` 或 `reinterpret_cast`）。因为 `void*` 不包含类型信息，编译器不知道它实际指向什么类型的数据。

```cpp
void* ptr = &x;
int* int_ptr = static_cast<int*>(ptr);  // 将 void* 转换为 int*
```











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







## `.` 和 `->`
`.` 和 `->`都用于访问对象的成员（属性或方法）。`.` 用于通过对象**直接访问**其成员；`->` 用于**通过指针**访问对象的成员。

#### 1. `.`的使用：
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

#### 2. `->`的使用：
`arrow` 操作符（`->`）用于通过指针访问对象的成员。**指针**指向对象时，我们使用 `->` 来访问该对象的成员。

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





















## 作用域解析运算符 `::`
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



















## 函数重载（Function Overloading）
函数重载是指在同一个作用域中，允许定义**多个同名**的函数，只要它们的**参数列表不同**（即参数的个数、类型或顺序不同）。函数的返回类型不影响重载，因为编译器是通过参数来区分不同的函数调用。

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

















## 函数模版（Function Template） 
函数模板允许编写一个函数的模板，而不需要指定具体的数据类型。函数模板可以用于创建一个函数，该函数可以处理多种数据类型，避免了为每个数据类型编写重复的代码。

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
虽然编译器可以根据参数自动推导模板参数的类型，但你也可以**显式****指定**模板参数（是指定，即告诉编译器类型是什么，而不是强制转化输出）。

```cpp
cout << add<int,double>(10, 2.5) << endl;   
```

### 5. **函数模板的特化（Template Specialization）**
函数模板可以针对特定类型进行特化。这意味着可以为某些数据类型提供一个特定的实现，而不是使用通用模板。（如果差别比较大，那我们为什么不用单纯的函数重载呢？）

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

### 6. **注意事项**
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







## 内存分区模型
内存大方向划分为4个区域：

+ **代码区**：存放函数体的**二进制代码**，由操作系统进行管理的
+ **全局区**：存放全局变量和**静态变量**以及**常量**
+ **栈区**：由编译器自动分配释放, 存放**函数的参数值**,**局部变量**等
+ **堆区**：由程序员分配和释放,若程序员不释放,程序结束时由操作系统回收

### 程序运行前
在程序编译后，生成了exe可执行程序，**未执行该程序前**分为两个区域

**代码区：**

存放 CPU 执行的机器指令。代码区是**共享**的，共享的目的是对于频繁被执行的程序，只需要在内存中有一份代码即可。代码区是**只读**的，使其只读的原因是防止程序意外地修改了它的指令。

**全局区：**

全局变量和静态变量存放在此。全局区还包含了常量区, 字符串常量和其他常量也存放在此。该区域的数据在程序结束后由操作系统释放。

**示例：**

```cpp
//全局变量
int g_a = 10;
int g_b = 10;

//全局常量
const int c_g_a = 10;
const int c_g_b = 10;

int main() {

    //局部变量
    int a = 10;
    int b = 10;

    //打印地址
    cout << "局部变量a地址为： " << (int)&a << endl;
    cout << "局部变量b地址为： " << (int)&b << endl;

    cout << "全局变量g_a地址为： " <<  (int)&g_a << endl;
    cout << "全局变量g_b地址为： " <<  (int)&g_b << endl;

    //静态变量
    static int s_a = 10;
    static int s_b = 10;

    cout << "静态变量s_a地址为： " << (int)&s_a << endl;
    cout << "静态变量s_b地址为： " << (int)&s_b << endl;

    cout << "字符串常量地址为： " << (int)&"hello world" << endl;
    cout << "字符串常量地址为： " << (int)&"hello world1" << endl;

    cout << "全局常量c_g_a地址为： " << (int)&c_g_a << endl;
    cout << "全局常量c_g_b地址为： " << (int)&c_g_b << endl;

    const int c_l_a = 10;
    const int c_l_b = 10;
    cout << "局部常量c_l_a地址为： " << (int)&c_l_a << endl;
    cout << "局部常量c_l_b地址为： " << (int)&c_l_b << endl;
    
    return 0;
}
```

打印结果：

![](assets/1545017602518.png)局部变量a地址为： 0x6ffe4c

局部变量b地址为： 0x6ffe48

全局变量g_a地址为： 0x472010

全局变量g_b地址为： 0x472014

静态变量s_a地址为： 0x472018

静态变量s_b地址为： 0x47201c

字符串常量地址为： 0x48808e

字符串常量地址为： 0x48809a

全局常量c_g_a地址为： 0x488104

全局常量c_g_b地址为： 0x488108

局部常量c_l_a地址为： 0x6ffe44

局部常量c_l_b地址为： 0x6ffe40



### 程序运行后
**栈区：**

由编译器自动分配释放, 存放函数的参数值,局部变量等

**注意事项**：

不要返回局部变量的地址，栈区开辟的数据由编译器自动释放

**示例：**

```cpp
int * func(){
    int a = 10;
    return &a;
}

int main() {

    int *p = func();

    cout << *p << endl;
    cout << *p << endl;
    return 0;
}
```



**堆区：**

由程序员分配释放,若程序员不释放,程序结束时由操作系统回收。在C++中主要利用new在堆区开辟内存。

**示例：**

```cpp
int* func(){
    int* a = new int(10);
    return a;
}

int main() {

    int *p = func();

    cout << *p << endl;
    cout << *p << endl;
    return 0;
}
```



**总结：**

堆区数据由程序员管理开辟和释放

堆区数据利用new关键字进行开辟内存



### new操作符
利用**new**操作符在堆区开辟数据。堆区开辟的数据，由程序员手动开辟，手动释放，释放利用操作符 **delete**。利用new创建的数据，会返回该数据对应的类型的**指针**。

语法：` new 数据类型`

**示例1： 基本语法**

```cpp
int* func(){
    int* a = new int(10);
    return a;
}

int main() {
    int *p = func();
    cout << *p << endl;

    //利用delete释放堆区数据
    delete p;
    //cout << *p << endl; //报错，释放的空间不可访问
    return 0;
}
```

**示例2：开辟数组**

```cpp
//堆区开辟数组
int main() {
    int* arr = new int[10];

    for (int i = 0; i < 10; i++) {
        arr[i] = i + 100;
    }

    for (int i = 0; i < 10; i++) {
        cout << arr[i] << endl;
    }
    //释放数组 delete 后加 []
    delete[] arr;
    return 0;
}

```













# **类和对象**
## **接口分离**
源文件包含客户端，例子为main.cpp

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

头文件包含接口，实现

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







## **封装**
**C++面向对象的三大特性为：封装、继承、多态**

C++认为万事万物都皆为对象，对象上有其属性和行为

### **意义：**
+ 将属性和行为作为一个整体
+ 将属性和行为加以权限控制



### struct和class区别：
在C++中 struct和class唯一的区别就在于 **默认的访问权限不同：**

+ struct 默认权限为公共
+ class  默认权限为私有

```cpp
class C1{
int  m_A; //默认是私有权限
};

struct C2{
int m_A;  //默认是公共权限
};

int main() {

    C1 c1;
    c1.m_A = 10; //错误，访问权限是私有

    C2 c2;
    c2.m_A = 10; //正确，访问权限是公共

    return 0;
}
```













### 对象的初始化和清理：
####  构造函数和析构函数
**构造函数**：主要作用在于创建对象时为对象的成员属性赋值，构造函数由编译器自动调用。

**构造函数语法：**`类名(){}`

1. 构造函数，没有返回值也不写void
2. 函数名称与类名相同
3. 构造函数可以有参数，因此可以发生**重载**
4. 程序在调用对象时候会自动调用构造，无须手动调用,而且只会调用一次



**析构函数**：主要作用在于对象**销毁前**系统自动调用。

**析构函数语法：** `~类名(){}`

1. 析构函数，没有返回值也不写void
2. 函数名称与类名相同,在名称前加上符号  ~
3. 析构函数**不可以有参数**，因此**不**可以发生**重载**
4. 程序在对象销毁前会自动调用析构，无须手动调用,而且只会调用一次











#### 构造函数的分类及调用
两种分类方式：

	按**参数**分为： 有参构造和无参构造

	按**类型**分为： 普通构造和拷贝构造

三种调用方式：括号法，显示法，隐式转换法

**示例：**

```cpp
class Person {
    public:
		//无参（默认）构造函数
		Person() {
			cout << "无参构造函数!" << endl;
		}
		//有参构造函数
		Person(int a) {
			age = a;
			cout << "有参构造函数!" << endl;
		}
		//拷贝构造函数
		Person(Person const& p) {
			age = p.age;
			cout << "拷贝构造函数!" << endl;
		}
		//析构函数
		~Person() {
			cout << "析构函数!" << endl;
		}

	public:
		int age;
};

//2、构造函数的调用
//调用无参构造函数
void test01() {
	Person p;  //调用无参构造函数
}

//调用有参的构造函数
void test02() {
	//2.1  括号法，常用
	Person p1(10);
	//注意1：调用无参构造函数不能加括号，如果加了编译器认为这是一个函数声明
	//Person p2();

	//2.2 显式法
	Person p2 = Person(10);
	Person p3 = Person(p2);
	//Person(10)单独写就是匿名对象  当前行结束之后，马上析构

	//2.3 隐式转换法
	Person p4 = 10;  // Person p4 = Person(10);
	Person p5 = p4;  // Person p5 = Person(p4);

	//注意2：不能利用 拷贝构造函数 初始化匿名对象 编译器认为是对象声明
	//Person p5(p4);
}

int main() {
	test01();
	//test02();
	return 0;
}
```















#### 拷贝构造函数调用时机
通常有三种情况：

+ 使用一个已经创建完毕的对象来**初始化**一个**新对象**
+ 值传递的方式给函数参数传值
+ 以值方式返回局部对象

```cpp
class Person {
	public:
		Person() {
			cout << "无参构造函数!" << endl;
			mAge = 0;
		}
		Person(int age) {
			cout << "有参构造函数!" << endl;
			mAge = age;
		}
		Person(const Person& p) {
			cout << "拷贝构造函数!" << endl;
			mAge = p.mAge;
		}
//析构函数在释放内存之前调用
		~Person() {
			cout << "析构函数!" << endl;
		}
	private:
		int mAge;
};

//1. 使用一个已经创建完毕的对象来初始化一个新对象
void test01() {
	Person man(100); //p对象已经创建完毕
	Person newman(man); //调用拷贝构造函数
	Person newman2 = man; //拷贝构造

	//Person newman3;
	//newman3 = man; //不是调用拷贝构造函数，赋值操作，即调用运算重载符
}

//2. 值传递的方式给函数参数传值
//相当于Person p1 = p;
void doWork(Person p1) {}
void test02() {
	Person p; //无参构造函数
	doWork(p);
}

//3. 以值方式返回局部对象
Person doWork2() {
	Person p1;
	cout << (int *)&p1 << endl;  //这里就是指针，即输出地址
	return p1;
}
void test03() {
	Person p = doWork2();
	cout << (int *)&p << endl;
}


int main() {

	//test01();
	//test02();
	test03();
	return 0;
}
```















#### <font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);">转换构造函数</font>
**<font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);">定义</font>**<font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);">：  
</font><font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);">转换构造函数是能通过</font>**<font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);">不同类型参数</font>**<font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);">构造对象的构造函数。  
</font><font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);">其标准形式为：</font>

```cpp
ClassName(T arg);  // T 表示其他类型（如 int、double）
```

**<font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);">核心作用</font>**<font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);">：</font>

1. <font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);">实现从其他类型到当前类的</font>**<font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);">隐式类型转换</font>**
2. <font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);">提供灵活的对象构造方式</font>

**<font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);">注意事项</font>**<font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);">：</font>

1. **<font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);">隐式类型转换</font>**
    - <font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);">默认允许从参数类型隐式转换为当前类对象。（隐式就是直接一个=；而显式就是要从新定义一个类型+（））</font>
    - <font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);">例如：</font>`<font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(243, 243, 243);">MagicScroll s = "Heal";</font>`<font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);"> </font><font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);">等价于</font><font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);"> </font>`<font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(243, 243, 243);">MagicScroll s("Heal");</font>`
    - **<font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);">风险</font>**<font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);">：可能导致意外的隐式转换（如</font><font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);"> </font>`<font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(243, 243, 243);">MagicScroll s = 3.14;</font>`<font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);"> </font><font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);">若存在</font><font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);"> </font>`<font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(243, 243, 243);">double</font>`<font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);"> </font><font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);">参数的构造函数）。</font>
2. `**<font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(243, 243, 243);">explicit</font>**`**<font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);"> </font>****<font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);">关键字</font>**
    - <font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);">禁止隐式转换，强制要求</font>**<font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);">显式调用</font>**<font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);">构造函数。</font>

```cpp
explicit MagicScroll(int level);  // 必须显式调用 MagicScroll(5)
```

    - <font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);">若未加</font><font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);"> </font>`<font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(243, 243, 243);">explicit</font>`<font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);">，</font>`<font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(243, 243, 243);">MagicScroll s = 5</font>`<font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);"> </font><font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);">是合法的；加了</font><font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);"> </font>`<font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(243, 243, 243);">explicit</font>`<font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);"> </font><font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);">后必须写成</font><font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);"> </font>`<font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(243, 243, 243);">MagicScroll s(5)</font>`<font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);">。</font>
3. **<font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);">多参数转换构造</font>**
    - <font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);">如果构造函数有多个参数，但除第一个外都有默认值，仍可视为转换构造函数。</font>

```cpp
MagicScroll(int power, std::string type = "Attack");
```

**<font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);">示例</font>**<font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);">：</font>

```cpp
public:
// 转换构造函数：int → Date
Date(int y) : year(y) {}
};

// 隐式转换示例
void printDate(Date d) {
	/* ... */
}

int main() {
	printDate(2023);  // 隐式调用 Date(2023)
}
```











#### <font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);">拷贝构造函数和转换构造函数区别</font>
| **<font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);">特性</font>** | <font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);">拷贝构造函数</font> | <font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);">转换构造函数</font> |
| :---: | :---: | :---: |
| **<font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);">参数类型</font>** | **<font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);">同类</font>**<font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);">对象的引用</font> | **<font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);">其他类型</font>**<font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);">参数</font> |
| **<font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);">调用场景</font>** | <font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);">同类型对象初始化</font> | <font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);">不同类型→当前类转换</font> |
| **<font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);">隐式行为</font>** | <font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);">总是允许</font> | <font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);">默认允许（可禁用）</font> |


**示例**

```cpp
#include <iostream>
#include <sstream>
#include <string>
using namespace std;

class MagicScroll {
 string spellContent;
 bool isAncientCopy;  // 标识是否是古老复刻版
 //没有访问控制修饰符，默认private，而结构体默认public

 public:
  /* 基础转换构造函数（支持隐式转换）*/
  MagicScroll(string const& spell) : spellContent("现代魔咒: " + spell), isAncientCopy(false) {
    cout << "✨ 转换构造新卷轴: " << spellContent << endl;
  }

  MagicScroll(char const* spell) : spellContent("现代魔咒: " + string(spell)), isAncientCopy(false) {
    cout << "✨ 转换构造新卷轴: " << spellContent << endl;
  }

  /* 高级转换构造函数（显式调用）*/
  explicit MagicScroll(int starLevel) {
    ostringstream oss;
    oss << "星际秘法_" << starLevel << "级";
    spellContent  = oss.str();
    isAncientCopy = (starLevel > 10);  // 超过10级的视为古老卷轴
    cout << "🌌 星际转换构造: " << spellContent << endl;
  }

  /* 标准拷贝构造函数 */
  MagicScroll(MagicScroll const& other)
      : spellContent(other.isAncientCopy ? "上古复刻: " + other.spellContent :  // 添加古老标识
                         "普通复制: " + other.spellContent),                    // 普通复制标识
        isAncientCopy(false) {                                                  // 复制品不再标记为古老
    cout << "🌀 复制生成: " << spellContent << endl;
  }

  /* 古老卷轴专用拷贝构造（演示重载拷贝构造）*/
  MagicScroll(MagicScroll const& other, bool forceAncient)
      : spellContent("[禁术]" + other.spellContent), isAncientCopy(true) {
    cout << "🔮 秘法复刻: " << spellContent << endl;
  }

  void reveal() const {
    cout << "卷轴解密 ▶ " << spellContent << (isAncientCopy ? " (上古)" : " (现代)") << endl;
  }

  // 制作古老副本的工厂方法
  static MagicScroll MakeAncientCopy(MagicScroll const& original) {
    return MagicScroll(original, true);  // 调用专用拷贝构造
  }
};

void enchantScroll(MagicScroll sc) {
  cout << "施法效果：";
  sc.reveal();
}

int main() {
  cout << "======= 转换构造演示 =======\n";
  MagicScroll modernScroll = "火焰冲击";      // 隐式转换构造
  MagicScroll starScroll   = MagicScroll(7);  // 显式星际转换

  cout << "\n======= 普通拷贝构造 =======\n";
  MagicScroll copiedScroll = modernScroll;  // 调用标准拷贝构造
  enchantScroll(starScroll);                // 传参时拷贝构造

  cout << "\n======= 古老复制流程 =======\n";
  MagicScroll ancientCopy = MagicScroll::MakeAncientCopy(modernScroll);

  cout << "\n======= 混合转换案例 =======\n";
  enchantScroll("寒冰箭");                                 // 隐式转换+拷贝构造
  MagicScroll hybridScroll = static_cast<MagicScroll>(9);  // 显式数字转换

  cout << "\n======= 最终卷轴状态 =======\n";
  modernScroll.reveal();
  copiedScroll.reveal();
  ancientCopy.reveal();
  hybridScroll.reveal();

  return 0;
}
```

**<font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);"></font>**















#### 构造函数调用规则
默认情况下，c++编译器至少给一个类添加3个函数

1．默认构造函数(无参，函数体为空)

2．默认析构函数(无参，函数体为空)

3．默认拷贝构造函数，对属性进行值拷贝

构造函数调用**规则**如下：

+ 如果用户定义有参构造函数，c++不在提供默认无参构造，但是会提供默认拷贝构造
+ 如果用户定义拷贝构造函数，c++不会再提供其他构造函数

```cpp
class Person {
	public:
        //无参（默认）构造函数
		Person() {
			cout << "无参构造函数!" << endl;
		}
        //有参构造函数
		Person(int a) {
			age = a;
			cout << "有参构造函数!" << endl;
		}
        //拷贝构造函数
		Person(const Person& p) {
			age = p.age;
			cout << "拷贝构造函数!" << endl;
		}
        //析构函数
		~Person() {
			cout << "析构函数!" << endl;
		}
	public:
		int age;
};

void test01() {
	Person p1(18);
	//如果不写拷贝构造，编译器会自动添加拷贝构造，并且做浅拷贝操作
	Person p2(p1);

	cout << "p2的年龄为： " << p2.age << endl;
}

void test02() {
	//如果用户提供有参构造，编译器不会提供默认构造，会提供拷贝构造
	Person p1; //此时如果用户自己没有提供默认构造，会出错
	Person p2(10); //用户提供的有参
	Person p3(p2); //此时如果用户没有提供拷贝构造，编译器会提供

	//如果用户提供拷贝构造，编译器不会提供其他构造函数
	Person p4; //此时如果用户自己没有提供默认构造，会出错
	Person p5(10); //此时如果用户自己没有提供有参，会出错
	Person p6(p5); //用户自己提供拷贝构造
}

int main() {
	test01();
	return 0;
}
```















#### 深拷贝与浅拷贝
浅拷贝：简单的**赋值拷贝**操作

深拷贝：在**堆区**重新申请空间，进行拷贝操作

```cpp
class Person {
	public:
//无参（默认）构造函数
		Person() {
			cout << "无参构造函数!" << endl;
		}
//有参构造函数
		Person(int age ,int height) {
			cout << "有参构造函数!" << endl;
			m_age = age;
			m_height = new int(height);
		}
//拷贝构造函数 自己实现拷贝构造函数 解决拷贝带来的问题
		Person(const Person& p) {
			cout << "拷贝构造函数!" << endl;
			//如果不利用深拷贝在堆区创建新内存，会导致浅拷贝带来的重复释放堆区问题
			m_age = p.m_age;
			m_height = new int(*p.m_height);
            //这里重新开辟内存空间，可以用深拷贝解决浅拷贝的问题
		}

//析构函数
		~Person() {
			cout << "析构函数!" << endl;
			if (m_height != NULL) {
				delete m_height; // 堆区手动开辟的数据记得要释放
                //m_height = NULL； 
                // 防止野指针的出现，规范操作。
                // 但是！注意浅拷贝带来的重复释放内存问题。
			}
		}
	public:
		int m_age;
		int* m_height;
};

void test01() {
	Person p1(18, 180);
	Person p2(p1);

	cout << "p1的年龄： " << p1.m_age << " 身高： " << *p1.m_height << endl;
	cout << "p2的年龄： " << p2.m_age << " 身高： " << *p2.m_height << endl;
}

int main() {
	test01();
	return 0;
}
```





















#### 初始化列表
**作用：**

C++提供了初始化列表语法，用来初始化属性

**语法：**

`构造函数()：属性1(值1),属性2（值2）... {}`

```cpp
class Person {
	public:

////传统方式初始化
//Person(int a, int b, int c) {
//	m_A = a;
//	m_B = b;
//	m_C = c;
//}

//初始化列表方式初始化
		Person(int a, int b, int c) :m_A(a), m_B(b), m_C(c) {
            
        }
		void PrintPerson() {
			cout << "mA:" << m_A << endl;
			cout << "mB:" << m_B << endl;
			cout << "mC:" << m_C << endl;
		}
	private:
		int m_A;
		int m_B;
		int m_C;
};

int main() {
	Person p(1, 2, 3);
	p.PrintPerson();
	return 0;
}
```









#### 类对象作为类成员
对象成员：类中的成员可以是另一个类的对象。

**示例**：

```cpp
class A {}
class B {
	A a；
}
```

****

****

****

****

****

#### **构造与析构的顺序**
**全局对象**:

构造：在任何函数( 含main)执行前

析构：在程序结束时

**局部对象**：

**自动变量**

构造：对象定义时

析构：块结束时

**静态变量**

构造：首次定义时

析构：程序结束时

**规则：**

1.多个全局和静态局部对象(均为静态存储类别, 程序结束时析构)析构顺序恰好与构造顺序**相反**。

2.先调用对象成员的构造，再调用本类构造。

3.调用exit函数退出程序执行时, 不调用剩余自动对象的析构函数。

4.调用abort函数退出程序执行时, 不调用任何剩余对象的析构函数。

**示例：**

```cpp
class Phone {
	public:
		Phone(string name) {
			m_PhoneName = name;
			cout << "Phone构造" << endl;
		}

		~Phone() {
			cout << "Phone析构" << endl;
		}
		string m_PhoneName;
};

class Person {
	public:
//初始化列表可以告诉编译器调用哪一个构造函数
		Person(string name, string pName) :m_Name(name), m_Phone(pName) {
			cout << "Person构造" << endl;
		}
		~Person() {
			cout << "Person析构" << endl;
		}
		void playGame() {
			cout << m_Name << " 使用" << m_Phone.m_PhoneName << " 牌手机! " << endl;
		}
		string m_Name;
		Phone m_Phone;
        //这里就是先调用了对象成员的构造，在调用本类构造
};

void test01() {
	//当类中成员是其他类对象时，我们称该成员为 对象成员
	//构造的顺序是 ：先调用对象成员的构造，再调用本类构造
	//析构顺序与构造相反
	Person p("张三" , "苹果X");
	p.playGame();  

}


int main() {
	test01();
    //输出： Phone构造
    //		Person构造
    //		张三 使用苹果X 牌手机!
    //		Person析构
    //		Phone析构
	return 0;
}
```











#### 静态成员
静态成员：在成员变量和成员函数前加上关键字 **static**。

静态成员分为：静态成员变量和静态成员函数。

**静态成员变量：**

+ 所有对象共享同一份数据（就相当于全局的）
+ 在编译阶段分配内存（在程序运行前就分配内存了）
+ 类内声明，**<font style="color:#DF2A3F;">类外初始化</font>**
+ 静态成员变量也是有**访问权限**的
+ 有两种访问方式
+ 属于类本身而不是实例（即存在第二种**通过类名**的访问方式）

**静态成员函数：**

+ 所有对象共享同一个函数
+ 静态成员函数**只能访问**静态成员变量
+ 和静态成员函数一样，有两种访问方式
+ 静态成员函数也是有访问权限的

示例1 ：**静态成员变量**

```cpp
class Person {
	public:
		static int m_A; //静态成员变量
	private:
		static int m_B; //静态成员变量也是有访问权限的
};
int Person::m_A = 10;  //先在类外初始化
int Person::m_B = 10;

void test01() {
	//静态成员变量两种访问方式

	//1、通过对象
	Person p1;
	p1.m_A = 100;
	cout << "p1.m_A = " << p1.m_A << endl;

	Person p2;
	p2.m_A = 200;
	cout << "p1.m_A = " << p1.m_A << endl; //共享同一份数据
	cout << "p2.m_A = " << p2.m_A << endl; //所以输出都为200

	//2、通过类名
	cout << "m_A = " << Person::m_A << endl;
	//cout << "m_B = " << Person::m_B << endl; //私有权限访问不到
}

int main() {
	test01();
	return 0;
}
```



示例2：**静态成员函数**

```cpp
class Person {
	public:
		static void func() {
            //前面有了static ，就是静态成员函数
			cout << "func调用" << endl;
			m_A = 100;
			//m_B = 100; 
            //错误，不可以访问非静态成员变量
		}

		static int m_A; //静态成员变量
		int m_B; //非静态成员变量
	private:
//静态成员函数也是有访问权限的
		static void func2() {
			cout << "func2调用" << endl;
		}
};
int Person::m_A = 10;


void test01() {
	//静态成员变量两种访问方式

	//1、通过对象
	Person p1;
	p1.func();

	//2、通过类名
	Person::func();
    
    //私有权限访问不到
	//Person::func2(); 
}

int main() {
	test01();
	return 0;
}
```









### 对象模型（类如何占用内存）
类内的成员**变量**和成员**函数分开存储**，只有**非静态成员**变量才属于类的对象上。

```cpp
class Person {
	public:
		Person() {
			mA = 0;
		}
        //非静态成员变量占对象空间，mA占4字节
		int mA;

        //静态成员变量不占对象空间
		static int mB;

        //函数也不占对象空间，所有函数共享一个函数实例
		void func() {
			cout << "mA:" << this->mA << endl;
		}
        //静态成员函数也不占对象空间
		static void sfunc() {
		}
};

//class Person{}
//空对象占用内存空间为：1
//C++编译器会给每一个空对象分配一个字节空间，有一个独一无二的内存地址，为了区分空对象占内存的位置。

int main() {
	cout << sizeof(Person) << endl;
	return 0;
}
```















### this指针
每一个非静态成员函数只会诞生一份函数实例，也就是说多个同类型的对象会共用一块代码。

那么问题是：这一块代码是如何区分那个对象调用自己的呢？

this指针指向被调用的成员函数所属的对象，隐含每一个非静态成员函数内的一种指针，不需要定义，直接使用即可。

**用途**：

+ 当形参和成员变量同名时，可用this指针来区分，解决名称冲突。
+ 在类的非静态成员函数中返回对象本身，可使用return *this。

```cpp
class Person {
	public:
		Person(int age) {
			//1、当形参和成员变量同名时，可用this指针来区分
			this->age = age;
		}
		Person& PersonAddPerson(Person p) {
			this->age += p.age;
			//返回对象本身
			return *this;
		}
		int age;
};

void test01() {
	Person p1(10);
	cout << "p1.age = " << p1.age << endl;
    //这里就输出10

	Person p2(10);
	p2.PersonAddPerson(p1).PersonAddPerson(p1).PersonAddPerson(p1);
	cout << "p2.age = " << p2.age << endl;
    //这里就输出40
}

int main() {
	test01();
	return 0;
}
```











#### 空指针访问成员函数
空指针也是可以调用成员函数的，但是也要注意有没有用到this指针

如果用到this指针，需要加以判断保证代码的健壮性

**示例：**

```cpp
//空指针访问成员函数
class Person {
public:
	void ShowClassName() {
		cout << "我是Person类!" << endl;
	}

	void ShowPerson() {
		if (this == NULL) {
			return;
		}
		cout << mAge << endl;
	}
public:
	int mAge;
};

void test01() {
	Person *p = NULL;
	p->ShowClassName(); //空指针，可以调用成员函数
	p->ShowPerson();  //但是如果成员函数中用到了this指针，就不可以了
}

int main() {
	test01();
	return 0;
}
```











#### const修饰成员函数
**常函数：**

+ 成员函数后加const后我们称为这个函数为**常函数**
+ 常函数内**不可以修改成员属性**
+ 成员属性声明时加关键字mutable后，在常函数中依然可以修改

**常对象：**

+ 声明对象前加const称该对象为常对象
+ 常对象只能调用常函数

**示例：**

```cpp
class Person {
public:
	Person() {
		m_A = 0;
		m_B = 0;
	}

//this指针的本质是一个指针常量，指针的指向不可修改
//如果想让指针指向的值也不可以修改，需要声明常函数
	void ShowPerson() const {
		//const Type* const pointer;
		//this = NULL; //不能修改指针的指向 Person* const this;
		//this->mA = 100; //但是this指针指向的对象的数据是可以修改的

		//const修饰成员函数，表示指针指向的内存空间的数据不能修改，除了mutable修饰的变量
		this->m_B = 100;
	}

	void MyFunc() const {
		//mA = 10000;
	}
	public:
		int m_A;
		mutable int m_B; //可修改 可变的
};

//const修饰对象  常对象
void test01() {
	const Person person; //常量对象
	cout << person.m_A << endl;
	//person.mA = 100; //常对象不能修改成员变量的值,但是可以访问
	person.m_B = 100; //但是常对象可以修改mutable修饰成员变量

	//常对象访问成员函数
	person.MyFunc(); //常对象不能调用const的函数
}

int main() {
	test01();
	return 0;
}
```











### 友元
有些**私有属性**也想**让类外**特殊的**一些函数或者类进行访问**，就需要用到友元的技术。友元的目的就是让一个函数或者类访问另一个类中私有成员。友元的关键字为**  friend。**

友元的三种实现

+ 全局函数做友元
+ 类做友元
+ 成员函数做友元

#### 全局函数做友元
```cpp
class Building {
//告诉编译器 goodGay全局函数 是 Building类的好朋友，可以访问类中的私有内容
		friend void goodGay(Building * building){
        	cout << "好基友正在访问： " << building->m_SittingRoom << endl;
        	cout << "好基友正在访问： " << building->m_BedRoom << endl;
        }
	public:
		Building() {
			this->m_SittingRoom = "客厅";
			this->m_BedRoom = "卧室";
		}
	public:
		string m_SittingRoom; //客厅
	private:
		string m_BedRoom; //卧室
};

void test01() {
	Building b;
	goodGay(&b);
}

int main() {
	test01();
	return 0;
}
```



#### 类做友元
```cpp
class Building {
//告诉编译器 goodGay类是Building类的好朋友，可以访问到Building类中私有内容
		friend class goodGay;
	public:
		Building() {
			this->m_SittingRoom = "客厅";
			this->m_BedRoom = "卧室";
		}
		string m_SittingRoom; //客厅
	private:
		string m_BedRoom;//卧室
};

class goodGay {
	public:
		goodGay() {
			building = new Building;
		}
		void visit() {
			cout << "好基友正在访问" << building->m_SittingRoom << endl;
			cout << "好基友正在访问" << building->m_BedRoom << endl;
		}
	private:
		Building *building;
};

void test01() {
	goodGay gg;
	gg.visit();
}
```



#### 成员函数做友元
```cpp
// 前向声明
class Building;

// 提前声明goodGay类，但成员函数稍后定义
class goodGay {
	public:
		goodGay();
		void visit();   // 声明为友元的函数
		void visit2();  // 普通成员函数
	private:
		Building* building;
};

// Building类的完整定义
class Building {
		// 声明goodGay的visit函数为友元
		friend void goodGay::visit();
	public:
		Building() : m_SittingRoom("客厅"), m_BedRoom("卧室") {}
		string m_SittingRoom;
	private:
		string m_BedRoom;
};

// goodGay成员函数的实现（此时Building已完整定义）
goodGay::goodGay() : building(new Building) {}

void goodGay::visit() {
	cout << "好基友正在访问" << building->m_SittingRoom << endl;
	cout << "好基友正在访问" << building->m_BedRoom << endl;  // 友元可访问私有成员
}

void goodGay::visit2() {
	cout << "普通访问：" << building->m_SittingRoom << endl;
	// cout << building->m_BedRoom << endl;  // 编译错误，非友元无法访问
}

void test01() {
	goodGay gg;
	gg.visit();
	gg.visit2();
}

int main() {
	test01();
	return 0;
}
```









## 运算符重载
概念：对已有的运算符**重新**进行定义，赋予其另一种功能，以适应不同的数据类型

#### 加号运算符重载
作用：实现两个自定义数据类型相加的运算

注意：

+ 对于内置的数据类型的表达式的的运算符是不可能改变的
+ 不要滥用运算符重载

```cpp
class Person {
public:
	Person() {};
	Person(int a, int b) {
		this->m_A = a;
		this->m_B = b;
	}
=//成员函数实现 + 号运算符重载
	Person operator+(const Person& p) {
		Person temp;
		temp.m_A = this->m_A + p.m_A;
		temp.m_B = this->m_B + p.m_B;
		return temp;
	}
public:
	int m_A;
	int m_B;
};

//全局函数实现 + 号运算符重载
//Person operator+(const Person& p1, const Person& p2) {
//	Person temp(0, 0);
//	temp.m_A = p1.m_A + p2.m_A;
//	temp.m_B = p1.m_B + p2.m_B;
//	return temp;
//}

//运算符重载 可以发生函数重载
Person operator+(const Person& p2, int val) {
	Person temp;
	temp.m_A = p2.m_A + val;
	temp.m_B = p2.m_B + val;
	return temp;
}

void test() {
	Person p1(10, 10);
	Person p2(20, 20);

	//成员函数方式
	Person p3 = p2 + p1;  //相当于 p2.operaor+(p1)
	cout << "mA:" << p3.m_A << " mB:" << p3.m_B << endl;

	Person p4 = p3 + 10; //相当于 operator+(p3,10)
	cout << "mA:" << p4.m_A << " mB:" << p4.m_B << endl;

}

int main() {
	test();
 	return 0;
}
```





#### 左移运算符重载
作用：可以输出自定义数据类型

```cpp
class Person {
friend ostream& operator<<(ostream& out, Person& p);
public:
	Person(int a, int b) {
		this->m_A = a;
		this->m_B = b;
	}

//成员函数 实现不了  p << cout 不是我们想要的效果
//void operator<<(Person& p){
//}

private:
	int m_A;
	int m_B;
};

//全局函数实现左移重载
//ostream对象只能有一个
ostream& operator<<(ostream& out, Person& p) {
	out << "a:" << p.m_A << " b:" << p.m_B;
	return out;
}

void test() {
	Person p1(10, 20);
	cout << p1 << "hello world" << endl; //链式编程
}

int main() {
	test();
    return 0;
}
```

> 总结：重载左移运算符配合友元可以实现输出自定义数据类型
>







#### 递增运算符重载
作用： 通过重载递增运算符，实现自己的整型数据

总结： 前置递增返回**引用**，后置递增返回**值**

```cpp
class MyInteger {
friend ostream& operator<<(ostream& out, MyInteger myint);
public:
	MyInteger() {
		m_Num = 0;
	}
//前置++
	MyInteger& operator++() {
		//先++
		m_Num++;
		//再返回
		return *this;
	}

//后置++
	MyInteger operator++(int) {
		//先返回
		MyInteger temp = *this; //记录当前本身的值，然后让本身的值加1，但是返回的是以前的值，达到先返回后++；
		m_Num++;
		return temp;
	}

private:
	int m_Num;
};

ostream& operator<<(ostream& out, MyInteger myint) {
	out << myint.m_Num;
	return out;
}

//前置++ 先++ 再返回
void test01() {
	MyInteger myInt;
	cout << ++myInt << endl;
	cout << myInt << endl;
}

//后置++ 先返回 再++
void test02() {
	MyInteger myInt;
	cout << myInt++ << endl;
	cout << myInt << endl;
}

int main() {
	test01();
	//test02();
	return 0;
}
```















#### 赋值运算符重载
c++编译器至少给一个类添加4个函数

1. 默认构造函数(无参，函数体为空)
2. 默认析构函数(无参，函数体为空)
3. 默认拷贝构造函数，对属性进行值拷贝
4. 赋值运算符 operator=, 对属性进行值拷贝

如果类中有属性指向堆区，做赋值操作时也会出现深浅拷贝问题

```cpp
class Person {
	public:
		Person(int age) {
			//将年龄数据开辟到堆区
			m_Age = new int(age);
		}

//重载赋值运算符
		Person& operator=(Person &p) {
			if (m_Age != NULL) {
				delete m_Age;
				m_Age = NULL;
			}
			//编译器提供的代码是浅拷贝
			//m_Age = p.m_Age;

			//提供深拷贝 解决浅拷贝的问题
			m_Age = new int(*p.m_Age);

			//返回自身
			return *this;
		}


		~Person() {
			if (m_Age != NULL) {
				delete m_Age;
				m_Age = NULL;
			}
		}

//年龄的指针
		int *m_Age;

};


void test01() {
	Person p1(18);
	Person p2(20);
	Person p3(30);
	p3 = p2 = p1; //赋值操作
	cout << "p1的年龄为：" << *p1.m_Age << endl;
	cout << "p2的年龄为：" << *p2.m_Age << endl;
	cout << "p3的年龄为：" << *p3.m_Age << endl;
}

int main() {
	test01();
	//int a = 10;
	//int b = 20;
	//int c = 30;

	//c = b = a;
	//cout << "a = " << a << endl;
	//cout << "b = " << b << endl;
	//cout << "c = " << c << endl;
	return 0;
}
```









#### 关系运算符重载
作用：重载关系运算符，可以让两个自定义类型对象进行对比操作

**示例：**

```cpp
class Person {
	public:
		Person(string name, int age) {
			this->m_Name = name;
			this->m_Age = age;
		};

		bool operator==(Person & p) {
			if (this->m_Name == p.m_Name && this->m_Age == p.m_Age) {
				return true;
			} else {
				return false;
			}
		}

		bool operator!=(Person & p) {
			if (this->m_Name == p.m_Name && this->m_Age == p.m_Age) {
				return false;
			} else {
				return true;
			}
		}

		string m_Name;
		int m_Age;
};

void test01() {
	//int a = 0;
	//int b = 0;

	Person a("孙悟空", 18);
	Person b("孙悟空", 18);

	if (a == b) {
		cout << "a和b相等" << endl;
	} else {
		cout << "a和b不相等" << endl;
	}

	if (a != b) {
		cout << "a和b不相等" << endl;
	} else {
		cout << "a和b相等" << endl;
	}
}


int main() {

	test01();

	system("pause");

	return 0;
}
```





#### 函数调用运算符重载
+ 函数调用运算符 ()  也可以重载
+ 由于重载后使用的方式非常像函数的调用，因此称为仿函数
+ 仿函数没有固定写法，非常灵活

**示例：**

```cpp
class MyPrint {
	public:
		void operator()(string text) {
			cout << text << endl;
		}

};
void test01() {
	//重载的（）操作符 也称为仿函数
	MyPrint myFunc;
	myFunc("hello world");
}


class MyAdd {
	public:
		int operator()(int v1, int v2) {
			return v1 + v2;
		}
};

void test02() {
	MyAdd add;
	int ret = add(10, 10);
	cout << "ret = " << ret << endl;

	//匿名对象调用
	cout << "MyAdd()(100,100) = " << MyAdd()(100, 100) << endl;
}

int main() {

	test01();
	test02();

	system("pause");

	return 0;
}
```













## 继承
#### 基本语法
继承**意义**：可以减少重复的代码。

class A : public B; 

A 类称为子类 或 派生类

B 类称为父类 或 基类

派生类中包含两大部分成员：

1.从基类继承过来的   2.自己增加的成员。

**普通实现：**

```cpp
//Java页面
class Java {
	public:
		void header() {
			cout << "首页、公开课、登录、注册...（公共头部）" << endl;
		}
		void footer() {
			cout << "帮助中心、交流合作、站内地图...(公共底部)" << endl;
		}
		void left() {
			cout << "Java,Python,C++...(公共分类列表)" << endl;
		}
		void content() {
			cout << "JAVA学科视频" << endl;
		}
};

//Python页面
class Python {
	public:
		void header() {
			cout << "首页、公开课、登录、注册...（公共头部）" << endl;
		}
		void footer() {
			cout << "帮助中心、交流合作、站内地图...(公共底部)" << endl;
		}
		void left() {
			cout << "Java,Python,C++...(公共分类列表)" << endl;
		}
		void content() {
			cout << "Python学科视频" << endl;
		}
};

//C++页面
class CPP {
	public:
		void header() {
			cout << "首页、公开课、登录、注册...（公共头部）" << endl;
		}
		void footer() {
			cout << "帮助中心、交流合作、站内地图...(公共底部)" << endl;
		}
		void left() {
			cout << "Java,Python,C++...(公共分类列表)" << endl;
		}
		void content() {
			cout << "C++学科视频" << endl;
		}
};

void test01() {
	//Java页面
	cout << "Java下载视频页面如下： " << endl;
	Java ja;
	ja.header();
	ja.footer();
	ja.left();
	ja.content();
	cout << "--------------------" << endl;

	//Python页面
	cout << "Python下载视频页面如下： " << endl;
	Python py;
	py.header();
	py.footer();
	py.left();
	py.content();
	cout << "--------------------" << endl;

	//C++页面
	cout << "C++下载视频页面如下： " << endl;
	CPP cp;
	cp.header();
	cp.footer();
	cp.left();
	cp.content();

}

int main() {
	test01();
	return 0;
}
```



**继承实现：**

```cpp
//公共页面
class BasePage {
	public:
		void header() {
			cout << "首页、公开课、登录、注册...（公共头部）" << endl;
		}

		void footer() {
			cout << "帮助中心、交流合作、站内地图...(公共底部)" << endl;
		}
		void left() {
			cout << "Java,Python,C++...(公共分类列表)" << endl;
		}

};

//Java页面
class Java : public BasePage {
	public:
		void content() {
			cout << "JAVA学科视频" << endl;
		}
};
//Python页面
class Python : public BasePage {
	public:
		void content() {
			cout << "Python学科视频" << endl;
		}
};
//C++页面
class CPP : public BasePage {
	public:
		void content() {
			cout << "C++学科视频" << endl;
		}
};

void test01() {
	//Java页面
	cout << "Java下载视频页面如下： " << endl;
	Java ja;
	ja.header();
	ja.footer();
	ja.left();
	ja.content();
	cout << "--------------------" << endl;

	//Python页面
	cout << "Python下载视频页面如下： " << endl;
	Python py;
	py.header();
	py.footer();
	py.left();
	py.content();
	cout << "--------------------" << endl;

	//C++页面
	cout << "C++下载视频页面如下： " << endl;
	CPP cp;
	cp.header();
	cp.footer();
	cp.left();
	cp.content();
}

int main() {
	test01();
	return 0;
}
```













#### 继承方式
继承的语法：`class 子类 : 继承方式  父类`

**方式：**

+ 公共继承
+ 保护继承
+ 私有继承

三个控制修饰访问符：

+ `<font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(243, 243, 243);">public</font>`<font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);">：无限制，任何代码均可访问。</font>
+ `<font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(243, 243, 243);">private</font>`<font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);">：仅类内部和友元可访问，派生类不可访问。</font>
+ `<font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(243, 243, 243);">protected</font>`<font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);">：介于两者之间，</font>**<font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);">允许派生类</font>**<font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);">访问，但阻止外部直接访问。</font>

![](https://cdn.nlark.com/yuque/0/2025/png/50259711/1744709051487-f875aec2-710f-43ea-9182-ad01cd0fb028.png)

**<font style="color:#DF2A3F;">总结：</font>**

**基类的private成员在派生类中都不可见；**

**继承方式public不改变成员类型，private和protected都会使成员变成继承方式。**

****

**示例：**

```cpp
class Base1 {
	public:
		int m_A;
	protected:
		int m_B;
	private:
		int m_C;
};

//公共继承
class Son1 :public Base1 {
	public:
		void func() {
			m_A; //可访问 public权限
			m_B; //可访问 protected权限
			//m_C; //不可访问
		}
};

void myClass() {
	Son1 s1;
	s1.m_A; //其他类只能访问到公共权限
}

//保护继承
class Base2 {
	public:
		int m_A;
	protected:
		int m_B;
	private:
		int m_C;
};
class Son2:protected Base2 {
	public:
		void func() {
			m_A; //可访问 protected权限
			m_B; //可访问 protected权限
			//m_C; //不可访问
		}
};
void myClass2() {
	Son2 s;
	//s.m_A; //不可访问
}

//私有继承
class Base3 {
	public:
		int m_A;
	protected:
		int m_B;
	private:
		int m_C;
};
class Son3:private Base3 {
	public:
		void func() {
			m_A; //可访问 private权限
			m_B; //可访问 private权限
			//m_C; //不可访问
		}
};
class GrandSon3 :public Son3 {
	public:
		void func() {
			//Son3是私有继承，所以继承Son3的属性在GrandSon3中都无法访问到
			//m_A;
			//m_B;
			//m_C;
		}
};
```













#### 对象模型
问题：从父类继承过来的成员，哪些属于子类对象中？

父类中**私有成员private**也是被子类继承下去了，只是由编译器给隐藏后访问不到

**示例：**

```cpp
class Base {
	public:
		int m_A;
	protected:
		int m_B;
	private:
		int m_C; //私有成员只是被隐藏了，但是还是会继承下去
};

//公共继承
class Son :public Base {
	public:
		int m_D;
};

void test01() {
	cout << "sizeof Son = " << sizeof(Son) << endl;
    // 输出：16
}

int main() {
	test01();
	return 0;
}
```

















#### 构造和析构顺序
子类继承父类后，当创建子类对象，也会调用父类的构造函数。

顺序：先调用**父类构造函数**，再调用**子类构造函数**，析构顺序与构造**相反**

**示例：**

```cpp
class Base {
	public:
		Base() {
			cout << "Base构造函数!" << endl;
		}
		~Base() {
			cout << "Base析构函数!" << endl;
		}
};

class Son : public Base {
	public:
		Son() {
			cout << "Son构造函数!" << endl;
		}
		~Son() {
			cout << "Son析构函数!" << endl;
		}

};


void test01() {
	Son s;
}

int main() {
	test01();
    //输出：Base构造函数!
    //	    Son构造函数!
    //		Son析构函数!
    //		Base析构函数!
    return 0;
}
```













#### 继承同名（静态）成员处理方式
问题：当子类与父类出现同名的（静态）成员，如何通过子类对象，访问到子类或父类中同名的数据呢？

+ 访问子类同名（静态）成员   直接访问即可
+ 访问父类同名（静态）成员   需要加作用域

注意：小心不同函数定义带来的运行错误。

**示例：**

```cpp
#include<iostream>
using namespace std;
class Base {
	public:
		Base():m_A(100){}
		void func() {
			cout << "Base - func()调用" << endl;
		}
		void func(int a) {
			cout << "Base - func(int a)调用" << endl;
		}
	public:
		int m_A;
};


class Son : public Base {
	public:
		Son():m_A(100){}
//当子类与父类拥有同名的成员函数，子类会隐藏父类中所有版本的同名成员函数
//如果想访问父类中被隐藏的同名成员函数，需要加父类的作用域
		void func() {
			cout << "Son - func()调用" << endl;
		}
	public:
		int m_A;
};

void test01() {
	Son s;
	cout << "Son下的m_A = " << s.m_A << endl;
    //输出：Son下的m_A = 200
	cout << "Base下的m_A = " << s.Base::m_A << endl; //这里就是调用的区别
    //输出：Base下的m_A = 100
    cout << "再次回到Son下的m_A = "<<s.m_A << endl;
    //输出：再次回到Son下的m_A = 200
    //解释：子类和父类的同名成员变量是独立的，不会相互影响，因为子类和父类属于不同的类作用域
	s.func();
    //输出：Son - func()调用
	s.Base::func();
    //输出：Base - func()调用
	s.Base::func(10);
    //输出：Base - func(int a)调用
}
int main() {
	test01();
 	return 0;
}
```













#### 多继承语法
允许一个类继承多个类，即有多个父类。

语法：` class 子类 ：继承方式 父类1 ， 继承方式 父类2...`

多继承可能会引发父类中有同名成员出现，需要加作用域区分

**示例：**

```cpp
#include<iostream>
using namespace std;
class Base1 {
	public:
		Base1():m_A(100) {}
	public:
		int m_A;
};

class Base2 {
	public:
		Base2():m_A(200) {}
		//开始是m_B 不会出问题，但是改为mA就会出现不明确
	public:
		int m_A;
};

//语法：class 子类：继承方式 父类1 ，继承方式 父类2
class Son : public Base2, public Base1 {
	public:
		Son():m_C(300),m_D(400) {}
	public:
		int m_C;
		int m_D;
};


//多继承容易产生成员同名的情况
//通过使用类名作用域可以区分调用哪一个基类的成员
void test01() {
	Son s;
	cout << "sizeof Son = " << sizeof(s) << endl;//输出：16
	cout << s.Base1::m_A << endl;
	cout << s.Base2::m_A << endl;
}

int main() {
	test01();
	return 0;
}
```











####  菱形继承
**菱形继承概念：**

	两个派生类继承同一个基类

	又有某个类同时继承者两个派生类

	这种继承被称为菱形继承，或者钻石继承

**菱形继承问题：**

1.羊继承了动物的数据，驼同样继承了动物的数据，当草泥马使用数据时，就会产生二义性。

2.草泥马继承自动物的数据继承了两份，其实我们应该清楚，这份数据我们只需要一份就可以。

**示例：**

```cpp
#include<iostream>
using namespace std;
class Animal {
	public:
		int m_Age;
};

//继承前加virtual关键字后，变为虚继承
//此时公共的父类Animal称为虚基类
class Sheep : virtual public Animal {};
class Tuo   : virtual public Animal {};
class SheepTuo : public Sheep, public Tuo {};

void test01() {
	SheepTuo st;
	st.Sheep::m_Age = 100;
	st.Tuo::m_Age = 200;

	cout << "st.Sheep::m_Age = " << st.Sheep::m_Age << endl;
	cout << "st.Tuo::m_Age = " <<  st.Tuo::m_Age << endl;
	cout << "st.m_Age = " << st.m_Age << endl;
}

int main() {
	test01();
	return 0;
}
```



总结：

+ 菱形继承带来的主要问题是子类继承两份相同的数据，导致资源浪费以及毫无意义
+ 利用虚继承可以解决菱形继承问题



















## 多态
#### 基本概念
多态分为两类

+ **静态**多态: 函数重载 和 运算符重载属于静态多态，复用函数名
+ **动态**多态: 派生类和虚函数实现运行时多态

静态多态和动态多态区别：

+ 静态多态的**函数地址早绑定**  -  编译阶段确定函数地址
+ 动态多态的**函数地址晚绑定**  -  运行阶段确定函数地址

多态使用条件

+ 父类指针或引用指向子类对象

**覆盖（override）**：**函数返回值类型  函数名 参数列表** **一致**称为覆盖

```cpp
class Animal {
	public:
//Speak函数就是虚函数
//函数前面加上virtual关键字，变成虚函数，那么编译器在编译的时候就不能确定函数调用了。
		virtual void speak() {
			cout << "动物在说话" << endl;
		}
};

class Cat :public Animal {
	public:
		void speak() {
			cout << "小猫在说话" << endl;
		}
};
class Dog :public Animal {
	public:
		void speak() {
			cout << "小狗在说话" << endl;
		}
};
//我们希望传入什么对象，那么就调用什么对象的函数
//如果函数地址在编译阶段就能确定，那么静态联编
//如果函数地址在运行阶段才能确定，就是动态联编

void DoSpeak(Animal & animal) {
	animal.speak();
}
//
//多态满足条件：
//1、有继承关系
//2、子类重写父类中的虚函数
//多态使用：
//父类指针或引用指向子类对象

void test01() {
	Cat cat;
	DoSpeak(cat);
	Dog dog;
	DoSpeak(dog);
}

int main() {
	test01();
	return 0;
}
```











**<font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);">静态类型 vs. 动态类型</font>**

+ <font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);">静态类型：指针/引用的声明类型（如 </font>`<font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(243, 243, 243);">A*</font>`<font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);">），相当于“</font>**<font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);">标签</font>**<font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);">”，非虚函数只看“标签”。</font>
+ <font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);">动态类型：</font>**<font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);">实际</font>**<font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);">指向的对象类型（如 </font>`<font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(243, 243, 243);">B</font>`<font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);">），相当于“</font>**<font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);">实际内容</font>**<font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);">”，虚函数看“实际内容”。</font>
+ **<font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);">非虚函数</font>**<font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);">由静态绑定，</font>**<font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);">虚函数</font>**<font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);">由动态绑定。</font>

**示例：**

```cpp
#include <iostream>
using namespace std;
class A {
public:
    // 非虚函数：静态绑定，调用路径由指针/引用的声明类型决定
    void testfuc() {  
        cout << "A::testfuc ";  // [Step1] 静态类型为A，直接调用A的testfuc
        func();                 // [Step2] 非虚函数func，继续静态绑定到A::func
    }

    // 非虚函数：派生类B中的func会隐藏此函数，但通过A类型调用时仍选此版本
    void func() {  
        cout << "A::func ";     // [Step3] 静态绑定到A::func
        vfunc();                // [Step4] 虚函数vfunc，动态绑定到实际对象类型
    }

    // 虚函数：动态绑定，实际调用由对象类型决定
    virtual void vfunc() {  
        cout << "A::vf" << endl;
    }
};

class B : public A {
public:
    // 非虚函数：隐藏A::func（非重写），仅通过B类型调用时生效
    void func() {  
        cout << "B::func" << endl;
    }

    // 虚函数重写：覆盖A::vfunc，通过基类指针调用时动态绑定到此版本
    virtual void vfunc() override {  
        cout << "B::vf" << endl;
    }
};

int main() {
    A a;
    a.func();cout<<endl;  
    // 输出：A::func A::vf

    B b;
    b.func();   
    // 输出：B::func
    b.testfuc();cout<<endl; // 从A继承的非虚函数testfuc → A::testfuc → A::func → 动态绑定B::vfunc
    // 输出：A::testfuc A::func B::vf

    A* p = &b;
    p->vfunc();    // 虚函数 → 动态绑定B::vfunc
    // 输出：B::vf

    p->testfuc();  // 非虚函数A::testfuc → A::func → 动态绑定B::vfunc
    // 输出：A::testfuc A::func B::vf

    p->func();     // 非虚函数 → 静态绑定A::func → 动态绑定B::vfunc
    // 输出：A::func B::vf
    return 0;
}
```

> **总结：**
>
> 非虚函数看"标签"，回基类；
>
> 虚函数看“实际内容”，在派生类。
>

**习题2：**

```cpp
#include <iostream>
using namespace std;

class Base {
 public:
  void foo() {
    cout << "Base::foo()\n";
    bar();
    baz();
  }

  virtual void bar() {
    cout << "Base::bar()\n";
  }

  void baz() {
    cout << "Base::baz()\n";
  }
};

class Derived : public Base {
 public:
  void foo() {
    cout << "Derived::foo()\n";
    bar();
    Base::baz();
  }

  virtual void bar() override {
    cout << "Derived::bar()\n";
  }

  void baz() {
    cout << "Derived::baz()\n";
  }
};

class DeepDerived : public Derived {
 public:
  void foo() {
    cout << "DeepDerived::foo()\n";
    bar();
    Derived::bar();
  }

  void bar() override {
    cout << "DeepDerived::bar()\n";
  }
  virtual void baz() {
    cout << "DeepDerived::baz()\n";
  }
};

int main() {
  DeepDerived dd;
  Base* p1= &dd;
  Derived* p2 = &dd;

  cout << "=== Test 1 ===" << endl;
  p1->foo();

  cout << "\n=== Test 2 ===" << endl;
  p2->foo();

  cout << "\n=== Test 3 ===" << endl;
  dd.foo();

  cout << "\n=== Test 4 ===" << endl;
  p1->baz();
  p2->baz();
  dd.baz();

  return 0;
}
```

> 输出：
>
> === Test 1 ===
>
> Base::foo()
>
> DeepDerived::bar()
>
> Base::baz()
>
> 
>
> === Test 2 ===
>
> Derived::foo()
>
> DeepDerived::bar()
>
> Base::baz()
>
> 
>
> === Test 3 ===
>
> DeepDerived::foo()
>
> DeepDerived::bar()
>
> Derived::bar()
>
> 
>
> === Test 4 ===
>
> Base::baz()
>
> Derived::baz()
>
> DeepDerived::baz()
>

**总结的总结：**

1.明确对象的“标签”和“实际内容”，判断对象是不是纯粹的（标签与实际一致）

2.回到**“标签”的基类**看看这个函数是否为（非）虚函数，**虚函数**用**实际内容**对应的域，**非虚函数**用**标签**对应的域。







#### <font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);">对象切片</font>
<font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);">对象切片发生在将派生类对象赋值给基类对象时，导致派生类特有的成员数据丢失。这是因为基类对象仅能存储基类部分的成员，而派生类新增的成员会被“切掉”。</font>

**<font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);">示例：</font>**

```cpp
class Base {
public:
    int a;
};

class Derived : public Base {
public:
    int b; // 派生类新增成员
};

Derived d;
Base b = d; // 对象切片：b 仅保留 Base::a，Derived::b 被丢弃
```

**<font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);">关键点：</font>**

+ **<font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);">原因</font>**<font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);">：直接对对象进行值传递或赋值时，编译器仅复制基类部分。</font>
+ **<font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);">解决方法</font>**<font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);">：使用基类的指针或引用，保持多态性：</font>

```cpp
Base& ref = d;     // 通过引用访问，避免切片
Base* ptr = &d;    // 通过指针访问，避免切片
```

#### 








#### 纯虚函数和抽象类
在多态中，通常父类中虚函数的实现是毫无意义的，主要都是调用子类重写的内容，因此可以将虚函数改为**纯虚函数。**

语法：`virtual 返回值类型 函数名 （参数列表）= 0 ;`

当类中有了纯虚函数，这个类也称为抽象类。

**抽象类特点**：

+ 无法实例化对象
+ 子类必须覆盖抽象类中的纯虚函数，否则也属于抽象类

**示例：**

```cpp
class Base {
	public:
		virtual void func() = 0;
};

class Son :public Base {
	public:
		virtual void func() {
			cout << "func调用" << endl;
		};
};

void test01() {
	Base * base = NULL;
	//base = new Base; // 错误，抽象类无法实例化对象
	base = new Son;
	base->func();
	delete base;//记得销毁
}

int main() {
	test01();
	return 0;
}
```









#### 虚析构和纯虚析构
多态使用时，如果子类中有属性开辟到堆区，那么父类指针在释放时无法调用到子类的析构代码。

解决方式：将父类中的析构函数改为**虚析构**或者**纯虚析构**

虚析构和纯虚析构**共性**：

+ 可以解决父类指针释放子类对象
+ 都需要有具体的函数实现

虚析构和纯虚析构**区别**：

+ 如果是纯虚析构，该类属于抽象类，无法实例化对象

虚析构语法：

`virtual ~类名(){}`

纯虚析构语法：

` virtual ~类名() = 0;`

`类名::~类名(){}`

**示例：**

```cpp
#include <iostream>
using namespace std;
class Animal {
 public:
  Animal() {
    cout << "Animal 构造函数调用！" << endl;
  }
  virtual void Speak() = 0;
  //析构函数加上virtual关键字，变成虚析构函数
  //virtual ~Animal()
  //{
  //	cout << "Animal虚析构函数调用！" << endl;
  //}
  virtual ~Animal() = 0;
};

Animal::~Animal() {
  cout << "Animal 纯虚析构函数调用！" << endl;
}

//和包含普通纯虚函数的类一样，包含了纯虚析构函数的类也是一个抽象类。不能够被实例化。
class Cat : public Animal {
	public:
		Cat(string name) {
			cout << "Cat构造函数调用！" << endl;
			m_Name = new string(name);
		}
		virtual void Speak() {
			cout << *m_Name <<  "小猫在说话!" << endl;
		}
		~Cat() {
			cout << "Cat析构函数调用!" << endl;
			if (this->m_Name != NULL) {
				delete m_Name;
				m_Name = NULL;
			}
		}
	public:
		string *m_Name;
};

void test01() {
	Animal *animal = new Cat("Tom");
	animal->Speak();
	//通过父类指针去释放，会导致子类对象可能清理不干净，造成内存泄漏
	//怎么解决？给基类增加一个虚析构函数
	//虚析构函数就是用来解决通过父类指针释放子类对象
	delete animal;
}

int main() {
	test01();
	return 0;
}
```

总结：

	1. 虚析构或纯虚析构就是用来解决通过父类指针释放子类对象

	2. 如果子类中没有堆区数据，可以不写为虚析构或纯虚析构

	3. 拥有纯虚析构函数的类也属于抽象类













## 类模版
代码示例：

```cpp
#include <iostream>
#include <stdexcept>
#include <vector>
using namespace std;

template <typename T>
class Stack;

// 模版化的友元函数必须前向声明
template <typename T>
ostream& operator>>(ostream& os, Stack<T>& stack);

template <typename T, int MaxSize = 0>
class myStack {
 private:
  std::vector<T> elements;

 public:
  myStack() {
    ++instance_count;
  }

  void push(T const& element);

  T top() const {
    if (empty()) {
      throw std::out_of_range("Stack<>::top(): empty stack");
    }
    return elements.back();
  }

  void pop() {
    if (empty()) {
      throw std::out_of_range("Stack<>::pop(): empty stack");
    }
    elements.pop_back();
  }

  bool empty() const {
    return elements.empty();
  }

  friend ostream& operator>> (ostream& os, myStack<T>& stack){
    for (const auto& elem : stack.elements) {
      os << elem << " ";
    }
    return os;
  }

  // 静态成员,每个模板特化类拥有独立的静态成员。
  static int instance_count;
};

// 外部成员函数定义，注意形式 类名<T>::
template <typename T, int MaxSize>
void myStack<T, MaxSize>::push(T const& element) {
  if constexpr (MaxSize > 0) {
    if (elements.size() >= MaxSize) {
      throw std::out_of_range("Stack is full");
    }
  }
  elements.push_back(element);
}

// 初始化静态成员
template <typename T, int MaxSize>
int myStack<T, MaxSize>::instance_count = 0;

int main() {
  myStack<int> intStack;   // 等价于 myStack<int, 0>,使用了默认的
  myStack<int> intStack2;  //同种类还是一个静态成员
  intStack.push(42);
  intStack.push(7);

  myStack<std::string, 3> strStack;  // 最大容量3
  try {
    strStack.push("Hello");
    strStack.push("Template");
    strStack.push("World");
    strStack.push("Extra");  // 这里会抛出异常
  } catch (std::exception const& e) {
    std::cout << "Exception: " << e.what() << std::endl;
  }

  myStack<double> anotherStack;
  std::cout << myStack<double>::instance_count << " " << myStack<double>::instance_count << std::endl;
  //输出：2 1

  return 0;
}
```















## 链表
```cpp
#include <iostream>
using namespace std;

// 链表节点模板
template<typename T>
struct ListNode {
    T data;
    ListNode<T>* next;
    ListNode(const T& val) : data(val), next(nullptr) {}
};

// 链表模板类
template<typename T>
class LinkedList {
private:
    ListNode<T>* head;
    ListNode<T>* tail;

public:
    // 构造函数
    LinkedList() : head(nullptr), tail(nullptr) {}
    
    // 析构函数
    ~LinkedList() {
        ListNode<T>* current = head;
        while (current) {
            ListNode<T>* next = current->next;
            delete current;
            current = next;
        }
    }
    
    // 尾部插入
    void push_back(const T& value) {
        ListNode<T>* newNode = new ListNode<T>(value);
        if (!head) {
            head = tail = newNode;
        } else {
            tail->next = newNode;
            tail = newNode;
        }
    }
    
    // 打印链表
    void print() const {
        ListNode<T>* current = head;
        while (current) {
            cout << current->data << " ";
            current = current->next;
        }
        cout << endl;
    }
    
    // 获取头节点（用于合并操作）
    ListNode<T>* get_head() const { return head; }
};

// 合并两个有序链表（非成员函数）
template<typename T>
void merge_sorted_lists(const LinkedList<T>& l1, 
                        const LinkedList<T>& l2, 
                        LinkedList<T>& result) {
    ListNode<T>* p1 = l1.get_head();
    ListNode<T>* p2 = l2.get_head();
    
    while (p1 && p2) {
        if (p1->data <= p2->data) {
            result.push_back(p1->data);
            p1 = p1->next;
        } else {
            result.push_back(p2->data);
            p2 = p2->next;
        }
    }
    
    // 添加剩余元素
    while (p1) {
        result.push_back(p1->data);
        p1 = p1->next;
    }
    while (p2) {
        result.push_back(p2->data);
        p2 = p2->next;
    }
}

// 使用示例
int main() {
    LinkedList<int> list1, list2, merged;
    
    // 创建有序链表
    list1.push_back(1);
    list1.push_back(3);
    list1.push_back(5);
    
    list2.push_back(2);
    list2.push_back(4);
    list2.push_back(6);
    
    // 合并链表
    merge_sorted_lists(list1, list2, merged);
    
    cout << "Merged list: ";
    merged.print();  // 输出: 1 2 3 4 5 6
    
    return 0;
}
```



















## 零散题目
### **<font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);">题目1：构造/析构顺序与虚函数</font>**
```cpp
class Base {
public:
    Base() { callVirtual(); }
    virtual ~Base() { cout << "~Base "; }
    virtual void callVirtual() { cout << "Base "; }
};

class Derived : public Base {
public:
    Derived() { callVirtual(); }
    ~Derived() { cout << "~Derived "; }
    void callVirtual() override { cout << "Derived "; }
};

Derived d; // 输出什么？
```

**<font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);">答案与考察点</font>**<font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);">  
</font><font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);">输出：</font>`<font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(243, 243, 243);">Base Derived ~Derived ~Base</font>`<font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);">  
</font>**<font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);">隐蔽点</font>**<font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);">：构造函数中虚函数机制未生效（此时对象类型仍视为</font>`<font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(243, 243, 243);">Base</font>`<font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);">）</font>



### **<font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);">题目2：继承中的对象切片</font>**
```cpp
class Animal {
public:
    virtual void speak() { cout << "Animal "; }
};

class Cat : public Animal {
public:
    void speak() override { cout << "Cat "; }
    void groom() { cout << "Grooming "; }
};

void process(Animal a) {
    a.speak();
}

Cat c;
process(c); // 输出什么？能否调用c.groom()？
```

**<font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);">答案与考察点</font>**<font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);">  
</font><font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);">输出：</font>`<font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(243, 243, 243);">Animal</font>`<font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);">  
</font>**<font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);">隐蔽点</font>**<font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);">：值传递导致对象切片，丢失派生类信息；groom()不可访问</font>

---

### **<font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);">题目3：成员初始化顺序</font>**
```cpp
class Clock {
    int hours = initHours();
    int minutes = 30;
public:
    Clock() : minutes(0) {}
    int initHours() { return minutes + 1; }
};
```

`<font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(243, 243, 243);">Clock</font>`<font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);">对象构造后，hours和minutes的值分别是多少？  
</font>**<font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);">答案与考察点</font>**<font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);">  
</font><font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);">hours=1, minutes=0  
</font>**<font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);">隐蔽点</font>**<font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);">：初始化顺序按声明顺序（先hours后minutes），覆盖初始化列表</font>



### **<font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);">题目4：虚函数表与内存布局</font>**
```cpp
class Empty {};
class WithVirtual { virtual void f() {} };
```

`<font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(243, 243, 243);">sizeof(Empty)</font>`<font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);">和</font>`<font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(243, 243, 243);">sizeof(WithVirtual)</font>`<font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);">的值为？若继承多个含虚函数的类，大小如何变化？  
</font>**<font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);">答案与考察点</font>**<font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);">  
</font><font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);">1（空类）、8（64位指针）  
</font>**<font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);">隐蔽点</font>**<font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);">：虚函数表指针的存在；多重继承可能增加多个vptr</font>



### **<font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);">题目5：静态绑定与默认参数</font>**
```cpp
class Shape {
public:
    virtual void draw(int thickness=1) {
        cout << "Shape:" << thickness << " ";
    }
};

class Circle : public Shape {
public:
    void draw(int thickness=5) override {
        cout << "Circle:" << thickness << " ";
    }
};

Shape* p = new Circle();
p->draw(); // 输出什么？
```

**<font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);">答案与考察点</font>**<font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);">  
</font>`<font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(243, 243, 243);">Circle:1</font>`<font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);">  
</font>**<font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);">隐蔽点</font>**<font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);">：默认参数静态绑定（根据</font>`<font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(243, 243, 243);">Shape</font>`<font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);">类型），函数动态绑定</font>



### **<font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);">题目6：移动语义陷阱</font>**
```cpp
class Buffer {
    int* data;
public:
    Buffer() : data(new int[1024]) {}
    Buffer(Buffer&& other) : data(other.data) {
        other.data = nullptr;
    }
    ~Buffer() { delete[] data; }
};

Buffer createBuffer() {
    Buffer local;
    return local; 
}

Buffer b = createBuffer(); // 调用几次构造函数？
```

**<font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);">答案与考察点</font>**<font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);">  
</font><font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);">1次（RVO优化）  
</font>**<font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);">隐蔽点</font>**<font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);">：移动构造可能被编译器优化完全跳过</font>



### **<font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);">题目7：类型转换运算符</font>**
```cpp
class Meter {
    double value;
public:
    explicit operator int() { return value; }
    operator double() { return value; }
};

Meter m{2.5};
double d = m; 
int i = m;    // 哪行编译错误？
```

**<font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);">答案与考察点</font>**<font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);">  
</font>`<font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(243, 243, 243);">int i = m</font>`<font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);">错误  
</font>**<font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);">隐蔽点</font>**<font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);">：explicit转换必须显式调用（如</font>`<font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(243, 243, 243);">static_cast<int>(m)</font>`<font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);">）</font>

---

### **<font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);">题目8：模板类的静态成员</font>**
```cpp
template<typename T>
class Counter {
public:
    static int count;
    Counter() { count++; }
};
template<> int Counter<int>::count = 0;

Counter<int> a, b;
Counter<double> c;
```

`<font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(243, 243, 243);">Counter<int>::count</font>`<font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);">和</font>`<font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(243, 243, 243);">Counter<double>::count</font>`<font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);">的值分别为？  
</font>**<font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);">答案与考察点</font>**<font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);">  
</font><font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);">2 和 1  
</font>**<font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);">隐蔽点</font>**<font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);">：模板特化导致不同模板参数的静态成员独立存在</font>



### **<font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);">题目9：析构函数多态</font>**
```cpp
class Base {
public:
    ~Base() { cout << "Base "; }
};

class Derived : public Base {
public:
    ~Derived() { cout << "Derived "; }
};

Base* p = new Derived();
delete p; // 输出什么？如何修正？
```

**<font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);">答案与考察点</font>**<font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);">  
</font><font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);">输出</font>`<font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(243, 243, 243);">Base </font>`<font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);">（资源泄漏）  
</font>**<font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);">隐蔽点</font>**<font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);">：基类析构函数未声明为virtual导致派生类析构未调用</font>



### **<font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);">题目10：const成员函数</font>**
```cpp
class Data {
    mutable int accessCount = 0;
    int value = 42;
public:
    void modify() const { 
        accessCount++; 
        value = 0;     // 是否合法？
    }
};
```

**<font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);">答案与考察点</font>**<font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);">  
</font>`<font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(243, 243, 243);">accessCount++</font>`<font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);">合法（mutable修饰），</font>`<font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(243, 243, 243);">value=0</font>`<font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);">不合法  
</font>**<font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);">隐蔽点</font>**<font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);">：const成员函数对mutable成员的可修改性</font>

  
 





















# 文件操作
程序运行时产生的数据都属于临时数据，程序一旦运行结束都会被释放，通过文件可以将**数据持久化**，对文件操作需要包含头文件 **< fstream >**。

文件类型分为两种：

1. **文本文件**     -  文件以文本的**ASCII码**形式存储在计算机中
2. **二进制文件** -  文件以文本的**二进制**形式存储在计算机中，用户一般不能直接读懂它们



操作文件的三大类:

1. ofstream：写操作
2. ifstream： 读操作
3. fstream ： 读写操作

### 文本文件
#### 写文件
**步骤**：

1. 包含头文件     #include <fstream>
2. 创建**流对象 ** ofstream ofs;
3. 打开文件ofs.open("文件路径",打开方式);
4. 写数据ofs << "写入的数据";
5. 关闭文件ofs.close();

文件打开方式：

| 打开方式 | 解释 |
| --- | --- |
| ios::in | 为读文件而打开文件 |
| ios::out | 为写文件而打开文件 |
| ios::ate | 初始位置：文件尾 |
| ios::app | 追加方式写文件 |
| ios::trunc | 如果文件存在先删除，再创建 |
| ios::binary | 二进制方式 |


**注意：** 文件打开方式可以配合使用，利用|操作符

例如：用二进制方式写文件 `ios::binary |  ios:: out`



**示例：**

```cpp
#include <fstream>

void test01(){
    ofstream ofs;
    ofs.open("test.txt", ios::out);

    ofs << "姓名：张三" << endl;
    ofs << "性别：男" << endl;
    ofs << "年龄：18" << endl;

    ofs.close();
}

int main() {
    test01();
    return 0;
}
```











#### 读文件
读文件与写文件步骤相似，但是读取方式相对于比较多

**步骤**：

1. 包含头文件     #include <fstream>
2. 创建**流对象**  ifstream ifs;
3. 打开文件并**判断**文件是否打开成功ifs.open("文件路径",打开方式);
4. 读数据四种方式读取
5. 关闭文件ifs.close();

**示例：**

```cpp
#include <fstream>
#include <string>
void test01(){
    ifstream ifs;
    ifs.open("test.txt", ios::in);

    if (!ifs.is_open()){
        cout << "文件打开失败" << endl;
        return;
    }

    //第一种方式
    char buf[1024] = {  };
    while (ifs >> buf){
    	cout << buf << endl;
    }

    //第二种
    char buf[1024] = { 0 };
    while (ifs.getline(buf,sizeof(buf))){
    	cout << buf << endl;
    }

    //第三种
    string buf;
    while (getline(ifs, buf)){
    	cout << buf << endl;
    }

    //第四种
    char c;
    while ((c = ifs.get()) != EOF){
        cout << c;
    }
    ifs.close();
}

int main() {
    test01();
    return 0;
}
```

总结：

+ 读文件可以利用 ifstream  ，或者fstream类
+ 利用is_open函数可以判断文件是否打开成功
+ close 关闭文件











### 二进制文件
以二进制的方式对文件进行读写操作，打开方式要指定为 **ios::binary**。

#### 写文件
二进制方式写文件主要利用流对象调用成员函数**write**。

函数原型 ：`ostream& write(const char * buffer,int len);`

参数解释：字符指针buffer指向内存中一段**存储空间**。len是读写的**字节数**。

**示例：**

```cpp
#include <fstream>
#include <string>
using namespace std;

class Person{
    public:
        char m_Name[64];
        int m_Age;
};

//二进制文件  写文件
void test01(){
    //1、包含头文件

    //2、创建输出流对象
    ofstream ofs("person.txt", ios::out | ios::binary);

    //3、打开文件
    //ofs.open("person.txt", ios::out | ios::binary);

    Person p = {"张三"  , 18};

    //4、写文件
    ofs.write((const char *)&p, sizeof(p));

    //5、关闭文件
    ofs.close();
}

int main() {
    test01();
    return 0;
}
```









#### 读文件
二进制方式读文件主要利用流对象调用成员函数**read**。

函数原型：`istream& read(char *buffer,int len);`

参数解释：字符指针buffer指向内存中一段存储空间。len是读写的字节数。

```cpp
#include <fstream>
#include <string>
using namespace std;

class Person{
    public:
        char m_Name[64];
        int m_Age;
};

void test01(){
    ifstream ifs("person.txt", ios::in | ios::binary);
    if (!ifs.is_open()){
        cout << "文件打开失败" << endl;
    }

    Person p;
    ifs.read((char *)&p, sizeof(p));

    cout << "姓名： " << p.m_Name << " 年龄： " << p.m_Age << endl;
}

int main() {
    test01();
    return 0;
}
```















### 文件和流（Files and Streams）
**<font style="color:rgb(17, 24, 39);">流（Stream） </font>**<font style="color:rgb(44, 44, 54);">：字节序列，用于数据传输。</font>

+ <font style="color:rgb(17, 24, 39);">输入流（Input Stream） </font><font style="color:rgb(44, 44, 54);">：数据从外部设备流向内存（如键盘、文件读取）。</font>
+ <font style="color:rgb(17, 24, 39);">输出流（Output Stream） </font><font style="color:rgb(44, 44, 54);">：数据从内存流向外部设备（如屏幕、文件写入）。</font>

**<font style="color:rgb(17, 24, 39);">C++文件流类 </font>**<font style="color:rgb(44, 44, 54);">：</font>

+ **<font style="color:rgb(17, 24, 39);">头文件 </font>**<font style="color:rgb(44, 44, 54);">：</font>`#include <fstream>`<font style="color:rgb(44, 44, 54);">。</font>
+ **<font style="color:rgb(17, 24, 39);">类模板特化 </font>**<font style="color:rgb(44, 44, 54);">：</font>
    - `ifstream`<font style="color:rgb(44, 44, 54);">：文件输入流（读文件）。</font>
    - `ofstream`<font style="color:rgb(44, 44, 54);">：文件输出流（写文件）。</font>
    - `fstream`<font style="color:rgb(44, 44, 54);">：文件输入输出流（支持读写）。</font>

**<font style="color:rgb(17, 24, 39);">流继承关系 </font>**<font style="color:rgb(44, 44, 54);">：</font>

 ios → istream/ostream → <font style="color:rgb(44, 44, 54);">iostream </font>

<font style="color:rgb(44, 44, 54);">→ ifstream/ofstream → fstream</font>

**<font style="color:rgb(17, 24, 39);">标准流对象 </font>**<font style="color:rgb(44, 44, 54);">：</font>

`cin`（输入）、`cout`（输出）、`cerr`（错误输出）。





### 创建顺序文件
**<font style="color:rgb(17, 24, 39);">步骤 </font>**<font style="color:rgb(44, 44, 54);"></font>

1. **<font style="color:rgb(17, 24, 39);">定义文件流对象 </font>**<font style="color:rgb(44, 44, 54);">：</font>

```cpp
ofstream outClientFile;
```

2. **<font style="color:rgb(17, 24, 39);">打开文件 </font>**<font style="color:rgb(44, 44, 54);">：</font>

**<font style="color:rgb(44, 44, 54);">方式一</font>**<font style="color:rgb(44, 44, 54);">：构造函数直接打开。</font>

```cpp
ofstream outClientFile("clients.dat", ios::out);
```

**<font style="color:rgb(44, 44, 54);">方式二</font>**<font style="color:rgb(44, 44, 54);">：先定义对象，后调用</font>`open`<font style="color:rgb(44, 44, 54);">函数。</font>

```cpp
outClientFile.open("clients.dat", ios::out);
```

3. **<font style="color:rgb(17, 24, 39);">文件模式（Mode） </font>**<font style="color:rgb(44, 44, 54);">：</font>

`ios::out`：默认模式，若文件存在则清空内容，若不存在则创建。

`ios::app`：在文件末尾追加数据。

4. **<font style="color:rgb(17, 24, 39);">写入数据 </font>**<font style="color:rgb(44, 44, 54);">：</font>

```cpp
outClientFile << account << ' ' << name << ' ' << balance << endl;
```

<font style="color:rgb(44, 44, 54);">需用空格分隔数据（便于后续读取）。</font>

5. **<font style="color:rgb(17, 24, 39);">关闭文件 </font>**<font style="color:rgb(44, 44, 54);">：</font>

```cpp
outClientFile.close();
```

<font style="color:rgb(44, 44, 54);">析构函数自动关闭文件，但建议显式调用</font>`close()`。





### 从顺序文件读取数据
**<font style="color:rgb(17, 24, 39);">步骤 </font>**<font style="color:rgb(44, 44, 54);">：</font>

1. **<font style="color:rgb(17, 24, 39);">定义文件流对象 </font>**<font style="color:rgb(44, 44, 54);">：</font>

```cpp
ifstream inClientFile;
```

2. **<font style="color:rgb(17, 24, 39);">打开文件 </font>**<font style="color:rgb(44, 44, 54);">：</font>

```cpp
ifstream inClientFile("clients.dat", ios::in);
```

3. **<font style="color:rgb(17, 24, 39);">读取数据 </font>**<font style="color:rgb(44, 44, 54);">：</font>

```cpp
inClientFile >> account >> name >> balance;
```

<font style="color:rgb(44, 44, 54);">需按写入时的格式读取（空格分隔）。</font>

4. **<font style="color:rgb(17, 24, 39);">判断文件结束 （</font>**使用`eof()`函数）<font style="color:rgb(44, 44, 54);">：</font>

```cpp
while (!inClientFile.eof()) {// 处理数据}
```

**<font style="color:rgb(17, 24, 39);">注意事项 </font>**<font style="color:rgb(44, 44, 54);">：文件末尾需有空行，否则可能忽略最后一行数据。</font>

5. **<font style="color:rgb(17, 24, 39);">重新定位文件指针 </font>**<font style="color:rgb(44, 44, 54);">：</font>

`seekg()`：移动输入流的“get指针”。

`seekp()`：移动输出流的“put指针”。

`tellg()`：获取当前“get指针”位置。

`tellg()`：获取当前“put指针”位置。

```cpp
inClientFile.seekg(0); // 回到文件开头
inClientFile.clear(); // 清除EOF标志
```

6. **<font style="color:rgb(17, 24, 39);">文件指针偏移方式 </font>**<font style="color:rgb(44, 44, 54);">：</font>

`ios::beg`：从文件开头偏移。

`ios::cur`：从当前位置偏移。

`ios::end`：从文件末尾偏移。



### 代码示例（若没有文件，创建文件）
```cpp
#include <fstream>
#include <iostream>
using namespace std;

int main() {
    string filename;
    cout << "输入文件名 (如：file.dat): ";
    cin >> filename;

    // 尝试以读写模式打开文件，若不存在则创建
    fstream file(filename, ios::in | ios::out | ios::binary);
    if (!file) {
        ofstream createFile(filename, ios::binary);
        if (!createFile) {
            cerr << "无法创建文件!" << endl;
            return 1;
        }
        createFile.close();
        file.open(filename, ios::in | ios::out | ios::binary);
    }

    // 连续写入三个字符，指针自动移动
  char data[] = {'a', 'b', 'c'};
  file.write(data, sizeof(data));  // 写入后指针在位置3
  file.seekp(0);  // 确保写入后指针重置
  file.seekg(0);  // 重置指针到开头以便读取

  // 阶段1：读取并修改数据
  cout << "----- 修改阶段 -----" << endl;
  char ch;
  while (file.read(&ch, sizeof(ch))) {
    // 显示读取信息
    cout << "读取字符: " << ch << " | 指针位置: " << file.tellg() << endl;

    // 修改数据
    ch += 1;
    file.seekp(-1, ios::cur);  // 回退写指针
    file.write(&ch, 1);        // 写入修改后的字符
    file.seekg(file.tellp());  // 同步读指针到当前写位置
  }

  // 阶段2：重新读取验证
  cout << "\n----- 验证阶段 -----" << endl;
  file.clear();   // 清除eof状态
  file.seekg(0);  // 重置到文件开头

  while (file.read(&ch, 1)) {
    cout << "最终字符: " << ch << " | 指针位置: " << file.tellg() << endl;
  }

    file.close();
    return 0;
}
```

<font style="color:rgb(44, 44, 54);"></font>

<font style="color:rgb(44, 44, 54);"></font>

### 随机存取文件
**<font style="color:rgb(17, 24, 39);">特点 </font>**<font style="color:rgb(44, 44, 54);">：</font>

<font style="color:rgb(44, 44, 54);">1.支持直接访问文件中任意记录（无需顺序读取）。</font>

<font style="color:rgb(44, 44, 54);">2.需固定记录大小（二进制模式写入）。</font>

**<font style="color:rgb(17, 24, 39);">实现步骤 </font>**<font style="color:rgb(44, 44, 54);">：</font>

1. **<font style="color:rgb(17, 24, 39);">定义数据结构 </font>**<font style="color:rgb(44, 44, 54);">：</font>

```cpp
class ClientData {
public:
    int accountNumber;
    char name[15]; // 固定长度字段
    double balance;
};
```

2. **<font style="color:rgb(17, 24, 39);">写入二进制文件 </font>**<font style="color:rgb(44, 44, 54);">：</font>

```cpp
ofstream outCredit("credit.dat", ios::out | ios::binary);
ClientData client = {100, "yang", 99.9};
outCredit.write(reinterpret_cast<const char*>(&client), sizeof(ClientData));
```

3. **<font style="color:rgb(17, 24, 39);">读取二进制文件 </font>**<font style="color:rgb(44, 44, 54);">：</font>

```cpp
ifstream inCredit("credit.dat", ios::in | ios::binary);
ClientData client;
inCredit.read(reinterpret_cast<char*>(&client), sizeof(ClientData));
```

4. **<font style="color:rgb(17, 24, 39);">定位特定记录 </font>**<font style="color:rgb(44, 44, 54);">：</font>

读取第`N`条记录：

```cpp
cpp1inCredit.seekg(sizeof(ClientData) * (N - 1));
```

写入第`N`条记录：

```cpp
fstream file("credit.dat", ios::in | ios::out | ios::binary);
file.seekp(sizeof(ClientData) * (N - 1));
```



### 综合示例
```cpp
#include "filehandler.h"
#include <fstream>
#include <iostream>
#include <iomanip>
#include <string>

static int findRecordPosition(std::fstream& file, int targetId) {
    file.clear();
    file.seekg(0);
    Student s ;
    int position = 0;
    while (file.read(reinterpret_cast<char*>(&s), sizeof(Student))) {
        if (s.getId() == targetId) {
            return position;
        }
        position++;
    }
    return -1;
}

static bool idExists(std::fstream& file, int id) {
    file.clear();
    file.seekg(0);

    Student s ;
    while (file.read(reinterpret_cast<char*>(&s), sizeof(Student))) {
        if (s.getId() == id && s.getId() != 0) {
            return true;
        }
    }
    return false;
}

void displayRecords(std::fstream& file) {
    file.clear();  
    file.seekg(0);
    Student s ;
    int count = 0;
    double total = 0.0;

    while (file.read(reinterpret_cast<char*>(&s), sizeof(Student))) {
        if (s.getId() != 0) {
            std::cout << "ID: " << s.getId() << "\n"
                << "姓名: " << s.getFirstName() << " " << s.getLastName() << "\n"
                << "成绩: " << std::fixed << std::setprecision(1) << s.getGrade() << "\n\n";
            total += s.getGrade();
            count++;
        }
    }

    if (count > 0) {
        std::cout << "平均成绩: " << (total / count) << "\n";
    }
    else {
        std::cout << "暂无记录.\n";
    }
}

void addRecord(std::fstream& file) {
    file.clear();
    file.seekg(0);
    int id;
    std::string fname, lname;
    double grade;

    std::cout << "输入学生ID: ";
    std::cin >> id;
    std::cin.ignore();

    std::cout << "输入姓氏: ";
    std::getline(std::cin, fname);
    std::cout << "输入名字: ";
    std::getline(std::cin, lname);
    std::cout << "输入成绩: ";
    std::cin >> grade;

    Student temp=Student(0," "," ",0);
    int position = -1;
    file.seekg(0);
    while (file.read(reinterpret_cast<char*>(&temp), sizeof(Student))) {
        if (temp.getId() == 0) {
            position = static_cast<int>(file.tellg()) / sizeof(Student) - 1;
            break;
        }
    }

    Student newStudent(id, fname, lname, grade);
    if (position != -1) {
        file.seekp(position * sizeof(Student));
    }
    else {
        file.clear();
        file.seekp(0, std::ios::end);
    }

    file.write(reinterpret_cast<const char*>(&newStudent), sizeof(Student));
    std::cout << "输入完毕.\n";
}

void deleteRecord(std::fstream& file) {
    file.clear();
    file.seekg(0);
    int targetId;
    std::cout << "输入要删除的ID: ";
    std::cin >> targetId;

    int pos = findRecordPosition(file, targetId);
    if (pos == -1) {
        std::cout << "无法找到该ID.\n";
        return;
    }

    Student blank;
    file.seekp(pos * sizeof(Student));
    file.write(reinterpret_cast<const char*>(&blank), sizeof(Student));
    std::cout << "记录已删除.\n";
}

void modifyRecord(std::fstream& file) {
    file.clear();
    file.seekg(0);
    int targetId;
    std::cout << "输入需要修改的ID: ";
    std::cin >> targetId;

    int pos = findRecordPosition(file, targetId);
    if (pos == -1) {
        std::cout << "无法找到该ID.\n";
        return;
    }

    Student s ;
    file.seekg(pos * sizeof(Student));
    file.read(reinterpret_cast<char*>(&s), sizeof(Student));

    int newId;
    std::string fname, lname;
    float grade;

    std::cout << "输入新ID ( " << s.getId() << "): ";
    std::cin >> newId;
    if (newId != targetId ) {
        std::cout << "错误：该ID已存在！\n";
        return;
    }

    std::cin.ignore();
    std::cout << "输入姓氏 ( " << s.getFirstName() << "): ";
    std::getline(std::cin, fname);
    std::cout << "输入名称 ( " << s.getLastName() << "): ";
    std::getline(std::cin, lname);
    std::cout << "输入成绩 ( " << s.getGrade() << "): ";
    std::cin >> grade;

    s.setId(newId);
    s.setFirstName(fname);
    s.setLastName(lname);
    s.setGrade(grade);

    file.seekp(pos * sizeof(Student));
    file.write(reinterpret_cast<const char*>(&s), sizeof(Student));
    std::cout << "记录已更新\n";
}


```













# 异常处理
![](https://cdn.nlark.com/yuque/0/2025/png/50259711/1747707517325-cf80dc8c-932f-41da-9f49-79570de0af5e.png)

### 处理流程
#### <font style="color:rgb(17, 24, 39);">try 块 </font><font style="color:rgb(44, 44, 54);">：</font>
<font style="color:rgb(44, 44, 54);">包裹可能抛出异常的代码。若 try 块内未抛出异常，程序继续执行后续代码。</font>

#### <font style="color:rgb(17, 24, 39);">throw 表达式 </font><font style="color:rgb(44, 44, 54);">：</font>
<font style="color:rgb(44, 44, 54);">抛出异常时，程序立即终止当前函数的执行，并沿调用链向上查找匹配的 </font>`**<font style="color:rgb(97, 92, 237);background-color:rgb(239, 238, 255);">catch</font>**`<font style="color:rgb(44, 44, 54);"> 块。</font>

#### <font style="color:rgb(17, 24, 39);">catch 块 </font><font style="color:rgb(44, 44, 54);">：</font>
<font style="color:rgb(44, 44, 54);">捕获并处理特定类型的异常。支持多态匹配（如 </font>`**<font style="color:rgb(97, 92, 237);background-color:rgb(239, 238, 255);">catch (const exception& e)</font>**`<font style="color:rgb(44, 44, 54);"> 可捕获所有标准异常派生类）。</font>

#### <font style="color:rgb(17, 24, 39);">终止模型（Termination Model） </font><font style="color:rgb(44, 44, 54);">：</font>
<font style="color:rgb(44, 44, 54);">异常未被捕获时，程序调用 </font>`**<font style="color:rgb(97, 92, 237);background-color:rgb(239, 238, 255);">terminate()</font>**`<font style="color:rgb(44, 44, 54);"> 终止（默认调用 </font>`**<font style="color:rgb(97, 92, 237);background-color:rgb(239, 238, 255);">abort()</font>**`<font style="color:rgb(44, 44, 54);">）。</font>

**<font style="color:rgb(17, 24, 39);">流程 </font>**<font style="color:rgb(44, 44, 54);">：</font>

+ <font style="color:rgb(44, 44, 54);">抛出异常 → 终止当前函数 → 栈展开 → 查找匹配的 </font>`**<font style="color:rgb(97, 92, 237);background-color:rgb(239, 238, 255);">catch</font>**`<font style="color:rgb(44, 44, 54);"> → 执行处理代码 → 程序继续执行后续代码。</font>

**<font style="color:rgb(17, 24, 39);">注意 </font>**<font style="color:rgb(44, 44, 54);">：未匹配的异常会导致程序崩溃，需确保关键路径有兜底处理。</font>

#### <font style="color:rgb(44, 44, 54);">示例代码：</font>
```cpp
#include <iostream>
#include <stdexcept>
using namespace std;

// 自定义除零异常类
class DivideByZeroException : public runtime_error {
public:
    DivideByZeroException() : runtime_error("Attempted to divide by zero") {}
};

// 计算商
double quotient(int numerator, int denominator) {
    if (denominator == 0) {
        throw DivideByZeroException(); // 抛出异常
    }
    return static_cast<double>(numerator) / denominator;
}

int main() {
    int a = 10, b = 0;
    try {
        double result = quotient(a, b); // 可能抛出异常
        cout << "Result: " << result << endl;
    } catch (const DivideByZeroException& e) {
        cerr << "DivideByZeroException: " << e.what() << endl; // 捕获并处理
    } catch (const exception& e) {
        cerr << "Standard exception: " << e.what() << endl; // 兜底捕获
    } catch (...) {
        cerr << "Unknown exception occurred." << endl; // 捕获所有未匹配异常
    }
    return 0;
}
```

### 处理标准库抛出的异常
#### **核心目标**
捕获并处理C++标准库抛出的异常（如 `bad_alloc`、`out_of_range` 等），避免程序因未处理异常而崩溃。

+ **关键操作**：使用 `try`、`catch` 和 `throw` 分离正常逻辑与错误处理。

#### **示例：**`bad_alloc`
+ **场景**：使用 `new` 动态分配内存时，若内存不足，会抛出 `bad_alloc` 异常。
+ **传统问题**：未捕获异常会导致程序直接调用 `abort()`，无法释放资源。
+ **解决方案**：通过 `try-catch` 捕获异常，执行清理操作或优雅退出。

##### **代码：捕获 **`bad_alloc`
```cpp
#include <iostream>
#include <new> // for bad_alloc
using namespace std;

class Test {
public:
    Test() { cout << "Constructor called." << endl; }
    ~Test() { cout << "Destructor ok." << endl; }
};

int main() {
    Test t;
    double* ptr[50];

    try {
        for (int i = 0; i < 50; i++) {
            ptr[i] = new double[50000000]; // 可能抛出 bad_alloc
            cout << "Allocated 50,000,000 doubles in ptr[" << i << "]" << endl;
        }
    } catch (bad_alloc& e) {
        cerr << "Exception occurred: " << e.what() << endl;
    }

    cout << "Exception handled." << endl;
    return 0;
}
```

**输出示例**：

```plain
Constructor called.
Allocated 50,000,000 doubles in ptr[0]
Allocated 50,000,000 doubles in ptr[1]
...
Exception occurred: bad allocation
Destructor ok.
Exception handled.
```

#### **异常类型匹配规则**
+ **is-a 关系**：`catch` 块按类型匹配异常。若异常类型是 `catch` 声明类型的派生类，则匹配成功。

```cpp
catch (const std::exception& e) { /* 可捕获所有标准库异常 */ }
```

+ **捕获所有异常**：使用 `catch (...)` 捕获未知异常。

```cpp
try {
    // 可能抛出任何异常
} catch (...) {
    cerr << "Unknown exception caught!" << endl;
}
```

#### **异常规范**
+ **异常说明（Exception Specification）**：指定函数可能抛出的异常类型。

```cpp
void func() throw(std::runtime_error); // 仅允许抛出 runtime_error
void func() throw();                   // 不允许抛出任何异常
```

+ **C++11 替代方案**：使用 `noexcept` 指定函数不抛出异常。

```cpp
void func() noexcept; // 等效于 throw()
```



### 栈展开
```cpp
#include <iostream>
using namespace std;

class obj{
  int id;
public:
  obj(int n){
    id=n;
    cout<<"ctor"<<n<<endl;
  }
  ~obj(){
    cout<<"dtor"<<id<<endl;
  }
};

void f2(){
  obj o(2);
  double a=0;
  try{
    throw a;
  }
  catch(double e){
    cout<<"OK2! "<<e<<endl;
    throw;
  }
  cout<<"end2"<<endl;
}

void f1(){
  obj o(1);
  try{
    f2();
  }
  catch(char e){
    cout<<"OK1! "<<e<<endl;
  }
  cout<<"end1"<<endl;
}
int main(){
  try{
    obj o(0);
    f1();
  }
  catch(double e){
    cout<<"OK0!"<<e<<endl;
  }
  cout<<"end0"<<endl;
  return 0;
}
```

>    							假如删去24行throw;
>
> 输出：ctor0				   	   输出：ctor0
>
> ctor1						      ctor1			
>
> ctor2 					      ctor2
>
> OK2! 0					      OK2! 0
>
> dtor2					    	      end2
>
> dtor1					              dtor2
>
> dtor0					              end1
>
> OK0! 0					      dtor1
>
> end0						      dtor0
>
>            end0
>

**<font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);">为什么</font>**`**<font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);">dtor2</font>**`**<font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);">在</font>**`**<font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);">OK0!</font>**`**<font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);">之前？</font>**

+ <font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);">当</font>`<font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);">f2</font>`<font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);">中的</font>`<font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);">throw;</font>`<font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);">重新抛出异常时，程序会立即退出</font>`<font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);">f2</font>`<font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);">函数作用域</font>
+ <font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);">在退出</font>`<font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);">f2</font>`<font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);">时，其局部对象</font>`<font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);">o(2)</font>`<font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);">必须被析构 → 输出</font>`<font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);">dtor2</font>`
+ <font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);">只有完成当前作用域的清理后，异常才会继续向上传播到</font>`<font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);">main</font>`

**<font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);">技术要点总结</font>**

1. **<font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);">栈展开的触发时机</font>**<font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);">：每次执行</font>`<font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);">throw</font>`<font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);">（包括重新抛出）都会立即触发当前作用域的析构</font>
2. **<font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);">析构顺序原则</font>**<font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);">：后构造的对象先析构（LIFO/FILO 后出先进/先进后出）</font>
3. **<font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);">重新抛出的特殊性</font>**<font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);">：</font>`<font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);">throw;</font>`<font style="color:rgba(0, 0, 0, 0.9);background-color:rgb(252, 252, 252);">语句会保留原始异常对象，但会触发当前函数作用域的清理</font>







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

### <font style="background-color:rgb(243, 245, 250);">1.</font>`left`<font style="background-color:rgb(243, 245, 250);"> 和 </font>`right`
<font style="background-color:rgb(243, 245, 250);">这两个操作符用于设置输出流的对齐方式。默认情况下，</font>`iostream`<font style="background-color:rgb(243, 245, 250);"> 是右对齐的。特点：都是</font>**<font style="background-color:rgb(243, 245, 250);">粘性设置</font>**<font style="background-color:rgb(243, 245, 250);">。</font>

+ `left`<font style="background-color:rgb(243, 245, 250);">：设置输出流为左对齐。</font>
+ `right`<font style="background-color:rgb(243, 245, 250);">：设置输出流为右对齐（</font>**<font style="background-color:rgb(243, 245, 250);">默认</font>**<font style="background-color:rgb(243, 245, 250);">）。</font>

### <font style="background-color:rgb(243, 245, 250);">2.</font>`setw(int width)`
<font style="background-color:rgb(243, 245, 250);">这个操作符用于设置输出的宽度。如果输出的字段宽度小于指定的宽度，</font>`setw`<font style="background-color:rgb(243, 245, 250);"> 会在字段前填充空格（默认），或者根据对齐方式填充。如果输出字段宽度大于指定的宽度，setw失效，无事发生。</font>

### <font style="background-color:rgb(243, 245, 250);">3.</font>`setfill(char fill)`
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

### <font style="background-color:rgb(243, 245, 250);">4.</font>`fixed`
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

### 6.`scientific`
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





