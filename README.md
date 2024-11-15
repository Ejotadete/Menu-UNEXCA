console.log("Menu");
#include <iostream>
#include <vector>
#include <string>

using namespace std;

// Estructura para representar un elemento
struct Elemento {
    int id;
    string nombre;
};

// Prototipos de funciones
void menuPrincipal();
void subMenuIncluir(vector<Elemento>& elementos);
void subMenuModificar(vector<Elemento>& elementos);
void mostrarElementos(const vector<Elemento>& elementos);
int obtenerOpcion();

int main() {
    menuPrincipal(); // Llamada a la función del menú principal
    return 0;
}

// Función que muestra el menú principal
void menuPrincipal() {
    vector<Elemento> elementos; // Vector para almacenar los elementos
    int opcion;
    
    do {
        cout << "=== Menu Principal ===" << endl;
        cout << "1. Incluir" << endl;
        cout << "2. Modificar" << endl;
        cout << "3. Eliminar" << endl;
        cout << "4. Informes" << endl;
        cout << "0. Salir" << endl;
        opcion = obtenerOpcion();

        switch (opcion) {
            case 1:
                subMenuIncluir(elementos); // Llama al submenú de incluir
                break;
            case 2:
                subMenuModificar(elementos); // Llama al submenú de modificar
                break;
            case 3:
                cout << "Funcionalidad de Eliminar no implementada." << endl; // Placeholder
                break;
            case 4:
                mostrarElementos(elementos); // Muestra los elementos
                break;
            case 0:
                cout << "Saliendo del programa." << endl;
                break;
            default:
                cout << "Opción inválida. Intente nuevamente." << endl;
        }
    } while (opcion != 0);
}

// Función que muestra el submenú para incluir
void subMenuIncluir(vector<Elemento>& elementos) {
    Elemento nuevoElemento;
    
    cout << "=== Submenú Incluir ===" << endl;
    cout << "Ingrese ID: ";
    cin >> nuevoElemento.id;
    cin.ignore(); // Limpiar el buffer

    cout << "Ingrese Nombre: ";
    getline(cin, nuevoElemento.nombre);

    elementos.push_back(nuevoElemento); // Agrega el nuevo elemento al vector
    cout << "Elemento incluido correctamente." << endl;
}

// Función que muestra el submenú para modificar
void subMenuModificar(vector<Elemento>& elementos) {
    int idModificar;
    bool encontrado = false;

    cout << "=== Submenú Modificar ===" << endl;
    cout << "Ingrese ID del elemento a modificar: ";
    cin >> idModificar;

    for (auto& elemento : elementos) {
        if (elemento.id == idModificar) {
            encontrado = true;

            cout << "Nuevo Nombre: ";
            cin.ignore(); // Limpiar el buffer
            getline(cin, elemento.nombre);
            cout << "Elemento modificado correctamente." << endl;
            break;
        }
    }

    if (!encontrado) {
        cout << "Elemento con ID " << idModificar << " no encontrado." << endl;
    }
}

// Función para mostrar todos los elementos
void mostrarElementos(const vector<Elemento>& elementos) {
    cout << "=== Informes ===" << endl;

    if (elementos.empty()) {
        cout << "No hay elementos registrados." << endl;
        return;
    }

    for (const auto& elemento : elementos) {
        cout << "ID: " << elemento.id 
             << ", Nombre: " << elemento.nombre 
             << endl;
    }
}

// Función para obtener una opción válida del usuario
int obtenerOpcion() {
    int opcion;
    cout << "Seleccione una opción: ";
    cin >> opcion;

    return opcion;
}
