## Inherit

### Animal

```java
package Inherit;

public abstract class Animal {

	private String name;

	public Animal() {

	}

	public String getName() {
		return name;
	}

	public void setName(String name) {
		this.name = name;
	}

	public Animal(String name) {
		super();
		this.name = name;
	}

	public abstract void run();

	public abstract void eatSomething(String food);
}
```

### AnimalTest

```java
package Inherit;

public class AnimalTest {

	public static void main(String[] args) {
		Goat goat = new Goat("山羊");
		Wolf wolf = new Wolf("狼");
		goat.run();
		goat.eating("草");
		wolf.run();
		wolf.eating("肉");
	}

}
```

### Bus

```java
package Inherit;

public class Bus extends Car {
	private String route;

	public String getRoute() {
		return route;
	}

	public void setRoute(String route) {
		this.route = route;
	}

	public Bus(String brand, int num, String energytype, String route) {
		super(brand, num, energytype);
		this.route = route;
	}

	public void print() {
		super.print();
		System.out.println(this.route);
	}

	public void run() {
		System.out.println(this.route + "公交车在城市道路上行驶");
	}

}
```

### Car

```java
package Inherit;

public class Car {

	private String brand;
	private int num;
	private String energytype;

	public String getBrand() {
		return brand;
	}

	public void setBrand(String brand) {
		this.brand = brand;
	}

	public int getNum() {
		return num;
	}

	public void setNum(int num) {
		this.num = num;
	}

	public String getEnergytype() {
		return energytype;
	}

	public void setEnergytype(String energytype) {
		this.energytype = energytype;
	}

	public Car(String brand) {
		this(brand, 0, "宝马");
	}

	public Car(String brand, int num, String energytype) {
		super();
		this.brand = brand;
		this.num = num;
	}

	public void print() {
		System.out.println("品牌:" + this.brand);
		System.out.println("乘坐人数:" + this.num);
		System.out.println("能源类型:" + this.energytype);
	}

	public void run() {
		System.out.println("车跑起来了");
	}
}
```

### CarTest

```java
package Inherit;

public class CarTest {

	public static void main(String[] args) {

		Bus bus1 = new Bus("比亚迪", 35, "新能源", "五");

		bus1.run();
		Truck truck1 = new Truck("东风", 2, "汽油", 1000);

		truck1.run();
	}
}
```

### Cat

```java
package Inherit;

public class Cat extends Pet {

	public Cat() {
	}

	public Cat(String Name, int Health, int Love,int intimacy) {
		super(Name, Health, Love,intimacy);
	}

	public void eatSomething(String food) {
		if (this.getHealth() != 100) {
			this.setHealth(this.getHealth() + 4 <= 100 ? this.getHealth() + 4 : 100);
			System.out.println(this.getName() + "吃了" + food);
		} else {
			System.out.println(this.getName() + "已经饱了，稍后再喂");
		}
	}
}
```

### CatTest

```java
package Inherit;

public class CatTest {

	public static void main(String[] args) {
		// TODO Auto-generated method stub
Pet pet=new Cat("小喵", 85, 85,85);
pet.print();
System.out.println("--------");
Master master=new Master("小小");
master.feed(pet,"小鱼干");

      }

}
```

### Cat1

```java
package Inherit;

public class Cat1 extends Pet {

	public Cat1() {
	}

	public Cat1(String Name, int Health, int Love, int intimacy) {
		super(Name, Health, Love, intimacy);
	}

	/*
	 * public void eatSomething(String food) { if (this.getHealth() != 100) {
	 * this.setHealth(this.getHealth() + 4 <= 100 ? this.getHealth() + 4 : 100);
	 * System.out.println(this.getName() + "吃了" + food); } else {
	 * System.out.println(this.getName() + "已经饱了，稍后再喂"); } }
	 */
	public void playwith() {
		if (this.getHealth() > 60) {
			System.out.println(this.getName() + "在玩逗猫棒游戏");
			this.setHealth(this.getHealth() - 3);
			this.setIntimacy(this.getIntimacy() + 2);
		} else {
			System.out.println(this.getName() + "在懒洋洋的睡觉");
		}
	}

}
```

