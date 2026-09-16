
# EX 3D Sudoku solver - Backtracking.
## DATE: 15.09.2026
## AIM:
To write a Java program to solve a Sudoku puzzle by filling the empty cells.

For example:
<img width="357" height="322" alt="image" src="https://github.com/user-attachments/assets/334b8c39-d547-4743-aca0-de92e38bdd1c" />



## Algorithm
1. Start and find an empty cell (0) in the 9×9 Sudoku board.
2. Try placing numbers 1 to 9 in the empty cell.
3. Check whether the number is safe in its row, column, and 3×3 subgrid.
4. If safe, place the number and recursively solve the remaining cells; if it fails, remove the number (backtrack).
5. When all cells are filled successfully, return true and print the solved Sudoku; otherwise return false.

## Program:
```
/*
Program to implement Reverse a String
Developed by: TIMMAPURAM YOGEESWAR
Register Number:  212223230233
*/
import java.util.Scanner;

public class SudokuSolver {

    // Check if it's safe to place the number
    static boolean isSafe(int[][] board, int row, int col, int num) {
        // Check row and column
        for (int i = 0; i < 9; i++) {
            if (board[row][i] == num || board[i][col] == num)
                return false;
        }

        // Check 3x3 subgrid
        int startRow = row - row % 3;
        int startCol = col - col % 3;

        for (int i = 0; i < 3; i++)
            for (int j = 0; j < 3; j++)
                if (board[startRow + i][startCol + j] == num)
                    return false;

        return true;
    }

    // Recursive backtracking solver
    static boolean solveSudoku(int[][] board, int row, int col) {
        //Type your code here
        if(row==8 && col==9) return true;
        if(col==9){
            row++;
            col=0;
        }
        if(board[row][col]!=0) return solveSudoku(board,row,col+1);
        for(int num=1;num<=9;num++){
            if(isSafe(board,row,col,num)){
                board[row][col]=num;
                if(solveSudoku(board,row,col+1))
                  return true;
                board[row][col]=0;
        }
        }
    return false;
    }

    // Utility to print the board
    static void printBoard(int[][] board) {
        for (int[] row : board) {
            for (int val : row)
                System.out.print(val + " ");
            System.out.println();
        }
    }

    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        int[][] board = new int[9][9];

      //  System.out.println("Enter the Sudoku puzzle row by row (use 0 for empty cells):");

        for (int i = 0; i < 9; i++) {
            //System.out.print("Enter row " + (i + 1) + ": ");
            for (int j = 0; j < 9; j++) {
                board[i][j] = sc.nextInt();
            }
        }

      //  System.out.println("\nSolving...\n");

        if (solveSudoku(board, 0, 0)) {
            System.out.println("Solved Sudoku:");
            printBoard(board);
        } else {
            System.out.println("No solution exists.");
        }

        sc.close();
    }
}

```

## Output:
<img width="672" height="546" alt="image" src="https://github.com/user-attachments/assets/1dbed281-bbae-413c-90a5-d75e4335d3d7" />



## Result:
The program successfully implemented and the expected output is verified.
