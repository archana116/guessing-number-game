# guessing-number-game
import java.util.Scanner;
import java.util.Random;

public class Main {
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        Random random = new Random();
        
        int minRange = 1;
        int maxRange = 100;
        int attempts = 0;
        int score = 0;
        
        System.out.println("Welcome to the Number Guessing Game!");
       
        
        boolean playAgain = true;
        
        while (playAgain) {
            int targetNumber = random.nextInt(maxRange - minRange + 1) + minRange;
            int guess;
            int maxAttempts = 10;  // You can adjust this value.
            
            System.out.println("Round " + (score + 1));
            
            while (attempts < maxAttempts) {
                System.out.print("Enter your guess: ");
                guess = scanner.nextInt();
                attempts++;
                
                if (guess < minRange || guess > maxRange) {
                    System.out.println("Your guess is out of the valid range.");
                } else if (guess == targetNumber) {
                    System.out.println("Congratulations! You've guessed the correct number in " + attempts + " attempts.");
                    score++;
                    break;
                } else if (guess < targetNumber) {
                    System.out.println("Try a higher number.");
                } else {
                    System.out.println("Try a lower number.");
                }
                
                if (attempts == maxAttempts) {
                    System.out.println("Sorry, you've reached the maximum number of attempts. The correct number was " + targetNumber);
                }
            }
            
            System.out.print("Do you want to play again? (yes/no): ");
            String playAgainResponse = scanner.next();
            if (!playAgainResponse.equalsIgnoreCase("yes")) {
                playAgain = false;
            }
            
            attempts = 0;
        }
        
        System.out.println("Game over! Your total score is: " + score);
        scanner.close();
    }
}