### Cat1Test

```java
package Inherit;

public class Cat1Test {

	public static void main(String[] args) {
		Cat1 cat = new Cat1("小喵", 85, 85, 85);
		System.out.println("--------");
		Master master = new Master("小小");
		master.feed(cat, "小鱼干");
		cat.eatSomething("");

		Pet pet4 = master.getPet("猫咪");
		pet4.print();

		master.playwith(pet4);
	}

}
```

### Customer

```java
package Inherit;

public class Customer {
	private String name;

	public String getName() {
		return name;
	}

	public void setName(String name) {
		this.name = name;
	}

	public Customer() {

	}

	public Customer(String name) {
		this.name = name;
	}

	public void Submit(Printer printer) {
		System.out.println("客户姓名:" + getName());
		System.out.println(getName() + "提交打印任务");
		/*if (printer instanceof PrinterColor) {
			PrinterColor printerColor = (PrinterColor) printer;
			printerColor.print();
		} else {
			System.out.println(this.getName() + "的彩色打印任务未完成");

		}
		if (printer instanceof PrinterFlat) {
			PrinterFlat printerFlat = (PrinterFlat) printer;
			printerFlat.print();
		} else {
			System.out.println(this.getName() + "的黑白平面打印任务未完成");

		}
		if (printer instanceof Printer3DColor) {
			Printer3DColor printer3DColor = (Printer3DColor) printer;
			printer3DColor.print();
		} else {
			System.out.println(this.getName() + "的三维彩色打印任务未完成");

		}*/
	}
}
```

### Dog

```java
package Inherit;

public class Dog extends Pet {
	private String strain;

	public String getStrain() {
		return strain;
	}

	public void setStrain(String strain) {
		this.strain = strain;
	}

	public Dog() {

		System.out.println("子类Dog的无参构造方法");

	}

	public Dog(String name, int health, int love, String strain,int intimacy) {
		// this.name=name; //不能直接访问父类的private属性
		/*
		 * System.out.println("子类Dog的有参构造方法");
		 * super.setName(name);//可以通过父类的public的setter方法来访问父类的属性 super.setHealth(health);
		 * super.setLove(love); this.strain=strain;
		 */

		super(name, health, love,intimacy);// 这个和上面的代码可以达到同样的效果
		this.strain = strain;
		System.out.println("子类Dog的有参构造方法");
	}

	public void print() {
		super.print();

		/*
		 * System.out.println("名称："+this.name); System.out.println("健康指数："+this.health);
		 * System.out.println("可爱指数："+this.love);
		 */
		System.out.println("品种：" + strain);
	}

	public void eatSomething(String food) {
		System.out.println(this.getName() + "正在吃" + food);
		if (this.getHealth() != 100) {

			this.setHealth(this.getHealth() + 3 <= 100 ? this.getHealth() + 3 : 100);
			System.out.println(this.getName() + "吃了" + food);
		} else {
			System.out.println(this.getName() + "已经饱了，稍后再喂");
		}
	}
}
```

### Employee

```java
package Inherit;

public class Employee {

	private String name;
	private int age;
	private String sex;
	private int pay;

	public String getName() {
		return name;
	}

	public void setName(String name) {
		this.name = name;
	}

	public int getAge() {
		return age;
	}

	public void setAge(int age) {
		this.age = age;
	}

	public String getSex() {
		return sex;
	}

	public void setSex(String sex) {
		this.sex = sex;
	}

	public int getPay() {
		return pay;
	}

	public void setPay(int pay) {
		this.pay = pay;
	}

	public Employee(String name, int age, String sex, int pay) {
		super();
		this.name = name;
		this.age = age;
		this.sex = sex;
		this.pay = pay;
	}

	public void printlncomebyMonth() {
		System.out.println("姓名:" + this.name);
		System.out.println("年龄:" + this.age);
		System.out.println("性别:" + this.sex);
		System.out.println("基本月薪:" + this.pay);
		System.out.println("----------------");
	}

}
```

### EmployeeTest

