# CCCloudPlatform
유저가 k8s 클러스터로 인프라를 제공받고자 할 때 쓰이는 컴포넌트입니다.

기본 구성은 마스터 노드 vm 1개, 슬레이브 노드 vm 2개를 제공합니다.
최종적으로는 사용자가 웹 서비스를 k8s로 배포한다는 옵션을 선택하고, 어떤 프레임워크를 사용했는지와 소스코드를 넣으면 k8s로 배포되어서 사용자는 배포에 신경쓰지 않아도 되는 PaaS 형태의 k8s 제공을 목표로 하고 있습니다.


## 1기 스터디 결과
아직은 오픈스택의 vm을 쓰지 못하는 상황이어서 NCP의 VM을 통해서 k8s를 구축하였습니다.
1. 호스트 파일 작성
![image](https://github.com/user-attachments/assets/f997e010-7a62-4ae1-835b-add778a97262)


 

2. 마스터 노드 셋업 플레이북 실행
![image](https://github.com/user-attachments/assets/46ece8f1-a691-4829-8dca-cd75e131ef1c)



 

실행 완료
![image](https://github.com/user-attachments/assets/66705954-cfc2-4f08-b3db-456304c0623f)



 

3. 워커 노드 셋업 플레이북 실행
![image](https://github.com/user-attachments/assets/5bb07497-f2de-4c83-bdf0-ef705a33e998)



 

4. 마스터노드에서 node 확인
![image](https://github.com/user-attachments/assets/03bc7a71-1bff-4634-be15-8bda985c6b62)



 

5. vm 추가 후, 워커 노드 셋업 플레이북 재실행
![image](https://github.com/user-attachments/assets/e2968e35-3f97-488b-a9db-86f4a8184eb8)



 

전에 붙인 노드는 건너뛰고 추가된 노드만 task진행됨
![image](https://github.com/user-attachments/assets/adf993e9-20c2-4f48-bc7c-929faf00e29e)



 

6. 추가된 노드 확인
![image](https://github.com/user-attachments/assets/c8aba61c-5633-4e98-ab95-9fe23ab04566)





---

## 2기 스터디 목표
1. 슬레이브 노드의 인바운드 트래픽이 증가하여서 노드의 리소스가 부족해지면 모니터링 서버가 ansible 서버로 api를 호출하고, ansible 서버는 노드를 추가로 구성하여서 마스터 노드에 조인시키는 것을 목표로 합니다.
