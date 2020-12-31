# 06. gitignore

* 우리가 git으로 관리하고 싶지 않은 파일들을 제외시키는 방법

  * 우리가 원하지 않는 파일을 제외
  * 외부에 공개되면 안되는 것들(key, secret)

* `.gitignore`

  * `.gitignore`에 작성된 파일들은 git으로 관리하지 않겠다! 무시해라!

  ```
  .DS_Store # Mac OS에서만 사용하는 파일
  ```

* 작성법

  ```
  f.txt # 특정 파일
  secret/ # 특정 폴더, 그 안에 있는 것들도 다 제외
  *.png # 특정 확장자 (.png로 끝나는 파일명을 모두 제외)
  !profile.png # 모든 png는 빼고, profile.png는 넣고!
  ```

* 처음부터, git으로 관리한 적이 없을 때부터 관리를 해줘야 함!
* 그렇다면 이미 commit을 한 파일들은 어떻게 제외할 수 있을까?
  1. `.gitignore` 에다가 파일 명시
  2. `git rm --cached [파일명]`
     * git에서 더 이상 관리하지 않겠다.
     * ![image-20201230134648273](images/image-20201230134648273.png)
     * ![image-20201230134703895](images/image-20201230134703895.png)
     * ![image-20201230134729523](images/image-20201230134729523.png)
     * ![image-20201230134744673](images/image-20201230134744673.png)
     * 

* `.DS_Store` : Mac OS
* `Thumbs.db` : Windows
* VSCode 상 파일명 옆 문자
  * U(Untracted files)
  * M(Modified)





Main 역할:

git hub 상에 repo 생성

내가 생성한 repo에 초대 (invite a collaborator)

초대 링크 공유

git clone

README.md 파일 생성

바로 origin main 으로 git push 가능







