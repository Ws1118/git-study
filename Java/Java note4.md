## DAO

### DBUtils

```java
package DAO;

import java.sql.Connection;
import java.sql.DriverManager;
import java.sql.PreparedStatement;
import java.sql.ResultSet;
import java.sql.SQLException;
import java.sql.Statement;
import java.util.ArrayList;
import java.util.HashMap;
import java.util.List;
import java.util.Map;
import java.sql.ResultSetMetaData;

public class DBUtils {

	public static Connection getConnection() throws ClassNotFoundException, SQLException {

		Class.forName("com.mysql.jdbc.Driver");
//可以通过url中增加“？useUnicode=true&characterEncoding=utf-8”来指定编码问题
		String url = "jdbc:mysql://localhost:3306/myjavadb";

		Connection connection = null;
		PreparedStatement statement = null;
		connection = DriverManager.getConnection(url, "root", "root123");
		/* System.out.println(connection); */

		return connection;
	}

	public static void closeResource(Connection connection, Statement statement) {
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

	public static void closeResource(Connection connection, Statement statement, ResultSet rs) {
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
//	public static int update(Connection connection,String sql,Object...objs){
//		
//		PreparedStatement statement = null;
//		int code=0;
//		try {
//			statement = connection
//					.prepareStatement(sql);
//			for(int i=0;i<objs.length;i++){
//			    statement.setObject(i+1, objs[i]);
//			}
//			code=statement.executeUpdate();
//
//		} catch (SQLException e) {
//			// TODO Auto-generated catch block
//			e.printStackTrace();
//		}
//		
//		closeResource(null, statement);
//		
//		return code;
//		
//	}

	public static int update(String sql, Object... objs) {
		Connection connection = null;

		int code = 0;
		PreparedStatement statement = null;
		try {
			connection = DBUtils.getConnection();
			statement = connection.prepareStatement(sql);
			for (int i = 0; i < objs.length; i++) {
				statement.setObject(i + 1, objs[i]);
			}
			code = statement.executeUpdate();

		} catch (ClassNotFoundException e) {
			// TODO Auto-generated catch block
			e.printStackTrace();
		} catch (SQLException e) {
			// TODO Auto-generated catch block
			e.printStackTrace();
		}

		finally {
			closeResource(connection, statement);
		}

		return code;
	}

	public static List<Map<String, Object>> query(String sql, Object... objs) {
		Connection connection = null;
		PreparedStatement statement = null;
		ResultSet rs = null;
		List<Map<String, Object>> list = new ArrayList<Map<String, Object>>();
		try {
			connection = DBUtils.getConnection();
			statement = connection.prepareStatement(sql);
			for (int i = 0; i < objs.length; i++) {
				statement.setObject(i + 1, objs[i]);
			}
			rs = statement.executeQuery();

			ResultSetMetaData rsmd = rs.getMetaData();

//			for(int i=0;i<rsmd.getColumnCount();i++){
//				System.out.println(rsmd.getColumnLabel(i+1));
//			}

			while (rs.next()) {
				HashMap<String, Object> entry = new HashMap<>();
				for (int i = 0; i < rsmd.getColumnCount(); i++) {
					entry.put(rsmd.getColumnLabel(i + 1), rs.getObject(i + 1));
				}
				list.add(entry);
			}

		} catch (ClassNotFoundException e) {
			// TODO Auto-generated catch block
			e.printStackTrace();
		} catch (SQLException e) {
			// TODO Auto-generated catch block
			e.printStackTrace();
		}

		finally {
			closeResource(connection, statement, rs);
		}

		return list;
	}

}
```

### LoginFrame2

