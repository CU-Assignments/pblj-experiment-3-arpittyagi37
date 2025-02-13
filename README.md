//QUES 1
import java.util.Scanner;

class ATM {
    private int pin;
    private double balance;

    
    public ATM(int pin, double balance) {
        this.pin = pin;
        this.balance = balance;
    }

    
    public void verifyPin(int enteredPin) throws Exception {
        if (enteredPin != this.pin) {
            throw new Exception("Invalid PIN!");
        }
    }

    
    public void withdraw(double amount) throws Exception {
        if (amount > this.balance) {
            throw new Exception("Insufficient balance!");
        }
        this.balance -= amount;
    }

    
    public void displayBalance() {
        System.out.println("Remaining Balance: $" + this.balance);
    }

    public static void main(String[] args) {
        ATM atm = new ATM(1234, 500); 
        Scanner scanner = new Scanner(System.in);
        
        try {
            System.out.print("Enter your PIN: ");
            int enteredPin = scanner.nextInt();
            atm.verifyPin(enteredPin); 

            System.out.print("Enter amount to withdraw: $");
            double withdrawalAmount = scanner.nextDouble();
            atm.withdraw(withdrawalAmount); 

            System.out.println("Withdrawal successful!");
        } catch (Exception e) {
            System.out.println("Error: " + e.getMessage());
        } finally {
            atm.displayBalance(); 
            scanner.close();
        }
    }
}
