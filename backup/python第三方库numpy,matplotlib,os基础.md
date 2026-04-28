# NumPy + Matplotlib + OS 核心操作总结

## 一、基础导入库
```python
import numpy as np
import matplotlib.pyplot as plt
import os
```
>[!NOTE]
以上库若在pycharm中运用需提前安装配置好环境
可在anaconda的jupyter中进行编写
>

---

## 二、NumPy 数组创建与基础属性
### 1. 数组创建

| 代码 | 说明 |
|------|------|
| `np.array([1])` | 创建一维数组 |
| `np.array([[1,2],[2,33]])` | 创建二维数组 |
| `np.ones(shape=(3,4))` | 生成 3行4列全1数组 |
| `np.eye(6)` | 生成 6×6 单位矩阵（对角线为1，其余为0） |
| `np.linspace(0,100,num=20)` | 生成 0~100 等差数列，共20个数据 |
| `np.arange(10,50,step=2)` | 生成 10~50 等差数列，步长为2 |
| `np.random.randint(0,100,size=(5,6))` | 生成 5行6列随机整数数组（范围0~100） |

### 2. NumPy中array创建数组操作优先级

| 代码 | 说明 |
|------|------|
| `np.array([12,1.1,'2'])` | 混合类型自动转为字符串数组 |
| `np.array([1.2,2])` | 混合数值自动向上转换为浮点数 |
| `np.array(['1.2',2])` | 字符串+数字 转为 字符串数组 |

* 由此可知
  - 数组：数组存储数据的类型必须是统一类型
    - 优先级：字符串>浮点数>整数

### 3. 数组属性查询

| 代码 | 说明 |
|------|------|
| `arr.size` | 返回数组元素总个数 |
| `arr.shape` | 返回数组形状（行数, 列数） |
| `arr.ndim` | 返回数组维度（一维/二维/...） |
| `arr.dtype` | 返回数组元素数据类型 |

---

## 三、数组变形与索引切片
### 1. 数组变形（reshape）
- **核心规则**：变形前后元素总数必须相等
* 二维变一维
```python
arr=np.random.randint(0,100,size=(5,6))  # 5*6=30个元素
arr_1=arr.reshape(30)  # 一维数组（30个元素）
# arr_1.reshape(6,5) 正确（6*5=30）
# arr_1.reshape(6,6) 错误（6*6=36≠30）
```
* 一维变二维
```python
arr=np.random.randint(0,100,size=(5,6))  # 5*6=30个元素
arr_1=arr.reshape(30)  # 一维数组（30个元素）
arr_2=arr_1.reshape((5,6))
```

### 2. 索引与切片
| 代码 | 说明 |
|------|------|
| `arr[i, j]` | 取第 i+1 行、第 j+1 列元素 |
| `arr[i, :]` | 取第 i+1 行所有元素 |
| `arr[:, j]` | 取第 j+1 列所有元素 |
| `arr[::-1, :]` | 行反转（上下翻转） |
| `arr[:, ::-1]` | 列反转（左右翻转） |

---

## 四、数组级联（拼接）
### `np.concatenate()` 函数
```python
# 列级联（axis=0）：沿列方向拼接，行数增加
np.concatenate((arr, arr), axis=0)

# 行级联（axis=1）：沿行方向拼接，列数增加
np.concatenate((arr, arr), axis=1)
```
- `axis=0`：上下拼接（行数叠加）
- `axis=1`：左右拼接（列数叠加）

---

## 五、NumPy 统计计算
| 函数 | 说明 |
|------|------|
| `arr.sum(axis=0)` | 沿列方向求和 |
| `arr.max(axis=0)` | 沿列方向求最大值 |
| `np.ptp(arr, axis=0)` | 沿列方向求极差（最大值-最小值） |
| `np.mean(arr, axis=0)` | 沿列方向求平均值 |
| `np.var(arr)` | 计算数组方差 |
| `np.std(arr)` | 计算数组标准差（方差开根号） |
| `np.sin(arr)` | 对数组每个元素求正弦值 |
| `np.sort(arr)` | 对数组元素排序 |

