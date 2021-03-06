# Week4 Class
#### B976082 박순범

# What is Logspace and what is main difference with sRGB, why and when we use?


## **1. Difference of Log and sRGB**


 ### + **sRGB**
 
 sRGB (standard Red Green Blue)는 1996년에 미국의 컴퓨터 기업인 마이크로소프트와 HP가 협력하여 만든 모니터 및 프린터 표준 RGB 색 공간이다. IEC에 의해 IEC 61966-2-1:1999로 최종 표준화되었다. 색 공간 정보가 없는 이미지(특히 이미지 화소들이 색 채널 당 8비트 정수로 저장되는 경우)에 대한 기본 색 공간으로 종종 사용된다.


![2](https://cdna.artstation.com/p/media_assets/images/images/000/394/820/large/image02.jpg?1552184260)
 
 추가로, 기술 발전으로 sRGB는 UHD TV에서는 더 이상 쓰이지 않을 예정이며, 현재는 HDR 등을 고려해 DCI-P3을 목표로 제조되고 있다. 장기적으로는 BT.2020을 목표로 한다. sRGB는 사람이 눈으로 인식 가능한 색상의 33.3%밖에 재현할 수 없다. sRGB가 사용하는 EOTF에 의하여 구현 가능한 최대 밝기도 100 nits가 한계라는 점도 단점으로 꼽힌다.
 
 빛에 대한 인간의 눈 감도가 높은 강도보다 낮은 강도에서 훨씬 더 미세하다는 것이다. 특히 값을 표현하기 위해 8 비트를 사용하는 경우, 너무 많은 밝은 음영이 발생하고 어두운 음영이 충분하지 않게된다. 선형 공간은 컴퓨터 처리에 사용하기에 완벽한 의미가 있지만 우리 눈은 동일한 간격 사이에서 거의 동일한 양의 밝기 변화를 볼 것으로 기대하기 때문에 사람이 보는 데 적합하지 않다.

 예를 들어, 우리의 뇌는 32가 16보다 두 배 더 밝고, 48(32+16과 같음)이 32보다 두 배 더 밝을 것으로 예상한다.
이 문제를 해결하기 위해 대부분의 최신 모니터는 감마 곡선을 사용하여 색상을 비선형으로 만드는 표준 인 sRGB라는 변환을 적용한다. 곡선은 하단이 더 얕아서 더 어두운 값을 표시하고 상단이 더 가파르기 때문에 더 적은 라이트 값을 가질 수 있다.
 
 ![4](https://cdnb.artstation.com/p/media_assets/images/images/000/185/191/medium/comparison2.jpg?1516129275)

왼쪽사진이 선형 색공간(Linear color space), 오른쪽 사진이 sRGB
 
  ### + **Log**
 
 로그를 색상 공간 **보관함**으로 생각할 수 있다 (파일에 대해 zip 또는 rar가 수행하는 것과 동일한 방식). 선형 공간은 동일한 단계로 값을 증가시키는 반면 로그 색상 공간은 이미지의 흰색 및 검은 색 영역의 값을 압축하여 정보를 저장하는 데 필요한 공간을 최소화하기 때문이다. 

![1](https://cdnb.artstation.com/p/media_assets/images/images/000/394/821/medium/image01.jpg?1552184324)

![1](https://assets.rocketstock.com/uploads/2017/05/Log-Curve.jpg)

 위 이미지는 선형 컬러 커브와 로그 컬러 커브간의 차이첨을 보여주는 것이다. 커브 그래프의 좌하단이 Black과 Shadows를 나타내고, 커브 그래프의 우상단이 White와 Highlight를 나타낸다는 것을 알 수 있다. 보시다시피, 이미지의 더 어두운 부분이 Shadows를 보유하기 위해 위로 치솟아 있다. 커브의 꼭대기는 Highlight를 보유하기 위해 아래쪽으로 꺽여있다. 그래서, 컬러 커브의 양쪽에서 더 많은 데이터를 얻을 수 있다.
 
 ## **2. Why and when we use?**
 
 로그 색상 곡선을 사용하는 가장 큰 이유 는 카메라 센서 (또는 필름 네거티브)에서 가장 역동적 인 정보 범위를 유지하는 방법이다. 카메라가 보는 것을 로그로 인코딩 하여 이미지 노출 (스톱 단위로 측정)과 기록 된 이미지 간의 상관 관계가 더 넓은 범위에서 완전히 일정하다는 것을 의미한다. 인간의 눈이나 비디오 화면을 위해 특별히 캡처하는 대신 가능한 한 많은 데이터를 저장하기 때문에 표준 비디오 곡선보다 센서정보를 더 많이 사용한다. 이것은 포스트 프로덕션에서 작업 할 수있는 훨씬 더 많은 색상 데이터를 제공한다.
 
[![1](https://img.youtube.com/vi/_tbXsgefzag/0.jpg)](https://www.youtube.com/watch?v=_tbXsgefzag)
 유튜브 영상
 
 그렇기에 채색이 덜 된 상태에서 우리가 원하는 색상으로 다시 색을 입힐 수 있고, 그렇게 되면 연출하고자 하는 영상의 느낌을 시청자들에게 전달할 수 있기 때문이다. 실내 촬영의 경우, 굳이 로그 촬영을 할 필요가 없다, 빛의 대비가 강한 낮 촬영의 경우 로그 촬영은 거의 필수다.
 
 
참고:

https://ko.wikipedia.org/wiki/SRGB

https://www.rocketstock.com/blog/tips-for-log-color-space-compositing/

https://m.blog.naver.com/passion8945/221516552960

https://tiberius-viris.artstation.com/blog/3ZBO/color-space-management-srgb-linear-and-log

https://aw2sum.tistory.com/entry/QA-Time-2-%EB%A1%9C%EA%B7%B8LOG-%EC%B4%AC%EC%98%81%EC%9D%B4-%EB%AD%94%EA%B0%80%EC%9A%94-2

https://www.youtube.com/watch?v=_tbXsgefzag
