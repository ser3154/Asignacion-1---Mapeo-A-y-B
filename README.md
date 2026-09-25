## Instalación

1. Clonar el repositorio
   git clone <url-de-tu-repo>
   cd reservaciones_de_restaurante

2. Instalar dependencias
   npm install

3. Configurar variables de entorno
   Crear un archivo .env en la raíz con el siguiente contenido:
   DATABASE_URL="mysql://usuario:contraseña@localhost:3306/restaurante"

   (Reemplazar usuario y contraseña con los propios.
   No hace falta crear la base de datos a mano, la migración la crea.)

4. Ejecutar las migraciones
   npx prisma migrate dev

5. (Opcional) Verificar los datos con Prisma Studio
   npx prisma studio

   ¿Por qué esa combinación única evita reservar la misma mesa dos veces en el mismo turno?
   @@unique([mesaId, turnoId]) crea un indice compuesto que impide que existan dos reservaciones con la
   misma combinacion de mesa y turno, aunque si se quiere evitar que la misma se reserve en el mismo turno
   pero en fechas diferentes, tambien seria necesario incluir fecha en la restriccion, por ejemplo @@unique([mesaId, turnoId, fecha])
