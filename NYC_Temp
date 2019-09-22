/**
 * @author Anik Barua
 * @since 5-2-2019
 * @version 1.0
 *
 * Description : This is my sixth Java program. This program analyzes the data
 * of the rise in temperature over the last 200 years. First it takes the
 * February, August and Annual average temperatures data and finds out the
 * largest temperature and lowest temperature for each, in the entire period
 * 1869-2017. Also, it gives the mean, median, mode and the standard deviation
 * of the temperatures for each. Then it gives the slope,m and y-intercept,b
 * value for the line of best fit equation, y = m(x)+b. After that, it plots the
 * years and temperatures for February, August and Annual average temperature
 * and draws the line of best fit for all of them in a graph.
 *
 * First this program scans the NYCtemperature file, gets the data, puts them in
 * 4 different arrays and prints out each array. Then it sends 2 arrays at a
 * time (years and the 3 different months) to each method - largest, lowest,
 * mean, mode, median, and standard deviation and reports them. That was part 1.
 *
 * For part 2, it finds the line of best fit. For that first, for each (x,y), x
 * is the years and y is temperatures, it calculates x^2 and xy, for all the
 * temperatures in February, August and Annual with the proper years. After that
 * additionInt and additionDouble method sums all x, y, x^2 and xy. After that
 * using the slope formula it finds out m. Then using the intercept b formula,
 * it calculates b. Now we have m and b for February, August and Annual. Then it
 * assembles the equation of line, y = m(x) +b with the values of m and b for
 * each of them.
 *
 * For part 3, it graphs all the data in arrays for February, August, and Annual
 * and draws the line of best fit line using the y = m(x) +b, that I found in
 * part 2. I used the stdLibray to draw the graph and to give labels to it. All
 * the output goes to "results.txt" file.
 *
 */
package assingmentnyctemperature;

import java.io.File;
import java.util.Scanner;
import java.io.PrintStream;
import java.util.Arrays;
import edu.princeton.cs.introcs.*;

public class AssingmentNYCTemperature {

