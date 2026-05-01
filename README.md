cada archivo puede ser creado en un solo archivo main.cpp
sin embargo con el fin de ser más claro
decidí separar las funciones

Tambien se debe ejecutar este codigo en MySQL Workbench 

CREATE DATABASE universidad;
USE universidad;

CREATE TABLE alumnos (
    id INT AUTO_INCREMENT PRIMARY KEY,
    nombres VARCHAR(100),
    apellidos VARCHAR(100),
    carnet VARCHAR(20)
);

CREATE TABLE cursos (
    id INT AUTO_INCREMENT PRIMARY KEY,
    nombre VARCHAR(100),
    codigo VARCHAR(20)
);

CREATE TABLE secciones (
    id INT AUTO_INCREMENT PRIMARY KEY,
    nombre VARCHAR(50),
    jornada VARCHAR(50)
);

CREATE TABLE alumnos_cursos (
    id INT AUTO_INCREMENT PRIMARY KEY,
    alumno_id INT,
    curso_id INT,
    UNIQUE(alumno_id, curso_id),
    FOREIGN KEY (alumno_id) REFERENCES alumnos(id),
    FOREIGN KEY (curso_id) REFERENCES cursos(id)
);

CREATE TABLE alumnos_seccion (
    id INT AUTO_INCREMENT PRIMARY KEY,
    alumno_id INT UNIQUE,
    seccion_id INT,
    FOREIGN KEY (alumno_id) REFERENCES alumnos(id),
    FOREIGN KEY (seccion_id) REFERENCES secciones(id)
);
