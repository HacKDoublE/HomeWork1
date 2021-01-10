<!DOCTYPE html>
<html>
    <head>
        <title>Калькулятор римских чисел</title>
        <meta charset="UTF-8">
    </head>
    <body>
        <script>
            
            var a;
function Perevod(r) //Конструктор с методами перевода
{
    this.r=r;
    var arab;//перевод в арабское число
    var rim='';//создаем пустую строку //перевод в римское число
    this.toArab=function()   //метод по переводу в арабское число
    {
        var letters = this.r;//
        arab=0;
        for (var i=0; i<letters.length;i++)
        {
            
            switch(letters[i])
            {
                case "X":{                              // Перевод X 
                    if(letters[i+1]=="L")
                        {arab=arab+40; i=i+1; break; };

                    if(letters[i+1]=="C")
                        {arab=arab+90; i=i+1; break;};
                    
                    if(letters[i+1]!= "L" && letters[i+1] != "C")
                        {arab=arab+10;};
                    };
                break;
                case "I": {                             //Перевод I                   
                    if(letters[i+1]=="X") 
                        {arab=arab+9; i=i+1; break; }; 
                    
                    
                    if(letters[i+1]=="V")
                        {arab=arab+4; i=i+1; break;};
                    
                    if(letters[i+1] != "X" && letters[i+1] != "V") {arab=arab+1;};
                    };
                break;
                
                case "V": {arab=arab+5;}                  //Перевод V
                break;
                
                case "L":{ arab=arab+50; break;}            // Перевод L
                break;

                case "C":{                                  //Перевод C
                    if(letters[i+1]=="M")
                        {arab=arab+900; i=i+1; break;};
                    
                    if(letters[i+1]=="D")
                        {arab=arab+400; i=i+1; break;};
                    
                    if(letters[i+1] != "M" && letters[i+1] != "D")
                        {arab=arab+100;}
                    
                }
                break;
                
                case "D" : {arab=arab+500;}                     //Перевод D
                break;

                case "M": {arab=arab+1000;}                     //Перевод M
                break;

                
                
            }
        }
        
        return arab;
    }
    this.toRim=function(){   //метод по переводу в римское число
        var j = parseInt(this.r); //j используется для цикла while в качестве счетчика
        var n = j  // переводимое число 
        if(n>=1000){
        while(j>=1000){
            j=j-1000;
            n=j;
            rim=rim+'M';
        }
        j=n; 
        }
        
        if(n>=900 && n<1000){
            n=n-900;
            rim=rim+'CM'
            j=n;
        }
        if(n<500 && n>=400){
            n=n-400;
            rim=rim+'CD';
            j=n;
        }
        if(n>=500 && n<900){
            n=n-500;
            j=n;
            rim=rim+'D';
        }
        if(n>=100 && n<400){
            while(j>=100){
                j=j-100;
                n=n-100;
                rim=rim+'C';
            }
            j=n;
        }
        if(n>=50 && n <90){
            rim=rim+'L';
            n=n-50;
            j=n;
            while(j>=10){
                j=j-10;
                n=n-10;
                rim=rim+'X';
            }
            j=n;
        }
        if(n>=40 && n<50){
            rim=rim+'XL';
            n=n-40;
            j=n;
        }
        if (n<40 && n>=10){
            j=n;
            while(j>=10){
                j=j-10;
                rim=rim+'X';
                n=n-10;
            }
            j=n;
        }
        if(n==9){
            n=n-9;
            rim=rim+'IX';
        }
        if(n>=5 && n<9){
            rim=rim+'V';
            n=n-5;
            j=n;
            while(j>0){
                j=j-1;
                n=n-1;
                rim=rim+'I';
            }
            
        }
        j=n;
        if(n==4){
            rim=rim+'IV'
            n=n-4;
        }
        if(n>0 && n<4){
            j=n;
            while(j>0){
                j=j-1;
                n=n-1;
                rim=rim+'I'
            }
        }
        alert(rim);
    }
}


var arab1 = new Perevod(prompt("Введите первое римское число:"));
var arab2 =  new Perevod(prompt("Введите второе римское число:"));
var c=arab1.toArab(); //переведенные числа с помощью метода toArab заключаем в переменные c и d и проводим действия
var d=arab2.toArab();
var dst=prompt("Введите действие: + - * / ");

switch(dst){                        //Анализ действий 
    case '+': {var summ=c+d; alert(summ);
                var summ1 = new Perevod(summ);
                summ1.toRim();  
        }
    break;

    case '-': {var razn=c-d; alert(razn);
                if(razn > 0){ var razn1 = new Perevod(razn); razn1.toRim()} else{alert("Отрицательные числа не переводят"); break;}
    
        } //надо учесть будет модуль и "-"
    break;

    case '*': {var proizv = c*d; alert(proizv);
                var proizv1 = new Perevod(proizv);
                proizv1.toRim();
        }
    break;

    case '/':{var del=c/d; alert(del);
                var del1 = new Perevod(del);
                del1.toRim();
        }
    break;
}
        </script>
    </body>
</html>
