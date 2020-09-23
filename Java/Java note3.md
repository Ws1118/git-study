## Commonclass

### Box

```java
package Commonclass;

class ToyCat {
	private String name;

	public String getName() {
		return name;
	}

	public void setName(String name) {
		this.name = name;
	}

	public ToyCat(String name) {
		super();
		this.name = name;
	}

	public String toString() {
		return "玩具" + this.name;
	}
}

class Cloth {
	public String toString() {
		return "布";
	}
}

public class Box<T, M> {
	private T thing;
	private M madeof;

	public T getThing() {
		return thing;
	}

	public void setThing(T thing) {
		this.thing = thing;
	}

	public M getMadeof() {
		return madeof;
	}

	public void setMadeof(M madeof) {
		this.madeof = madeof;
	}

	public Box(T thing, M madeof) {
		super();
		this.thing = thing;
		this.madeof = madeof;
	}

	public Box() {

	}

	public String toString() {
		return "装的是" + this.thing + "，是由" + this.madeof + "制成的";
	}
}
```

### BoxTest

```java
package Commonclass;

public class BoxTest {

	public static void main(String[] args) {
		/*
		 * Box<String, Integer> box = new Box<String, Integer>("数字", 2);
		 * System.out.println(box);
		 */

		Box<ToyCat, Cloth> box1 = new Box<ToyCat, Cloth>(new ToyCat("猫咪"), new Cloth());
		System.out.println(box1);
	}

}
```

### Date

```java
package Commonclass;

import java.text.DateFormat;
import java.text.ParseException;
import java.text.SimpleDateFormat;
import java.util.Locale;

public class Date {
	public static void main(String[] args) {

		DateFormat df1 = new SimpleDateFormat(" dd/mm/yyyy,a, HH:mm:ss ", Locale.US);
		String str1 = "13/03/2019 ,PM, 20:52:44";
		System.out.println(str1);

		System.out.println("----------------------");

		DateFormat df2 = new SimpleDateFormat("E,dd M月 yyyy HH:mm:ss", Locale.CHINA);
		String str2 = "星期三, 13 3月 2019 20:48:31";
		java.util.Date date2 = null;
		try {
			date2 = df2.parse(str2);
		} catch (ParseException e) {
			e.printStackTrace();
		}
		System.out.println(date2);
	}
}
```

### Gendor

```java
package Commonclass;

public enum Gendor {
	WOMEN,
    MEN
}
```

### GenericsMethod

```java
package Commonclass;

public class GenericsMethod {

	public <E> E getTheSecondLastElement(E[] arr) {
		return arr[arr.length - 2];
	}

	public static void main(String[] args) {

		GenericsMethod gmc = new GenericsMethod();
		Integer[] arr = new Integer[] { 12, 23, 34, 45 };
		int temp = gmc.getTheSecondLastElement(arr);
		System.out.println(temp);

	}
}
```

### GenericsMethodClass

```java
package Commonclass;

import java.util.Date;

public class GenericsMethodClass {

	public <E> E getExactOne(E[] arr, int index) {
		return arr[index];
	}

	public static void main(String[] args) {
		Date[] datearr = new Date[5];
		datearr[0] = new Date(2007, 7, 7);
		datearr[1] = new Date(2008, 8, 8);
		datearr[2] = new java.util.Date();
		datearr[3] = new Date(89, 8, 9);
		datearr[4] = new Date(2001, 10, 10);

		GenericsMethodClass gmc = new GenericsMethodClass();

		Date datetemp = gmc.getExactOne(datearr, 2);
		System.out.println(datetemp);
		
		Integer[] intarr=new Integer[] {1,2,3,4,5};
		int inttemp=gmc.getExactOne(intarr,2);
		System.out.println(inttemp);
		
		Double[] douarr=new Double[] {1.23,2.34,4.56,10000.07};
		Double doutemp=gmc.getExactOne(douarr,2);
		System.out.println(doutemp);
	}
}
```

### GenericsMethodinGenerics< T >

