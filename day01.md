理论题目：

1.在go.mod中有一些是eino,还有一些是indirect的，分开的原因是前一个是我们主动导入的，后面的是被动注入的

2.你依赖了 `github.com/cloudwego/eino v0.9.8`，但你需要 eino 在 GitHub 上的最新 commit（还没发新版本）。你有哪两种方法用上这个最新 commit？分别怎么写？1.用伪版本号，go get github.com/cloudwego/eino@abcdef123456    2.用replace  在go.mod的末尾加replace github.com/cloudwego/eino v0.9.8 => github.com/cloudwego/eino@latest-commit-hash

3.为什么 `go.sum` 要提交到 git，但 `vendor/` 目录不提交？因为是为了安全校验，go.sum中记录了每个依赖版本的**密码学哈希值**。如果有人篡改了 GitHub 上的依赖代码，Go 对比 `go.sum` 发现哈希不匹配就会**拒绝下载**。`vendor/` 只是依赖的本地副本。

4.你创建的 `internal/` 目录和 `pkg/` 目录有什么区别？Go 编译器对 `internal/` 有什么强制限制？如果外部项目尝试 `import "github.com/qpzz/myagent-platform/internal/agent"` 会发生什么？internal下的包可以只能被他父目录下的其他代码import，其他的不行，但是pkg是都可以的



编程：

学会了使用exec.Command("","","","")输出json,然后构建json对应的go结构，最后用反序列化json.Unmarshal(output,&data)来讲json数据反序列化



学会了使用testing包

测试函数硬性规则：

1. 函数名必须以 `Test` 开头
2. 参数固定 `t *testing.T`，用来打印错误、标记测试失败
3. 无返回值



还有提交到仓库中

```bash
git add .
git commit -m "Day 1: Go项目骨架 + go.mod解析 + 测试"
git remote add origin https://github.com/qpzz/myagent-platform.git
git push -u origin main
```





```bash
把仓库克隆到本地       git clone git@github.com:qpzz/agent-learning-notes.git
# 把笔记复制进去
cp 你的笔记文件路径 agent-learning-notes/

# 进去提交推送
cd agent-learning-notes
git add day01.md
git commit -m "Day 1 总结"
git push
```

