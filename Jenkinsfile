pipeline {
    agent any

    stages {
        stage('코드 가져오기 (Checkout)') {
            steps {
                checkout scm
            }
        }
        
        stage('패키지 설치 (Composer Install)') {
            steps {
                // 라라벨 구동에 필요한 외부 라이브러리 설치
                sh 'composer install --no-interaction --prefer-dist --optimize-autoloader'
            }
        }
        
        stage('환경 설정 및 키 생성') {
            steps {
                // 테스트를 위한 .env 파일 복사 및 암호화 키 생성
                sh 'cp .env.example .env'
                sh 'php artisan key:generate'
            }
        }
        
        // 추후에 아래에 배포(Deploy) 단계를 추가할 수 있습니다.
    }
}