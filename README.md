# WeatherComponent - Componente de Clima para Java Swing


![Screenshot 2025-05-07 094346](https://github.com/user-attachments/assets/21f3c486-1d62-4c61-8097-3e11b1dbd246)


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

## Codigo Completo
### Clase funcional con API
```java
package com.weatherComponent;

import com.weatherComponent.WeatherComponent;
import java.beans.BeanDescriptor;
import java.beans.IntrospectionException;
import java.beans.PropertyDescriptor;
import java.beans.SimpleBeanInfo;

public class WeatherComponentBeanInfo extends SimpleBeanInfo {

    @Override
    public PropertyDescriptor[] getPropertyDescriptors() {
        try {
            PropertyDescriptor city = new PropertyDescriptor("city", WeatherComponent.class);
            city.setShortDescription("Nombre de la ciudad para mostrar");

            PropertyDescriptor temperature = new PropertyDescriptor("temperature", WeatherComponent.class);
            temperature.setShortDescription("Temperatura en grados Celsius");

            PropertyDescriptor bgColor1 = new PropertyDescriptor("backgroundColor1", WeatherComponent.class);
            bgColor1.setShortDescription("Primer color del gradiente de fondo");

            PropertyDescriptor bgColor2 = new PropertyDescriptor("backgroundColor2", WeatherComponent.class);
            bgColor2.setShortDescription("Segundo color del gradiente de fondo");

            PropertyDescriptor textColor = new PropertyDescriptor("textColor", WeatherComponent.class);
            textColor.setShortDescription("Color del texto");

            PropertyDescriptor condition = new PropertyDescriptor("weatherCondition", WeatherComponent.class);
            condition.setShortDescription("Condición climática (Soleado, Nublado, Lluvioso)");

            return new PropertyDescriptor[]{city, temperature, bgColor1, bgColor2, textColor, condition};
        } catch (IntrospectionException ex) {
            ex.printStackTrace();
            return null;
        }
    }

    @Override
    public BeanDescriptor getBeanDescriptor() {
        BeanDescriptor descriptor = new BeanDescriptor(WeatherComponent.class);
        descriptor.setDisplayName("Componente del Clima");
        descriptor.setShortDescription("Un componente visual que muestra información meteorológica");
        return descriptor;
    }
}

```
### Clase que permite modificar las propiedades del componente
```java
package com.weatherComponent;

import java.awt.Color;
import java.awt.Font;
import java.awt.GradientPaint;
import java.awt.Graphics;
import java.awt.Graphics2D;
import java.awt.RenderingHints;
import javax.swing.JPanel;

public class WeatherComponent extends JPanel {

    private String city = "Madrid";
    private int temperature = 25;
    private Color backgroundColor1 = new Color(100, 150, 255);
    private Color backgroundColor2 = new Color(50, 100, 200);
    private Color textColor = Color.WHITE;
    private String weatherCondition = "Soleado";

    public WeatherComponent() {
        setPreferredSize(new java.awt.Dimension(200, 150));
    }

    @Override
    protected void paintComponent(Graphics g) {
        super.paintComponent(g);
        Graphics2D g2d = (Graphics2D) g;
        g2d.setRenderingHint(RenderingHints.KEY_ANTIALIASING, RenderingHints.VALUE_ANTIALIAS_ON);

        // Fondo con gradiente
        GradientPaint gradient = new GradientPaint(0, 0, backgroundColor1, getWidth(), getHeight(), backgroundColor2);
        g2d.setPaint(gradient);
        g2d.fillRect(0, 0, getWidth(), getHeight());

        // Dibujar icono del clima (simplificado)
        drawWeatherIcon(g2d);

        // Texto de la ciudad
        g2d.setColor(textColor);
        g2d.setFont(new Font("Arial", Font.BOLD, 16));
        g2d.drawString(city, 20, 30);

        // Temperatura
        g2d.setFont(new Font("Arial", Font.BOLD, 36));
        g2d.drawString(temperature + "°C", 20, 80);

        // Condición climática
        g2d.setFont(new Font("Arial", Font.PLAIN, 14));
        g2d.drawString(weatherCondition, 20, 110);
    }

    private void drawWeatherIcon(Graphics2D g2d) {
        // Icono simplificado según la condición
        g2d.setColor(new Color(255, 255, 255, 150));
        if (weatherCondition.toLowerCase().contains("sol")) {
            // Sol
            g2d.fillOval(getWidth() - 60, 20, 40, 40);
        } else if (weatherCondition.toLowerCase().contains("nub")) {
            // Nubes
            g2d.fillOval(getWidth() - 70, 20, 30, 30);
            g2d.fillOval(getWidth() - 50, 30, 40, 30);
            g2d.fillOval(getWidth() - 30, 20, 30, 30);
        } else if (weatherCondition.toLowerCase().contains("lluv")) {
            // Lluvia
            g2d.fillOval(getWidth() - 70, 20, 50, 30);
            for (int i = 0; i < 5; i++) {
                g2d.drawLine(getWidth() - 60 + i * 10, 50, getWidth() - 65 + i * 10, 60);
            }
        }
    }

    // Propiedades personalizables
    public String getCity() {
        return city;
    }

    public void setCity(String city) {
        this.city = city;
        repaint();
    }

    public int getTemperature() {
        return temperature;
    }

    public void setTemperature(int temperature) {
        this.temperature = temperature;
        repaint();
    }

    public Color getBackgroundColor1() {
        return backgroundColor1;
    }

    public void setBackgroundColor1(Color backgroundColor1) {
        this.backgroundColor1 = backgroundColor1;
        repaint();
    }

    public Color getBackgroundColor2() {
        return backgroundColor2;
    }

    public void setBackgroundColor2(Color backgroundColor2) {
        this.backgroundColor2 = backgroundColor2;
        repaint();
    }

    public Color getTextColor() {
        return textColor;
    }

    public void setTextColor(Color textColor) {
        this.textColor = textColor;
        repaint();
    }

    public String getWeatherCondition() {
        return weatherCondition;
    }

    public void setWeatherCondition(String weatherCondition) {
        this.weatherCondition = weatherCondition;
        repaint();
    }
    
    public static java.awt.Component createPaletteComponent(){
        WeatherComponent comp = new WeatherComponent();
        comp.setCity("Nueva Ciudad");
        comp.setTemperature(20);
        return comp;
    }
}

```

### Componente visual agregado en proyecto
Aca se puede ver una previsualizacion de como es el componente
![Captura de pantalla (33)](https://github.com/user-attachments/assets/5060a55a-4960-4fb3-82b7-7c3b89e56559)

Mostraremos algunas de las propiedades modificables que tiene este componente en este caso el color de el panel del componente.
![Captura de pantalla (35)](https://github.com/user-attachments/assets/d6f8e2b5-470a-4d42-8fc7-9a3aedf7b4f0)

El color de degradado del componente 
![Captura de pantalla (36)](https://github.com/user-attachments/assets/d22c2a8b-2698-4db6-b895-34936645e165)

La imgen con la cual eligiremos saber su clima
![image](https://github.com/user-attachments/assets/a01e1e3c-b9be-49cb-9121-7bfcc1008010)

Como un adicional podemos selccionar como mostrar la temperatura ya sea en celcius o Fahrenheit
![image](https://github.com/user-attachments/assets/5801be39-211d-4d19-8e9b-39d3ea5ffb74)

Si llegas a tner alguna duda para saber como se usa aca te dejamos un video donde te mostramos el paso a paso de como se usa:
https://www.youtube.com/watch?v=F22ZnhI_ve8&t=1s
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
