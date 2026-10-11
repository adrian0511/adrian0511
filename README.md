<p align="center">
  <img src="assets/header.svg" alt="Adrián Garcés — Backend Developer" width="100%" />
</p>

<p align="center">
  <img src="assets/typing.svg" alt="Backend Developer · Java 21 &amp; Spring Boot · Microservicios · Kafka · Spring Cloud" />
</p>

<p align="center">
  <a href="https://adrian0511.dev"><img src="assets/badge-portfolio.svg" alt="Portfolio" /></a>
  <a href="https://linkedin.com/in/adrdev"><img src="assets/badge-linkedin.svg" alt="LinkedIn" /></a>
  <a href="https://github.com/adrian0511?tab=repositories"><img src="assets/badge-github.svg" alt="Repositorios" /></a>
  <a href="README.en.md"><img src="assets/badge-lang-en.svg" alt="Read this in English" /></a>
</p>

---

## Sobre mí

Desarrollador **backend** centrado en Java y el ecosistema Spring, con foco en **sistemas
distribuidos**: microservicios, mensajería asíncrona y APIs documentadas por contrato. Trabajo
también el lado cliente (React, TypeScript) porque diseñar bien una API exige entender a quien
la consume, y APIs en Python con FastAPI cuando el problema pide algo más ligero.

El día a día es **Spring Boot 4** y **Spring Cloud** sobre **Kafka**, con arquitectura hexagonal
y tests en todas las capas. Más abajo está el detalle de cómo trabajo cada pieza.

