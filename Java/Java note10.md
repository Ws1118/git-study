## jdbcdemo

### DBUtils

```java
package jdbcdemo;

import java.sql.Connection;
import java.sql.DriverManager;
import java.sql.PreparedStatement;
import java.sql.ResultSet;
import java.sql.SQLException;
import java.sql.Statement;

public class DBUtils {
	
	public static Connection getConnection() throws ClassNotFoundException, SQLException{
		
		Class.forName("com.mysql.jdbc.Driver");
		
		String url="jdbc:mysql://localhost:3306/myjavadb";
		
		Connection connection=null;
		PreparedStatement statement=null;
		connection=DriverManager.getConnection(url, "root", "root");
		/*System.out.println(connection);*/
		
		return connection;
	}
	
	public static void closeResource(Connection connection,Statement statement){
		if (statement != null) {
			try {
				statement.close();
			} catch (SQLException e) {
				// TODO Auto-generated catch block
				e.printStackTrace();
			}
		}

		if (connection != null) {
			try {
				connection.close();
			} catch (SQLException e) {
				// TODO Auto-generated catch block
				e.printStackTrace();
			}
		}
		
	}
	
	public static void closeResource(Connection connection,Statement statement,ResultSet rs){
		if (rs != null) {
			try {
				rs.close();
			} catch (SQLException e) {
				// TODO Auto-generated catch block
				e.printStackTrace();
			}
		}
		
		if (statement != null) {
			try {
				statement.close();
			} catch (SQLException e) {
				// TODO Auto-generated catch block
				e.printStackTrace();
			}
		}

		if (connection != null) {
			try {
				connection.close();
			} catch (SQLException e) {
				// TODO Auto-generated catch block
				e.printStackTrace();
			}
		}
		
	}
	public static int update(Connection connection,String sql,Object...objs){
		
		PreparedStatement statement = null;
		int code=0;
		try {
			statement = connection
					.prepareStatement(sql);
			for(int i=0;i<objs.length;i++){
			    statement.setObject(i+1, objs[i]);
			}
			code=statement.executeUpdate();

		} catch (SQLException e) {
			// TODO Auto-generated catch block
			e.printStackTrace();
		}
		
		closeResource(null, statement);
		
		return code;
		
	}
	
	public static int update(String sql,Object...objs){
        try {
			Class.forName("com.mysql.jdbc.Driver");
		} catch (ClassNotFoundException e2) {
			// TODO Auto-generated catch block
			e2.printStackTrace();
		}
		
		String url="jdbc:mysql://localhost:3306/myjavadb";
		
		Connection connection=null;

		try {
			connection=DriverManager.getConnection(url, "root", "root");
		} catch (SQLException e1) {
			// TODO Auto-generated catch block
			e1.printStackTrace();
		}

		int code=0;
		PreparedStatement statement=null;
		try {
			statement = connection.prepareStatement(sql);
			for(int i=0;i<objs.length;i++){
			    statement.setObject(i+1, objs[i]);
			}
			code=statement.executeUpdate();

		} catch (SQLException e) {
			// TODO Auto-generated catch block
			e.printStackTrace();
		}
		
		closeResource(connection, statement);
		
		return code;	
	}
}
```

### Demo01_TestDriver