```java
package DAO;

import java.awt.Container;
import java.awt.event.ActionEvent;
import java.awt.event.ActionListener;
import java.util.List;

import javax.swing.JButton;
import javax.swing.JFrame;
import javax.swing.JLabel;

import javax.swing.JPasswordField;
import javax.swing.JTextField;
import javax.swing.WindowConstants;

import DAO.UserDao;
import DAO.UserDaoImpl;
import DAO.User;

public class LoginFrame2 extends JFrame implements ActionListener {

	JLabel jName = new JLabel("名字：");
	JLabel jPassword = new JLabel("密码：");

	JTextField jtfName = new JTextField("", 40);
	JTextField jtfPassword = new JPasswordField("", 40);

	JButton jButtonInsert = new JButton("注册");
	JButton jButtonDelete = new JButton("注销");
	JButton jButtonSearch = new JButton("登录");

	public LoginFrame2(String title) {
		super(title);
		Container container = this.getContentPane();

		container.setLayout(null);
		;

		jName.setBounds(10, 20, 40, 30);
		jtfName.setBounds(60, 20, 100, 30);

		jPassword.setBounds(10, 60, 40, 30);
		jtfPassword.setBounds(60, 60, 100, 30);

		jButtonInsert.setBounds(10, 150, 80, 40);
		jButtonDelete.setBounds(100, 150, 80, 40);
		jButtonSearch.setBounds(190, 150, 80, 40);

		container.add(jName);
		container.add(jtfName);

		container.add(jPassword);
		container.add(jtfPassword);

		container.add(jButtonInsert);
		container.add(jButtonDelete);
		container.add(jButtonSearch);
		jButtonInsert.addActionListener(this);
		jButtonDelete.addActionListener(this);
		jButtonSearch.addActionListener(this);

		this.setSize(300, 300);
		this.setVisible(true);
		this.setDefaultCloseOperation(WindowConstants.EXIT_ON_CLOSE);

	}

	@Override
	public void actionPerformed(ActionEvent e) {
		UserDao dao = new UserDaoImpl();
		// TODO Auto-generated method stub
		System.out.println(e.getActionCommand());
		if ("注册".equals(e.getActionCommand())) {

			User user = new User();
			user.setName(jtfName.getText());

			user.setPassword(jtfPassword.getText());

			int code = dao.add(user);

			System.out.println(code);
		} else if ("删除信息".equals(e.getActionCommand())) {

		} else if ("登录".equals(e.getActionCommand())) {

			List<User> userlist = null;
			User user = new User();
			user.setName(jtfName.getText());
			user.setPassword(jtfPassword.getText());
			userlist = dao.getUser(user);
			if (userlist.size() != 0) {
				new StudentFrame2("信息维护");
				this.setVisible(false);
			}

		}
	}

	public static void main(String[] args) {
		// TODO Auto-generated method stub
		new LoginFrame2("学生管理");

	}
}
```

### Student

```java
package DAO;

public class Student {
	private String name;
	private int id;
	private int class1;
	private int studynum;

	public Student() {
	}

	public String getName() {
		return name;
	}

	public void setName(String name) {
		this.name = name;
	}

	public int getId() {
		return id;
	}

	public void setId(int id) {
		this.id = id;
	}

	public int getClass1() {
		return class1;
	}

	public void setClass1(int class1) {
		this.class1 = class1;
	}

	public int getStudynum() {
		return studynum;
	}

	public void setstudynum(int studynum) {
		this.studynum = studynum;
	}

	public String toString() {
		return "[ " + this.name + ", " + this.id + ", " + this.class1 + ", " + this.studynum + "]";
	}
}
```

### StudentDAO

```java
package DAO;

import java.util.List;

import DAO.Student;

public interface StudentDAO {
	int add(Student Student);

	int delete(Student Student);

	int delete(int Student);

	List<Student> getById(int num);

	List<Student> getAll();

}
```

### studentDaolmp1

```java
package DAO;

import java.sql.Connection;
import java.sql.PreparedStatement;
import java.sql.ResultSet;
import java.sql.SQLException;
import java.util.ArrayList;
import java.util.List;

import DAO.Student;
import DAO.StudentDAO;
import jdbcdemo.DBUtils;;

public class studentDaolmp1 implements StudentDAO {
	@Override
	public int add(Student student) {
		int code = 0;
		String sq1 = "insert into Tstudent(name,id, class, studynum) values(?,?,?,?)";
		code = DBUtils.update(sq1, student.getName(),student.getId(), student.getClass1(), student.getStudynum());
		return code;
	}

	@Override
	public int delete(Student student) {
		// TODO Auto- generated method stub
		int code = 0;
		String sq1 = "delete from Tstudent where id=? ";
		code = DBUtils.update(sq1, student.getId());
		return code;
	}

	@Override
	public int delete(int student) {
		// TODO Auto- generated method stub
		return 0;
	}

	@Override
	public List<Student> getById(int num) {
		// TODO Auto-generated method stub
		return null;
	}

	@Override
	public List<Student> getAll() {
		// TODO Auto-generated method stub
		Connection connection = null;
		PreparedStatement statement = null;
		ResultSet rs = null;
		Student student = null;
		List<Student> students = new ArrayList<Student>();
		try {
			try {
				connection = DBUtils.getConnection();
			} catch (ClassNotFoundException e) {
				// TODO Auto-generated catch block
				e.printStackTrace();
			}
			statement = (PreparedStatement) connection
					.prepareStatement("select name, id,class, studynum from Tstudent");
			rs = statement.executeQuery();
			while (rs.next()) {
				student = new Student();				
				student.setName(rs.getString(2));
				student.setId(rs.getInt(1));
				student.setClass1(rs.getInt(3));
				student.setstudynum(rs.getInt(4));
				students.add(student);
			}
		} catch (SQLException e) {
			// TODO: handle exception
			e.printStackTrace();
		} finally {
			DBUtils.closeResource(connection, statement, rs);
		}
		return students;
	}

}
```

