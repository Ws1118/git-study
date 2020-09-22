## Collections

### Dog

```java
package Collections;

public class Dog {

	private String name;
	private int age;
	private String strain;

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

	public String getStrain() {
		return strain;
	}

	public void setStrain(String strain) {
		this.strain = strain;
	}

	public Dog(String name, int age, String strain) {
		super();
		this.name = name;
		this.age = age;
		this.strain = strain;
	}

	public String toString() {
		return "名称：" + this.name + "\t年龄：" + this.age + "\t品种：" + this.strain;
	}

}

```

### Dog0

```java
package Collections;

public class Dog0 implements Comparable<Dog0>{
	
		private String name;//作为主人的名字
		private int age;
		private String strain;
		
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
		public String getStrain() {
			return strain;
		}
		public void setStrain(String strain) {
			this.strain = strain;
		}
		public Dog0(String name, int age, String strain) {
			super();
			this.name = name;
			this.age = age;
			this.strain = strain;
		}

		@Override
		public String toString() {
			// TODO Auto-generated method stub
			return "主人："+this.name+"\t\t年龄："+this.age+"\t\t品种："+this.strain;
		}
		
		@Override
		public int hashCode() {
			// TODO Auto-generated method stub
			int prime=31;
			int result=17;
			result=prime*result+(this.name!=null?this.name.hashCode():0);
			result=prime*result+(this.strain!=null?this.strain.hashCode():0);
			
			return result;
		}
		
		@Override
		public boolean equals(Object obj) {
			// TODO Auto-generated method stub
			if(obj instanceof Dog){
				Dog dog=(Dog)obj;
				if(this.name.equals(dog.getName())&&this.strain.equals(dog.getStrain())){
					return true;
				}else{
					return false;
				}
			}else{
				return false;
			}
		}
		@Override
		public int compareTo(Dog0 o) {
			/*这里面使用age来作为TreeSet排序及判断是否是同一对象的依据，
			和上面的equals的判断原则不一样，这种做法不推荐，仅为展示而如此编码*/
			if(this.age<o.getAge()){
				return 3;
			}
			else if(this.age>o.getAge()){
				return -10001;
			}
			else{
			  return 0;
			}
		}
	}
```

### Dog1

```java
package Collections;

public class Dog1 {

	private String name;
	private String telnum;

	public String getName() {
		return name;
	}

	public void setName(String name) {
		this.name = name;
	}

	public String getTelnum() {
		return telnum;
	}

	public void setTelnum(String telnum) {
		this.telnum = telnum;
	}

	public Dog1(String name, String telnum) {
		super();
		this.name = name;
		this.telnum = telnum;
	}

	public String toString() {
		return "名称：" + this.name + "\t主人电话号码：" + this.telnum;
	}

	@Override
	public int hashCode() {
		// TODO Auto-generated method stub
		int prime = 31;
		int result = 17;
		result = prime * result + (this.name != null ? this.name.hashCode() : 0);
		result = prime * result + (this.telnum != null ? this.telnum.hashCode() : 0);

		return result;
	}

	public boolean equals(Object obj) {
		if (obj instanceof Dog1) {
			Dog1 dog = (Dog1) obj;
			if (this.getName().equals(dog.name)) {
				return true;
			} else {
				return false;
			}
		} else {
			return false;
		}
	}
}
```

### HashSetpractise

```java
package Collections;

import java.util.HashSet;
import java.util.Iterator;
import java.util.Set;

public class HashSetpractise {

	public static void main(String[] args) {
		// TODO Auto-generated method stub
		// TODO Auto-generated method stub
		Set<Dog1> set = new HashSet<Dog1>();
		set.add(new Dog1("zhangsan", "123456"));
		Dog1 dog = new Dog1("lisi", "234567");
		set.add(dog);
		set.add(new Dog1("wanger", "345678"));
		set.add(new Dog1("zhaoliu", "456789"));

		Iterator<Dog1> iterator = set.iterator();
		while (iterator.hasNext()) {
			System.out.println(iterator.next());
		}
	}
}
```

### LinkedListDemo

