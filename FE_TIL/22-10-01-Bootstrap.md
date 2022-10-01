## 부트스트랩
	웹 프레임워크 - 최소한의 작업으로 빠른 결과물 생성
    반응형 사이트 최적화
    
~~~html
<script src="https://cdn.jsdelivr.net/npm/bootstrap@5.2.1/dist/js/bootstrap.bundle.min.js">
</script>
~~~

## 그리드 시스템
	전체 화면을 12개의 컬럼으로 나눔
    12개 컬럼이 모여 1개의 row
    
~~~html
<div class="col-md-6">hello</div>	<!--12칸 중 6칸 차지-->
~~~

	넓이 100% 모두 사용하고 싶은 경우 -> .container-fluid 사용
    컬럼 사이 여백(패딩,마진) 제거 -> .row에 .no-gutters 적용
    
### 이미지
	반응형 이미지
    class = "img-fluid"
    
    둥근 1px 테두리 모양
    class = "img-thumbnail"
    
    이미지 정렬
    class = "rounded float-left"
    
### 테이블
	class = "table"
    
### 텍스트와 버튼

~~~html
<button type="button" class="btn btn-primary">Primary</button>
<button type="button" class="btn btn-secondary">Secondary</button>
<button type="button" class="btn btn-success">Success</button>
<button type="button" class="btn btn-danger">Danger</button>
<button type="button" class="btn btn-warning">Warning</button>
<button type="button" class="btn btn-info">Info</button>
<button type="button" class="btn btn-light">Light</button>
<button type="button" class="btn btn-dark">Dark</button>
<button type="button" class="btn btn-link">Link</button>
~~~

	button 요소와 함께 사용할 수 있지만 a 나 input 요소에도 사용이 가능하다.
    
### 모달창
	보통 footer 밑에 위치