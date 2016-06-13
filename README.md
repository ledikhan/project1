# project1
#include <stdio.h>

double totalMilesDrivePerDay = 0;
double costPerGallon = 0;
double avgMilesPerGal = 0;
double dailyParkingFee = 0;
double dailyTollCost = 0;

void get_input() {

    printf("Enter the amount of miles you drive per day: \n");
    scanf("%lf",&totalMilesDrivePerDay);
    printf("Enter the cost of gasoline per gallon:\n"); 
    scanf("%lf",&costPerGallon);
    printf("Enter your average amount of miles per gallon:\n");
    scanf("%lf",&avgMilesPerGal);
    printf("Enter your parking fees per day:\n");
    scanf("%lf",&dailyParkingFee);
    printf("Enter the  cost of tolls per day:\n");
    scanf("%lf",&dailyTollCost);
    
}

double calculate_expense() {
    double realCost = costPerGallon/avgMilesPerGal;
    double realPostTotalMiles = totalMilesDrivePerDay * realCost;    
    return (realPostTotalMiles + dailyParkingFee + dailyTollCost);
}

int main() {
    double result;
    int proceed = 0;
    char choice='n'; //added variable for user interaction
    do { //changed while to do-while, because the condition will continue to be checked and loop if met
        get_input();
        
        result = calculate_expense();        

        printf("%.2lf\n", result); //round to two decimal places
        printf("Would you like to proceed [y/N]\n"); //removed ctrl+c option
        scanf(" %c",&choice);
        if(choice == 'y' || choice == 'Y') { //if user inputs either y OR Y then option 1 will run
           proceed = 1;
        } else {
           proceed = 0; 
        } 
    }while(proceed); 
    
    return 0;
}
