## Tailwind CSS
	HTML을 벗어나지 않고 빠르게 웹사이트 구축
    클래스 이름 고민할 필요 없고 협업 문제 없으며 유지보스에 용이하다
    
    부트스트램과 달리 반응형을 별도로 짜야함
    reset 코드가 포함되어 있음
    마진 병합 현상도 발생함
    
    w-96 : 96px가 아님 
    기본적으로 w-0 : 0px
    w-px -> width:1px
    w-1 -> width:0.25rem -> 4px
    w-2 -> width:0.5rem -> 8px
    
    bg-red-200 : red color 숫자가 높아질수록 진해짐
    
### 기본 속성
	주어진 값 제외한 다른 값 사용하고 싶은 경우
    arbitrary value 사용 -> class="top-[117px]"

### flex & grid
	class = "flex"
    class = "flex-col"
    
    <!-- 
        justify-content: center        - justify-center
        justify-content: space-between - justify-between
        align-items: flex-start        - items-start
        align-items: center            - items-center
        align-self: auto               - self-auto
        align-slef: flex-start         - self-start
        align-slef: flex-end           - self-end
        flex: 1 1 0%                   - flex-1
        flex: 1 1 auto                 - flex-auto
        flex: 0 1 auto                 - flex-initial
        flex: none                     - flex-none
    -->
    
    class = "grid"
    
### 반응형
	sm : @media (min-width: 640px)
    md : @media (min-width: 768px)
    lg : @media (min-width: 1024px)
    xl : @media (min-width: 1280px)
    2xl : @media (min-width: 1536px)
    dark : @media (prefers-color-scheme: dark)
    
    <div class="w-16 h-16 bg-red-300 sm:w-20 sm:h-20 sm:bg-blue-300 md:w-32 md:h-32 md:bg-green-300">
    
### 계획
> Tailwind CSS 를 이용한 천하제일 이력서 만들어보기