    public static void main(String[] args) throws Exception {
        PrintStream ps = new PrintStream("results.txt");

        int count;
        final int MAXNUMBER = 149;
        double highestFeb, highestAug, highestAnnual;
        double lowestFeb, lowestAug, lowestAnnual;
        double meanFeb, meanAug, meanAnnual;
        double medianFeb, medianAug, medianAnnual;
        double modeFeb, modeAug, modeAnnual;
        double sdFeb, sdAug, sdAnnual;

        double y1feb, y2feb;
        double y1aug, y2aug;
        double y1annual, y2annual;
        Scanner sc1 = new Scanner(System.in);

        int[] year = new int[MAXNUMBER];
        double[] february = new double[MAXNUMBER];
        double[] august = new double[MAXNUMBER];
        double[] annual = new double[MAXNUMBER];

        count = populateArray(year, february, august, annual);

        highestFeb = findLargest(february, count);
        lowestFeb = findLowest(february, count);
        meanFeb = mean(february, count);
        medianFeb = median(february, count);
        modeFeb = mode(february, count);
        sdFeb = StandardDeviation(february, count);

        highestAug = findLargest(august, count);
        lowestAug = findLowest(august, count);
        meanAug = mean(august, count);
        medianAug = median(august, count);
        modeAug = mode(august, count);
        sdAug = StandardDeviation(august, count);

        highestAnnual = findLargest(annual, count);
        lowestAnnual = findLowest(annual, count);
        meanAnnual = mean(annual, count);
        medianAnnual = median(annual, count);
        modeAnnual = mode(annual, count);
        sdAnnual = StandardDeviation(annual, count);

        ps.printf("\n\tPrint Number 1 - ");     // prints the arrays.
        print(year, february, august, annual, ps);

        ps.printf("\n\n\n\tThe highest temperature for February is %.1f\n", highestFeb);
        ps.printf("\tThe lowest temperature for February is %.1f\n", lowestFeb);

        ps.printf("\n\tThe highest temperature for August is %.1f\n", highestAug);
        ps.printf("\tThe lowest temperature for August is %.1f\n", lowestAug);

        ps.printf("\n\tThe highest temperature for Annual is %.1f\n", highestAnnual);
        ps.printf("\tThe lowest temperature for Annual is %.1f\n", lowestAnnual);

        ps.printf("\n\n\n\tThe Mean temperature for February is %.2f\n", meanFeb);
        ps.printf("\tThe Median temperature for February is %.1f\n", medianFeb);
        ps.printf("\tThe Mode temperature for February is %.1f\n", modeFeb);
        ps.printf("\tThe Standard Deviation of temperature for February is %.4f\n", sdFeb);

        ps.printf("\n\n\n\tThe Mean temperature for august is %.2f\n", meanAug);
        ps.printf("\tThe Median temperature for august is %.1f\n", medianAug);
        ps.printf("\tThe Mode temperature for august is %.1f\n", modeAug);
        ps.printf("\tThe Standard Deviation of temperature for august is %.4f\n", sdAug);

        ps.printf("\n\n\n\tThe Mean temperature for annual is %.2f\n", meanAnnual);
        ps.printf("\tThe Median temperature for annual is %.1f\n", medianAnnual);
        ps.printf("\tThe Mode temperature for annual is %.1f\n", modeAnnual);
        ps.printf("\tThe Standard Deviation of temperature for annual is %.4f\n", sdAnnual);

        ps.printf("\n\n\n\tPrint Number 2 - ");   //prints the arrays for the second time.
        print(year, february, august, annual, ps);

        double[] xyValue = xy(year, february);
        double[] xSquareValue = xSquare(year);

        double sumX = additionInt(year);
        double sumY = additionDouble(february);
        double sumXY = additionDouble(xyValue);
        double sumXsquare = additionDouble(xSquareValue);

        double slopeValue = slope(sumX, sumY, sumXY, sumXsquare, count);
        double valueOfb = bValue(sumX, sumY, slopeValue, count);
        ps.printf("\n\n\n\tThe m value for February is %.4f\n", slopeValue);
        ps.printf("\tThe b value for February is %.4f\n", valueOfb);
        ps.printf("\tThe formula for February is, Y = %.4fx %.4f\n", slopeValue, valueOfb);

        double[] xyValue2 = xy(year, august);
        double[] xSquareValue2 = xSquare(year);

        double sumX2 = additionInt(year);
        double sumY2 = additionDouble(august);
        double sumXY2 = additionDouble(xyValue2);
        double sumXsquare2 = additionDouble(xSquareValue2);

        double slopeValue2 = slope(sumX2, sumY2, sumXY2, sumXsquare2, count);
        double valueOfb2 = bValue(sumX2, sumY2, slopeValue2, count);
        ps.printf("\n\tThe m value for August is %.4f\n", slopeValue2);
        ps.printf("\tThe b value for August is %.4f\n", valueOfb2);
        ps.printf("\tThe formula for August is, Y = %.4fx +%.4f\n", slopeValue2, valueOfb2);

        double[] xyValue3 = xy(year, annual);
        double[] xSquareValue3 = xSquare(year);

        double sumX3 = additionInt(year);
        double sumY3 = additionDouble(annual);
        double sumXY3 = additionDouble(xyValue3);
        double sumXsquare3 = additionDouble(xSquareValue3);

        double slopeValue3 = slope(sumX3, sumY3, sumXY3, sumXsquare3, count);
        double valueOfb3 = bValue(sumX3, sumY3, slopeValue3, count);
        ps.printf("\n\tThe m value for Annual is %.4f\n", slopeValue3);
        ps.printf("\tThe b value for Annual is %.4f\n", valueOfb3);
        ps.printf("\tThe formula for Annual is, Y = %.4fx %.4f\n", slopeValue3, valueOfb3);

        drawGrid(1800, 2040, 602, 12);            // draws the grid.
        double valueOfX, valueOfY, valueOfY2, valueOfY3;

        for (int k = 0; k <= 100; k += 1) {     
            valueOfX = year[k];
            valueOfY = february[k];
            StdDraw.setPenColor(StdDraw.MAGENTA);
            StdDraw.setPenRadius(.01);
            StdDraw.point(valueOfX, valueOfY);

            StdDraw.setPenColor(StdDraw.BLUE);
            StdDraw.setPenRadius(.005);
            y1feb = yValue(1800, slopeValue, valueOfb);
            y2feb = yValue(2040, slopeValue, valueOfb);
            StdDraw.line(1800, y1feb, 2040, y2feb);    // draws line of best fit for feb.

            valueOfY2 = august[k];
            StdDraw.setPenColor(StdDraw.RED);
            StdDraw.setPenRadius(.01);
            StdDraw.point(valueOfX, valueOfY2);

            StdDraw.setPenColor(StdDraw.ORANGE);
            StdDraw.setPenRadius(.005);
            y1aug = yValue(1800, slopeValue2, valueOfb2);
            y2aug = yValue(2040, slopeValue2, valueOfb2);
            StdDraw.line(1800, y1aug, 2040, y2aug);     // draws line of best fit for aug.

            valueOfY3 = annual[k];
            StdDraw.setPenColor(StdDraw.BLUE);
            StdDraw.setPenRadius(.01);
            StdDraw.point(valueOfX, valueOfY3);

            StdDraw.setPenColor(StdDraw.RED);
            StdDraw.setPenRadius(.005);
            y1annual = yValue(1800, slopeValue3, valueOfb3);
            y2annual = yValue(2040, slopeValue3, valueOfb3);
            StdDraw.line(1800, y1annual, 2040, y2annual);
                                              //draws line of best fit for annual average.
        }

        System.out.println("Type 0 and press enter to close the graph.");
        int x;
        x = sc1.nextInt();
        if (x == 0) {
            System.exit(0);
        }
    }

