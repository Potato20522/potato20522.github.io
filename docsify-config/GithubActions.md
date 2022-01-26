参考来源：

https://zhuanlan.zhihu.com/p/93829286

https://www.cnblogs.com/babycomeon/p/12771624.html

# 介绍

github actions。

`github` 会提供一个以下配置的服务器做为 runner，可以说相当良心了。

- 2-core CPU
- 7 GB of RAM memory
- 14 GB of SSD disk space（github文档上说是500 MB）

另外如果你有网络时延的需求，（比如推送及拉取镜像时产生的网络时延），你也可以自建 runner。

## GitHub Action 基本概念

GitHub Actions 有一些自己的术语。

1. workflow （工作流程）：持续集成一次运行的过程，就是一个 workflow。
2. job （任务）：一个 workflow 由一个或多个 jobs 构成，含义是一次持续集成的运行，可以完成多个任务。
3. step（步骤）：每个 job 由多个 step 构成，一步步完成。
4. action （动作）：每个 step 可以依次执行一个或多个命令（action）。

## 创建第一个工作流

- 如果 .github/workflows 目录不存在，请在 GitHub 的仓库中创建此目录。


- 在 .github/workflow 目录中，创建一个名为 github-actions-demo.yml 的文件。 更多信息请参阅“创建新文件”。


- 将以下 YAML 内容复制到 github-actions-demo.yml 文件中：

```yaml
name: GitHub Actions Demo
on: [push]
jobs:
  Explore-GitHub-Actions:
    runs-on: ubuntu-latest
    steps:
      - run: echo "🎉 The job was automatically triggered by a ${{ github.event_name }} event."
      - run: echo "🐧 This job is now running on a ${{ runner.os }} server hosted by GitHub!"
      - run: echo "🔎 The name of your branch is ${{ github.ref }} and your repository is ${{ github.repository }}."
      - name: Check out repository code
        uses: actions/checkout@v2
      - run: echo "💡 The ${{ github.repository }} repository has been cloned to the runner."
      - run: echo "🖥️ The workflow is now ready to test your code on the runner."
      - name: List files in the repository
        run: |
          ls ${{ github.workspace }}
      - run: echo "🍏 This job's status is ${{ job.status }}."
```

git commit

git push

到github Actions菜单下查看运行结果。



