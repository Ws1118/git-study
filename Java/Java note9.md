## IODemo

### Demo01_File

```java
package IODemo;

import java.io.File;
import java.io.IOException;

import org.junit.Test;

public class Demo01_File {
	
	@Test  //JUnit包，方便Java代码测试。
	public void TestFile() {
		//System.out.println("JUnit的第一个测试");
		File file1=new File("D:\\Case\\hello.txt");
		if(file1.exists()){
			System.out.println("文件存在，我就将其删掉");
			file1.delete();
		}
		
		if(!file1.exists()){
			try {
				System.out.println("文件不存在，我就新创建一个");
				file1.createNewFile();
				System.out.println("绝对路径为："+file1.getAbsolutePath());
				System.out.println("文件名为："+file1.getName());
				System.out.println("父路径为："+file1.getParent());
				
				file1.renameTo(new File("D:\\Case\\hello2.txt"));
	
			} catch (IOException e) {
				// TODO Auto-generated catch block
				e.printStackTrace();
			}
		}
	} 
	
	@Test  
	public void TestDirectory() {
		//System.out.println("JUnit的第一个测试");
		File dir1=new File("D:\\Case\\io2");
		if(dir1.exists()){
			System.out.println("目录存在，我就将其删掉");
			dir1.delete();
		}
		
		if(!dir1.exists()){
			System.out.println("目录不存在，我就新创建一个");
			dir1.mkdir();
		}  
		
		File dir2=new File("D:\\Case\\io10\\io3\\io4");
		if(dir2.exists()){
			System.out.println("多级目录存在");
		}
		
		if(!dir2.exists()){
			System.out.println("多级目录不存在，我就新创建整个目录结构");
			dir2.mkdirs();
		}  
	} 

}
```

### Demo02_FileInputOutputStream

