//AUTHOR: Dustin Brown
//COURSE: CPT 167
//PURPOSE: Generate a receipt that calculates and informs about different discounts and prices for Sod
//CREATEDATE: 7/25/19

package edu.cpt167.brown.participation;

import java.util.Scanner;

public class BrownSodNotZod {
	
	public static final double DISCOUNT_RATE_MEMBER = .15;
	public static final double DISCOUNT_RATE_SENIOR = .25;
	public static final double DISCOUNT_RATE_NONE = 0.0;
	public static final double TAX_RATE = .075;
	public static final String SENIOR = "Senior Discount";
	public static final String MEMBER = "Member Discount";
	public static final String NONE = "No Discount";
	public static final String QUIT = "Quit";
	public static final String NAME_PREMIUM = "Premium Sod";
	public static final String NAME_SPECIAL = "Special Sod";
	public static final String NAME_BASIC = "Basic Sod";
	public static final double PRICE_PREMIUM = 5.0;
	public static final double PRICE_SPECIAL = 3.5;
	public static final double PRICE_BASIC = 1.5;
	public static final int RESET_VALUE = 0;

	public static void main(String[] args) {
		//declare and initialize a Scanner object
		Scanner input = new Scanner(System.in);

		//declare and initialize variables
		String userName = "";
		String itemName = "";
		char menuSelection = ' ';
		char itemSelection = ' ';
		int howManyItems = 0;
		int howManyEach = 0;
		int memberCount = 0;
		int seniorCount = 0;
		int noDiscountCount = 0;
		int itemACount = 0;
		int itemBCount = 0;
		int itemCCount = 0;
		int itemCounter = 0;
		double origPrice = 0.0;
		double discountAmt = 0.0;
		double discountPrice = 0.0;
		double discountRate = 0.0;
		double subTotal = 0.0;
		double tax = 0.0;
		double totalCost = 0.0;
		double customerTotal = 0.0;
		double grandTotal = 0.0;
		
		//Welcome Banner
		displayWelcomeBanner();

		//input username
		userName = getUserName(input);

		//input main menu
		menuSelection = validateMainMenu(input);

		//Validate Menu Selection
		while (menuSelection != 'Q')
		{
			//Repetition structure howManyItems
			howManyItems = validateHowManyItems(input);
			
			while (itemCounter < howManyItems)
			{
				
				//input item menu
				itemSelection = validateItemMenu(input);
	
				//input how many items
				howManyEach = validateHowManyEach(input);
	
				//Process Selection Structure menuSection
				if (menuSelection == 'A')
				{
					discountRate = DISCOUNT_RATE_MEMBER;
					memberCount++;
				}
				else if (menuSelection == 'B')
				{
					discountRate = DISCOUNT_RATE_SENIOR;
					seniorCount++;
				}
				else
				{
					discountRate = DISCOUNT_RATE_NONE;
					noDiscountCount++;
				}
	
				//Process Selection Structure ItemSelection
				if (itemSelection == 'A')
				{
					itemName = NAME_PREMIUM;
					origPrice = PRICE_PREMIUM;
					itemACount++;
				}
				else if (itemSelection == 'B')
				{
					itemName = NAME_SPECIAL;
					origPrice = PRICE_SPECIAL;
					itemBCount++;
				}
				else 
				{
					itemName = NAME_BASIC;
					origPrice = PRICE_BASIC;
					itemCCount++;
				}
	
				//Processes
				discountAmt = origPrice * discountRate;
				discountPrice = origPrice - discountAmt;
				subTotal = howManyEach * discountPrice;
				tax = subTotal * TAX_RATE;		
				totalCost = subTotal + tax;
				customerTotal = customerTotal + totalCost;
				grandTotal = grandTotal + totalCost;
	
				//Display item Receipt
				displayItemReceipt(userName, itemName, origPrice, discountPrice, howManyEach, subTotal, tax, totalCost);
				
				//Update itemCounter
				itemCounter++;
				
			}//End of Rep Structure ValidatehowManyItems
			
			//Selection Structure howManyItems
			if (howManyItems > 0)
			{
				displayCustomerReport(howManyItems, customerTotal);
			}
			
			//reset itemCounter
			itemCounter = RESET_VALUE;
			//reset customerTotal
			customerTotal = RESET_VALUE;
			
			//Main Menu Again
			menuSelection = validateMainMenu(input);
			
		}//End of Rep Structure validateMainMenu

		//Grand Total Selection structure
		if (grandTotal > 0.0)
		{
			displayFinalReport(memberCount, seniorCount, noDiscountCount, itemACount, itemBCount, itemCCount, grandTotal);
		}

		//Farewell Message
		displayFarewellMessage();

		//close scanner object
		input.close();
	}//End of Main