```java
package Commonclass;

import java.util.Date;

public class GenericsMethodinGenerics<T> {

		public <E> E getExactOne(E[] arr, int index,T temp) {
			System.out.println(temp);
			return arr[index];
		}

		public static void main(String[] args) {
			Date[] datearr = new Date[5];
			datearr[0] = new Date(2007, 7, 7);
			datearr[1] = new Date(2008, 8, 8);
			datearr[2] = new java.util.Date();
			datearr[3] = new Date(89, 8, 9);
			datearr[4] = new Date(2001, 10, 10);

			GenericsMethodinGenerics<String> gmc = new GenericsMethodinGenerics<String>();

			Date datetemp = gmc.getExactOne(datearr, 2,"泛型类的泛型指定，String");
			System.out.println(datetemp);
			
			Integer[] intarr=new Integer[] {1,2,3,4,5};
			int inttemp=gmc.getExactOne(intarr,2,"第二次数字调用，仍然只能是String");
			System.out.println(inttemp);
			
			Double[] douarr=new Double[] {1.23,2.34,4.56,10000.07};
			Double doutemp=gmc.getExactOne(douarr,2,"第三次浮点型调用，仍然只能是String");
			System.out.println(doutemp);
		}
	}
```

### Information< I >

```java
package Commonclass;

public class Information<I> {
	private I info;

	public I getInfo() {
		return info;
	}

	public void setInfo(I info) {
		this.info = info;
	}

	public Information(I info) {
		super();
		this.info = info;
	}

	public String toString() {
		return "这只狗的品种是：" + this.info;
	}
}
```

### InformationTest

```java
package Commonclass;

public class InformationTest {

	public static void main(String[] args) {
		Information<String> info1 = new Information<String>("泰迪");
		System.out.println(info1);
	}
}
```

### Student

```java
package Commonclass;

class IDcard {
	private String num1;

	public String getNum1() {
		return num1;
	}

	public void setNum1(String num1) {
		this.num1 = num1;
	}

	public IDcard(String num1) {
		super();
		this.num1 = num1;
	}

	public String toString() {
		return "身份证号：" + this.num1;
	}
}

class StudentIDcard {
	private int num2;

	public int getNum1() {
		return num2;
	}

	public void setNum1(int num2) {
		this.num2 = num2;
	}

	public StudentIDcard(int num2) {
		super();
		this.num2 = num2;
	}

	public String toString() {
		return "学生证编号：" + this.num2;
	}
}

class SchoolMealcard {
	private int num3;

	public int getNum1() {
		return num3;
	}

	public void setNum1(int num3) {
		this.num3 = num3;
	}

	public SchoolMealcard(int num3) {
		super();
		this.num3 = num3;
	}

	public String toString() {
		return "学校饭卡编号：" + this.num3;
	}
}

public class Student<A> {
	private A num;

	public A getNum() {
		return num;
	}

	public void setNum(A num) {
		this.num = num;
	}

	public Student(A num) {
		super();
		this.num = num;
	}

	public Student() {

	}

	public String toString() {
		return "身份标识：" + this.num;
	}
}
```

### StudentTest

```java
package Commonclass;

public class StudentTest {

	public static void main(String[] args) {
		// TODO Auto-generated method stub
		Student<IDcard> student1 = new Student<IDcard>(new IDcard("320721202001011111"));
		System.out.println(student1);

		Student<StudentIDcard> student2 = new Student<StudentIDcard>(new StudentIDcard(20194321));
		System.out.println(student2);

		Student<SchoolMealcard> student3 = new Student<SchoolMealcard>(new SchoolMealcard(20191234));
		System.out.println(student3);
	}

}
```

### TestDate

```java
package Commonclass;

import java.text.DateFormat;
import java.text.ParseException;
import java.text.SimpleDateFormat;
import java.util.Date;
import java.util.Locale;

public class TestDate {
    public static void main(String[] args)  {
	    Date date1=new Date();
	    System.out.println(date1);
	   
	    Date date2=new Date(222222222222L);
	    System.out.println(date2);
	   
	    //从日期到字符串 Date=>String
	    DateFormat df1=new SimpleDateFormat("yyyy/MM/dd a,HH:mm:ss #E",Locale.US);//,Locale.CHINA);
	   
	    String str=df1.format(date2);
	   
	    System.out.println(str);
	    
	    //从字符串生成一个日期date:String=>Date
	    String str2="1990/01/16 AM,08:23:42 #Sun";
	    Date date3=null;
		try {
			date3 = df1.parse(str2);
		} catch (ParseException e) {
			// TODO Auto-generated catch block
			e.printStackTrace();
		}
	    
	    System.out.println(date3);
    }
}
```

