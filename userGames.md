import java.util.Scanner;



/**
 * 
 * @author Matt Parrella
 * @version 1.0
 * 	
 */

public class userGames {
    
	/**
	 * 
	 * Presents the user with a choice of 2 games.  Will continue prompting the user after each game, 
	 * until the user enters '3'.
	 * 
	 *  @return void
	 * 
	 */
	
	public static void userChoice(){
		
		System.out.println("Please choose a game to play: ");
		System.out.println("1 - Dice Game\n2 - Blackjack Game \n3 - Quit");
		
		Scanner input = new Scanner(System.in);
		int choice = input.nextInt();
				
			while (choice != 3){ // Will continue to prompt the player until they choose 'quit'
					if (choice == 1){
						userGames.playDice();
						break;
					}
						
					else if (choice == 2){
						userGames.playCards();
						break;
					}
				
					else{
						
						break;
					}
				
			}
		
		
		
	} // end of userChoice
	
	/**
	 * 
	 * Simulates rolling a dice.  The user will be asked to enter the number of die to roll.  They will
	 * then have a chance to guess the sum of all the die before the score is calculated by the method.  
	 * The method will then tell the user if they were correct or incorrect and display the sum of all the die.
	 * 
	 * @return void
	 * 
	 */
	
	public static void playDice(){
		
				
		System.out.println("Please enter the number of dice you'd like to play with: ");
		
		// Scanner will take in the user's selection for number of die
		
		Scanner kb = new Scanner(System.in);
		int choice = kb.nextInt();
		
		if (choice == 0){
			System.out.println("You must not want to play dice! Returning you to main menu.");
			userChoice();
			
		}
		
		else {
		int roll = ((int)(6.0 * Math.random()) + 1); // Simulate rolling a die
		
		int score = roll * choice; // Multiply the roll of a single die by the user's choice
		
		int maxscore = choice * 6; // Calculate maximum possible score
			
		
		System.out.println("Guess the sum of all the die: ");
		int choice2 = kb.nextInt();
		
		 if (choice2 == 0){
 			
 			System.out.println("Sum cannot equal zero! Returning you to the main menu.");
 			userChoice();
 		}
		 else if (choice2 <= maxscore){ // Checks to ensure user's guess is valid
						if (choice2 == score){
							System.out.println("You guessed correctly!!!\n");
						}
		
						else {
							System.out.println("You guessed incorrectly. :(\n");
						}
		
	    				System.out.println("The sum of the die is: " + score + "\n");
	    
	    
		    	}
	    
	    		
	    		
	    		
		 else  {  // If the user's guess is not valid, will loop back through the game
	    			
	    				System.out.println("Your answer is an unattainable score with the number of die you selected!!");
	    				System.out.println("Please retry:");
	    		    	
	    				userGames.playDice();
	    		}
	    
	    userGames.userChoice();  // Returns to main game menu

		}
	    
	} //end of playDice()
	
	
	/**
	 * Simulates a game of BlackJack for two players.  They will each be dealt two cards and will have a chance to draw 1
	 * more per turn until both players do not take any more cards.  The winner will be the player whose hand totals 21. If
	 * neither player's hand totals 21, the winner will be the one who holds the higher valued hand (but must be under 21 points).
	 * If a player goes over 21, the method immediately exits and awards the other player the win.
	 * 
	 * 
	 * @returns Void
	 * 
	 */
	
	public static void playCards(){
		
		// Declare local vars
		
	    String card = drawCard();
		int value = 0;
		
		/*
		 * flag and flag2 vars will keep track of whether or not a player chose a new card, 
		 * will be part of ending condition for loop
		 * 
		 */
		
		
		boolean flag = false;
		boolean flag2 = false;	
		
		// totalvalue vars will keep track of each player's hand value
		int totalvalue1;
		int totalvalue2;
		
		//  Player 1's first card
		System.out.println("Player 1's initial deal: ");
		card = drawCard();
		System.out.println("1st Card: " + card);
		value = assignValue(card);
			
		totalvalue1 = value;  // totalvalue1 will hold the value of player 1's hand
		
		// Player 1's second card
		card = drawCard();
		System.out.println("2nd Card: " + card);
		value = assignValue(card);
		
		totalvalue1 = totalvalue1 + value;  // totalvalue1 is updated with addition of 2nd card 
		System.out.println("Total hand value: " + totalvalue1); 
		
	    // Player 2's first card	
		System.out.println("\n\nPlayer 2's initial deal: ");
		card = drawCard();
		System.out.println("1st Card: " + card);
		value = assignValue(card);
	
		totalvalue2 = value;  // totalvalue2 will hold the value of player2's hand
        
		// Player 2's second card
		card = drawCard();
		System.out.println("2nd Card: " + card);
	    value = assignValue(card);
	
	    totalvalue2 = totalvalue2 + value; // totalvalue2 is updated with addition of 2nd card
		System.out.println("Player 2's hand value: " + totalvalue2); // hand value is displayed to the user
		
		
		/*
		 *  Start loop for asking each player if they'd like another card.
		 *  Will continue until BOTH players decline a new card.
		 * 
		 */
        
      
	    
	   do{
		    System.out.println("\nPlayer 1's current hand value: " + totalvalue1); 
		   	System.out.println("Player 1: Would you like another card? Press '1' for Yes, '2' for No.");
	        Scanner kb = new Scanner(System.in);
	        int p1choice = kb.nextInt();		   
	        
	        
	        // If Player 1 chooses a new card
	        
	        if (p1choice == 1){			 
			   card = drawCard();
			   value = assignValue(card);
			   totalvalue1 = totalvalue1 + value;
			   System.out.println("New card: " + card);
			   System.out.println("\nPlayer 1's current hand value: " + totalvalue1);
			   flag = true;	 	   
			   
			   if (totalvalue1 > 21){   // If over 21, game ends and Player 2 wins
				   System.out.println("BUST! Player 1 exceeded 21! PLAYER 2 WINS!");
				   break;
			   }
			   
	    
	        }
		   		   
	       // If Player 1 does not choose a new card
	        
		   else if (p1choice == 2){
			   flag = false; 
		   }
		   
	       // Player 2 will be prompted regardless of Player 1's choice
	        
		   System.out.println("Player 2's current hand value: " + totalvalue2);
		   System.out.println("Player 2: Would you like another card? Press '1' for Yes, '2' for No.");
		   int p2choice = kb.nextInt();
			
		   // If Player 2 chooses a new card
		   
		   if (p2choice == 1){
			 	flag2 = true;
			 	card = drawCard();
			 	value = assignValue(card);
			 	totalvalue2 = totalvalue2 + value;
			 	System.out.println("New card: " + card);
			 	System.out.println("Player 2's current hand value: " + totalvalue2);
		  				
					if (totalvalue2 > 21){  
						System.out.println("BUST! Player 2 exceeded 21! PLAYER 1 WINS!");
						break;
			   					
					}
			}
			
		   // If Player 2 does not choose a card
		   
			else if (p2choice == 2) {
				flag2 = false;
			}
		  
	   }
	   
	   while (flag == true || flag2 == true); // Ending conditional for do-while loop	   
	  
	   System.out.println(analyzeScores(totalvalue1, totalvalue2)); // Call analyzeScores() to determine the winner
	   userChoice(); // Return to game menu
		
	} // end of playCards()
	
