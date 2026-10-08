# 🍽️ 로이드케이 점메추

로이드케이 동료들과 함께 쓰는 점심 메뉴·맛집 뽑기 페이지입니다.

👉 https://r4nbbit.github.io/lloydk_lunch/

---

## ✨ 기능

- **메뉴 추천**: 메뉴판에서 점심 메뉴를 랜덤으로 뽑아요.
- **맛집 추천**: 회사 근처 맛집 중 한 곳을 뽑고, 종류·거리·주소와 네이버 지도 링크를 함께 보여줘요.
  - 휴무일인 가게는 그날 추천에서 자동으로 빠져요.
- **다시 뽑기**: 방금 나온 결과는 피해서 다시 뽑아요.
- **복사**: 결과를 복사해서 단톡방에 바로 붙여넣을 수 있어요.
- **같이 고치기**: 메뉴·가게를 추가하거나 삭제하면 링크를 연 모든 사람에게 바로 반영돼요. 로그인은 필요 없어요.
- **초기화**: 탭별로 처음 설정한 목록으로 되돌릴 수 있어요.

## 📂 구조

```
lloydk_lunch/
├─ index.html        # 페이지 전체 (화면, 기본 목록, Firebase 연결)
├─ firestore.rules   # Firestore 보안 규칙 (콘솔에 붙여넣는 용도)
└─ README.md
```

- 기본 메뉴판과 맛집 목록은 `index.html` 안의 `DEFAULT_MENUS`, `DEFAULT_PLACES`에 들어 있어요. 초기화하면 이 목록으로 돌아가요.
- 같이 고친 목록은 Firebase Firestore의 `lists/menus`, `lists/places` 문서에 저장돼요. 문서가 없으면 기본 목록을 보여줘요.

## 🔧 설정 방법

### 1. Firebase

1. Firebase 콘솔에서 프로젝트를 만들고 **Firestore Database**를 생성해요. (위치: `asia-northeast3`, 프로덕션 모드)
2. **Firestore → 규칙** 탭에 `firestore.rules` 내용을 붙여넣고 **게시**해요.
3. 웹 앱을 등록하고 나온 `firebaseConfig` 값을 `index.html`의 `firebaseConfig`에 넣어요.

> `firebaseConfig`는 웹페이지에 공개로 들어가는 값이라 저장소에 올라가도 괜찮아요. 데이터 접근은 보안 규칙이 막아줘요.

### 2. GitHub Pages

저장소 **Settings → Pages**에서 Source를 **Deploy from a branch**, Branch를 **main / (root)**로 저장하면 몇 분 뒤 위 주소로 열려요.

## ⚠️ 참고

- 링크만 있으면 누구나 목록을 고칠 수 있어요. 목록이 이상해지면 **초기화**를 눌러주세요.
- 무료(Spark) 요금제라 사용량 한도를 넘어도 요금은 나가지 않고, 그날만 잠시 저장이 멈춰요.
