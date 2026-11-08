# Scoped behavioral observations — 2026-11-09

## English

Target: public v0.2.3, commit `8c867a512e29388ac2176292cc41d3136511b661`. A user ran the scenarios in Claude desktop's Code tab on macOS. The plugin was **not loaded in that session**: the tester explicitly read the target bundle's skill, procedures, and templates. These are observations of following supplied instructions, not a pass for installed-plugin loading or automatic skill invocation. Host permission prompts were bypassed in the test environment; application-level approval questions still required actual user replies. This does not test the host permission system.

A subsequent review independently compared the bundle's 76 files with the Git tag, workspace snapshots, hashes, the proposed rule file, and the resulting diff. Raw conversation/account context is not published here.

| Scenario | Observed result | Scope |
|---|---|---|
| Declined setup | No project files created | First reply was approval; the tester asked for clarification and the user corrected it to decline before any write |
| Approved setup | Seven files matched the Korean templates; one instruction marker pair | File-only setup; no session operations |
| Repeated setup | Existing task records and files preserved; no duplicate rule section | Snapshot/content comparison unchanged |
| Read-only status | Correct completed/blocked/next actions with sources; unknown session state identified | Project hashes unchanged; session lookup omitted |
| Rule comparison | Bounded proposal retained custom prefix, ledger and task limit | Target version was explicitly read source, not a loaded plugin |
| Declined rule update | **Not tested** | User chose and confirmed application instead of rejection |
| Approved rule update | Only CLAUDE.md changed, exactly matching the proposed file; text outside markers and task data preserved | Additional observation following explicit confirmation; second comparison reported no further patch |
| Installed skill activation / UI session creation | **Not tested** | No installed v0.2.3 activation; no session-management operations |

The recorded comparisons support file-integrity findings; they do not independently reconstruct every model tool call or prove behavior on another host. A dedicated rule-update rejection run and a clean session with the actual v0.2.3 plugin loaded remain outstanding. Historical broader claims should not be inferred from this scoped run. See the [reproduction guide](reviewer-guide.md).

## 한국어

대상은 공개 v0.2.3(`8c867a5`)입니다. 사용자가 macOS의 Claude desktop Code 탭에서 시험했습니다. **해당 대화에 플러그인이 로드되지 않아** 번들의 스킬·절차·템플릿을 명시적으로 읽고 수행했습니다. 따라서 지침 수행 관찰이며 설치된 플러그인의 정상 로드·자동 발동 통과가 아닙니다. 호스트 권한은 bypass 상태였고 Podium 업무 승인 질문에는 실제 사용자 답변을 받았습니다. 호스트 권한 체계를 검증한 것은 아닙니다.

후속 검토에서 번들 76개 파일과 태그 일치, 프로젝트 스냅샷·해시·제안 파일·적용 diff를 직접 대조했습니다. 설정 거절 후 무변경, 승인한 7개 파일의 한글 템플릿 일치, 재설정 무중복·기록 보존, 현황 조회 무변경을 확인했습니다. 세션 조회는 생략한 파일 기반 시험입니다.

규칙 갱신 거절 시험은 **미검증**입니다. 사용자가 적용을 선택하고 재확인했으므로 대신 승인 적용을 관찰했습니다. CLAUDE.md만 제안 파일과 동일하게 바뀌었고 경계 밖 규칙·사용자 설정·업무 기록은 보존됐습니다. 2차 비교는 추가 변경 없음으로 보고됐습니다. 파일 증거 확인을 모든 도구 호출이나 다른 호스트 동작의 독립 검증으로 확대하지 않습니다.

남은 시험은 실제 0.2.3을 로드한 깨끗한 대화의 발동 확인과 별도의 규칙 갱신 거절 사례입니다. UI 대화 생성·이동·보관은 시험하지 않았습니다. 원본 대화·계정 맥락은 공개하지 않습니다. [재현 안내](reviewer-guide.ko.md)를 참고하세요.
