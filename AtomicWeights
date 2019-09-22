/**
 * @author Anik Barua
 * @since 5-10-2019
 * @version 1.0
 *
 * Description : This is my seventh java program. This program calculates the
 * the number of grams of 1 mole of a substance given its molecular formula.
 *
 * First this program scans the AtomicWeights file, gets the data and puts in
 * two different arrays - elements in element array and their weights in the
 * weight array. Then my bubbleSort method sorts my array alphabetically and
 * prints it out.
 *
 * After that it prompts the user to type the molecular formula and prints it
 * out both in the screens and in the output file. When the user types the
 * formula the main scans it and sends it to the numberOfGramsPerMole method.
 * The numberOfGramsPerMole method reads the string by each character and
 * whenever its detects a new element which is always in upper case, it does the
 * sum again and in the end it returns the total sum. After reading each element
 * it calls the findMassNumber method that scans the element array and returns
 * the index number of which array it is. After receiving the index number it
 * puts it in the weight array to get the weight and adds it to the sum. After
 * calculating the molar mass it returns to the main, and the main prints the
 * results out both in the output section and also in the output file.
 *
 */
package assignmentmolecularweight;

import java.util.Scanner;
import java.io.PrintStream;
import java.io.File;

public class AssignmentMolecularWeight {

    public static void main(String[] args) throws Exception {
        PrintStream ps = new PrintStream("output.txt");
        int count;
        final int MAXNUMBER = 118;
        String[] element = new String[MAXNUMBER];
        double[] weight = new double[MAXNUMBER];

        count = readPeriodicTable(element, weight);

        bubbleSort(element, weight, count);

        ps.printf("\n\tArrays - ");
        print(element, weight, ps);

        Scanner sc1 = new Scanner(System.in);
        System.out.println("Enter the molecular formula or Type 'stop' to end.");
        while (sc1.hasNext()) {
            String item = sc1.next();

            if (item.equalsIgnoreCase("stop")) {
                System.exit(0);
            }

            ps.printf("\n\n\tEnter the molecular formula: %s", item);
            double molecularWeight = numberOfGramsPerMole(element, weight, item);
            System.out.printf("The weight in grams of 1 mole of %s is %.3f.\n\n",
                    item, molecularWeight);
            ps.printf("\n\tThe weight in grams of 1 mole of %s is %.3f.\n\n",
                    item, molecularWeight);
            System.out.println("Enter the molecular formula or Type 'stop' to end.");
        }
    }

    // The readPeriodicTable method reads a string and a number at a time
    // and places it in next available slot of the each array and returns
    // the number of values that were read. 
    public static int readPeriodicTable(String[] element, double[] weight)
            throws Exception {
        
        Scanner sc = new Scanner(new File("AtomicWeights.txt"));
        int count = 0;
        while (sc.hasNext()) {
            element[count] = sc.next();
            weight[count] = sc.nextDouble();
            count++;
        }
        return count;
    }

    // This bubblesort method recives the two arrays (elements and weights)
    // and the count, and it sorts the array alphabeticaly.
    //
    public static void bubbleSort(String[] element, double[] weight, int n) {
        int pass, j;
        double hold;
        String temp;
        boolean switched = true;

        for (pass = 0; pass < n - 1 && switched; pass++) {
            switched = false;
            for (j = 0; j < n - pass - 1; j++) {
                if (element[j].compareToIgnoreCase(element[j + 1]) > 0) {
                    switched = true;
                    hold = weight[j];
                    weight[j] = weight[j + 1];
                    weight[j + 1] = hold;
                    temp = element[j];
                    element[j] = element[j + 1];
                    element[j + 1] = temp;
                }
            }
        }
    }

    // This method prints out the arrays. 
    public static void print(String[] element, double[] weight, PrintStream ps) {
        ps.println("\n\n\tElement\t\tWeight\n");
        for (int i = 0; i < 118; i++) {
            ps.printf("\t%s\t\t%.2f\n", element[i], weight[i]);
        }
    }

