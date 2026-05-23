SESSIONS = [
    [101, 240, 12],
    [102, 45, 2],
    [103, 120, 5],
    [104, 190, 9],
    [105, 75, 3],
]


def clasificar_compromiso(duracion_segundos, eventos_clics):
    """Calcula la clasificación de compromiso para una sesión."""
    if duracion_segundos > 180 and eventos_clics > 8:
        return "Alto"
    if duracion_segundos < 60 or eventos_clics < 3:
        return "Bajo"
    return "Medio"


def generar_informe(sesiones):
    """Genera un informe de compromiso por ID de cliente."""
    informe = []
    for sesion in sesiones:
        cliente_id, duracion, clics = sesion
        clasificacion = clasificar_compromiso(duracion, clics)
        informe.append((cliente_id, clasificacion))
    return informe


def imprimir_informe(sesiones):
    """Imprime el informe de clasificación de compromiso."""
    informe = generar_informe(sesiones)
    print("Informe de compromiso de sesiones:")
    for cliente_id, clasificacion in informe:
        print(f"- Cliente {cliente_id}: {clasificacion}")


if __name__ == "__main__":
    imprimir_informe(SESSIONS)
