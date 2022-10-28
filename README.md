### Task №1(6kyu)
Write the following function:

~~~ Java
public static double areaOfPolygonInsideCircle(double circleRadius, int numberOfSides)
~~~

It should calculate the area of a regular polygon of , , or sides inside a circle of radius , , or which passes through all the vertices of the polygon (such circle is called circumscribed circle or circumcircle). The answer should be a number rounded to 3 decimal places. 
~~~ Java
numberOfSidesnumber-of-sidesnumber_of_sidescircleRadiuscircle-radiuscircle_radius
~~~

Input :: Output Examples
~~~ Java
areaOfPolygonInsideCircle(3, 3) // returns 11.691

areaOfPolygonInsideCircle(5.8, 7) // returns 92.053

areaOfPolygonInsideCircle(4, 5) // returns 38.042
~~~
Note: if you need to use Pi in your code, use the native value of your language unless stated otherwise.

[Task_link](https://www.codewars.com/kata/5a58ca28e626c55ae000018a)

#### Solution

~~~ Java

public class Kata {

    public static double areaOfPolygonInsideCircle(double circleRadius, int numberOfSides) {
        double S = circleRadius * circleRadius * numberOfSides * Math.sin(2 * Math.PI / numberOfSides) / 2;
        S = Math.round(S * 1000.0) / 1000.0;
        return S;
    }
}
~~~

#### Fav Solution

~~~ Java
class Kata {
  static double areaOfPolygonInsideCircle(double r, int n) {
    return Math.round(.5e3 * n * Math.pow(r, 2) * Math.sin(6.2831853 / n)) / 1.0e3;
  }
}
~~~


### Task №2(7kyu)

In a small town the population is at the beginning of a year. The population regularly increases by per year and moreover new inhabitants per year come to live in the town. How many years does the town need to see its population greater or equal to inhabitants?p0 = 10002 percent50p = 1200

~~~ Java
At the end of the first year there will be:
1000 + 1000 * 0.02 + 50 => 1070 inhabitants

At the end of the 2nd year there will be:
1070 + 1070 * 0.02 + 50 => 1141 inhabitants (** number of inhabitants is an integer **)

At the end of the 3rd year there will be:
1141 + 1141 * 0.02 + 50 => 1213

It will need 3 entire years.
~~~
More generally given parameters:

p0, percent, aug (inhabitants coming or leaving each year), p (population to equal or surpass)

the function should return number of entire years needed to get a population greater or equal to .nb_yearnp

aug is an integer, percent a positive or null floating number, p0 and p are positive integers (> 0)

~~~ Java
Examples:
nb_year(1500, 5, 100, 5000) -> 15
nb_year(1500000, 2.5, 10000, 2000000) -> 10
~~~
Note:
Don't forget to convert the percent parameter as a percentage in the body of your function: if the parameter percent is 2 you have to convert it to 0.02.

[Task_link](https://www.codewars.com/kata/563b662a59afc2b5120000c6)

#### Solution

~~~ Java
class Arge {
    public static int nbYear(int p0, double percent, int aug, int p) {
        int year = 0;
        while (p0 < p) {
            p0 = p0 + (int) (p0 * percent / 100) + aug;
            year++;
        }
        return year;
    }
}
~~~

#### Fav Solution

~~~ Java
class Arge {
  static int nbYear(int p0, double percent, int aug, int p) {
    return p0 < p ? nbYear((int) (p0 * (percent / 100 + 1) + aug), percent, aug, p) + 1 : 0;
  }
}
~~~
