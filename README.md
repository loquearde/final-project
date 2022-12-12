# [](https://github.com/zantonz/final-project/blob/master/README.md)ToDo App

[Click para acceder a la web](https://todo-zantonz.vercel.app/)

Autor: Anton Zyrianov
Fecha: 25/08/2022

## Descripcion

![Pagina Home](https://i.postimg.cc/m2rV83dV/Captura-de-pantalla-2022-08-25-a-las-10-38-46.png)

Se trata del proyecto final realizado durante el bootcamp de Front End Development en el Ironhack que consiste en una pagina web que te permite gestionar tus tareas.

Es una aplicacion creada con Vue.js que permite a usuarios crear una cuenta, añadir tareas a completar, editarlas, marcarlas como completadas y finalmente borrarlas. Nuestra pagina web esta vinculada a una base de datos, donde estaremos almacenando todos los datos de usuarios y las tareas. En este caso, para gestionarlo utilizaremos Supabase, que nos ofrece un subconjunto de funcionalidades de Back End que nos permite gestionarlo como un servicio.

**El objetivo** de este proyecto es poner en practica los conocimientos de Vue.js obtenidos durante el curos y ademas poder conectarlo a una base de datos externa y gestionarla.

## Tecnologias empleadas:

- **Client:** Vue.js y Vite
- **Router:** Vue Router
- **Store:** Pinia y Pinia Persist para el Log In
- **Database:** Supabase

# Trello del proyecto

https://trello.com/b/lmqyGbvH/final-project-ironhack

# Journal

## Martes 6 de diciembre

Todavía estoy en la fase de preparación del proyecto, tengo que organizar cómo voy a trabajar y empezar a decidir un orden lógico para ir ejecutando el trabajo. Empezaré por trabajar el HTML y el CSS del Sign Up y Sign In. Una vez he preparado todo el HTML y el CSS del Sign Up y Sign In, he comenzado a trabajar en la lógica. Por la tarde, he podido empezar a trabajar en la lógica de las tasks junto con otros compañeros.

## Miércoles 7 de diciembre

Ayer avanzamos significativamente desarrollando la lógica de NewTask y TaskItem, así como creando en task.js las nuevas funciones. Hoy me he propuesto sacar adelante la lógica que me falta en el resto del proyecto (todavía pendiente la asíncrona de Sign In) y empezar a darle forma al CSS de las principales páginas. Hoy ya hemos terminado la lógica para poder marcar tasks como completadas y que se comunique correctamente a la base de datos. Dedicaré el resto del día a estilar las diferentes páginas.

## Jueves 8 de diciembre

Ayer pude terminar el CSS de las páginas de Sign In y Sign Up (las hice juntas ya que compartían casi todos sus elementos). Hoy voy a comenzar el día trabajando en la barra de navegación y estimo que me llevará al menos toda la mañana. Acabo el día con el estilado de New Task y New Item completo.

## Viernes 9 de diciembre

Hoy voy a comenzar creando un footer y estilándolo para móvil. Una vez acabado esto, quiero empezar a trabajar en las media queries para que la web se visualice correctamente en desktop. He podido acabar con la responsiveness. Dejo para la semana que viene el menú de hamburguesa.

## Lunes 12 de diciembre

Hoy me centraré en el menú hamburguesa, ya que necesito rediseñarlo para que funcione usando un v-show.