```java
package Collections;

import java.util.LinkedList;
import java.util.List;

public class LinkedListDemo {

	public static void main(String[] args) {
		List<Dog> doglist = new LinkedList<>();

		Dog dog1 = new Dog("ww", 5, "京巴");
		Dog dog2 = new Dog("ahuang", 7, "金毛");
		Dog dogfeifei = new Dog("feifei", 2, "拉布拉多");

		doglist.add(dog1);
		doglist.add(dog2);
		doglist.add(dogfeifei);

		for (int i = 0; i < doglist.size(); i++) {
			System.out.println(doglist.get(i));
		}
		if (doglist.contains(dogfeifei)) {
			doglist.remove(dogfeifei);
			System.out.println("feifei狗已经在list中了，我已经将其删掉");
		} else {
			System.out.println("feifei狗已经不在list中了");
		}
		LinkedList<Dog> lindoglist = (LinkedList<Dog>) doglist;
		// lindoglist.removeFirst();
		// lindoglist.removeLast();
		System.out.println(doglist.size());
		for (int i = 0; i < doglist.size(); i++) {
			System.out.println(doglist.get(i));
		}
		System.out.println(lindoglist.getLast());
	}

}
```

### ListIteratorDog

```java
package Collections;

import java.util.ArrayList;
import java.util.Iterator;
import java.util.List;

public class ListIteratorDog {
	public static void main(String[] args) {
		List<Dog> doglist = new ArrayList<>();

		Dog dog1 = new Dog("ww", 5, "京巴");
		Dog dog2 = new Dog("ahuang", 7, "金毛");
		Dog dogfeifei = new Dog("fei", 2, "拉布拉多");

		doglist.add(dog1);
		doglist.add(dog2);
		doglist.add(dogfeifei);
		doglist.add(new Dog("xiao", 3, "雪纳瑞"));
		// 遍历的第二种方式，推荐，适用于所有collection的集合类
		System.out.println("------Iteration遍历collection------");
		Iterator<Dog> iterator = doglist.iterator();

		while (iterator.hasNext()) {
			Dog dogtemp = iterator.next();
			System.out.println(dogtemp);
		}
		// 遍历的第三种方式
		System.out.println("------增强for循环遍历list------");
		for(Dog dog:doglist) {
			System.out.println(dog);
		}
	}
}
```

### ListPenguin

```java
package Collections;

import java.util.ArrayList;
import java.util.Iterator;
import java.util.List;

public class ListPenguin {

	public static void main(String[] args) {
		List<Penguin> penguinlist = new ArrayList<>();
		Penguin penguin1 = new Penguin("欧欧", "Q仔");
		Penguin penguin2 = new Penguin("亚亚", "Q妹");
		Penguin penguin3 = new Penguin("菲菲", "Q妹");
		Penguin penguin4 = new Penguin("美美", "Q妹");

		penguinlist.add(penguin1);
		penguinlist.add(penguin2);
		penguinlist.add(penguin3);
		penguinlist.add(penguin4);
		System.out.println("共计有4只企鹅。\n分别是：");

		Iterator<Penguin> iterator = penguinlist.iterator();

		while (iterator.hasNext()) {
			Penguin penguintemp = iterator.next();
			System.out.println(penguintemp);
		}

		System.out.println("删除之后还有2只企鹅。\n分别是：");

		if (penguinlist.contains(penguin3)) {
			penguinlist.remove(penguin3);
		}
		if (penguinlist.contains(penguin4)) {
			penguinlist.remove(penguin4);
		}
		for (int i = 0; i < penguinlist.size(); i++) {
			System.out.println(penguinlist.get(i));
		}

	}

}
```

### ListSimpleDog

