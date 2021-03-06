# Глава 3. Прости проверки

В настоящата глава ще разгледаме условните конструкции в езика C#, чрез които нашата програма може да има различно действие в зависимост от дадено условие. Ще обясним синтаксиса на условните оператори за проверки: if и if-else с подходящи примери, както и ще видим в какъв диапазон една променлива живее (нейният scope). Накрая ще разгледаме техники за дебъгване, чрез които лесно да проследяваме пътя, който извървява нашата програма по време на нейното изпълнение.

## Видео

<div class="video-player">
  Гледайте видео-урок по тази глава тук: <a target="_blank"
  href="https://www.youtube.com/watch?v=uwW_ueaOt7M">
  https://www.youtube.com/watch?v=uwW_ueaOt7M</a>.
</div>
<script src="/assets/js/video.js"></script>

## Сравняване на числа

В програмирането можем да сравняваме стойности чрез следните **оператори**:

1. Оператор **<** (по-малко)

1. Оператор **>** (по-голямо)

1. Оператор **<=** (по-малко или равно)

1. Оператор **==** (равно)

При сравнение ни се връща булева стойност `True` или `False` в зависимост от това дали сравнението е вярно

Пример: 

```cs
var a = 5;
var b = 10;
Console.WriteLine(a < b);      // True
Console.WriteLine(a > 0);      // True
Console.WriteLine(a > 100);    // False
Console.WriteLine(a < a);      // False
Console.WriteLine(a <= 5);     // True
Console.WriteLine(b == 2 * a); // True
```

### Оператори за сравнение

<table>
<tr>
<th>Оператор</th> <th>Означение</th> <th>Работи за</th>
</tr>
<tr>
<td>Проверка за равенство</td><td align="center"> == </td><td rowspan="2"> числа, стрингове, дати</td>
</tr>
<tr>
<td>Проверка за различно</td><td align="center"> != </td>
</tr>
<tr>
<td>По-голямо</td><td align="center"> > </td><td rowspan="4">числа, дати, други сравними типове</td>
</tr>
<tr>
<td>По-голямо или равно</td><td align="center"> >= </td>
</tr>
<tr>
<td>По-малко</td><td align="center"> < </td>
</tr>
<tr>
<td>По-малко или равно</td><td align="center"> <= </td>
</tr>
</table>

Пример:

```cs
var result = (5 <= 6);
Console.WriteLine(result); // True
```

## Прости проверки

В програмирането често **проверяваме дадени условия** и извършваме различни действия според резултатa от проверката. Това става чрез конструкцията `if`, която има следният основен формат:

```cs
if (булев израз)
{
      тяло на условната конструкция;
}
``` 

Пример: Въвеждаме оценка в конзолата и проверяваме дали тя е отлична (**≥ 5.50**)

```cs
var grade = double.Parse(Console.ReadLine());
if (grade >= 5.50)
{
   Console.WriteLine("Excellent!");
}
```

Тестване на решението: https://judge.softuni.bg/Contests/Practice/Index/152#0


## Проверки с if-else конструкция
Съществува разновидност на конструкцията `if`, която се нарича `if-else`. Изполваме я когато искаме да проверим дадено условие и ако резултата от него е **позитивен** да извършим едни действия, а ако е **негативен** - други. Нейният формат е следният:

```cs
if (булев израз)
{
      тяло на условната конструкция;
}
else
{
      тяло на else-конструкция;
}
```

Пример: Подобно на горния пример, въвеждаме оценка, проверяваме дали е отлична, но изписваме резултат **и в двата случая**

```cs
var grade = double.Parse(Console.ReadLine());
if (grade >= 5.50)
{
   Console.WriteLine("Excellent!");
}
else
{
   Console.WriteLine("Not excellent.");
}
```

Тестване на решението: https://judge.softuni.bg/Contests/Practice/Index/152#1


## За къдравите скоби { } след if / else