    // This method finds the largest element in the array.
    public static double findLargest(double[] x, int n) {
        double largest;
        int i;
        largest = x[0];
        for (i = 1; i < n; i++) {
            if (x[i] > largest) {
                largest = x[i];
            }
        }
        return largest;
    }

    // This method finds the lowest element in the array.
    public static double findLowest(double[] y, int n) {
        double lowest;
        int i;
        lowest = y[0];
        for (i = 1; i < n; i++) {
            if (y[i] < lowest) {
                lowest = y[i];
            }
        }
        return lowest;
    }

    // This method prints out the arrays. 
    public static void print(int[] year, double[] february, double[] august,
            double[] annual, PrintStream ps) {
        ps.printf("\n\n\tY̲E̲A̲R̲\t F̲E̲B̲\t  A̲U̲G̲\t    A̲N̲N̲U̲A̲L̲\n\n", "Year", "Feb", "Aug",
                "Annual");
        for (int i = 0; i < 149; i++) {
            ps.format("\t%2d\t%5.1f\t%6.1f\t%8.1f\n", year[i], february[i],
                    august[i], annual[i]);
        }
    }

    // The populateArray method reads a number at a time and places it in next
    // available slot of the each array and returns the number of values that were read. 
    public static int populateArray(int[] year, double[] feb, double[] aug, double[] annual)
            throws Exception {

        Scanner sc = new Scanner(new File("NYCTemperatureData.txt"));
        int count = 0;
        String x;
        x = sc.nextLine();
        while (sc.hasNext()) {
            year[count] = sc.nextInt();
            feb[count] = sc.nextDouble();
            aug[count] = sc.nextDouble();
            annual[count] = sc.nextDouble();
            count++;
        }
        return count;
    }

    // This method recives an array and the count, and it calculates the mean.
    public static double mean(double[] mean, int n) {
        double sum = 0;
        for (int i = 0; i < n; i++) {
            sum += mean[i];
        }
        return sum / n;
    }

    // This method recives an array and the count, and it finds out the median. 
    public static double median(double[] m, int n) {
        double[] b = Arrays.copyOf(m, n);
        sort(b, n);
        int middle = n / 2;
        if (n % 2 == 0) {
            return (b[middle - 1] + b[middle]) / 2.0;
        } else {
            return b[middle];
        }
    }

    // This sort method recives an array and the count, and it sorts the array. 
    public static void sort(double[] m, int n) {
        int pass, j;
        double hold;
        boolean switched = true;
        for (pass = 0; pass < n - 1 && switched; pass++) {
            switched = false;
            for (j = 0; j < n - pass - 1; j++) {
                if (m[j] > m[j + 1]) {
                    switched = true;
                    hold = m[j];
                    m[j] = m[j + 1];
                    m[j + 1] = hold;
                }
            }
        }
    }

    // This method recives an array and the count, and returns most repeated 
    // element in the array. If there is more than one mode value it will 
    // return their average.   
    public static double mode(double[] x, int n) {
        double[] a = Arrays.copyOf(x, n);
        sort(a, a.length);
        int count1 = 0;
        int count2 = 0;
        double maxValue1 = 0;
        double maxValue2 = 0;

        for (int i = 0; i < a.length; i++) {
            maxValue1 = a[i];
            count2 = 0;
            for (int j = i + 1; j < a.length; j++) {
                if (maxValue1 == a[j]) {
                    count2++;
                }
            }
            if (count2 > count1) {
                maxValue2 = maxValue1;
                count1 = count2;
            } else if (count2 == count1) {
                maxValue2 = (maxValue2 + maxValue1) / 2;
            }
        }
        return maxValue2;
    }

