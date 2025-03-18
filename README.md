# Solución a graphics.h en Vs Code

# Recomendaciones para la configuración del compilador

## Requisitos importantes

Antes de proceder, asegúrese de **no tener ningún compilador de C instalado**, como:
- TDM-GCC
- MinGW
- Clang

## Causa del problema
El problema de compatibilidad se debe a que la librería gráfica utilizada es antigua y está diseñada específicamente para un compilador de 32 bits. Por lo tanto, será necesario instalar una versión compatible.

## Solución propuesta: TDM-GCC 32 bits
Se recomienda instalar la versión de **TDM-GCC de 32 bits**, la cual puede descargarse desde el siguiente enlace:

[TDM-GCC 32-bit - Versión 10.3.0](https://jmeubank.github.io/tdm-gcc/articles/2021-05/10.3.0-release)

**IMPORTANTE**: Asegúrese de descargar exclusivamente la versión de **32 bits**.
<div aling = "center">
  <img src="https://github.com/user-attachments/assets/7190aa30-08d5-4ea7-8d69-9a789a1f5356">
</div>
![image]()

## Pasos para la instalación
1. Descargue el instalador desde el enlace proporcionado.
2. Ejecute el instalador y seleccione la opción **"Create"** al iniciar.
3. Siga el asistente de instalación:
   - Seleccione "NEXT".
   - Una vez más, haga clic en "NEXT".
4. Finalice la instalación.

---

¡Con estos pasos estará listo para compilar sus proyectos utilizando TDM-GCC de 32 bits!
