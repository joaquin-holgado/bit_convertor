#include <iostream>
#include <string>
#include <cmath>
#include <algorithm>
#include <fstream>
using namespace std;

// --- FUNCIONES DE CONVERSIÓN ---
int binarioADecimal(string binario) {
    int decimal = 0;
    int potencia = binario.size() - 1;
    for (int i = 0; i < binario.size(); i++) {
        if (binario[i] == '1') decimal += pow(2, potencia);
        potencia--;
    }
    return decimal;
}

string decimalABinario(int decimal) {
    string binario = "";
    if (decimal == 0) return "0";
    while (decimal > 0) {
        binario = char((decimal % 2) + '0') + binario;
        decimal /= 2;
    }
    return binario;
}

string decimalAOctal(int decimal) {
    string octal = "";
    if (decimal == 0) return "0";
    while (decimal > 0) {
        octal = char((decimal % 8) + '0') + octal;
        decimal /= 8;
    }
    return octal;
}

int octalADecimal(string octal) {
    int decimal = 0;
    int potencia = octal.size() - 1;
    for (int i = 0; i < octal.size(); i++) {
        decimal += (octal[i] - '0') * pow(8, potencia);
        potencia--;
    }
    return decimal;
}

string decimalAHexadecimal(int decimal) {
    string hexa = "";
    char digitos[] = "0123456789ABCDEF";
    if (decimal == 0) return "0";
    while (decimal > 0) {
        hexa = digitos[decimal % 16] + hexa;
        decimal /= 16;
    }
    return hexa;
}

int hexadecimalADecimal(string hexa) {
    int decimal = 0;
    int potencia = 0;
    reverse(hexa.begin(), hexa.end());
    for (char c : hexa) {
        if (c >= '0' && c <= '9')
            decimal += (c - '0') * pow(16, potencia);
        else if (c >= 'A' && c <= 'F')
            decimal += (c - 'A' + 10) * pow(16, potencia);
        else if (c >= 'a' && c <= 'f')
            decimal += (c - 'a' + 10) * pow(16, potencia);
        potencia++;
    }
    return decimal;
}

// --- VALIDACIÓN DE BINARIO ---
bool esBinario(const string &bin) {
    for (char c : bin) {
        if (c != '0' && c != '1') return false;
    }
    return true;
}

// --- FUNCIÓN PARA GUARDAR HISTORIAL ---
void guardarHistorial(const string &conversion) {
    ofstream archivo("historial.txt", ios::app);
    if (archivo.is_open()) {
        archivo << conversion << endl;
        archivo.close();
    } else {
        cout << "⚠ No se pudo abrir el archivo de historial.\n";
    }
}

// --- PROGRAMA PRINCIPAL ---
int main() {
    int opcion;
    do {
        cout << "\n===== CONVERSOR NUMERICO =====\n";
        cout << "1. Decimal -> Binario\n";
        cout << "2. Binario -> Decimal\n";
        cout << "3. Decimal -> Hexadecimal\n";
        cout << "4. Hexadecimal -> Decimal\n";
        cout << "5. Decimal -> Octal\n";
        cout << "6. Octal -> Decimal\n";
        cout << "7. Binario -> Hexadecimal\n";
        cout << "8. Hexadecimal -> Binario\n";
        cout << "9. Ver historial\n";
        cout << "10. Borrar historial\n";
        cout << "11. Salir\n";
        cout << "==============================\n";
        cout << "Elige una opcion: ";
        cin >> opcion;

        if (opcion == 1) {
            int num;
            cout << "Ingresa un numero decimal: ";
            cin >> num;
            string res = decimalABinario(num);
            cout << "Binario: " << res << endl;
            guardarHistorial("Decimal -> Binario: " + to_string(num) + " = " + res);
        } 
        else if (opcion == 2) {
            string bin;
            cout << "Ingresa un numero binario: ";
            cin >> bin;

            // VALIDACIÓN DE BINARIO
            while (!esBinario(bin)) {
                cout << "❌ Error: solo se permiten los digitos 0 y 1.\n";
                cout << "Intenta de nuevo: ";
                cin >> bin;
            }

            int res = binarioADecimal(bin);
            cout << "Decimal: " << res << endl;
            guardarHistorial("Binario -> Decimal: " + bin + " = " + to_string(res));
        } 
        else if (opcion == 3) {
            int num;
            cout << "Ingresa un numero decimal: ";
            cin >> num;
            string res = decimalAHexadecimal(num);
            cout << "Hexadecimal: " << res << endl;
            guardarHistorial("Decimal -> Hexadecimal: " + to_string(num) + " = " + res);
        } 
        else if (opcion == 4) {
            string hexa;
            cout << "Ingresa un numero hexadecimal: ";
            cin >> hexa;
            int res = hexadecimalADecimal(hexa);
            cout << "Decimal: " << res << endl;
            guardarHistorial("Hexadecimal -> Decimal: " + hexa + " = " + to_string(res));
        } 
        else if (opcion == 5) {
            int num;
            cout << "Ingresa un numero decimal: ";
            cin >> num;
            string res = decimalAOctal(num);
            cout << "Octal: " << res << endl;
            guardarHistorial("Decimal -> Octal: " + to_string(num) + " = " + res);
        } 
        else if (opcion == 6) {
            string oct;
            cout << "Ingresa un numero octal: ";
            cin >> oct;
            int res = octalADecimal(oct);
            cout << "Decimal: " << res << endl;
            guardarHistorial("Octal -> Decimal: " + oct + " = " + to_string(res));
        } 
        else if (opcion == 7) {
            string bin;
            cout << "Ingresa un numero binario: ";
            cin >> bin;

            // VALIDACIÓN DE BINARIO
            while (!esBinario(bin)) {
                cout << "❌ Error: solo se permiten los digitos 0 y 1.\n";
                cout << "Intenta de nuevo: ";
                cin >> bin;
            }

            int dec = binarioADecimal(bin);
            string res = decimalAHexadecimal(dec);
            cout << "Hexadecimal: " << res << endl;
            guardarHistorial("Binario -> Hexadecimal: " + bin + " = " + res);
        }
        else if (opcion == 8) {
            string hexa;
            cout << "Ingresa un numero hexadecimal: ";
            cin >> hexa;
            int dec = hexadecimalADecimal(hexa);
            string res = decimalABinario(dec);
            cout << "Binario: " << res << endl;
            guardarHistorial("Hexadecimal -> Binario: " + hexa + " = " + res);
        }
        else if (opcion == 9) {
            ifstream archivo("historial.txt");
            if (archivo.is_open()) {
                cout << "\n--- HISTORIAL DE CONVERSIONES ---\n";
                string linea;
                while (getline(archivo, linea)) {
                    cout << linea << endl;
                }
                archivo.close();
            } else {
                cout << "No hay historial disponible.\n";
            }
        }
        else if (opcion == 10) {
            ofstream archivo("historial.txt", ios::trunc);
            archivo.close();
            cout << "Historial borrado correctamente.\n";
        }
        else if (opcion == 11) {
            cout << "Saliendo del programa...\n";
        } 
        else {
            cout << "Opcion invalida. Intenta de nuevo.\n";
        }

    } while (opcion != 11);

    return 0;
}
