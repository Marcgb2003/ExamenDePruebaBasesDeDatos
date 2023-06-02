# ExamenDePruebaBasesDeDatos
1)
Select l.titulo 
from libros l inner join prestamos p on l.id_libro=p.id_libro
group by l.titulo
having l.titulo in (
Select l.titulo from libros l inner join prestamos p on l.id_libro=p.id_libro
where p.fecha_prestamo in (
select Min(fecha_prestamo) from prestamos))
![1](https://github.com/Marcgb2003/ExamenDePruebaBasesDeDatos/assets/122601138/a7baa6d9-1334-44fb-8017-eb92a5f6c766)

2)
Select l.titulo 
from libros l inner join prestamos p on l.id_libro=p.id_libro
group by l.titulo
having l.titulo not in (
Select l.titulo from libros l inner join prestamos p on l.id_libro=p.id_libro
where p.fecha_prestamo<NOW() - INTERVAL 6 MONTH)
![2](https://github.com/Marcgb2003/ExamenDePruebaBasesDeDatos/assets/122601138/a1ef0252-ba75-4d5a-afd0-57f34adfc1be)

3)
Select Month(p.fecha_prestamo)
from libros l inner join prestamos p on l.id_libro=p.id_libro
group by month(p.fecha_prestamo)
order by Count(p.id_prestamo) desc
Limit 1;
![3](https://github.com/Marcgb2003/ExamenDePruebaBasesDeDatos/assets/122601138/83acbc28-706c-492a-b6d0-9696793b426b)

4)
Select l.autor 
from libros l inner join prestamos p on l.id_libro=p.id_libro
group by l.autor
having count(p.id_prestamo)/Count(l.id_libro)<3
![4](https://github.com/Marcgb2003/ExamenDePruebaBasesDeDatos/assets/122601138/ce21f1da-01b4-4833-bee2-f45c547880ae)

5)
Select * from prestamos
where fecha_devolucion is null
![5](https://github.com/Marcgb2003/ExamenDePruebaBasesDeDatos/assets/122601138/c2b205c3-d514-42b5-91f2-4966ac8f92e8)

6)
Select l.titulo
from libros l inner join prestamos p on l.id_libro=p.id_libro
where fecha_prestamo< Now() -Interval 1 month
![6](https://github.com/Marcgb2003/ExamenDePruebaBasesDeDatos/assets/122601138/e7287c4e-cfc2-4342-9d10-6b6772b766a6)

7)
Select autor
from libros
group by autor
order by count(titulo) desc
Limit 1
![7](https://github.com/Marcgb2003/ExamenDePruebaBasesDeDatos/assets/122601138/23ce8ce3-09c4-47c3-af7a-0bf7c1060ad9)

8)
Select l.titulo
from libros l inner join prestamos p on l.id_libro=p.id_libro
group by l.titulo
order by count(id_prestamo) desc 
Limit 1
![8](https://github.com/Marcgb2003/ExamenDePruebaBasesDeDatos/assets/122601138/a0eab06b-ff10-4ddd-b9bd-8e566c96a6a6)

9)
Select titulo 
from libros where id_libro not in (
Select id_libro
from prestamos)
![9](https://github.com/Marcgb2003/ExamenDePruebaBasesDeDatos/assets/122601138/3dae4871-2147-4c07-a1a7-719328b24d76)

10)Select Year(p.fecha_prestamo)
from libros l inner join prestamos p on l.id_libro=p.id_libro
group by year(p.fecha_prestamo)
order by Count(p.id_prestamo) desc
Limit 1;
![10](https://github.com/Marcgb2003/ExamenDePruebaBasesDeDatos/assets/122601138/9e6844e3-770c-4371-8cf2-6fb5bd81c887)
