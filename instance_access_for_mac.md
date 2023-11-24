# 맥에서 터미널을 사용해서 인스턴스에 접근해보자!

<br/>

1. puTTY 설치
```
brew install putty
```

<br/>

2. .ppk 확장자라면 .pem으로 변환한다.
```
puttygen {keyname}.ppk -O private-openssh -o {keyname}.pem
```

<br/>

3. key파일에 읽기 권한만 주어 안전하게 보관한다.
```
chmod 400 {keyname}.pem
```

<br/>

4. 인스턴스에 접속해보자
```
ssh -i /{path}/{keyname}.pem -p {port} {hostname}@{ip}
```
