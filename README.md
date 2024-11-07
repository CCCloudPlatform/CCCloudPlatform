# CCCloudPlatform
유저가 k8s 클러스터로 인프라를 제공받고자 할 때 쓰이는 컴포넌트입니다.

기본 구성은 마스터 노드 vm 1개, 슬레이브 노드 vm 2개를 제공합니다.
최종적으로는 사용자가 웹 서비스를 k8s로 배포한다는 옵션을 선택하고, 어떤 프레임워크를 사용했는지와 소스코드를 넣으면 k8s로 배포되어서 사용자는 배포에 신경쓰지 않아도 되는 PaaS 형태의 k8s 제공을 목표로 하고 있습니다.


## 1기 스터디 결과
아직은 오픈스택의 vm을 쓰지 못하는 상황이어서 NCP의 VM을 통해서 k8s를 구축하였습니다.
1. 호스트 파일 작성
![image](https://github.com/user-attachments/assets/f997e010-7a62-4ae1-835b-add778a97262)


 

2. 마스터 노드 셋업 플레이북 실행
![image](https://github.com/user-attachments/assets/38240a58-5a44-430a-95e3-4b19dad5934e)


 

실행 완료
![image](https://github.com/user-attachments/assets/7d2833fa-294d-4aac-b065-d08a93ac1b74)


 

3. 워커 노드 셋업 플레이북 실행
![image](https://github.com/user-attachments/assets/04230c19-06c4-48d5-a96b-be4600138596)


 

4. 마스터노드에서 node 확인
![image](https://github.com/user-attachments/assets/3629ca3d-39ce-44cb-848f-d35ec66fc9f3)


 

5. vm 추가 후, 워커 노드 셋업 플레이북 재실행
![image](https://github.com/user-attachments/assets/22a07943-f986-4077-b10f-af8eac3f50ee)


 

전에 붙인 노드는 건너뛰고 추가된 노드만 task진행됨
![image](https://github.com/user-attachments/assets/575e812e-f765-4021-879b-ab413c9fb55f)


 

6. 추가된 노드 확인
![image](https://github.com/user-attachments/assets/4e149120-47a7-4e38-80f0-db89cc8a1390)




---

## 2기 스터디 목표
1. 슬레이브 노드의 인바운드 트래픽이 증가하여서 노드의 리소스가 부족해지면 모니터링 서버가 ansible 서버로 api를 호출하고, ansible 서버는 노드를 추가로 구성하여서 마스터 노드에 조인시키는 것을 목표로 합니다.
