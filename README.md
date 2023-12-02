#include<iostream>
using namespace std;

void BattleSystem();
int MonsterGen();
int PlayerHealth = 100;

string inventory[5] = { "flashlight", " ", " ", " ", " "};


void itemDropper();

int main() {
    srand(time(NULL));
    int room = 1;
    char input = 'a';
    int PlayerHealth = 100;
    //this sets each slot of inventory to " "
    //for (int i = 0; i < 10; i++) 
        //inventory[i] = " ";


    cout << "you wake up in a stone maze confused from the fall" << endl;



    while (input != 'q' && PlayerHealth >= 0) {

        cout << "your inventory:" << endl;
        for (int i = 0; i < 5; i++)
            cout << inventory[i] << " ";
        cout << endl;

        switch (room) {
        case 1:
            cout << "begin in a concreat dome with only one caged window , you can go (W)est" << endl;
            if (inventory[1] != "key")
                cout << "you see a shiny (k)ey on the ground." << endl;
            cin >> input;

            if (input == 'w')
                room = 2;
            if (input == 'k') {
                cout << "you got a shiny key!" << endl;
                inventory[1] = "key";
            }
            if (input == 'n') {
                cout << "you climb out the hole you fell throgh and leave" << endl;

            }
            break;
        case 2:
            cout << "thers is a locked door in your path. you can go (n)orth or (e)ast" << endl;
            cin >> input;
            if (input == 'n')
                if (inventory[1] == "key") {
                    room = 3;
                    cout << "the door is unlocked" << endl;
                }
            else 
                cout << "door is locked. you suck martin" << endl;



            if (input == 'e')
                room = 1;





            break;
        case 3:
            BattleSystem();
            cout << " you walk through the door before it shuts behind you. the only derection is forwerd. you can go (n)orth" << endl;
            cin >> input;
            if (input == 'n')
                room = 4;

            break;
        case 4:
            BattleSystem();
            cout << "you enter a room that has three doors, (r)ed, (b)lue, and (y)llow door" << endl;
            cin >> input;
            if (input == 'r')
                room = 5;
            if (input == 'b')
                room = 6;
            if (input == 'y')
                room = 7;

            break;
        case 5:
            cout << "you enter the red room. the room is dark and small. the red door shuts locking you inside. (n)orth is the only way now" << endl;
            cin >> input;
            if (input == 'n')
                room = 8;

            break;
        case 6:
            cout << "you you enter a bucher room with meat and rotton flesh on the walls and ground. there is a bundle of flesh tied togher making a door. you can go (w)est" << endl;
            cin >> input;
            if (input == 'w')
                room = 9;

            break;
        case 7:
            cout << "you enter a light room with grass and roots growing from the walls crack, a gecho climbs on your shoulder. (p)et and you can (e)ast" << endl;
            cin >> input;
            if (input == 'p')
                cout << "the gecko enjoys the pet" << endl;
            if (input == 'e')
                room = 10;

            break;
        case 8:
            cout << "you pull out your flash light and point it at a wall. there's writing on the wall and it spells out: subject 087 is coming. you can go (n)orth" << endl;

        }
    }
}


void BattleSystem() {
    int MonsterType = MonsterGen();
    int MonsterHealth = 20;
    int MonsterDmg = 0;
    int PlayerDmg = 0;

    if (MonsterType == 1) {
        MonsterHealth = 30;
    }
    if (MonsterType == 2) {
        MonsterHealth = 7;
    }

    if (MonsterType == 1) {
        MonsterDmg = rand() % 20 + 1;
    }

    if (MonsterType == 2) {
        MonsterDmg = rand() % 7 + 10;
    }

    if (MonsterType == 2) {
        MonsterDmg = rand() % 6 + 5;
    }


    while (MonsterHealth > 0 && PlayerHealth > 0) {

        //monster attacks player!
        if (inventory[1] == "sheild") {
            cout << "Your sheild parially blocks the DAVE. The DAVE bites you for " << MonsterDmg/2 << "HP" << endl;
            PlayerHealth -= MonsterDmg/2;
        }
        else {
            cout << "DAVE bites you " << MonsterDmg << "HP" << endl;
            PlayerHealth -= MonsterDmg;
        }


        //player attacks monster!
        if (inventory[0] == "sword") {
            PlayerDmg = rand() % 101;
        }
        else {
            PlayerDmg = rand() % 76;
        }
        //PlayerDmg /= 10;
        //if (inventory[0] == "sword")
        cout << "you attack the DAVE for " << PlayerDmg << " HP" << endl << endl;
        MonsterHealth -= PlayerDmg;
        system("pause");
        cout << "your health is now " << PlayerHealth << ", and the DAVE's health is " << MonsterHealth << endl;
        system("pause");

    }
    if (MonsterHealth <= 0)
        cout << "you stump on the dave" << endl;
    else
        cout << "you died from dave" << endl;


}



int MonsterGen() {
    int num = rand() % 100;
    if (num < 100) {
        cout << "" << endl;
        cout << "       _" << endl;
        cout << "      | |" << endl;
        cout << "    __| | __ ___   _____" << endl;
        cout << "A  / _` |/ _`\\ \\ / / _ \\"  << endl;
        cout << "  | (_| | (_||\\ V /  __/ " << endl;
        cout << "   \\__,_|\\__,_|\\_/ \\___|  appeared   " << endl;
        return 1;
    }
}
