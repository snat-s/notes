---
author: Santiago Pedroza Díaz
---
# Descripción

En el presente trabajo se analizará una de las áreas de oportunidad que tiene el Centro de Investigacion de Óptica (CIO) encontrado en Aguascalientes.

Actualmente el CIO tiene un programa anual de calibración e inventario de equipos y patrónes en el cual, el equipo interno es calibrado para que pueda ser utilizado en la creación de Certificados de Calibración. 

El equipo interno actualmente se tiene con las siguientes características: tiene una antigüedad, una ubicación, un modelo, un nombre, un ID interno único, un número de serie único, una fecha de calibrado y una fecha de la próxima calibración, además de tener una serie de observaciones y un control que puede ser externo o interno.

Además, todos los equipos tienen una fecha de registro, esta fecha de registro es para monitorear la entrada de nuevos elementos y tiene las siguientes características: un costo, la marca, un ID que es consecutivo y es único, un modelo, el nombre de la persona que lo compró, la fecha de entrada al CIO y parámetros que puede llegar a generar.

Los certificados de Calibración tienen una Carátula, el nombre del Cliente, el contacto, los datos del equipo que está siendo calibrado, el procedimiento que se llevó a cabo,  la persona que lo calibró y la persona que lo aprobó, la fecha de recivo, la fecha de calibración, la fecha de emisión del certificado, el número que avala al CIO con un número identificador único. Además de que se tienen varios parámetros del equipo en cuestión que se está certificando, llevan a cabo cierto número de mediciónes que entran en un rango, también tienen una órden de servicio y finalmente un número de folio único.

El equipo es avalado por los certificados  y estos a su vez tienen un número de serie único, un model, una marca y una serie de propiedades. 

Al ser certificado, los equipos son otorgados con una etiqueta que tiene el nombre del calibrador, un identificador único (ID) y la fecha de calibración.

Los folios internamente tienen un número identificador único, consecutivo un año, un mes, el servicio que se generó, una cotización, un cliente y una factura.

Los datos del cliente que se guardan son la razón social y su domicilio. El domicilio tiene varias dos partes, el código postal y la calle.

Se genera un certificado por equipo pero todos tienen una órden y no existe un método actualmente para conseguir rápidamente todos los resultados de una órden.

Un area en el que se podría mejorar mucho es reducir la cantidad  de información que existe en dos zonas distintas pero no tiene una razón de estar en dos lugares. Se recomienda consolidar la información. 

El hecho de que se tenga un registro en el programa anual de calibración e inventario de equipos y patrones y además se tengan actas de registro separadas es algo que se podría reducir y tener menos entidades pero con algunos atributos más. Cambiar el programa anual de calibración a que sea un programa de calibración. En segunda, se tiene un número de folio que es único para los certificados de calibración, creo que sería mejor idea tener una entidad de cliente con más atributos para poder acceder a las órdenes y no tener que buscar equipo por equipo lo que pidió el cliente.

La solución que se propone para eliminar la entidad que funciona en estos momentos como la fecha de registro es pasar esa información a la del programa de calibración e inventario de equipos y patrones. Esta entidad terminaría tendría los siguientes atributos:  Antigüedad, ubicación, modelo,  ID único interno, un número de serie único, la fecha de calibración y la fecha de la próxima calibración, las observaciónes y el control que puede ser externo e interno,  el costo, la marca, la persona que compró el producto, la fecha de compra y los parámetros que puede llegar a medir el equipo.

En segunda instancia, podriamos tener la entidad de Orden que es generada por un cliente (al cual también se le agregaría un identificador único) y tiene cierto número de Equipos y es individual por Cliente. Este nuevo atributo llamado órden tendría los elementos que normalmente se veían en el folio (número identificador único, un año, un mes, el servicio que se generó, una cotización, un cliente y una factura) pero, tendría varios Certificados de Calibración en vez de que un certificado de calibración tuviera una órden. Ahora una sola órden podría tener muchos certificados de calibración.

En conclusión, se podría eliminar parte de la duplicación de datos si se elimina la necesidad de las actas de registro y solo se utiliza el programa de calibración e inventario de equipos y patrones para tener esa información consolidada y en segunda si se genera una entidad que tenga las órdenes de los clientes ya no es necesario tener un folio único para cada uno de los certificados de calibración.


# Matriz de relación

| |Equipo Interno|Orden| Cliente| Certificado de Calibración | Equipo | Etiqueta| 
|-|--------------|------|--------|----------------------------|--------|----------|
|Equipo Interno ||| |   |  | |
|Orden ||| |   |  | |
|Cliente ||| |   |  | |
|Certificado de Calibración ||| |   |  | |
|Equipo ||| |   |  | |
|Etiqueta ||| |   |  | |

# Modelo E-R

Ya casi lo termino, solo le falta la cardinalidad.

# Modelo relacional o tablas

Cliente(Razón Social, Código Postal, Calle)

Orden(*IDOrden*, Año, Mes, Cotización, Factura, Servicio, Equipo)

Equipo(Marca, *Número de serie*, Modelo, **Propiedades**)

Equipo interno(*ID*, **Observaciones**, Costo, **Parámetros**, Fecha de calibración, Fecha próxima de calibración, Fecha de compra, Persona que lo compró, *Número de serie*, Antigüedad, Marca, Ubicación, Modelo)

Certificado de Calibración(*ID del CIO*, Calibrador, Supervisor del Calibrador, Fecha de resivo, Fecha de calibración, Fecha de emisión de certificado, Carátula, Contacto, **Datos del Equipo**, Procedimiento llevado a cabo, **Parámetros**)

Etiqueta(*IDEtiqueta*, Fecha de calibración, Nombre del Calibrador)