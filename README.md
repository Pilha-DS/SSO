# SSO Self-Study Organizer

    Organize, aprenda e compartilhe conhecimento de forma inteligente

[English](README.md) | [Português](README.pt.md) | [Español](README.es.md)

![angular](https://skillicons.dev/icons?i=angular) ![kafka](https://skillicons.dev/icons?i=kafka) ![spring](https://skillicons.dev/icons?i=spring) ![flutter](https://skillicons.dev/icons?i=flutter) ![java](https://skillicons.dev/icons?i=java)

---

## 1. Ideia Básica do Projeto

O Self-Study Organizer é uma plataforma completa para auxiliar estudantes autodidatas a organizarem seus estudos, aplicarem técnicas de aprendizado comprovadas e compartilharem conhecimento com outros na mesma jornada.

---

## 2. Ideia Explicada do Projeto

Estudar sozinho é desafiador. Muitas vezes perdemos o foco, não sabemos o que estudar em seguida ou simplesmente esquecemos o que aprendemos. Este projeto nasceu para resolver esses problemas.

O Self-Study Organizer é um ecossistema de estudo que oferece:

- 📝 Gerenciamento completo de conhecimento: Crie notas gerais, organize por cursos, indexe vídeos do YouTube, salve aulas baixadas e gerencie livros com links para PDFs e outros formatos.

- 🧠 Estudo Espaçado (Spaced Repetition): Assim como o Anki, o sistema ajuda você a revisar conteúdos nos momentos certos para fixar o aprendizado na memória de longo prazo.

- ⏱️ Técnicas de Estudo: Ative ou desative ferramentas como Pomodoro, Feynman Technique e outras conforme sua necessidade.

- 🤝 Compartilhamento de Conhecimento: Crie seu próprio curso dentro da plataforma, dividido em etapas e módulos, e compartilhe com outras pessoas que estão na mesma fase de aprendizado que você.

- 🌐 Multi-plataforma: Acesse via web ou aplicativo nativo disponível para download gratuito.

---

## 3. Ideia Técnica do Projeto

A arquitetura foi projetada para ser escalável, modular e educativa — um playground real para aplicar conceitos modernos de engenharia de software.

```
┌─────────────────────────────────────────────────────────────┐
│                     Frontend (Web & App)                    │
│  ┌──────────────┐  ┌──────────────┐  ┌──────────────────┐   │
│  │  Angular Web │  │ Flutter (App)│  │  PWA (futuro)    │   │
│  └──────────────┘  └──────────────┘  └──────────────────┘   │
└─────────────────────────────────────────────────────────────┘
                              │
                              ▼
┌─────────────────────────────────────────────────────────────┐
│                     API Gateway (Spring Cloud)              │
└─────────────────────────────────────────────────────────────┘
                              │
                              ▼
┌─────────────────────────────────────────────────────────────┐
│                   Microserviços (Spring Boot)               │
│  ┌─────────┐  ┌─────────┐  ┌──────────┐  ┌─────────────┐    │
│  │  Auth   │  │  Notes  │  │  Courses │  │ Repetition  │    │
│  └─────────┘  └─────────┘  └──────────┘  └─────────────┘    │
│  ┌─────────┐  ┌─────────┐  ┌──────────┐  ┌─────────────┐    │
│  │   Media │  │   Share │  │ Payments │  │   Pomodoro  │    │
│  └─────────┘  └─────────┘  └──────────┘  └─────────────┘    │
└─────────────────────────────────────────────────────────────┘
                              │
              ┌───────────────┴───────────────┐
              ▼                               ▼
┌──────────────────────┐  ┌──────────────────────────────────┐
│   MySQL (Principal)  │  │   Kafka (Event-driven)           │
│   - Dados de estudo  │  │   - Notificações                 │
│   - Usuários         │  │   - Sincronização                │
│   - Cursos/Notas     │  │   - Processamento assíncrono     │
└──────────────────────┘  └──────────────────────────────────┘
```

### Modelo de Negócio

- 🆓 Modelo Gratuito: Todo o código é aberto e você pode hospedar em seus próprios servidores.

- ☁️ Modelo SaaS Pago: Oferecerei uma versão hospedada em meus servidores para quem não quiser gerenciar a infraestrutura.

- 🔄 Revenda: O sistema terá suporte a gateways de pagamento, permitindo que você hospede e venda o serviço para outros.

---

## 4. Estrutura Básica

```
self-study-organizer/
├── backend/
│   ├── api-gateway/          # Spring Cloud Gateway
│   ├── auth-service/         # Autenticação e autorização
│   ├── notes-service/        # Gerenciamento de notas
│   ├── courses-service/      # Cursos, módulos e etapas
│   ├── repetition-service/   # Algoritmos de spaced repetition
│   ├── media-service/        # Upload e indexação de mídia
│   ├── share-service/        # Compartilhamento de conhecimento
│   ├── payments-service/     # Gateway de pagamentos
│   └── pomodoro-service/     # Técnica Pomodoro
├── frontend/
│   ├── web/                  # Angular
│   └── mobile/               # Flutter
└── docker/
    ├── docker-compose.yml    # Orquestração dos serviços
    └── .env.example
```

---

## 5. Estrutura Avançada
### Backend (Java 21 + Spring Boot)

```
backend/
├── config/                   # Configurações centralizadas
├── common/                   # Bibliotecas compartilhadas
│   ├── dto/                  # Data Transfer Objects
│   ├── exception/            # Tratamento global de exceções
│   └── security/             # Configurações de segurança JWT
├── infrastructure/
│   ├── persistence/          # Repositories JPA
│   ├── messaging/            # Configuração do Kafka
│   └── cache/                # Redis (futuro)
└── services/
    ├── [cada serviço]/       # Microserviço individual
    │   ├── controller/       # REST endpoints
    │   ├── service/          # Regras de negócio
    │   ├── model/            # Entidades JPA
    │   └── event/            # Eventos Kafka
    └── shared/
        └── kafka/
            ├── consumer/     # Consumidores de eventos
            └── producer/     # Produtores de eventos
```

### Frontend
#### Web (Angular)
```
frontend/web/
├── src/
│   ├── app/
│   │   ├── core/             # Serviços e interceptors
│   │   ├── shared/           # Componentes reutilizáveis
│   │   ├── features/         # Módulos por funcionalidade
│   │   │   ├── dashboard/
│   │   │   ├── courses/
│   │   │   ├── notes/
│   │   │   ├── repetition/
│   │   │   └── settings/
│   │   └── store/            # NgRx (state management)
│   └── assets/
│       ├── i18n/             # Internacionalização
│       └── styles/
```
#### Mobile (Flutter)

```
frontend/mobile/
├── lib/
│   ├── core/                 # Serviços, DI, config
│   ├── features/             # Módulos de features
│   ├── models/               # Data models
│   ├── providers/            # State management (Riverpod/Bloc)
│   └── widgets/              # Componentes UI
└── assets/
```

---

## 6. Tecnologias e Créditos

---
|Tecnologia|Versão|Créditos|
---
|Flutter|3.24.x|Google|
---
|Dart|3.5.x|Google|
---
|Riverpod|2.5.x|Riverpod|
---
|Dio|5.4.x|Flutter Community|
---
|Hive|2.2.x|Hive|
-
