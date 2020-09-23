## Figure

### Demo01_JFramePractise

```java
package Figure;

import java.awt.Container;
import java.awt.FlowLayout;
import java.awt.HeadlessException;
import java.awt.event.ActionEvent;
import java.awt.event.ActionListener;

import javax.swing.JButton;
import javax.swing.JFrame;
import javax.swing.JLabel;
import javax.swing.JTextField;

public class Demo01_JFramePractise extends JFrame implements ActionListener {
	private JLabel jl1 = null;
	private JTextField jtf1 = null;

	private JButton jb1 = null;
	private JLabel jl2 = null;

	public Demo01_JFramePractise() throws HeadlessException {
		super();
		// TODO Auto-generated constructor stub
	}

	public Demo01_JFramePractise(String title) throws HeadlessException {
		super("立方次幂的计算器");
		// TODO Auto-generated constructor stub
		this.setDefaultCloseOperation(Demo01_JFramePractise.EXIT_ON_CLOSE);

		Container container = this.getContentPane();

		container.setLayout(new FlowLayout());

		jl1 = new JLabel("请输入一个数字：");
		jtf1 = new JTextField(5);

		jb1 = new JButton("计算");
		jl2 = new JLabel("结果：");

		jb1.addActionListener(this);

		container.add(jl1);
		container.add(jtf1);

		container.add(jb1);
		container.add(jl2);

		this.setSize(300, 200);
		this.setLocation(200, 200);
		this.setVisible(true);
	}

	@Override
	public void actionPerformed(ActionEvent e) {
		// TODO Auto-generated method stub
		int total = Integer.parseInt(jtf1.getText());
		int value = total * total * total;
		jl2.setText("结果：" + value);
	}

	public static void main(String[] args) {
		// TODO Auto-generated method stub
		new Demo01_JFramePractise("立方次幂的计算器");
	}

}
```

### Demo01_SimpleFrame

```java
package Figure;

import java.awt.Container;
import java.awt.FlowLayout;
import java.awt.event.ActionEvent;
import java.awt.event.ActionListener;

import javax.swing.JButton;
import javax.swing.JFrame;
import javax.swing.JLabel;
import javax.swing.JTextField;

public class Demo01_SimpleFrame {

	public static void main(String[] args) {
		// TODO Auto-generated method stub
        JFrame jf=new JFrame("窗口1");
		jf.setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
        
        //获取jframe中的内容面板
        Container container=jf.getContentPane();
        //指定面板中组件的排列布局，流布局
        container.setLayout(new FlowLayout());
        //生成各组件
        JLabel jl1=new JLabel("加油费");
        JTextField jtf1=new JTextField(10);
        
        JLabel jl2=new JLabel("汽油价格");
        JTextField jtf2=new JTextField("5.98");
        
        JLabel jl3=new JLabel("行驶公里数");
        JTextField jtf3=new JTextField("200");
        
        JButton jb1=new JButton("计算");
        JLabel jl4=new JLabel("油耗为：");
        
        jb1.addActionListener(new ActionListener() {
			
			@Override
			public void actionPerformed(ActionEvent e) {
				// TODO Auto-generated method stub
				String total=jtf1.getText();
				double amount=Double.parseDouble(total);
				
				double price=Double.parseDouble(jtf2.getText());
				double kilos=Double.parseDouble(jtf3.getText());
				
				double value=amount/price/kilos*100;
				
				jl4.setText("油耗为："+value);
			}
		});
        
        //将所上的组件加入到面板中  
        container.add(jl1);
        container.add(jtf1);
        container.add(jl2);
        container.add(jtf2);
        container.add(jl3);
        container.add(jtf3);
        container.add(jb1);
        container.add(jl4);
        //大小，像素
        jf.setSize(300,200);
        jf.setLocation(200, 200);
        //一定要设置成可见的
        jf.setVisible(true);		
	}
}
```

### Demo02_JFrameCommon

```java
package Figure;

import java.awt.Container;
import java.awt.FlowLayout;
import java.awt.HeadlessException;
import java.awt.event.ActionEvent;
import java.awt.event.ActionListener;

import javax.swing.JButton;
import javax.swing.JFrame;
import javax.swing.JLabel;
import javax.swing.JTextField;

public class Demo02_JFrameCommon extends JFrame implements ActionListener {
	private JLabel jl1 = null;// =new JLabel("加油费");
	private JTextField jtf1 = null;// =new JTextField(10);

	private JLabel jl2 = null;// =new JLabel("汽油价格");
	private JTextField jtf2 = null;// =new JTextField("5.98");

	private JLabel jl3 = null;// =new JLabel("行驶公里数");
	private JTextField jtf3 = null;// =new JTextField("200");

	private JButton jb1 = null;// =new JButton("计算");
	private JLabel jl4 = null;// =new JLabel("油耗为：");

	public Demo02_JFrameCommon() throws HeadlessException {
		super();
		// TODO Auto-generated constructor stub
	}

	public Demo02_JFrameCommon(String title) throws HeadlessException {
		super(title);
		// TODO Auto-generated constructor stub
		this.setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);

		// 获取当前类的内容面板
		Container container = this.getContentPane();
		// 指定面板中组件的排列布局，流布局
		container.setLayout(new FlowLayout());
		// 生成各组件
		jl1 = new JLabel("加油费");
		jtf1 = new JTextField(10);

		jl2 = new JLabel("汽油价格");
		jtf2 = new JTextField("5.98");

		jl3 = new JLabel("行驶公里数");
		jtf3 = new JTextField("200");

		jb1 = new JButton("计算");
		jl4 = new JLabel("油耗为：");

		jb1.addActionListener(this);

		// 将所上的组件加入到面板中
		container.add(jl1);
		container.add(jtf1);
		container.add(jl2);
		container.add(jtf2);
		container.add(jl3);
		container.add(jtf3);
		container.add(jb1);
		container.add(jl4);

		this.setSize(300, 200);
		this.setLocation(200, 200);
		// 一定要设置成可见的
		this.setVisible(true);
	}

	@Override
	public void actionPerformed(ActionEvent e) {
		// TODO Auto-generated method stub
		String total = jtf1.getText();
		double amount = Double.parseDouble(total);

		double price = Double.parseDouble(jtf2.getText());
		double kilos = Double.parseDouble(jtf3.getText());

		double value = amount / price / kilos * 100;

		jl4.setText("油耗为：" + value);
	}

	public static void main(String[] args) {
		// TODO Auto-generated method stub
		new Demo02_JFrameCommon("耗油量计算");
	}
}
```
### Demo03_BorderLayout

```java
package Figure;

import java.awt.BorderLayout;
import java.awt.Container;
import java.awt.HeadlessException;

import javax.swing.JButton;
import javax.swing.JFrame;
import javax.swing.JPanel;
import javax.swing.JTextArea;
import javax.swing.JTextField;

public class Demo03_BorderLayout extends JFrame {

	JTextField jtf = null;// private可加可不加
	JTextArea jta = null;
	JButton jbgo = null;

	public Demo03_BorderLayout() throws HeadlessException {
		super();
		// TODO Auto-generated constructor stub
	}

	public Demo03_BorderLayout(String title) throws HeadlessException {
		super(title);
		// TODO Auto-generated constructor stub
		jtf = new JTextField(20);
		jtf.setText("上面的输入框");
		jta = new JTextArea(5, 20);
		jta.setText("中间的输入框，可以多行输入");
		jbgo = new JButton("计算结果");

		Container jp = this.getContentPane();
		jp.setLayout(new BorderLayout());

		jp.add(jtf, BorderLayout.NORTH);
		jp.add(jta, BorderLayout.CENTER);
		// jp.add(jbgo,BorderLayout.SOUTH);
		jp.add(jbgo, BorderLayout.EAST);
		jp.add(new JButton("西边按钮"), BorderLayout.WEST);

		this.setSize(400, 400);

		this.setLocation(200, 100);

		this.setVisible(true);

	}

	public static void main(String[] args) {
		new Demo03_BorderLayout("边界布局");
	}

}
```

### Demo04_GridLayout

```java
package Figure;

	import java.awt.BorderLayout;
	import java.awt.Container;
	import java.awt.GridBagConstraints;
	import java.awt.GridLayout;
	import java.awt.HeadlessException;

	import javax.swing.JButton;
	import javax.swing.JFrame;
	import javax.swing.JPanel;
	import javax.swing.JTextArea;
	import javax.swing.JTextField;
	import javax.swing.WindowConstants;

	public class Demo04_GridLayout extends JFrame{
		
		JTextField jtf=null;
		JTextArea jta=null;
		JButton jbgo=null;
		
		public Demo04_GridLayout() throws HeadlessException {
			super();
			// TODO Auto-generated constructor stub
		}

		public Demo04_GridLayout(String title) throws HeadlessException {
			super(title);
			// TODO Auto-generated constructor stub
			jtf=new JTextField(20);
			jtf.setText("上面的输入框");
			jta=new JTextArea(20, 30);
			jta.setText("中间的输入框，可以多行输入");
			jbgo=new JButton("第一个按钮");
			this.setDefaultCloseOperation(WindowConstants.EXIT_ON_CLOSE);		
			
			Container jp=this.getContentPane();
			jp.setLayout(new GridLayout(3,2,10,10));//行，列，行距，列距
			
			/*jp.add(jtf);
			jp.add(jta);
			jp.add(jbgo);
			jp.add(new JButton("第二个按钮"));*/
			
			for(int i=0;i<6;i++){
				jp.add(new JButton("按钮"+i));
			}
			
			this.setSize(300, 200);
			
			this.setLocation(200, 100);
			
			this.setVisible(true);
		}

		public static void main(String[] args) {
			new Demo04_GridLayout("网格布局");
		}

	}
```

