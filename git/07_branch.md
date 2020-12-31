# 07. Branch

* branch: 가지->가지치기
* `git branch` : 브랜치 목록 확인
* `git branch login`: `login` 브랜치 생성
* `git switch login` : login 브랜치로 이동
* 가지치기 시작점부터 보여줌
  * ![image-20201230153808932](images/image-20201230153808932.png)
  * `git log --oneline --graph --all` :  한줄로, 그래프 포함, 모든 브랜치를 보여줌
  * `git switch -c login` : 브랜치 만들면서 바로 이동(c: create)
    * `git branch login` + `git switch login` 
    *  구버전
      * 이동
        * `git checkout login` : 이동 
        * `git checkout -b login` : 생성하면서 바로 이동

