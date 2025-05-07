# WeatherComponent - Componente de Clima para Java Swing

![WeatherComponent Screenshot](ruta/a/la/imagen.png)

## Tabla de Contenidos
- [Características](#características)
- [Requisitos](#requisitos)
- [Instalación](#instalación)
- [Uso Básico](#uso-básico)
- [Configuración](#configuración)
  - [Personalización Visual](#personalización-visual)
  - [Datos Meteorológicos](#datos-meteorológicos)
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
- NetBeans (para integración con palette, opcional)  

## Instalación
1. Clona el repositorio o descarga el archivo `.jar`
2. Agrega el `.jar` a tu proyecto Java
3. Para NetBeans, coloca el `.jar` en la carpeta de módulos

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