### Demo05_NullLayout

```java
package Figure;

import java.awt.BorderLayout;
import java.awt.Container;
import java.awt.GridBagConstraints;
import java.awt.GridLayout;
import java.awt.HeadlessException;

import javax.swing.JButton;
import javax.swing.JFrame;
import javax.swing.JPanel;
import javax.swing.JTextArea;
import javax.swing.JTextField;
import javax.swing.WindowConstants;

public class Demo05_NullLayout extends JFrame{
	
	JTextField jtf=null;
	JTextArea jta=null;
	JButton jbgo=null;
	
	public Demo05_NullLayout() throws HeadlessException {
		super();
		// TODO Auto-generated constructor stub
	}

	public Demo05_NullLayout(String title) throws HeadlessException {
		super(title);
		// TODO Auto-generated constructor stub
		jtf=new JTextField(20);
		jtf.setText("上面的输入框");
		jta=new JTextArea(20, 30);
		jta.setText("中间的输入框，可以多行输入");
		jbgo=new JButton("第一个按钮");
		this.setDefaultCloseOperation(WindowConstants.EXIT_ON_CLOSE);		
		
		Container jp=this.getContentPane();
		jp.setLayout(null);//如果不显示设置null布局，那么缺省的是BorderLayout
		
		jp.add(jtf);
		jtf.setBounds(50, 20, 200, 50);
		jp.add(jta);
		jta.setBounds(50, 100,200,180);
		jp.add(jbgo);
		jbgo.setBounds(50, 300,100,60);
		
		
		this.setSize(400, 600);
		
		this.setLocation(200, 100);
		
		this.setVisible(true);
	}

	public static void main(String[] args) {
		new Demo05_NullLayout("自定义布局");
	}

}
```
### Demo06_BoxLayout

```java
package Figure;

import java.awt.BorderLayout;
import java.awt.Container;
import java.awt.GridBagConstraints;
import java.awt.GridLayout;
import java.awt.HeadlessException;

import javax.swing.BoxLayout;
import javax.swing.JButton;
import javax.swing.JFrame;
import javax.swing.JPanel;
import javax.swing.JTextArea;
import javax.swing.JTextField;
import javax.swing.WindowConstants;

public class Demo06_BoxLayout extends JFrame{
	
	JTextField jtf=null;
	JTextArea jta=null;
	JButton jbgo=null;
	JButton jbtake=null;
	
	public Demo06_BoxLayout() throws HeadlessException {
		super();
		// TODO Auto-generated constructor stub
	}

	public Demo06_BoxLayout(String title) throws HeadlessException {
		super(title);
		// TODO Auto-generated constructor stub
		jtf=new JTextField(20);
		jtf.setText("上面的输入框");
		jta=new JTextArea(20, 30);
		jta.setText("中间的输入框，可以多行输入");
		jbgo=new JButton("出发");
		jbtake=new JButton("行动");
		this.setDefaultCloseOperation(WindowConstants.EXIT_ON_CLOSE);		
		
		Container jp=this.getContentPane();
		jp.setLayout(new BoxLayout(jp, BoxLayout.X_AXIS));//如果不显示设置null布局，那么缺省的是BorderLayout
		
		/*
		 * 生成主面板的两个子面板，子面板里面加上纵向排列的对应组件
		 */
		JPanel jp1=new JPanel();
		jp1.setLayout(new BoxLayout(jp1, BoxLayout.Y_AXIS));
		
		jp1.add(jtf);
		jp1.add(jbgo);
				
		JPanel jp2=new JPanel();
		jp2.setLayout(new BoxLayout(jp2, BoxLayout.Y_AXIS));

		jp2.add(jta);
		jp2.add(jbtake);
		
		//子面板作为一个普通组件一样加到主面板里面去。横向的排列
		jp.add(jp1);
		jp.add(jp2);
		
		this.setSize(400, 300);
		
		this.setLocation(200, 100);
		
		this.setVisible(true);
	}

	public static void main(String[] args) {
		new Demo06_BoxLayout("网格布局");
	}

}
```

### Demo07_Calculator

```java
package Figure;

import java.awt.BorderLayout;
import java.awt.Container;
import java.awt.GridLayout;
import java.awt.HeadlessException;

import javax.swing.JButton;
import javax.swing.JFrame;
import javax.swing.JPanel;
import javax.swing.JTextArea;
import javax.swing.JTextField;

public class Demo07_Calculator extends JFrame{
	
	public Demo07_Calculator() throws HeadlessException {
		super();
		// TODO Auto-generated constructor stub
	}

	public Demo07_Calculator(String title) throws HeadlessException {
		super(title);
		// TODO Auto-generated constructor stub
	    //主面板获取
		Container jp=this.getContentPane();
		jp.setLayout(new BorderLayout());
		
		JTextField jtf=new JTextField("计算器的公式：");
		jp.add(jtf, BorderLayout.NORTH);
		
		//生成一个子面板，作为数字键等
		JPanel keys=new JPanel();
		keys.setLayout(new GridLayout(5, 3, 5, 5));
		
		for(int i=0;i<10;i++){
			keys.add(new JButton(""+i));
		}
		
		keys.add(new JButton("."));
		keys.add(new JButton("="));
		keys.add(new JButton("清空"));
		keys.add(new JButton("退格"));
		
		//将第一个子面板加入到主面板中间
		jp.add(keys,BorderLayout.CENTER);
		
		//生成另一个子面板，作为符号键
		JPanel symbols=new JPanel();
		symbols.setLayout(new GridLayout(4, 1, 5, 5));
		symbols.add(new JButton("  +  "));
		symbols.add(new JButton("  -  "));
		symbols.add(new JButton("  *  "));
		symbols.add(new JButton("  /  "));
		//将第二个子面板加入到主面板的东边
		jp.add(symbols,BorderLayout.EAST);
		
		this.setSize(400, 400);
		
		this.setLocation(200, 100);
		
		this.setVisible(true);
		
	}

	public static void main(String[] args) {
		new Demo07_Calculator("计算机界面");
	}

}
```

### Demo07_Calculator1

```java
package Figure;

	import java.awt.BorderLayout;
	import java.awt.Container;
	import java.awt.GridLayout;
	import java.awt.HeadlessException;
	import java.awt.event.ActionEvent;
	import java.awt.event.ActionListener;

	import javax.swing.JButton;
	import javax.swing.JFrame;
	import javax.swing.JPanel;
	import javax.swing.JTextArea;
	import javax.swing.JTextField;
	/*
	 * 第一步，类实现ActionListener接口
	 */
	public class Demo07_Calculator1 extends JFrame implements ActionListener{
		JTextField jtf=null;
		
		public Demo07_Calculator1() throws HeadlessException {
			super();
			// TODO Auto-generated constructor stub
		}

		public Demo07_Calculator1(String title) throws HeadlessException {
			super(title);
			// TODO Auto-generated constructor stub
		    //主面板获取
			Container jp=this.getContentPane();
			jp.setLayout(new BorderLayout());
			
			jtf=new JTextField("");
			jp.add(jtf, BorderLayout.NORTH);
			
			//生成一个子面板，作为数字键等
			JPanel keys=new JPanel();
			keys.setLayout(new GridLayout(5, 3, 5, 5));
			
			for(int i=0;i<10;i++){
				JButton jbtemp=new JButton(""+i);
				keys.add(jbtemp);
				
				/*
				 * 3）关联组件和事件监听器（addActionListener）。
				 * 因为本类已经实现了ActionListener接口，
				 * 所以 this可以作为一个ActionListener接口的
				 * 实现类使用多态传递给此接口引用可以传递。
				 */
				jbtemp.addActionListener(this);
				
			}
			JButton  jbdot=new JButton(".");
			keys.add(jbdot);
			jbdot.addActionListener(this);
			
			keys.add(new JButton("="));
			keys.add(new JButton("清空"));
			keys.add(new JButton("退格"));
			
			//将第一个子面板加入到主面板中间
			jp.add(keys,BorderLayout.CENTER);
			
			//生成另一个子面板，作为符号键
			JPanel symbols=new JPanel();
			symbols.setLayout(new GridLayout(4, 1, 5, 5));
			symbols.add(new JButton("  +  "));
			symbols.add(new JButton("  -  "));
			symbols.add(new JButton("  *  "));
			symbols.add(new JButton("  /  "));
			//将第二个子面板加入到主面板的东边
			jp.add(symbols,BorderLayout.EAST);
			
			this.setSize(400, 400);
			
			this.setLocation(200, 100);
			
			this.setVisible(true);
			
		}
		/*
		 * 2)在重写接口对应的方法中，增加对应的事件处理代码
		 * 
		 */
		@Override
		public void actionPerformed(ActionEvent e) {
			// TODO Auto-generated method stub
			String command=e.getActionCommand();
			if(command.equals("1")){
				jtf.setText("你敲了1");
			}else if(command.equals("2")){
				jtf.setText("你敲了2");
			}else if(command.equals("3")){
				jtf.setText("你敲了3");
			}else if(command.equals(".")){
				jtf.setText("你敲了.");
			}
		}

		public static void main(String[] args) {
			new Demo07_Calculator("计算机界面");
		}



	}
```
### Demo07_VIP