```java
package jdbcdemo;

import java.sql.Connection;
import java.sql.Driver;
import java.sql.DriverManager;
import java.sql.SQLException;
import java.util.Properties;

import org.junit.Test;

public class Demo01_TestDriver {

	/*
	 * 最常见的一种数据库链接获取方式 1. 将数据库驱动程序加入项目 2. 调用Class.forName(驱动程序类名称)来加载对应数据库的驱动程序 3.
	 * 调用DriverManager.getConnection(url,username,password)来得到数据库链接 4.
	 * 关闭第三步获得的数据库链接。
	 */
	@Test
	public void testDriverManager() {
		try {
			Class.forName("com.mysql.jdbc.Driver");
		} catch (ClassNotFoundException e) {
			// TODO Auto-generated catch block
			e.printStackTrace();
		}
		String url = "jdbc:mysql://localhost:3306/myjavadb";

		Connection connection = null;
		try {
			connection = DriverManager.getConnection(url, "root", "root123");
			System.out.println(connection);

		} catch (SQLException e) {
			// TODO Auto-generated catch block
			e.printStackTrace();
		}

		if (connection != null) {
			try {
				connection.close();
			} catch (SQLException e) {
				// TODO Auto-generated catch block
				e.printStackTrace();
			}
		}
	}

	/*
	 * 直接使用数据库驱动程序的类实例来得到数据库链接，代码复用性不好，不建议使用 1. 直接通过数据库驱动中的实现类来得到Driver接口实例； 2.
	 * 通过Driver的connect方法得到数据库链接， 参数为url和标识用户信息的Properties实例(至少要包括user和password两个属性)
	 * 3. 关闭第2步得到的数据库链接。
	 */
	@Test
	public void testDriver() {
		Driver driver = null;
		Connection connection = null;

		driver = new com.mysql.jdbc.Driver();

		String url = "jdbc:mysql://localhost:3306/myjavadb";
		Properties prop = new Properties();
		prop.setProperty("user", "root");
		prop.setProperty("password", "root123");

		try {
			connection = driver.connect(url, prop);
			System.out.println(connection);
		} catch (SQLException e) {
			// TODO Auto-generated catch block
			e.printStackTrace();
		}

		if (connection != null) {
			try {
				connection.close();
			} catch (SQLException e) {
				// TODO Auto-generated catch block
				e.printStackTrace();
			}
		}
	}
}
```

### Demo02_TestStatement

```java
package jdbcdemo;

import java.sql.Connection;
import java.sql.DriverManager;
import java.sql.SQLException;

import org.junit.Test;

import java.sql.PreparedStatement;
import java.sql.Statement;

public class Demo02_TestStatement {

	/*
	 * 1. 先使用connection.createStatement获得一个statement； 2.
	 * 调用statement.execute(sql)直接执行； 3. 关闭statement
	 */

	@Test
	public void TestStatement() {
		Connection connection=null;
		try {
			connection=DBUtils.getConnection();
			System.out.println(connection);
		} catch (ClassNotFoundException | SQLException e1) {
			// TODO Auto-generated catch block
			e1.printStackTrace();
		}
		Statement statement=null;
		// String
		// sql="insert into customers (id,name,birthday) values('3','wanger','1999-1-8')";
		String sql = "delete from customers where id='2'";
		if (connection != null) {
			try {
				statement = connection.createStatement();
				System.out.println(statement.execute(sql));

			} catch (SQLException e) {
				// TODO Auto-generated catch block
				e.printStackTrace();
			}

		}

		DBUtils.closeResource(connection, statement);
	}

	/*
	 * 1.
	 * 先使用connection.prepareStatement(一个带占位符？的sql语句)获得一个PreparedStatement实例statement
	 * ； 2. 使用statement.setXXX(index,具体的值)设置占位符的值。 3.
	 * 调用statement.executeUpdate()直接执行； 4. 关闭statement
	 */
	@Test
	public void TestPreparedStatement() {
		try {
			Class.forName("com.mysql.jdbc.Driver");
		} catch (ClassNotFoundException e) {
			// TODO Auto-generated catch block
			e.printStackTrace();
		}
		String url = "jdbc:mysql://localhost:3306/myjavadb";

		Connection connection = null;
		PreparedStatement statement = null;
		try {
			connection = DriverManager.getConnection(url, "root", "root");
			System.out.println(connection);

		} catch (SQLException e) {
			// TODO Auto-generated catch block
			e.printStackTrace();
		}
		// String
		// sql="insert into customers (id,name,birthday) values('3','wanger','1999-1-8')";
		// String sql="delete from customers where id='2'";

		try {
			/*
			 * statement=connection.prepareStatement(
			 * "insert into customers (id,name,birthday) values(?,?,?)");
			 * statement.setInt(1, 2); statement.setString(2, "lisi");
			 * statement.setString(3, "1990-11-12");
			 */

			statement = connection
					.prepareStatement("delete from customers where id=?");
			statement.setInt(1, 2);
			statement.executeUpdate();

		} catch (SQLException e) {
			// TODO Auto-generated catch block
			e.printStackTrace();
		}

		if (statement != null) {
			try {
				statement.close();
			} catch (SQLException e) {
				// TODO Auto-generated catch block
				e.printStackTrace();
			}
		}

		if (connection != null) {
			try {
				connection.close();
			} catch (SQLException e) {
				// TODO Auto-generated catch block
				e.printStackTrace();
			}
		}
	}
	
	@Test
	public void TestUpdateOperation() {
		
		//String sql="delete from customers where id=?";		
		//DBUtils.update( sql, new Integer(3));
		String sql="insert into customers (id,name,birthday) values('3','wanger','1999-1-8')";
		DBUtils.update(sql);
		
	}	
}
```

