# SupersetEX


# 오픈소스 시각화 툴 이다. python으로 제작됌


```
$ jupyter notebook --allow-root --ip=0.0.0.0 --port=8888
```

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