```java
package Figure;

import java.awt.BorderLayout;
import java.awt.Container;
import java.awt.FlowLayout;
import java.awt.GridLayout;
import java.awt.HeadlessException;

import javax.swing.JComboBox;
import javax.swing.JFrame;
import javax.swing.JLabel;
import javax.swing.JPanel;
import javax.swing.JTextField;

public class Demo07_VIP {

	public static void main(String[] args) {

		JComboBox jcb = null;

		JFrame jf = new JFrame("会员登记录入");

		JPanel jp = new JPanel();
		jp.setLayout(new BorderLayout());

		JPanel jp1 = new JPanel();
		jp1.setLayout(new FlowLayout());

		JPanel jp2 = new JPanel();
		jp2.setLayout(new GridLayout(3, 4, 5, 5));

		JPanel jp3 = new JPanel();
		jp3.setLayout(new GridLayout(1, 2, 5, 5));

		JLabel jl0 = new JLabel("会员登记录入");
		JLabel jl1 = new JLabel("姓名");
		JLabel jl2 = new JLabel("性别");
		JLabel jl3 = new JLabel("联系电话");
		JLabel jl4 = new JLabel("类型");
		JLabel jl5 = new JLabel("折扣");
		JLabel jl6 = new JLabel("是否挂失");
		JLabel jl7 = new JLabel("工作单位");

		JTextField jtf1 = new JTextField("刘富贵");
		JTextField jtf2 = new JTextField("女");
		JTextField jtf3 = new JTextField("0635-567890");
		JTextField jtf4 = new JTextField("普通会员");
		JTextField jtf5 = new JTextField("0.8");
		JTextField jtf7 = new JTextField("上海交通运输公司");

		jp1.add(jl0);

		jp2.add(jl1);
		jp2.add(jtf1);
		jp2.add(jl2);
		jp2.add(jtf2);
		jp2.add(jl3);
		jp2.add(jtf3);
		jp2.add(jl4);
		jp2.add(jtf4);
		jp2.add(jl5);
		jp2.add(jtf5);
		jp2.add(jl6);
		String[] str = { "否", "是" };
		jcb = new JComboBox(str);
		jp2.add(jcb);

		jp3.add(jl7);
		jp3.add(jtf7);

		jf.add(jp);
		jp.add(jp1, BorderLayout.NORTH);
		jf.setFont(new java.awt.Font("宋体", 1, 18));// 编辑字体
		jp.add(jp2, BorderLayout.CENTER);
		jp.add(jp3, BorderLayout.SOUTH);

		jf.setSize(500, 200);
		jf.setLocation(5, 0);
		jf.setVisible(true);
	}

}
```

### Demo08_practise

```java
package Figure;

import java.awt.Container;
import java.awt.HeadlessException;
import java.awt.event.FocusEvent;
import java.awt.event.FocusListener;
import java.awt.event.MouseEvent;
import java.awt.event.MouseListener;

import javax.swing.JButton;
import javax.swing.JFrame;
import javax.swing.JTextArea;
import javax.swing.JTextField;
import javax.swing.SwingConstants;
import javax.swing.WindowConstants;

public class Demo08_practise extends JFrame implements FocusListener, MouseListener {

	JTextField jtf = null;
	JTextArea jta = null;
	JButton jb = null;

	public Demo08_practise() throws HeadlessException {
		super();
		// TODO Auto-generated constructor stub
	}

	public Demo08_practise(String title) throws HeadlessException {
		super(title);
		// TODO Auto-generated constructor stub
		jtf = new JTextField(30);
		jtf.setText("鼠标坐标：");
		jta = new JTextArea(30, 30);
		jb = new JButton("按钮");
		this.setDefaultCloseOperation(WindowConstants.EXIT_ON_CLOSE);

		Container cp = this.getContentPane();
		cp.setLayout(null);

		cp.add(jtf);
		jtf.setBounds(50, 20, 200, 180);

		cp.add(jb);
		jb.setBounds(50, 250, 200, 50);
		jtf.addMouseListener(this);
		jtf.addFocusListener(this);

		this.setSize(400, 500);
		this.setLocation(200, 100);
		this.setVisible(true);
	}

	public static void main(String[] args) {
		new Demo08_practise("监听器");
	}

	@Override
	public void focusLost(FocusEvent e) {
		// TODO Auto-generated method stub
		jtf.setText(jtf.getText() + "\n失去焦点了！");
	}

	@Override
	public void focusGained(FocusEvent e) {
		// TODO Auto-generated method stub
		jtf.setText(jtf.getText() + "\n得到焦点了！");
	}

	@Override
	public void mousePressed(MouseEvent e) {
		// TODO Auto-generated method stub
	}

	@Override
	public void mouseReleased(MouseEvent e) {
		// TODO Auto-generated method stub
	}

	@Override
	public void mouseExited(MouseEvent e) {
		// TODO Auto-generated method stub
		jtf.setText(jtf.getText() + "\n鼠标挪出文本输入框");
	}

	@Override
	public void mouseEntered(MouseEvent e) {
		// TODO Auto-generated method stub
		jtf.setText(jtf.getText() + "\n鼠标位置：(" + e.getX() + "," + e.getY() + ")");
	}

	@Override
	public void mouseClicked(MouseEvent e) {
		// TODO Auto-generated method stub
		jtf.setText(jtf.getText() + "\n鼠标点击文本输入框了！坐标为(" + e.getX() + "," + e.getY() + ")");
	}

}
```

### Demo08_SeveralEvent

```java
package Figure;

import java.awt.BorderLayout;
import java.awt.Container;
import java.awt.GridBagConstraints;
import java.awt.GridLayout;
import java.awt.HeadlessException;
import java.awt.event.FocusEvent;
import java.awt.event.FocusListener;
import java.awt.event.KeyEvent;
import java.awt.event.KeyListener;
import java.awt.event.MouseEvent;
import java.awt.event.MouseListener;
import java.awt.event.WindowEvent;
import java.awt.event.WindowListener;

import javax.swing.JButton;
import javax.swing.JFrame;
import javax.swing.JPanel;
import javax.swing.JScrollPane;
import javax.swing.JTextArea;
import javax.swing.JTextField;
import javax.swing.WindowConstants;

public class Demo08_SeveralEvent extends JFrame implements FocusListener,MouseListener{

	JTextField jtf = null;
	JTextArea jta = null;
	JButton jbgo = null;

	public Demo08_SeveralEvent() throws HeadlessException {
		super();
		// TODO Auto-generated constructor stub
	}

	public Demo08_SeveralEvent(String title) throws HeadlessException {
		super(title);
		// TODO Auto-generated constructor stub
		jtf = new JTextField(20);
		jtf.setText("上面的输入框");
		jta = new JTextArea(20, 30);
		jta.setText("中间的输入框，可以多行输入");
		jbgo = new JButton("第一个按钮");
		// this.setDefaultCloseOperation(WindowConstants.EXIT_ON_CLOSE);

		Container jp = this.getContentPane();
		jp.setLayout(null);// 如果不显示设置null布局，那么缺省的是BorderLayout

		JScrollPane jsp = new JScrollPane(jta);

		jp.add(jsp);
		jsp.setBounds(50, 20, 200, 180);

		jp.add(jtf);
		jtf.setBounds(50, 250, 200, 50);
		jtf.addMouseListener(this);

		jtf.addFocusListener(this);

		jtf.addKeyListener(new KeyListener() {
			@Override
			public void keyTyped(KeyEvent e) {
				// TODO Auto-generated method stub
			}
			@Override
			public void keyReleased(KeyEvent e) {
				// TODO Auto-generated method stub
			}

			@Override
			public void keyPressed(KeyEvent e) {
				// TODO Auto-generated method stub
				jta.setText(jta.getText() + "\n正在输入:字母为" + e.getKeyChar()
						+ ",ASC码为：" + e.getKeyCode());
			}
		});

		jp.add(jbgo);
		jbgo.setBounds(50, 320, 100, 60);
		this.addWindowListener(new WindowListener() {
			@Override
			public void windowOpened(WindowEvent e) {
				// TODO Auto-generated method stub
			}
			@Override
			public void windowIconified(WindowEvent e) {
				// TODO Auto-generated method stub
			}
			@Override
			public void windowDeiconified(WindowEvent e) {
				// TODO Auto-generated method stub
			}
			@Override
			public void windowDeactivated(WindowEvent e) {
				// TODO Auto-generated method stub
				jta.setText(jta.getText() + "\n窗口去激活了！");
			}
			@Override
			public void windowClosing(WindowEvent e) {
				// TODO Auto-generated method stub
				System.out.println("窗口关闭中");
			}

			@Override
			public void windowClosed(WindowEvent e) {
				// TODO Auto-generated method stub
				System.out.println("窗口关闭了");
			}

			@Override
			public void windowActivated(WindowEvent e) {
				// TODO Auto-generated method stub
				jta.setText(jta.getText() + "\n窗口激活了！");
			}
		});

		this.setSize(400, 500);

		this.setLocation(200, 100);

		this.setVisible(true);
	}

	public static void main(String[] args) {
		new Demo08_SeveralEvent("网格布局");
	}

	@Override
	public void focusLost(FocusEvent e) {
		// TODO Auto-generated method stub
		jta.setText(jta.getText() + "\n文本输入框失去焦点了！");
	}

	@Override
	public void focusGained(FocusEvent e) {
		// TODO Auto-generated method stub
		jta.setText(jta.getText() + "\n文本输入框得到焦点了！");
	}

	public void mouseReleased(MouseEvent e) {
		// TODO Auto-generated method stub
	}

	@Override
	public void mousePressed(MouseEvent e) {
		// TODO Auto-generated method stub

	}

	@Override
	public void mouseExited(MouseEvent e) {
		// TODO Auto-generated method stub
		jta.setText(jta.getText() + "\n鼠标挪出文本输入框了！");
	}

	@Override
	public void mouseEntered(MouseEvent e) {
		// TODO Auto-generated method stub
		jta.setText(jta.getText() + "\n鼠标挪进文本输入框了！x=" + e.getX()
				+ ",y=" + e.getY());
	}

	@Override
	public void mouseClicked(MouseEvent e) {
		// TODO Auto-generated method stub
		jta.setText(jta.getText() + "\n鼠标点击文本输入框了！位置为x=" + e.getX()
				+ ",y=" + e.getY());
	}

}
```
### Demo09_JComboBox