```java
package Inherit;

public class EmployeeTest {

	public static void main(String[] args) {

		Employee employee = new Employee("赵某", 23, "男", 4500);

		Officer officer = new Officer("李某", 26, "女", 5000, "秘书", 2000);
		Manager manager = new Manager("张某", 31, "男", 6000, "总经理", 2000, 1000, 8000);
		employee.printlncomebyMonth();

		officer.printlncomebyMonth();

		manager.printlncomebyMonth();

	}

}
```

### Employee1

```java
package Inherit;

public class Employee1 {

	private String name;
	private int age;
	private String sex;
	private int pay;

	public String getName() {
		return name;
	}

	public void setName(String name) {
		this.name = name;
	}

	public int getAge() {
		return age;
	}

	public void setAge(int age) {
		this.age = age;
	}

	public String getSex() {
		return sex;
	}

	public void setSex(String sex) {
		this.sex = sex;
	}

	public int getPay() {
		return pay;
	}

	public void setPay(int pay) {
		this.pay = pay;
	}

	public Employee1(String name, int age, String sex, int pay) {
		super();
		this.name = name;
		this.age = age;
		this.sex = sex;
		this.pay = pay;
	}

	public void printlncomeFullYear() {
		System.out.println("姓名:" + this.name);
		System.out.println("年龄:" + this.age);
		System.out.println("性别:" + this.sex);
		System.out.println("基本月薪:" + this.pay);
		System.out.println("----------------");
	}


	public void print() {
		// TODO Auto-generated method stub
		
	}

}
```

### Employee1Test

```java
package Inherit;

public class Employee1Test {

	public static void main(String[] args) {
		Employee1 employee2 = new Employee1("小明", 24, "男", 5000);
		employee2.print();
		employee2.printlncomeFullYear();
		Managers manager = new Managers("小慕", 28, "男", 100000, 0.1, 8000);
		manager.print();
		manager.printcomeFullYear();
	}

}
```

### Friend

```java
package Inherit;

public abstract class Friend {

	private String name;
	private int age;
	private String sex;

	public String getName() {
		return name;
	}

	public void setName(String name) {
		this.name = name;
	}

	public int getAge() {
		return age;
	}

	public void setAge(int age) {
		this.age = age;
	}

	public String getSex() {
		return sex;
	}

	public void setSex(String sex) {
		this.sex = sex;
	}

	public Friend() {
		super();
	}

	public Friend(String name, int age, String sex) {
		super();
		this.name = name;
		this.age = age;
		this.sex = sex;
	}

	public abstract void sayhello(Host host);

}
```

### FriendChinese

```java
package Inherit;

public class FriendChinese extends Friend {
	public FriendChinese() {
		super();
	}

	public FriendChinese(String name, int age, String sex) {
		super(name, age, sex);
	}

	@Override
	public void sayhello(Host host) {
		System.out.println("中国客人：" + host.getName() + ",你好!好久不见。");
	}
}
```

### FriendForeign

```java
package Inherit;

public class FriendForeign extends Friend {

	public FriendForeign() {
		super();
	}

	public FriendForeign(String name, int age, String sex) {
		super(name, age, sex);
	}

	public void sayhello(Host host) {
		System.out.println("外国客人：Hi." + host.getName() + ",A cup of tea.");
	}

}
```

### Goat

```java
package Inherit;

public  class Goat extends Animal {
	public Goat() {

	}

	public Goat(String name) {
		super(name);
	}

	public void run() {
		System.out.println(this.getName() + "正在奔跑");
	}

	public void eating(String food) {
		System.out.println(this.getName() + "正在吃" + food);
	}

	@Override
	public void eatSomething(String food) {
		// TODO Auto-generated method stub
		
	}
}
```

### Host