```java
package Collections;

import java.util.List;
import java.util.ArrayList;

public class ListSimpleDog {
	public static void main(String[] args) {
		/*
		 * List<String> strlist = new ArrayList<String>();
		 * 
		 * String abc = new String("abc");
		 * 
		 * strlist.add(abc); strlist.add("def"); strlist.add(2, "uvw");
		 * strlist.add("xyz");
		 * 
		 * for (int i = 0; i < strlist.size(); i++) {
		 * System.out.println(strlist.get(i)); }
		 * 
		 * // strlist.remove(1); strlist.remove(abc); // strlist.clear();
		 * System.out.println("----------"); for (int i = 0; i < strlist.size(); i++) {
		 * System.out.println(strlist.get(i)); }
		 */
		List<Dog> doglist = new ArrayList<>();

		Dog dog1 = new Dog("ww", 5, "京巴");
		Dog dog2 = new Dog("ahuang", 7, "金毛");
		Dog dogfeifei = new Dog("feifei", 2, "拉布拉多");

		doglist.add(dog1);
		doglist.add(dog2);
		doglist.add(dogfeifei);
		doglist.add(dog1);

		for (int i = 0; i < doglist.size(); i++) {
			System.out.println(doglist.get(i));
		}
		if (doglist.contains(dogfeifei)) {
			doglist.remove(dogfeifei);
			System.out.println("feifei狗已经在list中了，我已经将其删掉");
		} else {
			System.out.println("feifei狗已经不在list中了");
		}
		doglist.remove(0);

		System.out.println(doglist.size());
		for (int i = 0; i < doglist.size(); i++) {
			System.out.println(doglist.get(i));
		}
	}
}
```

### MapHashMapDemo

```java
package Collections;
	import java.util.HashMap;
	import java.util.Iterator;
	import java.util.Map;
	import java.util.Set;

	public class MapHashMapDemo {

		public static void main(String[] args) {
			// TODO Auto-generated method stub
			Map<Dog,String> map = new HashMap<Dog,String>();
			map.put(new Dog("zhangsan", 4, "金毛"),"zhangahuang");
			map.put(new Dog("lisi", 4, "拉布拉多"),"lilabu");
			map.put(new Dog("wanger", 4, "京巴"),"wangjingba");

			/*		System.out.println(map);
			System.out.println(map.size());*/
			//hashmap的key对象相等的原则同hashset
			map.put(new Dog("wanger", 5, "土狗"),"wangtugou");

			
			/*
			 * 第一种遍历，使用entry条目set来遍历，同时使用iterator
			 */
			
			System.out.println("---------第一种遍历方法---------------------");
			Set<Map.Entry<Dog, String>> entries = map.entrySet();
			
			Iterator<Map.Entry<Dog, String>> iterator=entries.iterator();
			
			while (iterator.hasNext()) {
				Map.Entry<Dog, String> entry=iterator.next();
				System.out.println("key=["+entry.getKey()+"],value=["+entry.getValue()+"]");
			}
			
			/*
			 * 
			 */
			System.out.println("---------第二种遍历方法，是第一种的延申---------------------");
			for (Map.Entry<Dog, String> entry:entries) {
				
				System.out.println("key=["+entry.getKey()+"],value=["+entry.getValue()+"]");
				
			}
			
			System.out.println("---------第三种遍历方法,使用增强for循环遍历keySet读取key，然后联合Map的get读取value--------------------------------");
			
			Set<Dog> dogset=map.keySet();
			
			for (Dog dog:dogset) {
				
				System.out.println("key=["+dog+"],value=["+map.get(dog)+"]");
				
			}
			
			System.out.println("---------第四种遍历方法,使用iterator遍历keySet读取key，然后联合Map的get读取value--------------------------------");
			Iterator<Dog> iterator2= dogset.iterator();
			
			while (iterator2.hasNext()) {
				Dog dog2 = iterator2.next();
				System.out.println("key=["+dog2+"],value=["+map.get(dog2)+"]");
			}
			
		}
	}
```

### MapHashMapSimpleDemo

```java
package Collections;

	import java.util.HashMap;
	import java.util.Map;
	import java.util.TreeMap;

	public class MapHashMapSimpleDemo {

		public static void main(String[] args) {
			// TODO Auto-generated method stub
	        Map<String,String> map=new HashMap<>();
	        map.put("CN", "中华人民共和国");
	        map.put("US", "美利坚合众国");
	        map.put("UK", "大不列颠及北爱尔兰联合王国");
	        map.put("FR", "法兰西共和国");
	        
	        System.out.println(map.size());
	        
	        System.out.println(map.get("UK"));
	        
	        map.remove("FR");
	        System.out.println("FR还存在吗？"+map.containsKey("FR"));
	        
	        System.out.println(map.keySet());
	        System.out.println(map.values());
	        System.out.println(map);
	        
		}

	}
```

