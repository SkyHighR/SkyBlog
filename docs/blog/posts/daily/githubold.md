---
draft: false
comments: true
date:
  created: 2024-04-20
  updated: 2024-04-21
slug: githubold
authors:
  - skyhigh
categories:
  - 无聊
---

# **GitHub时光机**

让你的Github主页提交回到1969年  
其他你想要的日期也是可以的啦

<!-- uptoc -->

## 起因 

起初是看到了某个人的主页上的提交时间年份记录居然如此长，都长长长到1969年了，让GitHub个人页面多了几分神秘感，就像下面这样。于是一搜就发现了一个专门用于提交这种奇怪日期的脚本，想着其实也就是改改提交日期，就Fork了一份优化了一下脚本玩玩（[SkyHighR/github-oldyear](https://github.com/SkyHighR/github-oldyear)）

![2](https://mypic.skyhigh.moe/blog/githubold/2.png)


## 开始修改

### 1.准备工作

- 装了git的用户请掠过这行，没装的点[**这里**](https://git-scm.com/download/win)下载安装一下。
- 下面是修改后的代码，复制过去新建一个`index.sh`文档（用那个啥记事本新建一个粘贴进去再命名为`index.sh`就行）。


??? note "index.sh代码"

    ``` shell linenums="1"

    #!/usr/bin/env bash

    _() {
      OLDDIR="githubold"
      
      echo
      printf "请准备好所有咱要提交文件放在index.sh同目录下喵(ReadMe.md啥的) \n"
      echo
      printf "Step 0: \e]8;;https://github.com/new\e\\创建一个仓库喵？(可选,点击创建)\e]8;;\e\\ \n"
      echo
      echo "Step 1: 如何链接到咱的仓库喵？"
      echo
      PS3="要按 1 还是 2 :"
      options=("HTTPS" "SSH")
      select opt in "${options[@]}"
      do
          case $opt in
              "HTTPS")
                  echo
                  printf "Step 2: \e]8;;https://github.com/settings/tokens/new\e\\如果还没有个人访问令牌的话还请点击这里创建\e]8;;\e\\ \n"
                  printf "不要忘记给权限哦 \n"
                  echo
                  echo "PLS CTRL C+V Token|请复制粘贴咱的令牌: "
                  read -r ACCESS_TOKEN
                  [ -z "$ACCESS_TOKEN" ] && exit 1
                  echo
                  echo "Step 3: 键入咱的GitHub用户名: "
                  read -r USERNAME
                  [ -z "$USERNAME" ] && exit 1
                  echo
                  echo "Step 4: 键入咱的仓库名字: "
                  read -r REPONAME
                  [ -z "$REPONAME" ] && exit 1
                  break
                  ;;
              "SSH")
                  echo
                  echo "Step 2: 请复制咱仓库的SSH链接然后粘贴到下面喵"
                  read -r REPO_LINK
                  [ -z "$REPO_LINK" ] && exit 1
                  USERNAME=${REPO_LINK%/*} # remove suffix after "/"
                  USERNAME=${USERNAME#*:} # remove prefix before ":"
                  break
                  ;;
              *) echo "出错了喵, 请按 1 或 2 啦";;
          esac
      done

      [ ! -d $OLDIR ] && mkdir $OLDIR
      find . -name index.sh -prune -o -exec cp -r {} "${OLDIR}/" \;
      cd "${OLDIR}" || exit
      git init
      git add .
      git reset index.sh

      while true; do
        echo "键入想要的日期，像这样: (YYYY-MM-DD)"
        read -r DATE
        if [[ $DATE =~ ^[0-9]{4}-[0-9]{2}-[0-9]{2}$ ]]; then
          break
        else
          echo "出错啦，请使用 YYYY-MM-DD 格式的日期."
        fi
      done

      while true; do
        echo "键入想要的日期，像这样: (HH:MM:SS)"
        read -r TIME
        if [[ $TIME =~ ^[0-9]{2}:[0-9]{2}:[0-9]{2}$ ]]; then
          break
        else
          echo "出错啦，请使用 HH:MM:SS 格式的时间."
        fi
      done

      while true; do
        echo "键入想要的递交信息: "
        read -r COMMIT_MSG
        if [[ -n "$COMMIT_MSG" ]]; then
          break
        else
          echo "不要空着哦￣へ￣"
        fi
      done

      echo "键入想要的分支名:"
      read -r BRANCH_NAME
      [ -z "$BRANCH_NAME" ] && BRANCH_NAME="i-say-unknown"

      GIT_AUTHOR_DATE="${DATE}T${TIME}" \
        GIT_COMMITTER_DATE="${DATE}T${TIME}" \
        git commit -m "${COMMIT_MSG}"
        [ -z "$REPO_LINK" ] && \
          git remote add origin "https://${ACCESS_TOKEN}@github.com/${USERNAME}/${REPONAME}.git" || \
            git remote add origin "${REPO_LINK}"
      git branch -M $BRANCH_NAME
      git push -u origin $BRANCH_NAME -f
      cd ..
      rm -rf "${OLDIR}"

      echo
      echo "大功告成啦喵！"
    } && _

    unset -f _

    ```



### 2.