### StudentDaolmpl2

```java
package DAO;

import java.util.ArrayList;
import java.util.List;
import java.util.Map;

import DAO.DBUtils;
import DAO.StudentDAO;

import DAO.Student;;

public class StudentDaolmpl2 implements StudentDAO {

	@Override
	public int add(Student student) {
		int code = 0;
		String sql = "insert into Tstudent(id,name,class,studynum) values(?,?,?,?)";
		code = DBUtils.update(sql, student.getId(), student.getName(), student.getClass1(), student.getStudynum());

		return code;
	}

	@Override
	public int delete(Student student) {
		// TODO Auto-generated method stub
		int code = 0;
		String sql = "delete from Tstudent where id=? ";
		code = DBUtils.update(sql, student.getId());

		return code;
	}

	@Override
	public int delete(int student) {
		// TODO Auto-generated method stub

		return 0;
	}

	@Override
	public List<Student> getById(int class0) {
		// TODO Auto-generated method stub
		String aql = "select * from tstudent where class=?";
		List<Student> studentlist = new ArrayList<Student>();
		List<Map<String, Object>> maplist = DBUtils.query(aql, new Integer(class0));
		for (Map<String, Object> map : maplist) {
			Student student = new Student();
			student.setId((Integer) (map.get("id")));
			student.setName((String) (map.get("name")));
			student.setClass1((Integer) (map.get("class")));
			student.setstudynum((Integer) (map.get("studynum")));

			studentlist.add(student);
		}
		return studentlist;
	}

	@Override
	public List<Student> getAll() {
		return null;
	}

}
```

### StudentFrame

```java
package DAO;

import java.awt.Container;
import java.awt.event.ActionEvent;
import java.awt.event.ActionListener;
import java.util.List;
import javax.swing.JButton;
import javax.swing.JFrame;
import javax.swing.JLabel;
import javax.swing.JTextField;

import DAO.Student;
import DAO.StudentDAO;
import DAO.studentDaolmp1;

public class StudentFrame extends JFrame implements ActionListener {

	JLabel jName = new JLabel("名字: ");
	JLabel jId = new JLabel("ID: ");
	JLabel jClass = new JLabel("班级: ");
	JLabel jNum = new JLabel("学号: ");

	JTextField jtfName = new JTextField("", 40);
	JTextField jtfId = new JTextField("", 40);	
	JTextField jtfClass = new JTextField("", 40);
	JTextField jtfNum = new JTextField("", 40);

	JButton jButtonInsert = new JButton("增加学生信息");
	JButton jButtonDelete = new JButton("删除学生信息");
	JButton jButtonModify = new JButton("修改学生信息");
	JButton jButtonSearch = new JButton("查询学生信息");

	public StudentFrame(String title) {
		super(title);
		Container container = this.getContentPane();
		container.setLayout(null);

		jName.setBounds(10, 60, 40, 30);
		jtfName.setBounds(60, 60, 100, 30);
		jId.setBounds(10, 20, 40, 30);
		jtfId.setBounds(60, 20, 100, 30);
		jClass.setBounds(10, 100, 40, 30);
		jtfClass.setBounds(60, 100, 100, 30);
		jNum.setBounds(10, 140, 40, 30);
		jtfNum.setBounds(60, 140, 100, 30);
		jButtonInsert.setBounds(10, 230, 100, 30);
		jButtonDelete.setBounds(120, 230, 100, 30);
		jButtonModify.setBounds(130, 230, 100, 30);
		jButtonSearch.setBounds(230, 230, 100, 30);
				
		container.add(jName);	
		container.add(jtfName);
		container.add(jId);
		container.add(jtfId);
		container.add(jClass);
		container.add(jtfClass);
		container.add(jNum);
		container.add(jtfNum);
		container.add(jButtonInsert);
		container.add(jButtonDelete);
		container.add(jButtonModify);
		container.add(jButtonSearch);
		jButtonInsert.addActionListener(this);
		jButtonDelete.addActionListener(this);
		jButtonModify.addActionListener(this);
		jButtonSearch.addActionListener(this);
		this.setSize(400, 360);
		this.setVisible(true);
		this.setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
	}

	@Override
	public void actionPerformed(ActionEvent e) {
		StudentDAO dao = new studentDaolmp1();
		// TODO Auto-generated method stub
		System.out.println(e.getActionCommand());
		if ("增加学生信息".equals(e.getActionCommand())) {
			Student student = new Student();
			student.setId(Integer.parseInt(jtfId.getText()));
			student.setName(jtfName.getText());
			student.setClass1(Integer.parseInt(jtfClass.getText()));
			student.setstudynum(Integer.parseInt(jtfNum.getText()));
			int code = dao.add(student);
			System.out.println(code);
		} else if ("删除学生信息".equals(e.getActionCommand())) {
			Student student = new Student();
			student.setId(Integer.parseInt(jtfId.getText()));
			int code = dao.delete(student);
			System.out.println(code);
		} else if ("查询学生信息".equals(e.getActionCommand())) {
			Student student = new Student();
			List<Student> code = dao.getAll();
			System.out.println(code);
		}
	}

	public static void main(String[] args) {
		// TODO Auto-generated method stub
		new StudentFrame("学生信息管理");
	}

}
```

