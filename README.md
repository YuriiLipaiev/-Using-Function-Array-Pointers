# -Using-Function-Array-Pointers

// Function Array Pointers

#include <iostream>

const double* f1(const double arr[], int n);
const double* f2(const double [], int n);
const double* f3(const double *, int n);

int main()
{
    using namespace std;

    double av[3] = { 1112.3, 1542.6, 2227.9 };

    //pointer to function f1

    const double *(*p1)(const double arr[], int n) = f1;

    auto p2 = f2;

    //use pointers to a function

    cout << "Using pointers to functions: " << endl;
    cout << "Adress value: " << endl;
    cout << (*p1)(av, 3) << " : " << *(*p1)(av, 3) << endl;
    cout << p2(av, 3) << " : " << *p2(av, 3) << endl;

    const double* (*pa[3])(const double arr[], int n) = {f1, f2, f3};

    //pb pointer to the first element of the pointer array pa

    auto pb = pa;

    //use arrays of function pointers

    cout << "Using an array of pointers to functions: " << endl;
    cout << "Adress value: " << endl;

    for (size_t i = 0; i < 3; i++)
    {
        cout << pa[i](av, 3) << " : " << * pa[i](av, 3) << endl;
    }
   
    //use pointer to pointer function

    cout << "Using a pointer to a pointer to a function: " << endl;
    cout << "Adress value: " << endl;
    for (size_t i = 0; i < 3; i++)
    {
        cout << pb[i](av, 3) << " : " << *pb[i](av, 3) << endl;
    }

    //a pointer to an array of pointers to a function
    cout << "Using pointers to an array of pointers: " << endl;
    cout << "Adress value: " << endl;

    auto pc = &pa;

    cout << (*pc)[0](av, 3) << " : " << *(*pc)[0](av, 3) << endl;
    cout << (*pc)[0] << endl;

  

    return 0;
}

const double* f1(const double arr[], int n)
{
    return arr;
}

const double* f2(const double arr[], int n)
{
    return arr + 1;
}

const double* f3(const double* arr, int n)
{
    return arr + 2;
}
