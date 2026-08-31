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
│                         API Gateway                         │
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
backend/
├── config/                          # Configurações centralizadas
│   ├── application.yml
│   ├── kafka-config/
│   └── security-config/
│
├── common/                          # Código compartilhado entre serviços
│   ├── dto/                         # DTOs globais
│   ├── exception/                   # Exceções e handlers
│   ├── security/                    # JWT, autenticação
│   └── utils/                       # Utilitários comuns
│
├── infrastructure/                  # Infraestrutura técnica
│   ├── persistence/
│   │   ├── repositories/           # Interfaces Repository
│   │   └── mappings/              # Mapeamentos Entity <-> DTO
│   ├── messaging/
│   │   ├── producer/              # Produtores Kafka
│   │   └── consumer/              # Consumidores Kafka
│   └── cache/                      # Redis (futuro)
│
└── services/                       # Microserviços
    ├── user-service/               # Serviço de Usuários
    │   ├── api/                    # Camada de API
    │   │   ├── controller/         # REST endpoints
    │   │   └── dto/               # DTOs específicos do serviço
    │   ├── application/            # Camada de Aplicação
    │   │   ├── service/           # Regras de negócio
    │   │   └── mapper/            # Mapeadores específicos
    │   ├── domain/                 # Camada de Domínio (DDD)
    │   │   ├── model/             # Entidades de domínio
    │   │   ├── repository/        # Interfaces de repositório
    │   │   └── value-objects/     # Value Objects
    │   ├── infrastructure/         # Infraestrutura do serviço
    │   │   ├── persistence/
    │   │   │   ├── entities/      # Entidades JPA
    │   │   │   └── repositories/  # Implementações Repository
    │   │   └── events/
    │   │       ├── publishers/    # Publicadores de eventos
    │   │       └── listeners/     # Listeners de eventos
    │   └── UserServiceApplication.java
    │
    ├── order-service/              # Serviço de Pedidos
    │   └── [mesma estrutura]
    │
    └── shared/                     # Compartilhado entre serviços
        └── events/
            ├── user-events/       # Eventos relacionados a usuário
            └── order-events/      # Eventos relacionados a pedidos
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

## 6.  Meus Créditos

    "Pilha-DS" — Desenvolvedor e Estudante de Ciência da Computação

### Sobre mim

Sou um entusiasta de software e estudante de Ciência da Computação. Crio projetos para aprender, aplicar conceitos da universidade e, principalmente, ajudar outras pessoas que estão na mesma jornada de autodidatismo que eu.

#### Este projeto

Este projeto nasceu em agosto de 2026, a partir de um problema que enfrentei enquanto tentava estudar em casa. Ao buscar uma solução para essa dificuldade, percebi que ela também poderia ajudar outras pessoas que passam por situações semelhantes. Por isso, decidi disponibilizar o projeto para que mais pessoas possam utilizá-lo e se beneficiar dele.

- Microserviços e arquitetura distribuída

- Sistemas orientados a eventos com Kafka

- Design patterns e princípios SOLID

- Desenvolvimento full-stack

- DevOps e containerização

### Como contribuir

Este é um projeto de estudo, portanto não pretendo oferecer suporte ativo de longo prazo. No entanto, se você se sentir inspirado e quiser contribuir com código, ideias ou melhorias, sinta-se à vontade para abrir uma issue ou pull request. Toda ajuda é bem-vinda, e quem sabe este projeto não se torna uma comunidade?

### Lisenca

```
Este projeto é licenciado sob a GPL (GNU General Public License).

Você pode:
✅ Usar, modificar e distribuir o código
✅ Oferecer como SaaS sem compartilhar modificações
✅ Vender como serviço hospedado

Você deve:
⚠️ Compartilhar o código-fonte original e modificado se distribuir o software
⚠️ Manter os avisos de direitos autorais
⚠️ Licenciar quaisquer versões modificadas sob a mesma licença GPL
```

Contato

    🌐 GitHub: github.com/Pilha-DS

    📫 Email: [jonathan.cardoso2212@gmail.com]
