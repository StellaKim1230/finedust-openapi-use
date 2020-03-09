# 미세먼지 open api 조사

## 목적 : 측정소 목록 조회해온 api response 중 측정소명으로 대기오염정보조회 서비스 api를 호출한다.

### 사용되는 api

1. 측정소정보 조회 서비스 - 측정소 목록

- endpoint: `http://openapi.airkorea.or.kr/openapi/services/rest/MsrstnInfoInqireSvc/getMsrstnList`

- parameter:
```javascript
ServiceKey : L4QqdFjRlZri5UPZT0rXpky4Se9XLoYtaRS%2FaHiThbSLZAI62Qmr8NXWT1yWEcdaBUNEs4OWe3G06c0gCxiz5w%3D%3D
_returnType: json
numOfRows: 1
pageNo: 1
addr: 서울
stationName: 측정소명 (서울 전체 가져오려면 사용 안함)
```

- response:
```javascript
{
  ...
    "list": [
      {
        "_returnType": "json",
        "addr": "서울 중구 덕수궁길 15시청서소문별관 3동",
        "districtNum": "",
        "dmX": "37.564639",
        "dmY": "126.975961",
        "item": "SO2, CO, O3, NO2, PM10, PM2.5",
        "mangName": "도시대기",
        "map": "http://www.airkorea.or.kr/airkorea/station_map/111121.gif",
        "numOfRows": "10",
        "oper": "서울특별시보건환경연구원",
        "pageNo": "1",
        "photo": "http://www.airkorea.or.kr/airkorea/station_photo/NAMIS/station_images/111121/INSIDE_OTHER_1.JPG",
        "resultCode": "",
        "resultMsg": "",
        "rnum": 0,
        "serviceKey": "",
        "sggName": "",
        "sidoName": "",
        "stationCode": "",
        "stationName": "중구",
        "tm": 0,
        "tmX": "",
        "tmY": "",
        "totalCount": "",
        "umdName": "",
        "ver": "",
        "vrml": "http://www.airkorea.or.kr/airkorea/vrml/111121.swf",
        "year": "1995"
      }
    ],
  ...
}
```


2. 대기오염정보 조회 서비스 - 측정소별 실시간 측정정보 조회