```java
package IODemo;

import java.io.File;
import java.io.FileInputStream;
import java.io.FileNotFoundException;
import java.io.FileOutputStream;
import java.io.FileReader;
import java.io.IOException;
import java.io.UnsupportedEncodingException;
import java.util.Arrays;

import org.junit.Test;

public class Demo02_FileInputOutputStream {

	@Test
	public void FileInputStream() {

		// File file1=new File("d:\\Case\\helloworld3.txt");
		// File file1=new File("d:/Case/helloworld3.txt");
		File file1 = new File("d:" + File.separator + "Case" + File.separator
				+ "file1.txt");

		/*
		 * 创建一个文件输入字节流
		 */
		FileInputStream fis = null;
		try {
			fis = new FileInputStream(file1);
		} catch (FileNotFoundException e) {
			// TODO Auto-generated catch block
			e.printStackTrace();
		}

		/*
		 * 开始读文件
		 */
		byte[] bytes = new byte[6];
		int len = -1;

		/*
		 * do{ try { end=fis.read(bytes); System.out.print("本次读出"+end+"个字节:");
		 * if(end==-1){ break; } System.out.println(new String(bytes,0,end));
		 * 
		 * } catch (IOException e) { // TODO Auto-generated catch block
		 * e.printStackTrace(); } }while(end!=-1);
		 */
		try {
			while ((len = fis.read(bytes)) != -1) {
				System.out.print("本次读出" + len + "个字节:");
				for (int i = 0; i < len; i++) {
					System.out.print(bytes[i] + " ");
				}
				System.out.println("");
				
				// System.out.println(new String(bytes,0,end));
			}
		} catch (IOException e1) {
			// TODO Auto-generated catch block
			e1.printStackTrace();
		}

		// 将对应的流关闭
		if (fis != null) {
			try {
				fis.close();
			} catch (IOException e) {
				// TODO Auto-generated catch block
				e.printStackTrace();
			}
		}
	}

	@Test
	public void TestFileOutputStream() {
		File file1 = new File("d:" + File.separator + "Case" + File.separator
				+ "helloworld4.txt");

		if (!file1.exists()) {
			try {
				file1.createNewFile();
			} catch (IOException e) {
				// TODO Auto-generated catch block
				e.printStackTrace();
			}
		}

		/*
		 * 生成输出流
		 */
		FileOutputStream fos = null;
		try {
			fos = new FileOutputStream(file1);
		} catch (FileNotFoundException e) {
			// TODO Auto-generated catch block
			e.printStackTrace();
		}

		byte[] bytes = null;
		bytes="abcdefghijklmn".getBytes();

		try {
			//fos.write(98);//写的是ASCII为98的字符，也就是‘b’
			fos.write(bytes);
			//fos.write(bytes,5,5);
		} catch (IOException e) {
			// TODO Auto-generated catch block
			e.printStackTrace();
		}

		if (fos != null) {
			try {
				fos.close();
			} catch (IOException e) {
				// TODO Auto-generated catch block
				e.printStackTrace();
			}
		}
	}
	
	@Test
	public void copyByteFile(){
		File file1 = new File("d:\\Case\\mydir\\example.mp4");
		File file2 = new File("d:\\Case\\mydir\\examplecopyed.mp4");
		if(!file2.exists()){
			try {
				file2.createNewFile();
			} catch (IOException e) {
				// TODO Auto-generated catch block
				e.printStackTrace();
			}
		}
		
		/*
		 * 生成两个流
		 */
		FileInputStream fis=null;
		FileOutputStream fos=null;
		
		try {
			fis=new FileInputStream(file1);
			fos=new FileOutputStream(file2);
		} catch (FileNotFoundException e) {
			// TODO Auto-generated catch block
			e.printStackTrace();
		}
		
		/*
		 * 一个流是读，一个是写
		 */
		byte[] bytes=new byte[1024];
		int len=-1;
		try {
			while ((len=fis.read(bytes))!=-1) {
				fos.write(bytes, 0, len);
			}
		} catch (IOException e) {
			// TODO Auto-generated catch block
			e.printStackTrace();
		}
		
		if(fis!=null){
			try {
				fis.close();
			} catch (IOException e) {
				// TODO Auto-generated catch block
				e.printStackTrace();
			}
		}
		if(fos!=null){
			try {
				fos.close();
			} catch (IOException e) {
				// TODO Auto-generated catch block
				e.printStackTrace();
			}
		}
	}
	@Test
	public void print() throws UnsupportedEncodingException{
		byte[] b = "这个数据是中文！可能会出现乱码".getBytes();
		System.out.println(Arrays.toString(b));
		
		byte[] b2=null;
		
		b2 = "这个数据是中文！可能会出现乱码".getBytes("UTF-8");
		System.out.println("-----------------------------------");
		
		System.out.println(Arrays.toString(b2));
		
		//解码：
		
		System.out.println(new String(b));
		
		System.out.println(new String(b, "utf-8"));
		//编码和解码规则不一致 ==》出现乱码问题
		
		System.out.println(new String(b2,"GBK"));//编码和解码规则不一致 ==》出现乱码问题
		
		System.out.println(new String(b2,"utf-8"));//编码和解码规则一致 ==》不会出现乱码问题

	}
}
```

### Demo03_FileReaderWriter

