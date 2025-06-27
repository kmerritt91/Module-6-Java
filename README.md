import java.util.InputMismatchException;
import java.util.Scanner;

public class Survey {
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);

        // different types of coffee stored in String array
        String[] coffeeTypes = {
                "dark roast coffee",
                "medium roast coffee",
                "light roast coffee",
                "french vanilla coffee",
                "caramel coffee"
        };

        // ratings for each coffee stored in integer array
        int[] ratings = new int[coffeeTypes.length];

        // Variable for total
        int total = 0;

        System.out.println("Please rate each coffee type from 1 (poor) to 5 (outstanding)\n");

        // Loop for each coffee type rating
        for (int i = 0; i < coffeeTypes.length; i++) {
            boolean validInput = false;

            while (!validInput) {

                // exception handling for invalid types
                try {
                    System.out.printf(
                            "What is your rating of the %s (1-poor, 2-fair, 3-good, 4-excellent, 5-outstanding)? ",
                            coffeeTypes[i]);
                    ratings[i] = scanner.nextInt();

                    // rating must be between 1 and 5
                    if (ratings[i] < 1 || ratings[i] > 5) {
                        System.out.println("Please enter a number between 1 and 5.");
                    } else {
                        validInput = true;
                        total += ratings[i];
                    }
                } catch (InputMismatchException e) {
                    System.out.println("Invalid input. Please enter a number between 1 and 5.");
                    scanner.next(); // Clear the invalid input
                }
            }
        }

        // Display stars for each rating
        System.out.println("\nYour ratings visualized:");
        for (int rating : ratings) {
            System.out.print(" ");
            for (int j = 0; j < rating; j++) {
                System.out.print("*");
            }
        }

        // Calculate and display average
        double average = (double) total / ratings.length;
        System.out.printf("\n\nYour average rating is %.1f\n", average);

        scanner.close();


