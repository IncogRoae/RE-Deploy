## Deploy Web Server

빌드된 Web Server를 배포합니다.

### 구성

아래와 같은 playbook으로 구성되어 있습니다.

- backup: 현재 배포되어있는 서버의 아티팩트를 백업합니다.
- cleanup-blue: 배포 완료 후 Blue 환경을 정리합니다.
- deploy-green: 새로운 버전의 아티팩트를 가져와 Green 서버를 배포합니다.
- rollback: 이슈 발생시 백업했던 아티팩트로 재배포하고 다시 Blue 환경으로 트래픽을 전환합니다.
- switch-to-blue: 로드밸런서의 트래픽을 Blue로 전환합니다.
- switch-to-green: 로드밸런서의 트래픽을 Green으로 전환합니다.

### Templates

- nginx-blue: 트래픽을 Blue로 전환하기 위한 nginx proxy 설정 파일입니다.
- nginx-green: 트래픽을 Green으로 전환하기 위한 nginx proxy 설정 파일입니다.

### Inventory
새로운 버전을 배포할때 마다 webserver1, webserver2를 번갈아 가며 Blue/Green으로 사용합니다.
- webserver1
- webserver2
- loadbalancer