### StudentFrame2

```java
package DAO;

import java.awt.Container;
import java.awt.event.ActionEvent;
import java.awt.event.ActionListener;
import java.util.List;
import javax.swing.JButton;
import javax.swing.JFrame;
import javax.swing.JLabel;
import javax.swing.JTextField;
import DAO.StudentDAO;
import DAO.StudentDaolmpl2;
import DAO.Student;

public class StudentFrame2 extends JFrame implements ActionListener {
	JLabel jName = new JLabel("名字：");
	JLabel jId = new JLabel("id：");
	JLabel jClass = new JLabel("班级：");
	JLabel jNum = new JLabel("学号：");

	JTextField jtfName = new JTextField("", 40);
	JTextField jtfId = new JTextField("", 40);
	JTextField jtfClass = new JTextField("", 40);
	JTextField jtfNum = new JTextField("", 40);

	JButton jButtonInsert = new JButton("添加学生信息");
	JButton jButtonDelete = new JButton("删除学生信息");
	JButton jButtonSearch = new JButton("查询学生信息");

	public StudentFrame2(String title) {
		super(title);
		Container container = this.getContentPane();

		container.setLayout(null);
		jId.setBounds(10, 20, 40, 30);
		jtfId.setBounds(60, 20, 100, 30);

		jName.setBounds(10, 60, 40, 30);
		jtfName.setBounds(60, 60, 100, 30);

		jClass.setBounds(10, 100, 40, 30);
		jtfClass.setBounds(60, 100, 100, 30);

		jNum.setBounds(10, 140, 40, 30);
		jtfNum.setBounds(60, 140, 100, 30);

		jButtonInsert.setBounds(10, 230, 100, 30);
		jButtonDelete.setBounds(120, 230, 100, 30);
		jButtonSearch.setBounds(230, 230, 100, 30);

		container.add(jId);
		container.add(jtfId);

		container.add(jName);
		container.add(jtfName);

		container.add(jClass);
		container.add(jtfClass);

		container.add(jNum);
		container.add(jtfNum);

		container.add(jButtonInsert);
		container.add(jButtonDelete);
		container.add(jButtonSearch);
		jButtonInsert.addActionListener(this);
		jButtonDelete.addActionListener(this);
		jButtonSearch.addActionListener(this);

		this.setSize(400, 360);
		this.setVisible(true);
		this.setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);

	}

	@Override
	public void actionPerformed(ActionEvent e) {
		StudentDAO dao = new StudentDaolmpl2();
		// TODO Auto-generated method stub
		System.out.println(e.getActionCommand());
		if ("添加学生信息".equals(e.getActionCommand())) {

			Student student = new Student();
			student.setId(Integer.parseInt(jtfId.getText()));
			student.setName(jtfName.getText());
			student.setClass1(Integer.parseInt(jtfClass.getText()));
			student.setstudynum(Integer.parseInt(jtfNum.getText()));

			int code = dao.add(student);

			System.out.println(code);
		} else if ("删除学生信息".equals(e.getActionCommand())) {

			Student student = new Student();
			student.setId(Integer.parseInt(jtfId.getText()));
			int code = dao.delete(student);
			System.out.println(code);

		} else if ("查询班级".equals(e.getActionCommand())) {
			List<Student> studentlist = null;

			studentlist = dao.getById(Integer.parseInt(jtfClass.getText()));

			new StudentTableFrame(studentlist);
		}
	}

	public static void main(String[] args) {
		// TODO Auto-generated method stub
		new StudentFrame2("学生信息管理");

	}
}
```

