## 프로젝트 이름

- 누가 멜론에게 선글라스를 씌웠을까?
<br>

## 프로젝트 개요

- 현재 음원 사이트에 씌워진 선글라스, 즉 어뷰징이 어떤 형태로 그 안에 존재하는지, 어떤 특징을 가지고 있는지 분석하고 시각화합니다.
<br>

## Data 설명
### 차트 데이터
| 컬럼명 | 설명 |
|------|---|
|<b>year</b>|차트에 들어간 연도|
|<b>month</b>|차트에 들어간 월|
|<b>week</b>|차트에 들어간 주간|
|<b>rank</b>|주간 차트 순위|

### 음원 데이터
| 컬럼명 | 설명 |
|------|---|
|<b>song_id</b>|음원 고유 ID|
|<b>title</b>|음원 제목|
|<b>like</b>|음원 좋아요 수|
|<b>reply</b>|음원 댓글 수|
|<b>genre</b>|음원 장르|

### 가수 데이터
| 컬럼명 | 설명 |
|------|---|
|<b>artist_id</b>|가수 고유 ID|
|<b>artist</b>|가수 이름|
|<b>fan</b>|가수의 팬 맺은 수|

### 앨범 데이터
| 컬럼명 | 설명 |
|------|---|
|<b>album_id</b>|앨범 고유 아이디|
|<b>album</b>|앨범명|
|<b>album_release_date</b>|앨범 발매일자|
|<b>album_reply</b>|앨범 댓글 수|
|<b>album_score</b>|앨범 평점|
|<b>album_score_count</b>|앨범 평점 매긴 사람 수|
|<b>album_like</b>|앨범 좋아요 수|
<br>

## 새로 가공한 컬럼

1. 추후 데이터 활용이 어려운 리스트형의 전처리  
    <b>'main_genre'</b>  
    - 음원의 'genre'가 두 개 이상일 때 파이가 더 큰 장르를 'main_genre'로 선택  
    - list -> str

    <b>'fan_max'</b>  
    - 음원에 참여한 가수가 두 팀 이상일 때 팬 맺은 수가 더 많은 가수의 팬 맺은 수를 선택
    - list -> int
2. 장르 One-Hot Encoding
    - 장르가 리스트형일 때 count하기 어려워 One-Hot Encoding 컬럼 생성
3. Min-Max Scale
    - range가 다른 feature들을 0과 1사이의 값으로 처리하기 위해 가공한 컬럼들  
    : 'fan_per' , 'album_reply_per', 'reply_per', 'like_per', 'album_score_per', 'album_score_count_per', 'user_per_per', 'album_like_per'
    - 'album_like_like_per' : 앨범 좋아요를 음원 좋아요 수로 나눈 값을 Min-Max Scale 처리한 값

## 폴더 설명

1. crawling
    - 음원 사이트 웹 크롤링 관련 코드
    - Main File :  [191211_song_album_artist_crawling_git.ipynb](https://github.com/blackmelon5/black_melon/blob/master/1.%20Crawling/191211_song_album_artist_crawling_git.ipynb)
2. preprocessing
    - 데이터 전처리 관련 코드
    - Main File :  [191209_preprocessing_genre_fan.ipynb](https://github.com/blackmelon5/black_melon/blob/master/2.%20Preprocessing/191209_preprocessing_genre_fan.ipynb)
3. wordcloud
    - 음원 제목으로 구현한 워드클라우드 관련 코드
    - Main File :  [계절별.ipynb](https://github.com/blackmelon5/black_melon/blob/master/3.%20Wordcloud/계절별.ipynb)
4. genre visualization
    - 장르 데이터로 장르별 시각화를 구현한 코드
5. abusing visualization
    - 차트에서 발견할 수 있는 어뷰징 음원의 특징을 시각화한 코드
6. clustering
    - 시각화한 특징을 바탕으로 가수 군집을 클러스터링한 코드
7. make new chart
    - 전체 분석을 바탕으로 어뷰징의 영향을 최소화한 새로운 차트 구현 코드
8. EDA
    - 그 외에 데이터로 시도한 가벼운 분석들

## Data 드라이브

- [https://drive.google.com/drive/folders/19dZ-3XPSDcx1kwc7pf5b_QSrDXUMumDj?usp=sharing](https://drive.google.com/drive/folders/19dZ-3XPSDcx1kwc7pf5b_QSrDXUMumDj?usp=sharing)