```java
package Figure;

import java.awt.Container;
import java.awt.GridLayout;
import java.awt.event.ActionEvent;
import java.awt.event.ActionListener;
import java.awt.event.ItemEvent;
import java.awt.event.ItemListener;

import javax.swing.BorderFactory;
import javax.swing.Box;
import javax.swing.JComboBox;
import javax.swing.JFrame;
import javax.swing.border.Border;

public class Demo09_JComboBox extends JFrame{
	
	JComboBox<String> countries=null;
	JComboBox<Phone> phones=null;
	
	
	public Demo09_JComboBox(String title){
		super(title);
		this.setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
        
        //获取当前类的内容面板
 /*       Container container=this.getContentPane();
        container.setLayout(new GridLayout(1,2,10,10));*/

		String[] strs=new String[]{"中国","USA","德国","法国"};
        countries=new JComboBox<>(strs);
        
        countries.addActionListener(new ActionListener() {
			
			@Override
			public void actionPerformed(ActionEvent e) {
				// TODO Auto-generated method stub
				System.out.println("我选择了第"+countries.getSelectedIndex()+
						"个国家，为"+countries.getSelectedItem());
			}
		});
        
        Phone[] phs=new Phone[]{new Phone("小米", 1800),
        		                new Phone("华为", 3000),
        		                new Phone("iPhone", 5800),
        		                new Phone("OPPO", 1500)};
        
        phones=new JComboBox<Phone>(phs);
        phones.addItemListener(new ItemListener() {
			
			@Override
			public void itemStateChanged(ItemEvent e) {
				// TODO Auto-generated method stub
				System.out.println("我选择了第"+phones.getSelectedIndex()+
						"个手机，为"+phones.getSelectedItem());	
				System.out.println(e.getStateChange());
			}
		});
        
        //BoxLayout面板的另外一种实现方式
        Box boxv1=Box.createVerticalBox();
        
		boxv1.add(countries);
		
		countries.setBorder(BorderFactory.createTitledBorder("请选择国别："));
		boxv1.add(Box.createVerticalStrut(200));
		
		//BoxLayout面板的另外一种实现方式
        Box boxv2=Box.createVerticalBox();
        
		boxv2.add(phones);
		phones.setBorder(BorderFactory.createTitledBorder("请选择手机品牌："));
		boxv2.add(Box.createVerticalStrut(200));
		
		
		//主面板，横向的Box
        Box boxh1=Box.createHorizontalBox();
        boxh1.add(boxv1);
        boxh1.add(boxv2);
        
		//将Box主面板设为窗口的主面板
		this.setContentPane(boxh1);
        
        this.pack();
        this.setLocation(200, 200);
        //一定要设置成可见的
        this.setVisible(true);	
	}

	public static void main(String[] args) {
		new Demo09_JComboBox("组合框练习");
	}
}
```

### Demo10_JCheckBoxAndJRadioButtion

```java
package Figure;

import java.awt.Container;
import java.awt.GridLayout;
import java.awt.Label;
import java.awt.event.ActionEvent;
import java.awt.event.ActionListener;
import java.awt.event.ItemEvent;
import java.awt.event.ItemListener;
import java.util.List;

import javax.swing.BorderFactory;
import javax.swing.Box;
import javax.swing.ButtonGroup;
import javax.swing.JCheckBox;
import javax.swing.JComboBox;
import javax.swing.JFrame;
import javax.swing.JList;
import javax.swing.JRadioButton;
import javax.swing.ListSelectionModel;
import javax.swing.border.Border;
import javax.swing.event.ListSelectionEvent;
import javax.swing.event.ListSelectionListener;

public class Demo10_JCheckBoxAndJRadioButtion extends JFrame{
	
	public Demo10_JCheckBoxAndJRadioButtion(String title){
		super(title);
		this.setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
        

        //BoxLayout面板的另外一种实现方式,左边的一个
        Box boxv1=Box.createVerticalBox();
        
        String[] strs=new String[]{"跑步                 ","篮球                        ","柔道                      ",
        		                   "跳高                ","网球                          "};
        JList<String> jl=new JList<>(strs);
        jl.setBorder(BorderFactory.createTitledBorder("请选择你喜欢的运动:"));
        jl.setSelectionMode(ListSelectionModel.MULTIPLE_INTERVAL_SELECTION );

        boxv1.add(jl);
		boxv1.add(Box.createVerticalStrut(20));
        jl.addListSelectionListener(new ListSelectionListener() {
			
			@Override
			public void valueChanged(ListSelectionEvent e) {
				// TODO Auto-generated method stub
				int[] indices=jl.getSelectedIndices();
				List<String> list=jl.getSelectedValuesList();
				for(int i=0;i<list.size();i++){
					System.out.println("第"+indices[i]+"元素为"+list.get(i));
				}
			}
		});
		
		//右边的一个子面板		
        Box boxv2=Box.createVerticalBox();
        boxv2.add(new Label("请选择字体的样式:"));
        JCheckBox jcb1=new JCheckBox("黑体");
        jcb1.addItemListener(new ItemListener() {
			
			@Override
			public void itemStateChanged(ItemEvent e) {
				// TODO Auto-generated method stub
	            System.out.println("是否为选中:"+jcb1.isSelected());
				System.out.println(e.getStateChange());	
			}
		});

        JCheckBox jcb2=new JCheckBox("斜体");
        
        jcb2.addActionListener(new ActionListener() {
			
			@Override
			public void actionPerformed(ActionEvent e) {
				// TODO Auto-generated method stub
		           System.out.println("是否为选中:"+jcb2.isSelected());
                   System.out.println(e.getActionCommand());
			}
		});
        
        boxv2.add(jcb1);
        boxv2.add(jcb2);
        boxv2.add(Box.createVerticalStrut(100));
        
	
		//主面板，横向的Box
        Box boxh1=Box.createHorizontalBox();
        boxh1.add(boxv1);
        boxh1.add(boxv2);
		
        
		//将Box主面板设为窗口的主面板
		this.setContentPane(boxh1);
        
        this.pack();
        this.setLocation(200, 200);
        //一定要设置成可见的
        this.setVisible(true);	
	}

	public static void main(String[] args) {
		new Demo10_JCheckBoxAndJRadioButtion("组合框练习");
	}
}
```

### Demo11_FontSetMenu

