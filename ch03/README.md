docker container run --interactive --tty diamol/base
#### diamol/base 이미지로부터 대화식 컨테이너를 실행한다.
#### --tty 터미널 세션을 통해 컨테이너를 조작하겠다는 의미이다.

docker container ls --all
#### 상태와 상관없이 모든 컨테이너의 목록을 확인한다.

# 1. Nginx 컨테이너 실행
docker run --name web -d -p 80:80 nginx

# 2. 컨테이너 내부로 접속
docker exec -it web bash

# 3. 웹사이트 파일이 저장된 디렉터리 확인
cd /usr/share/nginx/html

# 4. 컨테이너 내부 파일 수정 (예: index.html 변경)
echo "<h1>Hello from Docker</h1>" > /usr/share/nginx/html/index.html

# 5. 변경 사항 확인
curl http://localhost
