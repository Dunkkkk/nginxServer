# Universal Link를 지원하기 위한 Nginx 웹 서버

이 프로젝트는 URL 클릭 시, 앱이 설치되어 있으면 앱으로 진입되고, 앱이 설치되어 있지 않으면 App Store로 리디렉션되는 기능을 제공하기 위해 만들어졌습니다.

## 기술 스택

- Universal Link: Deep Link의 한 종류인 Universal Link를 사용하였습니다.
- Nginx: 웹 서버로 Nginx를 사용하였습니다. 설정은 `fodinginx.conf` 파일을 참고하세요.
- HTTPS: Universal Link를 사용하기 위해 HTTPS를 사용하였습니다. Let's Encrypt로 무료 SSL 인증서를 발급받아 사용하였으며, 3개월마다 갱신이 필요합니다.

## 동작 방식

1. Port 80(HTTP)로 들어온 요청은 Port 443(HTTPS)로 리다이렉션됩니다.
2. 앱이 설치되어 있지 않은 경우, Nginx 서버를 통해 App Store로 리디렉션됩니다.

## 기타 정보

- 탄력적 고정 IP: 15.164.150.30
- 도메인: www.formationdirector.com
- SSL 인증서 경로: /etc/letsencrypt/live/www.formationdirector.com/fullchain.pem
- SSL 인증서 키 경로: /etc/letsencrypt/live/www.formationdirector.com/privkey.pem
- Nginx 설정 파일 `fodinginx.conf` 경로: /etc/nginx/sites-enabled (심볼릭 링크)
- Apple App Site Association (AASA) 파일 경로: /var/www/html/.well-known
- `apple-app-site-association` 파일을 Apple CDN 서버에 등록된 상태
