#include <iostream>
using namespace std;


double Get_value()
{
    while (true)
    {
        double a;
        cin >> a;

        if (cin.fail())
        {
            cin.clear();
            cin.ignore(32767, '\n');
            cout << endl;
            cout << "Invalid input.Enter correct data:";
        }
        else
        {
            cin.ignore(32767, '\n');
            return a;
        }
    }

}
void Checking(double a)
{
    while (a > 100)
    {
        cout << "Percentege of initial alloy can't be more than 100 %!" << endl;
        cout << "Enter percentage of cuper in first initial alloy: ";
        a = Get_value();
    }

}

void Calculation(double first_perc, double second_perc,double final_perc, double mass)
{
    double first_coef;
    double  second_coef;
    double third_coef;
    double mass_of_first;
    double mass_of_second;
    if (first_perc == final_perc && second_perc == final_perc)
    {
        mass_of_first = mass / 2;
        mass_of_second = mass / 2;
        cout << "Mass of first initial alloy: " << mass_of_first << " kg" << endl;
        cout << endl;
        cout << "Mass of second initial alloy: " << mass_of_second << " kg" << endl;

    }
    else if (first_perc == final_perc)
    {
        mass_of_first = mass;
        mass_of_second = 0;
        cout << "Mass of first initial alloy: " << mass_of_first  << " kg" << endl;
        cout << endl;
        cout << "Mass of second initial alloy: " << mass_of_second << " kg" << endl;

    }
    else if (second_perc == final_perc)
    {
        mass_of_first = 0;
        mass_of_second = mass;
        cout << "Mass of first initial alloy: " << mass_of_first << " kg" << endl;
        cout << endl;
        cout << "Mass of second initial alloy: " << mass_of_second << " kg" << endl;

    }
    else
    {
        first_coef = first_perc / 100;
        second_coef = second_perc / 100;
        third_coef = final_perc * mass / 100;
        mass_of_first = (third_coef - second_coef * mass) / (first_coef - second_coef);
        mass_of_second = mass - mass_of_first;
        cout << "Mass of first initial alloy: " << mass_of_first << " kg" << endl;
        cout << endl;
        cout << "Mass of second initial alloy: " << mass_of_second << " kg" << endl;

    }
 

}

int main()

{
   

    double first_alloy;
    double second_alloy;
    double final_alloy;
    double mass_of_final;
  
  
    cout << "Enter percentage of cuper in first initial alloy: ";
    first_alloy = Get_value();

    Checking(first_alloy);
   
    
    cout << endl;
    cout << "Enter percentage of cuper in second initial alloy: ";
    second_alloy = Get_value();
    Checking(second_alloy);

    cout << endl;
    cout << "Enter percentage of cuper in final  alloy: ";
    final_alloy = Get_value();
    while (final_alloy < first_alloy && final_alloy  < second_alloy ||
        final_alloy  >  first_alloy && final_alloy  >  second_alloy) {
        cout << "It's imposible to create final alloy whith this percentage of cuper!" << endl;
        cout << "Enter correct percentage of final alloy: ";
        final_alloy = Get_value();
    }
    cout << endl;
    cout << "Enter the mass of final alloy(kg): ";
    mass_of_final = Get_value();

    cout << endl;

    Calculation(first_alloy, second_alloy, final_alloy, mass_of_final);
}
