# CentOS 7 常用 Linux 命令笔记
## 基础命令
### 注释
*  ......：后续还可添加与前面一样格式的语句
* []:为根据实际情况而写
## 未归类 
- `man`：查询指令的使用方式
- `cd`：切换目录

---

## 软件环境变量配置（以 JDK 为例）
1. 编辑环境变量文件
```bash
vi /[文件路径]/[文件路径].../[文件名]
```
2. 在文件中添加配置
```bash
export JAVA_HOME=/[opt]/[module]/[jdk] #声明 jdk 安装根目录
export PATH=$PATH:$JAVA_HOME/[bin] #将 jdk 的 bin 目录加入系统命令路径
```
3. 让配置立即生效
```bash
source /[文件路径]/[文件路径]
```
4. 查看变量
```bash
echo [变量名]   # 打印变量名
echo $[变量名]  # 打印变量值
```

---

## Hadoop 相关配置命令
### 用户创建与配置
```bash
useradd [hadoop]       # 创建 hadoop 用户（仅 root 可执行）
passwd [hadoop]        # 为 hadoop 用户设置密码
grep 'hadoop' /[文件路径]/[文件路径]  # 验证用户配置
```
> `grep '关键词' 目标文件`：在文件或命令输出中匹配包含指定关键词的行，常用于验证配置。

---

### 安装包解压（以 Hadoop 为例）
```bash
tar -zxvf /[opt]/[software]/[hadoop-3.3.6.tar.gz] -C /[opt]/[module]/
```
#### 参数说明
- `tar`：打包/解压核心命令
- `-z`：处理 `.gz` 格式压缩包
- `-x`：解压模式（与打包 `-c` 区分）
- `-v`：显示解压过程
- `-f`：指定压缩包文件，必须放在所有参数最后
- `-C`：指定解压目标目录

#### 路径说明
- **绝对路径**：从根目录开始的完整文件路径
- **相对路径**：从当前目录出发的路径，`./` 表示当前目录

---

## SSH 密钥配置（免密登录）
```bash
ssh-keygen -t rsa -b 4096    # 生成 4096 位 RSA 密钥
ssh-copy-id [主机名]          # 将本机公钥复制到目标主机
ssh [主机名]                 # 验证免密登录
exit                         # 退出远程主机，回到原主机
```
#### 参数说明
- `-t`：指定密钥类型
- `-b`：指定密钥长度

---

## 防火墙管理
```bash
systemctl stop firewalld     # 立即停止防火墙
systemctl disable firewalld  # 禁止防火墙开机自启
systemctl status firewalld   # 查看防火墙运行状态
```