	public static void displayWelcomeBanner() 
	{
		//Welcome Banner
		System.out.println("************************************************************");
		System.out.println("                 Welcome to Sod, Not Zod!");
		System.out.println("  This program will help you calculate your sod costs");
		System.out.println("and give you a receipt including your discount, sub total,");
		System.out.println("                      tax and total.");
		System.out.println("************************************************************");
	}//End of displayWelcomeBanner
	
	public static String getUserName(Scanner borrowedInput)
	{
		//declare and initialize local variables
		String localUserName = "";

		//get username
		System.out.println("What is your name?");
		localUserName = borrowedInput.next();

		//return statement
		return localUserName;
	}//End of getUserName
	
	public static char validateMainMenu(Scanner borrowedInput)
	{
		//declare and initialize local variables
		char localMenuSelection = ' ';

		//call menu
		displayMainMenu();
		//user input
		localMenuSelection = borrowedInput.next().toUpperCase().charAt(0);

		//validation loop
		while (localMenuSelection != 'A' && localMenuSelection != 'B' && localMenuSelection != 'C' && localMenuSelection != 'Q')
		{
			System.out.println("\n~~~~~INVALID~~~~~\n");
			displayMainMenu();
			localMenuSelection = borrowedInput.next().toUpperCase().charAt(0);	
		}

		return localMenuSelection;
	}//End of validateMainMenu
	
	public static void displayMainMenu()
	{
		//menuSelection
		System.out.println("_________________");
		System.out.println("MAIN ACCOUNT MENU");
		System.out.println("'''''''''''''''''");
		System.out.printf("%-5s%3s%17s\n", "[A]", "for",  MEMBER);
		System.out.printf("%-5s%3s%17s\n", "[B]", "for",  SENIOR);
		System.out.printf("%-5s%3s%13s\n", "[C]", "for",  NONE);
		System.out.printf("%-5s%3s%6s\n", "[Q]", "for", QUIT);
		System.out.print("Please make your selection here:");
	}//End of displayMainMenu

	public static int validateHowManyItems(Scanner borrowedInput)
	{
		//declare and initialize local variable
		int localHowManyItems = 0;
		
		//user input
		System.out.println("\nHow many orders will you complete today?");
		localHowManyItems = borrowedInput.nextInt();

		//Validation loop
		while (localHowManyItems <= 0)
		{
			System.out.println("\n~~~~~INVALID~~~~~\n");
			System.out.println("\nHow many orders will you complete today?");
			localHowManyItems = borrowedInput.nextInt();
		}
		
		//return howManyItems
		return localHowManyItems;
	}//end of validatehowManyItems
	
	public static char validateItemMenu(Scanner borrowedInput)
	{
		//declare and initialize local variables
		char localItemSelection = ' ';

		//call menu
		displayItemMenu();
		//user input
		localItemSelection = borrowedInput.next().toUpperCase().charAt(0);

		//validation loop
		while (localItemSelection != 'A' && localItemSelection != 'B' && localItemSelection != 'C' && localItemSelection != 'Q')
		{
			System.out.println("\n~~~~~INVALID~~~~~\n");
			displayItemMenu();
			localItemSelection = borrowedInput.next().toUpperCase().charAt(0);	
		}

		return localItemSelection;
	}//End of validateItemMenu
	
	public static void displayItemMenu()
	{
		//Item Selection Menu
		System.out.println("___________________");
		System.out.println("ITEM SELECTION MENU");
		System.out.println("'''''''''''''''''''");
		System.out.printf("%-5s%3s%13s%3s%-4.2f%5s\n", "[A]", "for",  NAME_PREMIUM, "$", PRICE_PREMIUM, "/sq.ft.");
		System.out.printf("%-5s%3s%13s%3s%-4.2f%5s\n", "[B]", "for",  NAME_SPECIAL, "$", PRICE_SPECIAL, "/sq.ft.");
		System.out.printf("%-5s%3s%13s%3s%-4.2f%5s\n", "[C]", "for",  NAME_BASIC, "$", PRICE_BASIC, "/sq.ft.");
		System.out.print("Please make your selection here:");	
	}//End of displayItemMenu

