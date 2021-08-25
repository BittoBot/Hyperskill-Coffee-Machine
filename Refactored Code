package machine;
import java.util.Scanner;

public class CoffeeMachine {
    static int waterInMachine = 400;
    static int milkInMachine = 540;
    static int beansInMachine = 120;
    static int disposableCups = 9;
    static int cashInMachine = 550;
    static int currentFill = 0;
    final static String enoughResourcesMsg = "I have enough resources, making you a coffee!";
    final static String notEnoughResourcesMsg = "Sorry, not enough ";
    static machineStates currentState = machineStates.WRITE_ACTION;
    static coffeeTypes coffee;


    void buy(String inp) {
        if (inp.equals("back")) {
            currentState = machineStates.WRITE_ACTION;
            return;
        } else {
            coffee = inp.equals("1") ? coffeeTypes.ESPRESSO : inp.equals("2") ? coffeeTypes.LATTE : coffeeTypes.CAPPUCCINO;
            switch (coffee) {
                case ESPRESSO:
                    if (waterInMachine >= 250 && beansInMachine >= 16) {
                        waterInMachine -= 250;
                        beansInMachine -= 16;
                        disposableCups--;
                        cashInMachine += 4;
                        System.out.println(enoughResourcesMsg);
                    } else if (waterInMachine < 250) {
                        System.out.println(notEnoughResourcesMsg + "water!");
                    } else if (beansInMachine < 16) {
                        System.out.println(notEnoughResourcesMsg + "coffee beans!");
                    }
                    break;
                case LATTE:
                    if (waterInMachine >= 350 && milkInMachine >= 75 && beansInMachine >= 20) {
                        waterInMachine -= 350;
                        milkInMachine -= 75;
                        beansInMachine -= 20;
                        disposableCups--;
                        cashInMachine += 7;
                        System.out.println(enoughResourcesMsg);
                    } else if (waterInMachine < 350) {
                        System.out.println(notEnoughResourcesMsg + "water!");
                    } else if (milkInMachine < 75) {
                        System.out.println(notEnoughResourcesMsg + "milk!");
                    } else if (beansInMachine < 20) {
                        System.out.println(notEnoughResourcesMsg + "coffee beans!");
                    }
                    break;
                case CAPPUCCINO:
                    if (waterInMachine >= 200 && milkInMachine >= 100 && beansInMachine >= 12) {
                        waterInMachine -= 200;
                        milkInMachine -= 100;
                        beansInMachine -= 12;
                        disposableCups--;
                        cashInMachine += 6;
                        System.out.println(enoughResourcesMsg);

                    } else if (waterInMachine < 200) {
                        System.out.println(notEnoughResourcesMsg + "water!");
                    } else if (milkInMachine < 100) {
                        System.out.println(notEnoughResourcesMsg + "milk!");
                    } else if (beansInMachine < 12) {
                        System.out.println(notEnoughResourcesMsg + "coffee beans!");
                    }
                    break;
            }
        }
        currentState = machineStates.WRITE_ACTION;
    }
    void fill(String input) {
        int numInput = Integer.parseInt(input);

        switch (currentFill) {
            case 1:
                waterInMachine += numInput;
                System.out.println("Write how many ml of milk you want to add:");
                break;
            case 2:
                milkInMachine += numInput;
                System.out.println("Write how many g of coffee beans you want to add:");
                break;
            case 3:
                beansInMachine += numInput;
                System.out.println("Write how many disposable cups you want to add:");
                break;
            case 4:
                disposableCups += numInput;
                currentFill = 0;
                currentState = machineStates.WRITE_ACTION;
                break;
        }
    }

    void take() {
        System.out.println("I gave you $" + cashInMachine);
        cashInMachine = 0;
        currentState = machineStates.WRITE_ACTION;
    }
    void remaining() {
        System.out.println("The coffee machine has:");
        System.out.printf("%d ml of water\n", waterInMachine);
        System.out.printf("%d ml of milk\n", milkInMachine);
        System.out.printf("%d g of coffee beans\n", beansInMachine);
        System.out.printf("%d disposable cups\n", disposableCups);
        System.out.printf("$%d of money\n", cashInMachine);
        currentState = machineStates.WRITE_ACTION;
    }


    public void inputReceiver(String input) {
        if (currentState == machineStates.BUY) {
            buy(input);
        }
        if (currentState == machineStates.FILL) {
            currentFill++;
            fill(input);
        }
        if (input.equals("buy")) {
            currentState = machineStates.BUY;
            System.out.println("What do you want to buy? 1 - espresso, 2 - latte, 3 - cappuccino, back - to main meu");
        } else if (input.equals("fill")) {
            System.out.println("Write how many ml of water you want to add:");
            currentState = machineStates.FILL;
        } else if (input.equals("take")) {
            currentState = machineStates.TAKE;
            take();
        } else if (input.equals("remaining")) {
            currentState = machineStates.REMAINING;
            remaining();
        }
    }
}

class Main {
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);

        CoffeeMachine cm = new CoffeeMachine();
        machineStates state;
        while (true) {
            state = CoffeeMachine.currentState;
            if (state == machineStates.WRITE_ACTION) {
                System.out.println("Write action (buy, fill, take, remaining, exit):");
            }
            String input = scanner.next();
            cm.inputReceiver(input);

            if (input.equals("exit")) {
                break;
            }
        }
    }
}
enum machineStates {
    WRITE_ACTION, BUY, FILL, TAKE, REMAINING
}
enum coffeeTypes {
    ESPRESSO, LATTE, CAPPUCCINO
}