### Demo03_TestResultSet

```java
package jdbcdemo;

import java.sql.Connection;
import java.sql.DriverManager;
import java.sql.PreparedStatement;
import java.sql.ResultSet;
import java.sql.ResultSetMetaData;
import java.sql.SQLException;

import org.junit.Test;

public class Demo03_TestResultSet {
	/*
	 * ResultSet的使用：
	 * 1. 调用Statement.executeQuery()得到ResultSet实例
	 * 2. 遍历ResultSet实例，通过next方法及getXXX(index)
	 * 3. 关闭ResultSet实例*/
	@Test
	public void TestResultSet() {

        Connection connection=null;
        PreparedStatement statement=null;
		ResultSet rs=null;
		
        try {
			connection=DBUtils.getConnection();

			statement = connection.prepareStatement("select id,name,birthday from customers where id=?");
			statement.setInt(1, 3);
			rs=statement.executeQuery();
				
			while(rs.next()){
					System.out.println("-------------------------------------");
					int id=rs.getInt(1);
					System.out.println(id);
					System.out.println(rs.getString(2));
					System.out.println(rs.getDate(3));
			}
		}catch (ClassNotFoundException | SQLException e1) {
			// TODO Auto-generated catch block
			e1.printStackTrace();
		}finally{
			DBUtils.closeResource(connection, statement, rs);
		}
	}
	
	/*
	 * ResultSetMetaData是关于ResultSet的元数据，也就是读出来的字段信息：
	 * 比如读出几个字段，字段的名字是什么，该字段可不可以为null。
	 * 直接可以通过rs.getMetaData()得到。可以后面用于DAO的内容
	 */
	
	@Test
	public void TestResultSetMetaData() {

        Connection connection=null;
        PreparedStatement statement=null;
		ResultSet rs=null;
		
        try {
			connection=DBUtils.getConnection();

			statement = connection.prepareStatement("select id ID,name,birthday Birth from customers where id=?");
			statement.setInt(1, 3);
			rs=statement.executeQuery();
			
			ResultSetMetaData rsmd=rs.getMetaData();
			
			for(int i=0;i<rsmd.getColumnCount();i++){
				System.out.println(rsmd.getColumnLabel(i+1));
			}
					
	/*		while(rs.next()){
					System.out.println("-------------------------------------");
					int id=rs.getInt(1);
					System.out.println(id);
					System.out.println(rs.getString(2));
					System.out.println(rs.getDate(3));
			}*/
		}catch (ClassNotFoundException | SQLException e1) {
			// TODO Auto-generated catch block
			e1.printStackTrace();
		}finally{
			DBUtils.closeResource(connection, statement, rs);
		}
	}
}
```

### Demo04_CustomerManagment