```java
package Figure;

import java.awt.BorderLayout;
import java.awt.Color;
import java.awt.Container;
import java.awt.Font;
import java.awt.Label;
import java.awt.event.ActionEvent;
import java.awt.event.ActionListener;
import java.awt.event.KeyEvent;

import javax.swing.ButtonGroup;
import javax.swing.JCheckBoxMenuItem;
import javax.swing.JFrame;
import javax.swing.JMenu;
import javax.swing.JMenuBar;
import javax.swing.JMenuItem;
import javax.swing.JRadioButtonMenuItem;
import javax.swing.JTextArea;
import javax.swing.WindowConstants;


public class Demo11_FontSetMenu extends JFrame implements ActionListener{
	
	JTextArea txtDemo=new JTextArea("里面的文字需要格式通过菜单设置",10,30);
	JMenuBar jmb=new JMenuBar();
	
	JMenu fontMenu=new JMenu("字体");
	JMenu helpMenu=new JMenu("帮助");
	
	
	JMenu styleMenu=new JMenu("样式");
	JMenu colorMenu=new JMenu("颜色");
	
	JMenuItem exitItem=new JMenuItem("退出");
	JMenuItem aboutItem=new JMenuItem("关于");
	
	JCheckBoxMenuItem boldItem=new JCheckBoxMenuItem("粗体");
	JCheckBoxMenuItem italicItem=new JCheckBoxMenuItem("斜体");
	
	JRadioButtonMenuItem redItem=new JRadioButtonMenuItem("红色");
	JRadioButtonMenuItem greenItem=new JRadioButtonMenuItem("绿色");
	JRadioButtonMenuItem blueItem=new JRadioButtonMenuItem("蓝色");
	
	public Demo11_FontSetMenu(String title){
		super(title);
		this.setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
        
        Container container=this.getContentPane();
        
        container.add(new Label(""), BorderLayout.NORTH);
        
        container.add(txtDemo, BorderLayout.CENTER);
        
        this.setJMenuBar(jmb);
        jmb.add(fontMenu);
        jmb.add(helpMenu);
        
        //加快捷键F，alt+F就可以打开字体菜单
        fontMenu.setMnemonic(KeyEvent.VK_F);
        
        fontMenu.add(styleMenu);
        fontMenu.add(colorMenu);
        
        fontMenu.addSeparator();
        
        fontMenu.add(exitItem);
        fontMenu.add(aboutItem);
        
        styleMenu.add(boldItem);
        styleMenu.add(italicItem);
        
        //加快捷键I，alt+I就可以勾选或去选斜体复选框
        italicItem.setMnemonic(KeyEvent.VK_I);
        
        ButtonGroup bg=new ButtonGroup();
        bg.add(redItem);
        bg.add(greenItem);
        bg.add(blueItem);
        
        colorMenu.add(redItem);
        colorMenu.add(greenItem);
        colorMenu.add(blueItem);
        
        exitItem.addActionListener(this);
        redItem.addActionListener(this);
        greenItem.addActionListener(this);
        blueItem.addActionListener(this);
        boldItem.addActionListener(this);
        italicItem.addActionListener(this);

        this.pack();
        this.setLocation(200, 200);
        //一定要设置成可见的
        this.setVisible(true);	
	}
	
	
	@Override
	public void actionPerformed(ActionEvent e) {
		// TODO Auto-generated method stub
		int bold=Font.PLAIN, italic=Font.PLAIN;
		String command=e.getActionCommand();
		if("退出".equals(command)){
			System.exit(WindowConstants.EXIT_ON_CLOSE);
		}else if("红色".equals(command)){
			txtDemo.setForeground(Color.red);
		}else if("绿色".equals(command)){
			txtDemo.setForeground(Color.green);
		}else if("蓝色".equals(command)){
			txtDemo.setForeground(Color.blue);
		}else if("粗体".equals(command)){
			bold=boldItem.isSelected()?Font.BOLD:Font.PLAIN;
		}else if("斜体".equals(command)){
			italic=italicItem.isSelected()?Font.ITALIC:Font.PLAIN;
		}
		
		txtDemo.setFont(new Font("楷体",bold+italic,26));
		
	}

	public static void main(String[] args) {
		new Demo11_FontSetMenu("菜单练习");
	}
}
```
### Demo11_JList

```java
package Figure;

import java.awt.Container;
import java.awt.GridLayout;
import java.awt.Label;
import java.awt.event.ActionEvent;
import java.awt.event.ActionListener;
import java.awt.event.ItemEvent;
import java.awt.event.ItemListener;

import javax.swing.BorderFactory;
import javax.swing.Box;
import javax.swing.ButtonGroup;
import javax.swing.JCheckBox;
import javax.swing.JComboBox;
import javax.swing.JFrame;
import javax.swing.JRadioButton;
import javax.swing.border.Border;

public class Demo11_JList extends JFrame{
	
	public Demo11_JList(String title){
		super(title);
		this.setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
        

        //BoxLayout面板的另外一种实现方式,左边的一个
        Box boxv1=Box.createVerticalBox();
        
        JRadioButton jrb1=new JRadioButton("男");
        jrb1.setActionCommand("men");
        JRadioButton jrb2=new JRadioButton("女");
        jrb2.setActionCommand("women");
        
        ButtonGroup bg=new ButtonGroup();
        bg.add(jrb1);
        bg.add(jrb2);
        
        boxv1.add(new Label("请选择性别:"));
		boxv1.add(jrb1);
		boxv1.add(jrb2);
		boxv1.add(Box.createVerticalStrut(100));
		jrb1.addItemListener(new ItemListener() {
			
			@Override
			public void itemStateChanged(ItemEvent e) {
				// TODO Auto-generated method stub
//				System.out.println(bg.getSelection().getActionCommand());
				System.out.println("是否为选中:"+jrb1.isSelected());
				
				System.out.println(e.getStateChange());	
			}
		});
		
		//右边的一个子面板		
        Box boxv2=Box.createVerticalBox();
        boxv2.add(new Label("请选择字体的样式:"));
        JCheckBox jcb1=new JCheckBox("黑体");
        jcb1.addItemListener(new ItemListener() {
			
			@Override
			public void itemStateChanged(ItemEvent e) {
				// TODO Auto-generated method stub
	            System.out.println("是否为选中:"+jcb1.isSelected());
				System.out.println(e.getStateChange());	
			}
		});

        JCheckBox jcb2=new JCheckBox("斜体");
        
        jcb2.addActionListener(new ActionListener() {
			
			@Override
			public void actionPerformed(ActionEvent e) {
				// TODO Auto-generated method stub
		           System.out.println("是否为选中:"+jcb2.isSelected());
                   System.out.println(e.getActionCommand());
			}
		});
        
        boxv2.add(jcb1);
        boxv2.add(jcb2);
        boxv2.add(Box.createVerticalStrut(100));
        
	
		//主面板，横向的Box
        Box boxh1=Box.createHorizontalBox();
        boxh1.add(boxv1);
        boxh1.add(boxv2);
		
        
		//将Box主面板设为窗口的主面板
		this.setContentPane(boxh1);
        
        this.pack();
        this.setLocation(200, 200);
        //一定要设置成可见的
        this.setVisible(true);	
	}

	public static void main(String[] args) {
		new Demo11_JList("组合框练习");
	}
}
```

### Exer02_FrameCaculator

```java
package Figure;

import java.awt.*;
import java.awt.event.*;
import javax.swing.*;

public class Exer02_FrameCaculator extends JFrame implements ActionListener {	
	JTextField result;		// 显示输入的数字和计算结果
	int calculate_type = 0; // 0，无运算；1、2、3、4分别代表加减乘除
	
	Exer02_FrameCaculator(){	
		JPanel jp;
		JButton jb;
		jp = new JPanel();
		jp.setLayout(new BorderLayout());
		
		// 创建文本条，不允许编辑，添加到窗口上方
		result = new JTextField();
		result.setEditable(false);
		jp.add(result,BorderLayout.NORTH);
		
		// 窗口中间添加数字按钮、清空、退格、小数点按钮
		// 因为 BorderLayout 将窗口分为上下左右中五个区域，每个区域只能添加一个组件
		// 所以先在中间区域添加 keyPanel，再往keyPanel上添加数字按钮，实现容器的嵌套
		JPanel keyPanel = new JPanel();
		keyPanel.setLayout(new GridLayout(5,3));
		for(int i=1;i<=9;i++){
			jb = new JButton(""+i);
			jb.addActionListener(this);
			keyPanel.add(jb);
		}
		jb = new JButton("0");
		keyPanel.add(jb);
		jb.addActionListener(this);
		jb = new JButton("清空");
		keyPanel.add(jb);
		jb.addActionListener(this);
		jb = new JButton("退格");
		keyPanel.add(jb);
		jb.addActionListener(this);
		
		jb = new JButton(".");
		jb.addActionListener(this);	
		keyPanel.add(jb);
		
		jb = new JButton("=");
		jb.addActionListener(this);	
		keyPanel.add(jb);
		
		jp.add(keyPanel,BorderLayout.CENTER);
		
		JPanel operatorPanel = new JPanel();
		operatorPanel.setLayout(new GridLayout(4,1));
		jb = new JButton("+");
		jb.addActionListener(this);
		operatorPanel.add(jb);
		
		jb = new JButton("-");
		jb.addActionListener(this);
		operatorPanel.add(jb);
		
		jb = new JButton("*");
		jb.addActionListener(this);
		operatorPanel.add(jb);
		
		jb = new JButton("/");
		jb.addActionListener(this);
		operatorPanel.add(jb);
		jp.add(operatorPanel,BorderLayout.EAST);	
		
		//添加JPanel容器到窗体中
		setContentPane(jp);
		
		//设置窗体的标题、大小、可见性及关闭动作
		setTitle("计算器");
		setSize(340,260);
		setVisible(true);
		// 设置窗口关闭时，程序退出
		setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);		
	}
	
	public void actionPerformed(ActionEvent e) { 
		String cmd = e.getActionCommand();
		String c = result.getText();
		
		if(cmd.equals("清空")){
			result.setText("");
		}
		else if(cmd.equals("退格")){
			if(c.length() > 0){
				String slast = c.substring(c.length() - 1); 
				if(slast.equals("+") || slast.equals("-") || slast.equals("*") || slast.equals("/")){
					calculate_type = 0; // 如果删除了运算符，将计算类型恢复为未确定状态
				}		
				result.setText(c.substring(0,c.length() - 1));
			}
		}
		else if(cmd.compareTo("0") >= 0 && cmd.compareTo("9") <= 0){
			result.setText(c + cmd);
		}
		else if(cmd.equals(".")){
			result.setText(c + cmd);
		}
		else if(cmd.equals("+") || cmd.equals("-") || cmd.equals("*") || cmd.equals("/")){
			if(calculate_type == 0){ // 自上次计算完成后，第一次点击运算符
				result.setText(c + cmd);
				judgeCalculateType(cmd); // 判断计算类型
			}
			else{	// 自上次计算完成后，第二次点击运算符，触发计算
				calculate();
				result.setText(result.getText() + cmd);
				judgeCalculateType(cmd); // 判断计算类型
			}
		}
		else if(cmd.equals("=")){//点击  = 进行计算
			try{
				calculate();
			}
			catch(Exception exp){
			JOptionPane.showMessageDialog(this, "输入错误，请检查输出或重新启动程序");
			}
		}		
	}
	
	// 判断计算类型
	private void judgeCalculateType(String cmd){
		if(cmd.equals("+"))
			calculate_type = 1; // 记录运算类型
		else if(cmd.equals("-"))
			calculate_type = 2;
		else if(cmd.equals("*"))
			calculate_type = 3;
		else
			calculate_type = 4;
	}
	
	// 完成计算功能
	private void calculate(){
		double rt,op1,op2;
		String c = result.getText();
		int pos;
		char ops[] = new char[]{'+','-','*','/'};
		
		// 查找运算符位置
		pos = c.indexOf(ops[calculate_type - 1]);
		
		// 以运算符位置为分界点，分离出两个待计算的数
		op1 = Double.parseDouble(c.substring(0, pos));		
		op2 = Double.parseDouble(c.substring(pos + 1));		
		
		switch(calculate_type){
		case 1:
			rt = op1 + op2;
			break;
		case 2:
			rt = op1 - op2;
			break;
		case 3:
			rt = op1 * op2;
			break;
		case 4:
			rt = op1 / op2;
			break;
		default:
			rt = 0;
		}
		
		result.setText("" + rt); // 显示计算结果		
		calculate_type = 0;	// 准备记录下次计算的类型
	}
	
	public static void main(String[] args){		
		new Exer02_FrameCaculator();
	}
}
```

