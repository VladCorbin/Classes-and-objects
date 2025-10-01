#include <iostream>
#include <string>
#include <Windows.h>

class Calculator
{
private:
	double _num1;
	double _num2;

public:

	double add() { return _num1 + _num2; }

	double multiply() { return _num1 * _num2; }

	double subtract_1_2() { return _num1 - _num2; }

	double subtract_2_1() { return _num2 - _num1; }

	double divide_1_2() { return _num1 / _num2; }

	double divide_2_1() { return _num2 / _num1; }

	bool set_num1(double new_num1)
	{
		if (new_num1 != 0)
		{
			_num1 = new_num1;
			return true;
		}
		return false;
	}

	bool set_num2(double new_num2)
	{
		if (new_num2 != 0)
		{
			_num2 = new_num2;
			return true;
		}
		return false;
	}

};



int main()
{
	SetConsoleCP(1251);
	SetConsoleOutputCP(1251);

	double num1;
	double num2;

	std::cout << "Введите num1: ";
	std::cin >> num1;
	std::cout << "Введите num2: ";
	std::cin >> num2;

	if (num1 == 0 || num2 == 0)
	{
		std::cout << "Oшибка: Значения не должны быть равны 0!" << std::endl;
		return 1;
	}

	Calculator calculations = { num1, num2 };

	std::cout << "Сложение: " << calculations.add() << std::endl;
	std::cout << "Вычитание (_num1 - _num2): " << calculations.subtract_1_2() << std::endl;
	std::cout << "Вычитание (_num2 - _num1): " << calculations.subtract_2_1() << std::endl;
	std::cout << "Умножение: " << calculations.multiply() << std::endl;
	std::cout << "Деление (_num1 / _num2): " << calculations.divide_1_2() << std::endl;
	std::cout << "Деление (_num2 / _num1): " << calculations.divide_2_1() << std::endl;

	return EXIT_SUCCESS;
}