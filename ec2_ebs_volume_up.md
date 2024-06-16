# EC2 ebs 볼륨 증설

<br /><br />

1. aws 접속

<br />

2. ec2 선택

<br />

3. 인스턴스 이동 => 해당 인스턴스 선택 => 밑에 탭에서 스토리지로 이동

<br />

4. 루트 디바이스 이름에서 디바이스 이름 체크

<br />

5. 볼륨 id 클릭 => 해당 볼륨 체크하고 작업 메뉴에서 볼륨 수정

<br/>

6. 디스크 정보 확인
```
df -h 
```

<br />

7. 저장장치 정보 확인
```
lsblk 
```

<br />

8. 파티션 확장
```
sudo growpart /dev/xvda 1

* 파티션 경로가 /dev/nvme0n1p1 인 경우 => sudo growpart /dev/nvme0n1 1
```

<br />

9. 파일 시스템 확장
```
sudo resize2fs /dev/xvda1

* 리눅스의 파일 시스템이 xfs일 경우 => resize2fs 명령어 대신 xfs_growfs 사용 sudo xfs_growfs /dev/xvda1
```