Когато имаме **само една команда** в тялото на `if` конструкцията можем да **пропуснем къдравите скоби** обозначаващи тялото на условния оператор. Когато искаме да изпълним **блок от код** (група команди) къдравите скоби са **задължителни** понеже в случай, че ги изпуснем ще се изпълни **само следващият ред**.

TODO: Add important note that it's a good practice to always use { }

Ето един пример, в който изпускането на къдравите скоби води до объркване:

```cs
var color = "red";
if (color == "red")
  Console.WriteLine("tomato");
else if (color == "yellow")
  Console.WriteLine("banana");
Console.WriteLine("bye");
```

Изпълнението на горния код ще изведе следният резултат на конзолата:

```cs
tomato
bye
```

С къдрави скоби:

```cs
var color = "red";
if (color == "red")
{
  Console.WriteLine("tomato");
}
else if (color == "yellow")
{
  Console.WriteLine("banana");
  Console.WriteLine("bye");
}
```

На конзолата ще бъде отпечатано:

```cs
tomato
```
## Четно или нечетно – пример

Да се напише програма, която проверява дали цяло число е **четно** (even) или **нечетно** (odd).

Задачата можем да я решим чрез една `if-else` конструкция и оператора `%`, който ни връща **остатъка при деление** на едно число с друго.

```cs
var num = int.Parse(Console.ReadLine());
if (num % 2 == 0)
{
   Console.WriteLine("even");
}
else
{
   Console.WriteLine("odd");
}
```

Тестване на решението: https://judge.softuni.bg/Contests/Practice/Index/152#2

## По-голямото число – пример

Да се напише програма, която чете две цели числа и извежда по-голямото от тях

Първата ни задача е да **прочетем** двете числа. След което чрез прост `if-else` в съчетание с **оператора за по-голямо** `>` лесно можем да направим проверката.

```cs
Console.WriteLine("Enter two integers:");
var num1 = int.Parse(Console.ReadLine());
var num2 = int.Parse(Console.ReadLine());
if (num1 > num2)
{ 
  Console.WriteLine("Greater number: " + num1); 
}
else
{ 
  Console.WriteLine("Greater number: " + num2); 
}
```

## Живот на променлива

Всяка една променлива си има обхват на "живот" наречен **variable scope**. Този обхват уточнява къде една променлива може да бъде използвана. В C# областта, в която една променлива съществува започва от реда, на който сме я **дефинирали** и завърша до първата затваряща къдрава скоба "**}**" (на метода, на `if` конструкцията и т.н.). Така че е важно да знаем, че **всяка променлива дефинирана вътре в тялото на `if` няма да бъде достъпна извън него**, освен ако не сме я дефинирали по-нагоре в кода.

В долния пример на последният ред, в който се опитваме да отпечатаме променливата **salary**, която е дефинирана в if-a, ще получим **грешка** защото нямаме достъп до нея.

```cs
var myBankAccount = Bank.GetMyBankAccount();
if (DateTime.Now().Day >= PayDay)
{
    var salary = Job.GetMyMonthlySalary();
    myBankAccount = myBankAccount + salary;
}

Console.WriteLine(myBankAccount);
Console.WriteLine(salary) //Error!
```
## Серии от проверки

Конструкцията if-else-if-else… може да е в серия
Пример: да се изпише с английски текст дадено число (от 0 до 10)

```cs
var num = int.Parse(Console.ReadLine());
if (num == 1)
{ 
  Console.WriteLine("one"); 
}
else if (num == 2)
{
  Console.WriteLine("two");
}
else if (num == 3)
{ 
  Console.WriteLine("three"); 
}
// TODO: add more checks
else
{
  Console.WriteLine("number too big");
}
```

Тестване на решението: https://judge.softuni.bg/Contests/Practice/Index/152#4

## Бонус точки – задача

Дадено е цяло число – брой точки
Ако числото е до 100 включително, бонус точките са 5
Ако числото е по-голямо от 100, бонус точките са 20%
Ако числото е по-голямо от 1000, бонус точките са 10%
Допълнителни бонус точки:
За четно число  1 т.
За число, което завършва на 5  2 т.
Да се напише програма, която пресмята бонус точките и общия брой точки след прилагане на бонусите

