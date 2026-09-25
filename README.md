## Instalación

1. Clonar el repositorio
   git clone <url-de-tu-repo>
   cd taller-mecanico

2. Instalar dependencias
   npm install

3. Configurar variables de entorno
   Crear un archivo .env en la raíz con el siguiente contenido:
   DATABASE_URL="mysql://usuario:contraseña@localhost:3306/nombre_basedatos"

   (Reemplazar usuario, contraseña y nombre_basedatos con los propios.
   No hace falta crear la base de datos a mano, la migración la crea.)

4. Ejecutar las migraciones
   npx prisma migrate dev

5. (Opcional) Verificar los datos con Prisma Studio
   npx prisma studio


   ¿Qué pasaría si intentaras borrar un Cliente que todavía tiene un Vehiculo?
   Si se intenta eliminar un Cliente que todavia tiene un vehiculo asociado, MySQL rechazaria la operacion
   y mostraria un error de restriccion de llave foranea, debido a que la columna clienteId de la tabla Vehiculo
   tiene configurada una relacion con Cliente mediante ON DELETE RESTRICT. Esto significa que la base de datos
   protege la integridad referencial evitando que un Vehiculo quede asociado a un Cliente que ya no existe.
   Por lo tanto, para poder eliminar dicho Cliente, primero seria necesario eliminar los Vehiculos asociados o
   reasignalos a otro Cliente.
