# Ejercicio 1

Dadas las siguientes tablas:

1. empleado (idEmpleado, nombreEmpleado, fechaIngreso)
2. servicio (idServicio, nombreServicio, valorServicio)
3. vehiculo (idVehiculo, marcaVehiculo, modeloVehiculo)
4. prestación_servicio (idPrestacionServicio, IdServicio, idEmpleado, idVehiculo, fecha)

a.-  Mostrar la cantidad de prestaciones de servicios ejecutados entre el 01 de octubre y el 26 de noviembre del 2018.

b.- Mostrar la cantidad total de prestaciones realizadas agrupadas por idVehiculo.

c.- Mostrar los vehículos con la menor cantidad de prestaciones de servicios realizados.


## Creación de Tablas

### Crear tabla Empleado

La tabla empleado tiene un id, nombre del empleado y fecha de ingreso.

```SQL
CREATE TABLE EMPLEADO (
idEmpleado INTEGER PRIMARY KEY NOT NULL,
nombreEmpleado VARCHAR2(50),
fechaIngreso DATE
);
```
### Crear tabla Servicio

La tabla servicio tiene un id, nombre del servicio y un valor asociado al servicio.

``` SQL
CREATE TABLE SERVICIO (
idServicio INTEGER PRIMARY KEY NOT NULL,
nombreServicio VARCHAR2(50),
valorServicio FLOAT
);
```
### Crear tabla Vehiculo

La tabla Vehiculo tiene un id, una marca del vehiculo y un modelo del vehiculo.

``` SQL
CREATE TABLE VEHICULO (
idVehiculo INTEGER PRIMARY KEY NOT NULL,
marcaVehiculo VARCHAR2(50),
modeloVehiculo VARCHAR2(50)
);
```

### Crear tabla Prestación de Servicio

La tabla Prestación de Servicio tiene un id, una fecha, el id de la tabla Empleado, Servicio y Vehiculo.

``` SQL
CREATE TABLE PRESTACION_SERVICIO (
idPrestacionServicio INTEGER PRIMARY KEY NOT NULL,
fecha DATE,
idEmpleado INTEGER,
idServicio INTEGER,
idVehiculo INTEGER
);

ALTER TABLE PRESTACION_SERVICIO ADD FOREIGN KEY (idEmpleado) REFERENCES EMPLEADO(idEmpleado);
ALTER TABLE PRESTACION_SERVICIO ADD FOREIGN KEY (idServicio) REFERENCES SERVICIO(idServicio);
ALTER TABLE PRESTACION_SERVICIO ADD FOREIGN KEY (idVehiculo) REFERENCES VEHICULO(idVehiculo);
```

# Ingreso de datos a tablas

###  Insertar Datos a tabla Empleado

``` SQL 
INSERT INTO "SYSTEM"."EMPLEADO" (IDEMPLEADO, NOMBREEMPLEADO, FECHAINGRESO) VALUES ('1', 'Fernando Ruiz', TO_DATE('2018-10-01 00:00:00', 'YYYY-MM-DD HH24:MI:SS'));
INSERT INTO "SYSTEM"."EMPLEADO" (IDEMPLEADO, NOMBREEMPLEADO, FECHAINGRESO) VALUES ('2', 'Francisco Perez', TO_DATE('2017-01-15 00:00:00', 'YYYY-MM-DD HH24:MI:SS'));
INSERT INTO "SYSTEM"."EMPLEADO" (IDEMPLEADO, NOMBREEMPLEADO, FECHAINGRESO) VALUES ('3', 'Rocio Lopez', TO_DATE('2017-03-24 00:00:00', 'YYYY-MM-DD HH24:MI:SS'));
INSERT INTO "SYSTEM"."EMPLEADO" (IDEMPLEADO, NOMBREEMPLEADO, FECHAINGRESO) VALUES ('4', 'Catalina Rosas', TO_DATE('2017-12-19 00:00:00', 'YYYY-MM-DD HH24:MI:SS'));
INSERT INTO "SYSTEM"."EMPLEADO" (IDEMPLEADO, NOMBREEMPLEADO, FECHAINGRESO) VALUES ('5', 'Pedro Perez', TO_DATE('2018-11-30 00:00:00', 'YYYY-MM-DD HH24:MI:SS'));

```
### Insertar Datos a tabla Servicio

``` SQL
INSERT INTO "SYSTEM"."SERVICIO" (IDSERVICIO, NOMBRESERVICIO, VALORSERVICIO) VALUES ('1', 'Limpieza' , '10000');
INSERT INTO "SYSTEM"."SERVICIO" (IDSERVICIO, NOMBRESERVICIO, VALORSERVICIO) VALUES ('2', 'Lavado', '10000');
INSERT INTO "SYSTEM"."SERVICIO" (IDSERVICIO, NOMBRESERVICIO, VALORSERVICIO) VALUES ('3', 'Cambio de Llantas', '5000');
INSERT INTO "SYSTEM"."SERVICIO" (IDSERVICIO, NOMBRESERVICIO, VALORSERVICIO) VALUES ('4', 'Lavado y Limpieza', '20000');
INSERT INTO "SYSTEM"."SERVICIO" (IDSERVICIO, NOMBRESERVICIO, VALORSERVICIO) VALUES ('5', 'Arreglo Motor' , '7000');
```

