# ABBDD_P01
Práctica 01 - Administración de Bases de Datos
Realizada por Andrés Hernández Ortega y Luka Kravarusic Sljapic

Proyecto draw.io: https://drive.google.com/file/d/1jHXklJKXHCFSk1o-k9NsDQ2-O7wiioGj/view?usp=drive_link
# Modelo entidad-relación 
![Modelo entidad-relación](/practica1.drawio.png)


# Entidades definidas
## Medicamento
- Un medicamento contiene un NOMBRE
- Se debe indicar si es con o sin RECETA 
- Pertenece a una o varias FAMILIA de medicamentos en función de las enfermedades para las que se puede preinscribir (multivaluado)
- Tiene un PRECIO en euros
- Es de un TIPO en función de si es jarabe, comprimido, pomada,...
- Se almacena el número de UNIDADES VENDIDAS
- Se almacena el número de UNIDADES EN STOCK
- Puede poseer un CÓDIGO de LABORATORIO, en función de si ha sido fabricado en una laboratorio o por la propia farmacia
- Todo medicamento posee un CÓDIGO
Por tanto, un medicamento no puede contener un mismo código y código de laboratorio a la vez.
- **Identificadores**: 'Código' y 'Código Laboratorio'

### Ejemplo
- NOMBRE: Paracetamol
- RECETA: SÍ
- FAMILIA: analgésico, antipirético
- PRECIO:3
- TIPO: comprimido
- UNIDADES VENDIDAS: 164
- UNIDADES EN STOCK: 200
- CÓDIGO LABORATORIO: 0011
- CÓDIGO: 0057

## Laboratorio
- Existe una o varias PERSONA de CONTACTO como representante del laboratorio (multivaluado)
- Se almacena el o los números de FAX (multivaluado)
- Se almacena el o los números de TELÉFONO (multivaluado)
- Los laboratorios contienen un CÓDIGO único 
- Poseen un NOMBRE 
- Se ubican en una DIRECCIÓN (atributo compuesto):
  	- Cuenta con una CALLE
  	- Un NÚMERO de calle
  	- Pertenece a un MUNICIPIO
  	- Pertenece a una PROVINCIA
- **Identificador**: 'Código'

### Ejemplo
- PERSONA CONTACTO: Felipe González Armas, María José Gómez López
- FAX: 922 000 000, 928 000 000
- TELÉFONO: 608 000 000, 607 000 000
- CÓDIGO: 0034
- NOMBRE: Candelaria Lab
- DIRECCIÓN:
  	- CALLE: Av. Marítima
  	- NÚMERO: 45
  	- MUNICIPIO: Candelaria
  	- PROVINCIA: Santa Cruz de Tenerife
  
## Pedido
- Un pedido contiene una FECHA DE COMPRA
- Hay un NÚMERO DE PEDIDO que es único
- Existe una FECHA DE PAGO para el pedido, que puede ser NULL en caso de que sea realizado por un cliente con crédito y que, hasta que no realice el pago, no tendrá asignado un valor. En los casos de pago inmediato, es decir, clientes que no son con crédito, se le asignaría una fecha de pago-
- **Identificador**:  'Número de pedido'
  
### Ejemplo
- FECHA DE COMPRA: 06/10/2024
- NÚMERO DE PEDIDO: 0064
- FECHA DE PAGO: 06/10/2024
- MEDICAMENTOS:
	- NOMBRE: Paracetamol
	- RECETA: No
	- FAMILIA: analgésico, antipirético
	- PRECIO:3
	- TIPO: comprimido
	- UNIDADES VENDIDAS: 164
	- UNIDADES EN STOCK: 200
	- CÓDIGO LABORATORIO: 0011
	- CÓDIGO: 0057
	- UNIDADES: 3


## Clientes con crédito
- Un cliente con crédito posee un NOMBRE
- También posee unos APELLIDOS
- Se almacena la DIRECCIÓN (atributo compuesto):
	- Cuenta con una CALLE
  	- Un NÚMERO de calle
  	- Pertenece a un MUNICIPIO
  	- Pertenece a una PROVINCIA 
- Se guarda el NÚMERO DE TELÉFONO para los casos en los que sea necesario contactar 
- El NÚMERO de CUENTA IBAN para realizar los pagos según los plazos establecidos
- CÓDIGO que es único para el cliente y que sirve para identificarle de manera inequívoca
- El atributo PLAZOS DE PAGO indica el número de días respecto a las fechas de compras por la que se pasarán las cuantías pendientes de los diferentes pedidos realizados 
- **Identificador**: 'Código'

### Ejemplo
- NOMBRE: María
- APELLIDOS: Pino Sánchez
- DIRECCIÓN: Av. General Pérez, 23. Chipude. La Gomera. Santa Cruz de Tenerife
- NÚMERO DE TELÉFONO: 608934455
- NÚMERO CUENTA IBAN: ES66 0019 0020 9612 3456 7890
- CÓDIGO: 0025
- PLAZOS DE PAGO: 30

# Relaciones entre entidades

## Medicamento-Laboratorio
Un medicameneto puede no ser fabricado por ningún laboratorio, en los casos en los que lo hace la propia farmacia, o por varios laboratorios. 

Un laboratorio puede fabricar como mínimo un medicamento y como máximo un número indefinido (muchos) medicamentos. 

## Medicamento-Pedido
Un medicamento puede estar contenido en ningún o varios pedidos.
Un pedido debe estar compuesto por al menos un medicamento, pudiendo ser muchos medicamentos los que lo componen. En la relación se establece el número de unidades que un cliente puede adquirir de medicamentos.


## Pedido-Cliente con crédito
Un pedido puede estar realizado por ninguno o un cliente con crédito.
Un cliente con crédito puede no realizar ningún pedido o varios.


# Esquema de ejemplos
![Esquema de ejemplos](/ejemplo_farmacia.png)

