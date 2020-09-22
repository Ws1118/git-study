# 基本数据类型

### 整型数

(没有小数部分的数值型数。如123.0则不是整型数。)

- 字节型 byte 

（用一个字节‘8个二进制数’表示整型数，所以字节表示的范围为-128～127。）

- 短整型 short

（用两个字节‘16个二进制数’表示整型数，所以字节表示的范围为-32768～32767。）

- 基本整型 int

- 长整型 long

### 实型数(浮点数)

- 单精度数 float
- 双精度数 double

### 字符型数 char

### 布尔型数 boolean

```java
public static void main(String[] args) {
		// 数字型变量
		byte b1 = 4;
		short a2 = 257;
		int i3 = 65547;
		long i4 = 456L;
		float f5 = 3.458997f;
		double d6 = 1.123456789123456789123456789;
		// 字符型
		char c7 = 'v';
		char c8 = '中';
		// 布尔型
		System.out.println("我");
	}
```

数值型数据按精度从低到高的次序为：byte→short →char →int →long →float →double

| 转义字符 | 含义                | 转义字符 | 含义                        |
| -------- | ------------------- | -------- | --------------------------- |
| \a       | 响铃Bell            | \ '      | 单引号                      |
| \b       | 退格键Backspace     | \ \      | 字符' \ '                   |
| \f       | 换页form feed       | \ ""     | 双引号                      |
| \n       | 换行line feed       | \u0000   | 空字符"                     |
| \r       | 回车carriage return | \ddd     | 3个八进制数表示的转义字符   |
| \t       | 制表键Tab           | \udddd   | 4个十六进制数表示的转义字符 |

### 运算符：

| 运算符                                          | 含义                           | 举例                    |
| ----------------------------------------------- | ------------------------------ | ----------------------- |
| +、-、*、/、%                                   | 二元算数运算符                 | 2* 3.14* radius         |
| +、-、++、--                                    | 一元算数运算符                 | i++、--j                |
| \>、>=、<、<=、==、!=                           | 关系运算符                     | x>y、a+b==c+d           |
| &&、\|\|、！                                    | 逻辑运算符                     | x>y&&a+b==c+d           |
| &、\|、^、<<、>>、>>>                           | 位运算符                       | x&y、a>>2               |
| =                                               | 赋值运算符                     | x=a+b                   |
| ?:                                              | 条件运算符                     | x>y?x:y                 |
| +=、-=、*=、/=、%=、&=、^=、\|=、<<=、>>=、>>>= | 扩展的赋值运算符               | x+=a+b                  |
| instanceof                                      | 判断某一对象是否是某个类的实例 | aStu instanceof Student |

- 1.算术运算符（Java中共有9个算数运算符，其中包含5个二元运算符，4个一元运算符）
  - 二元运算符:+（加）、-（减）、*（乘）、/（除）和%（取余）做除法和取余运算时必须是整型数
    在Java中应写成：（-b+Math.sqrt(b * b-4*a*c))/(2*a)*
  - 一元运算符:+（取正）、-（取负）、++（变量值增加1）和--（变量值减少1）
    - 如下两组运算：int i=10,j;             int i=10,j;        j=++i;                           j=i++;
    - 此时前缀与后缀是不同的
    - 如果单独使变量增加1或减1，如：i++; 则不用考虑前缀还是后缀
