# Basic_Calculator_C-

#include<iostream>
using namespace std;
// Basic calculator in C++
bool invalid;

class Calculator
{
    protected:
    char op;
    float a, b, result;

    public:
    void set_values(float a1, float b1)
    {
        a = a1;
        b = b1;
    }

    void set_char(void)
    {
        char c;
        cin>>c;
        op = c;
    }

    void input();

    char return_char()
    {
        return op;
    }

};

void Calculator :: input()
{
    cout<<"Enter your two values: "<<endl;
    cin>>a;
    cin>>b;
    set_values(a, b);

    do
    {
        cout<<"Enter your operator "<<endl;
        set_char();

        switch (return_char())
        {
        case '*':
            result = a*b;
            invalid = false;
            break;

        case '/':
            result = a/b;
            invalid = false;
            break;

        case '+':
            result = a+b;
            invalid = false;
            break;

        case '-':
            result = a-b;
            invalid = false;
            break;

        
        default:
        cout<<"Invalid Operator!!"<<endl;
            invalid = true;
            break;
        }
        
    }while(invalid == true);

    cout << result;
}

class Scientifc_cal
{
protected:
    int n;
    int base, power;
public:
    int factorial(int n)
    {
        if (n == 1)
        {
            return 1;
        }
        else
            return factorial(n - 1) * n;
    }
    int pow(int base, int power)
    {
        int b = 1;
        for (int i = 0; i < power; i++)
        {
            b = base * b;
        }
        return b; 
    }

    void Result(void)
    {
        int number;
        cout<<"\nEnter your number ";
        cin>>number;
        //executing factorial() function here
        cout<<"Factorial of the number is "<<factorial(number)<<endl;

        cout<<"Enter Base ";
        cin>>base;
        cout<<"Enter the power of your Base ";
        cin>>power;

        //executing pow() function here
        cout<<pow(base, power)<<endl;
    }
};

class Hybrid_Cal : public Scientifc_cal , public Calculator
{
public:
    void display(void)
    {
        input();
        Result();
    }
};

int main(){
    Hybrid_Cal h1;
    h1.input();
    h1.Result();

    h1.display();
    return 0;
}

// hybrid cal --> multilevel inheritance

/* SINE FUNCTION -->

int factorial(int n)
{
    if(n == 1)
    {
        return 1;
    }
    else
    return factorial(n-1)*n;
}
int pow(int base, int power)
{
    int b = 1;
    for (int i = 0; i < power; i++)
    {
        b = base*b;
    }
    return b;
}

class Sin
{
    float x, sum_s;
    int n;
    public:
    Sin(float x1)
    {
        n = 5; // accuracy increases as n increases
        x = x1;
        sum_s = 0;
        float num;
        float denom;
        float coeff_nth;
        float a_nth;

        for (int i = 1; i <= n; i++)  // using maclaurin series expansion
        {
            num = pow(-1, i+1);
            denom = factorial(2i - 1);
            coeff_nth = num * denom;
            sum_s = sum_s + (coeff_nth*a_nth);
        }
        cout<<"sin(x) = "<<sum_s;
    }
};
hello
   */
