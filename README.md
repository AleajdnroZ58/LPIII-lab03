# LPIII-lab05
LABORATORIO 5 DE LENGUAJES DEPROGRAMACIÓN
Actividad 1

package Actividad1lab05;

public class Cuenta {
	
	private int numCuenta;
	private double saldo;
	
	
	public Cuenta(int numCuenta, double saldo) {
		super();
		this.numCuenta = numCuenta;
		this.saldo = saldo;
	}
	
	public Cuenta (int numCuenta) {
		this (numCuenta,50);
	}

	public int getNumCuenta() {
		return numCuenta;
	}

	public void setNumCuenta(int numCuenta) {
		this.numCuenta = numCuenta;
	}

	public double getSaldo() {
		return saldo;
	}

	public void setSaldo(double saldo) {
		this.saldo = saldo;
	}
	
	public void depositar(double cantidad) {
        if (cantidad > 0) {
            saldo += cantidad;
        }
    }
	
	public void retirar(double cantidad) {
        if (cantidad > 0 && saldo - cantidad >= 50) {
            saldo -= cantidad;
        }
    }

	public String toString() {
		return "Número de cuenta: " + numCuenta + ", Saldo: " + saldo;
    }
}


package Actividad1lab05;

public class Persona {

	private int id;
	private String nombre;
	private String apellido;
	private Cuenta cuenta;
	private char tipoCliente;
	
	private static int contadorC = 1000;
    private static int contadorB = 5000;
    private static int contadorE = 8000;
	
	public Persona(int id, String nombre, String apellido, int numCuenta) {
		super();
		this.id = id;
		this.nombre = nombre;
		this.apellido = apellido;
		this.setCuenta(new Cuenta(numCuenta));
		
		if (tipoCliente == 'C') {
            cuenta = new Cuenta(contadorC);
            contadorC++;
        } else if (tipoCliente == 'B') {
            cuenta = new Cuenta(contadorB);
            contadorB++;
        } else if (tipoCliente == 'E') {
            cuenta = new Cuenta(contadorE);
            contadorE++;
        } else {
            cuenta = new Cuenta(1000); // Valor por defecto (tipo C)
        }
	}

	public int getId() {
		return id;
	}

	public void setId(int id) {
		this.id = id;
	}

	public String getNombre() {
		return nombre;
	}

	public void setNombre(String nombre) {
		this.nombre = nombre;
	}

	public String getApellido() {
		return apellido;
	}

	public void setApellido(String apellido) {
		this.apellido = apellido;
	}

	public Cuenta getCuenta() {
		return cuenta;
	}

	public void setCuenta(Cuenta cuenta) {
		this.cuenta = cuenta;
	}
	
	public char getTipoCliente() {
        return tipoCliente;
    }

    public void setTipoCliente(char tipoCliente) {
        this.tipoCliente = tipoCliente;
    }
	
	public String toString() {
		return "Persona [id="+id+", nombre="+ nombre+", apellido= "+apellido+",cuenta="+cuenta+", tipoCliente=" + tipoCliente;
	}
}


package Actividad1lab05;

public class TestComposition {

	public static void main(String[] args) {
        Persona persona1 = new Persona(456789789, "Daniel", "Alagon", 'C');
        Persona persona2 = new Persona(123456789, "Eduardo", "Perez", 'B');
        Persona persona3 = new Persona(987654321, "Ana", "Gomez", 'E');

        System.out.println(persona1);
        System.out.println(persona2);
        System.out.println(persona3);

        persona1.getCuenta().depositar(100);
        persona2.getCuenta().retirar(50);
        persona3.getCuenta().depositar(200);

        System.out.println("Después de operaciones:");
        System.out.println(persona1);
        System.out.println(persona2);
        System.out.println(persona3);
    }
}
