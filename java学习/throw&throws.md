1、throws关键字通常被应用在声明方法时，用来指定可能抛出的异常。多个异常可以使用逗号隔开。当在主函数中调用
该方法时，如果发生异常，就会将异常抛给指定异常对象。如下面例子所示：
public class Shoot {   创建类
static void pop() throws NegativeArraySizeException {
//定义方法并抛出NegativeArraySizeException异常
int [] arr = new int[-3];//创建数组
}
public static void main(String[] args) {//主方法
try { 
pop(); //调用pop()方法
} catch (NegativeArraySizeException e) {
System.out.println("pop()方法抛出的异常");//输出异常信息
}
}
}


2、throw关键字通常用在方法体中，并且抛出一个异常对象。程序在执行到throw语句时立即停止，它后面的语句都不执行。
通过throw抛出异常后，如果想在上一级代码中来捕获并处理异常，则需要在抛出异常的方法中使用throws关键字在方法声
明中指明要跑出的异常；如果要捕捉throw抛出的异常，则必须使用try—catch语句。举例如下：


class MyException extends Exception { //创建自定义异常类
 String message; //定义String类型变量
 public MyException(String ErrorMessagr) {  //父类方法
       message = ErrorMessagr;
 }
 public String getMessage(){   //覆盖getMessage()方法
  return message;
 }
}
public class Captor { //创建类
static int quotient(int x,int y) throws MyException{//定义方法抛出异常
if(y < 0){  //判断参数是否小于0
         throw new MyException("除数不能是负数");//异常信息
 }
 return x/y;//返回值
 }
public static void main(String args[]){ //主方法
 try{ //try语句包含可能发生异常的语句
                int result = quotient(3,-1);//调用方法quotient()
    }catch (MyException e) { //处理自定义异常
  System.out.println(e.getMessage()); //输出异常信息
  }
    catch (ArithmeticException e) {
                   //处理ArithmeticException异常
  System.out.println("除数不能为0");//输出提示信息
  }
   catch (Exception e) { //处理其他异常
  System.out.println("程序发生了其他的异常");
                  //输出提示信息
  }
 }
}