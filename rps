import random
import colorama
from colorama import Fore, Back, Style
colorama.init(autoreset=True)


class Computer:
    moves = ['rock', 'paper', 'scissors']

    def __init__(self):
        self.my_move = self.moves
        self.their_move = self.moves

    def learn(self, my_move, their_move):
        self.my_move = my_move
        self.their_move = their_move


class RandomComputer(Computer):
    def move(self):
        return random.choice(self.moves)


class RockComputer(Computer):
    def move(self):
        return 'rock'


class ImitateComputer(Computer):
    def move(self):
        return self.their_move


class CycleComputer(Computer):
    def move(self):
        if self.my_move == self.moves[0]:
            return self.moves[1]
        elif self.my_move == self.moves[1]:
            return self.moves[2]
        else:
            return self.moves[0]


class Player(Computer):

    def move(self):
        while True:
            user_action = input("Enter a choice (rock, paper, scissors): ")
            if user_action.lower() in self.moves:
                return user_action.lower()


class Game:
    def __init__(self, p1, p2):
        self.p1 = p1
        self.p2 = p2
        self.score_p1 = 0
        self.score_p2 = 0

    def beats(self, one, two):
        return ((one == 'rock' and two == 'scissors') or
                (one == 'scissors' and two == 'paper') or
                (one == 'paper' and two == 'rock'))

    def play_round(self):
        user_action = self.p1.move()
        move2 = self.p2.move()

        if self.beats(user_action, move2):
            self.score_p1 += 1
            print("")
            print(Fore.GREEN + "\t""PLAYER WINS")
        elif user_action == move2:
            self.score_p1 = self.score_p1
            self.score_p2 = self.score_p2
            print("")
            print(Fore.CYAN + "\t""It's TIE")
        else:
            self.score_p2 += 1
            print("")
            print(Fore.RED + "\t""Computer WINS")

        print(f"Player chose: {user_action}  Computer chose: {move2}")

        if self.beats(user_action, move2):
            print("\t"f"{user_action} beats {move2}")
        elif user_action == move2:
            print("")
        else:
            print("\t"f"{move2} beats {user_action}")

        print("")
        print(f"Player ( {self.score_p1} ),     Computer( {self.score_p2} )")

        self.p1.learn(user_action, move2)
        self.p2.learn(move2, user_action)

    def play_game(self):
        print("")
        print(Fore.CYAN + "\t""Let's play a Game!")
        print(Fore.CYAN + "\t""There are 5 rounds!")
        for round in range(1, 6):
            print("")
            print(f"Round {round}:")
            self.play_round()
        if self.score_p1 == self.score_p2:
            print("")
            print("\t""Final Score")
            print(Fore.CYAN + "\t""It's a Tie!")
            print(f"Player ( {self.score_p1} wins),"
                  f"Computer ( {self.score_p2} wins)")
        elif self.score_p1 > self.score_p2:
            print("")
            print("\t""Final Score")
            print(Fore.GREEN + "\t""Player won!")
            print(f"Player ( {self.score_p1} wins),"
                  f"Computer ( {self.score_p2} wins)")
        else:
            print("")
            print("\t""Final Score")
            print(Fore.RED + "\t""You LOSE!")
            print(f"Score: Player( {self.score_p1} wins), "
                  f"Computer two ( {self.score_p2} wins)*"
            )
        print("")
        print("\t""Game over!")


if __name__ == '__main__':
    game = Game(Player(), RandomComputer())
    game.play_game()
