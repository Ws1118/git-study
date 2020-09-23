## Exception

### Age

```java
package Exception;

public class Age {
	private int age;

	public int getAge() {
		return age;
	}

	public void setAge(int age) throws Exception {
		if (age < 1 || age > 100) {
			throw new AgelnputException("年龄不对");
		} else {
			this.age = age;
			System.out.println("年龄：" + this.age + "岁");
		}
	}
}
```

### AgelnputException

```java
package Exception;

public class AgelnputException extends Exception {
	public AgelnputException(String message) {
		super(message);
	}
}
```

### AgeTest

```java
package Exception;

public class AgeTest {

	public static void main(String[] args) {
		Age age = new Age();
		try {
			age.setAge(111);
		} catch (Exception e) {
			System.out.println("年龄不符");
			e.printStackTrace();
		}
	}
}
```

### ExceptionCharAt

```java
package Exception;

import java.util.Scanner;

public class ExceptionCharAt {

	public static void main(String[] args) {
		Scanner in = new Scanner(System.in);
		System.out.println("请输入字符串长度内的数字：");
		try {
			byte num = in.nextByte();
			if (-128 <= num && num <= 127) {
				System.out.println("输入正确。");
			} else {
				System.out.println("输入错误。");
			}
		} catch (Exception ex) {
			System.out.println("程序运行时发现异常，并成功捕获了！");
			ex.printStackTrace();
		} finally {
			System.out.println("输入结束。");
		}
		System.out.println("感谢使用本程序！");
	}

}
```

### Firework

```java
package Exception;

public abstract class Firework implements Setoff {
	private String type;

	public String getType() {
		return type;
	}

	public void setType(String type) {
		this.type = type;
	}

	public Firework(String type) {
		super();
		this.type = type;
	}

	public Firework() {

	}
 }
```

### FireworkTest

```java
package Exception;

public class FireworkTest {

	public static void main(String[] args) {
		new Firework() {
			public void boom() {
				this.setType("烟花品种一:");
				System.out.println(this.getType() + "正在燃放");
			}
		}.boom();
		new Setoff() {
			String type = "烟花品种二：";

			public void boom() {
				System.out.println(this.type + "正在发射并燃放");
			}
		}.boom();
	}
}
```

### NotZeroSelfException

```java
package Exception;

public class NotZeroSelfException extends Exception{
    private int devidedNum;
    
	public int getDevidedNum() {
		return devidedNum;
	}

	public void setDevidedNum(int devidedNum) {
		this.devidedNum = devidedNum;
	}

	public NotZeroSelfException() {
		super();
		// TODO Auto-generated constructor stub
	}

	public NotZeroSelfException(String message) {
		super(message);
		// TODO Auto-generated constructor stub
	}	

}
```

### Person

```java
package Exception;

public class Person {
	private int age;

	public int getAge() {
		return age;
	}

	public void setAge(int age) {
		try {
			if (age < 1 || age > 100) {
				throw new AgelnputException("年龄不对");
			} else {
				this.age = age;
				System.out.println("年龄：" + this.age + "岁");
			}

		} catch (AgelnputException e) {
			// TODO: handle exception
			System.out.println("年龄不符");
			e.printStackTrace();
		} finally {
			System.out.println("设置年龄过程结束");
		}
		System.out.println("感谢使用本程序！");
	}

	public class AgelnputException extends Exception {
		public AgelnputException(String message) {
			super(message);
		}
	}

	public Person() {
		super();
	}

	public static void main(String[] args) {
		Person per = new Person();
		per.setAge(111);
	}

}
```

### Setoff

```java
package Exception;

public interface Setoff {
	void boom();
}
```

### StockException

```java
package Exception;

public class StockException extends Exception {
	public StockException(String message) {
		super(message);
	}

}
```

### StockHolder

```java
package Exception;

public class StockHolder {
	private double Astock;
	private double sellstock;

	public double getAstock() {
		return Astock;
	}

	public void setAstock(double astock) {
		Astock = astock;
	}

	public double getSellstock() {
		return sellstock;
	}

	public void setSellstock(double sellstock) {
		this.sellstock = sellstock;
	}

	public StockHolder() {

	}

	public StockHolder(double Astock, double sellStock) {
		this.Astock = Astock;
		this.sellstock = sellStock;
	}

	public void soldway() throws StockException {
		if (sellstock > Astock + Astock * 0.1 || sellstock < Astock + Astock * 0.1) {
			StockException ste = new StockException("自定义异常，股票卖出不得超过涨停幅度(A股为10%)");
			throw ste;
		} else {
			this.sellstock = sellstock;
			System.out.println("今日股票收盘价为" + this.sellstock + "元");
		}

	}
}
```

### TestException

```java
package Exception;

import java.util.Scanner;

public class TestException {

	public static void main(String[] args) {
		Scanner in = new Scanner(System.in);
		System.out.print("请输入被除数:");

		try {
			int num1 = in.nextInt();

			System.out.print("请输入除数:");
			int num2 = in.nextInt();
			System.out.println(String.format("%d / %d = %d", num1, num2, num1 / num2));
		} catch (Exception ex) {
			System.out.println("程序运行时发现异常，并成功捕获了！");
			ex.printStackTrace();
			// return;//return之前会查看一下有无finally代码块，有的话，先运行该代码块，然后再return
			System.exit(1);
		} finally {
			System.out.println("计算商的过程到此完成");
		}

		System.out.println("感谢使用本程序！");
	}

}
```

### TestExceptionThrows

