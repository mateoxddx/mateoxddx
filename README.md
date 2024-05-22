import os
os.environ['PYGAME_HIDE_SUPPORT_PROMPT'] = "hide"
import pygame

preguntas_respuestas = {
    "1": "¿De donde es originario este árbol?",
    "2": "¿Cual es su nombre cientifico?",
    "3": "¿Dónde puedo encontrar más información?"
}

respuestas = {
    "1": "\033[1;32mOriginaria de las isalas canarias de España\033[0m",
    "2": "\033[1;32mPhoenix canariensis\033[0m",
    "3": "\033[1;32mhttps://colombia.inaturalist.org/taxa/78554-Phoenix-canariensis\033[0m"
}

def mostrar_opciones():
    print("Selecciona una opción:")
    for opcion, pregunta in preguntas_respuestas.items():
        print(f"{opcion}: {pregunta}")

def mostrar_respuesta(opcion):
    if opcion in respuestas:
        print(respuestas[opcion])
        # Reproducir audio
        pygame.mixer.init()
        pygame.mixer.music.load("C:\\Users\\user\\Music\\1er audio palma\\ttsmaker-file-2024-5-21-21-20-29.mp3")
        pygame.mixer.music.play()
        while pygame.mixer.music.get_busy():
            continue
    else:
        print("Lo siento, no conozco la respuesta a esa pregunta.")

def main():
    print("¡Bienvenido a Árboles que Hablan!")
    pygame.init()
    while True:
        mostrar_opciones()
        seleccion = input("Ingresa el número de la pregunta que deseas responder (o escribe 'salir' para terminar): ")
        if seleccion.lower() == "salir":
            break
        elif seleccion in preguntas_respuestas:
            print(preguntas_respuestas[seleccion])
            mostrar_respuesta(seleccion)
        else:
            print("Opción no válida. Por favor, selecciona una opción válida.")
    pygame.quit()

if _name_ == "_main_":
    main()
