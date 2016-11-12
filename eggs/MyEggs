package eggs;

import java.awt.Color;
import java.awt.Graphics;
import java.awt.Rectangle;
import java.util.Random;

import yard.MyYard;

public class MyEgg {
	int row,col;
	private Color color;
	private static Random r =new Random();
	public MyEgg(){
		this(r.nextInt(MyYard.ROWS-2)+2,r.nextInt(MyYard.COLS));
	}
	public MyEgg(int row,int col){
		this.row=row; 
		this.col=col;
	}
	public void draw (Graphics g){
		if(color == Color.PINK){
			color = Color.GREEN;
		}else{
			color = Color.PINK;
		}
		g.setColor(color);
		g.fillOval(MyYard.BLOCK_SIZE * col, MyYard.BLOCK_SIZE * row, MyYard.BLOCK_SIZE, MyYard.BLOCK_SIZE);
	}
	public void reAppear(){
		this.row=r.nextInt(MyYard.ROWS-2)+2;
		this.col=r.nextInt(MyYard.COLS);
	}
	public Rectangle getRect(){
		return new Rectangle(MyYard.BLOCK_SIZE*col,MyYard.BLOCK_SIZE*row,MyYard.BLOCK_SIZE,MyYard.BLOCK_SIZE);
	}
}
