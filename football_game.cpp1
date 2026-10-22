#include <iostream>
#include <string>
#include <cstdlib>
#include <ctime>

using namespace std;

// Function declarations
void displayScoreboard(const string& team1, int score1, const string& team2, int score2);
int playTurn(const string& teamName);

int main() {
    srand(static_cast<unsigned int>(time(0)));

    string team1, team2;
    int score1 = 0, score2 = 0;
    const int WINNING_SCORE = 21;

    cout << "==========================================" << endl;
    cout << "     WELCOME TO C++ FOOTBALL SIMULATOR    " << endl;
    cout << "==========================================" << endl;

    cout << "Enter Name for Team 1: ";
    getline(cin, team1);
    cout << "Enter Name for Team 2: ";
    getline(cin, team2);

    cout << "\nGame On! First team to reach " << WINNING_SCORE << " points wins!\n" << endl;

    int quarter = 1;
    while (score1 < WINNING_SCORE && score2 < WINNING_SCORE) {
        cout << "--- Possession Phase " << quarter << " ---" << endl;

        // Team 1 Possession
        score1 += playTurn(team1);
        displayScoreboard(team1, score1, team2, score2);

        if (score1 >= WINNING_SCORE) break;

        // Team 2 Possession
        score2 += playTurn(team2);
        displayScoreboard(team1, score1, team2, score2);

        quarter++;
        cout << "Press ENTER to continue to the next play...";
        cin.get();
        cout << endl;
    }

    // Final Result
    cout << "==========================================" << endl;
    cout << "               GAME OVER!                 " << endl;
    cout << "==========================================" << endl;
    if (score1 >= WINNING_SCORE) {
        cout << "CONGRATULATIONS! " << team1 << " WINS WITH " << score1 << " POINTS!" << endl;
    } else {
        cout << "CONGRATULATIONS! " << team2 << " WINS WITH " << score2 << " POINTS!" << endl;
    }

    return 0;
}

void displayScoreboard(const string& team1, int score1, const string& team2, int score2) {
    cout << "\n------------------------------------------" << endl;
    cout << " SCOREBOARD: " << team1 << ": " << score1 << "  |  " << team2 << ": " << score2 << endl;
    cout << "------------------------------------------\n" << endl;
}

int playTurn(const string& teamName) {
    cout << teamName << " is on offense! Choose your play call:" << endl;
    cout << "  1. Touchdown Drive (High Risk, High Reward)" << endl;
    cout << "  2. Field Goal Attempt (Low Risk, Safe Points)" << endl;
    cout << "Select play (1 or 2): ";

    int choice = 0;
    cin >> choice;
    cin.ignore(); // Clear newline buffer

    int pointsEarned = 0;
    int outcome = rand() % 100; // Generate random number between 0 and 99

    if (choice == 1) {
        if (outcome < 55) { // 55% success rate
            cout << "-> TOUCHDOWN! " << teamName << " scores 7 points!" << endl;
            pointsEarned = 7;
        } else {
            cout << "-> TURNOVER! " << teamName << " failed to convert." << endl;
            pointsEarned = 0;
        }
    } else if (choice == 2) {
        if (outcome < 85) { // 85% success rate
            cout << "-> FIELD GOAL GOOD! " << teamName << " scores 3 points!" << endl;
            pointsEarned = 3;
        } else {
            cout << "-> MISSED FIELD GOAL! No points awarded." << endl;
            pointsEarned = 0;
        }
    } else {
        cout << "-> INVALID PLAY CALL! Turn wasted (0 points)." << endl;
        pointsEarned = 0;
    }

    return pointsEarned;
}
