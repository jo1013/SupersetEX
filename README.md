# SupersetEX


# 오픈소스 시각화 툴 이다.  python으로 제작됌




## 아래의 명령어를 입력시에  superset, postgres, mysql, pyspark container 실행

```
$ docker-compose -f docker-compose-non-dev.yml up
```



## GCP 연결방법

1. gcp  iam 및 관리자(i am admin)에 들어가서  서비스 계정  아이디 생성 후 키생성 (bigquery 뷰어 정도면됌 수정기능X )
2.  superset 웹 에서 데이터베이스 생성 SQLALCHEMY URI에 bigquery://[BigQueryID값] 입력



ADVANCED탭에서 Security
SECURE EXTRA

{
"credentials_info": 

key 추가할 때  json으로 뽑은 값(보안 조심) 
}

## 기본  super-set 이미지에  bigquery load 엔진 필요



```
$ docker ps  # 여기서 superset 이미지 로들어간다.
$ docker exec -it [container id] bash
$ docker push [continaer name or id] [image][tag]
$ pip install pybigquery 
```

* 설치 후 꼭 커밋하고 다시 켜준다 . flask api 기반으로 이루어졌기 때문에 웹이 동작중에 설치하면 적용되지않는다.