```java
package Inherit;

public class Host {

	private String name;
	private int age;
	private String sex;

	public String getName() {
		return name;
	}

	public void setName(String name) {
		this.name = name;
	}

	public int getAge() {
		return age;
	}

	public void setAge(int age) {
		this.age = age;
	}

	public String getSex() {
		return sex;
	}

	public void setSex(String sex) {
		this.sex = sex;
	}

	public Host(String name, int age, String sex) {
		super();
		this.name = name;
		this.age = age;
		this.sex = sex;
	}

	public void Serving(Friend friend, Host host) {
		if (friend instanceof FriendChinese) {
			System.out.println("主人：你好。" + friend.getName() + ",你有什么需要的?");
			friend.sayhello(host);
			System.out.println("中国客人：一个草莓蛋糕打包。");
			System.out.println("主人：好的，我现在去做。");
			System.out.println("中国客人：谢谢。");

		} else if (friend instanceof FriendForeign) {
			System.out.println("-----------");
			System.out.println("主人：Hello." + friend.getName() + ",What do you want to eat or drink?");
			friend.sayhello(host);

			System.out.println("主人：Anything else ?");
			System.out.println("外国客人：No，thanks.");
		}
	}
}
```

### HostTest

```java
package Inherit;

public class HostTest {

	public static void main(String[] args) {
		Host host1 = new Host("李立", 25, "男");
		FriendChinese friendChinese1 = new FriendChinese("小明", 22, "男");
		FriendForeign friendForeign1 = new FriendForeign("Sary", 23, "女");
		host1.Serving(friendChinese1, host1);
		host1.Serving(friendForeign1, host1);

	}
}
```

### Manager

```java
package Inherit;

public class Manager extends Officer {

	private int equity;// 股权
	private int sum;// 总股本

	public int getEquity() {
		return equity;
	}

	public void setEquity(int equity) {
		this.equity = equity;
	}

	public int getSum() {
		return sum;
	}

	public void setSum(int sum) {
		this.sum = sum;
	}

	public Manager(String name, int age, String sex, int pay, String position, int subsidy, int equity, int sum) {
		super(name, age, sex, pay, position, subsidy);
		this.equity = equity;
		this.sum = sum;
	}

	public void printlncomebyMonth() {
		System.out.println("姓名:" + getName());
		System.out.println("年龄:" + getAge());
		System.out.println("性别:" + getSex());
		System.out.println("基本月薪:" + getPay());
		System.out.println("职位：" + getPosition());
		System.out.println("行政补贴：" + getSubsidy());
		System.out.println("股权分红：" + getEquity() * getSum());
        System.out.println("月薪为："+getPay()+equity*sum+getSubsidy());

		System.out.println("----------------");

	}
}
```

### Managers

```java
package Inherit;

public class Managers extends Employee1 {

	private int equity;// 股权
	private int sum;// 总股本

	public int getEquity() {
		return equity;
	}

	public void setEquity(int equity) {
		this.equity = equity;
	}

	public int getSum() {
		return sum;
	}

	public void setSum(int sum) {
		this.sum = sum;
	}

	public Managers(String name, int age, String sex, int pay, double equity, int sum) {
		super(name, age, sex, pay);
		this.equity = (int) equity;
		this.sum = sum;
	}

	public void print() {
		super.print();
	}

	public void printcomeFullYear() {
		System.out.println("总经理的年薪:" + 12 * (getPay() + equity * sum));
	}
}
```

### Master

```java
package Inherit;

import Inherit.Dog;
import Inherit.Penguin;

public class Master {

	private String name;

	public String getName() {
		return name;
	}

	public void setName(String name) {
		this.name = name;
	}

	public Master() {
		
	}

	public Master(String name) {
		this.name = name;
	}
	
	/*public void feed(Penguin peg, String food) {
	    peg.eatSomething(food);
		
	}
	public void feed(Dog dog,String food) {
		dog.eatSomrthing(food);
		
	}*/
	
	public void feed(Pet pet,String food) {
		System.out.println(this.getName()+"喂给");
		pet.eatSomething(food);
		pet.print();
	}
	
	public Pet getPet(String typeID) {
		
		if("狗".equals(typeID)) {
			return new Dog("旺财", 90, 80, "京巴",80);
		}
		else if("企鹅".equals(typeID)) {
			return new Penguin("QQ", 80, 90, "雌",80);
		}else {"猫咪".equals(typeID);
            return new Cat("小喵", 85, 85,85);
        }
	}
	public void playwith(Pet pet) {
		
		}
	}
```