```java
package Exception;

import java.util.InputMismatchException;
import java.util.Scanner;

public class TestExceptionThrows {
	public static double divide() throws NotZeroSelfException,InputMismatchException{
		Scanner in = new Scanner(System.in);
		System.out.print("请输入被除数:");
		int num1 = in.nextInt();
	    System.out.print("请输入除数:");
	    int num2 = in.nextInt();
	    if(num2==0){
	    	NotZeroSelfException nzsx=new NotZeroSelfException("我们自己定义的有名异常");
	        nzsx.setDevidedNum(num1);
	        throw nzsx;
		}	
		return (double)num1/num2;
	}

	public static void main(String[] args) {
		// TODO Auto-generated method stub
	
		try{
			divide();				
		}catch(NotZeroSelfException ex){
			System.out.println("程序运行时发现异常，并成功捕获了！");
			System.out.println("被除数为："+ex.getDevidedNum());
			ex.printStackTrace();
		}catch(Exception ex){
			ex.printStackTrace();
		}
		finally{
			System.out.println("计算商的过程到此完成");		
		}
		
		System.out.println("感谢使用本程序！");
	}
}
```

### TestMultipleCatch

```java
package Exception;

import java.util.InputMismatchException;
import java.util.Scanner;

public class TestMultipleCatch {
    public static void main(String[] args) {
		Scanner in = new Scanner(System.in);
	
		try{
			System.out.print("请输入被除数:");
			int num1 = in.nextInt();
		    System.out.print("请输入除数:");
		    int num2 = in.nextInt();
		    System.out.println(String.format("%d / %d = %d", 
						num1, num2, num1/ num2));
		}catch(ArithmeticException ex){
			System.out.println("程序运行时发现算数异常，并成功捕获了！");
		}catch(InputMismatchException ex){
			System.out.println("程序运行时发现输入异常，并成功捕获了！");
			ex.printStackTrace();
		}catch(Exception ex){
			System.out.println("程序运行时发现其他异常，并成功捕获了！");
			ex.printStackTrace();
		}finally{
			System.out.println("计算商的过程到此完成");		
		}
		
		System.out.println("感谢使用本程序！");

    }
}
```

### TestNum

```java
package Exception;

import java.util.Scanner;

public class TestNum {

	public static void main(String[] args) {
		// TODO Auto-generated method stub
		Scanner scan = new Scanner(System.in);
		try {
			System.out.println("请输入1~3之间任意一数字");
			int num = scan.nextInt();
			switch (num) {
			case 1:
				System.out.println("Java");
				break;
			case 2:
				System.out.println("英语");
				break;
			case 3:
				System.out.println("高数");
				break;
			default:
				System.out.println("您输入错误");
			}
		} catch (Exception ex) {
			System.out.println("程序运行时发现异常，并成功捕获了！");
			ex.printStackTrace();
		} finally {
		}

		System.out.println("欢迎提出建议！");
	}

}
```

### TestRunTimeException

```java
package Exception;

import java.util.Scanner;

public class TestRunTimeException {

	public static void main(String[] args)  {
		// TODO Auto-generated method stub
		Scanner in = new Scanner(System.in);
			
			System.out.print("请输入被除数:");
			int num1 = in.nextInt();
		    System.out.print("请输入除数:");
		    int num2 = in.nextInt();
		    if(num2==0){
		    	
		        throw new RuntimeException("这个异常不处理，我看一下是否可以");
			}
		    System.out.println("商为："+num1/num2);
						
		System.out.println("感谢使用本程序！");
	} 

}
```

### TestStockException

```java
package Exception;

public class TestStockException {
	public static void main(String[] args) {
		StockHolder stock = new StockHolder();
		try {
			stock.setAstock(9);
			stock.setSellstock(3);
			stock.soldway();
		} catch (Exception ex) {
			System.out.println("股票卖出价格不符合要求");
			ex.printStackTrace();
		} finally {
			System.out.println("感谢购买本公司的股票！");
		}

	}
}
```

### TestThrow

```java
package Exception;

import java.util.Scanner;

public class TestThrow {
	public static void main(String[] args) {
		Scanner in = new Scanner(System.in);
		System.out.print("请输入被除数:");
	
		try{
			int num1 = in.nextInt();
		    System.out.print("请输入除数:");
		    int num2 = in.nextInt();
		    if(num2==0){
		    	throw new Exception("我们自定义异常：除数为0，不允许进行下面的运算");
		    }
		    System.out.println(String.format("%d / %d = %d", 
						num1, num2, num1/ num2));
		}catch(Exception ex){
			System.out.println("程序运行时发现异常，并成功捕获了！");
			ex.printStackTrace();
		}finally{
			System.out.println("计算商的过程到此完成");		
		}
		
		System.out.println("感谢使用本程序！");
	}
}
```

### TestThrowSelfException

```java
package Exception;

import java.util.Scanner;

public class TestThrowSelfException {
	public static void main(String[] args) {
		// TODO Auto-generated method stub
		Scanner in = new Scanner(System.in);
		try{		
			System.out.print("请输入被除数:");
			int num1 = in.nextInt();
		    System.out.print("请输入除数:");
		    int num2 = in.nextInt();
		    if(num2==0){
		    	NotZeroSelfException nzsx=new NotZeroSelfException("我们自己定义的有名异常");
		        nzsx.setDevidedNum(num1);
		        throw nzsx;
			}
		    System.out.println("商为："+num1/num2);
						
		}catch(NotZeroSelfException ex){
			System.out.println("程序运行时发现异常，并成功捕获了！");
			System.out.println("被除数为："+ex.getDevidedNum());
			ex.printStackTrace();
		}finally{
			System.out.println("计算商的过程到此完成");		
		}
		
		System.out.println("感谢使用本程序！");
	}

}
```

