```java
package supermarket2;

import java.util.List;
import java.util.Map;

/**
 * 账单类
 */
public class Bill {
    private String bid; //账单编号
    private Map<String, String> idAndNum; // 商品id和数量
    private String vipFlag; // vip标记 1.代表是会员 0.代表不是会员
    private String vipName; // vip姓名
    private String vipMoney; // vip余额
    private int vipIntegral; // vip积分
    private String total; // 总金额

    public String getBid() {
        return bid;
    }

    public void setBid(String bid) {
        this.bid = bid;
    }

    public Map<String, String> getIdAndNum() {
        return idAndNum;
    }

    public void setIdAndNum(Map<String, String> idAndNum) {
        this.idAndNum = idAndNum;
    }

    public String getVipFlag() {
        return vipFlag;
    }

    public void setVipFlag(String vipFlag) {
        this.vipFlag = vipFlag;
    }

    public String getVipName() {
        return vipName;
    }

    public void setVipName(String vipName) {
        this.vipName = vipName;
    }

    public String getVipMoney() {
        return vipMoney;
    }

    public void setVipMoney(String vipMoney) {
        this.vipMoney = vipMoney;
    }

    public int getVipIntegral() {
        return vipIntegral;
    }

    public void setVipIntegral(int vipIntegral) {
        this.vipIntegral = vipIntegral;
    }

    public String getTotal() {
        return total;
    }

    public void setTotal(String total) {
        this.total = total;
    }

    @Override
    public String toString() {
        return "Bill{" +
                "bid='" + bid + '\'' +
                ", idAndNum=" + idAndNum +
                ", vipFlag='" + vipFlag + '\'' +
                ", vipName='" + vipName + '\'' +
                ", vipMoney=" + vipMoney +
                ", vipIntegral=" + vipIntegral +
                ", total=" + total +
                '}';
    }
}
```

```java
package supermarket2;

import java.util.Scanner;

public class Festivalscost {
	

	public void festivalscost (){
		Scanner scan = new Scanner(System.in);
		int secondNum=0;
		  
		do {
			 
		System.out.println("————————————————");
		System.out.println("每周五所有商品打八八折");
		System.out.println("春节期间年货一律七折");
		System.out.println("儿童节学习用品打六六折");
		System.out.println("七夕节巧克力打七折");
		System.out.println("国庆节商品一律打六折");
		System.out.println("双十一所有商品打四折");
		System.out.println("双十二所有商品打五折");
		System.out.println("————————————————");
		System.out.println("\t 1.停留本界面");
		System.out.println("\t 0.返回上一界面");
		 secondNum =scan.nextInt();
		
		switch(secondNum) {
		case 1:
			Festivalscost fe=new Festivalscost();
			fe.festivalscost();
			break;
		case 0:
			System.out.println("返回上级菜单");
		   break;
		
		  default:
			System.out.println("请输入0-1之间的数");
			
		}			
		}while(secondNum!=0);
		
	}
}
```

```java
package supermarket2;

/**
 * 商品类
 * @author asus
 *
 */
public class Goods {
	
	private String gid; // 商品编号
	private String name; // 商品名字
	private String price; // 商品价格
	private int stock; // 商品库存

	public Goods() {
	}

	public Goods(String gid, String name, String price, int stock) {
		this.gid = gid;
		this.name = name;
		this.price = price;
		this.stock = stock;
	}

	public String getGid() {
		return gid;
	}
	public void setGid(String gid) {
		this.gid = gid;
	}
	public String getName() {
		return name;
	}
	public void setName(String name) {
		this.name = name;
	}
	public String getPrice() {
		return price;
	}
	public void setPrice(String price) {
		this.price = price;
	}
	public int getStock() {
		return stock;
	}
	public void setStock(int stock) {
		this.stock = stock;
	}
	@Override
	public String toString() {
		return "Goods [gid=" + gid + ", name=" + name + ", price=" + price + ", stock=" + stock + "]";
	}		
}
```