```java
package jdbcdemo;

import java.awt.Container;
import java.awt.event.ActionEvent;
import java.awt.event.ActionListener;
import java.sql.Connection;
import java.sql.PreparedStatement;
import java.sql.ResultSet;
import java.sql.SQLException;

import javax.swing.JButton;
import javax.swing.JFrame;
import javax.swing.JLabel;
import javax.swing.JMenuBar;
import javax.swing.JTextField;

class CustomerFrame extends JFrame implements ActionListener{
	JLabel jId=new JLabel("标识：");
	JLabel jName=new JLabel("名字：");
	JLabel jBirthday=new JLabel("生日：");
	
	JTextField jtfId=new JTextField("2",20);
	JTextField jtfName=new JTextField("lisi",20);
	JTextField jtfBirthday=new JTextField("1956-7-8",20);
	
	JButton jButtonInsert=new JButton("Insert");
	JButton jButtonDelete=new JButton("Update");
	JButton jButtonSearch=new JButton("Search");
	
	public CustomerFrame(String title){
		super(title);
		Container container=this.getContentPane();
		
		container.setLayout(null);
		jId.setBounds(10, 20, 40, 30);
		jtfId.setBounds(60, 20, 100, 30);
		
		jName.setBounds(10, 60, 40, 30);
		jtfName.setBounds(60, 60, 100, 30);
		
		jBirthday.setBounds(10, 100, 40, 30);
		jtfBirthday.setBounds(60, 100, 100, 30);
		
		jButtonInsert.setBounds(10, 160, 80, 30);
		jButtonDelete.setBounds(100, 160, 80, 30);
		jButtonSearch.setBounds(190, 160, 80, 30);
		
		container.add(jId);
		container.add(jtfId);
		
		container.add(jName);
		container.add(jtfName);
		
		container.add(jBirthday);
		container.add(jtfBirthday);
		
		container.add(jButtonInsert);
		container.add(jButtonDelete);
		container.add(jButtonSearch);
		jButtonInsert.addActionListener(this);
		jButtonDelete.addActionListener(this);
		jButtonSearch.addActionListener(this);
		
		this.setSize(300, 300);
		this.setVisible(true);
		this.setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
		
	}
	
	@Override
	public void actionPerformed(ActionEvent e) {
		// TODO Auto-generated method stub
		System.out.println(e.getActionCommand());
		if("Insert".equals(e.getActionCommand())){
			
			String sql="insert into customers (id,name,birthday) values(?,?,?)";
			Integer id=Integer.parseInt(jtfId.getText());
			String name=jtfName.getText();
			String date=jtfBirthday.getText();
			
			
			int code=DBUtils.update(sql, id,name,date);
			System.out.println(code);
			
			
		}else if("Search".equals(e.getActionCommand())){
	        Connection connection=null;
	        PreparedStatement statement=null;
			ResultSet rs=null;
			
	        try {
				connection=DBUtils.getConnection();

				statement = connection.prepareStatement("select id,name,birthday from customers where id=?");
				System.out.println(Integer.parseInt(jtfId.getText()));
				statement.setInt(1, Integer.parseInt(jtfId.getText()));
				rs=statement.executeQuery();
				while(rs.next()){
						System.out.println("-------------------------------------");
						int id=rs.getInt(1);
						System.out.println(id);
                        jtfName.setText(rs.getString(2));
                        jtfBirthday.setText(rs.getDate(3).toString());
				}
			}catch (ClassNotFoundException | SQLException e1) {
				// TODO Auto-generated catch block
				e1.printStackTrace();
			}finally{
				DBUtils.closeResource(connection, statement, rs);
			}
		}else if("Update".equals(e.getActionCommand())){
			
			String sql="update customers set name='zhao' where id=4";
			Integer id=Integer.parseInt(jtfId.getText());

			int code=DBUtils.update(sql);
			System.out.println(code);	
		}
	}	
}


public class Demo04_CustomerManagment {

	public static void main(String[] args) {
		// TODO Auto-generated method stub
		new CustomerFrame("客户管理");
	}

}
```

### Test1

```java
package jdbcdemo;

import java.sql.Connection;
import java.sql.Driver;
import java.sql.DriverManager;
import java.sql.SQLException;
import java.util.Properties;

import javax.swing.Spring;

import org.junit.Test;

public class Test1 {
	@Test
	public void testDrive() {
		try {
			Class.forName("com.mysql.jdbc.Driver");
		} catch (ClassNotFoundException e) {
			// TODO Auto-generated catch block
			e.printStackTrace();
		}
		String url = "jdbc:mysql://localhost:3306/myjavadb";

		Connection connection = null;
		try {
			connection = DriverManager.getConnection(url, "root", "root123");
			System.out.println(connection);

		} catch (SQLException e) {
			// TODO Auto-generated catch block
			e.printStackTrace();
		}

		if (connection != null) {
			try {
				connection.close();
			} catch (SQLException e) {
				// TODO Auto-generated catch block
				e.printStackTrace();
			}
		}
	}

	@Test
	public void DriverManager() {
		Driver driver = null;
		Connection connection = null;

		driver = new com.mysql.jdbc.Driver();

		String url = "jdbc:mysql://localhost:3306/myjavadb";
		Properties prop = new Properties();
		prop.setProperty("user", "root");
		prop.setProperty("password", "root123");

		try {
			connection = driver.connect(url, prop);
			System.out.println(connection);
		} catch (SQLException e) {
			// TODO Auto-generated catch block
			e.printStackTrace();
		}

		if (connection != null) {
			try {
				connection.close();
			} catch (SQLException e) {
				// TODO Auto-generated catch block
				e.printStackTrace();
			}
		}
	}
}
```

