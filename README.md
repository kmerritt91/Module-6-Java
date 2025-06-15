import java.util.Scanner;

public class CoffeeSurvey {

    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        
        // Questions to ask
        String[] questions = {
            "What is your rating of the dark roast coffee (1-poor, 2-fair, 3-good, 4-excellent, 5-outstanding)?",
            "What is your rating of the medium roast coffee (1-poor, 2-fair, 3-good, 4-excellent, 5-outstanding)?",
            "What is your rating of the light roast coffee (1-poor, 2-fair, 3-good, 4-excellent, 5-outstanding)?",
            "What is your rating of the french vanilla coffee (1-poor, 2-fair, 3-good, 4-excellent, 5-outstanding)?",
            "What is your rating of the caramel coffee (1-poor, 2-fair, 3-good, 4-excellent, 5-outstanding)?"
        };
        
        int[] ratings = new int[5];
        int totalScore = 0;
        
        // Loop through each question and collect ratings
        for (int i = 0; i < questions.length; i++) {
            int rating = -1;
            boolean validInput = false;
            
            // Ensure valid input is entered
            while (!validInput) {
                try {
                    System.out.println(questions[i]);
                    System.out.print("Please enter a rating (1-5): ");
                    rating = Integer.parseInt(scanner.nextLine());
                    
                    // Check if the rating is within valid range
                    if (rating >= 1 && rating <= 5) {
                        validInput = true;
                        ratings[i] = rating;
                        totalScore += rating;
                    } else {
                        System.out.println("Invalid input. Please enter a rating between 1 and 5.");
                    }
                } catch (NumberFormatException e) {
                    System.out.println("Invalid input. Please enter a numeric value between 1 and 5.");
                }
            }
        }
        
        // Display the stars for each rating
        System.out.println("\nSurvey Results:");
        for (int i = 0; i < ratings.length; i++) {
            System.out.print("Rating for question " + (i + 1) + ": ");
            for (int j = 0; j < ratings[i]; j++) {
                System.out.print("*");
            }
            System.out.println();
        }
        
        // Calculate and display the average rating
        double averageRating = totalScore / 5.0;
        System.out.printf("\nYour average rating is %.1f\n", averageRating);
        
        scanner.close();
    }
}
