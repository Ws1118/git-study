## Interface

### AptitudeHandst

```java
package Interface;

public class AptitudeHandst extends Handset implements TheakePictures, Network {

	public AptitudeHandst(String brand, String type) {
		super(brand, type);
		System.out.println("手机品牌：" + this.getBrand() + "    型号：" + this.getType());
	}

	public void networkConn() {
		System.out.println("正在连接网络......");
	}

	@Override
	public void takePicture() {
		System.out.println("正在照相");
	}

	@Override
	public void sendInfo() {
		System.out.println("正在发送信息......");
	}

	@Override
	public void call() {
		System.out.println("正在通话中......");
	}

	@Override
	public void info() {
		System.out.println("正在接收信息.....");
	}
}
```

### CommonHandset

```java
package Interface;

public class CommonHandset extends Handset implements PlayWiring {

	public CommonHandset(String brand, String type) {
		super(brand, type);
		System.out.println("手机品牌：" + this.getBrand() + "    型号：" + this.getType());
	}

	public void play(String video) {
		System.out.println("正在播放视频" + video);
	}

	@Override
	public void sendInfo() {
		System.out.println("正在发送信息......");
	}

	@Override
	public void call() {
		System.out.println("正在通话中");
	}

	@Override
	public void info() {
		System.out.println("正在接收信息....");
	}
}
```

### Figure

```java
package Interface;

public interface Figure {
	void perimeter();

	void area();
}
```

### FigureTest

```java
package Interface;

public class FigureTest {

	public static void main(String[] args) {

		Round round = new Round(1);
		round.perimeter();
		round.area();

		Square square = new Square(2);
		square.perimeter();
		square.area();

		Triangle triangle = new Triangle(3, 4, 5, 4);
		triangle.perimeter();
		triangle.area();
	}

}
```

### Figure0

```java
package Interface;

public interface Figure0 {
	void show();
}
```

### Figure0Tset

```java
package Interface;

public class Figure0Tset {

	public static void main(String[] args) {
		Figure0 figure1 = new Square0("正方形");
		figure1.show();

	}

}
```

### Handset

```java
package Interface;

public abstract class Handset {
	private String brand;
	private String type;

	public Handset(String brand, String type) {
		super();
		this.brand = brand;
		this.type = type;
	}

	public String getBrand() {
		return brand;
	}

	public void setBrand(String brand) {
		this.brand = brand;
	}

	public String getType() {
		return type;
	}

	public void setType(String type) {
		this.type = type;
	}

	public Handset() {

	}

	public abstract void sendInfo();

	public abstract void call();

	public abstract void info();
}
```

### HandsetTest

```java
package Interface;

public class HandsetTest {

	public static void main(String[] args) {

		AptitudeHandst apt = new AptitudeHandst("华为", "P40");
		apt.info();
		apt.networkConn();
		apt.call();
		apt.sendInfo();
		apt.takePicture();

		CommonHandset com = new CommonHandset("小米", "CC9");
		com.info();
		com.play("视频");
		com.call();
		com.sendInfo();

	}
}
```

### Mobile

```java
package Interface;

public class Mobile implements USB {

	public void insert() {
		System.out.println("移动硬盘插入中...");
	}

	public void start() {
		System.out.println("移动硬盘启动中...");
	}

	public void stop() {
		System.out.println("停止移动硬盘的连接");
	}
}
```

### Mouse

```java
package Interface;

public class Mouse implements USB {

	public void insert() {
		System.out.println("鼠标插入中...");
	}

	public void start() {
		System.out.println("鼠标启动中...");
	}

	public void stop() {
		System.out.println("停止鼠标的连接");
	}
}
```

### Network

```java
package Interface;

public interface Network {
	void networkConn();
}
```

### PlayWiring

```java
package Interface;

public interface PlayWiring {
	void play(String video);
}
```

### Round

```java
package Interface;

public class Round implements Figure {
	private double radius;

	public double getRadius() {
		return radius;
	}

	public void setRadius(double radius) {
		this.radius = radius;
	}

	public Round(double radius) {
		super();
		this.radius = radius;
	}

	public double Roundperimeter() {
		return 2 * Math.PI * radius;
	}

	public double Roundarea() {
		return Math.PI * radius * radius;
	}

	@Override
	public void perimeter() {
		System.out.println("圆的周长为：" + Roundperimeter());
	}

	@Override
	public void area() {
		System.out.println("圆的面积为：" + Roundarea());
	}
}
```

### Square

```java
package Interface;

public class Square implements Figure {

	private double length;

	public double getLength() {
		return length;
	}

	public void setLength(double length) {
		this.length = length;
	}

	public Square(double length) {
		super();
		this.length = length;
	}

	public double Squareperimeter() {
		return 4 * length;
	}

	public double Squarearea() {
		return length * length;
	}

	@Override
	public void perimeter() {
		System.out.println("正方形的周长为：" + Squareperimeter());
	}

	@Override
	public void area() {
		System.out.println("正方形的面积为：" + Squarearea());
	}
}
```

### Square0

```java
package Interface;

public class Square0 implements Figure0 {
	private String name;

	public String getName() {
		return name;
	}

	public void setName(String name) {
		this.name = name;
	}

	public Square0(String name) {
		super();
		this.name = name;
	}

	public Square0() {

	}

	public void show() {
		System.out.println("显示" + this.getName());
	}
}
```

### TheakePictures

```java
package Interface;

public interface TheakePictures {
	void takePicture();

}
```

### Triangle

```java
package Interface;

public class Triangle implements Figure {
	
	private double base1;// 底边
	private double base2;
	private double base3;
	private double high;// 底边上的高

	public double getBase1() {
		return base1;
	}

	public void setBase1(double base1) {
		this.base1 = base1;
	}

	public double getBase2() {
		return base2;
	}

	public void setBase2(double base2) {
		this.base2 = base2;
	}

	public double getBase3() {
		return base3;
	}

	public void setBase3(double base3) {
		this.base3 = base3;
	}

	public double getHigh() {
		return high;
	}

	public void setHigh(double high) {
		this.high = high;
	}

	public Triangle(double base1, double base2, double base3, double high) {
		super();
		this.base1 = base1;
		this.base2 = base2;
		this.base3 = base3;
		this.high = high;
	}

	public double Triangleperimeter() {
		return base1 + base2 + base3;

	}

	public double Trianglearea() {
		return (base1 * high) / 2;
	}

	@Override
	public void perimeter() {
		System.out.println("三角形的周长为：" + Triangleperimeter());
	}

	@Override
	public void area() {
		System.out.println("三角形的面积为：" + Trianglearea());
	}
}
```

### UDisk

```java
package Interface;

public class UDisk implements USB {

	public void insert() {
		System.out.println("U盘插入中...");
	}

	public void start() {
		System.out.println("U盘启动中...");
	}

	public void stop() {
		System.out.println("停止U盘的连接");
	}
}
```

### USB

```java
package Interface;

public interface USB {
	void insert();

	void start();

	void stop();
}
```

### USBTest

```java
package Interface;

public class USBTest {

	public static void main(String[] args) {
		UDisk udisk = new UDisk();
		udisk.insert();
		udisk.start();
		udisk.stop();

		Mobile mobile = new Mobile();
		mobile.insert();
		mobile.start();
		mobile.stop();

		Mouse mouse = new Mouse();
		mouse.insert();
		mouse.start();
		mouse.stop();
	}

}
```
