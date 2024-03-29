# acc_contents_selenium


## Introduction
월말이 되면 청구를 하기 위해 결제한 내용을 하나하나 입력하는데 **생각보다 많은 시간이 소요됩니다.**  
이 시간을 조금이라도 줄일 방법이 없을까하여, 고민을 하게 되었고 간단하게 구현을 해보았습니다.     

엑셀 파일에 따로 입력정보(날짜, 금액 등)들을 입력해두면 selenium을 활용해서 적요를 편하게 채울 수 있게 만들었습니다.   
코드는 간단+무식하게 짜여있기 때문에 조금만 이해해보시면 응용을 많이 할 수 있을 것 같습니다.   
추후에는(언젠가는) 폴더 내에 있는 증빙사진까지 업로드하여 결제로 바로 갈 수 있게끔 하는 것도 고려해보겠습니다.  

누군가 나중에 OCR을 활용하여 청구하는 날이 온다면 더 awesome 할 것 같습니다👋   




## Setting  
실행을 하기 위해서는 사전 작업이 필요합니다. 

#### 1. 아래 library들을 설치합니다. 
이전 버전은 본인 chrome 버전과 일치하는 chromedrive.exe 를 설치하였으나, 자동으로 설치를 해주는 library를 활용합니다. 

```sh
pip install selenium
pip install chromedriver-autoinstaller
```
  
#### 2. 그룹웨어 접속하여 메인 페이지 중간 ~ 아래 부근에 결재양식이 있습니다.   
톱니바퀴 버튼을 클릭해서 **휴가신청서, 지출결의서(개인경비)**를 추가해주세요.  
사진처럼 세팅을 하면 됩니다.  


![example](./templete.JPG)



  
#### 3. 경로 내에 sample_data.xlsx 파일에 본인 적요 내용을 채워넣습니다.   
경로를 바꾸시려면 pd.read_xlsx 부분에서 수정하시면 됩니다.  
**각 column의 설명은 다음과 같습니다.(sample_data.xlsx를 참고해주세요.)**  


date | type | howmany | amount | etc
---- | ---- | ---- | ---- | ----
20200802 | 중식 | 2인 | 19000 | 
20200803 | 석식 | 3인 | 27000 | 
  

- date : 적요일을 뜻합니다.  
- type : 적요를 실제로 검색하는데 활용하며, 적요 내용에도 입력이 됩니다.  
- howmany : 식사한 인원 수를 '?인' 으로 표기합니다.  
- amount : 금액을 뜻합니다.  
- etc : 적요 내용에 추가 기술하는 내용을 표기합니다.  



## Run  
경로로 들어가 다음처럼 실행합니다.   

```sh
python acc_selenium.py
```
아이디와 비밀번호를 입력하면 실행이 됩니다.   
결제상신 전 페이지까지 진행이 되며, 입력된 내용이 맞는지 반드시 확인해주세요.  


## Author
- Ho Young Jeong @hotorch
- Author Email : ghdud1519@agilesoda.ai
