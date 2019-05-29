#include <Keypad.h>
#include <LiquidCrystal.h>
#include <stdlib.h>

LiquidCrystal lcd(0,1,5,4,3,2);
float result(char [],int );

int i=0,count=0;
char arr[20],data,key,sign[10];
float ans;
const byte ROWS = 4; /* four rows */
const byte COLS = 4; /* four columns */
/* define the symbols on the buttons of the keypads */
char hexaKeys[ROWS][COLS] = {
  {'0','1','2','3'},
  {'4','5','6','7'},
  {'8','9','=','.'},
  {'+','-','*','/'}
};
byte rowPins[ROWS] = {10, 11, 12, 13}; /* connect to the row pinouts of the keypad */
byte colPins[COLS] = {6, 7, 8, 9}; /* connect to the column pinouts of the keypad */

Keypad customKeypad = Keypad( makeKeymap(hexaKeys), rowPins, colPins, ROWS, COLS); 

void setup(){
  lcd.begin (16,2) ; 
  lcd.setCursor (5,0) ;
  lcd.print ("Simple") ;
  lcd.setCursor (3,1) ;
  lcd.print ("Calculator") ;
  delay(1000);
  lcd.clear();
}

void loop(){  
 
char key = customKeypad.getKey();
  
  if (key != NO_KEY && (key=='1'||key=='2'||key=='3'||key=='4'||key=='5'||key=='6'||key=='7'||key=='8'||key=='9'||key=='0'||key == '/' || key == '*' || key == '-' || key == '+'||key=='.'))
  {
    arr[i]=key;
    lcd.setCursor (i,0);
    lcd.print(arr[i]);
    i=i+1;
  }
  if(key=='='){
    arr[i]='=';
    lcd.setCursor (i,0);
    lcd.print(arr[i]);
    ans=result(arr,i+1);
    lcd.setCursor (0,1);
    lcd.print("Result:");
    lcd.print(ans);
    delay(2000);
    i=0;
    lcd.clear();
  }

}


float result(char a[],int len)
{
int i,count,op[10],j=0,k=0,n=0;
float res,h[10];
char num[10][10],sign[10],nw[100],an[100];
count=len;
for(i=0;i<count;i++)
{
  lcd.setCursor (i,0);
   lcd.print(arr[i]);
}
for(i=0;i<count+1;i++)
{
  if(a[i]=='+'||a[i]=='-'||a[i]=='*'||a[i]=='/'||a[i]=='=')
  {
    op[j]=i;
    sign[j]=a[i];
    j=j+1;
  }
} 
for(n=0;n<j;n++)
{ 
  if(n==0)
  {
    for(k=0;k<op[n];k++)
    {
    nw[k]=a[k];
    nw[k+1]='\0';
      h[n]=atof(nw);
    }
  }
  else 
  {
    for(k=0;k<op[n]-op[n-1]-1;k++)
    {
    nw[k]=a[op[n-1]+1+k];
    nw[k+1]='\0';
      h[n]=atof(nw);
    }
  }}    

k=0;
  for(i=0;i<j-1;i++)
  {
    switch(sign[k])
    {
    case '+':
      res=h[i]+h[i+1];
      break;
    case '-':
      res=h[i]-h[i+1];
      break;
    case '*':
      res=h[i]*h[i+1];
      break;
    case '/':
      res=h[i]/h[i+1];
      break;
    }
    h[i+1]=res;
    k=k+1;
  }
return res;
}
