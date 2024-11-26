# parcial 1

## Pregunta 16 Base De Datos-Average Population

![Captura de pantalla 2024-11-25 182123](https://github.com/user-attachments/assets/2f5921ad-598e-4990-8e08-6cf9cccd9991)

### Resultado

![Captura de pantalla 2024-11-25 182437](https://github.com/user-attachments/assets/36f45ae5-7221-4fa2-9bbd-e70e424c8ef3)

## Pregunta 17 Base De Datos-Top Earners

![Captura de pantalla 2024-11-25 182758](https://github.com/user-attachments/assets/21ff4c33-7ad1-4bc3-93ac-8287d2f0d227)

### Resultado

![image](https://github.com/user-attachments/assets/af4631c9-2a34-430e-a7c3-f61c3360d142)

## Pregunta 18 Base De Datos-Population Census

![Captura de pantalla 2024-11-25 183605](https://github.com/user-attachments/assets/12d832de-5f1a-45f7-b62c-1827cc0a7ab8)

![Captura de pantalla 2024-11-25 183729](https://github.com/user-attachments/assets/7a467db1-9301-4344-8ebf-132449a2825d)

### resultado

![Captura de pantalla 2024-11-25 184201](https://github.com/user-attachments/assets/a51ac038-db10-4680-b6ed-6392c47ad0ab)

## Consultas Básicas

### 1. Listar los títulos únicos de los empleados que empiezan por 'S'

```sql
SELECT DISTINCT title
FROM titles
WHERE title LIKE 'S%';
```

![image](https://github.com/user-attachments/assets/a1a23611-e693-453e-a2cd-1a6cec06eebb)

### 2. Contar el número total de empleados en el departamento 'Sales' que empezaron después del '1989-01-01'

```sql

```

### 3. Calcular el salario promedio de los empleados que ganan más de 39.000. Imprimir solo 2 decimales redondeadas(comando ROUND())

```sql
SELECT ROUND(AVG(salary), 2) AS avg_salary
FROM employees e
JOIN salaries s ON e.emp_no = s.emp_no
WHERE s.salary > 39000;
```

![image](https://github.com/user-attachments/assets/9c918ad0-44f2-4ab6-b303-fe733ec11d9d)

### 4. Mostrar el número de empleados por departamento

```sql
SELECT 
    d.dept_name, 
    COUNT(*) AS num_employees
FROM 
    departments d
    JOIN dept_manager dm ON d.dept_no = dm.dept_no
    JOIN employees e ON dm.emp_no = e.emp_no
GROUP BY 
    d.dept_name
ORDER BY 
    num_employees DESC;
```

![image](https://github.com/user-attachments/assets/c3dd8c87-13e1-41c0-af58-1c62e3e1733b)

### 5. Filtrar empleados con salarios entre 39.000 y 40.000 y organizarlos en orden ascendente por salario

```sql
SELECT 
    e.emp_no,
    s.salary
FROM 
    employees e
    JOIN salaries s ON e.emp_no = s.emp_no
WHERE 
    s.salary BETWEEN 39000 AND 40000
ORDER BY 
    s.salary ASC;
```

![image](https://github.com/user-attachments/assets/8ae931b7-e585-4534-b164-4bd248c58151)


### 6. Encontrar el salario máximo y mínimo en la tabla `salaries`. Además, renombrarlos a `salario_maximo` y `salario_minimo`

```sql

```

### 7. Ordenar los empleados por fecha de contratación desde la más reciente a la más antigua

```sql
SELECT 
    emp_no, 
    hire_date
FROM 
    employees
ORDER BY 
    hire_date DESC;
```

![image](https://github.com/user-attachments/assets/edde6e82-c254-4b39-a5bf-de7038676666)

#### 8. Buscar empleados cuyo nombre contenga la silaba 'est', organizarlos en orden Alfabético

```sql
SELECT 
    emp_no, 
    first_name, 
    last_name
FROM 
    employees
WHERE 
    first_name LIKE '%est%'
    OR last_name LIKE '%est%'
ORDER BY 
    first_name ASC, 
    last_name ASC;
```

![image](https://github.com/user-attachments/assets/226b13e2-34b0-410e-9b65-194fb6414baa)

#### 9. Mostrar la cantidad de empleados con más de un título asignado. El empleado no debe salir repetido

```sql
SELECT 
    COUNT(DISTINCT e.emp_no) AS empleados_con_mas_de_un_titulo,first_name,last_name
FROM 
    employees e
    JOIN titles t ON e.emp_no = t.emp_no
GROUP BY 
    e.emp_no
HAVING 
    COUNT(t.title) > 1;
```

![image](https://github.com/user-attachments/assets/6c4fb377-637d-46ce-a89e-65acedd24045)

### 13. Listar los empleados que tienen múltiples títulos en la empresa

```sql
SELECT 
    e.emp_no, 
    e.first_name, 
    e.last_name, 
    GROUP_CONCAT(t.title) AS titles
FROM 
    employees e
    JOIN titles t ON e.emp_no = t.emp_no
GROUP BY 
    e.emp_no
HAVING 
    COUNT(t.title) > 1
ORDER BY 
    e.last_name, e.first_name;
```

![image](https://github.com/user-attachments/assets/dd6a2677-be0e-48a5-a4b6-4ca266d10f93)



