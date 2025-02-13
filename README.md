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





//ques 2
import java.util.Scanner;

public class SquareRootCalculator {
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        
        System.out.print("Enter a number: ");
        
        try {
            
            String input = scanner.nextLine();
            double number = Double.parseDouble(input);
            
            
            if (number < 0) {
                throw new IllegalArgumentException("Cannot calculate the square root of a negative number.");
            }
            
            
            double result = Math.sqrt(number);
            System.out.println("The square root of " + number + " is: " + result);
        } catch (NumberFormatException e) {
            
            System.out.println("Invalid input! Please enter a valid numeric value.");
        } catch (IllegalArgumentException e) {
            
            System.out.println(e.getMessage());
        } finally {
            scanner.close();
        }
    }
}

