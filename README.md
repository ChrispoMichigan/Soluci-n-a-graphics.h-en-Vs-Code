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
<div align="center">
    <img src="https://github.com/user-attachments/assets/7190aa30-08d5-4ea7-8d69-9a789a1f5356" alt="Version" />
</div>

## Pasos para la instalación
1. Descargue el instalador desde el enlace proporcionado.
2. Ejecute el instalador y seleccione la opción **"Create"** al iniciar.
<div align="center">
    <img src="https://github.com/user-attachments/assets/b32b6d32-6cc4-4827-a503-4a0118d51a41" alt="option" />
</div>
4. Siga el asistente de instalación:
   - Seleccione la versión de 32 bits
  <div align="center">
    <img src="https://github.com/user-attachments/assets/b9ef5652-fb15-4a43-9af8-02516f80c678" alt="option" />
  </div>
   - Seleccione "NEXT". <br>
   - Una vez más, haga clic en "NEXT". <br>
5. Finalice la instalación.

## Archivos requeridos

Una vez completada la instalación del compilador, descargue los siguientes archivos necesarios desde el repositorio:

- **graphics.h**  
- **libbgi.a**  
- **winbgim.h**

Asegúrese de colocarlos en las rutas adecuadas para que el programa funcione correctamente:
- `graphics.h` y `winbgim.h`: Colóquelos en la carpeta `include` del compilador. Ejemplo:
<div align="center">
  
`C:\TDM-GCC-32\include`
</div>

- `libbgi.a`: Colóquelo en la carpeta `lib` del compilador. Ejemplo:
<div align="center">
  
`C:\TDM-GCC-32\lib`
</div>

## Fuente de los archivos

Estos archivos se encuentran originalmente en el siguiente repositorio:

[Solução para graphics.h - Kumar Baberwal](https://github.com/kumarbaberwal/Solution-to-graphics.h/tree/main)

---
## Configuración de Visual Studio Code

1. **Abrir un nuevo proyecto** en Visual Studio Code con un archivo llamado `main.cpp`.  
   **Nota**: La librería `graphics.h` solo funcionará en archivos con extensión `.cpp`.

2. **Extensión**  
   Para mayor comodidad y evitar compilar desde la terminal, instalar una extensión que facilite la ejecución del programa y permita que se reconozcan las librerías necesarias.
   - Puedes buscar extensiones como **Code Runner** en el Marketplace de VS Code.
<div align="center">
    <img src="https://github.com/user-attachments/assets/5c94c541-cc15-4456-a080-92cc4b706667" alt="Code Runner" />
</div>

4. **Abrir la configuración de la extensión**  
   Una vez instalada, haz lo siguiente:
   - Selecciona el botón de engranaje ⚙️ junto a la extensión en la lista de extensiones.
   - Haz clic en la opción **Configuración**.
   
<div align="center">
    <img src="https://github.com/user-attachments/assets/0c27bfbf-be2e-491a-85d7-1308bb1ce889" alt="Code Runner" />
</div>
<div align="center">
    <img src="https://github.com/user-attachments/assets/c5f48395-6010-4cd6-b5d3-62cb7dbd3ffa" alt="Code Runner" />
</div>

4. **Configurar extensión**
   Bajaremos hasta `Code-runner: Executor Map` y seleccionaremos en `Editar en settings.json`
   <div align="center">
    <img src="https://github.com/user-attachments/assets/374cccf0-282c-43d1-b12c-f28d540a06bb" alt="Code Runner" />
</div>

   Buscaremos dentro del archivo el `"cpp:"`, lo cambiaremos por la siguiente linea:
<div align="center">
  
    "cpp": "cd $dir && g++ $fileName -o $fileNameWithoutExt -lbgi -lgdi32 -lcomdlg32 -luuid -loleaut32 -lole32 && $dir$fileNameWithoutExt"
</div>
  Debe verse de la siguiente forma
<div align="center">
    <img src="https://github.com/user-attachments/assets/2280679b-77bc-45cd-b3a7-0cb20bbe6944" alt="Code Runner" />
</div>

  Guardamos y salimos a nuestro archivo principal
  
## Nota importante: Configuración del antivirus

Para poder ejecutar el código correctamente, será necesario **deshabilitar el antivirus** del sistema operativo. Esto incluye:

- **El antivirus de Windows** (Windows Defender).
- Cualquier otro antivirus que esté instalado en el sistema. <br>
<br>
Ejemplo en Windows 11:

Seleccionar `Administrar la configuración`
<div align="center">
    <img src="https://github.com/user-attachments/assets/212443a1-25e9-4f7e-b8f0-f812872f5b77" alt="Code Runner" />
</div>

Desactivar `Protección en tiempo real`
<div align="center">
    <img src="https://github.com/user-attachments/assets/5c91548e-f5d9-4296-b0a1-5c4d601d5e46" alt="Code Runner" />
</div>

La razón de este paso es que algunos antivirus pueden interferir con la ejecución de programas gráficos como los que usan la librería `graphics.h`. 

---

⚠️ **Recuerda habilitar el antivirus una vez que termines de trabajar para proteger tu sistema.**

## Ejemplo de código con `main.cpp`

```cpp
#include <graphics.h>
#include <conio.h>

int main() {
    int gd = DETECT, gm;
    initgraph(&gd, &gm, (char*)"");

    circle(200, 200, 50);
    getch();
    closegraph();
    return 0;
}
```
## Ejecución y salida esperada

Al ejecutar el programa correctamente, debería generarse una ventana gráfica con la siguiente salida:
<div align="center">
    <img src="https://github.com/user-attachments/assets/6b8df63d-337f-45b6-a124-994a67e51525" alt="Code Runner" />
</div>

## Apoya al repositorio

Si este repositorio te fue de ayuda, considera dejar una ⭐ en el repositorio. 
