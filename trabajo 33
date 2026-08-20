
import os

NOMBRE_ARCHIVO = "estudiantes.txt"
REPORTE_ARCHIVO = "reporte.txt"

def procesar_y_generar_reporte():
    """Lee el archivo, calcula el promedio y crea el reporte."""
    try:
        with open(NOMBRE_ARCHIVO, "r", encoding="utf-8") as archivo:
            lineas = archivo.readlines()

        if not lineas:
            print("El archivo está vacío.")
            return

        total = 0.0
        contador = 0
        lineas_validas = []

        for linea in lineas:
            linea_limpia = linea.strip()
            if not linea_limpia:
                continue 
            
            
            if "," not in linea_limpia:
                print(f"Advertencia: Formato inválido ignorado -> '{linea_limpia}'")
                continue

            partes = linea_limpia.split(",")
            nombre = partes[0].strip()
            
            
            try:
                nota = float(partes[1].strip())
            except ValueError:
                print(f"Advertencia: Nota no válida ignorada para {nombre} -> '{partes[1]}'")
                continue

            total += nota
            contador += 1
            lineas_validas.append(linea)

        if contador == 0:
            print("No se encontraron registros válidos para calcular el promedio.")
            return

        promedio = total / contador

        
        with open(REPORTE_ARCHIVO, "w", encoding="utf-8") as reporte:
            for l in lineas_validas:
                reporte.write(l if l.endswith("\n") else l + "\n")
            reporte.write(f"Promedio general: {promedio:.1f}\n")

        print(f"Reporte generado con éxito en '{REPORTE_ARCHIVO}'.")
        print(f"Promedio general calculado: {promedio:.1f}")

    except FileNotFoundError:
        print(f"Error: El archivo '{NOMBRE_ARCHIVO}' no existe.")
    except Exception as e:
        print(f"Error inesperado al procesar: {e}")

def agregar_estudiante():
    """Permite al usuario agregar un nuevo estudiante al archivo original."""
    nombre = input("Ingrese el nombre del estudiante: ").strip()
    if not nombre:
        print("El nombre no puede estar vacío.")
        return

    try:
        nota = float(input("Ingrese la calificación: "))
    except ValueError:
        print("Error: La calificación debe ser un número válido.")
        return

    
    try:
        with open(NOMBRE_ARCHIVO, "a", encoding="utf-8") as archivo:
            archivo.write(f"{nombre}, {nota:.1f}\n")
        print(f"Estudiante '{nombre}' agregado correctamente.")
    except Exception as e:
        print(f"Error al escribir en el archivo: {e}")

def main():
   
    procesar_y_generar_reporte()

   
    while True:
        respuesta = input("\n¿Desea agregar un nuevo estudiante? (s/n): ").strip().lower()
        if respuesta == 's':
            agregar_estudiante()
            procesar_y_generar_reporte() 
        elif respuesta == 'n':
            print("Programa finalizado.")
            break
        else:
            print("Opción no válida. Responda 's' para sí o 'n' para no.")

if __name__ == "__main__":
    main()


