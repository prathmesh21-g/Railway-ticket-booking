#include <stdio.h>
#include <stdlib.h>
#include <string.h>
#include <time.h>

struct Train {

    char from[50];
    char to[50];
    char name[100];
    char time[30];
};

int main() {

    struct Train trains[20] = {

        {"Mumbai", "Pune", "Deccan Express", "06:00 AM"},
        {"Pune", "Mumbai", "Sinhagad Express", "07:30 AM"},
        {"Pune", "Delhi", "Rajdhani Express", "04:00 PM"},
        {"Delhi", "Pune", "Duronto Express", "05:00 PM"},
        {"Mumbai", "Delhi", "Rajdhani Express", "08:00 PM"},
        {"Delhi", "Mumbai", "Garib Rath", "09:00 PM"},
        {"Chennai", "Bangalore", "Shatabdi Express", "06:00 AM"},
        {"Bangalore", "Chennai", "Intercity Express", "07:00 AM"},
        {"Hyderabad", "Mumbai", "Hussain Sagar", "11:00 PM"},
        {"Mumbai", "Hyderabad", "Konark Express", "10:00 PM"},
        {"Nagpur", "Pune", "Vidarbha Express", "03:00 PM"},
        {"Pune", "Nagpur", "Azad Hind Express", "02:00 PM"},
        {"Kolkata", "Delhi", "Howrah Rajdhani", "05:00 PM"},
        {"Delhi", "Kolkata", "Poorva Express", "06:00 PM"},
        {"Goa", "Mumbai", "Mandovi Express", "08:00 AM"},
        {"Mumbai", "Goa", "Tejas Express", "09:00 AM"},
        {"Ahmedabad", "Mumbai", "Gujarat Express", "01:00 PM"},
        {"Mumbai", "Ahmedabad", "Shatabdi Express", "02:00 PM"},
        {"Pune", "Bangalore", "Udyan Express", "10:00 PM"},
        {"Bangalore", "Pune", "Sanghamitra Express", "09:00 PM"}

    };

    char from[50], to[50], date[20];
    char username[20], password[20];

    int classChoice, passengers;
    int userID;

    int i;
    int found = 0;
    int selectedTrain;

    int price[] = {2000, 1500, 800, 300};

    printf("\n========== RAILWAY BOOKING SYSTEM ==========\n");

    printf("\nEnter From Station: ");
    scanf("%s", from);

    printf("Enter To Station: ");
    scanf("%s", to);

    printf("Enter Journey Date: ");
    scanf("%s", date);

    // SHOW TRAINS AFTER DATE INPUT
    printf("\n========== AVAILABLE TRAINS ==========\n");

    for(i = 0; i < 20; i++) {

        if(stricmp(from, trains[i].from) == 0 &&
           stricmp(to, trains[i].to) == 0) {

            printf("\nTrain Number : %d", i);

            printf("\nTrain Name   : %s",
                   trains[i].name);

            printf("\nDeparture    : %s\n",
                   trains[i].time);

            found = 1;
        }
    }

    // IF NO TRAIN FOUND
    if(found == 0) {

        printf("\nNo trains available for this route.\n");

        return 0;
    }

    printf("\nSelect Train Number: ");
    scanf("%d", &selectedTrain);

    printf("\n========== LOGIN ==========\n");

    printf("Enter Username: ");
    scanf("%s", username);

    printf("Enter Password: ");
    scanf("%s", password);

    srand(time(0));

    userID = rand() % 9000 + 1000;

    printf("\nLogin Successful!\n");

    printf("Generated User ID: %d\n", userID);

    printf("\n========== CLASS OPTIONS ==========\n");

    printf("1. AC First Class\n");
    printf("2. AC 2 Tier\n");
    printf("3. Sleeper\n");
    printf("4. General\n");

    printf("\nEnter Class Choice: ");
    scanf("%d", &classChoice);

    printf("Enter Number of Passengers: ");
    scanf("%d", &passengers);

    int total = price[classChoice - 1] * passengers;

    printf("\nProcessing Payment...\n");

    printf("Payment Successful!\n");

    printf("\n========== BOOKED TICKET ==========\n");

    printf("User ID        : %d\n", userID);

    printf("From           : %s\n", from);

    printf("To             : %s\n", to);

    printf("Journey Date   : %s\n", date);

    printf("Train Name     : %s\n",
           trains[selectedTrain].name);

    printf("Departure Time : %s\n",
           trains[selectedTrain].time);

    printf("Passengers     : %d\n", passengers);

    printf("Total Fare     : Rs.%d\n", total);

    printf("\nPowered By RailYatri\n");

    return 0;
}