```java
package IODemo;

import java.io.File;
import java.io.FileInputStream;
import java.io.FileNotFoundException;
import java.io.FileOutputStream;
import java.io.FileReader;
import java.io.FileWriter;
import java.io.IOException;
import java.io.UnsupportedEncodingException;
import java.util.Arrays;

import org.junit.Test;

public class Demo03_FileReaderWriter {

	@Test
	public void TestReader() {

		// File file1=new File("d:\\Case\\helloworld3.txt");
		// File file1=new File("d:/Case/helloworld3.txt");
		File file1 = new File("d:" + File.separator + "Case" + File.separator
				+ "helloworld5.txt");

		/*
		 * 创建一个文件输入字符流（和源文件存储时使用的字符编码方式相关），FileReader ISO-XXXX-1编码（和ANSI兼容的）
		 */
		FileReader fr = null;
		try {
			fr = new FileReader(file1);
		} catch (FileNotFoundException e) {
			// TODO Auto-generated catch block
			e.printStackTrace();
		}

		/*
		 * 开始读文件
		 */
		char[] chars = new char[30];
		int len = -1;

	
		try {
			while ((len = fr.read(chars)) != -1) {
				System.out.print("本次读出" + len + "个字符:");
				/*
				 * 如果文件是UTF-8编码的，那么我需要转化：
				 */
				String str=new String(chars);
				byte[] bytes=str.getBytes();
				str=new String(bytes,"UTF-8");
				System.out.println("转化后的汉字序列为"+str);
				
				for (int i = 0; i < len; i++) {
					System.out.print(chars[i] + " ");
				}
				System.out.println("");
				
				// System.out.println(new String(bytes,0,end));
			}
		} catch (IOException e1) {
			// TODO Auto-generated catch block
			e1.printStackTrace();
		}

		// 将对应的流关闭
		if (fr != null) {
			try {
				fr.close();
			} catch (IOException e) {
				// TODO Auto-generated catch block
				e.printStackTrace();
			}
		}
	}

	@Test
	public void TestWriter() {
		File file1 = new File("d:" + File.separator + "Case" + File.separator
				+ "helloworld6.txt");

		if (!file1.exists()) {
			try {
				file1.createNewFile();
			} catch (IOException e) {
				// TODO Auto-generated catch block
				e.printStackTrace();
			}
		}

		/*
		 * 生成输出流
		 */
		FileWriter fw = null;
	
		try {
			fw = new FileWriter(file1);//new FileWriter(file1,true)将内容添加到文件的最后
		} catch (IOException e1) {
				// TODO Auto-generated catch block
		   e1.printStackTrace();
		}
	

		char[] chars = null;
		chars="我是一名学生，名字叫lizhongke".toCharArray();

		try {
	
			fw.write(chars);
			System.out.println("刚才我添加了："+new String(chars));
			
		} catch (IOException e) {
			// TODO Auto-generated catch block
			e.printStackTrace();
		}

		if (fw != null) {
			try {
				fw.close();
			} catch (IOException e) {
				// TODO Auto-generated catch block
				e.printStackTrace();
			}
		}
	}
	
	@Test
	public void copyCharFile(){
		//用字符流去拷贝字节文件（以字节为单位组织的文件）是无法实现拷贝的，它只能处理文本文件。
	/*	File file1 = new File("d:\\Case\\mydir\\example.mp4");
		File file2 = new File("d:\\Case\\mydir\\examplecopyed.mp4");*/
		File file1 = new File("d:\\Case\\file1.txt");
		File file2 = new File("d:\\Case\\file2.txt");
		if(!file2.exists()){
			try {
				file2.createNewFile();
			} catch (IOException e) {
				// TODO Auto-generated catch block
				e.printStackTrace();
			}
		}
		
		/*
		 * 生成两个流
		 */
		FileReader fis=null;
		FileWriter fos=null;
		
		try {
			fis=new FileReader(file1);
			try {
				fos=new FileWriter(file2);
			} catch (IOException e) {
				// TODO Auto-generated catch block
				e.printStackTrace();
			}
		} catch (FileNotFoundException e) {
			// TODO Auto-generated catch block
			e.printStackTrace();
		}
		
		/*
		 * 一个流是读，一个是写
		 */
		char[] chars=new char[128];
		int len=-1;
		try {
			while ((len=fis.read(chars))!=-1) {
				System.out.println(new String(chars));
				fos.write(chars, 0, len);
			}
		} catch (IOException e) {
			// TODO Auto-generated catch block
			e.printStackTrace();
		}
		
		if(fis!=null){
			try {
				fis.close();
			} catch (IOException e) {
				// TODO Auto-generated catch block
				e.printStackTrace();
			}
		}
		if(fos!=null){
			try {
				fos.close();
			} catch (IOException e) {
				// TODO Auto-generated catch block
				e.printStackTrace();
			}
		}
	}
}
```

### Demo04_BufferedFileInputOutputStream

