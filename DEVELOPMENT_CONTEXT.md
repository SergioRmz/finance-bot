# Contexto de Desarrollo del Proyecto Finance-Bot

## Buenas Prácticas Implementadas

### Manejo de Secretos
1. **.env.example**: Plantilla pública con variables requeridas (se sube a Git)
2. **.gitignore**: Ignora .env para evitar subir secretos a Git
3. **.env**: Archivo local con secretos reales, transferido de forma segura

### Commits Profesionales
- Estándar: Conventional Commits
- Formato: `tipo(ámbito): descripción`
- Tipos comunes:
  - `feat`: Nueva funcionalidad
  - `fix`: Corrección de errores
  - `chore`: Tareas de mantenimiento
  - `docs`: Cambios en documentación
  - `refactor`: Refactorización de código
  - `test`: Adición o modificación de tests

### Convenciones de Nomenclatura
- **Routers Traefik**: Nombres únicos (n8n-monitoring, n8n-finance)
- **Contenedores**: Nombres descriptivos y únicos
- **Dominios**: Subdominios específicos por servicio

## Proceso de Desarrollo

### 1. Diagnóstico de Problemas
1. Identificar el error específico
2. Analizar logs y mensajes de error
3. Formular hipótesis basadas en evidencia
4. Probar soluciones de forma aislada
5. Validar resultados y documentar aprendizajes

### 2. Pruebas de Aislamiento
- Crear configuraciones mínimas para identificar problemas específicos
- Probar componentes individualmente antes de integrar
- Comparar comportamientos entre servicios similares

### 3. Integración Incremental
1. Verificar conectividad básica entre servicios
2. Probar flujos simples de extremo a extremo
3. Agregar complejidad progresivamente
4. Documentar cada paso exitoso

## Herramientas de Desarrollo

### Comandos Útiles de Docker
```bash
# Ver logs de un contenedor
docker logs nombre_contenedor

# Reiniciar servicios
docker-compose down && docker-compose up -d

# Ver estado de contenedores
docker-compose ps

# Ejecutar comandos en un contenedor
docker exec -it nombre_contenedor comando
```

### Comandos de Git
```bash
# Commits con Conventional Commits
git commit -m "feat: añadir funcionalidad X"
git commit -m "fix: resolver problema Y"

# Ver historial de commits
git log --oneline
```