### MapHashStudent

```java
package Collections;

public class MapHashStudent {
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

	public MapHashStudent(String name, int age, String sex) {
		super();
		this.name = name;
		this.age = age;
		this.sex = sex;
	}

	public String toString() {
		return "Student{" + "name=" + name + "/" + ",age=" + age + ",sex=" + sex + "/" + "}";
	}
}
```

### MapHashStudentTest

```java
package Collections;

import java.util.HashMap;
import java.util.Iterator;
import java.util.Map;
import java.util.Set;

public class MapHashStudentTest {

	public static void main(String[] args) {
		// TODO Auto-generated method stub
		Map<String, MapHashStudent> map = new HashMap<>();

		map.put("1234561", new MapHashStudent("小明", 11, "男"));
		map.put("1234562", new MapHashStudent("小芳", 12, "女"));
		map.put("1234563", new MapHashStudent("小军", 13, "男"));

		MapHashStudent s1 = map.get("1234561");
		if (s1 == null) {
			System.out.println("无此学生信息");
		} else {
			System.out.println(map.get("1234561"));
		}
		MapHashStudent s2 = map.get("1234562");
		if (s2 == null) {
			System.out.println("无此学生信息");
		} else {
			System.out.println(map.get("1234562"));
		}
		MapHashStudent s3 = map.get("1234563");
		if (s3 == null) {
			System.out.println("无此学生信息");
		} else {
			System.out.println(map.get("1234563"));
		}
		Set<Map.Entry<String, MapHashStudent>> entries = map.entrySet();

		Iterator<Map.Entry<String, MapHashStudent>> iterator = entries.iterator();

		while (iterator.hasNext()) {

			Map.Entry<String, MapHashStudent> entry = iterator.next();

			System.out.println("key=[" + entry.getKey() + "],value=[" + entry.getValue() + "]");

		}
	}

}
```

### MapLinkedHashMapDemo

```java
package Collections;

	import java.util.Iterator;
	import java.util.LinkedHashMap;
	import java.util.Map;
	import java.util.Set;

	public class MapLinkedHashMapDemo {

		public static void main(String[] args) {
			// TODO Auto-generated method stub
			Map<Dog,String> map = new LinkedHashMap<Dog,String>();
			map.put(new Dog("zhangsan", 4, "金毛"),"zhangahuang");
			map.put(new Dog("lisi", 4, "拉布拉多"),"lilabu");
			map.put(new Dog("wanger", 4, "京巴"),"wangjingba");

			/*		System.out.println(map);
			System.out.println(map.size());*/
			//hashmap的key对象相等的原则同hashset
			map.put(new Dog("wanger", 5, "土狗"),"wangtugou");

			
			/*
			 * 第一种遍历，使用entry条目set来遍历，同时使用iterator
			 */
			
			System.out.println("---------第一种遍历方法---------------------");
			Set<Map.Entry<Dog, String>> entries = map.entrySet();
			
			Iterator<Map.Entry<Dog, String>> iterator=entries.iterator();
			
			while (iterator.hasNext()) {
				Map.Entry<Dog, String> entry=iterator.next();
				System.out.println("key=["+entry.getKey()+"],value=["+entry.getValue()+"]");
			}
			
			/*
			 * 
			 */
			System.out.println("---------第二种遍历方法，是第一种的延申---------------------");
			for (Map.Entry<Dog, String> entry:entries) {
				
				System.out.println("key=["+entry.getKey()+"],value=["+entry.getValue()+"]");
				
			}
			
			System.out.println("---------第三种遍历方法,使用增强for循环遍历keySet读取key，然后联合Map的get读取value--------------------------------");
			
			Set<Dog> dogset=map.keySet();
			
			for (Dog dog:dogset) {
				
				System.out.println("key=["+dog+"],value=["+map.get(dog)+"]");
				
			}
			
			System.out.println("---------第四种遍历方法,使用iterator遍历keySet读取key，然后联合Map的get读取value--------------------------------");
			Iterator<Dog> iterator2= dogset.iterator();
			
			while (iterator2.hasNext()) {
				Dog dog2 = iterator2.next();
				System.out.println("key=["+dog2+"],value=["+map.get(dog2)+"]");
			}
			
		}
	}
```