```java
package IODemo;

import java.io.BufferedInputStream;
import java.io.BufferedOutputStream;
import java.io.File;
import java.io.FileInputStream;
import java.io.FileNotFoundException;
import java.io.FileOutputStream;
import java.io.FileReader;
import java.io.IOException;
import java.io.UnsupportedEncodingException;
import java.util.Arrays;

import org.junit.Test;

public class Demo04_BufferedFileInputOutputStream {

	@Test
	public void copyByteFile(){
		
		File file1 = new File("d:\\Case\\mydir\\example2.mp4");
		File file2 = new File("d:\\Case\\mydir\\examplecopyed2.mp4");
		if(!file2.exists()){
			try {
				file2.createNewFile();
			} catch (IOException e) {
				// TODO Auto-generated catch block
				e.printStackTrace();
			}
		}
		
		/*
		 * 生成两个节点流，同时，使用缓冲流包装对应的节点流
		 */
		FileInputStream fis=null;
		FileOutputStream fos=null;

		BufferedInputStream bis=null;
		BufferedOutputStream bos=null;
		
		try {
			fis=new FileInputStream(file1);
			//缓冲流包装节点输入流--文件字节输入流
			bis=new BufferedInputStream(fis);
			
			fos=new FileOutputStream(file2);
			//包装节点输出流--文件字节输出流
			bos=new BufferedOutputStream(fos);
			
		} catch (FileNotFoundException e) {
			// TODO Auto-generated catch block
			e.printStackTrace();
		}
		
		long begin=System.currentTimeMillis();
		
		/*
		 * 一个流是读，一个是写
		 */
		byte[] bytes=new byte[1024];
		int len=-1;
		try {
			while ((len=bis.read(bytes))!=-1) {
				bos.write(bytes, 0, len);
			}
			bos.flush();
		} catch (IOException e) {
			// TODO Auto-generated catch block
			e.printStackTrace();
		}
		
		long end=System.currentTimeMillis();
		System.out.println("拷贝共用时："+(end-begin)+"毫秒");
		
		if(fis!=null){
			try {
				fis.close();
			} catch (IOException e) {
				// TODO Auto-generated catch block
				e.printStackTrace();
			}
		}
		if(fos!=null){
			try {
				fos.close();
			} catch (IOException e) {
				// TODO Auto-generated catch block
				e.printStackTrace();
			}
		}
		
		if(bis!=null){
			try {
				bis.close();
			} catch (IOException e) {
				// TODO Auto-generated catch block
				e.printStackTrace();
			}
		}
		if(bos!=null){
			try {
				bos.close();
			} catch (IOException e) {
				// TODO Auto-generated catch block
				e.printStackTrace();
			}
		}
	}
}
```

### Test01_File

```java
package IODemo;

import java.io.File;
import java.io.IOException;

import org.junit.Test;

public class Test01_File {

	@Test
	public void TestFile() {
		File file1 = new File("D:\\Case\\myDir\\我的青春我做主.txt");

		try {
			System.out.println("文件不存在，我就新创建一个");
			file1.createNewFile();
			System.out.println("绝对路径为：" + file1.getAbsolutePath());
			System.out.println("文件名为：" + file1.getName());
			System.out.println("父路径为：" + file1.getParent());

			file1.renameTo(new File("D:\\Case\\myDir\\我的青春我做主.txt"));

		} catch (IOException e) {
			// TODO Auto-generated catch block
			e.printStackTrace();
		}
		System.out.println("文件存在，我就将其删掉");
		file1.delete();
	}

}
```

### Test03_File

