
import random

class Character:
    def __init__(self, name, health, attack_power):
        self.name = name
        self.health = health
        self.attack_power = attack_power

    def is_alive(self):
        return self.health > 0

    def attack(self, other):
        damage = random.randint(1, self.attack_power)
        other.health -= damage
        print(f"{self.name} attacks {other.name} for {damage} damage!")

def fighting_game():
    player = Character("Player", 100, 20)
    enemy = Character("Enemy", 100, 15)

    print("Let the battle begin!")
    print(f"{player.name}: {player.health} HP")
    print(f"{enemy.name}: {enemy.health} HP")

    while player.is_alive() and enemy.is_alive():
        # Player's turn
        input("Press Enter to attack!")
        player.attack(enemy)
        print(f"{player.name}: {player.health} HP")
        print(f"{enemy.name}: {enemy.health} HP")

        if not enemy.is_alive():
            print("You defeated the enemy! Congratulations!")
            return

        # Enemy's turn
        enemy.attack(player)
        print(f"{player.name}: {player.health} HP")
        print(f"{enemy.name}: {enemy.health} HP")

        if not player.is_alive():
            print("You were defeated! Game over.")
            return

fighting_game()
