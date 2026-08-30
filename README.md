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

    📝 Gerenciamento completo de conhecimento: Crie notas gerais, organize por cursos, indexe vídeos do YouTube, salve aulas baixadas e gerencie livros com links para PDFs e outros formatos.

    🧠 Estudo Espaçado (Spaced Repetition): Assim como o Anki, o sistema ajuda você a revisar conteúdos nos momentos certos para fixar o aprendizado na memória de longo prazo.

    ⏱️ Técnicas de Estudo: Ative ou desative ferramentas como Pomodoro, Feynman Technique e outras conforme sua necessidade.

    🤝 Compartilhamento de Conhecimento: Crie seu próprio curso dentro da plataforma, dividido em etapas e módulos, e compartilhe com outras pessoas que estão na mesma fase de aprendizado que você.

    🌐 Multi-plataforma: Acesse via web ou aplicativo nativo disponível para download gratuito.

---

## 3. Ideia Técnica do Projeto

A arquitetura foi projetada para ser escalável, modular e educativa — um playground real para aplicar conceitos modernos de engenharia de software.

```
┌─────────────────────────────────────────────────────────────┐
│                     Frontend (Web & App)                    │
│  ┌──────────────┐  ┌──────────────┐  ┌──────────────────┐   │
│  │  Angular Web │  │ Flutter (App)│  │  PWA (futuro)    │    │
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
