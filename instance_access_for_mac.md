# 맥에서 인스턴스 접속(서버) 방법

<br /><br />

* 주의
---

```
가장 중요한 건,
인바운드 규칙에서 사용하는 IP를 허용한 상태에서 진행해야 한다.
```

<br /><br /><br />

* 순서
---

1. puTTY 설치

```
brew install putty
```

<br/>

2. .ppk 확장자라면 .pem으로 변환한다.(선택)

```
puttygen {keyname}.ppk -O private-openssh -o {keyname}.pem
```

<br/>

3. key파일에 읽기 권한만 주어 안전하게 보관한다.

```
chmod 400 {keyname}.pem
```

<br/>

4. 인스턴스 접속
```
Instance에 Port와 Hostname, IP를 확인한다.

ssh -i /{path}/{keyname}.pem -p {port} {hostname}@{ip}
```
