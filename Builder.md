´´´
 /*
 * To change this license header, choose License Headers in Project Properties.
 * To change this template file, choose Tools | Templates
 * and open the template in the editor.
 */
package discreetlearning;
import java.io.BufferedReader;
import java.io.InputStreamReader;
import java.io.IOException;
import java.io.PrintWriter;
import java.lang.ProcessBuilder;
/**
 *
 * @author mau
 */
public class Builder {

    public static String result;
    /**
     * @param args the command line arguments
     */
    public static void watch(final Process process) {
    new Thread(){
        public void run() {
           Archivo output = new Archivo("plan_output");
            /*BufferedReader input = new BufferedReader(new InputStreamReader(process.getInputStream()));
            String line = null; 
            try {
                while ((line = input.readLine()) != null) {
                    //System.out.println(line);
                    output.write(line);
                }
            } catch (IOException e) {
                e.printStackTrace();
            }*/
             BufferedReader reader = new BufferedReader(new InputStreamReader(process.getInputStream()));
            StringBuilder str = new StringBuilder();
            String line = null;
            
            try{
                while ( (line = reader.readLine()) != null) {
                str.append(line);
                str.append(System.getProperty("line.separator"));
                }
                 String result = str.toString();
                 output.write(result);
              //System.out.println(result);
            } catch (IOException e) {
                e.printStackTrace();
            }
    }
        
        }.start();
    }
    public static String plan()throws IOException {
      //Mau
        ProcessBuilder builder = new ProcessBuilder("/Users/pamelagarcia/Downloads/dlv.i386-apple-darwin.bin", "-FP", "/Users/pamelagarcia/DiscreteLearning/dlearning.plan", "/Users/pamelagarcia/DiscreteLearning/dlearninginit.plan", "/Users/pamelagarcia/DiscreteLearning/dlearning.dl", "-planlength=12");
        //Noe
        //ProcessBuilder builder = new ProcessBuilder("/src/Dlv/dlv.bin", "-FP", "/src/Dlv/dlearning.plan", "/src/Dlv/dlearninginit.plan", "/src/Dlv/dlearning.dl");
        //ProcessBuilder builder = new ProcessBuilder("/Users/noe/Documents/Developing/dlv/dlv.bin", "-FP", 
        //                                            "/Users/noe/Documents/Developing/DiscreteLearning/dlearning.plan", 
        //                                            "/Users/noe/Documents/Developing/DiscreteLearning/dlearninginit.plan", 
        //                                            "/Users/noe/Documents/Developing/DiscreteLearning/dlearning.dl");
        /*ProcessBuilder builder = new ProcessBuilder("/Users/noe/Documents/Developing/dlv/dlv.bin", "-FP", 
                                                    "/src/dlv/dlearning.plan", 
                                                    "/src/dlv/dlearninginit.plan", 
                                                    "/src/dlv/dlearning.dl", "-planlength=12");*/
        //Noe Windows
        //ProcessBuilder builder = new ProcessBuilder("/Users/hp/Documents/Developing/dlv.exe", "-FP", "/Users/hp/Documents/Developing/DiscreteLearning/dlearning.plan", "/Users/hp/Documents/Developing/DiscreteLearning/dlearninginit.plan", "/Users/hp/Documents/Developing/DiscreteLearning/dlearning.dl");
        //ProcessBuilder builder = new ProcessBuilder("/home/mau/Tools/dlv.x86-64-linux-elf-static.bin", "-FP", "/home/mau/Documents/School/Lenguajes Formales y Autómatas/DiscreteLearning/dlearning.plan", "/home/mau/Documents/School/Lenguajes Formales y Autómatas/DiscreteLearning/dlearninginit.plan", "/home/mau/Documents/School/Lenguajes Formales y Autómatas/DiscreteLearning/dlearning.dl");
        builder.redirectErrorStream(true);
        final Process process = builder.start();
        
        PrintWriter input = new PrintWriter(process.getOutputStream());
        input.print("n");
        input.print("n");
        input.close();

        Builder.watch(process);  
        
        
        return result;
    }
    
    public static void main(String[] args) throws IOException {
        // TODO code application logic here
        //Mau
        //ProcessBuilder builder = new ProcessBuilder("/Downloads/dlv.i386-apple-darwin.bin", "-FP", "/DLearning/dlearning.plan", "/DLearning/dlearninginit.plan", "/DLearning/dlearning.dl");
        //Noe
        /*ProcessBuilder builder = new ProcessBuilder("/Users/noe/Documents/Developing/dlv/dlv.i386-apple-darwin.bin", "-FP", "/Users/noe/Documents/Developing/dlv/dlearning.plan", "/Users/noe/Documents/Developing/dlv/dlearninginit.plan", "/Users/noe/Documents/Developing/dlv/dlearning.dl");
        builder.redirectErrorStream(true);
        final Process process = builder.start();
        
        PrintWriter input = new PrintWriter(process.getOutputStream()); 
        input.print("n");
        input.print("n");
        input.close();
        
        Builder.watch(process);*/
        plan();
    }
    
}
```
