# Fanorona
CS3 assignment (Dalton)
import java.util.Scanner;


public class Fanorona {
	/**
	 * ACSL 3 with 2d array
	 * 
	 * Test Data:
	 * 1. 3, 12, 17, 22, 3, 4, 14, 10
	 * 2. 3, 12, 17, 22, 3, 9, 10, 15
	 * 3. 3, 12, 17, 22, 3, 25, 9, 5
	 * 4. 3, 3, 16, 22, 3, 15, 19, 25
	 * 5. 3, 12, 17, 22, 3, 3, 18, 19
	 * 
	 * Returns:
	 * 1. 14
	 * 2. 9
	 * 3. 5, 9
	 * 4. 15
	 * 5. 18, 19
	 */


	static String[][] board = new String[7][7];
	static String[] s;
	static int[] available;


	public static void main(String[] args) {
		// TODO Auto-generated method stub
		int counter = 1;
		while(counter<=5)
		{
			@SuppressWarnings("resource")
			Scanner scan = new Scanner(System.in);
			s = scan.nextLine().split(", ");
			for(int i = 0; i<s.length; i++){
				//System.out.println("s[" + i + "]= " + s[i]);
			}

			int[] white = new int[(s.length/2)+1];//all values related to white
			int[] black = new int[(s.length/2)+1];//all values related to black
			int[] w = new int[(white.length)-2];//locations of white pieces
			int[] b = new int[(black.length)-2];//locations of black pieces

			for(int i= 0; i<s.length/2; i++){
				white[i] = Integer.parseInt(s[i]);
				//System.out.println("white[" + i + "]: " + white[i]);
			}

			for(int i=0; i<w.length; i++){
				w[i] = white[i+1];
				//System.out.println("w[" + i + "]: " + w[i]);
			}

			for(int i= 0; i<s.length/2; i++){
				black[i] = Integer.parseInt(s[i+(s.length/2)]);	
				//System.out.println("black[" + i + "]: " + black[i]);
			}

			for(int i=0; i<b.length; i++){
				b[i] = black[i+1];
				//System.out.println("b[" + i + "]: " + b[i]);
			}

			//makes a new array to hold all locations
			String[] holder = new String[w.length + b.length];
			for(int i = 0; i<holder.length; i++){
				if(i<w.length){
					holder[i] = Integer.toString(w[i]);
				}
				else{
					holder[i] = Integer.toString(b[i-w.length]);
				}
			}
			//prints values in holder
			for(int i = 0; i<holder.length; i++){
				//System.out.println("holder[" + i + "]: " + holder[i]);
			}

			//Initial(board);
			fill(holder, board);
			counter++;
		}
	}//main


	//fills board
	private static void fill(String[] holder, String[][] board){
		String piece;
		int x;
		int y;
		Initial(board);
		for(int i = 0; i<holder.length; i++){
			if(i<(holder.length)/2){
				piece = "w";
			}
			else{
				piece = "b";
			}
			y = (Integer.parseInt(holder[i])-1)%5 +1; 
			if(Integer.parseInt(holder[i])%5==0){
				x= (Integer.parseInt(holder[i])/5);
			}
			else{
				x = Integer.parseInt(holder[i])/5+1;
			}
			board[x][y] = piece;
			//System.out.println("board[" + x + "," + y + "]: " + board[x][y]);
		}

		print(board);
		up(board);
		down(board);
		right(board);
		left(board);
		tr(board);
		tl(board);
		br(board);
		bl(board);

	}

	private static void Initial(String[][] board){
		//System.out.println("initial");
		for(int i = 0; i<board.length; i++){
			for(int j = 0; j<board.length; j++){
				board[i][j] = "e";
				//System.out.print(board[i][j]);
			}
			//System.out.println();
		}
	}

