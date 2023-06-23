<h1 align="center"> МИНИСТЕРСТВО НАУКИ И ВЫСШЕГО ОБРАЗОВАНИЯ РОССИЙСКОЙ ФЕДЕРАЦИИ ФЕДЕРАЛЬНОЕ ГОСУДАРСТВЕННОЕ БЮДЖЕТНОЕ ОБРАЗОВАТЕЛЬНОЕ УЧРЕЖДЕНИЕ ВЫСШЕГО ОБРАЗОВАНИЯ «САХАЛИНСКИЙ ГОСУДАРСТВЕННЫЙ УНИВЕРСИТЕТ»</h1>

<p align="center">Лабораторная работа №13 <br> "PHP" </p>

<p align="right">Выполнил: Алексеев М. М.</p>
<p align="right">Проверил: Соболев Е. И.</p>

<p align="center">г. Южно-Сахалинск <br> 2023 год</p>

<h2 align="center">Введение</h2>
<p align="justify">Работа с формами через PHP.</p>

<h2 align="center">Цели и задачи</h2>

1.	Спросите город пользователя с помощью формы. Результат запишите в переменную `$city`. Выведите на экран фразу 'Ваш город: %Город%'.
2.	Решите предыдущую задачу так, чтобы пользователь не мог вводить теги и сломать сайт.
3.	Сделайте так, чтобы форма после отправки скрывалась.
4.	Спросите имя пользователя с помощью формы. Результат запишите в переменную `$name`. Выведите на экран фразу 'Привет, %Имя%'.
5.	Спросите у пользователя имя, возраст, а также попросите его ввести сообщение (его сделайте в textarea). Выведите эти данные на экран в формате, приведенном под данной задачей. Позаботьтесь о том, чтобы пользователь не мог вводить теги (просто удаляйте их) и таким образом сломать сайт.
6.	Спросите возраст пользователя. Если форма была отправлена и введен возраст, то выведите его на экран, а форму уберите. Если же форма не была отправлена (это будет при первом заходе на страницу) - просто покажите ее.
7.	Спросите у пользователя логин и пароль (в браузере должен быть звездочками). Сравните их с логином `$login` и паролем `$pass`, хранящихся в файле. Если все верно - выведите 'Доступ разрешен!', в противном случае - 'Доступ запрещен!'. Сделайте так, чтобы скрипт обрезал концевые пробелы в строках, которые ввел пользователь.
8.	Спросите имя пользователя с помощью формы. Результат запишите в переменную `$name`. Сделайте так, чтобы после отправки формы значения ее полей не пропадали.
9.	Спросите у пользователя имя, а также попросите его ввести сообщение (textarea). Сделайте так, чтобы после отправки формы значения его полей не пропадали.
10.	Дана строка 'ahb acb aeb aeeb adcb axeb'. Напишите регулярку, которая найдет строки ahb, acb, aeb по шаблону: буква 'a', любой символ, буква 'b'.
11.	Дана строка 'aba aca aea abba adca abea'. Напишите регулярку, которая найдет строки abba adca abea по шаблону: буква 'a', 2 любых символа, буква 'a'.
12.	Дана строка 'aba aca aea abba adca abea'. Напишите регулярку, которая найдет строки abba и abea, не захватив adca. 
13. Дана строка 'aa aba abba abbba abca abea'. Напишите регулярку, которая найдет строки aba, abba, abbba по шаблону: буква 'a', буква 'b' любое количество раз, буква 'a'. 
14.	 Дана строка 'aa aba abba abbba abca abea'. Напишите регулярку, которая найдет строки aa, aba, abba, abbba по шаблону: буква 'a', буква 'b' любое количество раз (в том числе ниодного раза), буква 'a'. 
15.	 Дана строка 'aa aba abba abbba abca abea'. Напишите регулярку, которая найдет строки aa, aba по шаблону: буква 'a', буква 'b' один раз или ниодного, буква 'a'. 
16.	Дана строка 'ab abab abab abababab abea'. Напишите регулярку, которая найдет строки по шаблону: строка 'ab' повторяется 1 или более раз. 
17.	Дана строка 'a.a aba aea'. Напишите регулярку, которая найдет строку a.a, не захватив остальные. 
18.	 Дана строка '2+3 223 2223'. Напишите регулярку, которая найдет строку 2+3, не захватив остальные. 
19.	 Дана строка '23 2+3 2++3 2+++3 345 567'. Напишите регулярку, которая найдет строки 2+3, 2++3, 2+++3, не захватив остальные (+ может быть любое количество). 
20.	 Дана строка '23 2+3 2++3 2+++3 445 677'. Напишите регулярку, которая найдет строки 23, 2+3, 2++3, 2+++3, не захватив остальные. 
21.	 Дана строка '*+ *q+ *qq+ *qqq+ *qqq qqq+'. Напишите регулярку, которая найдет строки *q+, *qq+, *qqq+, не захватив остальные. 
22.	 Дана строка '*+ *q+ *qq+ *qqq+ *qqq qqq+'. Напишите регулярку, которая найдет строки *+, *q+, *qq+, *qqq+, не захватив остальные. 
23.	Дана строка 'aba accca azzza wwwwa'. Напишите регулярку, которая найдет все строки по краям которых стоят буквы 'a', и заменит каждую из них на '!'. Между буквами a может быть любой символ (кроме a). 

