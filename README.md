# WeatherComponent - Componente de Clima para Java Swing

![WeatherComponent Screenshot](./docs/assets/component-screenshot.png)

Un componente visual personalizado para Java Swing que muestra información meteorológica en tiempo real.

## Características Principales
- Muestra temperatura en °C o °F (configurable)
- Gradiente de fondo personalizable
- Íconos climáticos dinámicos (sol, nubes)
- Actualización automática de datos
- Manejo de errores y estados de conexión
- Integración sencilla con NetBeans y otros IDEs

## Requisitos
- Java 8+
- Dependencias:
  - org.json (para procesamiento de JSON)

## Instalación
1. Clona este repositorio
2. Importa el proyecto en tu IDE favorito
3. Agrega el JAR resultante a tu proyecto o inclúyelo como dependencia Maven

## Uso Básico
```java
WeatherComponent weather = new WeatherComponent();
weather.setCity("Madrid");
frame.add(weather);

##Configuracion
// Cambiar ciudad y actualizar datos
weather.setCity("Barcelona");

// Cambiar a Fahrenheit
weather.setShowFahrenheit(true);

// Personalizar colores
weather.setBackgroundColor1(new Color(120, 180, 255));
weather.setBackgroundColor2(new Color(70, 120, 210));
weather.setTextColor(Color.WHITE);

### Diagrama de Clases
```mermaid
classDiagram
    class WeatherComponent {
        -apiKey: String
        -tempC: double
        -city: String
        -backgroundColor1: Color
        -backgroundColor2: Color
        -textColor: Color
        -weatherCondition: String
        -showFahrenheit: boolean
        -loading: boolean
        -initialized: boolean
        -hasNetwork: boolean
        
        +WeatherComponent()
        +actualizarClima(): void
        +getCity(): String
        +setCity(String): void
        +getTemperature(): double
        +setTemperature(double): void
        +isShowFahrenheit(): boolean
        +setShowFahrenheit(boolean): void
        +getBackgroundColor1(): Color
        +setBackgroundColor1(Color): void
        +getBackgroundColor2(): Color
        +setBackgroundColor2(Color): void
        +getTextColor(): Color
        +setTextColor(Color): void
        +getWeatherCondition(): String
        +isLoading(): boolean
        +createPaletteComponent(): Component
        -checkNetwork(): void
        -setupComponentListeners(): void
        -paintComponent(Graphics): void
        -drawCityName(Graphics2D): void
        -drawTemperature(Graphics2D): void
        -drawWeatherCondition(Graphics2D): void
        -drawLoadingIndicator(Graphics2D): void
        -drawWeatherIcon(Graphics2D): void
        -drawSunIcon(Graphics2D): void
        -drawCloudIcon(Graphics2D): void
        -drawErrorIcon(Graphics2D): void
    }