    // This numberOfGramsPerMole method recieves the two arrays (elements and weights) 
    // and the molecular formula as a parameter and returns the number of grams per mole.
    //
    public static double numberOfGramsPerMole(String[] element, double[] weight, String s){

        String e = s.concat("             ");
        double mass = 0, sum = 0, newMass;
        String x, y;

        for (int i = 0; i < s.length(); i++) {

            if (Character.isUpperCase(e.charAt(i)) && Character.isLowerCase(e.charAt(i + 1))
                    && Character.isDigit(e.charAt(i + 2)) 
                    && Character.isDigit(e.charAt(i + 3)) 
                    && Character.isWhitespace(e.charAt(i + 4))) {
                char c1 = e.charAt(i);
                char c2 = e.charAt(i + 1);
                char c3 = e.charAt(i + 2);
                char c4 = e.charAt(i + 3);

                x = "" + c1;
                y = x + c2;

                String digit = "" + c3 + c4;
                int z = Integer.parseInt(digit);

                mass = findMassNumber(element, weight, y);
                if (mass == -1) {
                    System.exit(0);
                }
                newMass = mass * z;
                sum += newMass;
            }

            if (Character.isUpperCase(e.charAt(i)) && Character.isLowerCase(e.charAt(i + 1))
                    && Character.isDigit(e.charAt(i + 2)) 
                    && Character.isWhitespace(e.charAt(i + 3))) {
                char c1 = e.charAt(i);
                char c2 = e.charAt(i + 1);
                char c3 = e.charAt(i + 2);

                x = "" + c1 + c2;

                String digit = "" + c3;
                int z = Integer.parseInt(digit);

                mass = findMassNumber(element, weight, x);
                if (mass == -1) {
                    System.exit(0);
                }
                newMass = mass * z;
                sum += newMass;

            }

            if (Character.isUpperCase(e.charAt(i)) && Character.isDigit(e.charAt(i + 1))
                    && Character.isDigit(e.charAt(i + 2)) 
                    && Character.isWhitespace(e.charAt(i + 3))) {
                char c1 = e.charAt(i);
                char c2 = e.charAt(i + 1);
                char c3 = e.charAt(i + 2);

                x = "" + c1;

                String digit = "" + c2 + c3;
                int z = Integer.parseInt(digit);

                mass = findMassNumber(element, weight, x);
                if (mass == -1) {
                    System.exit(0);
                }
                newMass = mass * z;
                sum += newMass;
            }

            if (Character.isUpperCase(e.charAt(i)) && Character.isDigit(e.charAt(i + 1))
                    && Character.isWhitespace(e.charAt(i + 2))) {

                char c1 = e.charAt(i);
                char c2 = e.charAt(i + 1);

                x = "" + c1;

                String digit = "" + c2;
                int z = Integer.parseInt(digit);

                mass = findMassNumber(element, weight, x);
                if (mass == -1) {
                    System.exit(0);
                }
                newMass = mass * z;
                sum += newMass;
            }

            if (Character.isUpperCase(e.charAt(i)) && Character.isLowerCase(e.charAt(i + 1))
                    && Character.isWhitespace(e.charAt(i + 2))) {
                char c1 = e.charAt(i);
                char c2 = e.charAt(i + 1);

                x = "" + c1 + c2;

                mass = findMassNumber(element, weight, x);
                if (mass == -1) {
                    System.exit(0);
                }
                newMass = mass;
                sum += newMass;
            }

            if (Character.isUpperCase(e.charAt(i)) 
                    && Character.isWhitespace(e.charAt(i + 1))) {
                char c1 = e.charAt(i);

                x = "" + c1;
                y = x;

                mass = findMassNumber(element, weight, y);
                if (mass == -1) {
                    System.exit(0);
                }
                newMass = mass;
                sum += newMass;
            }

            if (Character.isUpperCase(e.charAt(i)) 
                    && Character.isUpperCase(e.charAt(i + 1))
                    && !Character.isLetterOrDigit(e.charAt(i + 2))) {
                char c1 = e.charAt(i);
                x = "" + c1;
                y = x;
                mass = findMassNumber(element, weight, y);
                if (mass == -1) {
                    System.exit(0);
                }
                newMass = mass;
                sum += newMass;
                continue;
            }

            if (Character.isUpperCase(e.charAt(i)) 
                    && Character.isUpperCase(e.charAt(i + 1))
                    && Character.isUpperCase(e.charAt(i + 2))) {
                char c1 = e.charAt(i);
                x = "" + c1;
                y = x;
                mass = findMassNumber(element, weight, y);
                if (mass == -1) {
                    System.exit(0);
                }
                newMass = mass;
                sum += newMass;

                char c2 = e.charAt(i + 1);
                String x1 = "" + c2;
                String y1 = x1;
                mass = findMassNumber(element, weight, y1);
                if (mass == -1) {
                    System.exit(0);
                }
                newMass = mass;
                sum += newMass;
                i++;
                continue;
            }

            if (Character.isUpperCase(e.charAt(i)) && Character.isDigit(e.charAt(i + 1))
                    && Character.isUpperCase(e.charAt(i + 2)) 
                    && Character.isWhitespace(e.charAt(i + 5))) {
                char c1 = e.charAt(i);
                char c2 = e.charAt(i + 1);

                x = "" + c1;

                String digit = "" + c2;
                int z = Integer.parseInt(digit);

                mass = findMassNumber(element, weight, x);
                if (mass == -1) {
                    System.exit(0);
                }
                newMass = mass * z;
                sum += newMass;
                i++;
                continue;
            }

            if (Character.isUpperCase(e.charAt(i)) && Character.isLowerCase(e.charAt(i + 1))
                    && Character.isUpperCase(e.charAt(i + 2))) {
                char c1 = e.charAt(i);
                char c2 = e.charAt(i + 1);

                x = "" + c1 + c2;
                mass = findMassNumber(element, weight, x);
                if (mass == -1) {
                    System.exit(0);
                }
                newMass = mass;
                sum += newMass;
                i++;
                continue;
            }

            if (Character.isUpperCase(e.charAt(i)) && Character.isUpperCase(e.charAt(i + 1))
                    && Character.isDigit(e.charAt(i + 2))) {
                char c1 = e.charAt(i);
                x = "" + c1;
                y = x;
                mass = findMassNumber(element, weight, y);
                if (mass == -1) {
                    System.exit(0);
                }
                newMass = mass;
                sum += newMass;
                continue;
            }
            
            if (Character.isUpperCase(e.charAt(i)) && Character.isUpperCase(e.charAt(i + 1))
                    && Character.isUpperCase(e.charAt(i + 2))) {
                char c1 = e.charAt(i);
                char c2 = e.charAt (i+1);
                x = "" + c1;
                y = x;
                mass = findMassNumber(element, weight, y);
                if (mass == -1) {
                    System.exit(0);
                }
                newMass = mass;
                sum += newMass;
                
                x = "" + c2;
                String y1 = x;
                mass = findMassNumber(element, weight, y1);
                if (mass == -1) {
                    System.exit(0);
                }
                newMass = mass;
                sum += newMass;
                continue;
                
            }

            if (Character.isUpperCase(e.charAt(i)) && Character.isUpperCase(e.charAt(i + 1))
                    && Character.isLowerCase(e.charAt(i + 2)) 
                    && Character.isDigit(e.charAt(i + 3))) {
                char c1 = e.charAt(i);
                x = "" + c1;
                y = x;
                mass = findMassNumber(element, weight, y);
                if (mass == -1) {
                    System.exit(0);
                }
                newMass = mass;
                sum += newMass;
                continue;
            }

            if (Character.isUpperCase(e.charAt(i)) && Character.isUpperCase(e.charAt(i + 1))
                    && Character.isLowerCase(e.charAt(i + 2)) 
                    && Character.isUpperCase(e.charAt(i + 3))) {
                char c1 = e.charAt(i);
                x = "" + c1;
                y = x;
                mass = findMassNumber(element, weight, y);
                if (mass == -1) {
                    System.exit(0);
                }
                newMass = mass;
                sum += newMass;

                char c2 = e.charAt(i + 1);
                char c3 = e.charAt(i + 2);

                String x1 = "" + c2 + c3;
                String y1 = x1;
                mass = findMassNumber(element, weight, y1);
                if (mass == -1) {
                    System.exit(0);
                }
                newMass = mass;
                sum += newMass;
                i += 2;
                continue;
            }

            if (Character.isUpperCase(e.charAt(i)) && Character.isUpperCase(e.charAt(i + 1))
                    && Character.isLowerCase(e.charAt(i + 2)) 
                    && Character.isWhitespace(e.charAt(i + 3))) {
                char c1 = e.charAt(i);
                x = "" + c1;
                y = x;
                mass = findMassNumber(element, weight, y);
                if (mass == -1) {
                    System.exit(0);
                }
                newMass = mass;
                sum += newMass;

                char c2 = e.charAt(i + 1);
                char c3 = e.charAt(i + 2);

                String x1 = "" + c2 + c3;
                String y1 = x1;
                mass = findMassNumber(element, weight, y1);
                if (mass == -1) {
                    System.exit(0);
                }
                newMass = mass;
                sum += newMass;
                i += 2;
                continue;
            }

            if (Character.isUpperCase(e.charAt(i)) && Character.isLowerCase(e.charAt(i + 1))
                    && Character.isDigit(e.charAt(i + 2)) 
                    && Character.isUpperCase(e.charAt(i + 3))) {
                char c1 = e.charAt(i);
                char c2 = e.charAt(i + 1);
                char c3 = e.charAt(i + 2);

                x = "" + c1 + c2;

                String digit = "" + c3;
                int z = Integer.parseInt(digit);

                mass = findMassNumber(element, weight, x);
                if (mass == -1) {
                    System.exit(0);
                }
                newMass = mass * z;
                sum += newMass;
                i += 2;
                continue;
            }

            if (Character.isUpperCase(e.charAt(i)) && Character.isDigit(e.charAt(i + 1))
                    && Character.isDigit(e.charAt(i + 2)) 
                    && Character.isUpperCase(e.charAt(i + 3))) {
                char c1 = e.charAt(i);
                char c2 = e.charAt(i + 1);
                char c3 = e.charAt(i + 2);

                x = "" + c1;

                String digit = "" + c2 + c3;
                int z = Integer.parseInt(digit);

                mass = findMassNumber(element, weight, x);
                if (mass == -1) {
                    System.exit(0);
                }
                newMass = mass * z;
                sum += newMass;
                i += 2;
                continue;
            }

            if (Character.isUpperCase(e.charAt(i)) && Character.isLowerCase(e.charAt(i + 1))
                    && Character.isDigit(e.charAt(i + 2)) 
                    && Character.isDigit(e.charAt(i + 3))
                    && Character.isUpperCase(e.charAt(i + 4))) {
                char c1 = e.charAt(i);
                char c2 = e.charAt(i + 1);
                char c3 = e.charAt(i + 2);
                char c4 = e.charAt(i + 3);

                x = "" + c1 + c2;

                String digit = "" + c3 + c4;
                int z = Integer.parseInt(digit);

                mass = findMassNumber(element, weight, x);
                if (mass == -1) {
                    System.exit(0);
                }
                newMass = mass * z;
                sum += newMass;
                i += 3;
                continue;
            }

            if (Character.isUpperCase(e.charAt(i)) && Character.isDigit(e.charAt(i + 1))
                    && Character.isUpperCase(e.charAt(i + 2)) 
                    && Character.isDigit(e.charAt(i + 3))
                    && Character.isDigit(e.charAt(i + 4)) 
                    && Character.isUpperCase(e.charAt(i + 5))) {

                char c1 = e.charAt(i);
                char c2 = e.charAt(i + 1);
                x = "" + c1;
                String digit = "" + c2;
                int z = Integer.parseInt(digit);
                mass = findMassNumber(element, weight, x);
                if (mass == -1) {
                    System.exit(0);
                }
                newMass = mass * z;
                sum += newMass;

                char c3 = e.charAt(i + 2);
                char c4 = e.charAt(i + 3);
                char c5 = e.charAt(i + 4);
                String x1 = "" + c3;
                String digit1 = "" + c4 + c5;
                int z1 = Integer.parseInt(digit1);
                mass = findMassNumber(element, weight, x1);
                if (mass == -1) {
                    System.exit(0);
                }
                newMass = mass * z1;
                sum += newMass;
                i += 4;
                continue;
            }
            break;
        }
        if (sum == 0) {
            System.exit(0);
        }
        return sum;
    }

    // The method findMassNumber receives the elements and the weights array and a 
    // symbol of an element as a parameter and returns the weight of the element 
    // by searching the arrays. Also, if the element is not array, it prints out
    // an error message that returns a value -1 and after the numberOfGramsPerMole
    // recieves it, it will abort the program. 
    //
    public static double findMassNumber(String[] element, double[] weight, String item) {
        int i;
        for (i = 0; i < element.length; i++) {
            if (element[i].equals(item)) {
                return weight[i];
            }
        }
        System.out.print("Can't find the element!! \n");
        return -1;
    }
}
