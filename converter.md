// Distanc and currency convertor

class CurrencyConverter {

    double dollarToRupee(double dollar) {
        return dollar * 83;
    }

    double rupeeToDollar(double rupee) {
        return rupee / 83;
    }
}

class DistanceConverter {

    double kmToMiles(double km) {
        return km * 0.621;
    }

    double milesToKm(double miles) {
        return miles * 1.609;
    }
}

class TimeConverter {

    double hoursToMinutes(double hours) {
        return hours * 60;
    }

    double minutesToHours(double minutes) {
        return minutes / 60;
    }
}

public class MainProgram {

    public static void main(String[] args) {

        CurrencyConverter c = new CurrencyConverter();
        DistanceConverter d = new DistanceConverter();
        TimeConverter t = new TimeConverter();

        System.out.println("Currency Conversion");
        System.out.println("10 Dollars = " + c.dollarToRupee(10) + " Rupees");
        System.out.println("830 Rupees = " + c.rupeeToDollar(830) + " Dollars");

        System.out.println("\nDistance Conversion");
        System.out.println("5 KM = " + d.kmToMiles(5) + " Miles");
        System.out.println("3 Miles = " + d.milesToKm(3) + " KM");

        System.out.println("\nTime Conversion");
        System.out.println("2 Hours = " + t.hoursToMinutes(2) + " Minutes");
        System.out.println("120 Minutes = " + t.minutesToHours(120) + " Hours");
    }
}
