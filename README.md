# Rock-Paper-and-Scissor
An game built in java

_______________________________________________

import java.util.Random;
import java.util.Scanner;

public class RockPaperScissors {

    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        Random random = new Random();
        
        String[] choices = {"Rock", "Paper", "Scissors"};
        String playAgain;

        do {
            System.out.println("Enter your choice (Rock, Paper, Scissors): ");
            String userChoice = scanner.nextLine().trim();

            // Validate user input
            if (!isValidChoice(userChoice, choices)) {
                System.out.println("Invalid choice. Please try again.");
                continue;
            }

            // Computer's choice
            int computerIndex = random.nextInt(3);
            String computerChoice = choices[computerIndex];
            System.out.println("Computer chose: " + computerChoice);

            // Determine the winner
            String result = determineWinner(userChoice, computerChoice);
            System.out.println(result);

            // Ask if the user wants to play again
            System.out.println("Do you want to play again? (yes/no): ");
            playAgain = scanner.nextLine().trim().toLowerCase();

        } while (playAgain.equals("yes"));

        System.out.println("Thank you for playing!");
        scanner.close();
    }

    private static boolean isValidChoice(String choice, String[] validChoices) {
        for (String validChoice : validChoices) {
            if (validChoice.equalsIgnoreCase(choice)) {
                return true;
            }
        }
        return false;
    }

    private static String determineWinner(String userChoice, String computerChoice) {
        if (userChoice.equalsIgnoreCase(computerChoice)) {
            return "It's a tie!";
        } else if ((userChoice.equalsIgnoreCase("Rock") && computerChoice.equals("Scissors")) ||
                   (userChoice.equalsIgnoreCase("Paper") && computerChoice.equals("Rock")) ||
                   (userChoice.equalsIgnoreCase("Scissors") && computerChoice.equals("Paper"))) {
            return "You win!";
        } else {
            return "You lose!";
        }
    }
}