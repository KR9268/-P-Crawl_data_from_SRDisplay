# Crawl_HS_with_SR

## 개요
- SAP에 있는 SR의 데이터를 활용하여 모든 자재의 HSCODE 등 여러 정보를 중복없이 오름차순으로 정리해주는 툴
- 확인가능한 값 : Sales Org, Plant(Code,Name), POL, POD, HSCODE, Description
  - 2024.07.26 요청받아 항목추가(합산된 포장수량, 지정된 형식의 자재명/자재코드 요약본)
  - 2024.09.19 이집트 대응을 위한 항목추가(전체 포장수량 + 자재명/자재코드 전체요약본 제공)
    ```
    # 예시
    12 Packages of
    Airconditioner
    (Air-Con-material-code)
    Oven
    (Ov-en-material-code)
    ```

## 필수사항
- SAPGUI : SAP Scripting 활용
- SAP권한 : ZLED50110_D
- 아래의 SAP제어용 공통패키지 사용
  - [https://github.com/KR9268/NERPpkb](https://github.com/KR9268/NERPpkb)

## 사용법
- SAP 로그인 후 첫번째창 코드 실행

(1) 단 건 확인
- 두번째 박스 sr_no 변수에 SR번호를 입력하고 실행

(2) 여러 건 확인
- 세번째 박스 sr_no 변수의 '''와 '''사이에 모든 SR번호 입력 (\n, 즉 엔터를 기준으로 구분한다)
- 입력내용 이상없으면 실행
- 엑셀로 저장하고 싶은 경우, 네번째 박스 실행, 지정된 파일명+오늘날짜를 기준으로 다운로드 함

(3) 엑셀로 저장
- (1)이나 (2)에서 확인한 내용을 엑셀파일로 저장 


## 기능
- crawl_hscode_with_sr(session, sr_no) : SAP세션과 SR번호를 입력하면, 해당 메뉴에 들어가 크롤링 수행 후 중복제거된 값 리턴
