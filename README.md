# ExamenDePruebaBasesDeDatos
1)
Select l.titulo 
from libros l inner join prestamos p on l.id_libro=p.id_libro
group by l.titulo
having l.titulo in (
Select l.titulo from libros l inner join prestamos p on l.id_libro=p.id_libro
where p.fecha_prestamo in (
select Min(fecha_prestamo) from prestamos))

2)
Select l.titulo 
from libros l inner join prestamos p on l.id_libro=p.id_libro
group by l.titulo
having l.titulo not in (
Select l.titulo from libros l inner join prestamos p on l.id_libro=p.id_libro
where p.fecha_prestamo<NOW() - INTERVAL 6 MONTH)

3)
Select Month(p.fecha_prestamo)
from libros l inner join prestamos p on l.id_libro=p.id_libro
group by month(p.fecha_prestamo)
order by Count(p.id_prestamo) desc
Limit 1;

4)
Select l.autor 
from libros l inner join prestamos p on l.id_libro=p.id_libro
group by l.autor
having count(p.id_prestamo)/Count(l.id_libro)<3

5)
Select * from prestamos
where fecha_devolucion is null

6)
Select l.titulo
from libros l inner join prestamos p on l.id_libro=p.id_libro
where fecha_prestamo< Now() -Interval 1 month

7)
Select autor
from libros
group by autor
order by count(titulo) desc
Limit 1

8)
Select l.titulo
from libros l inner join prestamos p on l.id_libro=p.id_libro
group by l.titulo
order by count(id_prestamo) desc 
Limit 1

9)
Select titulo 
from libros where id_libro not in (
Select id_libro
from prestamos)

10)Select Year(p.fecha_prestamo)
from libros l inner join prestamos p on l.id_libro=p.id_libro
group by year(p.fecha_prestamo)
order by Count(p.id_prestamo) desc
Limit 1;
