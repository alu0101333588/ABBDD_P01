# ABBDD_P01
Práctica 01 - Administración de Bases de Datos
Realizada por Andrés Hernández Ortega y Luka Kravarusic Sljapic

Proyecto draw.io: https://drive.google.com/file/d/1jHXklJKXHCFSk1o-k9NsDQ2-O7wiioGj/view?usp=drive_link



## Medicamento
- Un medicamento contiene un NOMBRE 
- Se debe indicar si es con o sin RECETA 
- Pertenece a una o varias FAMILIA de medicamentos en función de las enfermedades para las que se puede preinscribir
- Tiene un PRECIO
- Es de un TIPO en función de si es jarabe, comprimido, pomada,...
- Se almacena el número de UNIDADES VENDIDAS
- Se almacena el número de UNIDADES EN STOCK
- Puede poseer un CÓDIGO de LABORATORIO, en función de si ha sido fabricado en una laboratorio o por la propia farmacia
- Todo medicamento posee un CÓDIGO
Por tanto, un medicamento no puede contener un mismo código y código de laboratorio a la vez.

## Laboratorio
- Existe una PERSONA de CONTACTO como representante del laboratorio
- Se almacena el número de FAX
- Se almacena el número de TELÉFONO
- Los laboratorios contienen un CÓDIGO único 
- Poseen un NOMBRE 
- Se ubican en una DIRECCIÓN POSTAL

