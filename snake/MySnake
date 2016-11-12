package snake;

import java.awt.Color;
import java.awt.Graphics;
import java.awt.Rectangle;
import java.awt.event.KeyEvent;

import eggs.MyEgg;
import yard.MyYard;

public class MySnake {
	private Node head =null;
	private Node tail =null;
	private int SCORE =0;
	public MySnake(){
		tail=head=new Node(15,15,1);
	}
	public Node getHead(){
		return this.head;
	}
	public int getScore(){
		return this.SCORE;
	}
	public void addToHead(){
		Node node = null;
		switch (head.dir){
		case 1:
			node = new Node(head.row-1,head.col,1);
			break;
		case 2:
			node = new Node(head.row,head.col+1,2);
			break;
		case 3:
			node = new Node(head.row+1,head.col,3);
			break;
		case 4:
			node = new Node(head.row,head.col-1,4);
			break;
		}
		node.next=head;
		head.privious=node;
		head=node;
	}
	private void deleteFromTail() {
		tail=tail.privious;
		tail.next=null;
	}
	public void draw(Graphics g){
		addToHead();
		deleteFromTail();
		for(Node n=head;n!=null;n=n.next){
			n.draw(g);
		}
	}
	public class Node{
		public int row;
		public int col;
		int dir;
		public Node next;
		Node privious;
		Node(int row,int col,int dir){
			this.row=row;
			this.col=col;
			this.dir=dir;
		}
		public Rectangle getRect(){
			return new Rectangle(MyYard.BLOCK_SIZE*col,MyYard.BLOCK_SIZE*row,MyYard.BLOCK_SIZE,MyYard.BLOCK_SIZE);
		}
		void draw (Graphics g){
			g.setColor(Color.RED);
			g.fillRect(MyYard.BLOCK_SIZE * col, MyYard.BLOCK_SIZE * row, MyYard.BLOCK_SIZE, MyYard.BLOCK_SIZE);
		}
	}
	public void eat(MyEgg e){
			if(head.getRect().intersects(e.getRect())){
				e.reAppear();
				this.addToHead();
				SCORE +=5;
			}
		}
	public void keyPressed(KeyEvent e) {
		int key=e.getKeyCode();
		switch(key){
			case KeyEvent.VK_UP:
				if(head.dir!=3)
					head.dir = 1;
				break;
			case KeyEvent.VK_RIGHT:
				 if(head.dir!=4)
				head.dir = 2;
				break;
			case KeyEvent.VK_DOWN:
				 if(head.dir!=1)
				head.dir = 3;
				break;
			case KeyEvent.VK_LEFT:
				 if(head.dir!=2)
				head.dir = 4;
				break;
		}
	}
}