```java
package supermarket2;

import java.util.ArrayList;
import java.util.Scanner;

public class GoodsManage {

	// 商品库存管理
	static void goodsStockManage(ArrayList<Goods> goodsArray) {

		while (true) {
			// 用输出语句完主界面的编写
			System.out.println("---------欢迎进入商品库存管理系统---------");
			System.out.println("1. 查看商品");
			System.out.println("2. 新增商品");
			System.out.println("3. 修改商品");
			System.out.println("4. 删除商品");
			System.out.println("5. 返回方舟系统主菜单");
			System.out.println("请输入指令");
			// 用Scanner实现键盘录入数据
			Scanner input = new Scanner(System.in);
			String line = input.nextLine();
			// 用switch语句完成操作的选择
			switch (line) {

			case "1":
				searchGoods(goodsArray);
				break;

			case "2":
				addGoods(goodsArray);
				break;

			case "3":
				updateGoods(goodsArray);
				break;

			case "4":
				deleteGoods(goodsArray);
				break;

			case "5":
				ShopMenu.manageMenu(); // 返回到主菜单
			}
		}

	}
	// 查询商品
		public static void searchGoods(ArrayList<Goods> goodsArray) {

			// 如果商品集合为空
			if (goodsArray.isEmpty()) {
				System.out.println("暂无商品, 请先添加商品!");
				goodsStockManage(goodsArray);
			}

			// 展示商品
			showGoods(goodsArray);
		}

		// 展示商品
		public static void showGoods(ArrayList<Goods> goodsArray) {

			// 显示表头信息
			System.out.println("商品编号\t\t商品名称\t单价\t库存数量");

			// 将集合中数据取出按照对应格式显示商品信息
			for (int i = 0; i < goodsArray.size(); i++) {
				Goods g = goodsArray.get(i);
				System.out.println(g.getGid() + "\t" + g.getName() + "\t" + g.getPrice() + "\t" + g.getStock());
			}
		}

		// 新增商品
		private static void addGoods(ArrayList<Goods> goodsArray) {

			// 键盘录入学生对象所需要的数据，显示提示信息，提示要输入何种信息
			Scanner input = new Scanner(System.in);

			// 为了gid在while循环外面被访问到，我们就把他定义在了循环外；
			String gid;

			// 为了让程序回到这里，我们使用循环实现
			while (true) {
				System.out.println("请输入商品编号(建议9位)");
				gid = input.nextLine();
				boolean flag = isUsed(goodsArray, gid);
				if (flag) {
					System.out.println("你输入的商品编号已经被使用，请重新输入!");
				} else {
					break;
				}
			}

			System.out.println("请输入商品名称");
			String name = input.nextLine();
			System.out.println("请输入商品单价");
			String price = input.nextLine();
			System.out.println("请输入商品库存");
			int stock = input.nextInt();

			// 创建学生对象，把键盘录入的数据赋值给学生对象的成员变量
			Goods g = new Goods();
			g.setGid(gid);
			g.setName(name);
			g.setPrice(price);
			g.setStock(stock);
			// 把学生对象添加到集合中
			goodsArray.add(g);
			System.out.println("添加商品成功");
		}
		// 修改商品
		private static void updateGoods(ArrayList<Goods> goodsArray) {
			// 键盘录入要修改的商品编号，显示提示信息
			Scanner input = new Scanner(System.in);

			System.out.println("请输入你要修改的商品编号");
			String gid = input.nextLine();
			int flag = -1;
			flag = getFlag(goodsArray, gid); // 获取商品编号的索引
			if (flag == -1) {

				System.out.println("该信息不存在，无法修改，请重新输入！");
				return;

			} else {

				// 键盘录入要修改的学生信息
				System.out.println("请输入商品的新名称：");
				String name = input.nextLine();
				System.out.println("请输入商品的新单价：");
				String price = input.nextLine();
				System.out.println("请输入商品的新库存：");
				int stock = input.nextInt();

				// 创建学生对象
				Goods g = new Goods();
				g.setGid(gid);
				g.setName(name);
				g.setPrice(price);
				g.setStock(stock);

				// 根据上面的索引值修改对应的商品信息
				goodsArray.set(flag, g);

			}

			// 给出修改成功提示
			System.out.println("修改商品信息成功");
		}

		// 删除商品
		private static void deleteGoods(ArrayList<Goods> goodsArray) {
			// 键盘录入要删除的商品编号，显示提示信息。
			Scanner input = new Scanner(System.in);

			System.out.println("请输入你要删除的商品：");
			String gid = input.nextLine();
			// 再删除/修改商品操作前，对商品是否存在进行判断
			// 如果不存在，显示提示信息
			// 如在存在，进行遍历集合操作将对应商品对象从集合中删除
			int index = -1;
			index = getFlag(goodsArray, gid); // 获得索引
			if (index == -1) {
				System.out.println("该商品信息不存在，请重新输入");
			} else {
				goodsArray.remove(index);
				// 给出删除成功提示
				System.out.println("删除商品成功");
			}

		}
		// 管理员登录
		public static void adminLogin() {

			Scanner scan = new Scanner(System.in);
			Scanner reader = new Scanner(System.in);
			String username = null, password = null;
			String username1 = "szzcmy";
			String password1 = "247246";
			boolean flag = true;
			do {
				System.out.println("请输入用户名(szzcmy)：");
				username = reader.next();
				System.out.println("请输入密码：");
				password = reader.next();
				if (username.equals(username1) && password.equals(password1)) {
					System.out.println("登入成功!");
					flag = false;
				} else {
					System.out.println("用户名或密码输入错误，请重新输入:");
				}

			} while (flag);
		}

		// 判断商品编号是否被使用
		public static boolean isUsed(ArrayList<Goods> goodsArray, String gid) {
			// 如果与集合中的某一个商品编号相同，返回true；如果都不相同，返回false
			boolean flag = false;
			for (int i = 0; i < goodsArray.size(); i++) {
				Goods s = goodsArray.get(i);
				if (s.getGid().equals(gid)) {
					flag = true;
					break;
				}
			}
			return flag;
		}

		// 返回一个商品编号
		public static int getFlag(ArrayList<Goods> goodsArray, String gid) {
			int flag = -1;
			for (int j = 0; j < goodsArray.size(); j++) {

				Goods g1 = goodsArray.get(j);
				if (g1.getGid().equals(gid)) {

					flag = j;
					break;
				}

			}
			return flag;
		}

	}
```

