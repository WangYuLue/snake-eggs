package yard;

import java.awt.Color;
import java.awt.Font;
import java.awt.Frame;
import java.awt.Graphics;
import java.awt.Image;
import java.awt.event.KeyAdapter;
import java.awt.event.KeyEvent;
import java.awt.event.WindowAdapter;
import java.awt.event.WindowEvent;

import eggs.MyEgg;
import snake.MySnake;

@SuppressWarnings("serial")
public class MyYard extends Frame{
	public static final int ROWS=30;
	public static final int COLS=30;
	public static final int BLOCK_SIZE=15;
	public static boolean FLAG=true;
	public static boolean OVER=false;
	MySnake s=new MySnake();
	MyEgg e=new MyEgg();
	private Image offScreenImage;
	public void launch(){
		this.setBounds(200, 200, BLOCK_SIZE*COLS, BLOCK_SIZE*ROWS);
		this.addWindowListener(new WindowAdapter(){
			public void windowClosing(WindowEvent e){
				System.exit(0);
			}
		});
		this.setVisible(true);
		this.addKeyListener(new KeyMonitor());
		this.run();	
	}
	@Override
	public void paint(Graphics g) {
		g.setColor(Color.GRAY);
		g.fillRect(0, 0, BLOCK_SIZE*COLS, BLOCK_SIZE*ROWS);
		g.setColor(Color.BLACK);
		for (int x=1;x<COLS;x++){
			g.drawLine(BLOCK_SIZE*x, 0, BLOCK_SIZE*x, BLOCK_SIZE*ROWS);
		}
		for (int x=1;x<ROWS;x++){
			g.drawLine(0, BLOCK_SIZE*x, BLOCK_SIZE*ROWS, BLOCK_SIZE*x);
		}
		g.setColor(Color.RED);
		g.drawString("score: "+s.getScore(), 10, 60);
		s.eat(e);
		s.draw(g);
		checkDead();
		e.draw(g);
		if(OVER){
			g.setFont(new Font("宋体", Font.BOLD, 50));
			g.drawString("游戏结束", 100, 200);
			FLAG=false;
		}
	}
	@Override
	public void update(Graphics g) {
		if(offScreenImage == null) {
			offScreenImage = this.createImage(COLS * BLOCK_SIZE, ROWS * BLOCK_SIZE);
		}
		Graphics gOff = offScreenImage.getGraphics();
		paint(gOff);
		g.drawImage(offScreenImage, 0, 0,  null);
	}
	private void checkDead() {
		if(s.getHead().row<2||s.getHead().col<0||s.getHead().col>COLS||s.getHead().row>ROWS){
			OVER=true;
		}
		for(MySnake.Node n =s.getHead().next;n !=null;n=n.next){
			if(s.getHead().row == n.row && s.getHead().col == n.col){
				OVER=true;
			}
		}
	}
	public void run(){
		while(FLAG){
			repaint();
			try {
				Thread.sleep(150);
			} catch (InterruptedException e) {
				e.printStackTrace();
			}
		}
	}
	private class KeyMonitor extends KeyAdapter{
		@Override
		public void keyPressed(KeyEvent e) {
			s.keyPressed(e);
		}
	}
}