- 关系运算符（共6个）&gt;(大于）、&gt;=(大于或等于）、&lt;(小于）、&lt;=(小于或等于）、==（等于）和！=（不等于）
  - 关系运算的结果是一个逻辑值：true或false
  - 关系运算符中&gt;、&gt;=、&lt;和&lt;=的优先级相同，==和！=的优先级相同，后两个的优先级小于前4个
  - 逻辑运算符（共3个）&amp;&amp;（与）、||（或）、！（非）。前两个是二元运算符，后一个是一元运算符。
  - 除运算符()、[]和.外，！（逻辑非）运算符的优先级比其他运算符的优先级都高，&amp;&amp;和||的优先级低于关系运算符，而&amp;&amp;的优先级比||高。
- 位运算符（共7个）:&amp;（位与）、|（位或）、~（位反）、^(位异或)、&lt;&lt;(位左移）、&gt;&gt;（位右移，算数右移）、&gt;&gt;&gt;(无符号位右移），其中只有&quot;~&quot;是一元运算符，其余都是二元运算符
- 位与运算；位或运算；位反运算；位异或运算；位左移运算；位右移运算；无符号位右移运算
- 条件运算符
- 赋值运算符
  - 基本的赋值运算符
  - 扩展的赋值运算符
- 类型比较运算

## if

```java
public static void main(String[] args) {
		int Num, j;
		for (Num = 1, j = 1; Num <= 10; Num++) {
			j = Num * j;
			if (j > 400) {
				break;
			}
		}
		System.out.println("阶乘值大于400的最小自然数" + Num);
	}
```

```java
public static void main(String[] args) {
		int x = 10;
		if (x > 0 && x < 3) {
			double y = 1;
			System.out.println("y=" + y);
		} else if (3 <= x && x < 5) {
			double y = 2 * x;
			System.out.println("y=" + y);
		} else if (x > 5) {
			double y = x * x + 5 * x + 1;
			System.out.println("y=" + y);
		}
	}
```

```java
public static void main(String[] args) {
		boolean isVIP = true;
		double y = 5000;
		if (isVIP) {
			if (y > 200) {
				System.out.println("价格=" + 0.75 * y);
			} else if (y > 200) {
				System.out.println("价格=" + 0.8 * y);
				if (y > 100) {
					System.out.println("价格=" + 0.9 * y);
				} else {
					System.out.println("价格=" + y);
				}
			}
		}
	}
```

```java
public static void main(String[] args) {

		for (int chicken = 0, rabbit = 0; chicken <= 35; chicken++) {

			rabbit = 35 - chicken;

			if (chicken * 2 + rabbit * 4 == 94) {
				System.out.printf("鸡有%d只,兔有%d只",chicken,rabbit);
				
				break;
			}
		}		
	}
```

```java
public static void main(String[] args) {
		// TODO Auto-generated method stub
		Scanner reader=new Scanner(System.in);
		System.out.println("---欢迎进入作业提交系统---");
		System.out.println("请输入Java文件名：");
		String filename=reader.next();
		
		int index=filename.indexOf(".java");
		if(filename.length()==index+".java".length()) {
			System.out.println("对的");
    	}else {
    		System.out.println("错的");
    	}
    	
    	System.out.println();
	}
```

## switch

```java
public static void main(String[] args) {
		Scanner scan = new Scanner(System.in);
		System.out.println("输入星期几");
		int y = scan.nextInt();
		switch (y) {
		case 1:
        case 4:
			System.out.println("学习java");
			break;
		case 2:
        case 5:
			System.out.println("学习数学");
			break;
		case 3:
		case 6:
			System.out.println("学习英语");
			break;
		case 7:
			System.out.println("休息");
		}
	}
```

```java
public static void main(String[] args) {
		// TODO Auto-generated method stub
		 Scanner scan=new Scanner(System.in);
		int productNo = 0;
		String str = "y";
		str = scan.next();
		while (str.equals("y")) {
			System.out.println("请输入商品编号");
			productNo = scan.nextInt();
			switch (productNo) {
			case 1:
				System.out.println("苹果五块钱一斤");
				break;
			case 2:
				System.out.println("橘子三块钱一斤");
				break;
			case 3:
				System.out.println("香蕉四块钱一斤");
				break;
			default:
				System.out.println("查无此编号");
			}

		}
	}
```

## do while

```java
public static void main(String[] args) {
		// TODO Auto-generated method stub
		
		 Scanner scan=new Scanner(System.in);
				int score=0;
				do {
					System.out.println("再次学习");
					System.out.println("再次考试");
					System.out.println("得到考试成绩");
					score = scan.nextInt();
				}while(score<60);
				System.out.println("你过关了!");
			}
```

```java
public static void main(String[] args) {
	Scanner scan=new Scanner(System.in);
	double t=1000;
	int d=0;
	t=t/2;
	while(d<10) {
	System.out.println("第"+d+"天，剩余的长度为"+t);
	}
	d++;
	}
```
## for循环

```java
public static void main(String[] args) {

		int num = 0;
		double re = 0;
		double[][] arr1 = new double[5][];
		double[][] arr2 = new double[5][4];
		double[] sum = new double[5];
		double[] arg = new double[5];

		for (int i = 0; i < arr1.length; i++) {
			num = (int) (2 * Math.random() + 3);
			arr1[i] = new double[num];
			System.out.printf("正在准备存放第%d位学生的%d门成绩：\n", i + 1, num);
			System.out.println("--------");
			Scanner scan = new Scanner(System.in);
			for (int j = 0; j < num; j++) {
				System.out.printf("请输入该学生的第%d门课成绩\n:", j + 1);
				arr1[i][j] = scan.nextDouble();
			}

		}
		System.out.println("--------");

		for (int i = 0; i < arr1.length; i++) {
			for (int j = 0; j < arr1[i].length; j++) {
				sum[i] += arr1[i][j];
			}
			arg[i] = sum[i] / arr1[i].length;
		}

		for (int i = 0; i < arr1.length; i++) {
			for (int cs = 0; cs < arr1[i].length - 1; cs++) {
				for (int j = 0; j < arr1[i].length - 1 - cs; j++) {
					if (arr1[i][j] > arr1[i][j + 1]) {
						re = arr1[i][j];
						arr1[i][j] = arr1[i][j + 1];
						arr1[i][j + 1] = re;
					}
				}
			}
		}

		for (int i = 0, j = 0; i < arr1.length; i++) {
			arr2[i][j] = sum[i];
			arr2[i][j + 1] = arg[i];
			arr2[i][j + 2] = arr1[i][arr1[i].length - 1];
			arr2[i][j + 3] = arr1[i][j];
		}
		System.out.println("--------");
		System.out.println("   " + "总分：" + "   " + "平均分：" + "   " + "最高分：" + "   " + "最低分：");

		for (double[] x : arr2) {
			for (double y : x) {
				System.out.print("  " + y);
			}
			System.out.println();
		}
		System.out.println("--------");

	}
```

```java
public static void main(String[] args) {
	
		Scanner scan = new Scanner(System.in);
			System.out.println("请输入该同学五门课程的成绩");
			double sum=0;
			int score=0;
			boolean flag=true;
			for(int i=0;i<5;i++) {
				System.out.println("请输入第"+(i+1)+"门课的成绩");
				score=scan.nextInt();
				if(score<0||score>100)
					{
					System.out.println("输入有误");
					flag=false;
					break;
					}
				System.out.println(score);
				sum+=score;
	          }
			if (flag=true)
			System.out.println("平均分为："+sum/5);

	}
```

```java
	public static void main(String[] args) {
		int sum = 0;
		for (int j = 1; j < 5; j++) {
			sum = 0;
			System.out.printf("外层第%d运算\n",j);
			for (int i = 1; i <= 10; i++) {
				System.out.printf("内层循环第%d\n",i);
				if (i % 2 != 0) {
					continue;
				}
				sum += i;
				
			}
			System.out.printf("外层第%d运算，得到的和为%d\n", j, sum);

		}
	}
```

```java
public static void main(String[] args) {
		int[] data;
		data = new int[] { 1, 2, 3, 4, 5, 98 };
		for (int i = 0; i < data.length; i++) {
			System.out.println(data[i]);
		}

	}
```

```java
	public static void main(String[] args) {
		int[] scores = new int[7];
		scores[0] = 90;
		scores[1] = 85;
		scores[2] = 82;
		scores[3] = 70;
		scores[4] = 60;

		int insertedscore = 75;
		int index =0;
		for (int i = 0; i < scores.length; i++) {
			if (insertedscore > scores[i]) {
				index = i;
				break;
			}
		}
		for (int i = scores.length - 2; i >= index; i--) {
			scores[i + 1] = scores[i];
		}
		scores[index] = insertedscore;
		for (int x : scores) {
			System.out.println(x);
		}

	}
```

```java
	public static void main(String[] args) {
		// TODO Auto-generated method stub
		int[][] arr20 = new int[10][5];
		for (int i = 0; i < arr20.length; i++) {
			for (int j = 0; j < arr20[0].length; j++) {
				arr20[i][j] = (int) (100 * Math.random());
			}
		}

		System.out.println(arr20);
		System.out.println(arr20[9]);
		System.out.println(arr20[9][4]);

		// 二维数组 的遍历
		// 第一层，遍历的是，指向一维数组int型数组的每个一维引用
		for (int[] row : arr20) {
			// 第二层，遍历的是，一维引用指向的每个元素
			for (int element : row) {
				System.out.print("  " + element);
			}
			System.out.println();
		}
	}
```

```java
public static void main(String[] args) {
		// TODO Auto-generated method stub
		char[][] chunxiao = new char[4][];
		chunxiao[0] = new char[5];
		chunxiao[0][0] = '春';
		chunxiao[0][1] = '眠';
		chunxiao[0][2] = '不';
		chunxiao[0][3] = '觉';
		chunxiao[0][4] = '晓';
		chunxiao[1] = new char[] { '处', '处', '闻', '啼', '鸟' };
		chunxiao[2] = new char[] { '夜', '来', '风', '雨', '声' };
		chunxiao[3] = new char[] { '花', '落', '知', '多', '少' };
		for (char[] clause : chunxiao) {
			for (char word : clause) {
				System.out.print("  " + word);
			}
			System.out.println();
		}
		System.out.println("------古诗词顺序------");
		for (int i = 0; i < chunxiao[0].length; i++) {
			for (int j = 0; j < chunxiao.length; j++) {
				System.out.print("  " + chunxiao[chunxiao.length - 1 - j][i]);
			}
			System.out.println();
		}

	}
```

```java
public static void main(String[] args) {
		// TODO Auto-generated method stub
		Scanner scan = new Scanner(System.in);
		System.out.print("请输入行数：");
		int rows = scan.nextInt();
		int[][] yanghui = new int[rows][];
		for (int i = 0; i < yanghui.length; i++) {
			yanghui[i] = new int[i + 1];
			for (int j = 0; j < yanghui[i].length; j++) {
				if (j == 0 || j == yanghui[i].length - 1) {
					yanghui[i][j] = 1;
				} else {
					yanghui[i][j] = yanghui[i - 1][j - 1] + yanghui[i - 1][j];
				}
				System.out.print("  " + yanghui[i][j]);
			}
			System.out.println();

		}
//使用增强型for循环
		System.out.println("-------增强型for循环输出-------");
		for(int[] row:yanghui) {
			for(int element:row) {
				System.out.print("  "+element);
			}
			System.out.println();
			}
		}
```

```java
public static void main(String[] args) {
		// TODO Auto-generated method stub
		// 直接赋值
		double[][] scores = { 
				{ 72, 60, 90 }, 
				{ 83, 51, 73 }, 
				{ 72, 66, 74 }, 
				{ 52, 62, 77 } 
				};
//第二种数组初始化
		scores = new double[5][3];
		scores[0][1] = 56.0;
//第三种初始化内容
		scores = new double[100][];
		scores[0] = new double[3];
		scores[0][2]=90;
		
//随机生成一个3或者4
		for(int i=0;i<scores.length;i++) {
		int rd=(int)(2*Math.random()+3);
		System.out.println(rd);
		scores[i]=new double[rd];
	     }
	}
```

```java
public static void main(String[] args) {
		// TODO Auto-generated method stub
		String str = "abc";
		str = str + "def" + 12345;
		System.out.println(str);

		int locchar = str.indexOf('d');
		System.out.println("第" + locchar + "个字符为" + 'd');

		int locsubstr = str.indexOf("123");
		System.out.println("第" + locsubstr + "个字符为" + "123");

		String date = "20191118";
		String month = date.substring(4, 6);
		String day = date.substring(6);
		
		String words="长亭外 古道边 芳草碧连天 晚风扶 柳笛声残 夕阳山外山";
		String[] strarr=words.split("  ");
		for(String word:strarr) {
			System.out.println(word);
		}


        words="长亭外,古道边,芳草碧连天,晚风扶,柳笛声残 夕阳山外山";
        
        strarr=words.split(",");
        for(String word:strarr) {
        	System.out.println(word);
        }
		System.out.println("月份为" + month + "," + day + "号");

		String str2 = "xyz";
		String str3 = str2.concat("abc");
		System.out.println(str3);
	}
```



## do while; if else

```java
	public static void main(String[] args) {
		// TODO Auto-generated method stub
		Scanner reader = new Scanner(System.in);
		String username = null, password = null, repassword = null;
		boolean flag = true;

		do {
			System.out.println("请输入用户名：");
			username = reader.next();
			System.out.println("请输入密码：");
			password = reader.next();
			System.out.println("请再次输入密码：");
			repassword = reader.next();
			flag = verify(username, password, repassword);

		} while (flag == false);
	}

	public static boolean verify(String name, String pass, String repass) {
		if (name.length() >= 3) {
			if (pass.length() >= 6) {
				if (pass.equals(repass)) {
					return true;
				} else {
					System.out.println("密码不相同");
					return false;
				}
			} else {
				System.out.println("密码不合法");
				return false;
			}
		} else {
			System.out.println("名字不合法");
			return false;
		}
	}
```

```java
public static void main(String[] args) {
		Scanner reader = new Scanner(System.in);
		String username = null, password = null, repassword = null;
		boolean flag = false;
		do {
			System.out.println("请输入用户名：");
			username = reader.next();
			if (username.length() > 3) {
				System.out.println("请输入密码：");
				password = reader.next();
				if (password.length() >= 6) {
					System.out.println("请再次输入密码：");
					repassword = reader.next();
					if (repassword.equals(password)) {
						System.out.println("注册成功");
						break;
					} else {
						System.out.println("第一次和第二次输入的密码不同，注册失败");
					}
				} else {
					System.out.println("密码输入错误");
				}
			} else {
				System.out.println("用户名输入错误");
			}
		} while (true);
	}
```

```java
public static void main(String[] args) {
		// TODO Auto-generated method stub
		
				System.out.println("字符串常量");
				String str = "字符串变量的值";
				System.out.println(str);

				str = new String("这是new出来的字符串");
				System.out.println(str);

				int length = str.length();
				System.out.println("如上字符串的长度为" + length);
				
				Scanner scan = new Scanner(System.in);
				String password = null;
				do {
					System.out.println("请输入密码：");

					password = scan.next();

					if (password.length() < 6) {
						System.out.println("输入的密码长度不能小于6,请重新输入");
					}
					else {
						break;
					}
				} while (true);

			}
```

## String; int

```java
// 属性，fields
	String name, major;
	int studentNum;

	// 方法，行为
	public void lizkPrintln() {
		System.out.println("-----------");
		System.out.println("班级名称：" + name);
		System.out.println("班级人数" + studentNum);
		System.out.println("专业名称：" + major);
		System.out.println();
	}


public static void main(String[] args) {
		// TODO Auto-generated method stub
		Data21_1 soft1921;
		soft1921 = new Data21_1();
		soft1921.name = "软件1921";
		soft1921.studentNum = 40;
		soft1921.major = "软件技术专业";

		soft1921.lizkPrintln();
	}
```

```java
	String name, banji;
	int age, xuehao;

	public void printInfo() {
		System.out.println("--------");
		System.out.println("姓名" + name);
		System.out.println("年龄" + age);
		System.out.println("班级" + banji);
		System.out.println("学号" + xuehao);
		System.out.println();
	}


	public static void main(String[] args) {
		// TODO Auto-generated method stub
		Data21_3 student;
		student = new Data21_3();
		student.name = "王珊";
		student.age = 18;
		student.banji = "软件1921";
		student.xuehao = 1902343235;
		student.printInfo();
	}
```

```java
	String name;
	int age;

	@SuppressWarnings("unused")
	public void buyTicket() {
		int price = age > 16 ? 30 : 15;
		int name1;
		System.out.println(name + ",您购买的票的价格为" + price + "元");
	}

public static void main(String[] args) {
		// TODO Auto-generated method stub
		Data21_5 vs1 = new Data21_5();
		vs1.name = "xiaozhu";
		vs1.age = 15;
		vs1.buyTicket();

		Data21_5 vs2 = new Data21_5();
		vs2.name = "peiqi";
		vs2.age = 60;
        vs2.buyTicket();
	}
```

```java
	String username, password;

	public void prrintAdmin() {
		System.out.println("------");
		System.out.printf("用户名：%s,密码%s\n", username, password);
		System.out.println("-------");
	}

	@SuppressWarnings("resource")
	public void modifyPassword() {
		Scanner scan = new Scanner(System.in);
		System.out.println("请输入用户名：");
		String name = scan.next();

		if (name.equals(username) && password.equals(password)) {
			System.out.println("请输入新密码：");
			String repassword = scan.next();
			password = repassword;
			System.out.println("密码修改成功");
		} else {
			System.out.println("密码没有修改成功");
		}
	}
```

```java
String pinpai, ranyouleixing;
	int lunziNum;

	public void way() {
		System.out.println("品牌:" + pinpai);
		System.out.println("轮子个数:" + lunziNum);
		System.out.println("燃油类型:" + ranyouleixing);
	}
	
	
public static void main(String[] args) {
		// TODO Auto-generated method stub
		Data21_9 car = new Data21_9();
		car.pinpai = "宝马";
		car.lunziNum = 4;
		car.ranyouleixing = "汽油";
		car.way();
	}
```

## Battery

```java
public class Battery {
   String brand; // 品牌；

	public String charge() { // 方法，充电
		String brandcharge = this.brand + "正在放电";
		return brandcharge;
	 
	}
```

```java
public class Battery1 {
	String brand;// 电池的品牌

	public void getPower() {// 实现充电方法
		System.out.println(this.brand + "正在充电中");

	}
```

```java
public class Score {
	String name;       
	float chinesescore;
	float mathscore;
	float englishscore;

	public void printof() { 
		System.out.println("你好!");
		System.out.println("你三门课的总成绩为：" + (chinesescore + mathscore + englishscore));
		System.out.println("你三门课的平均成绩为：" + (chinesescore + mathscore + englishscore) / 3);

	} 
```

```java
public class ScoreCalc1 {
	private float Javascore;
	private float Cscore;
	private float Dscore;
	float average;
	float sum;

	public float sumscore() {
		sum = this.getJavascore() + this.getCscore() + this.getDscore();
		return sum;
	}

	public float averscore() {
		average = (this.getJavascore() + this.getCscore() + this.getDscore()) / 3;
		return average;
	}

	public void showsumscore() {
		System.out.println("总成绩为：" + sumscore());
	}

	public void showaverscore() {
		System.out.println("总成绩为：" + averscore());
	}

	public float getJavascore() {
		return Javascore;
	}

	public void setJavascore(float javascore) {
		Javascore = javascore;
	}

	public float getCscore() {
		return Cscore;
	}

	public void setCscore(float cscore) {
		Cscore = cscore;
	}

	public float getDscore() {
		return Dscore;
	}

	public void setDscore(float dscore) {
		Dscore = dscore;
	}
```

```java
public class Scoresearch {
        public static void main(String[] args) {
		// TODO Auto-generated method stub
		Score student = new Score();
		student.name = "qingqing";
		student.chinesescore = 90;
		student.mathscore = 95;
		student.englishscore = 97;
		student.printof();

	}
```

```java
public class TestBattery {

	public static void main(String[] args) {
		// TODO Auto-generated method stub
		Battery battery = new Battery();
//创建电池类对象
		battery.brand = "白象";
		System.out.println(battery.charge());
//调用电池类的方法
	}
```

```java
public class TestScoresCale1 {
	public static void main(String[] args) {
		ScoreCalc1 sc=new ScoreCalc1();//定义对象
		@SuppressWarnings("resource")
		Scanner scan=new Scanner(System.in);
		//从屏幕读入字符
	System.out.print("请输入Java成绩:");
	//读入Java成绩
	sc.setJavascore(scan.nextFloat());
	System.out.print("请输入C#成绩：");
	//读入C#成绩
	sc.setCscore(scan.nextFloat());
	System.out.print("请输入DB成绩：");
	//读入DB成绩
	sc.setDscore(scan.nextFloat());
	
	sc.showsumscore();
	//调用显示总成绩的方法
	sc.showaverscore();
	//调用显示平均成绩的方法
	}
```

