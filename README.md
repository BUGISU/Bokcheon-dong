<div align="center">
  <img src="https://github.com/JISUSAMA/JISUSAMA/assets/38304918/47a5212d-7794-4c49-ae09-38466b9c9c4c" alt="복둥이의 시간여행 메인 이미지">
</div>

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
| `GameManager.cs` | 싱글톤. 전체 게임 흐름 및 진행 상황 저장 (`Mission_Complete`, `PausePopup` 등). |
| `DialogManager.cs` | 대화창 관리, 타이핑 연출, 나레이션 타이밍, 버튼 제어 포함. |
| `SoundManager.cs` / `SoundFunction.cs` | 배경음, 효과음, 캐릭터 음성 재생 기능 분리. 오디오 채널 관리. |
| `MissionCheck.cs` | 현재 AR 마커가 유효한 유물인지 판별. `Status.TRACKED` 기반 유물 매칭. |
| `Mission_UIManager.cs` | 미션 씬 UI 구성. 캐릭터별 스프라이트, 배경, 유물 이미지 설정. |
| `Game_[캐릭터].cs` | 각 캐릭터(예: Suro, Bihwa)의 이벤트, 대사, 애니메이션 로직 포함. |
| `Tutorial_UIManager.cs` / `Title_UIManager.cs` | 영상 재생과 씬 전환, 튜토리얼 연출 흐름 제어. |
| `CameraResolution.cs` | 16:9 비율 유지, Canvas 스케일 조정, 레터박스 구현. |

### 예시 코드: AR 유물 인식 판별
```csharp
if (imgTarget[2].CurrentStatus == TrackableBehaviour.Status.TRACKED)
{
    findRelicState = true;
    RelicAcquirePopup();
}
````

### 예시 코드: 대화 출력 & 사운드 연동

```csharp
Dialog_TM.DOText(dialog_str, Typing_speed);
SoundManager.Instance.PlayCharacterDialog("복둥이 1", 8f);
```

---

## 📁 디렉토리 구조 예시

```
Assets/
├── Scripts/
│   ├── UI/
│   │   ├── Title_UIManager.cs
│   │   ├── Tutorial_UIManager.cs
│   │   ├── Mission_UIManager.cs
│   ├── Characters/
│   │   ├── Game_Suro.cs
│   │   ├── Game_Bihwa.cs
│   │   └── Game_Goro.cs ...
│   ├── AR/
│   │   └── MissionCheck.cs
│   ├── System/
│   │   ├── SoundManager.cs
│   │   └── CameraResolution.cs
```

---

## 🖼️ 스크린샷

<table>
  <tr>
    <td align="center">
      <img src="https://github.com/JISUSAMA/JISUSAMA/assets/38304918/33925c28-de1b-4c4f-96ba-55b82f8f4c51" width="320"/><br>
      <sub>스크린샷 1</sub>
    </td>
    <td align="center">
      <img src="https://github.com/JISUSAMA/JISUSAMA/assets/38304918/3fd2d25d-ebc0-48e6-974f-39e3f63e01e5" width="320"/><br>
      <sub>스크린샷 2</sub>
    </td>
    <td align="center">
      <img src="https://github.com/JISUSAMA/JISUSAMA/assets/38304918/d7b5cb0e-fe93-491c-8d3d-872d0dfffa37" width="320"/><br>
      <sub>스크린샷 3</sub>
    </td>
  </tr>
</table>

---

## 🚀 실행 방법

1. Unity 2022.3 이상에서 프로젝트 열기
2. Vuforia Developer License Key 등록
3. `00TitleScreen` 씬 실행
4. 실제 마커를 사용하거나 에디터에서 테스트 가능

---

## 🎯 향후 개선 사항

* UI 반응성 향상 및 모바일 해상도 최적화
* 다양한 언어(영어, 일본어 등) 지원
* 추가 유물 및 캐릭터 확장 콘텐츠 적용

---

## 📌 참고 및 권한

* 본 콘텐츠는 복천 박물관과 협업하여 제작된 교육용 앱입니다.
* 소스코드 및 이미지의 상업적 무단 사용은 금지됩니다.
* 배포 및 라이선스 관련 문의: mcmedia solution

## 📎 부록: 캐릭터별 유물 및 마커 정보

| 캐릭터 | 유물 이름 | 설명 | 마커 이미지 (예시) |
|--------|-----------|------|---------------------|
| 복둥이 | 하늘을 나는 신발 | 가야의 상상력을 담은 전설 속 신발 | ![](https://github.com/JISUSAMA/JISUSAMA/assets/38304918/example-marker1.png) |
| 수로 | 고리자루칼 | 나라를 세우기 위한 상징적인 무기 | ![](https://github.com/JISUSAMA/JISUSAMA/assets/38304918/example-marker2.png) |
| 비화 | 굽다리 접시 | 다리가 달린 독특한 모양의 식기 | ![](https://github.com/JISUSAMA/JISUSAMA/assets/38304918/example-marker3.png) |
| 황옥 | 목걸이 | 부모님에게 물려받은 소중한 보물 | ![](https://github.com/JISUSAMA/JISUSAMA/assets/38304918/example-marker4.png) |
| 대로 | 재갈 | 말을 제어하는 도구, 말타기 필수품 | ![](https://github.com/JISUSAMA/JISUSAMA/assets/38304918/example-marker5.png) |
| 고로 | 투구 | 몸을 보호하기 위한 방어용 장비 | ![](https://github.com/JISUSAMA/JISUSAMA/assets/38304918/example-marker6.png) |
| 말로 | 화로 모양 그릇 받침 | 불을 담는 그릇 받침, 금속 작업에 사용 | ![](https://github.com/JISUSAMA/JISUSAMA/assets/38304918/example-marker7.png) |

> 🧾 **마커 이미지**는 박물관에서 제공한 실제 인식용 이미지입니다. 위 이미지는 예시이며, 실제 콘텐츠에서는 각 유물마다 고유한 Vuforia 마커가 연결되어 있습니다.

## 🔎 참고 사항
- AR 마커는 Vuforia에서 등록된 이미지로 구성되어 있으며, `MissionCheck.cs`에서 마커 ID와 캐릭터 이름을 매핑하여 유물 판별 로직을 수행합니다.
- 마커 인식 성공 시 → 미션 성공 애니메이션, 실패 시 → 캐릭터별 힌트 대사 출력.
- 마커 순서는 배열로 정리되어 있으며 `[0]~[8]` 번까지 인덱스를 사용합니다.