```java
package IODemo;

import java.io.File;
import java.io.FileInputStream;
import java.io.FileNotFoundException;
import java.io.FileOutputStream;
import java.io.FileReader;
import java.io.FileWriter;
import java.io.IOException;
import java.io.UnsupportedEncodingException;
import java.util.Arrays;

import org.junit.Test;

public class Test03_File {

	@Test
	public void TestReader() {

		File file1 = new File(
				"d:" + File.separator + "Case" + File.separator + "myyDir" + File.separator + "我的青春我做主.txt");

		FileReader fr = null;
		try {
			fr = new FileReader(file1);
		} catch (FileNotFoundException e) {
			// TODO Auto-generated catch block
			e.printStackTrace();
		}

		char[] chars = new char[30];
		int len = -1;

		/*
		 * try { while ((len = fr.read(chars)) != -1) { System.out.print("本次读出" + len +
		 * "个字符:");
		 * 
		 * String str=new String(chars); byte[] bytes=str.getBytes(); str=new
		 * String(bytes,"UTF-8"); System.out.println("转化后的汉字序列为"+str);
		 * 
		 * for (int i = 0; i < len; i++) { System.out.print(chars[i] + " "); }
		 * System.out.println("");
		 * 
		 * //System.out.println(new String(bytes,0,end)); } } catch (IOException e1) {
		 * // TODO Auto-generated catch block e1.printStackTrace(); }
		 */

		if (fr != null) {
			try {
				fr.close();
			} catch (IOException e) {
				// TODO Auto-generated catch block
				e.printStackTrace();
			}
		}
	}

	@Test
	public void TestWriter() {
		File file1 = new File(
				"d:" + File.separator + "Case" + File.separator + "myDir" + File.separator + "我的青春我做主2.txt");

		if (!file1.exists()) {
			try {
				file1.createNewFile();
			} catch (IOException e) {
				// TODO Auto-generated catch block
				e.printStackTrace();
			}
		}

		FileWriter fw = null;

		try {
			fw = new FileWriter(file1);
		} catch (IOException e1) {
			// TODO Auto-generated catch block
			e1.printStackTrace();
		}

		char[] chars = null;
		chars = "我是一名学生".toCharArray();

		try {

			fw.write(chars);
			System.out.println("刚才我添加了：" + new String(chars));

		} catch (IOException e) {
			// TODO Auto-generated catch block
			e.printStackTrace();
		}

		if (fw != null) {
			try {
				fw.close();
			} catch (IOException e) {
				// TODO Auto-generated catch block
				e.printStackTrace();
			}
		}
	}

	@Test
	public void copyCharFile() {
		File file1 = new File("d:\\Case\\file1.txt");
		File file2 = new File("d:\\Case\\file2.txt");
		if (!file2.exists()) {
			try {
				file2.createNewFile();
			} catch (IOException e) {
				// TODO Auto-generated catch block
				e.printStackTrace();
			}
		}

		FileReader fis = null;
		FileWriter fos = null;

		try {
			fis = new FileReader(file1);
			try {
				fos = new FileWriter(file2);
			} catch (IOException e) {
				// TODO Auto-generated catch block
				e.printStackTrace();
			}
		} catch (FileNotFoundException e) {
			// TODO Auto-generated catch block
			e.printStackTrace();
		}

		char[] chars = new char[128];
		int len = -1;
		try {
			while ((len = fis.read(chars)) != -1) {
				System.out.println(new String(chars));
				fos.write(chars, 0, len);
			}
		} catch (IOException e) {
			// TODO Auto-generated catch block
			e.printStackTrace();
		}

		if (fis != null) {
			try {
				fis.close();
			} catch (IOException e) {
				// TODO Auto-generated catch block
				e.printStackTrace();
			}
		}
		if (fos != null) {
			try {
				fos.close();
			} catch (IOException e) {
				// TODO Auto-generated catch block
				e.printStackTrace();
			}
		}
	}
}
```

### Test04_File

```java
package IODemo;

	import java.io.BufferedInputStream;
	import java.io.BufferedOutputStream;
	import java.io.File;
	import java.io.FileInputStream;
	import java.io.FileNotFoundException;
	import java.io.FileOutputStream;
	import java.io.FileReader;
	import java.io.IOException;
	import java.io.UnsupportedEncodingException;
	import java.util.Arrays;

	import org.junit.Test;

	public class Test04_File {
		@Test
		public void copyByteFile(){
			
			File file1 = new File("D:\\case\\mydir");
			File file2 = new File("C:\\myFile");
			if(!file2.exists()){
				try {
					file2.createNewFile();
				} catch (IOException e) {
					// TODO Auto-generated catch block
					e.printStackTrace();
				}
			}
		
			FileInputStream fis=null;
			FileOutputStream fos=null;

			BufferedInputStream bis=null;
			BufferedOutputStream bos=null;
			
			try {
				fis=new FileInputStream(file1);
				bis=new BufferedInputStream(fis);
				
				fos=new FileOutputStream(file2);
				bos=new BufferedOutputStream(fos);
				
			} catch (FileNotFoundException e) {
				// TODO Auto-generated catch block
				e.printStackTrace();
			}
			
			long begin=System.currentTimeMillis();
			
			byte[] bytes=new byte[1024];
			int len=-1;
			try {
				while ((len=bis.read(bytes))!=-1) {
					bos.write(bytes, 0, len);
				}
				bos.flush();
			} catch (IOException e) {
				// TODO Auto-generated catch block
				e.printStackTrace();
			}
			
			long end=System.currentTimeMillis();
			System.out.println("拷贝共用时："+(end-begin)+"毫秒");
			
			if(fis!=null){
				try {
					fis.close();
				} catch (IOException e) {
					// TODO Auto-generated catch block
					e.printStackTrace();
				}
			}
			if(fos!=null){
				try {
					fos.close();
				} catch (IOException e) {
					// TODO Auto-generated catch block
					e.printStackTrace();
				}
			}
			
			if(bis!=null){
				try {
					bis.close();
				} catch (IOException e) {
					// TODO Auto-generated catch block
					e.printStackTrace();
				}
			}
			if(bos!=null){
				try {
					bos.close();
				} catch (IOException e) {
					// TODO Auto-generated catch block
					e.printStackTrace();
				}
			}
		}
	}
```