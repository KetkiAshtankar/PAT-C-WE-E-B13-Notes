

````markdown
# Rock, Paper, Scissors – Python Logic & Notes

## 1️⃣ Game Rules
- Rock beats Scissors 🪨✂
- Paper beats Rock 📄🪨
- Scissors beat Paper ✂📄
- Same choice → Tie 🤝

---

## 2️⃣ Representing Choices in Python
```python
options = ["rock", "paper", "scissors"]
````

* `"rock"` → index 0
* `"paper"` → index 1
* `"scissors"` → index 2

---

## 3️⃣ Winner Formula

Instead of multiple `if` checks, use:

```python
result = (user_index - computer_index) % 3
```

Where:

```python
user_index = options.index(user_choice)
computer_index = options.index(computer_choice)
```

---

## 4️⃣ Formula Logic Table

| User vs Computer     | Calculation | Result | Outcome |
| -------------------- | ----------- | ------ | ------- |
| Rock vs Rock         | (0-0) % 3=0 | 0      | Tie     |
| Rock vs Paper        | (0-1) % 3=2 | 2      | Lose    |
| Rock vs Scissors     | (0-2) % 3=1 | 1      | Win     |
| Paper vs Rock        | (1-0) % 3=1 | 1      | Win     |
| Paper vs Paper       | (1-1) % 3=0 | 0      | Tie     |
| Paper vs Scissors    | (1-2) % 3=2 | 2      | Lose    |
| Scissors vs Rock     | (2-0) % 3=2 | 2      | Lose    |
| Scissors vs Paper    | (2-1) % 3=1 | 1      | Win     |
| Scissors vs Scissors | (2-2) % 3=0 | 0      | Tie     |

---

## 5️⃣ Modulo Magic

Example:

```
(0 - 1) % 3 = -1 % 3 = 2
```

* Python `%` always returns a **non-negative remainder**
* Think of `% 3` as moving around a **3-position circle**:

  * 0 → Rock
  * 1 → Paper
  * 2 → Scissors

---

## 6️⃣ Final Code

```python
import random

options = ["rock", "paper", "scissors"]

while True:
    user_choice = input("Enter rock, paper, or scissors (or 'exit' to stop): ").lower()
    if user_choice == "exit":
        break
    if user_choice not in options:
        print("Invalid choice, try again.")
        continue

    computer_choice = random.choice(options)
    print(f"Computer chose: {computer_choice}")

    result = (options.index(user_choice) - options.index(computer_choice)) % 3

    if result == 0:
        print("It's a tie!")
    elif result == 1:
        print("You win!")
    else:
        print("You lose!")
```

---

## 7️⃣ Cheat Code Summary

* **Tie** → `(user - comp) % 3 == 0`
* **User Wins** → `(user - comp) % 3 == 1`
* **User Loses** → `(user - comp) % 3 == 2`

---

💡 **Tip for Memory**:
Think clockwise around a circle:
Rock → Scissors → Paper → Rock
Moving 1 step forward = win ✅, moving 2 steps forward = lose ❌

````