```java
package supermarket2;

import java.math.BigDecimal;
import java.text.SimpleDateFormat;
import java.util.*;

public class MoneyManage {

    //购物车集合
    static Map<String, String> map = new HashMap<String, String>();

    // 收银管理
    static void moneyManage(ArrayList<Goods> goodsArray, ArrayList<Bill> billArray, ArrayList<Vip> vipArray) {
        while (true) {
            // 用输出语句完主界面的编写
            System.out.println("---------欢迎进入收银员系统---------");
            System.out.println("1. 查看所有的账单");
            System.out.println("2. 购物车");
            System.out.println("3. 结账");
            System.out.println("4. 返回方舟超市系统主菜单");
            System.out.println("请输入指令：");
            // 用Scanner实现键盘录入数据
            Scanner input = new Scanner(System.in);
            String line = input.nextLine();
            // 用switch语句完成操作的选择
            switch (line) {

                case "1":
                    searchBill(goodsArray, billArray, vipArray);
                    break;

                case "2":
                    shoppingCart(goodsArray, billArray, vipArray);
                    break;

                case "3":
                    closeAccounts(goodsArray, billArray, vipArray);
                    break;

                case "4":
                    ShopMenu.manageMenu(); // 返回到主菜单
            }
        }
    }

    // 结账
    private static void closeAccounts(ArrayList<Goods> goodsArray, ArrayList<Bill> billArray, ArrayList<Vip> vipArray) {
        showShopCart(map, goodsArray, billArray, vipArray); // 显示购物车数据
        Scanner sc = new Scanner(System.in);
        Bill bill = new Bill();
        System.out.println("是否有会员卡?(1有, 0没有)");
        String vipFlag = sc.nextLine();
        int index = 0;

        if("1".equals(vipFlag)) {
            while (true) {
                System.out.println("请输入你的会员卡号: ");
                String vid = sc.nextLine();
                index = isVip(vipArray, vid); //返回索引值, 方便打印账单
                if(index!=-1) {
                    break;
                }else if("-1".equals(vid)){
                    closeAccounts(goodsArray, billArray, vipArray);
                }else {
                    System.out.println("对不起, 不是会员, 请重新输入会员编号(或者按-1重新结账)");
                }
            }

            Vip vip = vipArray.get(index); // 通过索引得到会员
            bill.setBid(getBid());
            bill.setVipFlag(vipFlag);
            bill.setVipName(vip.getVipName());
            Map<String, String> actualMap = (Map<String, String>) ((HashMap<String, String>) map).clone();
            bill.setIdAndNum(actualMap);
            // 开始计算总金额
            String total = vipPrintBill(map, goodsArray,vipArray, index);
            bill.setTotal(total);
            bill.setVipMoney(vip.getVipMoney());
            bill.setVipIntegral(vip.getVipIntegral());
            billArray.add(bill);


        }else {
            bill.setBid(getBid());
            bill.setVipFlag(vipFlag);
            Map<String, String> actualMap = (Map<String, String>) ((HashMap<String, String>) map).clone();
            bill.setIdAndNum(actualMap);
            // 开始计算总金额
            String total = printBill(map, goodsArray);
            bill.setTotal(total);
            billArray.add(bill);

        }
    }

    // 显示购物车
    private static void showShopCart(Map<String, String> map, ArrayList<Goods> goodsArray, ArrayList<Bill> billArray, ArrayList<Vip> vipArray) {
        if(map.isEmpty()) {
            System.out.println("请先购买东西, 再进行结账!");
            moneyManage(goodsArray, billArray, vipArray);
        } else {
            System.out.println("购物车里有如下物品: ");
            Iterator it = map.keySet().iterator(); // 迭代器

            System.out.println("--------------购物车----------------");

            System.out.println("商品名称\t\t数量\t单价");
            // 遍历map集合
            while (it.hasNext()) {
                String key = it.next().toString(); // 主键
                // 商品名称
                String goodsName = findGoodsName(key, goodsArray);
                // 商品数量
                String goodsSize = map.get(key);
                // 商品单价
                String goodsPrice = findGoodsPrice(key, goodsArray);
                // 商品
                System.out.println(goodsName + "\t\t" + goodsSize + "\t" + goodsPrice);

            }
            System.out.println("1. 结账");
            System.out.println("2. 继续购买");
            Scanner sc = new Scanner(System.in);
            String selectNum = sc.nextLine();
            if ("2".equals(selectNum)) {
                moneyManage(goodsArray, billArray, vipArray);
            }
        }

    }
    // 收藏至购物车
    private static void shoppingCart(ArrayList<Goods> goodsArray, ArrayList<Bill> billArray, ArrayList<Vip> vipArray) {
        GoodsManage.showGoods(goodsArray);
        System.out.println("已进入购物车,请根据商品编号,添加到购物车");
        System.out.println("请输入你需要的商品(填写商品编号, 输入-1退出选择): ");

        Scanner sc = new Scanner(System.in);
        while (true) {
            System.out.println("请输入商品编号: ");
            String goodsId = sc.nextLine();

            if("-1".equals(goodsId)) {
                System.out.println("已退出购物车选择");
                break;
            }
            String goodsSize = "0";
            while(true) {
                System.out.println("请输入商品购买数量: ");
                goodsSize = sc.nextLine();
                int actualStock = findGoodsStock(goodsId, goodsArray);
                if( actualStock >= Integer.parseInt(goodsSize) || "-1".equals(goodsSize)) {
                    break;
                }else {
                    System.out.println("库存不足, 现存货" + actualStock + ", 请重新购买(按-1跳出此商品购买)");
                }
            }

            map.put(goodsId, goodsSize);

        }
        moneyManage(goodsArray, billArray, vipArray);

    }

    // 查询所有的账单
    private static void searchBill(ArrayList<Goods> goodsArray, ArrayList<Bill> billArray, ArrayList<Vip> vipArray) {

        // 如果商品集合为空
        if (billArray.isEmpty()) {
            System.out.println("暂无账单, 请先添加购物车,在结账生成账单!");
            moneyManage(goodsArray, billArray, vipArray);
        }

        // 展示账单
        showBill(goodsArray,billArray);
    }
    //展示账单
    private static void showBill(ArrayList<Goods> goodsArray, ArrayList<Bill> billArray) {

        // 显示表头信息
        System.out.println("------------账单-----------");

        // 将集合中数据取出按照对应格式显示商品信息
        for (int i = 0; i < billArray.size(); i++) {
            Bill b = billArray.get(i);
            System.out.println("账单编号: " + b.getBid());

            // 判断是否为会员
            if ("1".equals(b.getVipFlag())) {
                Map<String, String> idAndNum = b.getIdAndNum();
                Iterator it = idAndNum.keySet().iterator();
                double totalMoney = 0; // 总金额

                System.out.println("商品名称\t\t数量\t单价");

                // 遍历map集合
                while (it.hasNext()) {

                    String key = it.next().toString(); // 主键
                    // 商品名称
                    String goodsName = findGoodsName(key, goodsArray);
                    // 商品数量
                    String goodsSize = idAndNum.get(key);
                    // 商品单价
                    String goodsPrice = findGoodsPrice(key, goodsArray);
                    // 商品
                    System.out.println(goodsName + "\t\t" + goodsSize + "\t" + goodsPrice);

                }

                System.out.println("商品数量: " + idAndNum.size());
                System.out.println("商品总金额: " + b.getTotal());
                System.out.println("会员名称: " + b.getVipName());
                System.out.println("会员卡余额: " + b.getVipMoney());
                System.out.println("会员卡积分: " + b.getVipIntegral());
                System.out.println("-------------------------");
            } else {

                Map<String, String> idAndNum = b.getIdAndNum();
                Iterator it = idAndNum.keySet().iterator();
                double totalMoney = 0; // 总金额

                System.out.println("商品名称\t\t数量\t单价");

                // 遍历map集合
                while (it.hasNext()) {
                    String key = it.next().toString(); // 主键
                    // 商品名称
                    String goodsName = findGoodsName(key, goodsArray);
                    // 商品数量
                    String goodsSize = idAndNum.get(key);
                    // 商品单价
                    String goodsPrice = findGoodsPrice(key, goodsArray);
                    // 商品
                    System.out.println(goodsName + "\t\t" + goodsSize + "\t" + goodsPrice);

                }


                System.out.println("商品数量: " + idAndNum.size());
                System.out.println("商品总金额: " + b.getTotal());
                System.out.println("-------------------------");


            }
        }
    }
    // 收银员登录
    public static void CashierLogin() {

        Scanner scan = new Scanner(System.in);
        Scanner reader = new Scanner(System.in);
        String username = null, password = null;
        String username1 = "bncmy";
        String password1 = "247246";
        boolean flag = true;
        do {
            System.out.println("请输入用户名(bncmy)：");
            username = reader.next();
            System.out.println("请输入密码：");
            password = reader.next();
            if (username.equals(username1) && password.equals(password1)) {
                System.out.println("登入成功!");
                flag = false;
            } else {
                System.out.println("用户名或密码输入错误，请重新输入:");
            }

        } while (flag);
    }

    // 通过商品id找商品名称
    public static String findGoodsName(String goodsId, ArrayList<Goods> goodsArray) {

        String goodsName = "";

        for (int i = 0; i < goodsArray.size(); i++) {
            if(goodsArray.get(i).getGid().equals(goodsId)) {
                goodsName = goodsArray.get(i).getName();
            }
        }

        return goodsName;
    }

    // 通过商品id找商品库存
    public static int findGoodsStock(String goodsId, ArrayList<Goods> goodsArray) {

        int goodsStock = 0;

        for (int i = 0; i < goodsArray.size(); i++) {
            if(goodsArray.get(i).getGid().equals(goodsId)) {
                goodsStock = goodsArray.get(i).getStock();
            }
        }

        return goodsStock;
    }

    // 通过商品id找商品单价
    public static String findGoodsPrice(String goodsId, ArrayList<Goods> goodsArray) {

        String goodsPrice = "";

        for (int i = 0; i < goodsArray.size(); i++) {
            if(goodsArray.get(i).getGid().equals(goodsId)) {
                goodsPrice = goodsArray.get(i).getPrice();
            }
        }

        return goodsPrice;
    }

    // 通过商品id减少库存
    public static void reduceGoodsStock(String goodsId, ArrayList<Goods> goodsArray, String goodsSize) {
        int goodsStock = 0;

        for (int i = 0; i < goodsArray.size(); i++) {
            if(goodsArray.get(i).getGid().equals(goodsId)) {
                goodsStock = goodsArray.get(i).getStock();
                goodsArray.get(i).setStock(goodsStock-Integer.parseInt(goodsSize));
            }
        }

    }
 // 通过会员id找会员名称
    public static String findVipName(String vid, ArrayList<Vip> vipArray) {

        String vipName = "";

        for (int i = 0; i < vipArray.size(); i++) {
            if(vipArray.get(i).getVid().equals(vid)) {
                vipName = vipArray.get(i).getVipName();
            }
        }

        return vipName;
    }

    // 通过会员id找商品余额
    public static String findVipMoney(String vid, ArrayList<Vip> vipArray) {

        String vipMoney = "";

        for (int i = 0; i < vipArray.size(); i++) {
            if(vipArray.get(i).getVid().equals(vid)) {
                vipMoney = vipArray.get(i).getVipMoney();
            }
        }

        return vipMoney;
    }

    // 通过会员id增加会员积分
    public static int addVipIntegral(int index, ArrayList<Vip> vipArray, int vipIntegral) {

        int newVipIntegral = vipArray.get(index).getVipIntegral() + vipIntegral;  // 积分的计算规则
        vipArray.get(index).setVipIntegral(newVipIntegral);

        return newVipIntegral;
    }

    // 通过会员id减少会员余额
    public static String reduceVipMoney(String vid, ArrayList<Vip> vipArray, String vipMoney) {
        String newVipMoney = "";
        String newVipMoneyCpoy = "";
        BigDecimal money1 = new BigDecimal(vipMoney);

        for (int i = 0; i < vipArray.size(); i++) {
            if(vipArray.get(i).getVid().equals(vid)) {
                newVipMoney = vipArray.get(i).getVipMoney();
                BigDecimal money2 = new BigDecimal(newVipMoney);
                vipArray.get(i).setVipMoney(money2.subtract(money1).toString());
                newVipMoneyCpoy = vipArray.get(i).getVipMoney();
            }
        }
        return newVipMoneyCpoy;
    }

    // 查询会员id是否存在
    public static int isVip(ArrayList<Vip> vipArray, String vid) {

        int flag = -1;
        for (int j = 0; j < vipArray.size(); j++) {

            Vip v = vipArray.get(j);
            if (v.getVid().equals(vid)) {

                flag = j;
                break;
            }

        }
        return flag;
    }

    // 获得账单的编号 用年月日时分秒作为账单的编号
    public static String getBid () {

        Date date = new Date();
        SimpleDateFormat sdf = new SimpleDateFormat("yyMMddHHmmss");
        String format = sdf.format(date);
        return format;
    }
 // 打印发票
    public static String printBill(Map<String, String> map, ArrayList<Goods> goodsArray) {

        Iterator it = map.keySet().iterator(); // 迭代器

        double totalMoney = 0; // 总金额
        System.out.println("---------欢迎使用方舟购物系统----------");
        System.out.println("---------------小票-----------------");
        System.out.println("商品名称\t\t数量\t单价");
        int totalSize = 0 ; // 商品总数量
        BigDecimal sum = new BigDecimal("0");  // 总金额
        int mapSize = map.size();

        // 遍历map集合
        while (it.hasNext()) {
            String key = it.next().toString(); // 主键
            // 商品名称
            String goodsName = findGoodsName(key ,goodsArray);
            // 商品数量
            String goodsSize = map.get(key);
            BigDecimal goods_Size = new BigDecimal(goodsSize);
            totalSize += Integer.parseInt(goodsSize);
            // 商品单价
            String goodsPrice = findGoodsPrice(key, goodsArray);
            BigDecimal goods_Price = new BigDecimal(goodsPrice);
            sum = sum.add(goods_Price.multiply(goods_Size));
            // 商品
            System.out.println(goodsName +"\t\t" + goodsSize + "\t" + goodsPrice);

            // 减少库存
            reduceGoodsStock(key, goodsArray, goodsSize);

            // 打印后去除Map中的数据
            it.remove();
            map.remove(key);
        }


        System.out.println("商品种类: " + mapSize);
        System.out.println("商品总数量: " + totalSize);
        System.out.println("商品总额: " + sum.toString());
        System.out.println("-----------------------------------");

        return sum.toString();
    }

    // Vip打印发票
    public static String vipPrintBill(Map<String, String> map, ArrayList<Goods> goodsArray, ArrayList<Vip> vipArray, int index) {

        Iterator it1 = map.keySet().iterator(); // 迭代器
        Iterator it2 = map.keySet().iterator(); // 迭代器

        int totalSize = 0 ; // 商品总数量
        BigDecimal sum = new BigDecimal("0");  // 总金额
        BigDecimal advanceSum = new BigDecimal("0");  // 提前计算总金额
        
        Vip vip = vipArray.get(index); // 会员对象
        BigDecimal vipMoney = new BigDecimal(vip.getVipMoney());  // 会员卡余额
        String balance = ""; // 支付后会员余额
        int totalIntegral = 0; // 支付后会员积分

        int mapSize = map.size();

        // 遍历map集合
        while (it1.hasNext()) {
            String key = it1.next().toString(); // 主键

            // 商品数量
            String goodsSize = map.get(key);
            BigDecimal goods_Size = new BigDecimal(goodsSize);

            // 商品单价
            String goodsPrice = findGoodsPrice(key, goodsArray);
            BigDecimal goods_Price = new BigDecimal(goodsPrice);
            advanceSum = advanceSum.add(goods_Price.multiply(goods_Size));
        }

        if(vipMoney.compareTo(advanceSum) > -1) {
            System.out.println("会员卡里余额大于等于支付的总金额,是否选择会员卡余额支付?");
            System.out.println("1. 会员支付");
            System.out.println("2. 直接支付");
            Scanner sc = new Scanner(System.in);
            String payType = sc.nextLine();
            if("1".equals(payType)) {
                balance = reduceVipMoney(vip.getVid(), vipArray, advanceSum.toString()); // 支付扣卡里余额

            }
            totalIntegral = addVipIntegral(index, vipArray, Integer.parseInt(advanceSum.toString().split("\\.")[0])); // 会员增加积分
        }

        System.out.println("---------欢迎使用方舟购物系统----------");
        System.out.println("---------------小票-----------------");
        System.out.println("商品名称\t\t数量\t单价");
        // 遍历map集合
        while (it2.hasNext()) {
            String key = it2.next().toString(); // 主键
            // 商品名称
            String goodsName = findGoodsName(key ,goodsArray);
            // 商品数量
            String goodsSize = map.get(key);
            BigDecimal goods_Size = new BigDecimal(goodsSize);
            totalSize += Integer.parseInt(goodsSize);
            // 商品单价
            String goodsPrice = findGoodsPrice(key, goodsArray);
            BigDecimal goods_Price = new BigDecimal(goodsPrice);
            sum = sum.add(goods_Price.multiply(goods_Size));
            // 商品
            System.out.println(goodsName +"\t\t" + goodsSize + "\t" + goodsPrice);

            // 减少库存
            reduceGoodsStock(key, goodsArray, goodsSize);

            // 打印后去除Map中的数据
            it2.remove();
            map.remove(key);
        }

        System.out.println("商品种类: " + mapSize);
        System.out.println("商品总数量: " + totalSize);
        System.out.println("商品总额: " + sum.toString());
        System.out.println("会员编号:" + vip.getVid());
        System.out.println("会员余额:" + vip.getVipMoney());
//        System.out.println("检测会员余额是否修改" + balance);
        System.out.println("会员积分:" + vip.getVipIntegral());
//        System.out.println("检测会员积分是否修改:" + totalIntegral);
        System.out.println("-----------------------------------");

        return sum.toString();
    }
}
```

