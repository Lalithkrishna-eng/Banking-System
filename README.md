# BankAccount
import java.util.Scanner;
public class BankAccount {
    private String accountHolder;
    private String accountNumber;
    private double balance;

    public BankAccount(String accountHolder, String accountNumber, double initialBalance) {
        this.accountHolder = accountHolder;
        this.accountNumber = accountNumber;
        this.balance = initialBalance;
    }

    public void deposit(double amount) {
        if (amount > 0) {
            balance += amount;
            System.out.println("Deposited ₹" + amount);
        } else {
            System.out.println("Invalid deposit amount.");
        }
    }

    public void withdraw(double amount) {
        if (amount > 0 && amount <= balance) {
            balance -= amount;
            System.out.println("Withdrew ₹" + amount);
        } else {
            System.out.println("Invalid or insufficient balance.");
        }
    }

    public void showBalance() {
        System.out.println("Current balance: ₹" + balance);
    }

    public void showAccountInfo() {
        System.out.println("Account Holder: " + accountHolder);
        System.out.println("Account Number: " + accountNumber);
        System.out.println("Balance: ₹" + balance);
    }
}

public class Main {
    public static void main(String[] args) {
        BankAccount account = new BankAccount("Lalith Krishna", "ACC12345", 1000.0);
        Scanner scanner = new Scanner(System.in);
        int choice;

        do {
            System.out.println("\n1. Deposit\n2. Withdraw\n3. Show Balance\n4. Account Info\n5. Exit");
            choice = scanner.nextInt();

            switch (choice) {
                case 1:
                    System.out.print("Enter amount to deposit: ");
                    double dep = scanner.nextDouble();
                    account.deposit(dep);
                    break;
                case 2:
                    System.out.print("Enter amount to withdraw: ");
                    double wd = scanner.nextDouble();
                    account.withdraw(wd);
                    break;
                case 3:
                    account.showBalance();
                    break;
                case 4:
                    account.showAccountInfo();
                    break;
                case 5:
                    System.out.println("Thanks for using our banking system!");
                    break;
                default:
                    System.out.println("Invalid choice.");
            }
        } while (choice != 5);
    }
}