### Officer

```java
package Inherit;

public class Officer extends Employee {

	private String position;
	private int subsidy;

	public String getPosition() {
		return position;
	}

	public void setPosition(String position) {
		this.position = position;
	}

	public int getSubsidy() {
		return subsidy;
	}

	public void setSubsidy(int subsidy) {
		this.subsidy = subsidy;
	}

	public Officer(String name, int age, String sex, int pay, String position, int subsidy) {
		super(name, age, sex, pay);
		this.position = position;
		this.subsidy = subsidy;
	}

	public void printlncomebyMonth() {
		System.out.println("姓名:" + getName());
		System.out.println("年龄:" + getAge());
		System.out.println("性别:" + getSex());
		System.out.println("基本月薪:" + getPay());
		System.out.println("职位：" + position);
		System.out.println("行政补贴：" + subsidy);

		System.out.println("----------------");
	}

}
```

### Penguin

```java
package Inherit;

public class Penguin extends Pet {

	
	private String sex;

	public String getStrain() {
		return sex;
	}
	
	public void setStrain(String sex) {
		this.sex = sex;
	}
	
	public Penguin() {
		
	}
	
	public Penguin(String name,int health,int love,String sex,int intimacy){
		super(name,health,love,intimacy);
		this.sex=sex;	
	
	}
	
	public void print() {
		super.print();
		System.out.println("性别："+sex);
	}

	public void eatSomething(String food) {
		// TODO Auto-generated method stub
		if(this.getHealth()!=100){
			   this.setHealth(this.getHealth()+5<=100?this.getHealth()+5:100);
			      System.out.println(this.getName()+"吃了"+food);
		}
		else {
				  System.out.println(this.getName()+"已经饱了，稍后再喂");
			  }
	}
}
```

### PenguinTest

```java
package Inherit;

public class PenguinTest {

	public static void main(String[] args) {

		Penguin penguin3 = new Penguin("pig", 90, 80, "女", 85);

		penguin3.print();
	}
}
```

### Pet

```java

package Inherit;

public class Pet {
	private String name;
	private int health;
	private int love;
private int intimacy;
	

	public String getName() {
		return name;
	}

	public void setName(String name) {
		this.name = name;
	}

	public int getHealth() {
		return health;
	}

	public void setHealth(int health) {
		this.health = health;
	}

	public int getLove() {
		return love;
	}

	public void setLove(int love) {
		this.love = love;
	}
	public int getIntimacy() {
		return intimacy;
	}

	public void setIntimacy(int intimacy) {
		this.intimacy = intimacy;
	}
	public Pet(String name) {
		/*
		 * this.name=name; this.health=60; this.love=60;
		 */
		this(name, 60, 60,60);
	}

	public Pet() {
		System.out.println("Pet的无参构造方法");

	}
	
	public Pet(String name, int health, int love,int intimacy) {
		this.name = name;
		this.health = health;
		this.love = love;
		this.intimacy=intimacy;
	}

	public void playwith(String toy) {
		
	}
public void eatSomething(String food) {
	
}
	public void print() {
		System.out.println("---------------");
		System.out.println("名称:" + this.name);
		System.out.println("健康指数:" + this.health);
		System.out.println("可爱指数:" + this.love);
		System.out.println("亲密度："+this.intimacy);
	}
}
```

### PetTest

```java
package Inherit;

public class PetTest {

	public static void main(String[] args) {

		Dog dog = new Dog("旺财", 90, 80, "京巴",80);
		/*dog3.print();
		  Pet pet1=dog1;
	        pet1.print();*/

	     /*dog1.eatSomrthing("狗粮");
        System.out.println(dog1.getName()+"有"+dog1.getLegs()+"条腿");*/
		Penguin pgn = new Penguin("QQ", 80, 90, "雌",80);
		 /*Pet pet2=peg1;
		   peg1.print();  
		   pet2.print();*/
		Cat cat = new Cat("小喵", 85, 85,85);
		

		System.out.println("-----------");

		Master mst = new Master("张三");
		mst.feed(dog, "狗粮");
		mst.feed(pgn, "小鱼");
		mst.feed(cat, "猫粮");
	}
}
```

