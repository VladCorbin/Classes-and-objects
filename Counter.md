#include <iostream>
#include <string>
#include <Windows.h>

class Counter
{
private:
	int _num;

public:

	void set_num(int num) { _num = num; }

	int add() { return ++_num; }

	int subtract() { return --_num; }

	int ger_num() { return _num; }
};



int main()
{
	SetConsoleCP(1251);
	SetConsoleOutputCP(1251);

	std::string Approval;
	std::string command;

	std::cout << "Вы хотите указать начальное значение счётчика? Введите да или нет: ";
	std::cin >> Approval;
	std::cout << std::endl;

	Counter counter;

	if (Approval == "да")
	{
		int num;
		std::cout << "Введите начальное значение счётчика: ";
		std::cin >> num;
		std::cout << std::endl;

		counter.set_num(num);
	}
	else if (Approval == "нет")
	{
		counter.set_num(1);
	}

	do
	{
		do
		{
			std::cout << "Введите команду('+', '-', '=' или 'x') : ";
			std::cin >> command;

			if (command == "+")
			{
				counter.add();
			}
			else if (command == "-")
			{
				counter.subtract();
			}

			if(command != "-" && command != "+" && command != "=" && command != "x")
			{
				std::cout << "Ошибка: Не верная комадна! " << std::endl;
			}

		} while (command != "=" && command != "x");

		if (command == "=")
		{
			std::cout << counter.ger_num() << std::endl;
		}
	} while (command != "x");

	if (command == "x")
	{
		std::cout << "До свидания!" << std::endl;
		return 1;
	}	
	else 
	{
		std::cout << "Не понял ваш ответ, попробуйте заново." << std::endl;
		return 1;
	}


	return EXIT_SUCCESS;
}