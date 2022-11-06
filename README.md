
import java.util.ArrayList;
import java.util.Scanner;

public class SchoolSystem {
 int[] maxStudent;
 int[] currentStudent;
 ArrayList<Boolean> result;
// 初始化数据
 public SchoolSystem(int big,int medium,int small) {
  maxStudent=new int[3];
  currentStudent=new int[3];
  result = new ArrayList<>();
  maxStudent[0]=big;
  maxStudent[1]=medium;
  maxStudent[2]=small;
  for(int i=0;i<currentStudent.length;i++)
   currentStudent[i]=0;
 }
// 判断是否添加成功
 public boolean addStudent(int stuType) {
     if(currentStudent[stuType-1]<maxStudent[stuType-1]){
         currentStudent[stuType-1]+=1;
         return true;
     }else{
         return false;
     }
 }

 public boolean delStudent(Integer stuType) {
     if(currentStudent[stuType]>0){
         currentStudent[stuType]-=1;
         return true;
     }
     else{
         return false;
     }
 }

 public void print(){
   System.out.println(this.result);
  }

 public static ArrayList<Integer> parse(String input) {
     ArrayList<Integer> list = new ArrayList<>();
     String[] numList = input.split("\\s");
     for (String s : numList) {
         // System.out.println(s);
         list.add(Integer.parseInt(s));
         // System.out.println(list);
     }
     return list;
     //按格式输入字符串，分析字符串，获得相关参数存储到列表中并返回
 }

 public static ArrayList<Integer> parse2(String input) {
     ArrayList<Integer> list = new ArrayList<>();
     String[] numList = input.split("\\s");//空格分割字符
     for (String s : numList) {
         // System.out.println(s);
         list.add(Integer.parseInt(s));//保存
         // System.out.println(list);
     }
     return list;
 }
 
 public static void main(String[] args) {
     Scanner sc = new Scanner(System.in);
     String input = sc.nextLine();
     ArrayList<Integer> params2=SchoolSystem.parse(input);
     // System.out.println(params);
     SchoolSystem schoolSystem=new SchoolSystem(params2.get(0),params2.get(1),params2.get(2));
     for(int i=3;i<params2.size();i++) {
        //  schoolSystem.result.add(schoolSystem.addStudent(params.get(i)));
      if(params2.get(i)>0)
       schoolSystem.result.add(schoolSystem.addStudent(params2.get(i)));
      else
        //   处理参数，将-1、-2、-3转化成current中对应的地址下标0、1、2， Math.abs是求绝对值
       schoolSystem.result.add(schoolSystem.delStudent(Math.abs(params2.get(i))-1));
     }
     schoolSystem.print();
     System.out.println("王炫慧参与本代码开发，并进行了修改。");
 }
 }