### Test2

```java
package jdbcdemo;

import java.sql.Connection;
import java.sql.DriverManager;
import java.sql.SQLException;
import java.sql.Statement;
import java.util.Properties;

import org.junit.Test;

public class Test2 {
	@Test
	public void testDriverManager() {
		try {
			Class.forName("com.mysql.jdbc.Driver");
		} catch (ClassNotFoundException e) {
			// TODO Auto-generated catch block
			e.printStackTrace();
		}
		String url = "jdbc:mysql://localhost:3306/myjavadb";
		Statement statement = null;
		Connection connection = null;
		try {
			connection = DriverManager.getConnection(url, "root", "root123");
			//System.out.println(connection);

		} catch (SQLException e) {
			// TODO Auto-generated catch block
			e.printStackTrace();
		}
		String sql1 = "insert into student (学号,姓名,出生年月,学期平均成绩) values('2','ws','2001-11-18','01')";
		String sql2 = "delete from student where 学号='2'";
		if (connection != null) {
			try {
				statement = connection.createStatement();
				System.out.println(statement.execute(sql1));
				System.out.println(statement.execute(sql2));
			} catch (SQLException e) {
				// TODO Auto-generated catch block
				e.printStackTrace();
			}
		}
		if (statement != null) {
			try {
				statement.close();
			} catch (SQLException e) {
				// TODO Auto-generated catch block
				e.printStackTrace();
			}
		}

		if (connection != null) {
			try {
				connection.close();
			} catch (SQLException e) {
				// TODO Auto-generated catch block
				e.printStackTrace();
			}
		}
	}
}
```

### Test3

```java
package jdbcdemo;

	import org.junit.Test;

	import java.sql.Connection;
	import java.sql.PreparedStatement;
	import java.sql.ResultSet;
	import java.sql.SQLException;
	
	public class Test3 {
		
	    @Test
	    public void TestChenck(){
	        Connection connection=null;
	        PreparedStatement statement=null;
	        ResultSet rs=null;
	        try {
	            connection=DBUtils.getConnection();
	            statement=connection.prepareStatement("select 序号,标题名称,作者,创建时间 from music");
	            rs=statement.executeQuery();

	            while (rs.next()){
	                System.out.println("---------------------");
	                int 序号=rs.getInt(1);
	                System.out.println(序号);
	                System.out.println(rs.getString(2));
	                System.out.println(rs.getString(3));
	                System.out.println(rs.getDate(4));
	            }
	        }catch (ClassNotFoundException| SQLException e){
	            e.printStackTrace();
	        }finally {
	            DBUtils.closeResource(connection, statement, rs);
			}
		}
	}
```

### Test4

```java
package jdbcdemo;

import java.sql.Connection;
import java.sql.DriverManager;
import java.sql.PreparedStatement;
import java.sql.ResultSet;
import java.sql.SQLException;
import java.sql.Statement;

public class Test4 {

	public static Connection getConnection() throws ClassNotFoundException, SQLException {

		Class.forName("com.mysql.cj.jdbc.Driver");

		String url = "jdbc:mysql://127.0.0.1:3306/myjavadb?useUnicode=true&characterEncoding=utf8&serverTimezone=GMT";

		Connection connection = null;
		PreparedStatement statement = null;
		connection = DriverManager.getConnection(url, "root", "ldd123789dd.0");
		/* System.out.println(connection); */

		return connection;
	}

	public static void closeResource(Connection connection,Statement statement){
	        if (statement != null) {
	            try {
	                statement.close();
	            } catch (SQLException e) {
	                // TODO Auto-generated catch block
	                e.printStackTrace();
	            }finally {
		            DBUtils.closeResource(connection, statement);
				}
			}
	   } 
}
```

### Test5

