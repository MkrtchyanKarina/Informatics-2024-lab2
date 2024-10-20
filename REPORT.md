Отчёт по лабораторной работе №2:

Решение:

![image](https://github.com/user-attachments/assets/58566547-9f99-41be-905a-bc5c2cfa3f4c)


Объяснение решения:

1. В рабочей папке создадим новый файл ip-address.bash. Для этого используем команду gedit ip-address.bash. В открывшемся файле будем писать скрипт для перевода ip-адреса в двоичное представление.

2. В начале каждого скрипта должен стоять shebang-комментарий, указывающий, с каким интерпретатором нужно выполнять скрипт. Мы используем интерпретатор bash, который находится в корневом каталоге, в папке bin -> комментарий будет выглядеть следующим образом #!/bin/bash.

3. Создадим функцию binary().

4. В этой функции создадим переменную  bin_ip="", в которую будем записывать результат перевода ip, а также переменную ip_array=($(echo $1 | tr "." " ")). Эта переменная - массив, состоящий из 4х чисел ip-адреса, разделенных пробелом. Для того, чтобы получить такой массив, мы применяем функцию tr к значению первого аргумента функции ($1). Функция tr заменяет первый символ на второй, в нашем случае точку на пробел.

5. Затем мы проходимся в цикле по каждому элементу массива. Для этого на месте индекса укажем @, это означает, что мы выбираем все элементы из массива (${ip_array[@]}).

6. В цикле создадим переменную bin_n, в которую будем записывать результат, полученный при переводе одного из 4х чисел адреса (числа n). Если число удовлетворяет условиям - оно меньше 256 и больше 0. Если оно не входит в эти ограничения, то bin_n = 00000000.

7. Для перевода числа напишем ещё один (вложенный) цикл. В нем будет 8 итераций, так как длина каждого числа в двоичной записи должна быть равной 8.

8. На каждой итерации в начало переменной bin_n будем записывать остаток от деления на 2 числа n, а число n будет равно результату целочисленного деления себя же на 2.

9. После окончания вложенного цикла мы получим число n в двоичной системе счисления. Этот результат мы, вместе с точкой, присоединим к переменной bin_ip.

10. После окончания внешнего цикла bin_ip будет состоять из четырех чисел в двоичной СС, разделенных точкой. Выведем результат в терминал, удалив лишнюю точку в начале- ${bin_ip:1}.

11. В языке Bash есть не только аргументы функций, но и аргументы скрипта. При выполнении этого скрипта мы будем передавать один такой аргумент - ip-адрес. Поэтому при вызове функции binary() мы передадим ей в качестве аргумента $1 - значение первого аргумента скрипта.


Пример работы функции:

![image](https://github.com/user-attachments/assets/6f7861fe-5634-4bba-ba1f-82709aa5300a)
