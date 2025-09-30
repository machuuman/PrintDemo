# Python Print Examples — Quick Guide

이 저장소는 Python의 다양한 `print()` 사용법을 짧은 예제로 보여주고, VS Code/터미널/Jupyter에서 실행하는 방법만 간단히 정리합니다.

---

## 파일 목록

### 1) main_print_v1.py

- 설명: 기본적인 `print()` 활용 종합 예제입니다.
- 동작/기능:
  - 기본 출력, 여러 값 출력(`sep`, `end` 옵션 포함)
  - f-string, `str.format()`, `%` 포맷팅(C 스타일 옛날 방식)
  - 여러 줄 출력, 딕셔너리/리스트 출력
  - f-string 내 계산식/함수 호출 예시 포함

- 실행 방법:
  - VS Code: 파일 열고 우측 상단 **Run Python File**(▶️) 클릭
  - 터미널:
    - Windows: `python main_print_v1.py` (또는 `py main_print_v1.py`)
    - macOS/Linux: `python3 main_print_v1.py`

---

### 1) main_print_v2.py

- 설명: 콘솔을 보기 좋게 꾸미기 위해 `rich` 라이브러리를 사용하는 예제
from rich import print as rprint 
from rich.table import Table
from rich.panel import Panel

# 변수 선언
name = "Alice"
age = 25
score = 95.5
data = {"name": name, "age": age, "score": score}

# 1) 컬러/스타일 출력
rprint(f"[bold green] Hello, {name}![/] Your score is [cyan]{score:.2f}[/].")

# 2) 패널(박스)로 멀티라인 출력 
panel_text = f"""
[bold]Student Info[/]
- Name: [yellow] {name}[/] 
- Age: [magenta]{age}[/]
- Score: [cyan]{score:.2f}[/]
"""
rprint(Panel(panel_text, title="Profile", border_style="blue"))

# 3) 테이블 출력 (딕셔너리/리스트 보기 좋게)
table = Table(title="Records")
table.add_column("Key", style="bold")
table.add_column("Value")
for k, v in data.items():
    table.add_row(k, str(v))
rprint(table)

# 4) sep, end 옵션 그대로 활용
rprint("2025", "09", "23", sep="-", end=" ▼ \n")