	public static int validateHowManyEach(Scanner borrowedInput)
	{
		//declare and initialize local variable
		int localHowManyEach = 0;
		
		//user input
		System.out.println("\nHow many would you like to purchase?");
		localHowManyEach = borrowedInput.nextInt();

		//Validation loop
		while (localHowManyEach <= 0)
		{
			System.out.println("\n~~~~~INVALID~~~~~\n");
			System.out.println("\nHow many would you like to purchase?");
			localHowManyEach = borrowedInput.nextInt();
		}
		
		//return howManyEach
		return localHowManyEach;
	}//end of validateHowManyEach
	
	public static void displayItemReceipt(String borrowedUserName, String borrowedItemName, double borrowedOrigPrice,
			double borrowedDiscountPrice, int borrowedHowManyEach, double borrowedSubTotal,
			double borrowedTax, double borrowedTotalCost)
	{
		//Display item receipt
		System.out.println("\n~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~");
		System.out.println(borrowedUserName + ", here is a receipt of your transaction:");
		System.out.printf("\n%-30s%9s\n","Item:", borrowedItemName);
		System.out.printf("%-31s%9d\n","Quantity purchased:", borrowedHowManyEach);
		System.out.printf("%-31s%1s%8.2f%7s\n","Original Price:","$", borrowedOrigPrice, "/sq.ft.");
		System.out.printf("%-31s%1s%8.2f%7s\n","Price per item after discount:","$", borrowedDiscountPrice, "/sq.ft.");
		System.out.printf("%-31s%1s%8.2f\n","Subtotal:","$", borrowedSubTotal);
		System.out.printf("%-31s%1s%8.2f\n","Tax:","$", borrowedTax);
		System.out.printf("%-31s%1s%8.2f\n","Total:","$", borrowedTotalCost);
		System.out.println("~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~");
	}//end of displayItemReceipt

	public static void displayCustomerReport(int borrowedHowManyItems, double borrowedCustomerTotal)
	{
		System.out.println("\n*************************");
		System.out.println("Customer Report");
		System.out.println("*************************");
		System.out.printf("%-15s%s%9d\n", "Total Orders:", "", borrowedHowManyItems);
		System.out.printf("%-15s%s%8.2f\n", "Final Total:", "$", borrowedCustomerTotal);
		System.out.println("*************************");
	}//end of displayCustomerReport
	
	public static void displayFinalReport(int borrowedMemberCount, int borrowedSeniorCount, int borrowedNoDiscountCount,
			int borrowedItemACount, int borrowedItemBCount, int borrowedItemCCount,	double borrowedGrandTotal)
	{

		//display final report
		System.out.println("\n~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~");
		System.out.println("Final Report");
		System.out.println("~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~");
		System.out.printf("%-27s%s%8d\n", "Member Discounts:", "" , borrowedMemberCount);
		System.out.printf("%-27s%s%8d\n", "Senior Discounts:", "", borrowedSeniorCount);
		System.out.printf("%-27s%s%8d\n", "Orders without Discounts:", "", borrowedNoDiscountCount);
		System.out.printf("%-27s%s%8d\n", NAME_PREMIUM + " orders:", "", borrowedItemACount);
		System.out.printf("%-27s%s%8d\n", NAME_SPECIAL + " orders:", "", borrowedItemBCount);
		System.out.printf("%-27s%s%8d\n", NAME_BASIC + " orders:", "", borrowedItemCCount);
		System.out.printf("%-26s%S%8.2f\n", "Grand Total:", "$", borrowedGrandTotal);
		System.out.println("~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~\n");
	}//End of displayFinalReport

	public static void displayFarewellMessage()
	{
		//Farewell
		System.out.println("\nThank you for choosing Sod, not Zod!");
		System.out.println("Have a great day!");
	}//End of displayFarewellMessage
	
}//End of Class

