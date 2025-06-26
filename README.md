<p align="center">
  <img src="https://github.com/JISUSAMA/JISUSAMA/assets/38304918/47a5212d-7794-4c49-ae09-38466b9c9c4c" width="320" alt="복둥이의 시간여행 메인 이미지">
</p>

<h1 align="center">복둥이의 시간여행 프로젝트</h1>

<p align="center">
  복천 박물관 야외 전시관에서 운영되는 증강현실(AR) 기반 체험형 게임 콘텐츠 🎮<br>
  시간여행을 떠난 가야의 선조들을 도와 고장난 버스에서 떨어진 짐(유물)을 찾아주는 스토리 기반 AR 교육 콘텐츠입니다.
</p>

---

## 🗓️ 작업 기간
2021.09 ~ 2021.12 (4개월)

## 🧑‍💻 기여도
- 복천동 외주 프로젝트 3건 중 **'복둥이의 시간여행' 단독 개발**.
- UI/UX 설계, 애니메이션 연출, AR 인식, 사운드 시스템 포함 전반 개발 수행.
- 디자인팀의 결과물을 바탕으로 기능 설계 및 콘텐츠 연동 완수.

---

## ⚙️ 기술 스택

| 항목             | 내용                             |
|------------------|----------------------------------|
| 개발 환경        | Unity 2022.3 이상                |
| AR 라이브러리    | Vuforia                          |
| UI 애니메이션    | DOTween                          |
| 영상 재생        | UnityEngine.Video, RenderTexture |
| 오디오 관리      | AudioMixer, AudioSource          |
| 데이터 저장      | PlayerPrefs                      |

---

## 🎮 게임 플레이 흐름

1. **인트로 영상** →  
2. **튜토리얼(복둥이)** →  
3. **캐릭터 친구 선택** →  
4. **AR 유물 찾기 미션** →  
5. **성공/실패 반응 및 대사 출력** →  
6. **모든 미션 완료 시 엔딩 영상 재생**

---

## 🧠 주요 기능

### ✅ AR 유물 탐색
- Vuforia 기반 마커 인식을 통해 지정된 유물을 인식해야 미션 성공.
- 유물 매칭 실패 시 캐릭터의 실패 대사 및 애니메이션 출력.

### ✅ 캐릭터별 미션 스토리
- 수로, 비화, 황옥, 대로, 고로, 말로 총 6명의 캐릭터가 각각 유물을 잃어버린 상황 설정.
- 각 캐릭터는 고유한 나레이션, 감정 표현, 미션 유물을 가짐.

### ✅ UI/사운드/영상 통합 구성
- DOTween을 통한 자연스러운 대화창, 버튼 애니메이션 구현.
- AudioManager를 통해 BGM, 효과음, 캐릭터 나레이션 사운드 분리 재생.
- VideoPlayer를 통해 오프닝/튜토리얼/엔딩 영상 제어.

---

## 🔍 코드 구조 및 주요 클래스 설명

| 클래스 이름 | 설명 |
|-------------|------|
| `GameManager.cs` | 전체 게임 흐름 및 진행 상태 관리 |
| `DialogManager.cs` | 대화창, 타이핑 연출, 나레이션 타이밍 제어 |
| `SoundManager.cs` / `SoundFunction.cs` | 배경음, 효과음, 캐릭터 음성 관리 |
| `MissionCheck.cs` | 마커 인식 결과로 유물 판별 |
| `Game_[캐릭터].cs` | 캐릭터별 미션 진행, 대사, 애니메이션 |
| `Tutorial_UIManager.cs`, `Title_UIManager.cs` | 씬 전환, 영상 재생, 튜토리얼 제어 |
| `CameraResolution.cs` | 16:9 비율 유지 및 레터박스 처리 |

