# RL-Demo
一些强化学习相关的项目

- 红蓝对抗
- 智能交通信号灯规划


# **GitHub & Git 使用完整流程**
**一个前提**：配置 Git 的全局用户信息。通过
```bash
git config --global user.name "xxxxx"
git config --global user.email "xxxxx"
```
Git 会记录提交者的用户名和邮箱。这些信息会显示在提交历史中，方便其他人知道是谁提交了代码。由于使用的的邮箱和 GitHub 绑定的邮箱一致，GitHub 会自动将这些提交关联到你的 GitHub 账号。
## **1. 克隆（Clone）他人项目**
> 克隆就是把 GitHub 上的某个仓库下载到本地，以便查看或修改代码。

### **1.1 使用 SSH 克隆**
```bash
git clone git@github.com:对方的GitHub用户名/仓库名.git
```
示例：
```bash
git clone git@github.com:torvalds/linux.git
```
**说明：**
- 这个命令会在当前目录下创建一个 `linux` 文件夹，并把 `linux` 仓库的代码下载到本地。

### **1.2 进入仓库目录**
```bash
cd 仓库名
```
例如：
```bash
cd linux
```

### **1.3 查看仓库状态**
```bash
git status
```
如果只是想查看代码，而不改动，直接用 `ls` 浏览文件即可。

---

## **2. 提交（Push）自己的项目到 GitHub**
> 适用于 **创建新项目** 或 **更新已有项目**。

### **2.1 创建新仓库**
如果是新建项目，需要先在 GitHub 创建仓库：
1. 登录 GitHub
2. 点击右上角 ➝ “+” ➝ “New repository”
3. **填写仓库名**（Repository name）
4. 选择 **Public（公开）** 或 **Private（私有）**
5. 点击 **“Create repository”**

**注意**：新仓库不会自动包含 `README.md`，可以选择是否创建。

### **2.2 在本地创建新项目**
1. 在本地创建一个文件夹：
   ```bash
   mkdir MyProject && cd MyProject
   ```
2. 初始化 Git：
   ```bash
   git init
   ```
3. 创建一个 `README.md`（可选）：
   ```bash
   echo "# MyProject" > README.md
   ```
4. 把所有文件添加到 Git：
   ```bash
   git add .
   ```
5. 提交到本地仓库：
   ```bash
   git commit -m "初始化项目"
   ```
6. 关联远程仓库：
   ```bash
   git remote add origin git@github.com:GitHub用户名/仓库名.git
   ```
   例如：
   ```bash
   git remote add origin git@github.com:223qyc/MyProject.git
   ```
7. **推送到 GitHub**
   ```bash
   git push -u origin main
   ```

---

## **3. 修改本地代码并更新到 GitHub**
> 当你对本地代码进行了修改，需要提交并推送到 GitHub。

1. **查看本地修改**
   ```bash
   git status
   ```
2. **添加所有修改**
   ```bash
   git add .
   ```
3. **提交修改**
   ```bash
   git commit -m "修改了功能 XYZ"
   ```
4. **推送到 GitHub**
   ```bash
   git push origin main
   ```

---

## **4. 从 GitHub 拉取最新代码**
> 当团队成员修改了远程仓库的代码，你需要同步最新代码到本地。

```bash
git pull origin main
```
**如果出现冲突**
1. Git 会提示你解决冲突的文件
2. 手动编辑冲突文件，删除冲突标记 `<<<<<<<` 和 `>>>>>>>`
3. 重新提交代码：
   ```bash
   git add .
   git commit -m "解决冲突"
   git push origin main
   ```

---

## **5. 分支管理**
> 分支是 Git 的核心功能，适用于多人协作开发。

### **5.1 创建新分支**
```bash
git checkout -b 新分支名
```
示例：
```bash
git checkout -b feature-login
```

### **5.2 切换分支**
```bash
git checkout main  # 切换回主分支
git checkout feature-login  # 切换到 feature-login 分支
```

### **5.3 合并分支**
> 当 `feature-login` 分支开发完成，合并到 `main` 分支：
```bash
git checkout main  # 切换到主分支
git merge feature-login  # 合并 feature-login 分支
git push origin main  # 推送到远程
```

### **5.4 删除分支**
```bash
git branch -d feature-login  # 删除本地分支
git push origin --delete feature-login  # 删除远程分支
```

---

## **6. Fork & Pull Request（贡献代码）**
> 当你想贡献代码到别人的开源项目，而不是直接修改它时，你需要使用 Fork & Pull Request。

### **6.1 Fork 仓库**
1. 打开目标仓库，例如 `https://github.com/torvalds/linux`
2. 点击右上角 **“Fork”**
3. 现在你会在 **你的 GitHub 账号下** 看到这个仓库。

### **6.2 克隆 Fork 的仓库**
```bash
git clone git@github.com:你的GitHub用户名/linux.git
cd linux
```

### **6.3 创建新分支**
```bash
git checkout -b 修复-bug-xxx
```

### **6.4 提交修改**
```bash
git add .
git commit -m "修复了 XXX 问题"
git push origin 修复-bug-xxx
```

### **6.5 发起 Pull Request**
1. 打开 GitHub，进入你的 Fork 仓库
2. 点击 **"New pull request"**
3. 选择要合并的目标分支（通常是 `main`）
4. 填写 PR 描述，点击 **提交**

如果维护者接受你的 PR，你的代码就会合并到原始仓库。

---

# **总结**
### **克隆他人项目**
```bash
git clone git@github.com:对方的GitHub用户名/仓库名.git
cd 仓库名
git status
```

### **新建并推送自己的项目**
```bash
mkdir MyProject && cd MyProject
git init
git add .
git commit -m "初始化项目"
git remote add origin git@github.com:你的GitHub用户名/你的仓库名.git
git push -u origin main
```

### **更新本地代码**
```bash
git pull origin main
```

### **分支管理**
```bash
git checkout -b 新功能分支
git checkout main
git merge 新功能分支
git push origin main
```

### **贡献开源项目（Fork & PR）**
```bash
git clone git@github.com:你的GitHub用户名/对方的仓库.git
git checkout -b 新分支
git add .
git commit -m "修复问题"
git push origin 新分支
```
然后在 GitHub 上发起 **Pull Request**。
