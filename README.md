# Registro-de-tiempo-de-jugador
import time

# Decorador para registrar el tiempo de juego
def registrar_tiempo_juego(funcion):
    def envoltorio(self, *args, **kwargs):
# Registrar el tiempo de inicio
        inicio = time.time()
# Ejecutar la función decorada
        resultado = funcion(self, *args, **kwargs)
# Registrar el tiempo de fin
        fin = time.time()
# Calcular el tiempo jugado en minutos
        tiempo_jugado = (fin - inicio) / 60
# Acumular el tiempo jugado
        self.tiempo_jugado += tiempo_jugado
        return resultado
    return envoltorio

class Jugador:
    def __init__(self, nombre):
# Inicializar el nombre del jugador y el tiempo jugado
        self.nombre = nombre
        self.tiempo_jugado = 0  # Se inicia en 0 minutos

    @registrar_tiempo_juego
    def entrenar(self):
# Simular el entrenamiento del jugador
        print(f"{self.nombre} está entrenando")

# Crea una instancia del jugador "Eduard"
jugador1 = Jugador("Eduard")
# El jugador entrena, lo que registrará el tiempo jugado
jugador1.entrenar()
# Imprimir el tiempo total jugado 
print(f"Eduard ha jugado {jugador1.tiempo_jugado:.2f} minutos")
