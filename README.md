# 한국어 책 리뷰 텍스트를 이용한 아이템 기반 협업 필터링

## 배경

빅데이터 시대를 맞아 적지 않은 수의 이커머스 업체가 고객 맞춤 추천 서비스를 하고 있다. 개인화 마케팅이 뜨거운 화두로 떠오른 가운데 그러한 추세를 협업 필터링이 뒷받침하고 있다. 또한 한국어 자연어 처리는 활발히 연구되고 있는 영역이며, 아직 무궁무진한 가능성을 갖고 있는 분야이다. 

전자상으로 거래되는 수많은 상품 중에서도 서적은 콘텐츠 특성상 하나를 사서 소비하는데 적지 않은 심력과 시간이 소모된다. 그런 만큼 많은 수의 독서가들은 **자신에게 맞는** 책을 사서 조금이나마 더 행복한 독서 생활을 보내기를 바란다. 다독가의 충고 중 하나가 '자신에게 맞지 않는다고 생각되는 책은 과감하게 덮어라.'일 정도이다. 하지만 자신에게 맞지 않는다고 판단한 시점에서는 그 책을 구매한 후일 것이다. 하지만 정작 서적 분야에서는 비슷한 책 추천을 비롯한 개인화 서비스가 많이 활성화돼 있지 않다. 각 서점마다 유사 책 추천이란 시스템을 갖추고 있기는 하지만, 그것이 주요한 판촉 요소가 되지는 않는다. 이러한 상황에 아쉬움을 느껴 서적 분야, 한국어 분야에서 아이템 추천을 할 수 있는 방법론을 개발해 보려고 한다.

## 데이터

