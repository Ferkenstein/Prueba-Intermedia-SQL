# Ejercicio 2

Crear con DDL una tabla empleado que contenga lo siguiente:

1. IdEmpleado
2. nombre
3. apellido
4. dirección
5. teléfono
6. idDepartamento.

## Creación de Tabla

```SQL
CREATE TABLE EMPLEADOS (
idEmpleado INTEGER NOT NULL,
idDepartamento INTEGER NOT NULL,
nombre VARCHAR2(50),
apellido VARCHAR2(50),
dirección VARCHAR2(50),
teléfono INTEGER NOT NULL,
PRIMARY KEY (idEmpleado, idDepartamento)
);
```

