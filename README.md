# CV

원본: `mingyujeon_cv.yaml`. 생성 파일은 Git에서 제외된 `rendercv_output/`에 저장됩니다.

## 렌더링 (PowerShell)

프로젝트 폴더에서 실행합니다.

```powershell
$env:PYTHONUTF8 = '1'; uv run rendercv render mingyujeon_cv.yaml
```

결과 PDF: `rendercv_output/Mingyu_Jeon_CV.pdf`

`uv run`은 프로젝트의 가상환경을 사용하므로 별도 활성화나 전역 RenderCV 설치가 필요 없습니다. `PYTHONUTF8`은 Windows CP949 환경에서 완료 표시 문자를 출력할 때 발생하는 `UnicodeEncodeError`를 방지합니다. 새 PowerShell 세션에서도 위 명령을 그대로 사용하세요.

## 폴더 이동 후 실행 경로 오류

`uv trampoline failed to canonicalize script path`가 발생하면 이동 전 Python 경로가 가상환경 실행 파일에 남아 있을 수 있습니다. 잠금 파일의 버전을 유지하며 다시 설치한 뒤 렌더링합니다.

```powershell
uv sync --locked --reinstall
$env:PYTHONUTF8 = '1'; uv run rendercv render mingyujeon_cv.yaml
```

일반 `uv sync --locked`는 이미 설치된 패키지의 실행 파일을 다시 만들지 않아 이 오류를 해결하지 못할 수 있습니다.
