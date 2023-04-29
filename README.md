<h1 align="center"> МИНИСТЕРСТВО НАУКИ И ВЫСШЕГО ОБРАЗОВАНИЯ РОССИЙСКОЙ ФЕДЕРАЦИИ ФЕДЕРАЛЬНОЕ ГОСУДАРСТВЕННОЕ БЮДЖЕТНОЕ ОБРАЗОВАТЕЛЬНОЕ УЧРЕЖДЕНИЕ ВЫСШЕГО ОБРАЗОВАНИЯ «САХАЛИНСКИЙ ГОСУДАРСТВЕННЫЙ УНИВЕРСИТЕТ»</h1>
<br>
<br>
<br>
<br>
<br>
<br>
<p align="center">Лабораторная работа №9</p>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<p align="right">Выполнил: Морошкин Максим Александрович</p>
<p align="right">Проверил: Соболев Е. И.</p>
<br>
<br>
<br>
<br>
<br>
<br>

<p align="center">г. Южно-Сахалинск <br> 2023 год</p>

<h2 align="center">Введение</h2>
<p align="justify">Задачи на JavaScript</p>

<h2>Цели и задачи</h2>
Задачи:

1.	Есть некоторая строка (var str = 'fgfggg';), что будет, если мы возьмем str[0]?
2.	 Дана функция, она принимает в качестве аргументов строки '*', '1', 'b', '1c', реализуйте ее так, что бы она вернула строку '1*b*1c'
3.	Дано дерево, надо найти сумму всех вершин.
4.	Нарисовать стилями полукруг.
5.	Есть массив в котором лежат объекты с датами, отсортировать по датам.
6.	Есть несколько слов, определить состоят ли они из одних и тех же букв('кот', 'ток', 'окт')
7.	От них же. Числа от 1 до 100 лежат в массиве, они хаотично перемешанные, от туда изъяли одно число, надо найти, что это за число. алгоритм не должен превышать O(n^2) сложности.
8.	Реализовать сортировку пузырьком.
9.	Обратная польская нотация.
10.	Реализовать функцию является ли слово палендром.


<h2>Решение задач</h2>

```html
<div class="Block1">
			<style>
				.task4 {
					margin:20px;
					width: 200px;
					height: 100px;
					border-radius: 0 0 100px 100px;
					background-color: blue;
					text-align:center;
				}
			</style>
			<h1>Задачи</h1>
			<button onclick="task1()">Задача 1</button><br>		
			<button onclick="task2()">Задача 2</button><br>	
			<button onclick="task3()">Задача 3</button><br>	
			<div class="task4">Задача 4</div>
			<button onclick="task5()">Задача 5</button><br>	
			<button onclick="alert(task6('кот', 'ток', 'окт'))">Задача 6</button><br>	
			<button onclick="task7()">Задача 7</button><br>
			<button onclick="task8()">Задача 8</button><br>
			<button onclick="task9('1 3 5 * -')">Задача 9</button><br>
			<button onclick="task10()">Задача 10</button><br>

			<div id="result">Тут будет ответ!!!</div>
	
		</div>
		
		<script>
		function task1() {
			var str = 'fgfggg';
			var firstChar = str[0];
			document.getElementById('result').innerHTML = firstChar;
		}
		
		function task2() {
			var args = ['*', '1', 'b', '1c'];
			var result="";
			for (var i = 1; i < args.length; i++) 
			{
				if (i == args.length-1) { result+=args[i]; break;}
				result +=args[i] + args[0]; 
			}
			document.getElementById('result').innerHTML = result;
		}
							
		class Node {
			constructor(value, left = null, right = null) {
			this.value = value;
			this.left = left;
			this.right = right;
			}
		}

		// Создаем дерево
		const root = new Node(1);
		root.left = new Node(2);
		root.right = new Node(3);
		root.left.left = new Node(4);
		root.left.right = new Node(5);
		root.right.left = new Node(6);
		root.right.right = new Node(7);

		// Функция для нахождения суммы вершин
		function task3(node) {
			if (!node) {
				return 0;
			}
			return node.value + task3(node.left) + task3(node.right);
		}					
		
		function task5() {
			const arr = [
				{ date: new Date('2017-10-31') },
				{ date: new Date('2003-02-12') },
				{ date: new Date('2023-05-15') },
				{ date: new Date('2019-01-30') }
			];
			arr.sort((a, b) => a.date - b.date);
			var result ="";
			for (var i = 0; i < arr.length; i++) {
				const year = arr[i].date.getFullYear();
				const month = arr[i].date.getMonth() + 1;
				const day = arr[i].date.getDate();
				result += `${year}-${month}-${day}<br>`;
			}
			document.getElementById('result').innerHTML = result;
		}
		
		function task6(...words) {
			var result ="";
			const firstWord = words[0].split('').sort().join('');
			for (let i = 1; i < words.length; i++) {
				const word = words[i].split('').sort().join('');
				if (word !== firstWord) {
					return false;
				}
			}
			return true;
		}
		
		function task7() {
			const arr = [1, 2, 3, 4, 5, 6, 7, 8, 10, 11, 12, 13, 14, 15, 16, 17, 18, 19, 20, 21, 22, 23, 24, 25, 26, 27, 28, 29, 30, 31, 32, 33, 34, 35, 36, 37, 38, 39, 40, 41, 42, 43, 44, 45, 46, 47, 48, 49, 50, 51, 52, 53, 54, 55, 56, 57, 58, 59, 60, 61, 62, 63, 64, 65, 66, 67, 68, 69, 70, 71, 72, 73, 74, 75, 76, 77, 78, 79, 80, 81, 82, 83, 84, 85, 86, 87, 88, 89, 90, 91, 92, 93, 94, 95, 96, 97, 98, 99, 100];
			const sumOfArray = arr.reduce((acc, cur) => acc + cur);
			const sumOfNumbers = (100 * 101) / 2;
			document.getElementById('result').innerHTML = sumOfNumbers - sumOfArray;
		}
		
		function task8()
		{
			var array = [9,5,2,1,3,8,6,4,7]
			for (var i = 0; i < array.length; i++)
			{
				for (var j = i + 1; j < array.length; j++)
				{
					if(array[j] < array[i])
					{
						var temp = array[i];
						array[i] = array[j];
						array[j] = temp;
					}
				}	
			}
			document.getElementById('result').innerHTML = array;
		}
		
		function task9(expression) {
			const stack = [];
			for (let i = 0; i < expression.length; i++) {
				const token = expression[i];
				if (token === " ") continue; 
				if (!isNaN(token)) {
					stack.push(parseInt(token)); 
				} else {
					const b = stack.pop();
					const a = stack.pop();
					if (token === "+") {
						stack.push(a + b);
					} else if (token === "-") {
						stack.push(a - b);
					} else if (token === "*") {
						stack.push(a * b);
					} else if (token === "/") {
						stack.push(a / b);
					} else {
						document.getElementById('result').innerHTML = "Неизвестный оператор: " + token;
					}
				}
			}
			if (stack.length !== 1) {
				document.getElementById('result').innerHTML = "Некорректное выражение: " + expression;
			}
			document.getElementById('result').innerHTML = stack.pop();
		}


		function task10() {
			var word = "шалаш";
			var result ="";
			if (word === word.split("").reverse().join("")) {result = "Палиндром";} else {result = "Непалиндром";}
			document.getElementById('result').innerHTML = result;
		}
		
		</script>	
```

<h2>Вывод</h2>
Я научился работать, с функциями, алгоритмами, методами в JS