<h2 align="center">Решение задач</h2>

```php
<!DOCTYPE html>
<html>

<head>
	<title>Лабораторная 13</title>
	<link rel="stylesheet" href="style.css">
</head>

<body>

    <h4>1 задание</h4>
    <?php
         //isset — Определяет, была ли установлена переменная значением, отличным от null
         if (isset($_REQUEST['city'])) {
            $city = $_REQUEST['city'];
            echo 'Ваш город, ' . $city;
        }
	?>
	<form action="" method="get">
		<input type="text" name="city">
		<br>
		<input type="submit">
	</form>

    <h4>2 задание</h4>
    <?php
        if (isset($_REQUEST['input'])) {
            $input = $_POST['input'];
            //strip_tags — Удаление тегов HTML и PHP из строки
            $clean_input = strip_tags($input);
        }
    ?>
    <form action="" method="get">
        <input type="text" name="city" placeholder="Введите город">
        <br>
        <input type="submit">
    </form>

    <h4>3 задание</h4>
    <?php
    if (empty($_GET)) {
    ?>
        <form action="" method="GET">
            <input name="test1">
            <br>
            <input type="submit">
        </form>
    <?php
    } else {
    ?>
        <form action="" method="GET">
            <input type="submit">
        </form>
    <?php
    }
    ?>

    <h4>4 задание</h4>
    <?php
    if (isset($_REQUEST['name'])) {
        $name = $_REQUEST['name'];
        echo 'Привет, ' . $name;
    }
    ?>
    <form action="" method="get">
        <input type="text" name="name">
        <br>
        <input type="submit">
    </form>

    <h4>5 задание</h4>
    <?php
    if (isset($_REQUEST['name']) and isset($_REQUEST['age']) and isset($_REQUEST['text'])) {
        $name = strip_tags($_REQUEST['name']);
        $age = strip_tags($_REQUEST['age']);
        $text = strip_tags($_REQUEST['text']);
        echo 'Имя - ' . $name . '<br>' . 'Возраст - ' . $age . '<br>Сообщение: ' . $text;
    }
    ?>
    <form action="" method="get">
        <input type="text" name="name" placeholder="Имя">
        <br>
        <input type="text" name="age" placeholder="Возраст">
        <br>
        <textarea name="text" placeholder="Сообщение"></textarea>
        <br>
        <input type="submit">
    </form>

    <h4>6 задание</h4>
    <?php
    if (isset($_REQUEST['age'])) {
        $age = $_REQUEST['age'];
        echo $age;
    }
    if (!isset($_REQUEST['age'])) {
    ?>
        <form action="" method="get">
            <input name="age" placeholder="Введите ваш возраст">
            <br>
            <input type="submit">
        </form>
    <?php } 
    ?>

    <h4>7 задание</h4>
    <?php
    $loginFile = 'maxim';
    $passwordFile = 'qwerty';
    if (isset($_REQUEST['login']) and isset($_REQUEST['password'])) {
        if ($_REQUEST['login'] == $loginFile and $$_REQUEST['password'] == $passwordFile) {
            echo 'введено верно';
        } else {
            echo 'неверный логин или пароль';
        }
    }
    ?>
    <form action="" method="post">
        <input type="text" name="login" placeholder="Логин">
        <br>
        <input type="password" name="password" placeholder="Пароль">
        <br>
        <input type="submit">
    </form>

    <h4>8 задание</h4>
    <?php
    $name = '';
    if (isset($_REQUEST['name'])) {
        $name = $_REQUEST['name'];
        echo $name;
    }
    ?>
    <form action="" method="post">
        <input type="text" name="name" value="<?= $name; ?>">
        <br>
        <input type="submit">
    </form>

    <h4>9 задание</h4>
    <?php
        $message = '';
        $name = '';
        if (isset($_REQUEST['name']) and isset($_REQUEST['message'])) {
            $name = $_REQUEST['name'];
            $message = $_REQUEST['message'];
        }
    ?>
    <form action="" method="post">
        <input type="text" name="name" placeholder="Имя" value="<?= $name; ?>">
        <br>
        <textarea name="message" placeholder="Введите сообщение"> <?= $message; ?></textarea>
        <br>
        <input type="submit">
    </form>

    <h4>10 задание</h4>
    <?php
    
    echo preg_replace('#a.b#', 'true', 'ahb acb aeb aeeb adcb axeb');
    ?>

    <h4>11 задание</h4>
    <?php
    echo preg_replace('#a..a#', 'true', 'aba aca aea abba adca abea');
    ?>

    <h4>12 задание</h4>
    <?php
    echo preg_replace('#ab.a#', 'true', 'aba aca aea abba adca abea');
    ?>

    <?php
    echo preg_replace('#ab+a#', 'true', 'aa aba abba abbba abca abea');
    ?>

    <h4>13 задание</h4>
    <?php
    echo preg_replace('#ab*a#', 'true', 'aa aba abba abbba abca abea');
    ?>

    <h4>14 задание</h4>
    <?php
    echo preg_replace('#ab?a#', 'true', 'aa aba abba abbba abca abea');
    ?>

    <h4>15 задание</h4>
    <?php
    echo preg_replace('#(ab)+#', 'true', 'ab abab abab abababab abea');
    ?>

    <h4>16 задание</h4>
    <?php
    echo preg_replace('#a\.a#', 'true', 'a.a aba aea');
    ?>

    <h4>17 задание</h4>
    <?php
    echo preg_replace('#2\+3#', 'true', '2+3 223 2223');
    ?>

    <h4>18 задание</h4>
    <?php
    echo preg_replace('#2\++3#', 'true', '23 2+3 2++3 2+++3 345 567')
    ?>

    <h4>19 задание</h4>
    <?php
    echo preg_replace('#2\+*3#', 'true', '23 2+3 2++3 2+++3 445 677');
    ?>

    <h4>20 задание</h4>
    <?php
    echo preg_replace('#\*q+\+#', 'true', '*+ *q+ *qq+ *qqq+ *qqq qqq+');
    ?>

    <h4>21 задание</h4>
    <?php
    echo preg_replace('#\*q*\+#', 'true', '*+ *q+ *qq+ *qqq+ *qqq qqq+');
    ?>

    <h4>22 задание</h4>
    <?php
    echo preg_replace('#a.+?a#', '!', 'aba accca azzza wwwwa');
    ?>

</body>

</html>
```


<h2 align="center">Вывод</h2>
В этой лабораторной работе я научился работать с формами, узнал, чем отличаются глобальные переменные $_POST и $_GET, а также научился пользоваться регулярными выражениями. 
