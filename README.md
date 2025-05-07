# WeatherComponent - Componente de Clima para Java Swing

![WeatherComponent Screenshot](ruta/a/tu/imagen.png)

## Tabla de Contenidos

- [Características](#características)  
- [Requisitos](#requisitos)  
- [Instalación](#instalación)  
- [Uso Básico](#uso-básico)  
- [Configuración](#configuración)  
- [Integración con NetBeans](#integración-con-netbeans)  
- [Propiedades](#propiedades)  
- [Métodos](#métodos)  
- [Licencia](#licencia)  

## Características

- Visualización de información meteorológica básica  
- Diseño atractivo con gradiente de fondo personalizable  
- Muestra ciudad, temperatura y condición climática  
- Íconos visuales según el clima (sol, nubes, lluvia)  
- Integración con NetBeans Palette  
- Personalización completa de colores  

## Requisitos

- Java JDK 8 o superior  
- Entorno Swing compatible  
- NetBeans (opcional, para integración con la paleta)  

## Instalación

1. Clona el repositorio o descarga el archivo `.jar`.  
2. Agrega el `.jar` a tu proyecto Java.  
3. Para NetBeans, coloca el `.jar` en la carpeta de módulos si deseas integración con la paleta.  

## Uso Básico

```java
import com.weatherComponent.WeatherComponent;
import javax.swing.*;

public class Main {
    public static void main(String[] args) {
        JFrame frame = new JFrame("Weather App");
        frame.setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
        
        WeatherComponent weather = new WeatherComponent();
        weather.setCity("Barcelona");
        weather.setTemperature(22);
        weather.setWeatherCondition("Soleado");
        
        frame.add(weather);
        frame.pack();
        frame.setVisible(true);
    }
}
```

## Configuración

### Personalización Visual

```java
// Cambiar colores del gradiente
weather.setBackgroundColor1(new Color(120, 180, 255)); // Azul claro
weather.setBackgroundColor2(new Color(70, 120, 210));  // Azul oscuro

// Cambiar color del texto
weather.setTextColor(Color.WHITE);
```

### Datos Meteorológicos

```java
// Establecer ciudad
weather.setCity("Madrid");

// Establecer temperatura (en °C)
weather.setTemperature(18);

// Establecer condición climática
weather.setWeatherCondition("Nublado");
```

## Integración con NetBeans

Este componente incluye soporte para la paleta de NetBeans:

- Agrega el archivo `.jar` a tu proyecto en NetBeans.  
- El componente aparecerá automáticamente en la paleta de componentes.  
- Puedes arrastrarlo y soltarlo directamente en tu formulario.  
- Personaliza sus propiedades desde el inspector de propiedades.

## Propiedades

| Propiedad          | Tipo   | Descripción                          |
|--------------------|--------|--------------------------------------|
| `city`             | String | Nombre de la ciudad a mostrar        |
| `temperature`      | int    | Temperatura en grados Celsius        |
| `backgroundColor1` | Color  | Color superior del gradiente         |
| `backgroundColor2` | Color  | Color inferior del gradiente         |
| `textColor`        | Color  | Color del texto                      |
| `weatherCondition` | String | Condición climática                  |

## Métodos

### Métodos Principales

- `setCity(String city)`: Establece la ciudad a mostrar.  
- `setTemperature(int temp)`: Establece la temperatura.  
- `setWeatherCondition(String condition)`: Establece la condición climática.  

### Métodos de Configuración Visual

- `setBackgroundColor1(Color color)`: Establece el color superior del gradiente.  
- `setBackgroundColor2(Color color)`: Establece el color inferior del gradiente.  
- `setTextColor(Color color)`: Establece el color del texto.  

### Método de Integración con NetBeans

- `createPaletteComponent()`: Crea una instancia para que el componente esté disponible en la paleta de NetBeans.

![Captura de pantalla (33)](https://github.com/user-attachments/assets/5060a55a-4960-4fb3-82b7-7c3b89e56559)

## Licencia

**MIT License**

```text
MIT License

Copyright (c) 2025 CeC Solutions

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
SOFTWARE.
```
