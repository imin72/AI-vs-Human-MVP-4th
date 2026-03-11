# Core DB 구축 실행 프롬프트 (arts.ts)

```text
Core DB 구축

목표 카테고리: arts.ts

규칙
1) `data/questions/arts.ts`의 **16개 세부분야를 모두 유지**한다.
2) 각 세부분야에 포함된 질문 중 **정확히 50%**를 coreDB로 선별한다.
3) 선별된 질문을 앱 지원 6개 언어(`en`, `ko`, `ja`, `es`, `fr`, `zh`)로 번역해 coreDB 반영 가능한 결과를 만든다.

입력 데이터:
- 대상 카테고리 파일: `data/questions/arts.ts`
- 기존 core 파일: `data/questions/core/arts.core.ts`
- 지원 언어: `en`, `ko`, `ja`, `es`, `fr`, `zh`
- 카테고리명: `Arts`

작업 규칙(반드시 준수):
- [선정 규칙]
  - 세부분야 16개는 모두 포함(세부분야 삭제/제외 금지).
  - 각 세부분야별 질문 수의 50%만 선택.
  - 질문 수가 홀수면 `ceil(원본 질문 수 × 0.5)`를 적용.
  - 기존 core 파일에 이미 포함된 질문(`id`/질문본문/보기 조합)은 선택 금지.
- [중복 방지]
  - 질문 `id`는 기존 core 및 원본과 충돌 금지.
  - 질문 텍스트/보기 조합이 기존 core와 사실상 동일하면 금지.
- [번역 품질]
  - 정답 의미가 언어별로 바뀌면 안 됨.
  - 고유명사(인명/작품명/브랜드)는 원문 유지 + 필요 시 현지 표기 병기.
  - 보기 4개 길이/난이도 균형 유지.

출력 형식(반드시 이 순서):
1. `SELECTION_REPORT` (JSON)
2. `CORE_DB_PATCH` (TypeScript 코드 블록)
3. `VALIDATION_CHECKLIST` (마크다운 체크리스트)

`CORE_DB_PATCH` 조건:
- `export const ARTS_CORE_DB: Record<string, QuizQuestion[]> = { ... }` 형태.
- 키: `"{{Subtopic}}_MEDIUM_{{lang}}"` 포맷.
- 16개 세부분야 × 6개 언어 키 모두 포함.
- 세부분야별 질문 수는 원본의 50% 규칙 준수.

설명 문장은 최소화하고, 바로 반영 가능한 결과만 출력.
```
