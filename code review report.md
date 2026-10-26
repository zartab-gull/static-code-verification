# Code Review Report

| Line Number | Defect Type | Why It Is a Problem | Proposed Fix | Severity |
|---|---|---|---|---|
| 41–42 | Array Bounds | `spawnMonster()` does not check the maximum array capacity. Adding a sixth monster exceeds the array size. | Check `monsterCount < MAX_MONSTERS` before adding a monster. | High |
| 47 | Logical Error | The assignment operator `=` is used instead of the comparison operator `==`. | Replace `=` with `==`. | High |
| 55–56 | Arithmetic / Type Error | Unsigned damage can cause incorrect comparisons when health becomes negative. | Use signed integers and validate damage before subtraction. | High |
| 56 | Null Pointer | `findMonster()` may return `nullptr`, but `m->health` is accessed without checking. | Check whether `m == nullptr` before accessing health. | High |
| 64–65 | Array Bounds | The loop condition `i <= monsterCount` accesses an extra array element. | Change the condition to `i < monsterCount`. | High |
| 71–73 | Dangling Reference | The function returns a reference to a local string that is destroyed when the function ends. | Return `std::string` by value and check for a null pointer. | High |
| 77, 79 | Uninitialized Variable | `sum` is used without initialization, producing an indeterminate starting value. | Initialize it using `double sum = 0.0;`. | High |
| 80 | Division by Zero | `averageAttack()` divides by `monsterCount`, which may be zero. | Check for zero monsters before division and return an appropriate result. | Medium |
| 85–86 | Use-After-Free | The code accesses `m->name` after deleting `m`. | Print the name before deletion and remove the pointer from the array. | High |
| 91 | Arithmetic / Precision | Integer division may discard the fractional part of the damage calculation. | Use floating-point arithmetic, such as `attack * armorPercent / 100.0`. | Medium |
| 94–99 | Missing Return | `playerRank()` does not return a value when `score <= 100`. | Add a return statement for the remaining cases. | High |
| 102, 105, 109 | Buffer / Memory Management | The input can overflow the character buffer, and `delete` is used instead of `delete[]`. | Use `std::string` instead of a dynamically allocated character array. | High |
| 108 | Capacity / Input Validation | `readBoss()` can add a monster when the array is already full. | Check array capacity and validate input before spawning. | High |
| 121 | Memory Leak | The dynamically allocated `bonus` monster is never deleted. | Use automatic storage or `std::unique_ptr`. | Medium |
| 130 | Double Deletion | The deleted monster's pointer remains in the array, so the destructor may delete it again. | Remove the pointer from the array and update `monsterCount`. | Critical |
| 133 | Shallow Copy | `Game copy = game;` copies raw pointers, causing both objects to delete the same monsters. | Implement a deep copy or delete the copy constructor and copy assignment operator. | Critical |

