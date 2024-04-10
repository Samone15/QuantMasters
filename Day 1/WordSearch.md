## Word Find

In word find puzzle, the player is asked to find each of a given set of words in a square table filled with single letters. A word can read horizontally 
(left or right), vertically (up or down), or along a 45 degree diagonal (in any of the four directions) formed by consecutively adjacent cells of the table; 
it may wrap around the table’s boundaries, but it must read in the same direction with no zigzagging. The same cell of the table may be used in different words, but,
in a given word, the same cell may be used no more than once. 
Write a program to read the character 2d array (representing square table) and a string, print true if string is present and false if not




```java
import java.util.*;


class Practice{
    static char matrix[][];
    static int res[] = new int[2];
    static int directions[][] = {{1, 0},{-1, 0}, {0, 1},{0, -1}, {1, 1}, {-1, -1}, {1, -1}, {-1, 1}};

    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);

        int n = sc.nextInt();
        int m = sc.nextInt();
        sc.nextLine();

        matrix= new char[n][m];
        for(int i=0; i<n; i++){
            for(int j=0; j<m; j++){
                matrix[i][j] = sc.next().charAt(0);
            }
        }
        sc.nextLine();
    
        String word = sc.nextLine();
        boolean ans = search(word.toCharArray());
        if(!ans){
            System.out.println("WORD NOT FOUND");
        }else{
            System.out.println("WORD STARTS FROM " + res[0] + " ROw AND " + res[1] + " COL.");
        }
        sc.close();
    }

    public static boolean search(char[] word){
        int len = word.length;
        int n = matrix.length, m = matrix[0].length;
        if(len > n && len > m){
            return false;
        }

        for(int i=0; i<n; i++){
            for(int j=0; j<m; j++){
                if(matrix[i][j] == word[0]){
                    for(int[] direction: directions){
                        int dx = direction[0];
                        int dy = direction[1];
                        int x = i;
                        int y = j;
                        int k;
                        for(k=1; k<len; k++){
                            x = (x + dx + n) % n; //Wrapping around condition
                            y = (y + dy + m) % m; //Wrapping around condition
                            if(matrix[x][y] != word[k]){
                                break;
                            }
                        }
                        if(k == len){
                            res[0] = i;
                            res[1] = j;
                            return true;
                        }
                    }
                }
            }
        }
        return false;
    }
}```