### MapProperties

```j
package Collections;

import java.io.File;
import java.io.FileInputStream;
import java.io.FileNotFoundException;
import java.io.FileOutputStream;
import java.io.IOException;
import java.util.Properties;

public class MapProperties {

	public static void main(String[] args) throws FileNotFoundException, IOException {
		// TODO Auto-generated method stub
		Properties properties = new Properties();
		properties.load(new FileInputStream(new File("F:/proterties.txt")));

		String id = properties.getProperty("id");
		System.out.println(id);
		String grade = properties.getProperty("grade");
		System.out.println(grade);

		properties.setProperty("id", "1902343235");
		properties.setProperty("grade", "80");

		properties.list(System.out);

	}

}
```

### MapPropertiesDemo

```java
package Collections;

import java.io.File;
import java.io.FileInputStream;
import java.io.FileNotFoundException;
import java.io.FileOutputStream;
import java.io.IOException;
import java.util.Properties;

public class MapPropertiesDemo {

	public static void main(String[] args) throws FileNotFoundException, IOException {
		// TODO Auto-generated method stub
		Properties properties = new Properties();
		properties.load(new FileInputStream(new File("d:/conf.properties")));

		String user = properties.getProperty("user");
		System.out.println(user);
		String password = properties.getProperty("password");
		System.out.println(password);

		properties.setProperty("user", "wangermazi");
		properties.setProperty("alias", "wanger");

		properties.list(System.out);

		properties.store(new FileOutputStream(new File("d:/conf.txt")), "lzk modified");

	}
}
```

### MapStudent

```java
package Collections;

public class MapStudent {

	private String id;
	private String name;

	public String getId() {
		return id;
	}

	public void setId(String id) {
		this.id = id;
	}

	public String getName() {
		return name;
	}

	public void setName(String name) {
		this.name = name;
	}

	public MapStudent(String id, String name) {
		super();
		this.id = id;
		this.name = name;
	}

	public String toString() {
		return "学号：" + this.getId() + "\t姓名：" + this.getName();
	}

}
```

### MapStudentTest

```java
package Collections;

import java.util.List;
import java.util.ArrayList;
import java.util.HashMap;
import java.util.Iterator;
import java.util.Map;
import java.util.Set;

public class MapStudentTest {

	public static void main(String[] args) {
		// TODO Auto-generated method stub
		Map<MapStudent, String> CommonClass = new HashMap<MapStudent, String>();
		CommonClass.put(new MapStudent("1234561", "小明"), "普通班");
		CommonClass.put(new MapStudent("1234562", "小红"), "普通班");

		Map<MapStudent, String> IntensiveClass = new HashMap<MapStudent, String>();
		IntensiveClass.put(new MapStudent("1234563", "小军"), "强化班");
		IntensiveClass.put(new MapStudent("1234564", "小雪"), "强化班");

		System.out.println("普通班：");
		Set<Map.Entry<MapStudent, String>> entries = CommonClass.entrySet();
		Iterator<Map.Entry<MapStudent, String>> iterator = entries.iterator();
		while (iterator.hasNext()) {
			Map.Entry<MapStudent, String> entry = iterator.next();
			System.out.println(entry);
		}

		System.out.println("\n强化班：");
		Set<Map.Entry<MapStudent, String>> entries2 = IntensiveClass.entrySet();
		Iterator<Map.Entry<MapStudent, String>> iterator2 = entries2.iterator();
		while (iterator2.hasNext()) {
			Map.Entry<MapStudent, String> entry2 = iterator2.next();
			System.out.println(entry2);
		}
	}
}
```

### MapTreeMapCustomSeqDemo

