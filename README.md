# SupersetEX

## 개요
SupersetEX는 Apache-2.0 라이센스를 갖고 있는 오픈소스 시각화 툴입니다. Python으로 개발되었으며, 데이터 시각화 및 분석을 위한 강력한 인터페이스를 제공합니다.

## 실행 방법
아래 명령어를 실행하면 superset, postgres, mysql, pyspark 컨테이너가 함께 실행됩니다:

```bash
docker-compose -f docker-compose-non-dev.yml up
```

## GCP BigQuery 연결 방법

### 1. GCP 서비스 계정 설정
1. GCP IAM 및 관리자(IAM Admin)에 접속합니다
2. 서비스 계정 ID를 생성한 후 키를 생성합니다 (BigQuery 뷰어 권한 정도면 충분합니다)

### 2. Superset에서 BigQuery 연결 설정
1. Superset 웹 인터페이스에서 데이터베이스 생성 메뉴로 이동합니다
2. SQLALCHEMY URI에 `bigquery://[BigQueryID값]`을 입력합니다
3. ADVANCED 탭의 SECURE EXTRA 항목에 다음과 같이 입력합니다:
   ```json
   {
     "credentials_info": {
       // GCP 서비스 계정 키 JSON 내용을 여기에 붙여넣기 (보안 주의)
     }
   }
   ```

## BigQuery 연결 엔진 설치

기본 Superset 이미지에는 BigQuery 로드 엔진이 포함되어 있지 않아 별도 설치가 필요합니다:

```bash
# 저장소 복제
git clone github.com/jo1013.git

# 실행 중인 컨테이너 확인
docker ps

# Superset 컨테이너에 접속
docker exec -it [container id] bash

# BigQuery 연결 라이브러리 설치
pip install pybigquery

# 변경사항 저장
docker commit [container id] [image]:[tag]
```

> **중요**: 라이브러리 설치 후 반드시 컨테이너를 커밋하고 다시 시작해야 합니다. Superset은 Flask API 기반으로 동작하기 때문에 웹 서비스 실행 중에 설치한 라이브러리는 즉시 적용되지 않습니다.
