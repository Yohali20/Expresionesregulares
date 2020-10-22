# Expresionesregulares

## CP #15dfg
0[1-9][0-9]{3}|[1-4][0-9]{4}|5[0-2][0-9]{3}

## Correo institucional # l151190020@milpaalta2.tecnm.mx
package ejemplo1;
import java.util.Scanner;
import java.util.regex.Matcher;
import java.util.regex.Pattern;

public class Ejemplo1 {

    public static void main(String[] args) {                                                                      
 
       Scanner sc = new Scanner(System.in);
       String email;
       System.out.print("Introduce email: ");
       email = sc.nextLine();
       Pattern pat = Pattern.compile("^[\\w-]+(\\.[\\w-]+)*@[A-Za-z0-9]+(\\.[A-Za-z0-9]+)*(\\.[A-Za-z]{2,})$");   
       Matcher mat = pat.matcher(email);
       if(mat.find()){
          System.out.println("Correo Válido");
       }else{
          System.out.println("Correo No Válido");
     }
   }
}

## Correo externo  # l151190020@google.com
String email = "[^@]+@[^@]+\\.[a-zA-Z]{2,}";

// Lo siguiente devuelve true
System.out.println(Pattern.matches(email, "a@b.com"));
System.out.println(Pattern.matches(email, "+++@+++.com"));

// Lo siguiente devuelve faslse
System.out.println(Pattern.matches(email, "@b.com")); // Falta el nombre
System.out.println(Pattern.matches(email, "a@b.c")); // El dominio final debe tener al menos dos letras


## Fecha (YYYY/mm/dd) 

String date = "\\d{1,2}/\\d{1,2}/\\d{4}";

// Lo siguiente devuelve true
System.out.println(Pattern.matches(date, "11/12/2014"));
System.out.println(Pattern.matches(date, "1/12/2014"));
System.out.println(Pattern.matches(date, "11/2/2014"));


// Los siguientes devuelven false
System.out.println(Pattern.matches(date, "11/12/14"));  // El año no tiene cuatro cifras
System.out.println(Pattern.matches(date, "11//2014"));  // el mes no tiene una o dos cifras
System.out.println(Pattern.matches(date, "11/12/14perico"));  // Sobra "perico"

## No. Control Institucional  l151190020
String numcontrol = "\\d{8}[A-HJ-NP-TV-Z]";

// Lo siguiente devuelve true
System.out.println(Pattern.matches(numcontrol, "012345678"));

//Lo siguiente devuelve false
System.out.println(Pattern.matches(numcontrol, "01234567U")); // La U no es válida
System.out.println(Pattern.matches(numcontrol, "0123567X")); // No tiene 8 cifras