### TestEnumGendor

```java
package Commonclass;

import java.util.Random;

public class TestEnumGendor {

	public static void main(String[] args) {
        Random rand=new Random();
        
        Gendor gd=null;
        
        for(int i=0;i<100;i++){
        	int temp=rand.nextInt(100);
        	if(temp%2==0){
        		gd=Gendor.WOMEN;
        	}else{
        		gd=Gendor.MEN;
        	}
        	switch(gd){
        	case WOMEN:
        		System.out.println("女士");
        	case MEN:
        		System.out.println("先生");
        	}
        }
	}
}
```

### TestMathandRandom

```java
package Commonclass;

import java.util.Random;

public class TestMathandRandom {

	public static void main(String[] args) {
		// TODO Auto-generated method stub
		/*
		 * System.out.println(Math.ceil(20.56)); System.out.println(Math.floor(20.56));
		 * 
		 * System.out.println(Math.sqrt(2)); System.out.println(Math.pow(2, 12));
		 */

		Random random = new Random(100);
		for (int i = 0; i < 100; i++) {
			// System.out.println(random.nextInt(1000));
			System.out.println(50 * random.nextDouble());
		}
	}
}
```

### TestNumber

```java
package Commonclass;

import java.text.DecimalFormat;

public class TestNumber {
	public static void main(String[] args) {
		// TODO Auto-generated method stub
		Integer in1 = new Integer(100);
		System.out.println(in1);
		System.out.println(in1.MAX_VALUE);
		System.out.println(in1.SIZE);
		Integer in2 = new Integer("123");
		System.out.println(in2);

		int i1 = in1;// 自动拆箱
		int i2 = new Integer(10000);
		System.out.println(i2);

		Integer in3 = 599;// 自动装箱
		System.out.println(in3);

		System.out.println(Integer.toHexString(in3));
		System.out.println(Integer.toBinaryString(in3));

		Double db1 = new Double(12.57900);
		System.out.println(db1);
		DecimalFormat df = new DecimalFormat("0.000000");
		System.out.println(df.format(db1));

		Number num1 = new Double(12.4444);
		Number num2 = new Byte((byte) 15);

		System.out.println(num1.intValue());

		System.out.println(Double.toHexString(db1));
		System.out.println(Double.toHexString(db1));

	}
}
```

### TestStrRegExp

```java
package Commonclass;

public class TestStrRegExp {
	public static void main(String[] args) {
		// 第1个字符必须是$、_、字母或汉字
		String regex = "[\\p{Alpha}$_\u4E00-\u9FFF]{1}";
		// 其后的若干字符可以是$、_、字母、数字或汉字
		regex += "[$_\\p{Alnum}\u4E00-\u9FFF]*";

		String id[] = { "$$ab", "姓名", "-x", "i+j", "a_12$3", "6class", "_123_", "$年龄", "25", "a123x", "i" };

		for (String str : id) {
			// matches方法可以判断str是否与regex匹配
			if (str.matches(regex))
				System.out.println(str + " 合法");
			else
				System.out.println(str + " 不合法");
		}
	}
}
```

### WeChatGetPrize

```java
package Commonclass;

import java.util.Random;

public class WeChatGetPrize {
	public static void main(String[] args) {
		int[] weights = new int[50];

		Random rd = new Random();
		int sum = 0;
		for (int i = 0; i < weights.length; i++) {
			weights[i] = rd.nextInt(100);
			sum += weights[i];
		}

		for (int i = 0; i < weights.length; i++) {
			double prize = Math.floor((double) weights[i] / (double) sum * 50.0 * 100) / 100;
			System.out.println(prize);
			/*
			 * 加一点最后一位同学的红包额度的处理
			 */
		}
	}
}
```

