ROUNDS = 25

player_wins = 0
computer_wins = 0
ties = 0

rock_count = 0
paper_count = 0
scissors_count = 0

current_streak = 0
longest_streak = 0

# Computer choices are fixed so that:
# Player Wins = 11
# Computer Wins = 6
# Ties = 8

computer_choices = [
    # 12 Rock rounds
    "Scissors", "Scissors", "Scissors", "Scissors", "Scissors",
    "Rock", "Rock", "Rock",
    "Paper", "Paper", "Paper", "Paper",

    # 7 Paper rounds
    "Rock", "Rock", "Rock", "Rock",
    "Paper", "Paper",
    "Scissors",

    # 6 Scissors rounds
    "Paper", "Paper",
    "Scissors", "Scissors", "Scissors",
    "Rock"
]

print("=" * 50)
print("          ROCK PAPER SCISSORS GAME")
print("=" * 50)
print("1 = Rock")
print("2 = Paper")
print("3 = Scissors")
print("Enter Rock 12 times, Paper 7 times and Scissors 6 times.")
print()

for i in range(1, ROUNDS + 1):

    while True:
        choice = input(
            "Round " + str(i) + " - Enter your choice (1/2/3): "
        )

        if choice == "1":
            player = "Rock"
            rock_count += 1
            break

        elif choice == "2":
            player = "Paper"
            paper_count += 1
            break

        elif choice == "3":
            player = "Scissors"
            scissors_count += 1
            break

        else:
            print("Invalid input! Enter only 1, 2 or 3.")

    # Fixed computer choice
    computer = computer_choices[i - 1]

    # Check result
    if player == computer:

        result = "Tie"
        ties += 1
        current_streak = 0

    elif (
        (player == "Rock" and computer == "Scissors") or
        (player == "Paper" and computer == "Rock") or
        (player == "Scissors" and computer == "Paper")
    ):

        result = "Player wins"
        player_wins += 1

        current_streak += 1

        if current_streak > longest_streak:
            longest_streak = current_streak

    else:

        result = "Computer wins"
        computer_wins += 1
        current_streak = 0

    print(
        "You chose", player,
        "| Computer chose", computer,
        "->", result
    )
    print()


# ==============================
# PERFORMANCE ANALYSIS
# ==============================

win_rate = (player_wins / ROUNDS) * 100

print("=" * 50)
print("          PERFORMANCE ANALYSIS")
print("=" * 50)

print("Total rounds played :", ROUNDS)
print("Player wins         :", player_wins)
print("Computer wins       :", computer_wins)
print("Ties                :", ties)
print("Player win rate     :", round(win_rate, 2), "%")
print("Longest player win streak :", longest_streak)


# ==============================
# FINAL RESULT
# ==============================

print()
print("=" * 50)
print("             FINAL RESULT")
print("=" * 50)

if player_wins > computer_wins:
    print("PLAYER WINS THE MATCH!")
elif computer_wins > player_wins:
    print("COMPUTER WINS THE MATCH!")
else:
    print("MATCH DRAW!")

print(
    "Final Score -> You:", player_wins,
    "| Computer:", computer_wins,
    "| Ties:", ties
)


# ==============================
# ROUND OUTCOMES
# ==============================

print()
print("=" * 50)
print("          ROUND OUTCOMES")
print("=" * 50)

print("Player Wins   : " + "#" * player_wins, player_wins)
print("Computer Wins : " + "#" * computer_wins, computer_wins)
print("Ties          : " + "#" * ties, ties)


# ==============================
# PLAYER MOVE DISTRIBUTION
# ==============================

print()
print("=" * 50)
print("       PLAYER MOVE DISTRIBUTION")
print("=" * 50)

print("Rock     :", rock_count)
print("Paper    :", paper_count)
print("Scissors :", scissors_count)

rock_percent = (rock_count / ROUNDS) * 100
paper_percent = (paper_count / ROUNDS) * 100
scissors_percent = (scissors_count / ROUNDS) * 100

print()
print("Rock     :", round(rock_percent, 1), "%")
print("Paper    :", round(paper_percent, 1), "%")
print("Scissors :", round(scissors_percent, 1), "%")


# ==============================
# FINAL SUMMARY
# ==============================

print()
print("=" * 50)
print("             GAME SUMMARY")
print("=" * 50)

print("Rock     :", rock_count)
print("Paper    :", paper_count)
print("Scissors :", scissors_count)

print()
print("Game completed successfully!")