```java
package Collections;

	import java.util.Comparator;
	import java.util.HashMap;
	import java.util.Iterator;
	import java.util.Map;
	import java.util.Set;
	import java.util.TreeMap;

	public class MapTreeMapCustomSeqDemo {

		public static void main(String[] args) {
			// TODO Auto-generated method stub
			Map<Dog,String> map = new TreeMap<Dog,String>(new Comparator<Dog>(){
				@Override
				public int compare(Dog o1, Dog o2) {
					// TODO Auto-generated method stub
					return o1.getName().compareTo(o2.getName());
				}
			});
			map.put(new Dog("zhangsan", 4, "金毛"),"zhangahuang");
			map.put(new Dog("lisi", 4, "拉布拉多"),"lilabu");
			map.put(new Dog("wanger", 5, "京巴"),"wangjingba");

			/*		System.out.println(map);
			System.out.println(map.size());*/
			//hashmap的key对象相等的原则同hashset
			map.put(new Dog("wanger", 6, "土狗"),"wangtugou");

			
			/*
			 * 第一种遍历，使用entry条目set来遍历，同时使用iterator
			 */
			
			System.out.println("---------第一种遍历方法---------------------");
			Set<Map.Entry<Dog, String>> entries = map.entrySet();
			
			Iterator<Map.Entry<Dog, String>> iterator=entries.iterator();
			
			while (iterator.hasNext()) {
				Map.Entry<Dog, String> entry=iterator.next();
				System.out.println("key=["+entry.getKey()+"],value=["+entry.getValue()+"]");
			}
		}
	}
```

### MapTreeMapDemo

```java
package Collections;

	import java.util.Iterator;
	import java.util.Map;
	import java.util.Set;
	import java.util.TreeMap;

	public class MapTreeMapDemo {

		public static void main(String[] args) {
			// TODO Auto-generated method stub
			Map<Dog,String> map = new TreeMap<Dog,String>();
			map.put(new Dog("zhangsan", 4, "金毛"),"zhangahuang");
			map.put(new Dog("lisi", 4, "拉布拉多"),"lilabu");
			map.put(new Dog("wanger", 5, "京巴"),"wangjingba");

			/*		System.out.println(map);
			System.out.println(map.size());*/
			//hashmap的key对象相等的原则同hashset
			map.put(new Dog("wanger", 6, "土狗"),"wangtugou");

			
			/*
			 * 第一种遍历，使用entry条目set来遍历，同时使用iterator
			 */
			
			System.out.println("---------第一种遍历方法---------------------");
			Set<Map.Entry<Dog, String>> entries = map.entrySet();
			
			Iterator<Map.Entry<Dog, String>> iterator=entries.iterator();
			
			while (iterator.hasNext()) {
				Map.Entry<Dog, String> entry=iterator.next();
				System.out.println("key=["+entry.getKey()+"],value=["+entry.getValue()+"]");
			}
			
	/*		
			 * 
			 
			System.out.println("---------第二种遍历方法，是第一种的延申---------------------");
			for (Map.Entry<Dog, String> entry:entries) {
				
				System.out.println("key=["+entry.getKey()+"],value=["+entry.getValue()+"]");
				
			}
			
			System.out.println("---------第三种遍历方法,使用增强for循环遍历keySet读取key，然后联合Map的get读取value--------------------------------");
			
			Set<Dog> dogset=map.keySet();
			
			for (Dog dog:dogset) {
				
				System.out.println("key=["+dog+"],value=["+map.get(dog)+"]");
				
			}
			
			System.out.println("---------第四种遍历方法,使用iterator遍历keySet读取key，然后联合Map的get读取value--------------------------------");
			Iterator<Dog> iterator2= dogset.iterator();
			
			while (iterator2.hasNext()) {
				Dog dog2 = iterator2.next();
				System.out.println("key=["+dog2+"],value=["+map.get(dog2)+"]");
			}
			*/
		}
	}
```

### Penguin

```java
package Collections;

public class Penguin {
	private String name;
	private String sex;

	public String getName() {
		return name;
	}

	public void setName(String name) {
		this.name = name;
	}

	public String getSex() {
		return sex;
	}

	public void setSex(String sex) {
		this.sex = sex;
	}

	public Penguin(String name, String sex) {
		super();
		this.name = name;
		this.sex = sex;
	}

	public String toString() {
		return "姓名：" + this.name + "\t性别：" + this.sex;
	}

	public boolean equals(Object obj) {
		if (obj instanceof Penguin) {
			Penguin penguin = (Penguin) obj;
			if (this.getName().equals(penguin.name)) {
				return true;
			} else {
				return false;
			}
		} else {
			return false;
		}
	}
}
```

