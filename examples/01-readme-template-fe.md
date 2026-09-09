# 예시 1. template-fe 리드미

실제 사용 기록입니다. 아래 원문은 Claude 가 작성한 초안이고, 개선본은 dadeum 을 적용한
결과입니다. 두 판본 모두 공개 저장소의 git 이력에서 확인할 수 있습니다.

- 저장소: https://github.com/rhseung/template-fe
- 커밋: [`67b8875`](https://github.com/rhseung/template-fe/commit/67b8875)

## 원문

```markdown
## 공통 기능

- **MVVM을 린트로 강제한다.** `eslint-plugin-boundaries`가 View→Model 직접 접근, ViewModel→View 참조를 에러로 막는다.
- 구조는 `src/features/<name>/{models,viewmodels,views}` + 루트 배럴 없는 `src/common/`.
- **백엔드는 OpenAPI 스펙 하나면 붙는다.** Hey API가 타입·클라이언트·zod·react-query 훅을 한 번에 생성한다.
- i18n은 i18next-cli가 돌린다. `t()` 호출에서 키를 뽑고 `src/@types`에 타입까지 만든다. ko 먼저, en 나중.
- UI는 shadcn/ui(`base-nova` / Base UI) + Tailwind v4 CSS-first + Phosphor 아이콘.
- **Storybook 스토리가 곧 테스트다.** 테마·로케일 툴바 데코레이터가 붙어 있고 vitest 브라우저 프로젝트로 실행된다.
- Playwright e2e와 MSW가 같이 온다 — 백엔드 없이 `bun dev`가 돈다.
- ESLint는 엄격하다. kebab-case, named export만, 배럴 경유 import, React Compiler 룰까지.
- lint/typecheck/test는 pre-commit 훅(husky, `bun run verify`)이 커밋마다 돈다. CI는 build/storybook/e2e만
  맡고, [react-doctor](https://react.doctor)와 Claude(`review.yml`)가 PR을 리뷰한다.
  배포는 Cloudflare Pages/Vercel의 git 연동이 알아서 한다 — 별도 배포 워크플로는 없다.
- `AGENTS.md` 하나를 Claude Code, Cursor, Copilot이 전부 읽는다.

```

## 개선본

```markdown
## 공통 기능

- MVVM 구조를 lint 로 강제합니다. `eslint-plugin-boundaries` 가 View 에서 Model 로 직접
  접근하는 것과 ViewModel 이 View 를 참조하는 것을 에러로 막습니다.
- 디렉토리 구조는 `src/features/<name>/{models,viewmodels,views}` 와 root barrel 이 없는
  `src/common/` 으로 구성됩니다.
- 백엔드는 OpenAPI spec 하나만 있으면 연결됩니다. Hey API 가 type, client, zod,
  react-query hook 을 한 번에 생성합니다.
- i18n 은 i18next-cli 가 처리합니다. `t()` 호출에서 key 를 추출하고 `src/@types` 에 type 까지
  생성합니다. ko 를 먼저 작성하고 en 을 나중에 채웁니다.
- UI 는 shadcn/ui (`base-nova`, Base UI), Tailwind v4 CSS-first, Phosphor 아이콘으로
  구성합니다.
- Storybook story 를 그대로 테스트로 사용합니다. theme 과 locale toolbar decorator 가 붙어
  있고, vitest browser 프로젝트로 실행됩니다.
- Playwright e2e 와 MSW 를 함께 제공합니다. 백엔드를 실행하지 않아도 `bun dev` 가
  정상적으로 동작합니다.
- ESLint 설정은 엄격합니다. kebab-case, named export 만 허용, barrel 을 경유하는 import,
  React Compiler rule 까지 적용합니다.
- lint, typecheck, test 는 pre-commit hook (husky, `bun run verify`) 이 커밋할 때마다
  실행합니다. CI 는 build, storybook, e2e 만 담당하고, [react-doctor](https://react.doctor)
  와 Claude (`review.yml`) 가 PR 을 리뷰합니다. 배포는 Cloudflare Pages 와 Vercel 의 git
  연동이 처리하므로, 별도의 배포 워크플로는 없습니다.
- `AGENTS.md` 파일 하나를 Claude Code, Cursor, Copilot 이 모두 읽습니다.

```

## 무엇이 바뀌었나

| 규칙 | 원문 | 개선본 |
| --- | --- | --- |
| 비ASCII 문장부호 | `타입·클라이언트·zod·react-query` | `type, client, zod, react-query` |
| 비ASCII 문장부호 | `MSW가 같이 온다 — 백엔드 없이` | `MSW 를 함께 제공합니다. 백엔드를` |
| 비ASCII 문장부호 | `View→Model 직접 접근` | `View 에서 Model 로 직접 접근하는 것` |
| 비유적 어휘 | `Storybook 스토리가 곧 테스트다` | `Storybook story 를 그대로 테스트로 사용합니다` |
| 비유적 어휘 | `MSW가 같이 온다` | `MSW 를 함께 제공합니다` |
| 비유적 어휘 | `git 연동이 알아서 한다` | `git 연동이 처리하므로` |
| 기술 용어 원어 | `린트`, `루트 배럴`, `훅`, `로케일` | `lint`, `root barrel`, `hook`, `locale` |
| 종결어미 완성 | `루트 배럴 없는 src/common/.` | `root barrel 이 없는 src/common/ 으로 구성됩니다.` |
| 강조 기준 | 9개 중 4개에만 붙은 굵은 강조 | 전부 제거하고 항목 길이를 맞춤 |

목록 항목이라 접속 표시어(`즉`, `따라서`)는 넣지 않았습니다. 규칙 5번에 따른 것입니다.
