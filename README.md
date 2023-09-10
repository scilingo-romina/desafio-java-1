# desafio-java-1


import java.util.Scanner;

public class ValidacionFecha {
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        
        System.out.print("Ingrese la fecha (dd/mm/yyyy): ");
        String fecha = scanner.nextLine();
        
     
        String[] partes = fecha.split("/");
        
        if (partes.length != 3) {
            System.out.println("Formato de fecha incorrecto. Debe ser dd/mm/yyyy");
        } else {
            try {
                int dia = Integer.parseInt(partes[0]);
                int mes = Integer.parseInt(partes[1]);
                int año = Integer.parseInt(partes[2]);
                
                if (validarFecha(dia, mes, año)) {
                    System.out.println("La fecha ingresada es válida.");
                } else {
                    System.out.println("La fecha ingresada no es válida.");
                }
            } catch (NumberFormatException e) {
                System.out.println("Formato de fecha incorrecto. Debe ser dd/mm/yyyy");
            }
        }
        
        scanner.close();
    }
    
    // Función para validar la fecha
    public static boolean validarFecha(int dia, int mes, int año) {
        if (año >= 1900 && año <= 2099) {
            if (mes >= 1 && mes <= 12) {
                if (mes == 2) { // Febrero
                    if ((año % 4 == 0 && año % 100 != 0) || año % 400 == 0) {
                        return (dia >= 1 && dia <= 29);
                    } else {
                        return (dia >= 1 && dia <= 28);
                    }
                } else if (mes == 4 || mes == 6 || mes == 9 || mes == 11) {
                    return (dia >= 1 && dia <= 30);
                } else {
                    return (dia >= 1 && dia <= 31);
                }
            }
        }
        return false;
    }
}