### Queue< T >

```java
package Collections;

import java.util.LinkedList;

public class Queue<T> {

	private LinkedList<T> list = new LinkedList<T>();

	public void In(T t) {
		this.list.addLast(t);
	}

	public T Out() {
		return this.list.removeFirst();
	}

	public boolean isEmpty() {

		if (this.list.size() == 0) {
			return true;
		} else {
			return false;
		}
	}

	@Override
	public String toString() {
		// TODO Auto-generated method stub
		String str = "";
		System.out.println("当前队列为：\n");
		for (T t : list) {
			str += "名字：" + t.toString() + "\n";
		}
		return str;
	}

	public static void main(String[] args) {
		// TODO Auto-generated method stub
		Queue<Dog> dogque = new Queue<>();
		dogque.In(new Dog("往往", 2, "京巴"));
		dogque.In(new Dog("阿黄", 5, "金毛"));

		System.out.println(dogque);
		System.out.println("队首为：" + dogque.Out() + "已被服务完，从队列中删除了");
		System.out.println("--------------out一个后------------------");
		System.out.println(dogque);

		dogque.In(new Dog("小怪", 3, "拉布拉多"));
		System.out.println("---------in一个以后----------------------");
		System.out.println(dogque);

	}

}
```

### Queue0< T >

```java
package Collections;

import java.util.LinkedList;

public class Queue0<T> {

		private LinkedList<T> list = new LinkedList<>();

		public void In(T t) {
			this.list.addLast(t);
		}

		public T Out() {
			return this.list.removeLast();
		}
		
		public boolean isEmpty() {

			if (this.list.size() == 0) {
				return true;
			} else {
				return false;
			}
		}

		@Override
		public String toString() {
			// TODO Auto-generated method stub
			String str = "";
			System.out.println("当前队列为：\n");
			for (T t : list) {
				str += "名字：" + t.toString() + "\n";
			}
			return str;
		}

		public static void main(String[] args) {
			// TODO Auto-generated method stub
			Queue<Dog> dogque = new Queue<>();
			dogque.In(new Dog("往往", 2, "京巴"));
			dogque.In(new Dog("阿黄", 5, "金毛"));
            System.out.println(dogque);

			dogque.In(new Dog("小怪", 3, "拉布拉多"));
			System.out.println("---------in一个以后----------------------");
			System.out.println(dogque);
            
			System.out.println("队尾为：" + dogque.Out());
			System.out.println("--------------out一个后------------------");
			System.out.println(dogque);

		}

	}
```

### Queue1< T >

```java
package Collections;

import java.util.LinkedList;

public class Queue1<T> {

	private LinkedList<T> list = new LinkedList<>();

	public void In(T t) {
		this.list.addLast(t);
	}

	public T Out() {
         return this.list.removeLast();
	}

	public boolean isEmpty() {
	if (this.list.size() == 0) {
	return true ;
} else {
	return false;
	}
	}
	public String toString() {
	
	String string = "" ;
	
	for(T t:list){
	string += t. toString() + "\n";
	}
	return string;
	
}

	public static void main(String[] args) {
		// TODO Auto- generated method stub
		Queue1<Dog> dogqu = new Queue1<>();
		dogqu.In(new Dog("方方", 3, "柯基"));
		dogqu.In(new Dog("沁沁", 3, "黄毛"));
		System.out.println("当前入电梯的狗狗: \n" + dogqu);
		dogqu.In(new Dog("周舟", 4, "哈士奇"));
		System.out.println("增加后，当前入电梯的狗狗: \n" + dogqu);
		System.out.println("栈尾为: \n" + dogqu.Out() + "已经 下电梯，从栈中删除了");
		System.out.println("现在电梯中剩下的狗狗为; \n" + dogqu);

	}
}
```

### SetHashSetDemo

