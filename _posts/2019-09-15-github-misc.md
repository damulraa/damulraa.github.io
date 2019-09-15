---
title:  "Github advanced"
excerpt: "Git, Github 관련 miscellanies"

categories:
  - Blog
tags:
  - [Git, Github,]
last_modified_at: 2019-09-15T05:30:00-08:00
---

## --set-upstream-to
### Branch 추적

* 리모트 트래킹 브랜치를 로컬 브랜치로 Checkout 하면 자동으로 “트래킹(Tracking) 브랜치” 가 만들어진다
    * 트래킹 하는 대상 브랜치를 “Upstream 브랜치” 라고 부른다.
        - Upstream, Downstream은 상대적인 개념이다.
        - Github과 같이 Server-Client 환경에서는 upload, download로 보면된다.
        - 즉 client -> server : upstream, client <- server : downstream
    * 트래킹 브랜치는 리모트 브랜치와 직접적인 연결고리가 있는 로컬 브랜치이다. 
    * 트래킹 브랜치에서 git pull 명령을 내리면 리모트 저장소로부터 데이터를 내려받아 연결된 리모트 브랜치와 자동으로 Merge 한다.

* 서버로부터 저장소를 Clone을 하면 Git은 자동으로 master 브랜치를 origin/master 브랜치의 트래킹 브랜치로 만든다. 
* 트래킹 브랜치를 직접 만들 수 있는데 리모트를 origin 이 아닌 다른 리모트로 할 수도 있고, 브랜치도 master 가 아닌 다른 브랜치로 추적하게 할 수 있다. 
* git checkout -b <branch> <remote>/<branch> 명령으로 간단히 트래킹 브랜치를 만들 수 있다. --track 옵션을 사용하여 로컬 브랜치 이름을 자동으로 생성할 수 있다.

### set-upstream-to
만약 git checkout abc_branch 로 당신의 local에 branch를 만들었다.
이를 github의 origin repository 의 def_branch를 추적하게 하고 싶다면,
```bash
git checkout abc_branch # local에 branch 생성
git push origin abc_branch # remote origin에 abc_branch를 push하여 origin에도 branch 생성, 이미 생성된 branch라면 이부분은 생략 가능.
git branch --set-upstream-to origin/abc_branch # upstream - to를 설정(origin/abc_branch로.)
```

### Remote Origin의 모든 Remote Branch를 Track하는 명령어가 있나요?
* 없습니다.
* Shell Script를 사용하는 방법 뿐입니다.
```
# Need to check
```


## fast-forward
1. 사전적 의미 : fast-forward 는 테이프에서 앞으로 빨리 감는 것을 의미한다. 즉 빨리 감기이다.
2. context  : 

|![current-state]({{"/assets/img/current-state.png"| relative_url}})|
|:--:|
|현재 상태(master,bugfix branch)|

이런 경우 master의 이력이 이후 변경되지 않았다면 B 와 X의 merge는 따로 필요없다.
즉 B(master)를 X로 이동만 시켜주면 된다. 이걸 fast-forward 라고 한다.
따라서 이렇게 하는 경우는 bugfix 와 master의 이력이 하나이므로 이력관리에서는 별루다.

|![fast-forward-commit]({{"/assets/img/fast-forward-commit.png"| relative_url}})|
|:--:|
|fast-forward로 merge한 그림|

#### master에 이후 변경 이력이 있는 경우는 일반적인 merge commit

|![normal-merge-commit]({{"/assets/img/normal-merge-commit.png"| relative_url}})|
|:--:|
|일반적인 merge한 그림|

## non-fast-forward 
* 위의 2번의 경우 간결하지만 브랜치 이력관리에서는 어떤 브랜치에서 뭐가 분기되고, 또 뭐가 머지되었는지 안보이니 *non-fast-forward* 로 이력을 보는 것도 좋다.
  
   |![non-fast-forward-commit]({{"/assets/img/non-fast-forward-commit.png"| relative_url}})|
   |:--:|
   |non-fast-forward 그림|
              
              




* Local 변수에는 앞에 _ 를 붙이지 않는다.( function 내부에서만 사용하는 로컬변수 leading underscore )
* len(abc) != 0 -> abc
> ###### For sequences, (strings, lists, tuples), use the fact that empty sequences are false.
>
>Yes: if not seq:
>if seq:
>
>No: if len(seq):
>if not len(seq):

* 리스트 초기화 : list() -> []
* I am in <span style="font-family:Papyrus; font-size:2em; color:red">LOVE!</span>
* for loop에 enumerate 사용하여 count = count + 1 제거
  * ```python for idx, value in enumerate([1,2,3,4,5], 1) ```
  * ```python for tuple_item in enumerate([1,2,3,4,5])```
* 문자열 + 보다는 string{}.{}'.format( , ,...) 형식 그리고, zfill(2) 보다는 {:02}로 formatting