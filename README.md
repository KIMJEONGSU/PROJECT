# 유입 채널별 고객 생애 가치를 통한 전환율 상승 프로젝트

<br>

### 프로젝트 기간
2023.08.14 ~ 2023.09.08

### 기술 스택
- SQL: 데이터 가공 및 추출
- Python: pandas와 plotly를 활용한 데이터 분석 및 시각화
- AWS RDS: 클라우드 데이터 베이스 생성
- Tableau: 계산식, 매개변수, 동작 등의 기능을 활용하여 대시보드 제작

### 데이터 소개
[Marketing Funnel by Olist](https://www.kaggle.com/datasets/olistbr/marketing-funnel-olist/versions/2?resource=download)
<details>
<summary>olist_closed_deals_dataset</summary>
<div markdown="1">
  
| mql_id | 기업에서 선별한 잠재 고객 식별 ID |
| --- | --- |
| seller_id | 판매자ID |
| sdr_id | 영업 개발 담당자ID : 잠재 고객 찾고, 첫번째 접촉점을 만드는 담당자 |
| sr_id | 영업 담당자 ID : 잠재 고객을 실제 고객으로 전환하기 위해 그들과 직접적으로 상호 작용하고, 제품 또는 서비스에 대해 더 상세히 설명하고, 계약을 체결하는 역할 |
| won_date | SR과 잠재 고객의 계약 체결 일자, 시각 |
| business_segment | 판매자의 비즈니스 세그먼트(ex,리셀러 제조업체 등) |
| lead_type | 리드 타입 (ex 온라인, 오프라인 등) |
| lead_behaviour_profile | 잠재 고객의 행동 프로필 (현재 우리는 아래 단어의 의미를 추측만 가능한 상태) |
| has_company | 판매자의 회사 보유 여부 |
| has_gtin | 판매자의 제품에 대한 GTIN(Global Trade Item Number) 보유 여부 * GITN :국제적으로 인정되는 제품의 고유 식별자 |
| average_stock | 판매자의 평균 재고량 |
| business_type | 판매자의 비즈니스 유형(ex 제조업체, 도매업체, 소매업체 등 ) |
| declared_product_catalog_size | 판매자가 등록한 제품 카탈로그 크기 |
| declared_monthly_revenue | 판매자가 보고한 월 간 매출 |
</div>
</details>

<details>
<summary>olist_marketing_qualified_leads_dataset</summary>
<div markdown="2">

| mql_id | 기업에서 정의한 잠재 고객 식별 id |
| --- | --- |
| first_contact_date | 기업이 처음 잠재 고객에게 컨택한 날짜 |
| landing_page_id | 잠재 고객이 처음 접속한 페이지 |
| origin | 잠재 고객이 처음 접속한 채널(유입경로) |
</div>
</details>


[Brazilian E-Commerce Public Dataset by Olist](https://www.kaggle.com/datasets/olistbr/brazilian-ecommerce)
<details>
<summary>olist_customers_dataset</summary>
<div markdown="2">

| customer_id | 고객 ID : 구매 시 마다 생김 |
| --- | --- |
| customer_unique_id | 고유한 고객 ID |
| customer_zip_code_prefix | 우편번호 앞자리 |
| customer_city | 고객 거주 도시 이름 |
| customer_state | 고객 거주 주 이름 |
</div>
</details>


<details>
<summary>olist_geolocation_dataset</summary>
<div markdown="2">

| geolocation_zip_code_prefix: | 우편번호 앞자리 |
| --- | --- |
| geolocation_lat | 위도 |
| geolocation_lng | 경도 |
| geolocation_city | 도시 이름 |
| geolocation_state | 주 이름 |
</div>
</details>

<details>
<summary>olist_order_items_dataset</summary>
<div markdown="2">

| order_id | 주문 ID |
| --- | --- |
| order_item_id | 한 주문서에서의 아이템 순서 |
| product_id | 제품 ID |
| seller_id | 판매자 ID |
| shipping_limit_date | 배송 마감 기한 |
| price | 제품 가격 |
| freight_value | 운송 비용 |
</div>
</details>

<details>
<summary>olist_order_payments_dataset</summary>
<div markdown="2">

| order_id | 주문서 ID |
| --- | --- |
| payment_sequential | 결제 순서 |
| payment_type | 결제 방식 (credit card, boleto, voucher, debit card ) |
| payment_installments | 할부 개월 수 |
| payment_value | 결제 금액 |
</div>
</details>

<details>
<summary>olist_order_reviews_dataset</summary>
<div markdown="2">

| review_id | 리뷰 ID |
| --- | --- |
| order_id | 주문 ID |
| review_score | 평점 (1-5) |
| review_comment_title | 리뷰 제목 |
| review_comment_message | 리뷰 메시지 |
| review_creation_date | 리뷰 작성일 |
| review_answer_timestamp | 리뷰에 대한 답변 시간 |
</div>
</details>


<details>
<summary>olist_orders_dataset</summary>
<div markdown="2">

| order_id | 주문서 ID |
| --- | --- |
| customer_id | 고객 ID |
| order_status | 주문 상태|
| order_purchase_timestamp | 주문한 날짜와 시간 |
| order_approved_at | 주문이 승인된 날짜와 시간 |
| order_delivered_carrier_date | 판매자→ 운송업체 제품 인수 날짜   |
| order_delivered_customer_date | 고객에게 실제로 배송 된 날짜 |
| order_estimated_delivery_date | 판매자 또는 운송업체가 고객에게 처음 안내했던 예상 배송일 |
</div>
</details>

<details>
<summary>olist_products_dataset</summary>
<div markdown="2">

| product_id | 제품 ID |
| --- | --- |
| product_category_name | 제품 카테고리 이름 |
| product_name_lenght | 제품 이름 길이 |
| product_description_lenght | 제품 설명 길이 |
| product_photos_qty | 제품 사진 수 |
| product_weight_g | 제품 무게 (g) |
| product_length_cm | 제품 길이 (cm) |
| product_height_cm | 제품 높이 (cm) |
| product_width_cm | 제품 넓이 (cm) |
</div>
</details>


<details>
<summary>olist_sellers_dataset</summary>
<div markdown="2">

| seller_id | 판매자 ID |
| --- | --- |
| seller_zip_code_prefix | 판매자 우편번호 앞자리 |
| seller_city | 판매자 도시 |
| seller_state | 판매자 주 |
</div>
</details>

### 파이프라인
![Untitled (4)](https://github.com/KIMJEONGSU/PROJECT/assets/23291338/ec9e5de3-311e-45d3-95a5-b9526cb1f199)
- `AWS RDS` : EC2 안에 PostgreSQL을 설치해서 사용할 수도 있지만 RDS는 스샷 생성이나 복제본 생성이 가능하다. 데이터베이스의 관리와 안정성을 높여준다는 측면에서 RDS는 추가적인 보안 설정이 가능하다.
- `Tableau` : 다양한 데이터 소스와 연결하여 데이터를 통합 및 분석이 가능하고 다양한 시각화 가능. 또한, 대규모 데이터 처리에 적합하기 때문.