### Exer03_FontConfig

```java
package Figure;

import javax.swing.*;
import java.awt.event.*;
import java.awt.*;

public class Exer03_FontConfig  extends JFrame implements ItemListener, ActionListener{
	
	JRadioButton jrbRed = new JRadioButton("红色",true);
	JRadioButton jrbGreen = new JRadioButton("绿色");
	JRadioButton jrbBlue = new JRadioButton("蓝色");		
	private ButtonGroup bg = new ButtonGroup();
	
	JCheckBox jcb1 = new JCheckBox("加粗");
	JCheckBox jcb2 = new JCheckBox("倾斜");	
	
	JComboBox listFont;
	JList listSize;
	JTextArea taDemo;
	JButton btnExit,btnEdit;
	
	public Exer03_FontConfig(){
		
		GraphicsEnvironment g = GraphicsEnvironment.getLocalGraphicsEnvironment();
		String fontName[] = g.getAvailableFontFamilyNames();
		
		Box boxV1 = Box.createVerticalBox();
		boxV1.add(new JLabel("请选择字体"));
		listFont = new JComboBox(fontName);
		boxV1.add(new JScrollPane(listFont));
		boxV1.add(Box.createVerticalStrut(155));
				
		Box boxV2 = Box.createVerticalBox();
		boxV2.add(new JLabel("请选择字号"));
		String strSize[] = new String[30];
		for(int i=0;i<30;i++){
			strSize[i] = ""+(i+16);
		}
		listSize = new JList(strSize);
		boxV2.add(new JScrollPane(listSize));
		
		Box boxV3 = Box.createVerticalBox();
		boxV3.add(new JLabel("请选择字形"));		
		boxV3.add(jcb1);
		boxV3.add(jcb2);
		boxV3.add(Box.createVerticalGlue());
		
		Box boxV4 = Box.createVerticalBox();		
		boxV4.add(new JLabel("请选择字色"));
		boxV4.add(jrbRed);
		boxV4.add(jrbGreen);
		boxV4.add(jrbBlue);
		boxV4.add(Box.createVerticalGlue());
		
		bg.add(jrbRed);
		bg.add(jrbGreen);
		bg.add(jrbBlue);
		
		Box boxH1 = Box.createHorizontalBox();
	
		boxH1.add(boxV1);
		boxH1.add(Box.createHorizontalStrut(15));
		boxH1.add(boxV2);
		boxH1.add(Box.createHorizontalStrut(15));
		boxH1.add(boxV3);
		boxH1.add(Box.createHorizontalStrut(15));
		boxH1.add(boxV4);
		
		Box boxH2 = Box.createHorizontalBox();
		taDemo = new JTextArea("这是字体设置的测试文字",5,20);
		boxH2.add(taDemo);
		
		Box boxV5 = Box.createVerticalBox();
		
		btnExit = new JButton("退出");
		btnEdit = new JButton("编辑");
		boxV5.add(btnExit);
		boxV5.add(btnEdit);	
		boxH2.add(boxV5);
		
		btnExit.addActionListener(this);
		btnEdit.addActionListener(this);
		
		Box baseBox = Box.createVerticalBox();
		baseBox.add(boxH1);
		baseBox.add(boxH2);
	
        this.setContentPane(baseBox);
		
		setTitle("字体设置器");
		setBounds(150,150,550,380);
		setVisible(true);
		
		setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);		
	}
	
	public void itemStateChanged(ItemEvent e){		
	}
	
	public void actionPerformed(ActionEvent e){
		if (e.getSource() == btnExit) {
			dispose();
		}
		else if (e.getSource() == btnEdit){
			int style = Font.PLAIN;
			if(jcb1.isSelected()) 
				style |= Font.BOLD;
			if(jcb2.isSelected()) 
				style |= Font.ITALIC;
			
			//根据单选按钮的选择，直接设置文本输入区的字体颜色
			if(jrbRed.isSelected())
				taDemo.setForeground(Color.RED);
			if(jrbGreen.isSelected())
				taDemo.setForeground(Color.GREEN);
			if(jrbBlue.isSelected())
				taDemo.setForeground(Color.BLUE);
	
			String strFont = (String)listFont.getSelectedItem();
			//根据组件的选择，得到构造字体的多个参数，然后构造字体
			Font ft = new Font(strFont,style,listSize.getSelectedIndex()+16);
			//对文本输入区设置字体
			taDemo.setFont(ft);
		}
		//构造其他组件的事件处理过程，比如复选框，直接根据仔细显示。
	}
	
	public static void main(String[] args){
		Exer03_FontConfig vt = new Exer03_FontConfig();
	}
}
```
### Ext01_JTableSimpleDemo

```java
package Figure;

import javax.swing.*;
import java.awt.*;

public class Ext01_JTableSimpleDemo {

    public static void main(String[] args) {
        JFrame jf = new JFrame("测试窗口");
        jf.setDefaultCloseOperation(WindowConstants.EXIT_ON_CLOSE);

        // 创建内容面板，使用边界布局
        JPanel panel = new JPanel(new BorderLayout());

        // 表头（列名）
        Object[] columnNames = {"姓名", "语文", "数学", "英语", "总分"};

        // 表格所有行数据
        Object[][] rowData = {
                {"张三", 80, 80, 80, 240},
                {"John", 70, 80, 90, 240},
                {"Sue", 70, 70, 70, 210},
                {"Jane", 80, 70, 60, 210},
                {"Joe", 80, 70, 60, 210}
        };

        // 创建一个表格，指定 所有行数据 和 表头
        JTable table = new JTable(rowData, columnNames);

        // 把 表头 添加到容器顶部（使用普通的中间容器添加表格时，表头 和 内容 需要分开添加）
        panel.add(table.getTableHeader(), BorderLayout.NORTH);
        // 把 表格内容 添加到容器中心
        panel.add(table, BorderLayout.CENTER);

        jf.setContentPane(panel);
        jf.pack();
        jf.setLocationRelativeTo(null);
        jf.setVisible(true);
    }

}
```

### Ext02_JTableScrollPane

