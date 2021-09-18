# Tic-Tac-Toe-_Game
Game (java)

import java.util.Arrays;
import java.util.InputMismatchException;
import java.util.Scanner;

public class GFG {

   static String board[]=new String[9];
    static String turn;
    
        public static void main(String[] args) {
             Scanner a=new Scanner(System.in);
             turn ="X";
            String winner=checkWinner();
        for(int i=0;i<9;i++)
            board[i]=String.valueOf(i+1);

        System.out.println("Welcome to Tic Tac Toe!!!");
        System.out.println("Let's begin the GAME.....");
        pBoard();
        
        System.out.println("Enter a slot Number for X : ");
        while(winner==null){
            int input;
            input=a.nextInt();
            try{
                //input=a.nextInt();
                if(input<=0&&input>9){
                    System.out.print("Input Not-Valid...RE-ENTER slot number : ");
                continue;
                }
            }
            catch(InputMismatchException e){
               // System.out.print("Input Not-Valid...RE-ENTER slot number : ");
               // continue;
            }
           // if(board[input-1].equals(String.valueOf(input)))
                 
                
           if(board[input-1].equalsIgnoreCase(String.valueOf(input))){
            
                board[input-1]=turn;
                if(turn=="X")
                    turn="O";
                else 
                    turn="X";
            
            pBoard();
            winner=checkWinner();
            }
            else{
                System.out.println("Slot already taken..RE-ENTER again...");
            }
            if(winner.equalsIgnoreCase("draw"))
                System.out.println(
                "It's a draw! Thanks for playing.");
            else{
                System.out.println(
                "Congratulations! " + winner
                + "'s have won! Thanks for playing.");
            }
        }

       
        
    }
    public static void pBoard(){
                 System.out.println("|---|---|---|");
              System.out.println("| "+board[0]+" | "+board[1]+" | "+board[2]+" |");
                 System.out.println("|---|---|---|");
              System.out.println("| "+board[3]+" | "+board[4]+" | "+board[5]+" |");
                 System.out.println("|---|---|---|");
              System.out.println("| "+board[6]+" | "+board[7]+" | "+board[8]+" |");
                 System.out.println("|---|---|---|");
    }
    static String checkWinner(){
        for(int a=0;a<8;a++){
            String line=null;
            
            switch(a){
                case 0:
                    line=board[0]+board[1]+board[2];
                    break;
                case 1:
                    line=board[3]+board[4]+board[5];
                    break;
                case 2:
                    line=board[6]+board[7]+board[8];
                    break;
                case 3:
                    line=board[0]+board[3]+board[6];
                    break;
                case 4:
                    line=board[1]+board[4]+board[7];
                    break;
                case 5:
                    line=board[2]+board[5]+board[8];
                    break;
                case 6:
                    line=board[0]+board[4]+board[8];
                    break;
                case 7:
                    line=board[2]+board[4]+board[6];
                    break;
            }
            if(line.equals("XXX"))
                return "X";
            else if(line.equals("OOO"))
                return "O";
        }
        for(int i=0;i<9;i++)
        {
            if(Arrays.asList(board).contains(String.valueOf(i+1)))
                break;
            else if(i==8)
                return "draw";
        }
         System.out.println(turn + "'s turn; enter a slot number to place "+ turn + " in:");
         return null;
    }
}
