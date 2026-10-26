# Review Checklist

| Category | Result (Issue/OK) | Defect / Observation |
|---|---|---|
| Initialization | Issue | Variable `sum` is uninitialized, and array entries may contain uninitialized pointers. |
| Pointers | Issue | Null pointer dereference, dangling reference, use-after-delete, and memory leaks. |
| Arrays / Buffers | Issue | `monsterCount` is not checked against `MAX_MONSTERS`, causing possible array overflow. |
| Loops | Issue | `totalMonsterHealth()` uses `i <= monsterCount`, accessing an extra array element. |
| Arithmetic | Issue | Unsigned damage, integer division, and division-by-zero risks. |
| Control Flow | Issue | `playerRank()` does not return a value for every possible score. |
| Function Calls | Issue | Functions may dereference a null pointer when a monster is not found. |
| Classes / Memory Management | Issue | Shallow copying causes double deletion, and deleted objects are accessed. |
