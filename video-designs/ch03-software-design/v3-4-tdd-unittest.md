---
video_id: V3.4
chapter: 3
title: "Test-Driven Development (TDD) for Network Scripts with Python unittest"
composition_id: net226-v3-4-tdd-unittest
duration_target: "5:00"
aspect: "16:9"
engine: codevideo
libraries: [prismjs, terminal-emulator]
blocks: [editor-tdd-split, terminal-test-runner]
objectives:
  - Explain the Red-Green-Refactor cycle of Test-Driven Development.
  - Construct automated unit test suites using Python's `unittest` framework.
  - Test boundary conditions and verify exceptions with `assertRaises()`.
opens_with: cpcc-open
source_section: ch03 §3.7
---

# Video Design: V3.4 Test-Driven Development with unittest

---

## Scene 1 — Why Test Network Scripts? (0:00–1:00)
**Visual:** A diagram of the Testing Pyramid highlighting the broad base: Unit Tests.
**Narration:**
> If you write an automation script that configures core network switches, how do you verify it won't crash when an unexpected string appears?
>
> You don't test it on live routers. You test it locally using automated unit tests.
>
> Test-Driven Development, or TDD, is a software discipline where you write the automated test *before* you write the functional code.

---

## Scene 2 — Writing the Failing Test: RED (1:00–2:15)
**Visual:** Authoring `tests/test_vlan.py` in VS Code:
```python
import unittest
from src.vlan_parser import parse_vlan_id

class TestVlanParser(unittest.TestCase):
    def test_valid_vlan(self):
        self.assertEqual(parse_vlan_id("100"), 100)
    
    def test_out_of_range_raises_error(self):
        with self.assertRaises(ValueError):
            parse_vlan_id("5000")
```
Terminal runs `python3 -m unittest`. Output:
`ImportError: cannot import name 'parse_vlan_id'` -> FAILED (Red).
**Narration:**
> Stage one of TDD is RED: write a failing test.
>
> We define what our function *should* do before it even exists. It should take a string `"100"` and return integer `100`. And if someone passes VLAN `5000`, it should raise a `ValueError` because VLAN IDs only go up to 4094.
>
> When we run the test, it fails immediately. That's good—we now have an objective target.

---

## Scene 3 — Writing Minimum Code: GREEN (2:15–3:45)
**Visual:** Opening `src/vlan_parser.py` and writing the minimum logic to pass:
```python
def parse_vlan_id(vlan_input: str) -> int:
    vlan_id = int(vlan_input)
    if 1 <= vlan_id <= 4094:
        return vlan_id
    raise ValueError(f"VLAN ID {vlan_id} out of range (1-4094)")
```
Terminal runs `python3 -m unittest`. Output:
`..`
`Ran 2 tests in 0.001s`
`OK` (Green).
**Narration:**
> Stage two is GREEN: write the simplest possible code to pass the test.
>
> We implement the function, run `python3 -m unittest`, and both tests pass in one millisecond.
>
> If anyone ever accidentally changes our validation logic in the future, this test will catch the regression instantly.

---

## Scene 4 — Refactor & Milestone 2 Guidance (3:45–5:00)
**Visual:** Refactoring with type annotations and docstrings. Reviewing Milestone 2 submission requirements.
**Narration:**
> Stage three is REFACTOR: clean up variable names, add type hints, and ensure documentation is crisp, knowing your unit tests will verify you didn't break functionality.
>
> For Milestone 2 this week, your pull request must include unit tests that validate normal, boundary, and error cases. Head to Section 3.8 to begin!
