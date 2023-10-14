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
