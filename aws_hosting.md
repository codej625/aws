# AWS 서버를 사용, 서버를 구성해보자.

<br /><br />

1. EC2 > Instance를 만든다.

```
1) 이름 설정

2) AMI 설정(Application and OS Image) -> linux가 저렴하다.

3) 인스턴스 유형을 설정한다.

4) 키 페어(로그인)을 설정한다. -> 미리 만들어놓은 키를 사용해도 상관없다.

5) 네트워크 설정 -> VPC, 서브넷, 보안 그룹, 인바운드 규칙을 설정한다.

6) 스토리지 구성

7) 고급 설정
```

<br />

2. 탄력적 IP > Instance를 연결 -> 고정(Public IP) 아이피를 만드는 것.

<br />

3. Route 53 > Domain을 등록

```
A 레코드를 해당 인스턴스의 Public IPv4 주소 or 로드 밸런서와 연결한다.
(A 레코드가 없으면, 도메인과 연결할 수 없다.)
```

<br />

4. Certificate Manager > 인증서를 요청

```
1) 퍼블릭 인증서를 요청한다.

2) 도메인 이름을 설정한다. -> *. 와 같은 와일드카드 형식도 가능.

3) 검증 방법을 선택한다. -> DNS or 이메일 검증

4) 인증서를 요청한다.

5)
- DNS 방식은 요청중인 인증서를 선택하고 "Route 53에서 레코드 생성"을 눌러 CNAME 레코드를 등록한다.
- 이메일 검증 방식은 이메일 인증을 받고 로드 밸런서에 곧바로 연결하면 된다.
```

<br />

5. 대상 그룹을 만든다.

```
1) 기본 구성 -> 인스턴스 선택

2) 대상 그룹 이름 설정

3) 프로토콜 : 포트를 설정 -> ex) Tomcat 사용시 Default Port 8080에 맞춰 HTTP 8080으로 설정한다.

4) IP 주소 유형 선택 -> IPv4를 선택한다.

5) VPC 선택 -> 대상 그룹에 포함할 인스턴스가 있는 VPC를 선택한다.

6) 프로토콜 버전 -> 일반적으로 HTTP1을 선택한다.

7) 상태검사 프로토콜은 HTTP, 검사 경로는 /이 기본이다.

8) 사용 가능한 인스턴스를 등록 -> ex) Tomcat 사용시 Default Port 8080에 맞춰 HTTP 8080으로 설정한다.
```

<br>

6. 로드 밸런서를 만든다.

```
1) Application Load Balancer를 선택

2) 로드 밸런서 이름을 설정

3) 체계는 인터넷 경계를 선택

4) IP 주소 유형은 일반적으로 IPv4를 선택

5) 네트워크 매핑 -> VPC를 선택하고 가용 영역의 서브넷을 선택
(가용 영역은 Instance의 가용 영역을 포함시켜야 한다.)

6) 보안 그룹을 선택

7) 리스터 및 라우팅 설정 -> 리스너는 80 Port, 443 Port용 두개를 만들고 대상 그룹을 선택한다.
```

<br/>

7. 접속 테스트

```
1) Instance에서 인바운드규칙 -> 접속할 IP를 설정해준다.

2) PuTTY와 같은 프로그램을 사용하여 Public IP, Port를 입력하고 접속한다.
(ubuntu를 선택했다면 이름을 "ubuntu"를 입력, 기본 포트번호 22, 키-페어를 사용했다면 키로 로그인한다.)

3) linux를 업데이트하고 JDK를 설치

4) Jar 파일을 실행시킨다. -> ex) java -jar {jarfile.jar} * 테스트 기준
```