>[!NOTE]
极差(ptp)：最大值 − 最小值` max - min`
方差(var)：每个数减去平均值的平方，再求平均`mean((x - x.mean()) ** 2)`
标准差(std)：方差开根号`sqrt(np.var(x))`
>
---

## 六、Matplotlib 图片处理

### 1. 图片读取与展示
* 图片展示为42姐

<img width="2560" height="1546" alt="Image" src="https://github.com/user-attachments/assets/3ec1a9fe-c1db-4580-8174-e2f8f130598f" />

```python
im_arr = plt.imread('./ENDFIELD_SHARE_1770208989.png')
plt.imshow(im_arr)  # 展示图片
plt.show()
```
>[!NOTE]
### 2. 图片数组操作
| 代码 | 说明 |
|------|------|
| `im_arr.shape` | 查看图片形状（高, 宽, 颜色通道） |
| `im_arr + 0.5` | 逐元素加法（调整亮度） |
| `plt.imshow(im_arr[:, ::-1])` | 图片左右翻转 |
| `plt.imshow(im_arr[::-1, :])` | 图片上下翻转 |
| `plt.imshow(im_arr[0:1400, 700:1800])` | 裁剪图片区域 |
| `np.concatenate((im_arr, im_arr), axis=1)` | 图片左右拼接 |
| `np.concatenate((im_arr, im_arr), axis=0)` | 图片上下拼接 |

---

## 七、OS 模块文件操作
| 代码 | 说明 |
|------|------|
| `os.getcwd()` | 获取当前代码所在文件夹路径 |
| `os.listdir('.')` | 列出当前目录下所有文件/文件夹 |
>[!NOTE]
. ：当前目录
.. ：上一级目录
>
---

## 八、矩阵相加
|------|------|
| `np.eye(6)` | 创建矩阵（6*6） |
| `np.eye(6).T` | 反转矩阵 |
| `np.dot(a1,a2) | 矩阵相乘 |

<img width="474" height="324" alt="Image" src="https://github.com/user-attachments/assets/6727a59c-5925-4f72-855d-06faef137972" />

<img width="432" height="126" alt="Image" src="https://github.com/user-attachments/assets/660abe21-c77f-4ae5-a55e-1f205a73a9b5" />

* 这里主要讲解图二，矩阵与矩阵相乘规则为：a矩阵第一行与a1矩阵第一列相乘得出a2矩阵第一行第一列，a矩阵第一行与a1矩阵第二列相乘得出a2矩阵第一行第二列，下面a2矩阵第二行以上规则进行

## 九、常见报错与注意事项
1. **reshape 报错**：`ValueError: cannot reshape array of size 30 into shape (6,6)`
   - 原因：变形前后元素总数不匹配（30 ≠ 36）
   - 解决：确保 `行数 × 列数 = 元素总个数`
2. **NumPy 是第三方库**：需先 `pip install numpy` 才能导入使用
3. **数组运算**：支持逐元素运算（如 `im_arr + 0.5`），无需循环遍历

---

## 十、完整代码示例
```python
import numpy as np
import matplotlib.pyplot as plt
import os

# 1. 创建数组
arr = np.random.randint(0, 100, size=(5, 6))
print("数组形状：", arr.shape)

# 2. 数组变形
arr_1 = arr.reshape(30)
print("变形后一维数组：", arr_1)

# 3. 统计计算
print("列和：", arr.sum(axis=0))
print("列最大值：", arr.max(axis=0))
print("极差：", np.ptp(arr, axis=0))
print("平均值：", np.mean(arr))
print("方差：", np.var(arr))
print("标准差：", np.std(arr))

# 4. 图片处理
im_arr = plt.imread('./ENDFIELD_SHARE_1770208989.png')
plt.imshow(im_arr)
plt.show()

# 5. 文件操作
print("当前路径：", os.getcwd())
print("当前目录文件：", os.listdir('.'))
```
# 图例

<img width="2053" height="6312" alt="Image" src="https://github.com/user-attachments/assets/9b3095c1-f2de-4411-bc07-0db9d0e428ae" />

<img width="2053" height="6312" alt="Image" src="https://github.com/user-attachments/assets/0c2766e4-6d34-48a0-b413-84533fccd76b" />
