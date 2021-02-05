

docker compose up

![image-20210205145027517](images/image-20210205145027517.png)

이미 다른 서비스가 80포트로 실행되고 있음.

도커 앱 인스턴스로 컨테이너마다 연결된 포트를 확인할 수 있다.





![image-20210205162348628](images/image-20210205162348628.png)

```shell
Error response from daemon: OCI runtime create failed: container_linux.go:370: starting container process caused: process_linux.go:459: container init caused: rootfs_linux.go:59: mounting "/run/desktop/mnt/host/c/Users/albei/cloud-msa/docker_workspace/dockertext2-master/mariadb/mariadb_home" to rootfs at 
"/var/lib/docker/overlay2/82bd739b99f78bb3f221929b66b3cc6706efb465f89d6c07ae04a9d0cab6cba1/merged/var/lib/mysql" caused: not a directory: unknown: Are you trying to mount a directory onto a file (or vice-versa)? Check if the specified host path exists and is the expected type
```







mariadb_home을 폴더가 아닌 파일로 생성해서 발생했음



