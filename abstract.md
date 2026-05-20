//CREATION OF THE ABSTRACT CLASS

abstract class Shape {

    abstract void printArea();
}

class Rectangle extends Shape {

    int length, breadth;

    Rectangle(int l, int b) {
        length = l;
        breadth = b;
    }

    void printArea() {
        System.out.println("Area of Rectangle = " + (length * breadth));
    }
}

class Triangle extends Shape {

    int base, height;

    Triangle(int b, int h) {
        base = b;
        height = h;
    }

    void printArea() {
        System.out.println("Area of Triangle = " + (0.5 * base * height));
    }
}

class Circle extends Shape {

    int radius;

    Circle(int r) {
        radius = r;
    }

    void printArea() {
        System.out.println("Area of Circle = " + (3.14 * radius * radius));
    }
}

public class MainProgram {

    public static void main(String[] args) {

        Rectangle r = new Rectangle(10, 5);
        Triangle t = new Triangle(8, 6);
        Circle c = new Circle(7);

        r.printArea();
        t.printArea();
        c.printArea();
    }
}