```java
package supermarket2;

import java.util.Arrays;
import java.util.List;

public class Repository {

    public static List<Goods> getArray() {

        Goods[] data = new Goods[38];
        data[0]= new Goods("201912000","八宝粥","4.5",10);
        data[1]= new Goods("201912001","可乐","3",10);
        data[2]= new Goods("201912002","矿泉水","2",10);
        data[3]= new Goods("201912003","椰子汁","8",10);
        data[4]= new Goods("201912004","牛奶","2",10);
        data[5]= new Goods("201912005","薯片","6",10);
        data[6]= new Goods("201912006","蛋糕","5",10);
        data[7]= new Goods("201912007","饼干","6",10);
        data[8]= new Goods("201912008","蛋黄酥","8",10);
        data[9]= new Goods("201912009","辣条","1.5",10);
        data[10]= new Goods("201912010","小鱼干","2",10);
        data[11]= new Goods("201912011","青菜","2",10);
        data[12]= new Goods("201912012","萝卜","1",10);
        data[13]= new Goods("201912013","金针菇","3",10);
        data[14]= new Goods("201912014","西兰花","4",10);
        data[15]= new Goods("201912015","香蕉","6",10);
        data[16]= new Goods("201912016","火龙果","8",10);
        data[17]= new Goods("201912017","苹果","16",10);
        data[18]= new Goods("201912018","草莓","38",10);
        data[19]= new Goods("201912019","牛肉","50",10);
        data[20]= new Goods("201912020","羊肉","50",10);
        data[21]= new Goods("201912021","猪肉","60",10);
        data[22]= new Goods("201912022","鸡肉","50",10);
        data[23]= new Goods("201912023","基围虾","38",10);
        data[24]= new Goods("201912024","带鱼","26",10);
        data[25]= new Goods("201912025","三文鱼","45",10);
        data[26]= new Goods("201912026","餐巾纸","15",10);
        data[27]= new Goods("201912027","毛巾","8",10);
        data[28]= new Goods("201912028","牙刷","6",10);
        data[29]= new Goods("201912029","洁厕灵","25",10);
        data[30]= new Goods("201912030","洗洁精","25",10);
        data[31]= new Goods("201912031","冰箱","8000",10);
        data[32]= new Goods("201912032","空调","8000",10);
        data[33]= new Goods("201912033","吹风机","200",10);
        data[34]= new Goods("201912034","风扇","300",10);
        data[35]= new Goods("201912035","小号塑料袋","0.5",10);
        data[36]= new Goods("201912036","中号塑料袋","0.8",10);
        data[37]= new Goods("201912037","大号塑料袋","1",10);
        List<Goods> goodsArray = Arrays.asList(data);
        return goodsArray;
    }
}
```