```java
package Figure;

	import javax.swing.*;
	import java.awt.*;

	public class Ext02_JTableScrollPane {

	    public static void main(String[] args) {
	        JFrame jf = new JFrame("测试窗口");
	        jf.setDefaultCloseOperation(WindowConstants.EXIT_ON_CLOSE);

	        // 创建内容面板
	        JPanel panel = new JPanel();

	        // 表头（列名）
	        String[] columnNames = {"序号", "姓名", "语文", "数学", "英语", "总分"};

	        // 表格所有行数据
	        Object[][] rowData = {
	                {1, "张三", 80, 80, 80, 240},
	                {2, "John", 70, 80, 90, 240},
	                {3, "Sue", 70, 70, 70, 210},
	                {4, "Jane", 80, 70, 60, 210},
	                {5, "Joe_05", 80, 70, 60, 210},
	                {6, "Joe_06", 80, 70, 60, 210},
	                {7, "Joe_07", 80, 70, 60, 210},
	                {8, "Joe_08", 80, 70, 60, 210},
	                {9, "Joe_09", 80, 70, 60, 210},
	                {10, "Joe_10", 80, 70, 60, 210},
	                {11, "Joe_11", 80, 70, 60, 210},
	                {12, "Joe_12", 80, 70, 60, 210},
	                {13, "Joe_13", 80, 70, 60, 210},
	                {14, "Joe_14", 80, 70, 60, 210},
	                {15, "Joe_15", 80, 70, 60, 210},
	                {16, "Joe_16", 80, 70, 60, 210},
	                {17, "Joe_17", 80, 70, 60, 210},
	                {18, "Joe_18", 80, 70, 60, 210},
	                {19, "Joe_19", 80, 70, 60, 210},
	                {20, "Joe_20", 80, 70, 60, 210}
	        };

	        // 创建一个表格，指定 表头 和 所有行数据
	        JTable table = new JTable(rowData, columnNames);

	        // 设置表格内容颜色
	        table.setForeground(Color.BLACK);                   // 字体颜色
	        table.setFont(new Font(null, Font.PLAIN, 14));      // 字体样式
	        table.setSelectionForeground(Color.DARK_GRAY);      // 选中后字体颜色
	        table.setSelectionBackground(Color.LIGHT_GRAY);     // 选中后字体背景
	        table.setGridColor(Color.GRAY);                     // 网格颜色

	        // 设置表头
	        table.getTableHeader().setFont(new Font(null, Font.BOLD, 14));  // 设置表头名称字体样式
	        table.getTableHeader().setForeground(Color.RED);                // 设置表头名称字体颜色
	        table.getTableHeader().setResizingAllowed(false);               // 设置不允许手动改变列宽
	        table.getTableHeader().setReorderingAllowed(false);             // 设置不允许拖动重新排序各列

	        // 设置行高
	        table.setRowHeight(30);

	        // 第一列列宽设置为40
	        table.getColumnModel().getColumn(0).setPreferredWidth(40);

	        // 设置滚动面板视口大小（超过该大小的行数据，需要拖动滚动条才能看到）
	        table.setPreferredScrollableViewportSize(new Dimension(400, 100));

	        // 把 表格 放到 滚动面板 中（表头将自动添加到滚动面板顶部）
	        JScrollPane scrollPane = new JScrollPane(table);

	        // 添加 滚动面板 到 内容面板
	        panel.add(scrollPane);

	        // 设置 内容面板 到 窗口
	        jf.setContentPane(panel);

	        jf.pack();
	        jf.setLocationRelativeTo(null);
	        jf.setVisible(true);
	    }
	}
```

### Ext03_JTableByTableModel

```java
package Figure;

import javax.swing.*;
import javax.swing.table.AbstractTableModel;
import java.awt.*;

public class Ext03_JTableByTableModel {

    public static void main(String[] args) {
        JFrame jf = new JFrame("测试窗口");
        jf.setDefaultCloseOperation(WindowConstants.EXIT_ON_CLOSE);

        // 创建内容面板，使用边界布局
        JPanel panel = new JPanel(new BorderLayout());

        // 使用表格模型创建一个表格
        JTable table = new JTable(new MyTableModel());

        // 把 表头 添加到容器顶部（使用普通的中间容器添加表格时，表头 和 内容 需要分开添加）
        panel.add(table.getTableHeader(), BorderLayout.NORTH);
        // 把 表格内容 添加到容器中心
        panel.add(table, BorderLayout.CENTER);

        jf.setContentPane(panel);
        jf.pack();
        jf.setLocationRelativeTo(null);
        jf.setVisible(true);
    }

    /**
     * 表格模型实现，表格显示数据时将调用模型中的相应方法获取数据进行表格内容的显示
     */
    public static class MyTableModel extends AbstractTableModel {
        /**
         * 表头（列名）
         */
        private Object[] columnNames = {"姓名", "语文", "数学", "英语", "总分"};

        /**
         * 表格所有行数据
         */
        private Object[][] rowData = {
                {"张三", 80, 80, 80, 240},
                {"John", 70, 80, 90, 240},
                {"Sue", 70, 70, 70, 210},
                {"Jane", 80, 70, 60, 210},
                {"Joe", 80, 70, 60, 210}
        };

        /**
         * 返回总行数
         */
        @Override
        public int getRowCount() {
            return rowData.length;
        }

        /**
         * 返回总列数
         */
        @Override
        public int getColumnCount() {
            return columnNames.length;
        }

        /**
         * 返回列名称（表头名称），AbstractTableModel 中对该方法的实现默认是以
         * 大写字母 A 开始作为列名显示，所以这里需要重写该方法返回我们需要的列名。
         */
        @Override
        public String getColumnName(int column) {
            return columnNames[column].toString();
        }

        /**
         * 返回指定单元格的显示的值
         */
        @Override
        public Object getValueAt(int rowIndex, int columnIndex) {
            return rowData[rowIndex][columnIndex];
        }
    }

}
```
### Ext04_JTableModelListener

```java
package Figure;

import javax.swing.*;
import javax.swing.event.TableModelEvent;
import javax.swing.event.TableModelListener;
import javax.swing.table.AbstractTableModel;
import javax.swing.table.TableModel;
import java.awt.*;

public class Ext04_JTableModelListener {

    public static void main(String[] args) {
        JFrame jf = new JFrame("测试窗口");
        jf.setDefaultCloseOperation(WindowConstants.EXIT_ON_CLOSE);

        // 创建内容面板，使用边界布局
        JPanel panel = new JPanel(new BorderLayout());

        // 表头（列名）
        final Object[] columnNames = {"姓名", "语文", "数学", "英语", "总分"};

        // 表格所有行数据
        final Object[][] rowData = {
                {"张三", 80, 80, 80, 240},
                {"John", 70, 80, 90, 240},
                {"Sue", 70, 70, 70, 210},
                {"Jane", 80, 70, 60, 210},
                {"Joe", 80, 70, 60, 210}
        };

        // 自定义表格模型，创建一个表格
        JTable table = new JTable(new AbstractTableModel() {
            @Override
            public int getRowCount() {
                return rowData.length;
            }

            @Override
            public int getColumnCount() {
                return rowData[0].length;
            }

            @Override
            public String getColumnName(int column) {
                return columnNames[column].toString();
            }

            @Override
            public boolean isCellEditable(int rowIndex, int columnIndex) {
                // 总分列的索引为 4，总分列不允许编辑，其他列允许编辑，
                // 总分列的数值由 语文、数学、英语 这三列的值相加得出，并同步更新
                return columnIndex != 4;
            }

            @Override
            public Object getValueAt(int rowIndex, int columnIndex) {
                return rowData[rowIndex][columnIndex];
            }

            @Override
            public void setValueAt(Object newValue, int rowIndex, int columnIndex) {
                // 设置新的单元格数据时，必须把新值设置到原数据数值中，
                // 待更新UI重新调用 getValueAt(...) 获取单元格值时才能获取到最新值
                rowData[rowIndex][columnIndex] = newValue;
                // 设置完数据后，必须通知表格去更新UI（重绘单元格），否则显示的数据不会改变
                fireTableCellUpdated(rowIndex, columnIndex);
            }
        });

        /*
         * 上面的继承 AbstractTableModel 实现自定义表格模型，功能并不完整，还有很多需要自己
         * 去实现（例如更新数据，通知UI更新，列名称获取等），建议使用 DefaultTableModel 类，
         * 该类对 TableModel 做了较为完善的实现，支持自动更新数据处理，支持UI自动更新，列名称
         * 处理，添加/移除行列等。无特殊要求不需要重写方法，直接使用即可，如下两行代码即可:
         */
        // DefaultTableModel tableModel = new DefaultTableModel(rowData, columnNames);
        // JTable table = new JTable(tableModel);

        // 获取 表格模型
        final TableModel tableModel = table.getModel();
        // 在 表格模型上 添加 数据改变监听器
        tableModel.addTableModelListener(new TableModelListener() {
            @Override
            public void tableChanged(TableModelEvent e) {
                // 获取 第一个 和 最后一个 被改变的行（只改变了一行，则两者相同）
                int firstRow = e.getFirstRow();
                int lastRow = e.getLastRow();

                // 获取被改变的列
                int column = e.getColumn();

                // 事件的类型，可能的值有:
                //     TableModelEvent.INSERT   新行或新列的添加
                //     TableModelEvent.UPDATE   现有数据的更改
                //     TableModelEvent.DELETE   有行或列被移除
                int type = e.getType();

                // 针对 现有数据的更改 更新其他单元格数据
                if (type == TableModelEvent.UPDATE) {
                    // 只处理 语文、数学、英语 这三列（索引分别为1、2、3）的分数的更改
                    if (column < 1 || column > 3) {
                        return;
                    }
                    // 遍历每一个修改的行，单个学科分数更改后同时更新总分数
                    for (int row = firstRow; row <= lastRow; row++) {
                        // 获取当前行的 语文、数学、英语 的值
                        Object chineseObj = tableModel.getValueAt(row, 1);
                        Object mathObj = tableModel.getValueAt(row, 2);
                        Object englishObj = tableModel.getValueAt(row, 3);

                        // 把对象值转换为数值
                        int chinese = 0;
                        try {
                            chinese = Integer.parseInt("" + chineseObj);
                        } catch (Exception ex) {
                            ex.printStackTrace();
                        }
                        int math = 0;
                        try {
                            math = Integer.parseInt("" + mathObj);
                        } catch (Exception ex) {
                            ex.printStackTrace();
                        }
                        int english = 0;
                        try {
                            english = Integer.parseInt("" + englishObj);
                        } catch (Exception ex) {
                            ex.printStackTrace();
                        }

                        // 重新计算新的总分数
                        int totalScore = chinese + math + english;
                        // 将新的分数值设置到总分单元格（总分数的列索引为4）
                        tableModel.setValueAt(totalScore, row, 4);
                    }
                }
            }
        });

        // 把 表头 添加到容器顶部（使用普通的中间容器添加表格时，表头 和 内容 需要分开添加）
        panel.add(table.getTableHeader(), BorderLayout.NORTH);
        // 把 表格内容 添加到容器中心
        panel.add(table, BorderLayout.CENTER);

        jf.setContentPane(panel);
        jf.pack();
        jf.setLocationRelativeTo(null);
        jf.setVisible(true);
    }

}
```

