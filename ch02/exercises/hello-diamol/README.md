
0. Build and push the arch images

1. Enable experimental in `~/.docker/config.json`:

```
{
  "experimental": "enabled"
}
```

2. Create the manifest list (multi-arch name followed by individual image names):

```
docker manifest create `
 diamol/ch02-hello-diamol:1.0 `
 diamol/ch02-hello-diamol:windows-x64 `
 diamol/ch02-hello-diamol:linux-x64 `
 diamol/ch02-hello-diamol:linux-amd64
```

3. Inspect & confirm archs:

```
docker manifest inspect diamol/ch02-hello-diamol:1.0
```

4. Push

```
docker manifest push diamol/ch02-hello-diamol:1.0
```

Quiz

docker run -d --name my-web diamol/ch02-hello-diamol-web

웹 사이트 컨테이너를 실행하고 index.html 파일을 교체해 웹 페이지의 내용 을 수정하는 것이다. 컨테이너도 자신만의 파일 시스템을 갖는다고 설명했었다. 이 웹 페이지 파일 역시 컨테이너의 파 일 시스템 안에 담겨 있다.
다음 힌트를 참고하기 바란다.
• docker container 명령을 사용하면 컨테이너를 대상으로 할 수 있는 일의 목록을 볼 수 있다.
• 모든 docker 명령에 --heLp 플래그를 추가하면 해당 명령의 도움말을 볼 수 있다.
• 도커 이미지 diamoL/cho2-heLLo-diamol-web 안에서 웹 페이지 파일이 위치한 경로는 /ust/local/apache2/htd ocs다(윈도의 경우 C:lusrllocallapache2 (htdocs).

```
docker run -d --name my-web diamol/ch02-hello-diamol-web
echo "<html><body><h1>새로운 웹 페이지</h1></body></html>" > index.html
docker cp index.html my-web:/usr/local/apache2/htdocs/index.html
```



