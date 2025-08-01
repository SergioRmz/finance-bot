# Contexto del Proyecto Finance-Bot

## Visión General
Finance-bot es un asistente financiero personal que permite a los usuarios registrar y clasificar sus gastos mediante mensajes de Telegram. El sistema utiliza inteligencia artificial para procesar el lenguaje natural y almacenar la información en una base de datos para análisis posterior.

## Objetivos del Proyecto
1. Aprender principios de arquitectura de software y DevOps
2. Construir un producto funcional que demuestre habilidades técnicas
3. Mejorar las perspectivas laborales mediante el desarrollo de un portafolio sólido

## Arquitectura General
- **Infraestructura base**: VPS con Linux
- **Contenerización**: Docker y Docker Compose
- **Proxy inverso**: Traefik para enrutamiento y SSL
- **Red compartida**: Conexión con vps-monitoring_default
- **Componentes principales**:
  - n8n-finance: Orquestación de la lógica del bot
  - personal-finance-db: Base de datos PostgreSQL para almacenamiento
  - IA (Groq): Procesamiento de lenguaje natural

## Metodología de Trabajo
- Colaboración basada en mentoría de arquitectura de software
- Enfoque iterativo e incremental
- Diagnóstico de problemas como oportunidades de aprendizaje
- Uso de herramientas del mundo real para análisis de causa raíz

## Estado Actual
En desarrollo activo, enfrentando desafíos de configuración de red con Traefik.