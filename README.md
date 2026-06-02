# Quiz-Application
Quiz Application
import java.util.Scanner;

class Question {
    String question;
    String[] options;
    int correctAnswer;

    public Question(String question, String[] options, int correctAnswer) {
        this.question = question;
        this.options = options;
        this.correctAnswer = correctAnswer;
    }

    public boolean askQuestion(Scanner sc) {
        System.out.println("\n" + question);

        for (int i = 0; i < options.length; i++) {
            System.out.println((i + 1) + ". " + options[i]);
        }

        System.out.print("Enter your answer (1-4): ");
        int answer = sc.nextInt();

        return answer == correctAnswer;
    }
}

public class QuizApplication {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);

        Question[] questions = {
            new Question(
                "What is the capital of India?",
                new String[]{"Mumbai", "Delhi", "Kolkata", "Chennai"},
                2
            ),
            new Question(
                "Which language is used for Android development?",
                new String[]{"Python", "C++", "Java", "PHP"},
                3
            ),
            new Question(
                "Who is known as the Father of Computers?",
                new String[]{"Charles Babbage", "Newton", "Einstein", "Tesla"},
                1
            ),
            new Question(
                "Which keyword is used to inherit a class in Java?",
                new String[]{"implements", "extends", "inherits", "super"},
                2
            ),
            new Question(
                "Which planet is known as the Red Planet?",
                new String[]{"Earth", "Mars", "Venus", "Jupiter"},
                2
            )
        };

        int score = 0;

        System.out.println("===== QUIZ APPLICATION =====");

        for (Question q : questions) {
            if (q.askQuestion(sc)) {
                System.out.println("Correct!");
                score++;
            } else {
                System.out.println("Wrong Answer!");
            }
        }

        System.out.println("\n===== QUIZ COMPLETED =====");
        System.out.println("Your Score: " + score + "/" + questions.length);

        double percentage = (score * 100.0) / questions.length;
        System.out.println("Percentage: " + percentage + "%");

        sc.close();
    }
}
