# Sobel_HLS_ZYBO

Detector de contornos SOBEL en SoC Zybo de Xilinx.

El proyecto se desarrolló utilizando la plataforma de desarrollo ZYBO y las herramientas de Xilinx. La placa ZYBO se basa en la arquitectura AP SoC y está integrada por un procesador de doble núcleo ARM Cortex-A9 y una FPGA XC7Z010-1-CLG400C. 

La implementación del detector SOBEL se desarrolló en lenguaje de alto nivel con la herramienta Vivado HLS 2019.1 y la integración del sistema se realizó en Vivado 2019.1. La pruebas reales se realizaron con dos imágenes obtenidas de repositorios públicos denominadas Mandril (512x512) y Kodim23 (768x512) y la herramienta XSDK 2019.1.

El diseño permite procesar imágenes de hasta 1920 x 1080 píxeles (Full HD) pero se puede extender. Se recomienda utilizar Vivado 2019.1 para evitar problemas de compatibilidad

Pasos para utilizar el proyecto

1) En vivado HLS sintetizar y exportar los bloques edge_detect, rgb2gray y u8tou32.

2) En vivado 2019.1, crear un proyecto nuevo y agregar los repositorios de los ip generados (edge_detect, rgb2gray y u8tou32)

3) Ejecutar system.tcl (source <path to file>/system.tcl)
  
4) Crear la envoltura HDL al diseño de bloques (HDL wrapper) y generar el bitstream

5) Exportar el hardware y ejecutar XSDK

6) Crear un proyecto de apliación vacío con el nombre edgeDetect e importar los archivos "cabecera.h" y "edgeDetect.c"

7) Modificar el paquete de soporte de la placa (Board Support Package) e incorporar la librería xilffs (Generic Fat File System Library)

8) Almacenar las imágenes de prueba en una microSD. Incorporar la microSD en la placa ZYBO. 

9) Conectar la placa ZYBO a la pc y ejecutar la aplicación edgeDetect. 