```java
package jdbcdemo;

import javax.swing.*;
import java.awt.*;
import java.awt.event.ActionEvent;
import java.awt.event.ActionListener;

class Frame extends JFrame implements ActionListener {
	JLabel jID = new JLabel(" I  D：");
	JLabel jName = new JLabel("姓名:");
	JLabel jAge = new JLabel("年龄:");
	JLabel jMoney = new JLabel("工资:");
	JTextField jtfID = new JTextField("", 20);
	JTextField jtfName = new JTextField("", 20);
	JTextField jtfAge = new JTextField("", 20);
	JTextField jtfMoney = new JTextField("", 20);

	JButton jButtonInsert = new JButton("Insert");
	JButton jButtonUpdate = new JButton("Update");
	JButton jButtonDelete = new JButton("Delete");

	public Frame(String title) {
		super(title);
		Container container = this.getContentPane();

		container.setLayout(null);
		jID.setBounds(10, 20, 40, 30);
		jtfID.setBounds(60, 20, 100, 30);

		jName.setBounds(10, 60, 40, 30);
		jtfName.setBounds(60, 60, 100, 30);

		jAge.setBounds(10, 100, 40, 30);
		jtfAge.setBounds(60, 100, 100, 30);

		jMoney.setBounds(10, 140, 40, 30);
		jtfMoney.setBounds(60, 140, 100, 30);

		jButtonInsert.setBounds(10, 200, 80, 30);
		jButtonUpdate.setBounds(100, 200, 80, 30);
		jButtonDelete.setBounds(190, 200, 80, 30);

		container.add(jID);
		container.add(jtfID);

		container.add(jName);
		container.add(jtfName);

		container.add(jAge);
		container.add(jtfAge);

		container.add(jMoney);
		container.add(jtfMoney);

		container.add(jButtonInsert);
		container.add(jButtonUpdate);
		container.add(jButtonDelete);
		jButtonInsert.addActionListener(this);
		jButtonUpdate.addActionListener(this);
		jButtonDelete.addActionListener(this);

		this.setSize(300, 300);
		this.setVisible(true);
		this.setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
	}

	@Override
	public void actionPerformed(ActionEvent e) {
		System.out.println(e.getActionCommand());
		if ("Insert".equals(e.getActionCommand())) {
			String sql = "insert into company (ID,姓名,年龄,工资) values(?,?,?,?)";
			Integer id = Integer.parseInt(jtfID.getText());
			String 姓名 = jtfName.getText();
			Integer 年龄 = Integer.parseInt(jtfAge.getText());
			Integer 工资 = Integer.parseInt(jtfMoney.getText());

			int code = DBUtils.update(sql, id, 姓名, 年龄, 工资);
			System.out.println(code + "\n已加入" + 姓名 + "的基本资料");

		} else if ("Delete".equals(e.getActionCommand())) {
			String sql = "delete from company where id=?";

			int code = DBUtils.update(sql, new Integer(4));
			System.out.println(code + "\n已删除4号职员基本资料");

		} else if ("Update".equals(e.getActionCommand())) {
			String sql = "Update company set 工资=工资*1.1 where ID=2";
			Integer id = Integer.parseInt(jtfID.getText());

			int code = DBUtils.update(sql);
			System.out.println(code + "\n已将2号职员工资增加10%");

		}
	}
}

public class Test5 {
	public static void main(String[] args) {
		new Frame("企业管理");

	}
}
```

### Driver

```java
package com.mysql.jdbc;

import java.sql.Connection;
import java.sql.DriverPropertyInfo;
import java.sql.SQLException;
import java.sql.SQLFeatureNotSupportedException;
import java.util.Properties;
import java.util.logging.Logger;

public class Driver implements java.sql.Driver {

	@Override
	public boolean acceptsURL(String url) throws SQLException {
		// TODO Auto-generated method stub
		return false;
	}

	@Override
	public Connection connect(String url, Properties info) throws SQLException {
		// TODO Auto-generated method stub
		return null;
	}

	@Override
	public int getMajorVersion() {
		// TODO Auto-generated method stub
		return 0;
	}

	@Override
	public int getMinorVersion() {
		// TODO Auto-generated method stub
		return 0;
	}

	@Override
	public Logger getParentLogger() throws SQLFeatureNotSupportedException {
		// TODO Auto-generated method stub
		return null;
	}

	@Override
	public DriverPropertyInfo[] getPropertyInfo(String url, Properties info) throws SQLException {
		// TODO Auto-generated method stub
		return null;
	}

	@Override
	public boolean jdbcCompliant() {
		// TODO Auto-generated method stub
		return false;
	}
 }
```
