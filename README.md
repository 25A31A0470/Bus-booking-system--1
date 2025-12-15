#include <stdio.h>

#define MAX 40

int main() {

    int seat[MAX] = {0};   // 0 = free, 1 = booked
    int choice, s;

    while(1) {

        printf("\n===== BUS TICKET BOOKING SYSTEM =====\n");
        printf("1. Book Ticket\n");
        printf("2. Cancel Ticket\n");
        printf("3. Check Bus Status\n");
        printf("0. Exit\n");
        printf("Enter your choice: ");
        scanf("%d", &choice);

        switch(choice) {

            case 1:
                printf("Enter seat number to book (1-40): ");
                scanf("%d", &s);

                if(s < 1 || s > 40)
                    printf("Invalid seat number!\n");
                else if(seat[s-1] == 1)
                    printf("Seat already booked!\n");
                else {
                    seat[s-1] = 1;
                    printf("Seat booked successfully!\n");
                }
                break;

            case 2:
                printf("Enter seat number to cancel (1-40): ");
                scanf("%d", &s);

                if(s < 1 || s > 40)
                    printf("Invalid seat number!\n");
                else if(seat[s-1] == 0)
                    printf("Seat is not booked!\n");
                else {
                    seat[s-1] = 0;
                    printf("Seat cancelled successfully!\n");
                }
                break;

            case 3:
                printf("\nBus Seat Status:\n");
                for(int i = 0; i < 40; i++) {
                    if(seat[i] == 0)
                        printf("Seat %d : Free\n", i+1);
                    else
                        printf("Seat %d : Booked\n", i+1);
                }
                break;

            case 0:
                printf("Thank you! Visit again.\n");
                return 0;

            default:
                printf("Invalid choice! Try again.\n");
        }
    }
}
