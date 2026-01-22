# Directivas de grupo

## Carpeta compartida
Para esta GPO es necesario antes un carpeta compartida donde se alojará el fondo de escritorio. Para ello, se creará una en E:\ 
Botón derecho > Compartir > Uso compartido avanzado
![Compartir carpeta 1](../../assests/images/aso/ud6/act5/compartir_carpeta_1.png)
![Compartir carpeta 2](../../assests/images/aso/ud6/act5/compartir_carpeta_2.png)
![Compartir carpeta 3](../../assests/images/aso/ud6/act5/compartir_carpeta_3.png)
![Compartir carpeta 4](../../assests/images/aso/ud6/act5/compartir_carpeta_4.png)

## Crear GPO
Herramientas > Administración de directivas de grupo > Bosque > Dominio > Objetos de directiva de grupo > Botón derecho > Nuevo
![GPO 1](../../assests/images/aso/ud6/act5/gpo_1.png)
![GPO 2](../../assests/images/aso/ud6/act5/gpo_2.png)
Una vez creada, se editará para seleccionar la GPO correspondiente al fondo de pantalla.
Configuración de usuario > Directivas > Plantillas administravias > Active Desktop > Active Desktop > Tapiz de escritorio
![GPO 3](../../assests/images/aso/ud6/act5/gpo_3.png)
![Tapiz de escritorio 1](../../assests/images/aso/ud6/act5/tapiz_escritorio_1.png)
![Tapiz de escritorio 2](../../assests/images/aso/ud6/act5/tapiz_escritorio_2.png)
Como también se requiere que el usuario no pueda realizar cambios, se habilitará la GPO "No permitir cambios"
![No changes](../../assests/images/aso/ud6/act5/no_cambios.png)
![No changes 2](../../assests/images/aso/ud6/act5/no_cambios_2.png)

## Vincular GPO a Objeto
En este caso asignaremos la GPO a la unidad organizativa. Botón derecho > Vincular GPO existente...
![Vincular GPO 1](../../assests/images/aso/ud6/act5/vincular_gpo_1.png)
![Vincular GPO 2](../../assests/images/aso/ud6/act5/vincular_gpo_2.png)
A continuación, en el servidor, se ejecutará "gpupdate /force" para actualizar las GPOs
![Actualizar GPO](../../assests/images/aso/ud6/act5/actualizar_gpo.png)
