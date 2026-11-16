[README.md](https://github.com/user-attachments/files/34929224/README.md)
# Alta Usuario Spring

Formulario web de alta de usuarios hecho con Spring Boot y Thymeleaf. Incluye dos versiones del mismo formulario para comparar enfoques: una con validación manual y otra con **DTO + Bean Validation** y mensajes en **español e inglés**.

## Qué hace

La página de inicio ofrece dos formas de darse de alta. En ambas se piden:

- **Nombre** y **email**
- **Tecnología** de interés (lista desplegable)
- **Nivel** (selección múltiple: Principiante, Intermedio, Avanzado)

| Ruta | Versión |
|------|---------|
| `/alta` | Validación manual en el controlador con `@RequestParam` (comprueba que el nombre no esté vacío y conserva los datos rellenados si hay error). |
| `/alta-validacion` | Validación con `UsuarioDto` y Bean Validation (`@NotBlank`, `@Size`, `@Email`). Los errores se muestran junto a cada campo. |

Si todo es correcto, se muestra una página de confirmación con los datos enviados.

Otros detalles:

- Las listas de tecnologías y niveles se leen de ficheros de texto (`resources/datos/`) a través de un servicio, así el controlador no depende de dónde vengan los datos.
- Mensajes de validación **internacionalizados** (`messages.properties` y `messages_en.properties`).
- Manejo de errores con página propia (por ejemplo, si falta un fichero de datos).

## Tecnologías

Java 21 · Spring Boot · Thymeleaf · Bean Validation · Lombok · Maven

## Estructura

```
src/main/java/es/daw/altausuariospring
├── controller   # AltaController, AltaValidationController
├── service      # AltaService (lee tecnologías y niveles)
├── dto          # UsuarioDto (con validaciones) y UsuarioDtoRecord
├── exception    # GlobalExceptionHandler, FicheroNoEncontradoException
└── config       # WebConfig (ruta "/" -> index)
src/main/resources
├── datos        # tecnologias.txt, niveles.txt
├── templates    # formularios y confirmaciones
├── messages*.properties
└── static/css
```

## Cómo ejecutarlo

Requisitos: JDK 21.

```bash
git clone https://github.com/Alvaro970/Alta-Usuario-Spring.git
cd Alta-Usuario-Spring
./mvnw spring-boot:run        # en Windows: mvnw.cmd spring-boot:run
```

Después abre <http://localhost:8080>.

## Autor

Álvaro Escribano Gómez · [GitHub](https://github.com/Alvaro970)
