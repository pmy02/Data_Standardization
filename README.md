# 상품정보 표준화
- 프로젝트 소개 : 상품정보 데이터 EDA & 표준화
- 프로젝트 기간 : 2023.02.06 ~ 2023.03.24

# 프로젝트 설명

![image](https://user-images.githubusercontent.com/62882579/230099319-877484fb-9b6f-4bd3-9ecb-6bd3a1b54c5e.png)

상품정보 표준화 프로젝트는 한 디지털 플랫폼 기업의 제안으로, 단기 업무협약을 계약하며 시작되었습니다. <br>
매장별로 판매되고 있는 비슷한 메뉴 정보를 표준화된 메뉴로 정리하는 작업을 수행하였습니다.

프로젝트를 진행하면서 2천만 개의 상품정보 EDA 및 표준화를 통해 약 1천 개의 레이블로 축소할 수 있었습니다. <br>
이러한 데이터는 추천 서비스에서 상품 추천을 위한 기반이 되며, 계약 상의 비밀유지 조항으로 인해 기업 정보와 데이터를 공개할 수 없습니다.

# 데이터 표준화

![image](https://user-images.githubusercontent.com/62882579/230099504-b06359ed-e883-4a77-b344-6997cbdeabad.png)

우선 기존 데이터에서 추천 대상 상품을 정의하였습니다. <br>
이를 위해 바코드의 체크디지트를 계산하여 유효성 검사를 실시하고 유통 상품을 제거하였습니다. <br>
또한, 음식점이 아닌 상점들의 데이터는 제외하였습니다. 이후 중복된 데이터를 제거하여 20만 개의 데이터를 보유하게 되었습니다. <br><br>

![image](https://user-images.githubusercontent.com/62882579/230099694-e6371357-d2c6-44a3-af57-9a4a6e3cb7ae.png) <br>
다음으로는 데이터 EDA 작업을 진행하였습니다. <br>
이를 통해 데이터 분포가 Long-Tail 형태를 띄어 레이블의 개수가 매우 많은 것을 확인하였습니다. <br><br>

![image](https://user-images.githubusercontent.com/62882579/230100111-132506d0-564c-40bd-82bb-f48877419f70.png)
![image](https://user-images.githubusercontent.com/62882579/230100166-7572d634-8d44-468a-9b7e-38ac7b30441d.png) <br>
Long-Tail의 원인을 파악하고자 KMeans Clustering 알고리즘을 적용하여 레이블을 그룹화하였습니다. <br>
그룹 간에는 유의미한 차이를 발견할 수 없었으며, 이는 불용어가 원인임을 알 수 있었습니다. <br><br>


데이터 내부의 노이즈를 제거하기 위해 결측치 처리와 특수 문자 제거, 그리고 영어를 한글로 번역하는 등의 전처리 과정을 거쳤습니다. <br>
이후, 텍스트 데이터를 분석하기 위해 품사 태깅을 수행하였습니다. 이를 위해 한국어 형태소 분석기 중에서 MeCab을 선택하였습니다.

그러나 MeCab은 한국어 외래어나 신조어에 대한 분석 성능이 떨어지는 단점이 있어, 아래와 같이 정확한 결과를 도출해내지 못했습니다. <br>
이를 보완하기 위해 추가적으로 사용자 정의 사전을 구축하는 방법을 선택하였습니다. <br>
![image](https://user-images.githubusercontent.com/62882579/230101580-19e9517e-6c91-42a1-9cfa-3ec66a98e066.png) <br><br>


사용자 정의 사전을 구축하여 표준화를 진행하였고, 이를 통해 높은 정확도의 품사 태깅을 달성하였습니다. <br>
![image](https://user-images.githubusercontent.com/62882579/230102400-74f9ed90-16b6-4a18-846d-a028adeb2424.png) <br><br>

또한, 구축한 사용자 정의 사전을 바탕으로 불용어를 제거하여 데이터 내부의 노이즈를 제거하여 최종적으로 95%의 표준화 정확도를 달성하였습니다. <br>
![image](https://user-images.githubusercontent.com/62882579/230101970-24b72172-5315-4d75-942f-8dd8856dad40.png)


![image](https://github.com/pmy02/Data_Standardization/assets/62882579/3e47b418-b525-40b3-85cc-19c745a2e2eb)
