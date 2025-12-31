---
name: publish
description: "Write-Saver에서 작성한 글을 GitHub Pages 블로그에 게시"
---

# /publish - 블로그 게시

**CRITICAL: Write-Saver에서 작성한 글을 Jekyll 기반 GitHub Pages 블로그에 게시합니다.**

## 인자 파싱

```yaml
/publish              → 최근 글 목록에서 선택하여 게시
/publish today        → 오늘 작성한 글 게시
/publish [파일명]     → 특정 세션 파일 게시
/publish draft        → 초안으로 저장 (게시 안 함)
/publish list         → 게시된 글 목록 확인
/publish stats        → 블로그 게시 통계
```

## 저장소 경로

- 세션 파일: `./sessions/`
- 블로그 설정: `./progress.json`의 `blog` 필드 참조

## 게시 플로우

### 1단계: 글 선택

```
📝 게시할 글 선택
━━━━━━━━━━━━━━━━━━━━━━

최근 작성한 글:
1. [2025-12-31] 기술 - "SwiftUI 상태 관리 패턴"
2. [2025-12-30] 에세이 - "개발자로 살아가기"
3. [2025-12-29] 창작 - "새벽의 카페"

게시할 글 번호를 선택하세요 (또는 파일 경로 입력):
```

### 2단계: 메타데이터 확인/수정

```
📋 게시 정보 확인
━━━━━━━━━━━━━━━━━━━━━━

제목: SwiftUI 상태 관리 패턴
카테고리: tech
태그: swift, swiftui, ios, state-management
설명: SwiftUI에서 상태를 효과적으로 관리하는 방법을 알아봅니다.

수정이 필요하면 말씀해주세요.
"게시"라고 입력하면 블로그에 게시됩니다.
```

### 3단계: 변환 및 게시

```
🚀 게시 중...
━━━━━━━━━━━━━━━━━━━━━━

✓ 마크다운 변환 완료
✓ Front matter 추가
✓ 블로그 저장소에 복사
✓ Git commit 생성
✓ GitHub에 push

✅ 게시 완료!
🔗 https://[username].github.io/[year]/[month]/[day]/[title]

(GitHub Actions 빌드 후 1-2분 내 반영됩니다)
```

## Jekyll 포스트 변환 규칙

### 파일명 규칙
```
YYYY-MM-DD-title-slug.md

예시:
2025-12-31-swiftui-state-management.md
```

### Front Matter 변환

원본 (write-saver 세션):
```markdown
---
date: 2025-12-31
genre: tech
duration: 30
words: 1500
---

# SwiftUI 상태 관리 패턴
```

변환 후 (Jekyll 포스트):
```markdown
---
layout: post
title: "SwiftUI 상태 관리 패턴"
date: 2025-12-31 10:30:00 +0900
categories: [tech]
tags: [swift, swiftui, ios, state-management]
author: 작성자 이름
description: "SwiftUI에서 상태를 효과적으로 관리하는 방법"
---
```

## 장르별 카테고리 매핑

| Write-Saver 장르 | 블로그 카테고리 | 기본 태그 |
|------------------|-----------------|-----------|
| journal | 일상 | daily, life |
| essay | 에세이 | essay, thoughts |
| story | 창작 | creative, fiction |
| tech | 기술 | tech, development |
| copy | 마케팅 | marketing, copywriting |

## 게시 전 체크리스트

자동으로 확인:

- [ ] 제목이 있는가?
- [ ] 본문이 100자 이상인가?
- [ ] 개인정보가 포함되어 있지 않은가? (일기 장르 경고)
- [ ] 이미지 경로가 올바른가?

### 일기(journal) 게시 경고

```
⚠️  주의: 일기 장르의 글입니다.

일기에는 개인적인 내용이 포함될 수 있습니다.
공개 블로그에 게시해도 괜찮으신가요?

[계속 게시] [취소] [일부 내용 수정 후 게시]
```

## 게시 취소/수정

```bash
/publish unpublish [제목]   # 게시된 글 삭제
/publish edit [제목]        # 게시된 글 수정
```

## /publish list

```
📋 게시된 글 목록
━━━━━━━━━━━━━━━━━━━━━━

1. [2025-12-31] SwiftUI 상태 관리 패턴 (tech)
2. [2025-12-28] 개발자의 하루 (essay)
3. [2025-12-25] 크리스마스 이야기 (story)
```

## /publish stats

```
📊 블로그 게시 통계
━━━━━━━━━━━━━━━━━━━━━━

총 게시 글: 15편
- 기술: 8편
- 에세이: 4편
- 창작: 2편
- 일상: 1편

이번 달: 3편 게시
연속 게시: 2주
```
