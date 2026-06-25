# 🌐 Innovatech Chile - Cliente Web

Este repositorio alberga la aplicación Frontend de Innovatech Chile, encargada de proporcionar una interfaz intuitiva para la gestión de pedidos y procesos logísticos. Desde esta plataforma, los usuarios pueden consultar órdenes, monitorear estados de despacho y administrar información relacionada con las entregas.

## 🏛️ Infraestructura de la Aplicación

La aplicación se distribuye como una imagen Docker y se ejecuta dentro de un entorno Kubernetes administrado mediante Amazon EKS. La exposición del servicio hacia Internet se realiza a través de un balanceador de carga configurado automáticamente por Kubernetes, permitiendo un acceso seguro y escalable.

## 🛠️ Configuración y Ejecución Local

### Requisitos

* Node.js 16 o superior
* npm o yarn

### Instalación

1. Obtener una copia del repositorio:

```bash
git clone https://github.com/DoomedPlayer/DevopsEV3-front.git
```

2. Instalar las librerías necesarias:

```bash
npm install
```

3. Definir las variables de entorno del proyecto:

Crear un archivo `.env` en la carpeta raíz y configurar las direcciones de los servicios backend.

```bash
VITE_URL_VENTAS=http://localhost:8082
VITE_URL_DESPACHOS=http://localhost:8081
```

Durante el desarrollo se utilizan endpoints locales, mientras que en producción se emplean las direcciones públicas entregadas por la infraestructura AWS.

4. Levantar el entorno de desarrollo:

```bash
npm run dev
```

## 🔄 Automatización de Entrega (CI/CD)

La publicación de nuevas versiones está automatizada mediante GitHub Actions. Cuando se reciben cambios en la rama principal, se ejecuta el siguiente proceso:

### Flujo de Despliegue

1. Instalación de dependencias y construcción de la aplicación React.

2. Generación de la imagen Docker correspondiente al Frontend.

3. Envío de la imagen hacia un repositorio privado alojado en Amazon ECR.

4. Actualización automática del Deployment en Amazon EKS utilizando herramientas de Kubernetes.

5. Uso de GitHub Secrets para proteger credenciales, tokens y variables sensibles relacionadas con AWS.

Gracias a este proceso, las nuevas versiones pueden publicarse con mínima interrupción del servicio y de forma completamente automatizada.