```csharp
// 유물 인식 판별 예시
if (imgTarget[2].CurrentStatus == TrackableBehaviour.Status.TRACKED)
{
    findRelicState = true;
    RelicAcquirePopup();
}
````

```csharp
// 대화 타이핑 + 사운드 연동
Dialog_TM.DOText(dialog_str, Typing_speed);
SoundManager.Instance.PlayCharacterDialog("복둥이 1", 8f);
```

---

## 🖼️ 스크린샷

<table>
  <tr>
    <td align="center">
      <img src="https://github.com/JISUSAMA/JISUSAMA/assets/38304918/33925c28-de1b-4c4f-96ba-55b82f8f4c51" width="300"/><br>
      <sub>스크린샷 1</sub>
    </td>
    <td align="center">
      <img src="https://github.com/JISUSAMA/JISUSAMA/assets/38304918/3fd2d25d-ebc0-48e6-974f-39e3f63e01e5" width="300"/><br>
      <sub>스크린샷 2</sub>
    </td>
    <td align="center">
      <img src="https://github.com/JISUSAMA/JISUSAMA/assets/38304918/d7b5cb0e-fe93-491c-8d3d-872d0dfffa37" width="300"/><br>
      <sub>스크린샷 3</sub>
    </td>
  </tr>
</table>

---

## 📎 부록: 캐릭터별 유물 및 마커 정보

<table>
  <thead>
    <tr>
      <th>캐릭터</th>
      <th>유물 이름</th>
      <th>설명</th>
      <th>마커 이미지 (예시)</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>복둥이</td>
      <td>하늘을 나는 신발</td>
      <td>가야의 상상력을 담은 전설 속 신발</td>
      <td><img src="https://raw.githubusercontent.com/BUGISU/Bokcheon-dong/main/ScreenShots/Bokdungi_scaled.jpg" width="100"/></td>
    </tr>
    <tr>
      <td>수로</td>
      <td>고리자루칼</td>
      <td>나라를 세우기 위한 상징적인 무기</td>
      <td><img src="https://raw.githubusercontent.com/BUGISU/Bokcheon-dong/main/ScreenShots/Suro.jpg" width="100"/></td>
    </tr>
    <tr>
      <td>비화</td>
      <td>굽다리 접시</td>
      <td>다리가 달린 독특한 모양의 식기</td>
      <td><img src="https://raw.githubusercontent.com/BUGISU/Bokcheon-dong/main/ScreenShots/Bihwa_scaled.jpg" width="100"/></td>
    </tr>
    <tr>
      <td>황옥</td>
      <td>목걸이</td>
      <td>부모님에게 물려받은 소중한 보물</td>
      <td><img src="https://raw.githubusercontent.com/BUGISU/Bokcheon-dong/main/ScreenShots/Hwangok_scaled.jpg" width="100"/></td>
    </tr>
    <tr>
      <td>대로</td>
      <td>재갈</td>
      <td>말을 제어하는 도구, 말타기 필수품</td>
      <td><img src="https://raw.githubusercontent.com/BUGISU/Bokcheon-dong/main/ScreenShots/Daero_scaled.jpg" width="100"/></td>
    </tr>
    <tr>
      <td>고로</td>
      <td>투구</td>
      <td>몸을 보호하기 위한 방어용 장비</td>
      <td><img src="https://raw.githubusercontent.com/BUGISU/Bokcheon-dong/main/ScreenShots/Goro_scaled.jpg" width="100"/></td>
    </tr>
    <tr>
      <td>말로</td>
      <td>화로 모양 그릇 받침</td>
      <td>불을 담는 그릇 받침, 금속 작업에 사용</td>
      <td><img src="https://raw.githubusercontent.com/BUGISU/Bokcheon-dong/main/ScreenShots/Malro_scaled.jpg" width="100"/></td>
    </tr>
  </tbody>
</table>

> ※ 위 마커 이미지는 예시이며, 실제 콘텐츠에서는 Vuforia AR 마커로 활용됩니다.

---

## 🚀 실행 방법

1. Unity 2022.3 이상에서 프로젝트 열기
2. Vuforia 개발자 키 등록
3. `00TitleScreen` 씬 실행
4. 에디터 또는 실제 마커 기반 테스트 진행
---

## 📌 라이선스 및 문의

* 본 프로젝트는 복천 박물관과 협업한 교육용 AR 콘텐츠입니다.
* 무단 복제, 상업적 사용을 금지합니다.