```java
package supermarket2;

import java.util.*;

import supermarket1.Festivalscost;

public class ShopMenu {
	// 创建集合对象，用于存储商品信息数据
	static List<Goods> array2 = Repository.getArray(); // 商品集合
	static ArrayList<Goods> goodsArray = new ArrayList<Goods>(array2);
	static ArrayList<Bill> billArray = new ArrayList<Bill>(); // 账单集合
	static ArrayList<Vip> vipArray = new ArrayList<Vip>(); // 会员集合

	public static void main(String[] args) {
		manageMenu();
	}
	
	// 主菜单
	static void manageMenu() {

		// 用循环完成再次回到主界面
		while (true) {
			// 用输出语句完主界面的编写
			System.out.println("---------欢迎进入方舟购物系统---------");
			System.out.println("1. 商品库存管理系统");
			System.out.println("2. 收银员管理系统");
			System.out.println("3. 会员管理系统");
			System.out.println("4. 活动期间打折查看");
			System.out.println("5. 退出方舟购物系统");
			System.out.println("请输入指令：");
			// 用Scanner实现键盘录入数据
			Scanner input = new Scanner(System.in);
			String line = input.nextLine();
			// 用switch语句完成操作的选择
			switch (line) {

			case "1":
				GoodsManage.adminLogin(); // 管理员登录
				GoodsManage.goodsStockManage(goodsArray);
				break;

			case "2":
				MoneyManage.CashierLogin(); // 收银员登陆
				MoneyManage.moneyManage(goodsArray, billArray,vipArray);
				break;
			case "3":
				VipManage.adminLogin(); // 会员登陆
				VipManage.vipManage(vipArray);
				break;
			case"4":
				Festivalscost fe=new Festivalscost();
        		fe.festivalscost();
				break;
			case "5":
				System.out.println("谢谢使用，已退出系统");
				// break;
				System.exit(0);// JVM退出
			}
		}
	}
}
```