### Printer

```java
package Inherit;

public class Printer {
	private String name;

	public String getName() {
		return name;
	}

	public void setName(String name) {
		this.name = name;
	}

	public Printer(String name) {
		this.name = name;
	}

	public Printer() {

	}

	public void print() {
	}
}
```

### Printer3DColor

```java
package Inherit;

public class Printer3DColor extends Printer {
	public Printer3DColor() {

	}

	public Printer3DColor(String name) {
		super(name);
	}

	public void print() {
		System.out.println("----------");
		System.out.println(this.getName() + "使用中");
		System.out.println(this.getName() + "三维彩色打印");
	}
}
```
### PrinterColor

```java
package Inherit;

public class PrinterColor extends Printer {
	public PrinterColor() {

	}

	public PrinterColor(String name) {
		super(name);
	}

	public void print() {
		System.out.println("----------");
		System.out.println(this.getName() + "使用中");
		System.out.println(this.getName() + "彩色打印");
	}
}
```

### PrinterFlat

```java
package Inherit;

public class PrinterFlat extends Printer {
	public PrinterFlat() {

	}

	public PrinterFlat(String name) {
		super(name);
	}

	public void print() {
		System.out.println("----------");
		System.out.println(this.getName() + "使用中");
		System.out.println(this.getName() + "黑白平面打印");
	}
}
```

### PrinterTest

```java
package Inherit;

public class PrinterTest {

	public static void main(String[] args) {
		System.out.println("----------");
		System.out.println("打印机的种类：");
		Printer printer1 = new PrinterColor("彩色打印机");
		printer1.print();
		Printer printer2 = new PrinterFlat("黑白平面打印机");
		printer2.print();
		Printer printer3 = new Printer3DColor("三维彩色打印机");
		printer3.print();
		Customer customer = new Customer("小明");
		customer.Submit(printer1);
	}

}
```

### Truck

```java
package Inherit;

public class Truck extends Car {
	private int heavy;

	public int getHeavy() {
		return heavy;
	}

	public void setHeavy(int heavy) {
		this.heavy = heavy;
	}

	public Truck(String brand, int num, String energytype, int heavy) {
		super(brand, num, energytype);
		this.heavy = heavy;
	}

	public void print() {

		super.print();
		System.out.println("卡车的载重量为：" + heavy);
	}

	public void run() {

		System.out.println(this.heavy + "卡车在城市道路上行驶");
	}

}
```

### User

```java
package Inherit;

public class User {

	private String name;
	private String phonenum;

	public String getName() {
		return name;
	}

	public void setName(String name) {
		this.name = name;
	}

	public String getPhonenum() {
		return phonenum;
	}

	public void setPhonenum(String phonenum) {
		this.phonenum = phonenum;
	}

	public User(String name, String phonenum) {
		super();
		this.name = name;
		this.phonenum = phonenum;
	}

	public boolean equals(Object object) {
		if (object instanceof User) {
			User user = (User) object;
			if (this.getPhonenum().equals(user.getPhonenum())) {
				return true;
			} else {
				return false;
			}
		} else {
			return false;
		}
	}

	public String toString() {
		return "姓名：" + this.getName() + "    手机号码：" + this.getPhonenum();
	}
}
```

### UserTest

```java
package Inherit;

public class UserTest {

	public static void main(String[] args) {

		User user = new User("小明", "12345678989");
		System.out.println(user.toString());
	}

}
```

### Wolf

```java
package Inherit;

public  class Wolf extends Animal {

	public Wolf() {

	}

	public Wolf(String name) {
		super(name);
	}

	public void run() {
		System.out.println(this.getName() + "正在奔跑");
	}

	public void eating(String food) {
		System.out.println(this.getName() + "正在吃" + food);
	}

	@Override
	public void eatSomething(String food) {
		// TODO Auto-generated method stub
		
	}
}
```