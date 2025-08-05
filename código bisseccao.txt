import java.util.Scanner;

public class Bisseccao {

    public static double f(double x) {
         return Math.pow(x, 3) - 9 * x + 3;
    }

    public static void bisseccao(double a, double b, double tol, int maxIter) {
        if (f(a) * f(b) >= 0) {
            System.out.println("A função deve ter sinais opostos em a e b.");
            return;
        }

        double c = a;
        int iter = 0;

        System.out.printf("%-10s%-15s%-15s%-15s%-15s\n", "Iteração", "a", "b", "c", "f(c)");
        while ((b - a) / 2 > tol && iter < maxIter) {
            c = (a + b) / 2;
            double fc = f(c);

            System.out.printf("%-10d%-15.8f%-15.8f%-15.8f%-15.8f\n", iter + 1, a, b, c, fc);

            if (fc == 0.0) break;

            if (f(a) * fc < 0) {
                b = c;
            } else {
                a = c;
            }

            iter++;
        }

        System.out.println("\nA raiz aproximada é: " + c);
        System.out.println("Número de iterações: " + iter);
    }

    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);

        System.out.print("Digite o valor de a: ");
        double a = scanner.nextDouble();
        scanner.nextLine(); // limpa o buffer

        System.out.print("Digite o valor de b: ");
        double b = scanner.nextDouble();
        scanner.nextLine(); // limpa o buffer

        System.out.print("Digite a tolerância (ex: 0,0001): ");
        double tolerancia = scanner.nextDouble();
        scanner.nextLine(); // limpa o buffer

        System.out.print("Digite o número máximo de iterações: ");
        int maxIteracoes = scanner.nextInt();
        scanner.nextLine(); // limpa o buffer

        bisseccao(a, b, tolerancia, maxIteracoes);

        scanner.close();
    }
}
