# 미세먼지 open api 조사

## 목적 : 측정소 목록 조회해온 api response 중 측정소명으로 대기오염정보조회 서비스 api를 호출한다.

### 사용되는 api

1. 측정소정보 조회 서비스 - 측정소 목록

- endpoint: `http://openapi.airkorea.or.kr/openapi/services/rest/MsrstnInfoInqireSvc/getMsrstnList`

- parameter:
```javascript
'ServiceKey' : 'L4QqdFjRlZri5UPZT0rXpky4Se9XLoYtaRS%2FaHiThbSLZAI62Qmr8NXWT1yWEcdaBUNEs4OWe3G06c0gCxiz5w%3D%3D'
'_returnType': 'json'
'numOfRows': 1 // 한 페이지 결과 수
'pageNo': 1 // 페이지 번호
'addr': 서울 // 주소
'stationName': '측정소명' (서울 전체 가져오려면 사용 안함)
```

- response:
```javascript
{
  ...
    "list": [
      {
        "_returnType": "json",
        "addr": "서울 중구 덕수궁길 15시청서소문별관 3동", // 측정소 주소
        "districtNum": "",
        "dmX": "37.564639", // 위도
        "dmY": "126.975961", // 경도
        "item": "SO2, CO, O3, NO2, PM10, PM2.5", // 측정항목
        "mangName": "도시대기", // 측정망
        "map": "http://www.airkorea.or.kr/airkorea/station_map/111121.gif",
        "numOfRows": "10",
        "oper": "서울특별시보건환경연구원", // 관리기관명
        "pageNo": "1",
        "photo": "http://www.airkorea.or.kr/airkorea/station_photo/NAMIS/station_images/111121/INSIDE_OTHER_1.JPG", // 측정소 이미지
        "resultCode": "",
        "resultMsg": "",
        "rnum": 0,
        "serviceKey": "",
        "sggName": "",
        "sidoName": "",
        "stationCode": "",
        "stationName": "중구", // 측정소명
        "tm": 0,
        "tmX": "",
        "tmY": "",
        "totalCount": "",
        "umdName": "",
        "ver": "",
        "vrml": "http://www.airkorea.or.kr/airkorea/vrml/111121.swf", // 측정소 지도 이미지
        "year": "1995" // 설치년도
      }
    ],
  ...
}
```


2. 대기오염정보 조회 서비스 - 측정소별 실시간 측정정보 조회
측정소 목록에서 검색된 `stationName` 측정소명으로 파라미터에 추가한다.

- endpoint: `http://openapi.airkorea.or.kr/openapi/services/rest/ArpltnInforInqireSvc/getMsrstnAcctoRltmMesureDnsty`

- parameter:
```javascript
'ServiceKey' : 'L4QqdFjRlZri5UPZT0rXpky4Se9XLoYtaRS%2FaHiThbSLZAI62Qmr8NXWT1yWEcdaBUNEs4OWe3G06c0gCxiz5w%3D%3D'
'_returnType': 'json'
'numOfRows': 1 // 한 페이지 결과 수
'pageNo': 1 // 페이지 변호
'stationName': '중구' // 측정소명
'dataTerm': 'DAILY' // 요청 데이터 기간 (DAILY: 1일, MONTH: 1개월, 3MONTH: 3개월)
```

- response:
```javascript
{
  ...
    "list": [
      {
        "_returnType":"json",
        "coGrade":"1", // 일산화탄소 지수
        "coValue":"0.6", // 일산화탄소 농도
        "dataTerm":"",
        "dataTime":"2020-03-10 10:00", // 측정일
        "khaiGrade":"3", // 통합대기환경지수
        "khaiValue":"147", // 통합대기환경수치
        "mangName":"도시대기", // 측정망 정보
        "no2Grade":"1", // 이산화질소 지수
        "no2Value":"0.023", // 이산화질소 농도
        "numOfRows":"10",
        "o3Grade":"1", // 오존 지수
        "o3Value":"0.020", // 오존농도
        "pageNo":"1",
        "pm10Grade":"2", // 미세먼지(pm10) 24시간 등급
        "pm10Grade1h":"2", // 미세먼지(pm10) 1시간 등급
        "pm10Value":"42", // 미세먼지(pm10) 농도
        "pm10Value24":"60", // 미세먼지(pm10) 농도 24시간 예측이동농도
        "pm25Grade":"3", // 미세먼지(pm2.5) 24시간 등급
        "pm25Grade1h":"3", // 미세먼지 (pm2.5)  1시간 등급
        "pm25Value":"37", // 미세먼지(pm2.5) 농도
        "pm25Value24":"48", // 미세먼지(pm2.5) 농도 24시간 예측이동농도
        "resultCode":"",
        "resultMsg":"",
        "rnum":0,
        "serviceKey":"",
        "sidoName":"",
        "so2Grade":"1", // 아황산가스 지수
        "so2Value":"0.003", // 아황산가스 농도
        "stationCode":"",
        "stationName":"",
        "totalCount":"",
        "ver":""
      }
    ],
  ...
}
```