### Insertar Datos a tabla Vehiculo

``` SQL
INSERT INTO "SYSTEM"."VEHICULO" (IDVEHICULO, MARCAVEHICULO, MODELOVEHICULO) VALUES ('1', 'Suzuki' , 'Baleno');
INSERT INTO "SYSTEM"."VEHICULO" (IDVEHICULO, MARCAVEHICULO, MODELOVEHICULO) VALUES ('2', 'Nissan', 'Qashqai');
INSERT INTO "SYSTEM"."VEHICULO" (IDVEHICULO, MARCAVEHICULO, MODELOVEHICULO) VALUES ('3', 'Toyota', 'Yaris');
INSERT INTO "SYSTEM"."VEHICULO" (IDVEHICULO, MARCAVEHICULO, MODELOVEHICULO) VALUES ('4', 'Chevrolet', 'Spark');
INSERT INTO "SYSTEM"."VEHICULO" (IDVEHICULO, MARCAVEHICULO, MODELOVEHICULO) VALUES ('5', 'Suzuki' , 'Swift');
``` 

### Insertar Datos a tabla Prestación Servicio

``` SQL
INSERT INTO "SYSTEM"."PRESTACION_SERVICIO" (IDPRESTACIONSERVICIO, FECHA, IDEMPLEADO, IDSERVICIO, IDVEHICULO) VALUES ('1', TO_DATE('2018-10-01 00:00:00', 'YYYY-MM-DD HH24:MI:SS'), '3', '2', '1');
INSERT INTO "SYSTEM"."PRESTACION_SERVICIO" (IDPRESTACIONSERVICIO, FECHA, IDEMPLEADO, IDSERVICIO, IDVEHICULO) VALUES ('2', TO_DATE('2019-01-15 00:00:00', 'YYYY-MM-DD HH24:MI:SS'), '3', '1', '5');
INSERT INTO "SYSTEM"."PRESTACION_SERVICIO" (IDPRESTACIONSERVICIO, FECHA, IDEMPLEADO, IDSERVICIO, IDVEHICULO) VALUES ('3', TO_DATE('2018-12-19 00:00:00', 'YYYY-MM-DD HH24:MI:SS'), '2', '2', '3');
INSERT INTO "SYSTEM"."PRESTACION_SERVICIO" (IDPRESTACIONSERVICIO, FECHA, IDEMPLEADO, IDSERVICIO, IDVEHICULO) VALUES ('4', TO_DATE('2019-03-24 00:00:00', 'YYYY-MM-DD HH24:MI:SS'), '1', '3', '4');
INSERT INTO "SYSTEM"."PRESTACION_SERVICIO" (IDPRESTACIONSERVICIO, FECHA, IDEMPLEADO, IDSERVICIO, IDVEHICULO) VALUES ('5', TO_DATE('2018-11-30 00:00:00', 'YYYY-MM-DD HH24:MI:SS'), '5', '5', '2');
``` 

# Consultas

#### Mostrar la cantidad de prestaciones de servicios ejecutados entre el 01 de octubre y el 26 de noviembre del 2018.

``` SQL
SELECT * 
FROM PRESTACION_SERVICIO 
WHERE fecha 
BETWEEN TO_DATE ('2018/10/01', 'yyyy/mm/dd') AND TO_DATE ('2018/12/26', 'yyyy/mm/dd');

SELECT COUNT(*) 
FROM PRESTACION_SERVICIO 
WHERE fecha 
BETWEEN TO_DATE ('2018/10/01', 'yyyy/mm/dd') AND TO_DATE ('2018/12/26', 'yyyy/mm/dd');
``` 

#### Mostrar la cantidad total de prestaciones realizadas agrupadas por idVehiculo.

``` SQL
SELECT idVehiculo, COUNT(*) AS "TOTAL" 
FROM PRESTACION_SERVICIO 
GROUP BY idvehiculo;
```

#### Mostrar los vehículos con la menor cantidad de prestaciones de servicios realizados.

``` SQL
SELECT VEH.MarcaVehiculo, VEH.ModeloVehiculo, COUNT(*) as CantidadPrestaciones
FROM PRESTACION_SERVICIO PS
INNER JOIN VEHICULO VEH ON PS.IdVehiculo = VEH.IdVehiculo
GROUP BY PS.IdVehiculo, VEH.MarcaVehiculo, VEH.ModeloVehiculo
ORDER BY CantidadPrestaciones ASC
```