```java
package Collections;

import java.util.HashSet;
import java.util.Iterator;
import java.util.Set;

public class SetHashSetDemo {

	public static void main(String[] args) {
		// TODO Auto-generated method stub
        Set<Dog> set=new HashSet<Dog>();
        set.add(new Dog("zhangsan", 4, "金毛"));
        Dog dog=new Dog("lisi", 5, "金毛");      
        set.add(dog);
        set.add(new Dog("wanger", 5, "金毛"));
        set.add(new Dog("zhaoliu", 5, "金毛"));
        
       
        set.add(new Dog("zhangsan", 8, "金毛"));
        //set.add(dog);
        
        Iterator<Dog> iterator=set.iterator();
        while(iterator.hasNext()){
        	System.out.println(iterator.next());
        } 
	}
}
```

### SetLinkedHashSetDemo

```java
package Collections;

	import java.util.Iterator;
	import java.util.LinkedHashSet;
	import java.util.Set;

	public class SetLinkedHashSetDemo {
		public static void main(String[] args) {
			// TODO Auto-generated method stub
	        Set<Dog> set=new LinkedHashSet<Dog>();
	        set.add(new Dog("zhangsan", 4, "金毛"));
	        Dog dog=new Dog("lisi", 5, "金毛");      
	        set.add(dog);
	        set.add(new Dog("wangwu", 5, "金毛"));
	        set.add(new Dog("zhaoliu", 5, "金毛"));
	        set.add(new Dog("zhangsan", 4, "金毛"));  
	       
	        set.add(new Dog("zhangsan", 8, "金毛"));
	        //set.add(dog);
	        
	        Iterator<Dog> iterator=set.iterator();
	        while(iterator.hasNext()){
	        	System.out.println(iterator.next());
	        } 
		}
	}
```

### SetTreesetCustomizedSeqDemo

```java
package Collections;

	import java.util.Iterator;
	import java.util.Set;
	import java.util.TreeSet;

	public class SetTreesetCustomizedSeqDemo {

		public static void main(String[] args) {
			// TODO Auto-generated method stub
			Set<Dog> set = new TreeSet<Dog>();
			set.add(new Dog("zhangsan", 7, "金毛"));
			Dog dog = new Dog("lisi", 5, "金毛");
			set.add(dog);
			/*
			 * 因为Dog中的Comparable实现是仅根据年龄是否一样来判断是否是同一对象，
			 * 所以下面出现了另一个age为5的对象，就不能加到treeset中了。
			 */
			set.add(new Dog("wanger", 5, "金毛"));
			set.add(new Dog("zhangsan", 6, "金毛"));
			// set.add(dog);

			Iterator<Dog> iterator = set.iterator();
			while (iterator.hasNext()) {
				System.out.println(iterator.next());
			}
		}

	}
```

### SetTreesetNaturalSeqDemo

```java
package Collections;

	import java.util.Comparator;
	import java.util.Iterator;
	import java.util.Set;
	import java.util.TreeSet;

	public class SetTreesetNaturalSeqDemo {

		public static void main(String[] args) {
			// TODO Auto-generated method stub
			
	/*		Comparator<Dog> comparator=new Comparator<Dog>(){
				@Override
				public int compare(Dog o1, Dog o2) {
					// TODO Auto-generated method stub
					return o1.getName().compareTo(o2.getName());
				}
			};		
			Set<Dog> set1 = new TreeSet<Dog>(comparator);*/
			
			Set<Dog> set = new TreeSet<Dog>(new Comparator<Dog>(){
				@Override
				public int compare(Dog o1, Dog o2) {
					// TODO Auto-generated method stub
					return o1.getName().compareTo(o2.getName());
				}
			});
			set.add(new Dog("zhangsan", 7, "金毛"));
			Dog dog = new Dog("lisi", 5, "金毛");
			set.add(dog);
			/*
			 * 因为Dog中的Comparable实现是仅根据年龄是否一样来判断是否是同一对象，
			 * 所以下面出现了另一个age为5的对象，就不能加到treeset中了。
			 */
			set.add(new Dog("wanger", 4, "金毛"));
			set.add(new Dog("zhaoliu", 5, "金毛"));
			// set.add(dog);

			Iterator<Dog> iterator = set.iterator();
			while (iterator.hasNext()) {
				System.out.println(iterator.next());
			}
		}

	}
```

