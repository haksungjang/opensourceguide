# Pull Request

### References

* [https://github.com/kubernetes/community/blob/master/contributors/guide/github-workflow.md](https://github.com/kubernetes/community/blob/master/contributors/guide/github-workflow.md)

![](../.gitbook/assets/image%20%281%29.png)

## Step 1. Fork

Upstream Repository를 자신의 GitHub 계정으로 [Fork](https://help.github.com/en/github/getting-started-with-github/fork-a-repo) 한다.

## Step 2. Clone

Fork한 Repository를 자산의 Local working directory로 Clone 한다.

```text
$ mkdir -p $working_dir
$ cd $working_dir
$ git clone https://github.com/$user/[repository]
```

Upstream Repository를 [Remote](https://git-scm.com/book/ko/v2/Git-%EB%B8%8C%EB%9E%9C%EC%B9%98-%EB%A6%AC%EB%AA%A8%ED%8A%B8-%EB%B8%8C%EB%9E%9C%EC%B9%98)에 추가한다.

```text
$ cd [repository]
$ git remote add upstream https://github.com/[upstream]/[repository]

# Confirm that your remotes make sense: 
$ git remote -v
```

## Step 3. Create a branch

먼저 master branch를 fetch와 [rebase](https://git-scm.com/book/ko/v2/Git-%EB%B8%8C%EB%9E%9C%EC%B9%98-Rebase-%ED%95%98%EA%B8%B0)하여 최신 상태로 유지한다. 

```text
$ cd $working_dir/[repository]
$ git fetch upstream
$ git checkout master
$ git rebase upstream/master
```

그리고 개발용 [branch](https://git-scm.com/book/ko/v2/Git-%EB%B8%8C%EB%9E%9C%EC%B9%98-%EB%B8%8C%EB%9E%9C%EC%B9%98%EB%9E%80-%EB%AC%B4%EC%97%87%EC%9D%B8%EA%B0%80) \(myfeature\)를 생성한다. 

```text
$ git checkout -b myfeature
```

## Step 4. Keep your branch in sync

Branch를 fetch와 [rebase](https://git-scm.com/book/ko/v2/Git-%EB%B8%8C%EB%9E%9C%EC%B9%98-Rebase-%ED%95%98%EA%B8%B0)하여 최신 상태로 유지한다. 

```text
# While on your myfeature branch
$ git fetch upstream
$ git rebase upstream/master
```

그 상태에서 code 작업을 한다. 

## Step 5. Commit

수정 사항을 [commit](https://git-scm.com/book/ko/v2/Git%EC%9D%98-%EA%B8%B0%EC%B4%88-%EC%88%98%EC%A0%95%ED%95%98%EA%B3%A0-%EC%A0%80%EC%9E%A5%EC%86%8C%EC%97%90-%EC%A0%80%EC%9E%A5%ED%95%98%EA%B8%B0) 한다. 

```text
$ git commit -a -m '[commit message]'
```

## Step 6. Push

myfeature branch의 수정 사항을 자신의 GitHub Repository에 Push한다. 

```text
git push -f origin myfeature
```

## Step 7. Create a pull request

GitHub에서 자신의 Repository에 가면 Compare & pull request 버튼이 활성화 된 것을 볼 수 있다. 이를 눌러서 Pull Request를 생성한다. 

이후 Upstream Repository의 관리자는 요청된 Pull Request를 검토하여 Merge 여부를 결정한다. 

