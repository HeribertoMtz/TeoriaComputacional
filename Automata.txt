
/*
   Heriberto Castro Martinez,     Matricula: 140119
    AFD 1(00*)*
    caracteristicas del funcionamiento: el programa pide ingresar una cadena, 
    la cadena solo puede contener ceros o unos, si se ingresa otro caracter se envia un 
    mensaje de caracter invalido y por lo tanto la cadena es invalida. 
    Una vez ingresando la cadena, el programa determina si es valida o invalida y muestra el mensaje correspondiente
    si se desea ingresar otra cadena, se presiona 1, cualquier otro caracter termina el programa

    lógica: Primero se revisa que la cadena sólo contega ceros o unos, en caso de tener otro caracter
    automaticamente esa cadena se toma como invalida.
    De acuerdo al automata el primer numero debe ser estrictamente un 1, si es asi la cadena es valida
    en caso contrario es invalida, despues de ese primer 1 puede o no llevar un cero o muchos ceros, 
    se revisa la cadena a partir del segundo numero, posición por posición, si se encuentra un 1 la cadena
    es invalida. 
*/

import java.util.Scanner;
public class Automata {

    public static void main(String[] args) {
        Datos();
    }
    
    public static void Datos() {
        Scanner sc=new Scanner(System.in);
        System.out.println("\n\nAFD 1(00*)*");
        System.out.println("INGRESE CADENA: ");
        String cadena=sc.nextLine();
         
        int invalido=0;
        char[] cadena_caracter = cadena.toCharArray();
        if (cadena.length()==0){
            System.out.println("CADENA VACIA ");
        }
        else{
            for (int i=0;i<cadena.length();i++){
                if((cadena_caracter[i] != '1') && (cadena_caracter[i] != '0')){
                    invalido++;
                    System.out.println("CARACTER INVALIDO "+cadena_caracter[i]);
                }
            }
            if((cadena_caracter[0] != '1')){
                invalido++;
            }
            else{
                for (int i=1;i<cadena.length();i++){
                    if((cadena_caracter[i] != '0')){
                        invalido++;
                    }
                }
            }
        }
        if(invalido>0){
            System.out.println("CADENA INVALIDA");
        }
        else{
            System.out.println("CADENA VALIDA!!");
        }
        
        System.out.println("\nPRESIONE 1 PARA INTENTAR CON OTRA CADENA: ");
        int op = sc.nextInt();
        if(op == 1) {
            Datos();
        }   
    }   
}
