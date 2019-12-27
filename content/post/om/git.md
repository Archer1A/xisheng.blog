---
title: "Git"
date: 2019-12-27T16:48:50+08:00
draft: true
---

## 合并
    git add ./
    git commit -m "update some"
    git pull --rebase dev
    
    if has conflict
        handle conflict
        git add ./
        git rebase --continue
    end
    git push origin ${your_branch}

## show commit log
git log

## 多次commit后取消前面的commit
git rest --soft= ${commit_id}

## git瘦身
git gc  --prune=now

## 完全复制其他分支
git reset origin/${other_branch}