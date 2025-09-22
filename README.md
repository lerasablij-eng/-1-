#include <iostream>
using namespace std;

struct Pair {
    int first;   // номінал купюри
    int second;  // кількість купюр

    // метод ініціалізації з перевіркою коректності
    bool Init(int f, int s) {
        // дозволені номінали
        int allowed[] = {1, 2, 5, 10, 20, 50, 100, 500, 1000};
        bool validNominal = false;

        for (int i = 0; i < 9; i++) {
            if (f == allowed[i]) {
                validNominal = true;
                break;
            }
        }

        if (!validNominal || s <= 0) {
            cout << "Помилка: некоректні дані!" << endl;
            return false;
        }

        first = f;
        second = s;
        return true;
    }

    // метод введення з клавіатури
    void Read() {
        int f, s;
        bool ok;
        do {
            cout << "Введіть номінал купюри (1, 2, 5, 10, 20, 50, 100, 500, 1000): ";
            cin >> f;
            cout << "Введіть кількість купюр: ";
            cin >> s;
            ok = Init(f, s);  // перевірка через Init()
        } while (!ok);
    }

    // метод виведення
    void Display() {
        cout << "Номінал: " << first << " грн, "
             << "Кількість: " << second << endl;
    }

    // метод для обчислення суми
    int summa() {
        return first * second;
    }
};

// демонстрація роботи
int main() {
    Pair money;
    money.Read();        // введення даних
    money.Display();     // виведення
    cout << "Загальна сума: " << money.summa() << " грн" << endl;
    return 0;
}
