
#include <iostream>
#include <ctime>
using namespace std;

class ProstoCLass
{
public:
    
    ProstoCLass(unsigned int size)
    {
        this->size = size;
        arr = new int[size];
    }
    
                                   unsigned int GetSize()
                                                             { return size; }
                                   int* GetArr()
                                                             { return arr; }

    void InitArrayRandomly()
    {
        for (int i = 0; i < size; i++)
        {
            arr[i] = (rand() % 20) - 10;
        }
    }
    
    void DisplayArray()
    {
        setlocale(LC_CTYPE, "ukr");
        
        cout << "Розмiр масиву : " << this->size << endl;
        cout << "Масив : " << ends;
        for (int i = 0; i < size; i++)
        {
            cout << arr[i] << " ";
        }
    }

    const ProstoCLass& operator+=(int value)
    {
        for (int i = 0; i < this->size; i++)
        {
            this->arr[i] += value;
        }

        return *this;
    }

    const ProstoCLass& operator-=(int value)
    {
        for (int i = 0; i < this->size; i++)
        {
            this->arr[i] -= value;
        }
        return *this;
    }

    const ProstoCLass& operator*=(int value)
    {
        for (int i = 0; i < this->size; i++)
        {
            this->arr[i] *= value;
        }
        return *this;
    }

    ~ProstoCLass()
    {
        delete[] arr;
    }
private:
    int* arr;
    unsigned int size;
};


ProstoCLass& TransformProstoCLass(ProstoCLass& vector);

int main()
{
    setlocale(LC_CTYPE, "ukr");
    srand(time(NULL));
    const int arrSize = 10;

    ProstoCLass* testVec = new ProstoCLass(arrSize);
    testVec->InitArrayRandomly();

    cout << "Початковий масив :" << endl;
    testVec->DisplayArray();

    cout << "\n\nОператор дадовання (тест +1)" << endl;
    *testVec += 1;
    testVec->DisplayArray();

    cout << "\n\nОператор вiднiмання (тест -1)" << endl;
    *testVec -= 1;
    testVec->DisplayArray();

    cout << "\n\nОператор множення (тест *(-1))" << endl;
    *testVec *= -1;
    testVec->DisplayArray();

    cout << "\n\nПеретворення масиву (Варiант №3)" << endl;
    TransformProstoCLass(*testVec);
    testVec->DisplayArray();
}

ProstoCLass& TransformProstoCLass(ProstoCLass& vector)
{
    for (int i = 0; i < 10; ++i)
    {
        if (vector.GetArr()[i] == 0)
        {
            vector.GetArr()[i] = 1;
        }
    }

    return vector;
}
