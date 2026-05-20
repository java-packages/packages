//SUM OF DIGITS

import java.util.Scanner;
public class SumOfDigits { 
ALGORITHM: 
SUM OF DIGITS OF A POSITIVE INTEGER 
public static void main(String[] args) { 
Scanner sc = new Scanner(System.in); 
System.out.print("Enter an integer: "); 
int num = sc.nextInt();
int sum = 0; 
int temp = num; 
while (temp != 0) { 
int digit = temp % 10;
sum += digit; 
temp = temp / 10; 
} 
System.out.println("Sum of digits = " + sum);
}}