```java
package supermarket2;

/**
 * 会员类
 */
public class Vip {

    private String vid; // vip编号
    private String vipFlag; // vip 标记
    private String vipName; // vip名字
    private String vipMoney; // vip余额
    private int vipIntegral; // vip积分

    public String getVid() {
        return vid;
    }

    public void setVid(String vid) {
        this.vid = vid;
    }

    public String getVipFlag() {
        return vipFlag;
    }

    public void setVipFlag(String vipFlag) {
        this.vipFlag = vipFlag;
    }

    public String getVipName() {
        return vipName;
    }

    public void setVipName(String vipName) {
        this.vipName = vipName;
    }

    public String getVipMoney() {
        return vipMoney;
    }

    public void setVipMoney(String vipMoney) {
        this.vipMoney = vipMoney;
    }

    public int getVipIntegral() {
        return vipIntegral;
    }

    public void setVipIntegral(int vipIntegral) {
        this.vipIntegral = vipIntegral;
    }

    @Override
    public String toString() {
        return "Vip{" +
                "vid='" + vid + '\'' +
                ", vipFlag='" + vipFlag + '\'' +
                ", vipName='" + vipName + '\'' +
                ", vipMoney='" + vipMoney + '\'' +
                ", vipIntegral=" + vipIntegral +
                '}';
    }
}
```