    // This method recives an array and the count, and returns the standard deviation of the 
    // elements in the array. 
    public static double StandardDeviation(double[] data, int n) {
        final double mean1 = mean(data, n);
        double sum = 0;
        for (int i = 0; i < n; i++) {
            sum += Math.pow((data[i] - mean1), 2);
        }
        return Math.sqrt(sum / n);
    }

    // This method recives two arrays, multiplyies the two elements of the same slot
    // and puts them in a new array. 
    public static double[] xy(int[] x, double[] y) {
        double[] result = new double[x.length];
        for (int i = 0; i < x.length; i++) {
            result[i] = x[i] * y[i];
        }
        return result;
    }

    // This method recives an array, finds the square of the elements and puts them 
    // in a new array. 
    public static double[] xSquare(int[] x) {
        double[] result2 = new double[x.length];
        for (int i = 0; i < x.length; i++) {
            result2[i] = Math.pow(x[i], 2);
        }
        return result2;
    }

    // The additionInt method recives an integer array and calculates the sum of all 
    // the elements in that array. 
    public static double additionInt(int[] x) {
        double sum = 0;
        for (int i = 0; i < x.length; i++) {
            sum = sum + x[i];
        }
        return sum;
    }

    // The additionDouble method recives an double array and calculates the sum of all 
    // the elements in that array.  
    public static double additionDouble(double[] x) {
        double sum = 0;
        for (int i = 0; i < x.length; i++) {
            sum = sum + x[i];
        }
        return sum;
    }

    // The slope method recives all the sum values of x, y, xy, and xSquare, and the total 
    // count and it calculates the slope using the formula.
    public static double slope(double x, double y, double xy, double xSquare, int N) {
        double m = ((N * xy) - (x * y)) / ((N * xSquare) - (Math.pow(x, 2)));
        return m;
    }

    // The bValue method recives all the sum values of x and y, the slope, and the total  
    // count, and it calculates the bValue using the formula.
    public static double bValue(double x, double y, double m, int N) {
        double b = (y - (m * x)) / N;
        return b;
    }

    // This method draws the grid and the lables for the graph.
    public static void drawGrid(int lower, int upper, int canvasSize, double increment) {
        StdDraw.setCanvasSize(canvasSize, canvasSize);
        StdDraw.setScale(lower, upper);

        for (double i = 0; i < upper - lower; i += increment) {
            StdDraw.line(lower, upper - i, upper, upper - i);
            StdDraw.line(lower + i, upper, lower + i, lower);
        }
        StdDraw.setXscale(1800, 2040);
        StdDraw.setYscale(0, 100);
        StdDraw.setPenRadius(0.01);
        StdDraw.line(lower, 0, upper, 0);
        StdDraw.line(1801, 0, 1801, 2040);

        StdDraw.setPenColor(StdDraw.DARK_GRAY);
        StdDraw.textLeft(1801, 3, "1800");
        StdDraw.textLeft(2024, 3, "2040");
        StdDraw.textLeft(1801, 98, "100");
        StdDraw.setPenColor(StdDraw.BLUE);
        StdDraw.textLeft(1802, 93, "Temperatures (Y-axis)");
        StdDraw.setPenColor(StdDraw.RED);
        StdDraw.textLeft(1900, 3, "Years (X-axis)");
        StdDraw.setPenColor(StdDraw.BLUE);
        StdDraw.textRight(1960, 47, "Annaul Average (Y = 0.0291x -2.5616)");
        StdDraw.setPenColor(StdDraw.RED);
        StdDraw.textRight(1960, 65, "August (Y = 0.0247x +26.6422)");
        StdDraw.setPenColor(StdDraw.MAGENTA);
        StdDraw.textRight(1960, 18, "February (Y = 0.0393x -43.5131)");
    }

    // This method assembles the slope, x and the b value and calcutes for y 
    // using y =mx + b formula. 
    public static double yValue(double x, double m, double b) {
        double y;
        y = (m * x) + b;
        return y;
    }
}  // end class AssingmentNYCTemperature
