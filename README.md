import java.util.Random;
import java.util.Scanner;

public class GuessingGame {
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        Random random = new Random();
        int min = 1;
        int max = 100;
        int maxAttempts = 10;
        boolean playAgain = true;
        int totalRounds = 0;
        int totalAttempts = 0;

        System.out.println("Welcome to the Guessing Game!");

        while (playAgain) {
            int targetNumber = random.nextInt(max - min + 1) + min;
            int attempts = 0;
            boolean guessedCorrectly = false;

            System.out.println("\nA new number has been generated! Try to guess the number between " + min + " and " + max + ".");

            while (attempts < maxAttempts && !guessedCorrectly) {
                System.out.print("Enter your guess: ");
                int userGuess = scanner.nextInt();
                attempts++;

                if (userGuess == targetNumber) {
                    guessedCorrectly = true;
                    System.out.println("Congratulations! You've guessed the correct number.");
                } else if (userGuess < targetNumber) {
                    System.out.println("Too low! Try again.");
                } else {
                    System.out.println("Too high! Try again.");
                }
            }

            if (!guessedCorrectly) {
                System.out.println("You've used all your attempts. The correct number was " + targetNumber + ".");
            }

            totalRounds++;
            totalAttempts += attempts;

            System.out.print("Do you want to play again? (yes/no): ");
            String response = scanner.next();
            playAgain = response.equalsIgnoreCase("yes");
        }

        System.out.println("\nGame Over! You've played " + totalRounds + " rounds.");
        System.out.println("Your total attempts: " + totalAttempts);
        System.out.println("Your average attempts per round: " + (double) totalAttempts / totalRounds);

        scanner.close();
    }
}
