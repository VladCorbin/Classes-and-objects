#include <iostream>
#include <string>
#include <Windows.h>

class Calculator
{
private:
	double _num1;
	double _num2;

public:
	bool set_num(double num1, double num2) 
	{
        if (num1 == 0 && num2 == 0) 
		{
            std::cout << "Ошибка: оба числа не могут быть равны нулю!" << std::endl;
            return false;
        }
        _num1 = num1;
        _num2 = num2;
        return true;
    }

	double add() { return _num1 + _num2; }

	double multiply() { return _num1 * _num2; }

	double subtract_1_2() { return _num1 - _num2; }

	double subtract_2_1() { return _num2 - _num1; }

	double divide_1_2() 
	{ 
		if (_num2 == 0) {
            std::cout << "Ошибка: деление на ноль!" << std::endl;
            return 0;
        }
		return _num1 / _num2; 
	}

	double divide_2_1() 
	{ 
		if (_num1 == 0) 
		{
            std::cout << "Ошибка: деление на ноль!" << std::endl;
            return 0;
        }
		return _num2 / _num1; 
	}

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

	std::string Approval;
	double num1;
	double num2;
	do 
	{
		do
		{
			std::cout << "Введите num1: ";
			std::cin >> num1;

			if (num1 == 0) 
			{
                std::cout << "Ошибка: значение не должно быть равно нулю!" << std::endl;
            }
		} while (num1 == 0);

		do
		{
			std::cout << "Введите num2: ";
			std::cin >> num2;

			if (num2 == 0) 
			{
                std::cout << "Ошибка: значение не должно быть равно нулю!" << std::endl;
            }
		} while (num2 == 0);

		
			Calculator calculations;
			calculations.set_num(num1, num2);

			std::cout << "num1 + num2 = " << calculations.add() << std::endl;
			std::cout << "num1 - num2 = " << calculations.subtract_1_2() << std::endl;
			std::cout << "num2 - num1 = " << calculations.subtract_2_1() << std::endl;
			std::cout << "num1 * num2 = " << calculations.multiply() << std::endl;
			std::cout << "num1 / num2 = " << calculations.divide_1_2() << std::endl;
			std::cout << "num2 / num1 = " << calculations.divide_2_1() << std::endl;


			std::cout << "Закончить операцию?";
			std::cin >> Approval;

	

	} while (Approval != "да");

		std::cout << "Операция завершилась!" << std::endl;

	return EXIT_SUCCESS;
}