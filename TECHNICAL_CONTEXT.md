# Contexto Técnico del Proyecto Finance-Bot

## Infraestructura y Tecnologías

### Contenedores y Servicios
1. **n8n-finance**
   - Imagen: n8nio/n8n
   - Función: Orquestador de flujos de trabajo
   - Puerto interno: 5678
   - Variables de entorno importantes:
     - GROQ_API_KEY: Para integración con IA
     - TELEGRAM_BOT_TOKEN: Para comunicación con Telegram
     - N8N_HOST: Dominio configurado
     - N8N_PROTOCOL: HTTPS

2. **personal-finance-db**
   - Imagen: postgres:15-alpine
   - Función: Almacenamiento persistente de datos
   - Variables de entorno:
     - POSTGRES_USER: Usuario de la base de datos
     - POSTGRES_PASSWORD: Contraseña del usuario
     - POSTGRES_DB: Nombre de la base de datos

### Redes y Conectividad
- **Red compartida**: vps-monitoring_default (externa)
- **Proxy inverso**: Traefik para enrutamiento y certificados SSL
- **Dominios**: Uso de subdominios únicos (n8n-finance.dominio.com)

### Configuración de Traefik
Etiquetas importantes en docker-compose.yml:
```yaml
labels:
  - "traefik.enable=true"
  - "traefik.docker.network=vps-monitoring_default"
  - "traefik.http.routers.n8n-finance.rule=Host(`${N8N_DOMAIN}`)"
  - "traefik.http.routers.n8n-finance.entrypoints=websecure"
  - "traefik.http.routers.n8n-finance.tls.certresolver=myresolver"
  - "traefik.http.services.n8n-finance.loadbalancer.server.port=5678"
```

## Estructura del Proyecto
```
finance-bot/
├── docker-compose.yml     # Definición de servicios
├── .env.example          # Plantilla de variables de entorno
├── .env                  # (local) Variables de entorno con secretos
├── .gitignore            # Archivos ignorados por Git
├── README.md             # Documentación del proyecto
└── n8n-data/             # Datos persistentes de n8n
```

## Modelo de Datos
Tabla `expenses` en PostgreSQL:
- id (serial, primary key)
- timestamp (timestamp with time zone)
- amount (numeric)
- concept (text)
- category (text)

## Integración con IA
- Servicio: Groq API
- Técnica: Few-Shot Prompting
- Función: Extracción de entidades (monto, concepto) y clasificación de gastos