	/**
	 * 
	 * This will randomly draw a card from the deck (using a random number generator from 1- 14).  
	 * Will assign cards higher than 10 to their equivalent face card and return them as a String data type.
	 * 
	 * @return String facecard will hold the String of the card name (King, Queen, Ace, etc)
	 * 
	 */
	
	public static String drawCard(){
		
		int card = ((int)(14.0 * Math.random()) + 1);
		String facecard = Integer.toString(card); // Must convert value of card into a String for parsing
		
		/*
		 * switch statement will substitute cards higher than
		 * 10 with their face card equivalent
		 */
		
		switch (card){
		
			case 1:  // If 1 is generated, call drawCard() method again since 1 is not part of the deck
				drawCard();
		
			case 11:
				facecard = "J";
				break;
											
			case 12:
				facecard = "Q";
				break;
				
			case 13:
				facecard = "K";
				break;
			case 14:
				facecard = "A";
				break;
					
			default:
				facecard = Integer.toString(card); // Store card value in a string for parsing
				break;	
		}
	
	
		return facecard;
		
	} // end of drawCard();

    
	/**
	 * 
	 * This method will determine the value of the card passed into it (of type String),
	 * assign it that value, and then return that value as an integer data type.
	 * 
	 * @param card String type - the card who's value needs to be assigned
	 * @return int value of card that is passed into the method
	 * 
	 */
	
	public static int assignValue(String card){
	
		int value;
		switch (card){
	
			case "J":
				value = 10;
				break;
		
			case "Q":
				value = 10;
				break;
		
			case "K":
				value = 10;
				break;
		
			case "A": // User will be allowed to decide if Ace is worth 1 or 11 points, if drawn
				System.out.println("\nPlease choose either 1 or 11 for Ace's value:");
				
				Scanner kb = new Scanner(System.in);
				int choice = kb.nextInt();
				
				if (choice == 1) { 
					value = 1;
					break;
				}
		
				else if (choice == 11){
					value = 11;
					break;
				}
				
				else { // Error check for user input
					
					throw new IllegalArgumentException("Error: Value is not 1 or 11!");					
				}
		
			default:
		
			value = Integer.parseInt(card);				
	
		}
	
		return value;
		
	} // end of assignValue()
	
	
	/**
	 * 
	 * This method will analyze the total scores of each player and determine the winner.
	 *  
	 * @param score1 int type - will be the first score to be compared
	 * @param score2 int type - will be the second score to be compared
	 * @return String a message will output to the users, alerting which is the winner
	 * 
	 */

	public static String analyzeScores(int score1, int score2){
	
		String w = " ";
	
		if (score1 > score2  && score1 <= 21){ 
		
			System.out.println("Final Scores: \nPlayer 1: " + score1 + "\nPlayer 2: " + score2);
		
			w = "\nPLAYER 1 WINS!!\n\n";
		}
	
		else if (score2 > score1 && score2 <=21){
		
			System.out.println("Final Scores: \nPlayer 1: " + score1 + "\nPlayer 2: " + score2);		
			w = "\nPLAYER 2 WINS!!\n\n";
		}
	
		else if (score1 == score2){
		
			System.out.println("Final Scores: \nPlayer 1: " + score1 + "\nPlayer 2: " + score2);
			w = "\nTIE GAME!!\n\n";
		}
	
		return w;
	
	} // end of analyzeScore()
	
} // end of Class
	
	
	
	
	
	



