import java.util.*;

public class SimuladorViajeInterplanetario {
    static Scanner scanner = new Scanner(System.in);
    static Random random = new Random();
    static final double VELOCIDAD_NAVE = 100000; // km/h
    static final double CONSUMO_COMBUSTIBLE_POR_KM = 0.05; // en toneladas
    static final double CONSUMO_OXIGENO_POR_HORA = 2.0; // en unidades
    
    static Map<String, Double> planetas = new HashMap<>();
    
    public static void main(String[] args) {
        planetas.put("Mercurio", 91700000.0);
        planetas.put("Venus", 41000000.0);
        planetas.put("Marte", 78000000.0);
        planetas.put("Júpiter", 628700000.0);
        planetas.put("Saturno", 1275000000.0);
        
        System.out.println("Bienvenido al Simulador de Viaje Interplanetario!");
        iniciarSimulador();
    }
    
    public static void iniciarSimulador() {
        while (true) {
            System.out.println("\nMenú Principal:");
            System.out.println("1. Seleccionar destino");
            System.out.println("2. Salir");
            System.out.print("Seleccione una opción: ");
            int opcion = scanner.nextInt();
            scanner.nextLine();
            
            if (opcion == 1) {
                realizarViaje();
            } else if (opcion == 2) {
                System.out.println("Gracias por usar el simulador. ¡Hasta la próxima!");
                break;
            } else {
                System.out.println("Opción no válida, intente de nuevo.");
            }
        }
    }
    
    public static void realizarViaje() {
        System.out.println("\nSeleccione un destino:");
        List<String> nombresPlanetas = new ArrayList<>(planetas.keySet());
        for (int i = 0; i < nombresPlanetas.size(); i++) {
            System.out.println((i + 1) + ". " + nombresPlanetas.get(i));
        }
        
        System.out.print("Ingrese el número del destino: ");
        int seleccion = scanner.nextInt();
        scanner.nextLine();
        
        if (seleccion < 1 || seleccion > nombresPlanetas.size()) {
            System.out.println("Selección inválida.");
            return;
        }
        
        String destino = nombresPlanetas.get(seleccion - 1);
        double distancia = planetas.get(destino);
        double tiempoHoras = distancia / VELOCIDAD_NAVE;
        double combustibleNecesario = distancia * CONSUMO_COMBUSTIBLE_POR_KM;
        double oxigenoNecesario = tiempoHoras * CONSUMO_OXIGENO_POR_HORA;
        
        System.out.println("Destino seleccionado: " + destino);
        System.out.println("Distancia: " + distancia + " km");
        System.out.println("Tiempo estimado: " + tiempoHoras + " horas");
        System.out.println("Combustible necesario: " + combustibleNecesario + " toneladas");
        System.out.println("Oxígeno necesario: " + oxigenoNecesario + " unidades");
        
        System.out.println("¿Desea iniciar el viaje? (si/no)");
        String respuesta = scanner.nextLine();
        if (!respuesta.equalsIgnoreCase("si")) {
            System.out.println("Viaje cancelado.");
            return;
        }
        
        simularViaje(distancia, tiempoHoras);
    }
    
    public static void simularViaje(double distancia, double tiempoHoras) {
        double distanciaRecorrida = 0;
        int horasTranscurridas = 0;
        
        while (distanciaRecorrida < distancia) {
            horasTranscurridas++;
            distanciaRecorrida += VELOCIDAD_NAVE;
            double progreso = (distanciaRecorrida / distancia) * 100;
            System.out.printf("\nProgreso del viaje: %.2f%%", progreso);
            
            if (random.nextInt(100) < 15) {
                if (!manejarEventoAleatorio()) {
                    System.out.println("La nave no pudo superar el problema. Viaje abortado.");
                    return;
                }
            }
        }
        System.out.println("\n¡Felicidades! Has llegado a tu destino con éxito.");
    }
    
    public static boolean manejarEventoAleatorio() {
        System.out.println("\n¡Evento inesperado! Algo ha sucedido durante el viaje:");
        int evento = random.nextInt(3);
        
        switch (evento) {
            case 0:
                System.out.println("Un asteroide está en curso de colisión.");
                System.out.println("1. Esquivar  2. Acelerar  3. Reducir velocidad");
                break;
            case 1:
                System.out.println("Falla en el sistema de oxígeno.");
                System.out.println("1. Reparar  2. Ignorar  3. Usar reserva de emergencia");
                break;
            case 2:
                System.out.println("Pérdida de comunicación con la Tierra.");
                System.out.println("1. Reiniciar sistemas  2. Continuar viaje  3. Regresar");
                break;
        }
        
        System.out.print("Seleccione una opción: ");
        int decision = scanner.nextInt();
        scanner.nextLine();
        
        if (decision == 1) {
            System.out.println("Problema resuelto con éxito. Continuando viaje.");
            return true;
        } else {
            System.out.println("Decisión no efectiva. El problema persiste.");
            return false;
        }
    }
}
