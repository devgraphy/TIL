용어

* statefulset : stateful app을 관리하는데 사용되는 workload API 중 하나
  * 파드 집합의 배포 및 확장을 관리하고
  * 이러한 파드의 순서와 고유성을 보장한다.
  * Deployment처럼 동일한 컨테이너 스펙에 기반해서 파드를 관리한다.
  * 반면에 Deployment와 달리
  * workload: 
    * 파드 집합 내에서 사용자를 대신해서 파드 집합을 관리하는 애플리케이션
    * 쿠버네티스 빌트인 워크로드 리소스
      * Deployment & ReplicaSet
      * StatefulSet
      * DaemonSet
      * Job & CronJob
  * pod