### StudentTableFrame

```java
package DAO;

import java.util.List;
import java.util.Vector;

import javax.swing.JFrame;
import javax.swing.JPanel;
import javax.swing.JScrollPane;
import javax.swing.JTable;
import javax.swing.WindowConstants;
import javax.swing.border.TitledBorder;

import DAO.Student;

public class StudentTableFrame extends JFrame {
	public StudentTableFrame(List<Student> list) {
		Vector<Vector<Object>> vectordate = new Vector<>();
		for (Student student : list) {
			Vector<Object> objs = new Vector<>();
			objs.add(new Integer(student.getId()));
			objs.add(student.getName());
			objs.add(new Integer(student.getClass1()));
			objs.add(new Integer(student.getStudynum()));
			vectordate.add(objs);
		}
		String[] labels = { "序号", "姓名", "班级", "学号" };
		Vector<String> columNames = new Vector<>();
		for (String label : labels) {
			columNames.add(label);
		}

		JTable table = new JTable(vectordate, columNames);

		JScrollPane scrollPane = new JScrollPane(table);
		this.setDefaultCloseOperation(WindowConstants.DISPOSE_ON_CLOSE);

		JPanel panel = new JPanel();

		panel.setLayout(null);
		panel.setBorder(new TitledBorder(null, "总面板", TitledBorder.LEADING,
				TitledBorder.TOP, null, null));
		this.getContentPane().add(panel);
		panel.add(scrollPane);
		scrollPane.setBounds(15, 15, 300, 200);
		scrollPane.setBorder(new TitledBorder(null, "分数面板", TitledBorder.LEADING, 
				TitledBorder.TOP, null, null));
		this.setSize(420, 300);
		this.setLocationRelativeTo(null);
		this.setVisible(true);
	}
}
```

### User

```java
package DAO;

public class User {

	private int id;
	private String name;
	private String password;

	public User() {
	}

	public int getId() {
		return id;
	}

	public void setId(int id) {
		this.id = id;
	}

	public String getName() {
		return name;
	}

	public void setName(String name) {
		this.name = name;
	}

	public String getPassword() {
		return password;
	}

	public void setPassword(String password) {
		this.password = password;
	}
}
```

### UserDao

```java
package DAO;

import java.util.List;
import DAO.User;

public interface UserDao {
	int add(User user);

	List<User> getUser(User user);

}
```

### UserDaoImpl

```java
package DAO;

import java.util.ArrayList;
import java.util.List;
import java.util.Map;

import DAO.DBUtils;
import DAO.UserDao;

import DAO.User;

public class UserDaoImpl implements UserDao {

	@Override
	public int add(User user) {
		// TODO Auto-generated method stub
		int code = 0;
		String sql = "insert into users (name,password) values(?,?)";

		code = DBUtils.update(sql, user.getName(), user.getPassword());

		return code;
	}

	@Override
	public List<User> getUser(User user) {
		// TODO Auto-generated method stub
		String sql = "select * from users where name=? and password=?";
		List<User> userlist = new ArrayList<User>();
		List<Map<String, Object>> maplist = DBUtils.query(sql, user.getName(), user.getPassword());
		for (Map<String, Object> map : maplist) {
			User us = new User();
			us.setId((Integer) (map.get("id")));
			us.setName((String) (map.get("name")));
			us.setPassword((String) (map.get("password")));

			userlist.add(us);
		}

		return userlist;
	}
}
```

