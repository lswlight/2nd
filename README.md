# claude-skills

PC의 Claude Code에서 어느 폴더를 열어도 쓸 수 있는 개인 스킬 모음입니다.
이 저장소를 사용자 스킬 폴더(`~/.claude/skills`)에 그대로 받아서 씁니다.

## 설치

**Windows (PowerShell)**
```powershell
git clone https://github.com/lswlight/2nd.git $env:USERPROFILE\.claude\skills
```

**Mac**
```bash
git clone https://github.com/lswlight/2nd.git ~/.claude/skills
```

`skills` 폴더가 이미 있고 비어 있지 않으면 실패합니다. 기존 폴더 이름을 `skills_old` 로 바꾼 뒤 다시 실행하세요.
업데이트는 그 폴더에서 `git pull` 하면 됩니다.

## Google Workspace 스킬 (gws-*, recipe-*, persona-researcher)

[googleworkspace/cli](https://github.com/googleworkspace/cli) v0.22.5 에서 가져왔습니다 (Apache-2.0, `LICENSE-googleworkspace-cli.txt`).

| 용도 | 스킬 |
|---|---|
| 실험 데이터·매매일지 기록과 조회 | `gws-sheets`, `gws-sheets-read`, `gws-sheets-append` |
| 시트 데이터로 Docs 보고서 만들기 | `recipe-generate-report-from-sheet` |
| 시트 탭 비교 (기존 배합 vs 신규 배합) | `recipe-compare-sheet-tabs` |
| 메일 첨부 성적서를 Drive에 저장 | `recipe-save-email-attachments` |
| 매매일지 월별 탭 만들기 | `recipe-copy-sheet-for-new-month` |
| 할 일 관리 | `gws-tasks` |
| 연구자용 묶음 | `persona-researcher` |
| 위 스킬들이 함께 쓰는 스킬 | `gws-shared`, `gws-docs`, `gws-docs-write`, `gws-drive`, `gws-drive-upload`, `gws-gmail` |

### 처음 한 번 설정

```bash
npm install -g @googleworkspace/cli
gws auth setup      # Google Cloud 프로젝트 생성 (gcloud 필요)
gws auth login -s sheets,docs,drive,gmail,tasks
```

로그인은 기본 상태(테스트 모드)에서 7일마다 풀립니다. 오래 쓰려면:

1. https://console.cloud.google.com/apis/credentials/consent 에서 게시 상태를 **프로덕션으로 게시**로 바꿉니다.
2. `gws auth login -s sheets,docs,drive,gmail,tasks` 를 한 번 더 실행합니다.

"확인되지 않은 앱" 경고는 **고급 → 계속** 으로 넘어가면 됩니다.

## 스킬 추가

폴더 하나에 `SKILL.md` 하나가 스킬 하나입니다. 이 저장소 맨 위에 폴더를 추가하고 커밋하면 됩니다.
