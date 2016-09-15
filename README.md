# userGames
import java.util.Scanner;



public class userGames {


	
	public static void main(String[] args) {

		userGames.userChoice();

	}	
	
    
	public static void userChoice(){
		
		System.out.println("Please choose a game to play: ");
		System.out.println("1 - Dice Game\n2- Card Game \n3 - Quit");
		
		Scanner input = new Scanner(System.in);
		int choice = input.nextInt();
		
		
		
		while (choice != 3){
			
			
				if (choice == 1){
			
					userGames.playDice();
					break;
					
					}
		
				
		else if (choice == 2){
			
			System.out.println("Game is unavailable: Still in Beta testing :)\n");
			
			userGames.userChoice();
			break;
			
			
		}
		
		break;
		
		
		
		}
	}// end of userChoice
		
	public static void playDice(){
		
		//System.out.println("Entering playDice() method!");
		
		System.out.println("Please enter the number of dice you'd like to play with: ");
		
		Scanner kb = new Scanner(System.in);
		int choice = kb.nextInt();
				
		int roll = ((int)(6.0 * Math.random()) + 1);
		
		int score = roll * choice;
		
		int maxscore = choice * 6;
			
		
		System.out.println("Guess the value of all the die: ");
		int choice2 = kb.nextInt();
		
		
	    if (choice2 <= maxscore){
		
		
		
	    		if (choice2 == score){
			
	    			System.out.println("You guessed correctly!!!\n");
			
	    		}
		
	    		else {
			
	    			System.out.println("You guessed incorrectly. :(\n");
			
	    		}
		
	    		System.out.println("The sum of the die is: " + score + "\n");
		
	    	}
	    
	    else{
	    	System.out.println("Your answer is an unattainable score with the number of die you selected!!");
	    	System.out.println("Please retry:");
	    	
	    	
	    	userGames.playDice();
	    }
	    
	    userGames.userChoice();
		
	} //end of playDice()
		
		
		
	} // end of userChoice
