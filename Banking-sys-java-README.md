# Banking_system-java
// Saakshi Krishnani

package practical;

import java.util.*;

public class bank_account {

    static HashMap<Integer, Double> accounts = new HashMap<>();

    public static void deposit(int accNo, double amount) {
        double currentBalance = accounts.get(accNo);
        accounts.put(accNo, currentBalance + amount);
        System.out.println("₹" + amount + " deposited to account " + accNo);
    }

    public static void withdraw(int accNo, double amount) {
        double currentBalance = accounts.get(accNo);
        if (amount > currentBalance) {
            System.out.println("Error: Insufficient balance in account " + accNo);
        } else {
            accounts.put(accNo, currentBalance - amount);
            System.out.println("₹" + amount + " withdrawn from account " + accNo);
        }
    }

    public static void displayAccounts() {
        System.out.println("\n--- Account Details ---");
        for (Map.Entry<Integer, Double> entry : accounts.entrySet()) {
            System.out.println("Account No: " + entry.getKey() + ", Balance: ₹" + entry.getValue());
        }
    }

    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);

        accounts.put(101, 5000.0);
        accounts.put(102, 10000.0);
        accounts.put(103, 7500.0);

        int choice;

        do {
            System.out.println("\n--- Banking System ---");
            System.out.println("1. Deposit");
            System.out.println("2. Withdraw");
            System.out.println("3. View Account Details");
            System.out.println("4. Exit");
            System.out.print("Enter your choice: ");
            choice = scanner.nextInt();

            int accNo;
            double amount;

            switch (choice) {
                case 1:
                    System.out.print("Enter Account Number: ");
                    accNo = scanner.nextInt();
                    if (accounts.containsKey(accNo)) {
                        System.out.print("Enter amount to deposit: ");
                        amount = scanner.nextDouble();
                        deposit(accNo, amount);
                    } else {
                        System.out.println("Error: Account number does not exist.");
                    }
                    break;

                case 2:
                    System.out.print("Enter Account Number: ");
                    accNo = scanner.nextInt();
                    if (accounts.containsKey(accNo)) {
                        System.out.print("Enter amount to withdraw: ");
                        amount = scanner.nextDouble();
                        withdraw(accNo, amount);
                    } else {
                        System.out.println("Error: Account number does not exist.");
                    }
                    break;

                case 3:
                    displayAccounts();
                    break;

                case 4:
                    System.out.println("Exiting... Thank you for using the Banking App!");
                    break;

                default:
                    System.out.println("Invalid choice. Please try again.");
            }

        } while (choice != 4);

        scanner.close();
    }
}
