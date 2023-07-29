import java.util.*;
public class NumberGuessingGame {
    static ArrayList<Integer> scores = new ArrayList<Integer>();
    public static void main(String[] args) {
        NumberGuessingGame methodChange = new NumberGuessingGame();
        methodChange.menu(scores);
    }
    public void menu(ArrayList<Integer> scores) {
        NumberGuessingGame methodChange = new NumberGuessingGame();
        Scanner sc = new Scanner(System.in);
        System.out.println("*-*-*-*-*-*-*-*-*-*-*-*-*-*-*-*-*-*-*-*");
        System.out.println("HELLO! COMEON, LET'S START GUESSING!");
        System.out.println("1) Ready To Play!");
        System.out.println("2) My Scores");
        System.out.println("3) I'll Definitely Try Next Time");
        System.out.println("*-*-*-*-*-*-*-*-*-*-*-*-*-*-*-*-*-*-*-*");
        try {
            System.out.print("What Do You Wanna Do? (Choose 1, 2 Or 3) ");
            int menuOption = sc.nextInt();
            switch (menuOption) {
                case 1:
                    System.out.print("\n"+"Your End Range Number Would Be? ");
                    int numberRange = sc.nextInt();
                    int randomNumber = methodChange.randomNumber(numberRange);
                    methodChange.guessNumber(randomNumber);
                    break;
                case 2:
                    methodChange.displayScores();
                    break;
                case 3:
                    System.out.println("\n"+"Thankyou For Your Co-operation! Hope You Had Fun!");
                    System.exit(1);
                    break;
                default:
                    throw new InputMismatchException("Uh-Uh! A Little Careful With The Number Please!");
            }
        }catch(InputMismatchException e){
            System.err.println("\n"+e.getMessage() +"\n");
            menu(scores);
        }
    }
    public int randomNumber(int numberRange) {
        Random random = new Random();
        int randomNumber = random.nextInt(numberRange) + 1;
        return randomNumber;
    }
    public void guessNumber(int randomNumber) {
        Scanner sc = new Scanner(System.in);
        int userGuess;
        int guess = 0;
        do {
            System.out.print("Your Number : ");
            userGuess = sc.nextInt();
            guess++;
            if (userGuess > randomNumber) {
                System.out.println("A Little Lower And You're There!");
            } else if (userGuess < randomNumber) {
                System.out.println("A Little Higher, Come On!");
            }
        } while (randomNumber != userGuess);
        System.out.println(" ");
        if (guess == 1) {
            System.out.println("Wohoo! You Guessed That Right In The " + guess + " Try!");
        } else {
            System.out.println("Booyah! You Guessed That Right In " + guess + " Tries!");
        }
        scores.add(guess);
        System.out.println(" ");

        menu(scores);
    }
    public void displayScores() {
        System.out.println("--------------------");
        System.out.println("My Scores");
        System.out.println("--------------------");
        System.out.println("Lightening Speed In: " +"\n");
        Collections.sort(scores);
        for (Integer scores : scores) {
            System.out.println("Nailed The Game In " + scores + " Tries");
        }
        System.out.println(" ");
        menu(scores);
    }
}


ONLINE RESERVATION SYSTEM
import java.util.Scanner;
class OnlineReservationSystem 
{
private static boolean[] seat = new boolean[10];
public static void main(String[] args) 
{
    Scanner sc = new Scanner(System.in);
    while (true) 
    {
    System.out.println("*-*-*-*-*-*-*-*-*-*-*-*-*-*-*-*-*-*-*-*-*-*-*-*-*-*-*-*-*-*");
    System.out.println("1. Look At The Seating Arrangement");
    System.out.println("2. Let Me Reserve A Seat!");
    System.out.println("3. I Wanna Cancel The Reservation");
    System.out.println("4. Exit");
    System.out.println("*-*-*-*-*-*-*-*-*-*-*-*-*-*-*-*-*-*-*-*-*-*-*-*-*-*-*-*-*-*");
    System.out.println("Select Any ONE Option From The Above Given Options");
    System.out.println("I Choose : ");
    int option = sc.nextInt();
    switch (option) 
    {
    case 1:
        seatingArrangement();
        break;
    case 2:
        reserveASeat();
        break;
    case 3:
        cancelTheReservation();
        break;
    case 4:
        System.exit(0); // exit the program
    default:
        System.out.println("Uh-Oh, Let's Try Again!");
    }
    }
}
private static void seatingArrangement() 
{
    System.out.println("\nseatingArrangement :");
    for (int i = 0; i < seat.length; i++) 
    {
        if (seat[i]) 
        {
        System.out.print("X  ");
        } 
        else 
        {
        System.out.print(i+1+"  "); 
        }
    }
    System.out.println();
}
private static void reserveASeat() 
{
    Scanner sc = new Scanner(System.in);
    System.out.print("\nSelect Any Seat Number Between 1 to 10 : ");
    int seatNum = sc.nextInt();
    if (seatNum < 1 || seatNum > 10) 
    {
        System.out.println("Uh-Oh, Let's Try Again!");
    } 
    else if (seat[seatNum - 1]) 
    {
        System.out.println("Oops! This Seat Is Already Reserved, Sorry :( ");
    } 
    else 
    {
    seat[seatNum - 1] = true;
    System.out.println("Yay! This Seat Has Been Reserved By You!");
    }
}
private static void cancelTheReservation() 
{
    Scanner sc = new Scanner(System.in);
    System.out.print("\nSelect Any Seat Number between 1 to 10 : ");
    int seatNum = sc.nextInt();
    if (seatNum < 1 || seatNum > 10) 
    {
        System.out.println("Uh-Oh, Let's Try Again!");
    } 
    else if (!seat[seatNum - 1]) 
    {
        System.out.println("Oops, This Seat Is Unreserved!");
    } 
    else 
    {
    seat[seatNum - 1] = false;
    System.out.println("This Reservation Has Been Cancelled, Have A Good Day! :) ");
     }
 }
}
