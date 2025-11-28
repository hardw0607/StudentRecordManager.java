# StudentRecordManager.java
StudentRecordManager.java
package mypackages;

// public class StudentRecordManager {

// }
import java.util.Scanner;

public class StudentRecordManager {
    static String[] names = new String[100];
    static int[] rollNumbers = new int[100];
    static int[] marks = new int[100];
    static int count = 0;

    public static void addStudent(Scanner sc) {
        System.out.print("Enter Name: ");
        names[count] = sc.next();
        System.out.print("Enter Roll Number: ");
        rollNumbers[count] = sc.nextInt();
        System.out.print("Enter Marks: ");
        marks[count] = sc.nextInt();
        count++;
        System.out.println("Student added successfully.\n");
    }

    public static void viewAllStudents() {
        if (count == 0) {
            System.out.println("No records available.\n");
            return;
        }

        System.out.println("Roll\tName\tMarks");
        for (int i = 0; i < count; i++) {
            System.out.println(rollNumbers[i] + "\t" + names[i] + "\t" + marks[i]);
        }
        System.out.println();
    }

    public static void searchStudent(Scanner sc) {
        System.out.print("Enter roll number to search: ");
        int roll = sc.nextInt();
        boolean found = false;

        for (int i = 0; i < count; i++) {
            if (rollNumbers[i] == roll) {
                System.out.println("Name: " + names[i] + ", Marks: " + marks[i] + "\n");
                found = true;
                break;
            }
        }

        if (!found) {
            System.out.println("Student not found.\n");
        }
    }

    public static void updateMarks(Scanner sc) {
        System.out.print("Enter roll number to update: ");
        int roll = sc.nextInt();
        boolean found = false;

        for (int i = 0; i < count; i++) {
            if (rollNumbers[i] == roll) {
                System.out.print("Enter new marks: ");
                marks[i] = sc.nextInt();
                System.out.println("Marks updated.\n");
                found = true;
                break;
            }
        }

        if (!found) {
            System.out.println("Student not found.\n");
        }
    }

    public static void deleteStudent(Scanner sc) {
        System.out.print("Enter roll number to delete: ");
        int roll = sc.nextInt();
        boolean found = false;

        for (int i = 0; i < count; i++) {
            if (rollNumbers[i] == roll) {
                for (int j = i; j < count - 1; j++) {
                    names[j] = names[j + 1];
                    rollNumbers[j] = rollNumbers[j + 1];
                    marks[j] = marks[j + 1];
                }
                count--;
                System.out.println("Student deleted.\n");
                found = true;
                break;
            }
        }

        if (!found) {
            System.out.println("Student not found.\n");
        }
    }

    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        int choice;

        do {
            System.out.println("===== Student Record Manager =====");
            System.out.println("1. Add Student");
            System.out.println("2. View All Students");
            System.out.println("3. Search Student");
            System.out.println("4. Update Marks");
            System.out.println("5. Delete Student");
            System.out.println("6. Exit");
            System.out.print("Enter choice: ");
            choice = sc.nextInt();

            switch (choice) {
                case 1:
                    addStudent(sc);
                    break;
                case 2:
                    viewAllStudents();
                    break;
                case 3:
                    searchStudent(sc);
                    break;
                case 4:
                    updateMarks(sc);
                    break;
                case 5:
                    deleteStudent(sc);
                    break;
                case 6:
                    System.out.println("Exiting program.");
                    break;
                default:
                    System.out.println("Invalid choice.\n");
            }

        } while (choice != 6);

        sc.close();
    }
}
#===== Student Record Manager =====
#1. Add Student
#2. View All Students
#3. Search Student
#4. Update Marks
#5. Delete Student
#6. Exit
Enter choice:
