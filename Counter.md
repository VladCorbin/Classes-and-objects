#include <iostream>
#include <string>
#include <Windows.h>

class Counter
{
private:
	int _num;

public:

	Counter(int num = 1) : _num(num) {}

	void add() { ++_num; }

	void subtract() { --_num; }

	int get_num() { return _num; }
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

    int initial_value = 1; 

	if (Approval == "да")
	{
		std::cout << "Введите начальное значение счётчика: ";
		std::cin >> initial_value;
		std::cout << std::endl;
	}
	
	Counter counter(initial_value);

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
	}	
	else 
	{
		std::cout << "Не понял ваш ответ, попробуйте заново." << std::endl;
	}


	return EXIT_SUCCESS;
}