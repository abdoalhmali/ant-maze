#include <iostream>
using namespace std;

class AntMaze {
private:
    // # = wall, F = flooded cell, . = free cell, X = food
    char maze[5][6] = {
        "....X",
        "#F###",
        ".F...",
        "#F#.#",
        ".F..."
    };

    int row, col;
    int cost;

public:
    AntMaze() {
        row = 4;
        col = 0;
        cost = 0;
    }

    bool validCell(int r, int c) {
        if (r < 0 || r >= 5 || c < 0 || c >= 5)
            return false;
        return maze[r][c] != '#';
    }

    void setStart(int r, int c) {
        if (validCell(r, c)) {
            row = r;
            col = c;
            cost = 0;
        } else {
            cout << "Invalid start: wall or outside the maze.\n";
        }
    }

    void showMaze() {
        cout << "\nMaze (A = ant):\n";
        for (int i = 0; i < 5; i++) {
            for (int j = 0; j < 5; j++) {
                if (i == row && j == col)
                    cout << "A ";
                else
                    cout << maze[i][j] << ' ';
            }
            cout << '\n';
        }
        cout << "Cost = " << cost << "\n";
    }

    bool atGoal() {
        return maze[row][col] == 'X';
    }

    void moveAnt(char direction) {
        int newRow = row;
        int newCol = col;

        if (direction == 'U' || direction == 'u') newRow--;
        else if (direction == 'D' || direction == 'd') newRow++;
        else if (direction == 'L' || direction == 'l') newCol--;
        else if (direction == 'R' || direction == 'r') newCol++;
        else if (direction == 'S' || direction == 's') {
            cost++;   // Staying in place also costs 1
            return;
        } else {
            cout << "Unknown command.\n";
            return;
        }

        if (validCell(newRow, newCol)) {
            row = newRow;
            col = newCol;
            cost++;
        } else {
            cout << "Cannot move: wall or outside the maze.\n";
        }
    }
};

int main() {
    AntMaze game;
    int startRow, startCol;
    char direction;

    cout << "Ant in a Flooded Maze\n";
    cout << "Rows and columns are from 0 to 4.\n";
    cout << "Enter start row and column: ";
    cin >> startRow >> startCol;
    game.setStart(startRow, startCol);

    while (true) {
        game.showMaze();
        if (game.atGoal()) {
            cout << "The ant found the food!\n";
            break;
        }

        cout << "Move U/D/L/R, S = stay, Q = quit: ";
        cin >> direction;
        if (direction == 'Q' || direction == 'q') break;
        game.moveAnt(direction);
    }
    return 0;
}
