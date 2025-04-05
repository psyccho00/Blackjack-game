# 🃏 Blackjack Game

Welcome to the **Blackjack Game** – a simple yet engaging terminal-based card game built with Python. This game lets you test your luck and strategy against a computerized dealer using the classic rules of Blackjack (also known as 21).

---

## 📂 Repository Contents

- `main.py` – The heart of the game, containing all core logic and gameplay.
- `art.py` – Stores ASCII art to enhance the visual appeal in the terminal.

---

## 🎮 Gameplay Overview

Blackjack is a card game where the goal is to get your hand’s value as close to 21 as possible without going over. You play against a dealer (computer), drawing cards and deciding when to stop ("stand") or continue ("hit").

- Aces can be worth 11 or 1.
- Face cards are worth 10.
- Blackjack = Ace + 10-value card (in 2 cards).

---

## 🚀 Getting Started

### 🔧 Requirements

- Python 3.x

### ▶️ How to Run

```bash
git clone https://github.com/psyccho00/Blackjack-game.git
cd Blackjack-game
python main.py
```

---

## 🧠 Code Breakdown

Let’s dive into each file and its responsibilities.

---

### 📄 `art.py` – Visual Flair

```python
logo = r"""
.------.            _     _            _    _            _    
|A_  _ |.          | |   | |          | |  (_)          | |   
|( \/ ).-----.     | |__ | | __ _  ___| | ___  __ _  ___| | __
| \  /|K /\  |     | '_ \| |/ _` |/ __| |/ / |/ _` |/ __| |/ /
|  \/ | /  \ |     | |_) | | (_| | (__|   <| | (_| | (__|   < 
`-----| \  / |     |_.__/|_|\__,_|\___|_|\_\ |\__,_|\___|_|\_\\
      |  \/ K|                            _/ |                
      `------'                           |__/           
"""
```

---

### 📄 `main.py` – Game Logic

#### ✅ Imports

```python
import random
from art import logo
```

---

#### 🃏 `deal_card()` – Draw a Card

```python
def deal_card():
    cards = [11, 2, 3, 4, 5, 6, 7, 8, 9, 10, 10, 10, 10]
    return random.choice(cards)
```

---

#### 🧮 `calculate_score(cards)` – Hand Value Logic

```python
def calculate_score(cards):
    if sum(cards) == 21 and len(cards) == 2:
        return 0  # Blackjack
    if 11 in cards and sum(cards) > 21:
        cards.remove(11)
        cards.append(1)
    return sum(cards)
```

---

#### ⚖️ `compare(user_score, computer_score)` – Decide the Winner

```python
def compare(user_score, computer_score):
    if user_score == computer_score:
        return "Draw 🙃"
    elif computer_score == 0:
        return "Lose, opponent has Blackjack 😱"
    elif user_score == 0:
        return "Win with a Blackjack 😎"
    elif user_score > 21:
        return "You went over. You lose 😭"
    elif computer_score > 21:
        return "Opponent went over. You win 😁"
    elif user_score > computer_score:
        return "You win 😃"
    else:
        return "You lose 😤"
```

---

#### 🔁 `play_game()` – The Main Game Loop

```python
def play_game():
    print(logo)
    user_cards = []
    computer_cards = []
    is_game_over = False

    for _ in range(2):
        user_cards.append(deal_card())
        computer_cards.append(deal_card())

    while not is_game_over:
        user_score = calculate_score(user_cards)
        computer_score = calculate_score(computer_cards)
        print(f"   Your cards: {user_cards}, current score: {user_score}")
        print(f"   Computer's first card: {computer_cards[0]}")

        if user_score == 0 or computer_score == 0 or user_score > 21:
            is_game_over = True
        else:
            user_should_deal = input("Type 'y' to get another card, type 'n' to pass: ")
            if user_should_deal == "y":
                user_cards.append(deal_card())
            else:
                is_game_over = True

    while computer_score != 0 and computer_score < 17:
        computer_cards.append(deal_card())
        computer_score = calculate_score(computer_cards)

    print(f"   Your final hand: {user_cards}, final score: {user_score}")
    print(f"   Computer's final hand: {computer_cards}, final score: {computer_score}")
    print(compare(user_score, computer_score))
```

---

#### 🎮 Loop to Play Again

```python
while input("Do you want to play a game of Blackjack? Type 'y' or 'n': ") == "y":
    play_game()
```

---

## 📜 Game Rules Summary

- You start with two cards.
- Type `y` to draw another card ("Hit") or `n` to hold ("Stand").
- Dealer draws until their score is 17 or higher.
- Try to get closer to 21 than the dealer without going over.

---

## 🌟 Features

- 💡 Dynamic Ace handling (11 or 1)
- 🎨 ASCII logo for aesthetics
- 🔁 Replayability
- 🧠 Dealer logic with realistic Blackjack rules
- 👀 Clear terminal-based UI

---

## 🤝 Acknowledgments

- Inspired by classic casino-style Blackjack.
- Built using core Python concepts: functions, conditionals, loops, and lists.

---

## 📌 Future Enhancements

- ✅ Multi-player mode
- ✅ Betting system
- ✅ Score tracking across games

---


## 👨‍💻 Author

Developed by [psyccho00](https://github.com/psyccho00)

---
