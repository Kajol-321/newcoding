# WAP to find the percentage of student who contains 5 subjects and check the following condition (Take
the input from user) using interface and super keywordCalculate the percentage of any student who have 5 subjects.
If percentage is greater than , equal to 90 but less than 100 then print “You are an outstanding
student”.
If percentage is greater than , equal to 80 but less than 90 then print “Your performance is good”.
If percentage is greater than , equal to 70 but less than 80 then print “Your performance is better”.
If percentage is greater than , equal to 60 but less than 70 then print “Your performance is average”.
If percentage is greater than , equal to 50 but less than 60 then print “Work hard, you can do better”.
Otherwise print “You have to work hard”

import java.util.Scanner;

interface PercentageCalculator {
    void calculatePercentage();
}

class Person {
    String name;

    Person(String name) {
        this.name = name;
    }

    void display() {
        System.out.println("Name: " + name);
    }
}

class Student extends Person implements PercentageCalculator {
    int[] marks = new int[5];

    Student(String name, int[] marks) {
        super(name);
        this.marks = marks;
    }

    @Override
    public void calculatePercentage() {
        int totalMarks = 0;
        for (int mark : marks) {
            totalMarks += mark;
        }
        double percentage = (double) totalMarks / marks.length;

        System.out.printf("Percentage: %.2f%%\n", percentage);

        if (percentage >= 90 && percentage < 100) {
            System.out.println("You are an outstanding student");
        } else if (percentage >= 80 && percentage < 90) {
            System.out.println("Your performance is good");
        } else if (percentage >= 70 && percentage < 80) {
            System.out.println("Your performance is better");
        } else if (percentage >= 60 && percentage < 70) {
            System.out.println("Your performance is average");
        } else if (percentage >= 50 && percentage < 60) {
            System.out.println("Work hard, you can do better");
        } else {
            System.out.println("You have to work hard");
        }
    }
}

public class Main {
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);

        System.out.print("Enter student's name: ");
        String name = scanner.nextLine();

        int[] marks = new int[5];
        for (int i = 0; i < 5; i++) {
            System.out.print("Enter marks for subject " + (i + 1) + ": ");
            marks[i] = scanner.nextInt();
        }

        Student student = new Student(name, marks);
        student.display();
        student.calculatePercentage();

        scanner.close();
    }
}