Santa Cruz de Bezana, Cantabria (España) · [adrian0511.dev](https://adrian0511.dev)

---

## Publicado en Maven Central

**[`prompt-link`](https://github.com/adrian0511/prompt-link)** — cliente Java reutilizable para IA
generativa a través de OpenRouter, con auto-configuración de Spring Boot.

<a href="https://central.sonatype.com/artifact/io.github.adrian0511/prompt-link"><img src="https://img.shields.io/maven-central/v/io.github.adrian0511/prompt-link?label=Maven%20Central&labelColor=0D1524&color=00F7FF&style=flat-square" alt="Última versión en Maven Central" /></a>

```xml
<dependency>
    <groupId>io.github.adrian0511</groupId>
    <artifactId>prompt-link</artifactId>
    <version>1.1.0</version>
</dependency>
```

- Auto-configuración: basta con añadir la dependencia, sin `@EnableFeignClients`
- Cliente Feign **aislado** — el interceptor de la API key vive solo en su contexto, así que la
  clave no se filtra a otros clientes Feign de la aplicación
- Errores **tipados** (`AiClientException`): distingue error de API, de red, respuesta inutilizable
  y fallo de configuración
- *Streaming* de tokens con `Flux<String>` sobre WebFlux, y conversaciones multi-turno

---

## Proyectos

| Proyecto | Qué es | Stack |
|---|---|---|
| **[orderflow](https://github.com/adrian0511/orderflow)** | Plataforma de pedidos sobre **9 microservicios**: catálogo, reserva de inventario, pago simulado y notificación por correo, coordinados por eventos. | Java 21 · Spring Boot 4 · Kafka · OAuth2 |
| **[finance-tracker](https://github.com/adrian0511/finance-tracker)** | Gestión de finanzas personales con asistente de IA que categoriza movimientos. Un solo artefacto: el backend sirve el cliente React desde el propio jar, sin CORS ni doble despliegue. | Spring Boot · React · PostgreSQL · JWT |
| **[cookbook](https://github.com/adrian0511/cookbook)** | Gestor de recetas full-stack con **arquitectura hexagonal** (puertos y adaptadores), invariantes de dominio, paginación, búsqueda por ingrediente y valoraciones. **102 tests**. | Java 21 · Spring Boot 4 · React 19 · PostgreSQL |
| **[portfolio](https://github.com/adrian0511/portfolio)** · [en vivo](https://adrian0511.dev) | Portfolio reactivo que consume la API de GitHub en tiempo real, con *timeouts*, *fallback* e i18n español/inglés. | Spring WebFlux · React 18 · Vite |
| **[gym-reservas](https://github.com/adrian0511/gym-reservas)** | Reservas de clases de gimnasio con cupos en tiempo real, lista de espera y control de acceso por roles. | NestJS · React 18 · TypeScript · PostgreSQL |
| **[ride-hailing-microservices](https://github.com/adrian0511/ride-hailing-microservices)** | Microservicios de *ride hailing* con autenticación centralizada: `authorization_code` para usuarios y `client_credentials` entre servicios. | Spring Cloud · OAuth2 · Eureka · OpenFeign |
| **[challengehub](https://github.com/adrian0511/challengehub)** | API REST de retos y recompensas: progreso por usuario, insignias y control de acceso por roles, con mapeo entidad-DTO por MapStruct. | Java 25 · Spring Boot 4 · JWT · PostgreSQL |
| **[bug-hunt](https://github.com/adrian0511/bug-hunt)** | Dos retos que comparten un mismo *token bucket* implementado **una sola vez**: filtro `stdin → stdout` y acortador de URLs con *rate limiting* por IP. | Python 3.12 · FastAPI · SQLite |

> El resto de repositorios, en **[github.com/adrian0511?tab=repositories](https://github.com/adrian0511?tab=repositories)**

---

## Stack

<p align="center">
  <img src="assets/animated-icons.svg" alt="Java, Spring, Python, FastAPI, NestJS, TypeScript, React, Redux, Docker, Git, PostgreSQL, MySQL, Kafka, Prometheus, Grafana, Linux, Nginx, Postman, GitHub" width="100%" />
</p>

<p align="center">
  <img src="assets/tools.svg" alt="Spring Cloud, Spring Security, Spring WebFlux, Eureka, OpenFeign, Resilience4j, Apache Kafka, OAuth2, JWT, OpenAPI y Swagger, Hibernate y JPA, Flyway, JUnit 5, Mockito, Testcontainers, Docker Compose, Nginx, Prometheus, Grafana, Vite, Tailwind CSS, Redux Toolkit, Sequelize, Vitest" width="100%" />
</p>

---

## Arquitectura y enfoque

| Área | Cómo lo trabajo |
|---|---|
| **Diseño de APIs** | Contrato primero con OpenAPI, documentación viva en Swagger UI, validación con Postman |
| **Microservicios** | Spring Cloud Gateway como entrada única, Eureka para descubrimiento, OpenFeign entre servicios |
| **Resiliencia** | Circuit breaker y *fallbacks* con Resilience4j, *timeouts* explícitos, degradación controlada |
| **Event-driven** | Kafka para desacoplar servicios; saga para consistencia eventual en pedidos y pagos |
| **Seguridad** | Spring Security + OAuth2 Authorization Server, JWT con *scopes* y roles |
| **Arquitectura** | Hexagonal y DDD: el dominio no conoce a Spring ni a la base de datos |
| **Testing** | JUnit 5, Mockito, AssertJ y *slices* de Spring en backend; Vitest y Testing Library en frontend |
| **Persistencia** | PostgreSQL y MySQL con JPA/Hibernate; Sequelize en NestJS; SQLAlchemy en Python |
| **Infraestructura** | Docker Compose, Nginx como *reverse proxy*, métricas con Prometheus y paneles en Grafana |

---

## Contribuciones

<p align="center">
  <picture>
    <source media="(prefers-color-scheme: dark)" srcset="https://raw.githubusercontent.com/adrian0511/adrian0511/output/github-contribution-grid-snake-dark.svg" />
    <img src="https://raw.githubusercontent.com/adrian0511/adrian0511/output/github-contribution-grid-snake.svg" alt="Serpiente recorriendo el grid de contribuciones" width="100%" />
  </picture>
</p>

---

## En qué estoy ahora

- Manteniendo **prompt-link** en Maven Central: *streaming*, errores tipados y compatibilidad con Spring Boot 4.
- Llevando el patrón **saga** de `orderflow` a un flujo con compensaciones completas sobre Kafka.
- Consolidando la **arquitectura hexagonal** de `cookbook` como plantilla base para nuevos servicios.
- Observabilidad de extremo a extremo: métricas de Spring Actuator en Prometheus y paneles en Grafana.

---

## Hablemos

Estoy abierto a oportunidades como **desarrollador backend** (Java / Spring) y a colaborar en
proyectos de sistemas distribuidos. Si has llegado hasta aquí desde una oferta o un proyecto,
la vía más rápida es LinkedIn:

<p align="center">
  <a href="https://linkedin.com/in/adrdev"><img src="assets/badge-linkedin.svg" alt="LinkedIn" /></a>
  <a href="https://adrian0511.dev"><img src="assets/badge-portfolio.svg" alt="Portfolio" /></a>
</p>

<p align="center">
  <i>Siempre aprendiendo · Siempre construyendo · Siempre enviando</i>
</p>
