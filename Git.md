# Git

## Git代码提交流程

```bash
# 添加文件追踪
git add . | file_name
# 提交记录
git commit -m 'commit info'
# 获取线上最新代码
git pull origin dev | master
# 推送代码到服务器
git push origin dev | master
```

```bash
# 切换分支
git checkout dev | master
# 创建分支
git checkout -b name
# 删除分支
git branch -d name
# 合并分支（在当前分支下合并目标分支）
git merge <branch>
```

```bash
# 查看状态
git status
```

```bash
# 有冲突合并
:wq
```

