import java.util.Scanner;
public class Main {
    static Scanner sc = new Scanner(System.in);
    static String[] arrayRegaxActions = {"\\+", "-", "/", "\\*"," "};
    static String[] arrayActions = {"+", "-", "/", "*"};
    static int actionIndex = 4;

    public static String calc(String input) {
        input = input.replace(" ","");
        int a,b;
        int result;
        String output;
        for (int i = 0; i < arrayActions.length; i++) {
            if (input.contains(arrayActions[i])) {
                actionIndex = i;
                break;
            }
        }
        String[] data = input.split(arrayRegaxActions[actionIndex]);
        if (data.length == 1) {
            throw new RuntimeException("Так как строка не является математической операцией");
        } else if (data.length > 2) {
            throw new RuntimeException("Т.к. формат математической операции не удовлетворяет заданию - два операнда и один оператор (+, -, /, *)");
        }
        Converter2 converter = new Converter2();
        if (converter.isRoman(data[0]) && converter.isRoman(data[1])) {
            a = converter.toArabian(data[0]);
            b = converter.toArabian(data[1]);
                result = getResult(a,b);
                if (result<1) {
                    throw new RuntimeException("В римской системе счисления нет отрицательных чисел и нуля");}
                output = converter.convertToRoman(result);
        } else if (!converter.isRoman(data[0]) && !converter.isRoman(data[1])) {
            a = Integer.parseInt(data[0]);
            b = Integer.parseInt(data[1]);
                result = getResult(a,b);
                output = String.valueOf(result);
        } else throw new RuntimeException("Используются одновременно разные системы счисления");
        return output;
    }
    public static int getResult(int a,int b) {
        int result = 0;
        if (a > 10 || a < 0 && b < 0 || b > 10){
            throw new RuntimeException("числа должны быть целыми от 1 до 10 включительно");
        }
            switch (arrayActions[actionIndex]) {
                case "/" -> result = a / b;
                case "*" -> result = a * b;
                case "-" -> result = a - b;
                case "+" -> result = a + b;
            }
            return result;
    }

    public static void main (String[]args) {
        System.out.println("Введите выражение: ");
        String input = sc.nextLine();
        System.out.print("Результат : "+calc(input));
    }
}
class Converter2 {
    String[] romanArguments = {"O", "I", "II", "III", "IV", "V", "VI", "VII", "VIII", "IX", "X", "XI", "XII", "XIII", "XIV", "XV", "XVI", "XVII", "XVIII", "XIX", "XX",
            "XXI", "XXII", "XXIII", "XXIV", "XXV", "XXVI", "XXVII", "XXVIII", "XXIX", "XXX", "XXXI", "XXXII", "XXXIII", "XXXIV", "XXXV", "XXXVI", "XXXVII", "XXXVIII", "XXXIX", "XL",
            "XLI", "XLII", "XLIII", "XLIV", "XLV", "XLVI", "XLVII", "XLVIII", "XLIX", "L", "LI", "LII", "LIII", "LIV", "LV", "LVI", "LVII", "LVIII", "LIX", "LX",
            "LXI", "LXII", "LXIII", "LXIV", "LXV", "LXVI", "LXVII", "LXVIII", "LXIX", "LXX",
            "LXXI", "LXXII", "LXXIII", "LXXIV", "LXXV", "LXXVI", "LXXVII", "LXXVIII", "LXXIX", "LXXX",
            "LXXXI", "LXXXII", "LXXXIII", "LXXXIV", "LXXXV", "LXXXVI", "LXXXVII", "LXXXVIII", "LXXXIX", "XC",
            "XCI", "XCII", "XCIII", "XCIV", "XCV", "XCVI", "XCVII", "XCVIII", "XCIX", "C"};
    boolean isRoman(String value){
        for (String s : romanArguments) {
            if (value.equals(s)) {
                return true;}
        }
        return false;
    }
    int toArabian(String value){
        for (int i=0;i<romanArguments.length;i++){
            if (value.equals(romanArguments[i])){
                return i;
            }
        }return -1;
    }
    String convertToRoman(int arabian) {return romanArguments[arabian];}
}
