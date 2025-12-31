# Write-Saver 프로젝트 설정

이 프로젝트는 글쓰기 실력 향상을 위한 일일 글쓰기 연습 시스템입니다.

## 프로젝트 구조

```
write-saver/
├── CLAUDE.md           # 이 파일 (프로젝트 설정)
├── progress.json       # 진행 상황 데이터
├── sessions/           # 일일 글쓰기 세션 기록
│   └── YYYY-MM-DD.md
└── weekly/             # 주간 리포트
    └── YYYY-WW.md
```

## 연동 스킬

이 프로젝트는 다음 글쓰기 스킬들과 연동됩니다:

- `write-saver` - 메인 에이전트 (세션 관리, 진행 추적)
- `daily-journal` - 일기/감정 기록
- `essay-builder` - 에세이/칼럼
- `story-crafter` - 창작/소설/시
- `tech-writer` - 기술 문서/블로그
- `copywriting` - 광고/마케팅 문구

## 주요 명령어

```
/write           - 오늘의 글쓰기 세션 시작
/write [genre]   - 특정 장르로 세션 시작
/write status    - 진행 상황 확인
/write weekly    - 주간 리포트 생성
```

## 데이터 관리 규칙

1. **세션 저장**: 각 세션은 `sessions/YYYY-MM-DD.md` 형식으로 저장
2. **진행 상황**: `progress.json`에 XP, 스트릭, 배지 등 기록
3. **주간 리포트**: 매주 일요일 `weekly/YYYY-WW.md`로 저장

## 세션 파일 형식

```markdown
---
date: YYYY-MM-DD
genre: journal|essay|story|tech|copy
duration: 30
words: 500
xp_earned: 75
---

# 오늘의 글쓰기

[사용자가 작성한 글]

---

## 피드백

[Claude의 피드백]

## 오늘의 베스트 문장

> [가장 잘 쓴 문장]
```

## 피드백 스타일 설정

현재 설정: `balanced` (균형 잡힌 피드백)

옵션:
- `encouraging` - 격려 중심, 잘한 점 강조
- `balanced` - 장점과 개선점 균형
- `critical` - 개선점 중심, 날카로운 분석

## 알림 설정

일일 글쓰기 알림: 미설정

## 목표

2026년 목표:
- [ ] 100일 연속 글쓰기
- [ ] 5가지 장르 모두 마스터
- [ ] 10,000 XP 달성
- [ ] 기술 블로그 10편 발행
- [ ] 에세이 공모전 도전
