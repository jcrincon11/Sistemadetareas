package Sistemadetareas;

import java.util.Scanner;
import java.util.ArrayList;

public class Sistemadetareas {

    public String tarea;
    public int identificacion;

    public Sistemadetareas() {

    }

    public Sistemadetareas(String tarea, int identificacion) {
        this.tarea = tarea;
        this.identificacion = identificacion;
    }

    public String gettarea() {
        return tarea;
    }

    public int getidentificacion() {
        return identificacion;
    }

    public void settarea(String tarea) {
        this.tarea = tarea;
    }

    public void setidentificacion(int identificacion) {
        this.identificacion = identificacion;
    }

    public static void main(String[] args) {

        Scanner datos = new Scanner(System.in);

        ArrayList<Sistemadetareas> blocktareas = new ArrayList<Sistemadetareas>();
        int opciones = 0;

        do {
            System.out.println("Menu de tareas");
            System.out.println("1.Agregar tareas");
            System.out.println("2.consultar tarea por id");
            System.out.println("3.Mostrar todas las tareas");
            System.out.println("4.Salir");
            opciones = datos.nextInt();

            switch (opciones) {
                case 1:
                    System.out.println("Ingrese la tarea que va a realizar");
                    String tarea = datos.next();
                    System.out.println("Ingrese una identificacion para la tarea");
                    int identificacion = datos.nextInt();
                    Sistemadetareas block = new Sistemadetareas(tarea, identificacion);
                    blocktareas.add(block);
                    System.out.println("La tarea ha sido agregada correctamente");
                    break;
                case 2:
                    System.out.println("Ingrese el numero de identificacion de la tarea");
                    String buscar = datos.next();
                    boolean localizar = false;
                    int opcionestareas = 0;
                    for (Sistemadetareas n : blocktareas) {
                        if (n.gettarea().equals(buscar) || n.getidentificacion() == Integer.parseInt(buscar)) {
                            System.out.println("Tarea localizada");
                            System.out.println("Tarea:" + n.gettarea());
                            System.out.println("Identificaion:" + n.getidentificacion());
                            System.out.println("Digite 1 si ya realizo la tarea");
                            System.out.println("Digite 2 si no ha realizado la tarea");
                            opcionestareas = datos.nextInt();
                            switch (opcionestareas) {
                                case 1:
                                    System.out.println("Felicidades ya terminaste tu tarea");
                                    System.out.println("si desea eliminar la tarea marque 1, en sudefecto marque 2");
                                    int op = 0;
                                    op = datos.nextInt();
                                    switch (op) {
                                        case 1:
                                            System.out.println("La tarea ha sido borrada exitosamente");
                                            blocktareas.remove(n);

                                            break;
                                        case 2:
                                            System.out.println("La tarea no ha sido borrada");
                                    }
                                    break;
                                case 2:
                                    System.out.println("Debes realizar la tarea correspondiente");
                            }
                            localizar = true;
                            break;
                        }
                        
                        if (!localizar) {
                            System.out.println("Tarea no encontrada");
                        }
                    }

                    break;
                case 3:
                    if (blocktareas.isEmpty()) {
                        System.out.println("No hay tareas agregadas");
                    } else {
                        System.out.println("Lista de tareas");
                        for (Sistemadetareas n : blocktareas) {

                            System.out.println("Tarea:" + n.gettarea());
                            System.out.println("Identificaion:" + n.getidentificacion());
                            System.out.println("-----------------");
                        }
                    }

                    break;

                case 4:
                    System.out.println("Gracias por utilizar el programa");
                    break;
                default:
                    System.out.println("Los numeros son del 1 al 4");
                    break;
            }
        } while (opciones != 4);
        datos.close();
    }
}