	private static void print(String[][] board){
		//System.out.println("board");
		for(int j = 0; j<board.length; j++){
			for(int k = 0; k<board.length; k++){
				System.out.print(board[j][k]);
			}
			System.out.println();
		}
	}
	private static void boardNumbers(String[][] board, int x, int y){
		if(x==1){
			if(y==1){
				board[x][y] = "1";
			}
			else if(y==2){
				board[x][y] = "2";
			}
			else if(y==3){
				board[x][y] = "3";
			}
			else if(y==4){
				board[x][y] = "4";
			}
			else if(y==5){
				board[x][y] = "5";
			}
			else{
				board[x][y] = "e";
			}
		}
		else if(x==2){
			if(y==1){
				board[x][y] = "6";
			}
			else if(y==2){
				board[x][y] = "7";
			}
			else if(y==3){
				board[x][y] = "8";
			}
			else if(y==4){
				board[x][y] = "9";
			}
			else if(y==5){
				board[x][y] = "10";
			}
			else{
				board[x][y] = "e";
			}
		}
		else if(x==3){
			if(y==1){
				board[x][y] = "11";
			}
			else if(y==2){
				board[x][y] = "12";
			}
			else if(y==3){
				board[x][y] = "13";
			}
			else if(y==4){
				board[x][y] = "14";
			}
			else if(y==5){
				board[x][y] = "15";
			}
			else{
				board[x][y] = "e";
			}
		}
		else if(x==4){
			if(y==1){
				board[x][y] = "16";
			}
			else if(y==2){
				board[x][y] = "17";
			}
			else if(y==3){
				board[x][y] = "18";
			}
			else if(y==4){
				board[x][y] = "19";
			}
			else if(y==5){
				board[x][y] = "20";
			}
			else{
				board[x][y] = "e";
			}
		}
		else if(x==5){
			if(y==1){
				board[x][y] = "21";
			}
			else if(y==2){
				board[x][y] = "22";
			}
			else if(y==3){
				board[x][y] = "23";
			}
			else if(y==4){
				board[x][y] = "24";
			}
			else if(y==5){
				board[x][y] = "25";
			}
			else{
				board[x][y] = "e";
			}
		}
		else{
			board[x][y] = "e";
		}
		
	}

	public static void up(String[][]board){
		for(int i = 0; i<board.length; i++){
			for(int j = 0; j<board.length; j++){
				if((i!=1 && j!=1)||(i!=1 && j!=2)||(i!=1 && j!=3)||(i!=1 && j!=4)||(i!=1 && j!=5) && (board[i-5][j] == "e" && (board[i-10][j] == "b" || board[i-5][j-1] == "b" || board[i-5][j+1] == "b"))){
					int f;
					int g;
					if(board[i-10][j] == "b"){
						f = i-10;
						g = j;
					}
					else if(board[i-5][j-1] == "b"){
						f = i-5;
						g = j-1;
					}
					else{
						f = i-5;
						g = j+1;
					}
					boardNumbers(board, f, g);
				}
			}
		}
	}
	public static void down(String[][]board){
		for(int i = 0; i<board.length; i++){
			for(int j = 0; j<board.length; j++){
				if((i!=5 && j!=1)||(i!=5 && j!=2)||(i!=5 && j!=3)||(i!=5 && j!=4)||(i!=5 && j!=5) && (board[i+5][j] == "e" && (board[i+10][j] == "b" || board[i+5][j-1] == "b" || board[i+5][j+1] == "b"))){
					int f;
					int g;
					if(board[i+10][j] == "b"){
						f = i+10;
						g = j;
					}
					else if(board[i+5][j-1] == "b"){
						f = i+5;
						g = j-1;
					}
					else{
						f = i+5;
						g = j+1;
					}
					boardNumbers(board, f, g);
				}
			}
		}
	}
	public static void right(String[][]board){
		for(int i = 0; i<board.length; i++){
			for(int j = 0; j<board.length; j++){

			}
		}

	}
	public static void left(String[][]board){
		for(int i = 0; i<board.length; i++){
			for(int j = 0; j<board.length; j++){

			}
		}

	}
	public static void tr(String[][]board){
		for(int i = 0; i<board.length; i++){
			for(int j = 0; j<board.length; j++){

			}
		}

	}
	public static void tl(String[][]board){
		for(int i = 0; i<board.length; i++){
			for(int j = 0; j<board.length; j++){

			}
		}

	}
	public static void br(String[][]board){
		for(int i = 0; i<board.length; i++){
			for(int j = 0; j<board.length; j++){

			}
		}
	}
	public static void bl(String[][]board){
		for(int i = 0; i<board.length; i++){
			for(int j = 0; j<board.length; j++){

			}
		}

	}

	//use holder values to see which spaces are unavailable so you can tell which are available
	
}//class
