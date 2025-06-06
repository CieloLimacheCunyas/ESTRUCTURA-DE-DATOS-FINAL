// PARTE 1 - Estructura de Nodo y ListaEnlazada para gestión de procesos

#include <iostream>
#include <string>
using namespace std;

struct Nodo {
    int id;
    string nombre;
    int prioridad;
    Nodo* siguiente;

    Nodo(int i, string n, int p) : id(i), nombre(n), prioridad(p), siguiente(nullptr) {}
};

class ListaEnlazada {
private:
    Nodo* cabeza;
    int contadorId;

public:
    ListaEnlazada() : cabeza(nullptr), contadorId(1) {}

    void insertarProceso(const string& nombre, int prioridad) {
        Nodo* nuevo = new Nodo(contadorId++, nombre, prioridad);
        if (!cabeza || prioridad > cabeza->prioridad) {
            nuevo->siguiente = cabeza;
            cabeza = nuevo;
        } else {
            Nodo* actual = cabeza;
            while (actual->siguiente && prioridad <= actual->siguiente->prioridad) {
                actual = actual->siguiente;
            }
            nuevo->siguiente = actual->siguiente;
            actual->siguiente = nuevo;
        }
    }

    bool eliminarProceso(int id) {
        if (!cabeza) return false;
        if (cabeza->id == id) {
            Nodo* temp = cabeza;
            cabeza = cabeza->siguiente;
            delete temp;
            return true;
        }
        Nodo* actual = cabeza;
        while (actual->siguiente && actual->siguiente->id != id) {
            actual = actual->siguiente;
        }
        if (actual->siguiente) {
            Nodo* temp = actual->siguiente;
            actual->siguiente = temp->siguiente;
            delete temp;
            return true;
        }
        return false;
    }

    Nodo* buscarProceso(int id) {
        Nodo* actual = cabeza;
        while (actual && actual->id != id) {
            actual = actual->siguiente;
        }
        return actual;
    }

    void mostrarProcesos() {
        Nodo* actual = cabeza;
        cout << "\n Lista de Procesos Actuales:\n";
        cout << "ID\tNombre\tPrioridad\n";
        while (actual) {
            cout << actual->id << "\t" << actual->nombre << "\t" << actual->prioridad << endl;
            actual = actual->siguiente;
        }
    }
};