데이터로 [Yes24](http://www.yes24.com/Main/default.aspx)의 리뷰 텍스트를 수집하여 사용했다. [일주일 간 가장 많이 리뷰된 책](http://blog.yes24.com/BlogMain/Review/ManyReviewGoods?c1=001)을 2020-10-07 기준으로 두 번째 카테고리를 순회하며 수집했다.

총 1,523권의 책과 26,483건의 리뷰가 수집되었다. 이중 추천에서는 의미없는, 한 권에만 리뷰를 달은 유저의 리뷰 7,429건을 삭제했다. 그 외에도 중복된 리뷰와 결측치가 있는 리뷰를 제외하여 총 16,780건, 4,100명 유저, 1,425권의 책이 남았다.

## 협업필터링

협업필터링은 널리 사용되고 있는 추천 알고리즘이다. 협업필터링은 다음과 같은 과정을 거쳐 이루어진다.

* 유저-아이템 행렬 구성

<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th>BookCode</th>
      <th>8.801748e+12</th>
      <th>8.809124e+12</th>
      <th>8.809255e+12</th>
      <th>8.809255e+12</th>
      <th>8.809264e+12</th>
      <th>8.809333e+12</th>
      <th>8.809417e+12</th>
      <th>8.809470e+12</th>
      <th>8.809475e+12</th>
      <th>8.809475e+12</th>
      <th>...</th>
      <th>9.791197e+12</th>
      <th>9.791197e+12</th>
      <th>9.791197e+12</th>
      <th>9.791197e+12</th>
      <th>9.791197e+12</th>
      <th>9.791197e+12</th>
      <th>9.791197e+12</th>
      <th>9.791197e+12</th>
      <th>9.791197e+12</th>
      <th>1.844674e+19</th>
    </tr>
    <tr>
      <th>Author</th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>'_'*</th>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>...</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
    </tr>
    <tr>
      <th>**01 22 2020  9:45PM**</th>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>...</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
    </tr>
    <tr>
      <th>**09  4 2018  1:15PM**</th>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>...</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
    </tr>
    <tr>
      <th>**09 12 2017 10:14AM**</th>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>...</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
    </tr>
    <tr>
      <th>**10 27 2017  4:24PM**</th>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>...</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
    </tr>
    <tr>
      <th>...</th>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
    </tr>
    <tr>
      <th>히또리도리돌</th>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>...</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
    </tr>
    <tr>
      <th>히야신스</th>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>...</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
    </tr>
    <tr>
      <th>히이이익</th>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>...</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
    </tr>
    <tr>
      <th>히키</th>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>...</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
    </tr>
    <tr>
      <th>힘찬발걸음</th>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>...</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>8.0</td>
    </tr>
  </tbody>
</table>

* 아이템 간 혹은 유저 간 유사도 행렬 구성: cos 유사도를 사용했다.

<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right">
      <th>BookCode</th>
      <th>8.801748e+12</th>
      <th>8.809124e+12</th>
      <th>8.809255e+12</th>
      <th>8.809255e+12</th>
      <th>8.809264e+12</th>
      <th>8.809333e+12</th>
      <th>8.809417e+12</th>
      <th>8.809470e+12</th>
      <th>8.809475e+12</th>
      <th>8.809475e+12</th>
      <th>...</th>
      <th>9.791197e+12</th>
      <th>9.791197e+12</th>
      <th>9.791197e+12</th>
      <th>9.791197e+12</th>
      <th>9.791197e+12</th>
      <th>9.791197e+12</th>
      <th>9.791197e+12</th>
      <th>9.791197e+12</th>
      <th>9.791197e+12</th>
      <th>1.844674e+19</th>
    </tr>
    <tr>
      <th>BookCode</th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>8.801748e+12</th>
      <td>1.0</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>...</td>
      <td>0.000000</td>
      <td>0.0</td>
      <td>0.000000</td>
      <td>0.0</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.0</td>
      <td>0.000000</td>
      <td>0.000000</td>
    </tr>
    <tr>
      <th>8.809124e+12</th>
      <td>0.0</td>
      <td>1.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>...</td>
      <td>0.000000</td>
      <td>0.0</td>
      <td>0.000000</td>
      <td>0.0</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.0</td>
      <td>0.000000</td>
      <td>0.070646</td>
    </tr>
    <tr>
      <th>8.809255e+12</th>
      <td>0.0</td>
      <td>0.000000</td>
      <td>1.000000</td>
      <td>0.728219</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>...</td>
      <td>0.201619</td>
      <td>0.0</td>
      <td>0.000000</td>
      <td>0.0</td>
      <td>0.258199</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.0</td>
      <td>0.000000</td>
      <td>0.000000</td>
    </tr>
    <tr>
      <th>8.809255e+12</th>
      <td>0.0</td>
      <td>0.000000</td>
      <td>0.728219</td>
      <td>1.000000</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>...</td>
      <td>0.000000</td>
      <td>0.0</td>
      <td>0.000000</td>
      <td>0.0</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.0</td>
      <td>0.000000</td>
      <td>0.000000</td>
    </tr>
    <tr>
      <th>8.809264e+12</th>
      <td>0.0</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>1.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>...</td>
      <td>0.000000</td>
      <td>0.0</td>
      <td>0.000000</td>
      <td>0.0</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.0</td>
      <td>0.000000</td>
      <td>0.000000</td>
    </tr>
    <tr>
      <th>...</th>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
    </tr>
    <tr>
      <th>9.791197e+12</th>
      <td>0.0</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>...</td>
      <td>0.000000</td>
      <td>0.0</td>
      <td>0.000000</td>
      <td>0.0</td>
      <td>0.000000</td>
      <td>1.000000</td>
      <td>0.162586</td>
      <td>0.0</td>
      <td>0.000000</td>
      <td>0.000000</td>
    </tr>
    <tr>
      <th>9.791197e+12</th>
      <td>0.0</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>...</td>
      <td>0.000000</td>
      <td>0.0</td>
      <td>0.000000</td>
      <td>0.0</td>
      <td>0.000000</td>
      <td>0.162586</td>
      <td>1.000000</td>
      <td>0.0</td>
      <td>0.000000</td>
      <td>0.000000</td>
    </tr>
    <tr>
      <th>9.791197e+12</th>
      <td>0.0</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>...</td>
      <td>0.000000</td>
      <td>0.0</td>
      <td>0.000000</td>
      <td>0.0</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>1.0</td>
      <td>0.000000</td>
      <td>0.000000</td>
    </tr>
    <tr>
      <th>9.791197e+12</th>
      <td>0.0</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>...</td>
      <td>0.000000</td>
      <td>0.0</td>
      <td>0.000000</td>
      <td>0.0</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.0</td>
      <td>1.000000</td>
      <td>0.029128</td>
    </tr>
    <tr>
      <th>1.844674e+19</th>
      <td>0.0</td>
      <td>0.070646</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>...</td>
      <td>0.000000</td>
      <td>0.0</td>
      <td>0.014025</td>
      <td>0.0</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.0</td>
      <td>0.029128</td>
      <td>1.000000</td>
    </tr>
  </tbody>
</table>

* 유사도를 이용해 유저의 아이템에 대한 점수 예측

<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right">
      <th>BookCode</th>
      <th>8.801748e+12</th>
      <th>8.809124e+12</th>
      <th>8.809255e+12</th>
      <th>8.809255e+12</th>
      <th>8.809264e+12</th>
      <th>8.809333e+12</th>
      <th>8.809417e+12</th>
      <th>8.809470e+12</th>
      <th>8.809475e+12</th>
      <th>8.809475e+12</th>
      <th>...</th>
      <th>9.791197e+12</th>
      <th>9.791197e+12</th>
      <th>9.791197e+12</th>
      <th>9.791197e+12</th>
      <th>9.791197e+12</th>
      <th>9.791197e+12</th>
      <th>9.791197e+12</th>
      <th>9.791197e+12</th>
      <th>9.791197e+12</th>
      <th>1.844674e+19</th>
    </tr>
    <tr>
      <th>Author</th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>'_'*</th>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>...</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
    </tr>
    <tr>
      <th>**01 22 2020  9:45PM**</th>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>...</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
    </tr>
    <tr>
      <th>**09  4 2018  1:15PM**</th>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>10.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>...</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
    </tr>
    <tr>
      <th>**09 12 2017 10:14AM**</th>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>...</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
    </tr>
    <tr>
      <th>**10 27 2017  4:24PM**</th>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>...</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
    </tr>
    <tr>
      <th>...</th>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
    </tr>
    <tr>
      <th>히또리도리돌</th>
      <td>10.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>...</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>9.0</td>
      <td>10.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
    </tr>
    <tr>
      <th>히야신스</th>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>...</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
    </tr>
    <tr>
      <th>히이이익</th>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>10.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>10.0</td>
      <td>0.0</td>
      <td>10.0</td>
      <td>...</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
    </tr>
    <tr>
      <th>히키</th>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>...</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
    </tr>
    <tr>
      <th>힘찬발걸음</th>
      <td>0.0</td>
      <td>8.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>...</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
    </tr>
  </tbody>
</table>

* 예측된 점수를 평가

|  MAP(Mean Average Precision)  |   Recall  |  F-1 Score  |  F-0.5 Score  |
|:---:|:---:|:---:|:---:|
|0.797|0.729|0.762|0.783|

## 텍스트의 유사도 측정

텍스트를 벡터로 임베딩하는데는 여러 가지 방법이 있다. 본 연구에서는 그 중 두 가지 방법을 시험하였다.
* Word2Vec

Word2Vec은 

* TF-IDF

## 모델 평가 방법

* MAP(Mean Average Precision): 

Precision은 True라고 예측한 것 중, 실제로 True인 것의 비율이다. 그런데 추천 시스템에 Precision을 적용하면 다음과 같은 문제가 생긴다. **0(점수가 매겨지지 않음)을 True로 예측한 경우에는 실제로 True인 것으로 봐야하는가?** 우리는 유저가 이것을 실제로 좋아할지 싫어할지 알 수 없다. Ground Truth를 구하지 못하는 것이다. 따라서 Map은 "유저의 기존 경험에 신경쓰지 말고, 아이템의 추천 여부에 주목하자"는 생각으로 만들어졌다. MAP의 계산 공식은 다음과 같다.

`MAP = sum(추천된 아이템의 비율)/추천된 아이템 수`

실제로 유저가 긍정적으로 평가한 아이템을 긍정적으로 평가했는가보다 얼마나 유용한 추천 정보를 제공했는가에 더 초점을 맞추는 것이다.

출처: [Precision and recall in recommender systems, Kirill Bondarenko](https://bond-kirill-alexandrovich.medium.com/precision-and-recall-in-recommender-systems-and-some-metrics-stuff-ca2ad385c5f8)

* Recall
* F-1 Score
* F-0.5 Score: MAP에 더 가중치를 두어 추천에 더 큰 의미를 두는 점수도 계산하였다.

## 결과

결과는 k를 10, 20, 30으로 늘려가며 측정했다.

일반 평점 모델
|K|  MAP(Mean Average Precision)  |   Recall  |  F-1 Score  |  F-0.5 Score  |
|:---:|:---:|:---:|:---:|:---:|
|10|0.797|0.729|0.762|0.783|
|20|0.797|0.729|0.762|0.783|
|30|0.797|0.729|0.762|0.783|

일반 평점+TF-IDF 유사도 모델
|K|  MAP(Mean Average Precision)  |   Recall  |  F-1 Score  |  F-0.5 Score  |
|:---:|:---:|:---:|:---:|:---:|
|10|0.797|0.729|0.762|0.783|
|20|0.797|0.729|0.762|0.783|
|30|0.797|0.729|0.762|0.783|
