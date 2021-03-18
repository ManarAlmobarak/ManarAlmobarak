- 👋 Hi, I’m @ManarAlmobarak
- 👀 I’m interested in ...
- 🌱 I’m currently learning ...
- 💞️ I’m looking to collaborate on ...
- 📫 How to reach me ...

<!---
ManarAlmobarak/ManarAlmobarak is a ✨ special ✨ repository because its `README.md` (this file) appears on your GitHub profile.
You can click the Preview link to take a look at your changes.
--->
/*
 * To change this license header, choose License Headers in Project Properties.
 * To change this template file, choose Tools | Templates
 * and open the template in the editor.
 */
package ospro;

import java.util.InputMismatchException;
import java.util.Scanner;

/**
 *
 * @author mnarr
 */
public class Memory {
   
                static int partitionsNumber;
  // arays to store the data 
     static String[] partitionStatus;
       static int[] partitionNum ;
     static int [] pSize ;
     static int [] StartAdress ;
     static int [] EndAdress ;
     static String [] processName ;
     static int [] fragmentation ;
        static  int partitionSize;
  static Scanner scanner = new Scanner(System.in);
    public static void main(String args[]){

    try{
    System.out.println("Enter the number of partitions :");
          partitionsNumber=scanner.nextInt();
// if the user enter a negative number will ask him to enter again..
while(partitionsNumber<0){
             System.out.println("invalid input, you entered a negative number");
           System.out.println("please re-enter a number");

      partitionsNumber=scanner.nextInt();
      
     }}
    //  if the user enter a char for partitionsNumber the system will catch it and stop the run  ..
     catch(InputMismatchException E){
       System.out.println("Invaled entry you should enter a number ..");
return;
         }
      partitionStatus = new String[partitionsNumber];
     partitionNum = new int[partitionsNumber];
     pSize =new int[partitionsNumber];
     StartAdress =new int[partitionsNumber];
      EndAdress =new int[partitionsNumber];
      processName =new String[partitionsNumber];
     fragmentation =new int[partitionsNumber];
     
     
     
 try{
     for(int i = 0 ; i<partitionsNumber;i++){
      System.out.println("Enter the size of partition "+(i+1)+" in KB:");
       partitionSize = scanner.nextInt();
 
         partitionNum[i]=i;
         pSize[i]=partitionSize;
         partitionStatus[i]="Free";
         processName[i]=null;
         fragmentation[i]=-1;
         
        //if it in the first partitions the start address will be 0
     if(i==0){
     
         StartAdress[0]=0;
     }
     else{
    //if it not the  size of start address will be the size of the last end address
     StartAdress[i]=EndAdress[i-1];
     }
     
     EndAdress[i]= (partitionSize*1024)+StartAdress[i];

     }}
 
 
 // if the user enter a char for the size the system will catch it and stop the run 
          catch(InputMismatchException E){
       System.out.println("Invaled entry you should enter a number ..");
     return;


         }
 
   // to print the report    
System.out.println("-------- Status report of memory partitions --------- ");


   // for loop to print all partitions information    

for(int j = 0 ; j < partitionsNumber;j++){
        System.out.println("Partition number ["+ (j +1)+"]");
System.out.println("--------------------------------------------------");
    System.out.println("●The Starting Address:"+StartAdress[j]+"B");
    System.out.println("●The Ending Address:"+EndAdress[j]+"B");
    System.out.println("●Partition Status:"+partitionStatus[j]);
    System.out.println("●The Partition Size:"+pSize[j]+"KB");
    System.out.println("●The Procces Name:"+processName[j]);
    System.out.println("●Fragmentation Size:"+fragmentation[j]+"KB");
System.out.println("--------------------------------------------------");

}
}
    
    }
    

