# Credit-Card-Validator

import java.util.*;


//Full name: Muhammad Ibraheem
//Description: To check is credit card numbers are valid.
public class Validator {

	public static void main(String[] args) {
		Scanner input = new Scanner(System.in); // Creates scanner object MI
		
		SystemTitle();
	for(int i = 0;i<3;i++) {
		System.out.print("Enter a credit card number: "); //prompt user for cc number MI
		String cardNumberStr = input.next(); // takes user input as string MI
	
		
		
		if(identifierCheck(cardNumberStr) && lengthCheck(cardNumberStr) && luhnCheck(cardNumberStr)) {
			System.out.println(cardNumberStr + " is valid"); //prints that cc is valid MI
		}
		else {
			System.out.println(cardNumberStr + " is invalid"); //prints that cc is invalid MI
		}
		System.out.print("Enter the expiration date(MM/YY): ");
		String expire = input.next();
		header();
		int sumNumbers = sum(cardNumberStr);
		System.out.printf("%15s\t%6s\t\t\t%4d\n",cardNumberStr,expire,sumNumbers);
		
		}
	}
		
		
	
		public static void SystemTitle() {
			System.out.print("Welcome to the validation! \nDeveloper: Diaz\n");
		}
		
		public static boolean identifierCheck(String cardNumber) {
			if(cardNumber.startsWith("37")) {
				return true; //returns true is cc starts with 37 MI
				}
			else if (cardNumber.startsWith("4") || cardNumber.startsWith("5") || cardNumber.startsWith("6")) {
				return true; //returns true is cc starts with 4 5 or 6 MI
				}
			else {
				return false; //returns false if not MI
			}
		}
			public static boolean lengthCheck(String cardNum) {
				return (cardNum.length()>=13 && cardNum.length()<=16);
			}
			
			public static int luhnCheckEvens(String cardNum ) {
				int sum = 0;
				
				for(int i = cardNum.length() - 2; i>=0; i -=2) {//for loop starts at 2nd number from right, skips to every 2nd number MI
					int index = Integer.parseInt(Character.toString(cardNum.charAt(i))) *2;
					
					if(index >= 10 ) { //if index is greater than 10 than is it a double digit MI
						String temp = Integer.toString(index);
						index = Integer.parseInt(Character.toString(temp.charAt(0))) + Integer.parseInt(Character.toString(temp.charAt(1)));
					}
					sum += index; //adds to sum as appropriate MI
				}
				return sum;
			}
			
			public static int luhnCheckOdds(String cardNum ) {
				int sum = 0;
				
				for(int i = cardNum.length() - 1; i>=0; i -=2) {//for loop starts at 2nd number from right, skips to every 2nd number MI
					int index = Integer.parseInt(Character.toString(cardNum.charAt(i)));
					
					sum += index; //adds to sum as appropriate MI
				}
				return sum;
			}
			public static boolean luhnCheck(String cardNum) {
				return ((luhnCheckOdds(cardNum) + luhnCheckEvens(cardNum)) % 10 == 0);
			}
			public static void header() {
				System.out.println("Credit Card Number\tExpiration Date\t\tSum of Credit card numbers");
				System.out.println("------------------\t---------------\t\t--------------------------");
			}
			public static int sum (String cnumber) {
				int sum = 0;
				for(int i = 0;i<cnumber.length();i++) {
					sum += Integer.parseInt(Character.toString(cnumber.charAt(i)));
				}
				return sum;
			}
}
