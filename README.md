# 接口程序实验
### ___实验目的___
掌握Java中抽象类和抽象方法的定义  
掌握Java中接口的定义，熟练掌握接口的定义形式以及接口的实现方法  
了解异常的使用方法，并在程序中根据输入情况做异常处理  
### ___实验内容___
某学校为了给学生提供勤工俭学机会，也减轻授课教师的部分压力，准许博士研究生参与课程的助教工作;  
此时，该博士研究生有双重身份：学生和助教教师;  
1.设计两个管理接口：学生管理接口和教师管理接口。学生接口必须包括缴纳学费、查学费的方法；教师接口包括发放薪水和查询薪水的方法;  
2.设计博士研究生类，实现上述的两个接口，该博士研究生应具有姓名、性别、年龄、每学期学费、每月薪水等属性。（其他属性及方法，可自行发挥）;  
3.编写测试类，并实例化至少两名博士研究生，统计他们的年收入和学费。根据两者之差，算出每名博士研究生的年应纳税金额（国家最新工资纳税标准，请自行检索）;  
### ___实验要求___
1.在 博士研究生类中实现各个接口定义的抽象方法;  
2.对年学费和年收入进行统计，用收入减去学费，求得纳税额;  
3.国家最新纳税标准（系数），属于某一时期的特定固定值，与实例化对象没有关系，考虑如何用static  final修饰定义;  
4.实例化研究生类时，可采用运行时通过main方法的参数args一次性赋值，也可采用Scanner类实现运行时交互式输入;  
5.根据输入情况，要在程序中做异常处理; 
### ___核心代码___
```
/**
这里通过接口分别定义了两个抽象方法，分别为（发放薪水、查询薪水；缴纳学费、查询学费）;
在这里考虑到钱可能会涉及到小数，先将参数设置为double类型;
*/

TeacherInterface.java
//发放薪水
public abstract void setPay(double pay);
//查询薪水
public abstract void getPay(double Checkpay);

StudentInterface.java
//缴纳学费
public abstract void setFee(double fee);
//查询学费
public abstract void getFee(double fee);
```
```
因为main中需要使用static类型的，方法必须定义为static类型；
此方法通过if(){}else if(){}、计算应纳税款和实发工资；
try()catch(Exception e){}、是异常捕获机制；
(pay:为月工资*12为一年的总工资-fee:学费)*该范围内应该提交的税率百分比；
public static void ratepaying() {
		try{
		if((pay-fee)<3000) {
			System.out.print("应纳税款"+(pay-fee)*0.03);
			System.out.println("\t实发工资"+((pay-fee)-((pay-fee)*0.03)));
		}else if((pay-fee)>3000 && (pay-fee)<=12000){
			System.out.print("应纳税款"+(pay-fee)*0.1);
			System.out.println("\t实发工资"+((pay-fee)-((pay-fee)*0.1)));
		}else if((pay-fee)>12000 && (pay-fee)<=25000) {
			System.out.print("应纳税款"+(pay-fee)*0.2);
			System.out.println("\t实发工资"+((pay-fee)-((pay-fee)*0.2)));
		}else if((pay-fee)>25000 && (pay-fee)<=35000) {
			System.out.print("应纳税款"+(pay-fee)*0.25);
			System.out.println("\t实发工资"+((pay-fee)-((pay-fee)*0.25)));
		}else if((pay-fee)>35000 && (pay-fee)<=55000) {
			System.out.print("应纳税款"+(pay-fee)*0.3);
			System.out.println("\t实发工资"+((pay-fee)-((pay-fee)*0.3)));
		}else if((pay-fee)>55000 && (pay-fee)<=80000) {
			System.out.print("应纳税款"+(pay-fee)*0.35);
			System.out.println("\t实发工资"+((pay-fee)-((pay-fee)*0.35)));
		}else if((pay-fee)>80000) {
			System.out.print("应纳税款"+(pay-fee)*0.45);
			System.out.println("\t实发工资"+((pay-fee)-((pay-fee)*0.45)));
		}	
		}catch(Exception e){
			System.out.println(e.toString());
		}
	}
  
  /**
 此方法是计算，要查询几个月的工资
 eg：用户想要查询6个月的工资，方法将会获取用户输入的几个月进行计算并返回这几个月的工资；
  */
  public static int check(int check){
		switch(check) {
		case 1: System.out.println(check+"个月的工资："+Checkpay+"¥");break;
		case 2: System.out.println(check+"个月的工资："+Checkpay * 2+"¥");break;
		case 3: System.out.println(check+"个月的工资："+Checkpay * 3+"¥");break;
		case 4: System.out.println(check+"个月的工资："+Checkpay * 4+"¥");break;
		case 5: System.out.println(check+"个月的工资："+Checkpay * 5+"¥");break;
		case 6: System.out.println(check+"个月的工资："+Checkpay * 6+"¥");break;
		case 7: System.out.println(check+"个月的工资："+Checkpay * 7+"¥");break;
		case 8: System.out.println(check+"个月的工资："+Checkpay * 8+"¥");break;
		case 9: System.out.println(check+"个月的工资："+Checkpay * 9+"¥");break;
		case 10: System.out.println(check+"个月的工资："+Checkpay * 10+"¥");break;
		case 11: System.out.println(check+"个月的工资："+Checkpay * 11+"¥");break;
		case 12: System.out.println(check+"个月的工资："+Checkpay * 12+"¥");break;
		}
		return check;
	}
  /**
  通过Scanner和for循环来获取和判断用户想要查询几个人的工资;
  并依次输入用户基本信息、薪水、学费;
  */
  System.out.println("请输入要查询人的个数");
		
		int j = scanner.nextInt();
		for(int i=1;i<=j;i++){
		//初始化研究生对象
		System.out.println("请输入姓名");
		graduate.name = scanner.next();		//姓名
		System.out.println("请输入年龄");
		graduate.age = scanner.nextInt();	//年龄
		System.out.println("请输入性别");
		graduate.sex = scanner.next();		//性别
		//设置工资
		System.out.println("请输入月工资");
		double pay = scanner.nextDouble();	//月工资
		graduate.setPay(pay);
		graduate.getPay(pay);
		System.out.println("请输入要查询几个月的薪水金额");//查询工资
		int check = scanner.nextInt();
		//graduate.getPay(check);
		System.out.println("请输入学费");
		double fee = scanner.nextDouble();	//学费
		graduate.setFee(fee);
		System.out.println("--------------基本信息------------");
		System.out.println("姓名："+graduate.name+"\t年龄："+graduate.age+"\t性别："+graduate.sex);
		System.out.println("--------------工资信息------------");
		System.out.print("工资："+pay+"\t学费："+fee+"\t");
		ratepaying();
		System.out.println("--------------工资查询------------");
		check(check);
```
### ___纳税标准___
![运行结果](https://github.com/Traveller-g/School/blob/main/img/1-1P9201S1231B.jpg)
### ___运行结果截图___
![运行结果](https://github.com/Traveller-g/School/blob/main/img/1605098188.jpg)
### ___编程感想___
通过这次接口程序实验的编写，发现自己对数组的知识掌握的不是很熟练。