```java
package supermarket2;

import java.util.ArrayList;
import java.util.Scanner;

public class VipManage {

	// 会员库存管理
	static void vipManage(ArrayList<Vip> vipArray) {

		while (true) {
			// 用输出语句完主界面的编写
			System.out.println("---------欢迎进入会员管理系统---------");
			System.out.println("1. 查看会员");
			System.out.println("2. 新增会员");
			System.out.println("3. 修改会员");
			System.out.println("4. 删除会员");
			System.out.println("5. 返回上一级菜单");
			System.out.println("请输入你的选择");
			// 用Scanner实现键盘录入数据
			Scanner input = new Scanner(System.in);
			String line = input.nextLine();
			// 用switch语句完成操作的选择
			switch (line) {

			case "1":
				searchVip(vipArray);
				break;

			case "2":
				addVip(vipArray);
				break;

			case "3":
				updateVip(vipArray);
				break;

			case "4":
				deleteVip(vipArray);
				break;

			case "5":
				ShopMenu.manageMenu(); // 返回到主菜单
			}
		}

	}

	// 查询会员
	public static void searchVip(ArrayList<Vip> vipArray) {

		// 如果会员集合为空
		if (vipArray.isEmpty()) {
			System.out.println("暂无会员, 请先添加会员!");
			vipManage(vipArray);
		}

		// 展示会员
		showVip(vipArray);
	}

	// 展示会员
	public static void showVip(ArrayList<Vip> vipArray) {

		// 显示表头信息
		System.out.println("会员编号\t\t会员名称\t会员余额\t会员积分");

		// 将集合中数据取出按照对应格式显示会员信息
		for (int i = 0; i < vipArray.size(); i++) {
			Vip v = vipArray.get(i);
			System.out.println(v.getVid() + "\t" + v.getVipName() + "\t" + v.getVipMoney() + "\t\t" + v.getVipIntegral());
		}
	}

	// 新增会员
	private static void addVip(ArrayList<Vip> vipArray) {

		// 键盘录入会员对象所需要的数据，显示提示信息，提示要输入何种信息
		Scanner input = new Scanner(System.in);

		// 为了vid在while循环外面被访问到，我们就把他定义在了循环外；
		String vid;

		// 为了让程序回到这里，我们使用循环实现
		while (true) {
			System.out.println("请输入会员编号(建议手机号)");
			vid = input.nextLine();
			boolean flag = isUsed(vipArray, vid);
			if (flag) {
				System.out.println("你输入的会员编号已经被使用，请重新输入!");
			} else {
				break;
			}
		}

		System.out.println("请输入会员名称");
		String vipName = input.nextLine();
		System.out.println("请输入会员余额");
		String vipMoney = input.nextLine();
		System.out.println("请输入会员积分");
		int vipIntegral = input.nextInt();
		// 创建会员对象，把键盘录入的数据赋值给会员对象的成员变量
				Vip v = new Vip();
				v.setVid(vid);
				v.setVipName(vipName);
				v.setVipMoney(vipMoney);
				v.setVipIntegral(vipIntegral);
				// 把会员对象添加到集合中
				vipArray.add(v);
				System.out.println("添加会员成功");
			}

			// 修改会员
			private static void updateVip(ArrayList<Vip> vipArray) {
				// 键盘录入要修改的会员编号，显示提示信息
				Scanner input = new Scanner(System.in);

				System.out.println("请输入你要修改的会员编号");
				String vid = input.nextLine();
				int flag = -1;
				flag = getFlag(vipArray, vid); // 获取会员编号的索引
				if (flag == -1) {

					System.out.println("该信息不存在，无法修改，请重新输入！");
					return;

				} else {

					// 键盘录入要修改的会员信息
					System.out.println("请输入会员的新名称：");
					String vipName = input.nextLine();
					System.out.println("请输入会员的新会员余额：");
					String vipMoney = input.nextLine();
					System.out.println("请输入会员的新积分：");
					int vipIntegral = input.nextInt();

					// 创建会员对象
					Vip v = new Vip();
					v.setVid(vid);
					v.setVipName(vipName);
					v.setVipMoney(vipMoney);
					v.setVipIntegral(vipIntegral);

					// 根据上面的索引值修改对应的会员信息
					vipArray.set(flag, v);

				}

				// 给出修改成功提示
				System.out.println("修改会员信息成功");
			}

			// 删除会员
			private static void deleteVip(ArrayList<Vip> vipArray) {
				// 键盘录入要删除的会员编号，显示提示信息。
				Scanner input = new Scanner(System.in);

				System.out.println("请输入你要删除的会员编号：");
				String vid = input.nextLine();
				// 再删除/修改会员操作前，对会员是否存在进行判断
				// 如果不存在，显示提示信息
				// 如在存在，进行遍历集合操作将对应会员对象从集合中删除
				int index = -1;
				index = getFlag(vipArray, vid); // 获得索引
				if (index == -1) {
					System.out.println("该会员信息不存在，请重新输入");
				} else {
					vipArray.remove(index);
					// 给出删除成功提示
					System.out.println("删除会员成功");
				}

			}
			// 管理员登录
			public static void adminLogin() {

				Scanner scan = new Scanner(System.in);
				Scanner reader = new Scanner(System.in);
				String username = null, password = null;
				String username1 = "alnecmy";
				String password1 = "247246";
				boolean flag = true;
				do {
					System.out.println("请输入用户名(alnecmy)：");
					username = reader.next();
					System.out.println("请输入密码：");
					password = reader.next();
					if (username.equals(username1) && password.equals(password1)) {
						System.out.println("登入成功!");
						flag = false;
					} else {
						System.out.println("用户名或密码输入错误，请重新输入:");
					}

				} while (flag);
			}

			// 判断会员编号是否被使用
			public static boolean isUsed(ArrayList<Vip> vipArray, String vid) {
				// 如果与集合中的某一个会员编号相同，返回true；如果都不相同，返回false
				boolean flag = false;
				for (int i = 0; i < vipArray.size(); i++) {
					Vip s = vipArray.get(i);
					if (s.getVid().equals(vid)) {
						flag = true;
						break;
					}
				}
				return flag;
			}

			// 返回一个会员编号
			public static int getFlag(ArrayList<Vip> vipArray, String vid) {
				int flag = -1;
				for (int j = 0; j < vipArray.size(); j++) {

					Vip g1 = vipArray.get(j);
					if (g1.getVid().equals(vid)) {

						flag = j;
						break;
					}

				}
				return flag;
			}

		}
```