### Ext05_JTable

```java
package Figure;

import java.awt.BorderLayout;
import java.awt.Dimension;

import javax.swing.JFrame;
import javax.swing.JPanel;
import javax.swing.JScrollPane;
import javax.swing.JTable;
import javax.swing.WindowConstants;
import javax.swing.event.TableModelEvent;
import javax.swing.event.TableModelListener;
import javax.swing.table.DefaultTableModel;

public class Ext05_JTable {
     public static void main(String[] args) {
		JFrame jf=new JFrame("价格表");
		 jf.setDefaultCloseOperation(WindowConstants.EXIT_ON_CLOSE);
		
		// 表头（列名）
        final Object[] columnNames = {"名称", "价格", "数量",  "花费"};

        // 表格所有行数据
        final Object[][] rowData = {
                {"手机壳", 80, 2, 160},
                {"榴莲", 70, 3, 210},
                {"苹果", 7, 4, 28},
                {"黄桃", 4, 1, 4},
                 };
        
        DefaultTableModel tableModel = new DefaultTableModel(rowData, columnNames);
        JTable table=new JTable(tableModel);

        // 设置行高
        table.setRowHeight(30);

        // 第一列列宽设置为40
        table.getColumnModel().getColumn(0).setPreferredWidth(40);

        // 设置滚动面板视口大小（超过该大小的行数据，需要拖动滚动条才能看到）
        table.setPreferredScrollableViewportSize(new Dimension(400, 200));
		JScrollPane jscrollpane=new JScrollPane(table);
        //jscrollpane.setViewportView(table);
		JPanel panel = new JPanel();
		panel.add(jscrollpane);
        jf.setContentPane(panel);//(jscrollpane, BorderLayout.CENTER);
        
        tableModel.addTableModelListener(new TableModelListener() {
            @Override
            public void tableChanged(TableModelEvent e) {
                // 获取 第一个 和 最后一个 被改变的行（只改变了一行，则两者相同）
                int firstRow = e.getFirstRow();
                int lastRow = e.getLastRow();

                // 获取被改变的列
                int column = e.getColumn();

                // 事件的类型，可能的值有:
                //     TableModelEvent.INSERT   新行或新列的添加
                //     TableModelEvent.UPDATE   现有数据的更改
                //     TableModelEvent.DELETE   有行或列被移除
                int type = e.getType();

                // 针对 现有数据的更改 更新其他单元格数据
                if (type == TableModelEvent.UPDATE) {
                    // 只处理价格和数量 这三列（索引分别为1、2）的更改
                    if (column < 1 || column > 2) {
                        return;
                    }
                    // 遍历每一个修改的行，更新总价
                    for (int row = firstRow; row <= lastRow; row++) {
                        // 获取当前行的 价格、数量、英语 的值
                        Object chineseObj = tableModel.getValueAt(row, 1);
                        Object mathObj = tableModel.getValueAt(row, 2);

                        // 把对象值转换为数值
                        int price = 0;
                        try {
                            price = Integer.parseInt("" + chineseObj);
                        } catch (Exception ex) {
                            ex.printStackTrace();
                        }
                        int count = 0;
                        try {
                        	count = Integer.parseInt("" + mathObj);
                        } catch (Exception ex) {
                            ex.printStackTrace();
                        }
                      
                        // 重新计算新的总分数
                        int total = price*count;
                        // 将新的总价值设置到总价
                        tableModel.setValueAt(total, row, 3);
                    }
                   //Object[] obj= {"123",1,2,34};
                   // tableModel.addRow(obj);
               // tableModel.insertRow(1,obj);
                }
            }
        });
        
	    jf.pack();
	    jf.setLocationRelativeTo(null);;
		jf.setVisible(true);
	}
}
```

### Graph

```java
package Figure;

import java.awt.HeadlessException;
import java.awt.event.ActionEvent;
import java.awt.event.ActionListener;
import java.awt.event.ItemEvent;
import java.awt.event.ItemListener;
import java.util.List;

import javax.swing.BorderFactory;
import javax.swing.Box;
import javax.swing.ButtonGroup;
import javax.swing.JComboBox;
import javax.swing.JFrame;
import javax.swing.JLabel;
import javax.swing.JList;
import javax.swing.JRadioButton;
import javax.swing.JScrollPane;
import javax.swing.JTextField;
import javax.swing.ListSelectionModel;
import javax.swing.event.ListSelectionEvent;
import javax.swing.event.ListSelectionListener;

public class Graph extends JFrame {

	JComboBox<Phone> phones = null;
	JTextField jtf = null;

	public Graph() throws HeadlessException {

	}

	public Graph(String title) throws HeadlessException {

		Box boxv1 = Box.createVerticalBox();

		boxv1.add(new JLabel("请选择籍贯:"));
		JRadioButton jrb1 = new JRadioButton("江苏省 连云港市");
		jrb1.setActionCommand("江苏省 连云港市");
		JRadioButton jrb2 = new JRadioButton("江苏省 南京市");
		jrb2.setActionCommand("江苏省 南京市");

		boxv1.add(jrb1);
		boxv1.add(jrb2);
		boxv1.add(Box.createVerticalStrut(200));

		ButtonGroup bg = new ButtonGroup();
		bg.add(jrb1);
		bg.add(jrb2);
		jrb1.addItemListener(new ItemListener() {
			public void itemStateChanged(ItemEvent e) {
				jtf.setText(jtf.getText() + "\n您选择的籍贯为：" + bg.getSelection().getActionCommand());
			}
		});

		Box boxv2 = Box.createVerticalBox();

		String[] strs = new String[] { "Java       ", "数据库          ", "英语          ", "高数          ", "思修          " };

		JList<String> jl1 = new JList<>(strs);
		List<String> list = jl1.getSelectedValuesList();
		boxv2.add(new JScrollPane(jl1));
		jl1.setBorder(BorderFactory.createTitledBorder("请选择你选修的课程:"));
		jl1.addListSelectionListener(new ListSelectionListener() {
			public void valueChanged(ListSelectionEvent e) {
				int[] indices = jl1.getSelectedIndices();
				List<String> list = jl1.getSelectedValuesList();
				for (int i = 0; i < list.size(); i++) {
					jtf.setText(jtf.getText() + "\n你选择的课程为：" + list.get(i));
				}
			}
		});
		boxv2.add(Box.createVerticalStrut(100));

		Box boxv3 = Box.createVerticalBox();
		Phone[] ph = new Phone[] { new Phone("华为", 2399), new Phone("三星", 3999), new Phone("苹果", 6699) };
		phones = new JComboBox<Phone>(ph);
		phones.addItemListener(new ItemListener() {

			public void itemStateChanged(ItemEvent e) {
				jtf.setText(jtf.getText() + "\n您选择的手机品牌为：" + phones.getSelectedItem());
			}
		});
		boxv3.add(phones);
		phones.setBorder(BorderFactory.createTitledBorder("请选择手机品牌"));
		boxv3.add(Box.createVerticalStrut(100));

		Box boxh1 = Box.createHorizontalBox();
		boxh1.add(boxv1);
		boxh1.add(boxv2);
		boxh1.add(boxv3);

		Box boxh2 = Box.createHorizontalBox();
		jtf = new JTextField("请选择", 100);
		boxh2.add(jtf);

		Box boxh3 = Box.createHorizontalBox();
		boxh3.add(boxv1);
		boxh3.add(boxv2);
		this.setContentPane(boxh3);
		setBounds(50, 100, 300, 300);
		setVisible(true);

	}

	public static void main(String[] args) {
		new Graph("图形界面程序");

	}

	public void ActionPerformed(ActionEvent e) {

	}

}
```
### Phone

```java
package Figure;

public class Phone {
	private String brand;
	private int price;

	public Phone() {
	}

	public Phone(String brand) {
		super();
		this.brand = brand;
		this.price = 1000;
	}

	public Phone(String brand, int price) {
		super();
		this.brand = brand;
		this.price = price;
	}

	public String getBrand() {
		return brand;
	}

	public void setBrand(String brand) {
		this.brand = brand;
	}

	public int getPrice() {
		return price;
	}

	public void setPrice(int price) {
		this.price = price;
	}

	@Override
	public String toString() {
		// TODO Auto-generated method stub
		return this.brand + "牌手机，价格" + this.price;
	}

}
```
