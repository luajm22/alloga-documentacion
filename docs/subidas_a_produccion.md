<div id='id_subir_a_produccion' />

## Subidas a producción

<div id='id_subir_visual_a_produccion' />

### Subir Visual Basic a producción

**Paso 1.** Modificamos el archivo original **.frm** en el ambiente de pruebas.

**Paso 2.** Se crea el ejecutable **.exe** en el ambiente de pruebas, que es donde hemos hecho nuestras modificaciones.

Para crear el ejecutable: Archivo > Generar **nombre_ejecutable**

Es necesario crear una copia de seguridad del ejecutable anterior.

**Paso 3.** Se copia el **.frm** en el SVN. 

**Paso 4.** En este paso se presentan dos opciones:
1. En el servidor **borox-ts-prd** están ejecutándose 4 procesos: Productividades, Informes, Vincilab y SII-AH.
Si se hace una mopdificación en alguno de estos 4 proscesos, es necesario realizar las modificaciones en el servidor **borox-ts-prd**  [Ver pasos](#id_modificaciones_borox).
2. En caso de no modificar ninguno de estos 4 procesos, realizaríamos las modificaciones en el servidor de **producción** [Ver pasos](#id_modificaciones_produccion).

<div id='id_modificaciones_borox' />

#### Modificaciones en el servidor **borox-ts-prd**.

1. En la carpeta del Traductor que hemos modificado hacemos las copias de seguridad de los archivos **.frm** y **.exe**.
2. Detenemos el proceso (vemos en pantalla que se está ejecutando), el proceso de detención puede llevar un tiempo en caso de que tenga alguna tarea incompleta. Una vez que se haya detenido, lo cerramos.
3. Copiamos el **.frm** y el **.exe** del ambiente de pruebas a producción.
4. Generamos el acceso directo y lo reemplazamos en el Escritorio del servidor.
5. Ejecutamos el servicio (debemos volver a verlo por pantalla, como estaba al principio). Lanzamos la ejecución del servicio desde el Acceso Directo que acabamos de crear en el escritorio para verificar que esté funcionado correctamente.

<div id='id_modificaciones_produccion' />

#### Modificaciones en el servidor \\\10.20.4.38
 
En caso de no modificar ninguno de estos 4 procesos, realizaríamos las modificaciones en:

```
\\10.20.4.38 Producción
```
1. Abrimos el archivo **apps.ini.** almacenado en la ruta:
```
C:\Programacion\Aplicaciones
```

2. Hacemos un comentario (#) a la línea del ejecutable correspondiente y guardamos el archivo.

3. Hacemos las copias de seguridad de los archivos **.frm** y **.exe**.
4. Cortar y pegar las copias de seguridad en la ruta:
```
\\10.20.4.38\Programacion\Aplicaciones\Versiones antiguas
```
5. Detenemos el proceso (vemos en pantalla que se está ejecutando), el proceso de detención puede llevar un tiempo en caso de que tenga alguna tarea incompleta. Una vez que se haya detenido, lo cerramos.

6. Copiamos el **.frm** y lo dejamos en la carpeta correspondiente del traductor:
```
\\10.20.4.38\Programacion\
```

7. Copiamos el **.exe** en la carpeta:
```
\\10.20.4.38\Programacion\Aplicaciones\
```

8. Quitamos el comentario (#) a la línea del ejecutable correspondiente en el archivo **apps.ini.** que modificamos en el paso 2 y guardamos el archivo.

9. Validamos que el programa quede ejecutándose.

<div id='id_subir_plsql_a_produccion' />

### Subir PL/SQL a producción

1. Obtenemos el bloqueo del fuente en SVN.
2. Modificamos el objeto en el ambiente de desarrollo.
3. Copiamos el **.sql** en el SVN.
4. Comparar el **.sql** de producción con el que hemos modificado para verificar que no haya cambios no deseados.
5. Ejecutamos/Compilamos el **.sql** en producción.
6. Hacer Commit en SVN.

