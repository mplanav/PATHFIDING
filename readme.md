# 🧭 Pathfinding Planner con Frontend y Backend Integrado

Este proyecto implementa un sistema completo de planificación de rutas utilizando algoritmos de pathfinding, con una interfaz web en React y un backend en Python (FLASK). Está diseñado para recibir mapas y coordenadas dinámicamente y calcular el camino más corto, integrando lógica avanzada como priorización de "tracks".

---

## 🚀 Funcionalidades principales

- Cálculo de caminos con D* Lite adaptado
- Heurística dinámica según pertenencia a "tracks"
- Mapas dinámicos cargados desde JSON o mediante POST
- Visualización en tiempo real del grid y path
- Coordinadas mostradas bajo el cursor
- Arquitectura dockerizada para despliegue fácil

---

## 🧱 Estructura del proyecto
├── back/
│ ├── app/
│ │ ├── init.py
│ │ ├── dstar.py
│ │ └── mapa.json
│ ├── Dockerfile
│ └── .dockerignore
│
├── front/
│ ├── src/
│ │ ├── components/
│ │ │ └── Grid.tsx
│ │ ├── App.tsx
│ │ └── ...
│ ├── Dockerfile
│ └── .dockerignore
│
├── docker-compose.yml
└── README.md


---

## ⚙️ Requisitos

- [Docker](https://www.docker.com/)
- [Docker Compose](https://docs.docker.com/compose/)

---

## ▶️ Cómo ejecutar el proyecto

1. Clona este repositorio:

```bash
git clone https://github.com/mplanav/PATHFINDING.git
cd PATHFINDING
docker-compose up --build

Accede desde tu navegador:
Frontend: http://localhost:80
Backend (API): http://localhost:5000

## 📤 Endpoint `/set-checkpoints`

Este endpoint permite definir dinámicamente los puntos de partida (`source`) y destino (`goal`) del planificador. Es útil para simular movimientos o cambios de objetivo en tiempo real.

### Método: `POST`

**URL: http://localhost:5000/set-checkpoints**  

### Body del mensaje

Puedes enviar la petición usando herramientas como **Thunder Client**, **Postman** o mediante `curl`. Asegúrate de que el tipo de contenido sea `application/json`.

**Ejemplo de cuerpo (JSON):**

```json
{
  "source": [2, 3],
  "goal": [15, 9]
}

**Respuesta esperada: **
{
  "path": [[2, 3], [3, 3], [4, 3], ..., [15, 9]]
}

# 🖼️ Frontend interactivo
Renderiza walls, start, goal, visited, path, tracks.
El camino (path) se dibuja por encima de los tracks, manteniendo su color distintivo.
Las coordenadas del mouse se muestran justo donde apunta el cursor.
Reintentos automáticos para conexión con backend.