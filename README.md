# Conductores-y-Constructores
# Demo JDBC Project

## Descripción

Este proyecto es una aplicación Java que utiliza JDBC para interactuar con una base de datos y mostrar estadísticas de Fórmula 1. La aplicación permite seleccionar el año y muestra los resultados de los pilotos, incluyendo el nombre del piloto, victorias, puntos totales y su clasificación.

## Dependencias

- JDK 17
- JDBC Driver para la base de datos que se esté utilizando (MySQL, PostgreSQL, etc.)
- Librerías adicionales que se indiquen en el `pom.xml` si se utiliza Maven

## Instalación

1. Clona el repositorio:
    ```bash
    git clone https://github.com/tu_usuario/demo_jdbc.git
    ```
2. Importa el proyecto en tu IDE favorito (Eclipse, IntelliJ IDEA, etc.).
3. Asegúrate de tener configurado el JDK 17 en tu IDE.
4. Configura la conexión a la base de datos en el archivo de configuración correspondiente (por ejemplo, en un archivo `application.properties` o directamente en el código).

## Uso

1. Ejecuta la clase `Main.java` para iniciar la aplicación.
2. Utiliza el menú desplegable para seleccionar el año que deseas visualizar.
3. La tabla se actualizará con las estadísticas de los pilotos para el año seleccionado.

## Capturas de Pantalla

### Selección de Año

![Selección de Año]( https://github.com/BryanR69/Conductores-y-Constructores/blob/main/Captura%20de%20pantalla%20-%20Conductores.png)

### Resultados de Pilotos

![Resultados de Pilotos]( https://github.com/BryanR69/Conductores-y-Constructores/blob/main/Captura%20de%20pantalla%20-%20Conductores%20y%20Constructores.png)

## Código Ejemplo

### Main.java

```java
package demo_jdbc;

import demo_jdbc.models.DriverResult;
import demo_jdbc.repositories.DriverResultRepository;
import java.util.List;

public class Main {
    public static void main(String[] args) {
        DriverResultRepository driverResultRepository = new DriverResultRepository();
        List<DriverResult> results = driverResultRepository.getResultByYear(2009);

        for (DriverResult rs : results) {
            System.out.println(rs.getDriverName() + "\t" + rs.getWins() + "\t" + rs.getTotalPoints());
        }

        // Assume there is a method to get top drivers
        List<DriverResult> topDrivers = driverResultRepository.getTopDrivers();
        for (DriverResult topDriver : topDrivers) {
            System.out.println(topDriver.getDriverName() + "\t" + topDriver.getTotalPoints());
        }
    }
}
