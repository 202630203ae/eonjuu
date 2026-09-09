// 저녁 메뉴 데이터베이스 (이모지, 메뉴명, 카테고리)
const menuList = [
    { emoji: "🥘", name: "돼지고기 김치찌개", category: "한식 • 칼칼한 국물" },
    { emoji: "🍲", name: "차돌박이 된장찌개", category: "한식 • 구수한 국물" },
    { emoji: "🥩", name: "삼겹살 구이", category: "한식 • 고기 요리" },
    { emoji: "🍗", name: "양념 양념치킨", category: "야식 • 바삭함" },
    { emoji: "🍕", name: "콤비네이션 피자", category: "양식 • 고소함" },
    { emoji: "🍝", name: "매콤 아라비아따 파스타", category: "양식 • 면 요리" },
    { emoji: "🍣", name: "모둠 초밥", category: "일식 • 깔끔함" },
    { emoji: "🍱", name: "바삭한 등심 돈가스", category: "일식 • 튀김" },
    { emoji: "🍜", name: "진한 돈코츠 라멘", category: "일식 • 면 요리" },
    { emoji: "🥘", name: "알싸한 마라탕", category: "중식 • 매콤함" },
    { emoji: "🥟", name: "바삭한 꿔바로우", category: "중식 • 튀김" },
    { emoji: "🍔", name: "수제 치즈버거", category: "패스트푸드 • 든든함" },
    { emoji: "🥓", name: "족발 & 보쌈", category: "한식/야식 • 푸짐함" },
    { emoji: "🍲", name: "얼큰한 뼈해장국", category: "한식 • 든든한 국물" },
    { emoji: "🍲", name: "부대찌개", category: "한식 • 자극적인 맛" },
    { emoji: "🍛", name: "마늘 후레이크 카레", category: "일식/양식 • 든든함" },
    { emoji: "🥗", name: "닭가슴살 샐러드", category: "다이어트 • 가벼움" },
    { emoji: "🌮", name: "소고기 타코", category: "멕시칸 • 이색적인 맛" }
];

// DOM 요소 가져오기
const emojiDisplay = document.getElementById("emojiDisplay");
const menuName = document.getElementById("menuName");
const menuCategory = document.getElementById("menuCategory");
const recommendBtn = document.getElementById("recommendBtn");
const historyTags = document.getElementById("historyTags");

let history = [];

// 랜덤 추천 함수
function getRandomMenu() {
    // 버튼 비활성화 (연타 방지)
    recommendBtn.disabled = true;
    
    let counter = 0;
    const totalFrames = 15; // 슬롯머신 효과 횟수
    
    // 슬롯머신 애니메이션 효과
    const interval = setInterval(() => {
        const randomIndex = Math.floor(Math.random() * menuList.length);
        const item = menuList[randomIndex];
        
        emojiDisplay.textContent = item.emoji;
        menuName.textContent = item.name;
        menuCategory.textContent = item.category;
        
        counter++;
        
        if (counter >= totalFrames) {
            clearInterval(interval);
            
            // 최종 결과 선택
            const finalIndex = Math.floor(Math.random() * menuList.length);
            const selectedMenu = menuList[finalIndex];
            
            emojiDisplay.textContent = selectedMenu.emoji;
            menuName.textContent = selectedMenu.name;
            menuCategory.textContent = selectedMenu.category;
            
            // 통통 튀는 애니메이션
            emojiDisplay.classList.remove("bounce");
            void emojiDisplay.offsetWidth; // reflow 발생
            emojiDisplay.classList.add("bounce");
            
            // 히스토리 업데이트
            updateHistory(selectedMenu);
            
            // 버튼 재활성화
            recommendBtn.disabled = false;
        }
    }, 60);
}

// 최근 추천 내역 업데이트 함수
function updateHistory(menu) {
    // 중복 제거 및 최근 5개만 유지
    history = [menu, ...history.filter(h => h.name !== menu.name)].slice(0, 5);
    
    historyTags.innerHTML = "";
    history.forEach(item => {
        const tag = document.createElement("span");
        tag.className = "history-tag";
        tag.textContent = `${item.emoji} ${item.name}`;
        historyTags.appendChild(tag);
    });
}

// 이벤트 리스너 등록
recommendBtn.addEventListener("click", getRandomMenu);
