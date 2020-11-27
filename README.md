# -5
作业处理
## 实验目的
掌握字符串String及其方法的使用  
掌握文件的读取/写入方法  
掌握异常处理结构
## 业务要求
在某课上,学生要提交实验结果，该结果存储在一个文本文件A中。  
文件A包括两部分内容：  
一是学生的基本信息；  
二是学生处理后的作业信息，该作业的业务逻辑内容是：利用已学的字符串处理知识编程完成《长恨歌》古诗的整理对齐工作，写出功能方法，实现如下功能：

1、每7个汉字加入一个标点符号，奇数时加“，”，偶数时加“。”  
2、允许提供输入参数，统计古诗中某个字或词出现的次数  
3、输入的文本来源于文本文件B读取，把处理好的结果写入到文本文件A  
4、考虑操作中可能出现的异常，在程序中设计异常处理程序
## 实验要求
1、设计学生类（可利用之前的）；  
2、采用交互式方式实例化某学生；  
3、设计程序完成上述的业务逻辑处理，并且把“古诗处理后的输出”结果存储到学生基本信息所在的文本文件A中。
## 实验代码
    public class Student {
	    String name,sex;
	    int age,number;	
    }
>设计学生类，定义变量

    Student stu =new Student();                     //创建对象
    stu.name="小明";                                //给对象赋值
    stu.age=21;
    stu.sex="男";
    stu.number=2018123456;  
>实例化学生

    char [] c =new char[7];
	      try{
	    	  Writer out  = new FileWriter(targetFile,true);      //指向目的地的
	    	  Reader in = new FileReader(sourceFile);             //指向源的输入流
	    	  int n = -1;
	    	  int x = 1;
	    	  out.write("姓名："+stu.name+"\t"+"年龄："+stu.age+"\t"+"\t"+"性别："+stu.sex+"\t"+"\t"+"学号："+stu.number+"\r");
	    	  out.write("作业处理结果："+"\r");
	          while((n=in.read(c))!=-1){
	        	  x=x*-1;
	        	  if(x==-1) {
	        		  out.write(c,0,n);
		              out.write(",  ");
	        	  }
	        	  else{
	        		  out.write(c,0,n);
	        		  out.write("。"+"\r");
	        	  }	              
	           }
	          out.flush();
	          out.close();
	          in.close();
	      }	      
	      catch(IOException e){
	    	  System.out.println("Error"+e);
	      }
>先写入学生的信息。定义一个数组，容量为7，设置循环，n的值不为-1就循环读取、写入。定义x=1，在循环开始时乘以-1，当x=-1时，读取的时一句诗的前半句，
则尾加一个逗号，反之则加句号并换行，以实现古诗整理的功能。

## 实验结果
![源文件](https://github.com/2018310768/-5/blob/main/java源TXT.JPG)
![结果](https://github.com/2018310768/-5/blob/main/java结果.JPG)
## 实验感想
这次实验我掌握了Java的文件处理和String的用法。遇到的问题是，文本文件的默认编码格式是uft-8，eclipse的编码格式是GBK，所以写入的
时候总是出现乱码，通过与室友讨论解决了问题。