## Бонус точки – решение

```cs
Console.Write("Enter score: ");
var num = int.Parse(Console.ReadLine());
var bonusScore = 0.0;
if (num > 1000)
  { bonusScore = num * 0.10; }
else // TODO: write more logic here … 
if (num % 10 == 5)
  { bonusScore += 2; }
else // TODO: write more logic here …
Console.WriteLine("Bonus score: {0}", bonusScore);
Console.WriteLine("Total score: {0}", num + bonusScore);
```

TODO: show the samples

Тестване на решението: https://judge.softuni.bg/Contests/Practice/Index/152#5

## Сумиране на секунди – задача

Трима спортни състезатели финишират за някакъв брой секунди (между 1 и 50). Да се пресметне сумарното им време във формат "минути:секунди". Секундите да се изведат с водеща нула (2  "02", 7  "07", 35  "35").

TODO: add examples

## Сумиране на секунди – решение

```cs
var sec1 = int.Parse(Console.ReadLine());
// TODO: Read also sec2 and sec3 …
var secs = sec1 + sec2 + sec3;
var mins = 0;
if (sec > 59)   // TODO: Repeat this 2 times …
{ mins++; secs = sec - 60; }
if (secs < 10)
 { Console.WriteLine(mins + ":" + "0" + secs); }
else
 { Console.WriteLine(mins + ":" + secs); }
```

Тестване на решението: https://judge.softuni.bg/Contests/Practice/Index/152#6

## Конвертор за мерни единици

Да се напише програма, която преобразува разстояние между посочените в таблицата мерни единици:
Вход: число +входна мерна единица +изходна мерна единица

TODO: add the table

Примерен вход и изход:

TODO: add the table

## Конвертор за мерни единици – решение

var size = double.Parse(Console.ReadLine());
var sourceMetric = Console.ReadLine().ToLower();
var destMetric = Console.ReadLine().ToLower();
if (sourceMetric == "km")
    { size = size / 0.001; }
// Check the other metrics: mm, cm, ft, yd, ...
if (destMetric == "ft")
    { size = size * 3.2808399; }
// Check the other metrics: mm, cm, ft, yd, ...
Console.WriteLine(size + " " + destMetric);

Тестване на решението: https://judge.softuni.bg/Contests/Practice/Index/152#7


## Дебъгване - прости операции с дебъгер

### Какво е "дебъгване"?

Процес на „закачане“ към изпълнението на програмата, което ни позволява да проследи процеса на изпълнение 
Това ни позволява да откриваме грешки (бъгове)

TODO: image

### Дебъгване във Visual Studio

Натискане на [F10] ще стартира програмата в debug режим.
Можем да преминем към следващата стъпка отново [F10]
Можем да създаваме [F9] стопери – breakpoints
До тях можем директно да стигнем изпозлвайки [F5]


## Упражнения: прости проверки

TODO: Да се следва съдържанието от файла "3. Simple-Conditions-Exercises.docx".
TODO: Повтарящите се задачи да се махнат -> да се прехвърли съдържанието за тях по-нагоре в тази глава от книгата.

### 0. Празно Visual Studio решение (Blank Solution)

### 1. Проверка за отлична оценка

### 2. Отлична оценка или не

### 3. Четно или нечетно

### 4. Намиране на по-голямото число

### 5. Изписване на число до 10 с думи

### 6. Бонус точки

### 7. Сумиране на секунди

### 8. Конвертор за мерни единици

### 9. Познай паролата

### 10. Число от 100 до 200

### 11. Еднакви думи

### 12. Информация за скоростта

### 13. Лица на фигури

### 14. Време + 15 минути

### 15. Еднакви 3 числа

### 16. * Изписване на число до 100 с думи

## Упражнения: графични и Web приложения: конветор за валути



