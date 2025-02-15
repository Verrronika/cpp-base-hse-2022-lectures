# Лекция 1. Введение в C++ (11.01.2022)

## Вводная часть

### Элементы контроля

- ДЗ (H)
- КР 1 (T1)
- КР 2 (T2)
- Проект (P)
- Экзамен (E)
- Бонусный балл (b)

### Формула оценки

min(0.1(T1 + T2) + 0.3H + 0.3P + 0.2E + b, 10)

### Info

- Время проверки задач ДЗ: до 3-х дней (будет code revue; Компилятор Clang, 20-й стандарт языка. Но можно пользоваться и компилятором g++, проблем возникнуть не должно).
- КР с асинхронным прокторингом, как обычно.
- На экзамене те же самые задачи, что и на КР.

### Дедлайны по ДЗ

- До дедлайна: 100 %
- Между дедлайном и неделей после: линейно 100 % —> 0 %
- Позже: 0 %

### Когда надо писать в личку лектору:

- Проблемы с семинаристом
- Проблемы с проверкой ДЗ

## Введение в C++

C++ — компилируемый язык.

Компилятор получает программу и выдаёт исполняемый файл.

Компилятор компилирует файл один раз, проделывая оптимизационные процессы:

1. Он смотрит на код и старается, чтобы он выполнялся как можно быстрее
2. Он отслеживает ошибки

## Компилирование программ вручную с помощью g++

Пусть main.cpp — наш код на C++, и мы хотим его скомпилировать.

1. Создаём исполняемый файл с именем program: `g++ main.cpp -o program` 
При выполнении команды `g++ main.cpp` будет создан исполняемый файл с именем a.out, который можно запустить аналогичным образом: `./a.out`.
Важно: Компиляция ДЗ происходит командой `g++ main.cpp -o program -Werror -Wall`.
Флаг `-Werror` означает, что все предупреждения компилятора будут трактоваться, как ошибки. Флаг `-Wall` устанавливает уровень того, какие проблемы считаются ворнингами.
2. Выводим информацию про этот и другие файлы в директории: `ls -lah`
3. Запустим исполняемый файл program: `./program`
4. Смотрим код возврата последней выполненной команды (а именно, запуска исполняемого файла program): `echo $?`

## Из чего состоит программа на C++?

```cpp
#include <iostream>  // заголовочный файл (библиотека)

int main() {
	std::cout << "Hello, world!" << std::endl;  // Почему не \n? Потому что не на всех OS \n - это перенос строки, а endl - работает всегда
	return 0;  // 0 - ок, не 0 - программа сломалась. Можно не писать, но лучше писать
}
```

## Чтение из консоли

```cpp
#include <iostream>

int main() {
	int value;  // завели переменную типа int, но не задали никакого значения (не инициализировали её)
	std::cin >> value;  // прочитаем значение в value
	std::cout << "Hello, world!" << value << std::endl;  // выведем значение value
	return 0;
}
```

Проблема заключается в том, что если создать, но не инициализировать переменную, то в ней может храниться мусор (ранодомное мусорное значение).

Исправим это:

```cpp
#include <iostream>

int main() {
	int value = 0;  // завели переменную типа int и инициализировали её
	std::cin >> value;
	std::cout << "Hello, world! " << value << std::endl;
	return 0;
}
```

## Что такое `std`?

`std` — пространство имён.

Можно писать так:

```cpp
#include <iostream>

using namespace std;

int main() {
	int value = 0;
	cin >> value;
	cout << "Hello, world! " << value << endl;
	return 0;
}
```

Но не рекомендуется так делать, потому что `namespace std` одержит очень много стандартных функций $\Longrightarrow$ могут возникнуть конфликты с рукописными функциями.

## Конструкция `if`

```cpp
#include <iostream>

int main() {
	int value = 0;
	if (value > 0) {
	    std::cout << "Hello, world!" << value << std::endl;
	}
	return 0;
}
```

Отступы значения не имеют.

Если `if` содержит одну строчку, то фигурные скобочки можно не писать, но так делать не рекомендуется.

## Цикл `for`

```cpp
#include <iostream>

int main() {
	int value = 0;
	
	for (int i = 0; i < 10; ++i) {
	    std::cout << "Hello, world! " << i << std::endl;
	}
	return 0;
}
```

1. Инициализируется переменная `i`;
2. Проверяется условие;
3. Выполняется `++i` и тело `for`.

### Префиксная и постфиксная записи

`++i` — **префиксная** запись (возвращает значение `i` после инкремента)

`i++` — **постфиксная** запись (возвращает значение `i` до инкремента)

## Цикл `while`

```cpp
#include <iostream>

int main() {
	int value = 0;

	while (value < 10) {
	    std::cout << value << std::endl;
	    value++;
	}
	return 0;
}
```
