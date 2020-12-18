# ATM-Simulator
# Java code for ATM Simulator
import java.util.Scanner;
public class ATM{
    static float balance=0;
    public static void main(String args[]) {
        transaction();
    }
    public static void transaction() {
        Scanner n =new Scanner(System.in);
        int choice;
        System.out.println("Please select an option");
        System.out.println("1. Withdraw");
        System.out.println("2. Deposit");
        System.out.println("3. Balance");
        choice = n.nextInt();
        switch (choice) {
            case 1:
                float amount;
                System.out.println("Please enter amount to withdraw: ");
                amount = n.nextFloat();
                if (amount > balance || amount == 0) {
                    System.out.println("You have insufficient funds\n\n");
                    anotherTransaction(); 
                } 
                else {
                    balance = balance - amount;
                    System.out.println("You have withdrawn " + amount + " and your new balance is " + balance + "\n");
                    anotherTransaction();
                }
                break;
            case 2:
                float deposit;
                System.out.println("Please enter amount you would wish to deposit: ");
                deposit = n.nextFloat();
                balance = deposit + balance;
                System.out.println("You have deposited " + deposit + " new balance is " + balance + "\n");
                anotherTransaction();
                break;
            case 3:
                System.out.println("Your balance is " + balance + "\n");
                anotherTransaction();
                break;
            default:
                System.out.println("Invalid option:\n\n");
                anotherTransaction();
                break;
        }
    }
    public static void anotherTransaction() {
        Scanner a =new Scanner(System.in);
        int anotherTrans;
        System.out.println("Do you want another transaction?\n\nPress 1 for another transaction\n2 To exit");
        anotherTrans = a.nextInt();
        if (anotherTrans == 1) {
            transaction(); 
        } 
        else if (anotherTrans == 2) {
            System.out.println("Thanks for choosing us. Good Bye!");
        } 
        else {
            System.out.println("Invalid choice\n\n");
            anotherTransaction();
        }
    }
}
