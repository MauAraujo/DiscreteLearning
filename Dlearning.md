´´´
package discreetlearning;

import java.io.BufferedReader;
import java.io.BufferedWriter;
import java.io.FileReader;
import java.io.FileWriter;
import java.util.ArrayList;


public class Dlearning {
    public static String action;
    
    public static String dlv(){
         try{
             //This function excecute DLV and the planning
             Builder.plan();
         }catch(Exception e){System.out.println("DLV failed");}
        //Archivo actions = new Archivo("actions");
        Archivo dlv = new Archivo("plan_output");
        Archivo planning = new Archivo("planning");
        planning.clean();
        //Se necesita migrar la informacion de plan_output.txt a otro archivo, en este caso es planning.txt
        dlv.read();
        planning.write(dlv.content);
        dlv.read();
        if (planning.content.equals(null) || planning.content.equals("")){
            while(planning.content.equals(null) || planning.content.equals("")){
                dlv.read();
                planning.write(dlv);
                dlv.read();
            }
        }
        
        //actions.writePlan(planning);
        
        //Notas
        //planning es el archivo que va a contener el plan a seguir, y especificamente la accion
        //Solo necesitamos trabajar sobre el archivo planning
        planning.Plan();
        //planning.content es el output de dlv 
        //planning.planning contendra la accion a seguir i.e. "teach(basico)"
        
        //Borraremos el archivo plan_output.txt para que en un futuro si lo volvemos a utilizar, 
        //este no se duplique.
        dlv.clean();
        
        //action es la accion a seguir
        action = planning.planning;
        System.out.println(action);
       
        
        return action;
    } 
    
    public static void main(String[] args) {
        Subject s1 = new Subject("Basics");
        
         s1.setDef("Es todo lo basico antes de aprender relaciones");
         s1.setDef("Antes de aprender Relaciones, debes aprender teoria de conjuntos");
         
         s1.teach();
         try{
             //This function excecute DLV and the planning
             Builder.plan();
         }catch(Exception e){System.out.println("DLV failed");}
        //Archivo actions = new Archivo("actions");
        Archivo dlv = new Archivo("plan_output");
        Archivo planning = new Archivo("planning");
        planning.clean();
        //Se necesita migrar la informacion de plan_output.txt a otro archivo, en este caso es planning.txt
        dlv.read();
        planning.write(dlv.content);
        dlv.read();
        if (planning.content.equals(null) || planning.content.equals("")){
            while(planning.content.equals(null) || planning.content.equals("")){
                dlv.read();
                planning.write(dlv);
                dlv.read();
            }
        }
        
        //actions.writePlan(planning);
        
        //Notas
        //planning es el archivo que va a contener el plan a seguir, y especificamente la accion
        //Solo necesitamos trabajar sobre el archivo planning
        planning.Plan();
        //planning.content es el output de dlv 
        //planning.planning contendra la accion a seguir i.e. "teach(basico)"
        
        //Borraremos el archivo plan_output.txt para que en un futuro si lo volvemos a utilizar, 
        //este no se duplique.
        dlv.clean();
        
        //action es la accion a seguir
        action = planning.planning;
        System.out.println(action);
       
    }
       
}
´´´
