#include <iostream>
#include <string>

class Character {
public:
    // Constructor to initialize the character
    Character(std::string name, int health, int attack) 
        : name(name), health(health), attack(attack) {}

    // Method to display character information
    void displayInfo() {
        std::cout << "Name: " << name << std::endl;
        std::cout << "Health: " << health << std::endl;
        std::cout << "Attack: " << attack << std::endl;
    }

    // Method to make the character attack another character
    void attackCharacter(Character& otherCharacter) {
        std::cout << name << " attacks " << otherCharacter.getName() << " for " << attack << " damage!" << std::endl;
        otherCharacter.takeDamage(attack);
    }

    // Method to take damage
    void takeDamage(int damage) {
        health -= damage;
        if (health < 0) {
            health = 0;
        }
    }

    // Getter method for character's name
    std::string getName() const {
        return name;
    }

private:
    std::string name;
    int health;
    int attack;
};

int main() {
    // Create two character objects
    Character hero("Hero", 100, 20);
    Character enemy("Enemy", 80, 15);

    // Display character information
    std::cout << "Character Information:" << std::endl;
    hero.displayInfo();
    enemy.displayInfo();

    // Make characters attack each other
    hero.attackCharacter(enemy);
    enemy.attackCharacter(hero);

    // Display updated character information
    std::cout << "\nUpdated Character Information:" << std::endl;
    hero.displayInfo();
    enemy.displayInfo();

    return 0;
}
