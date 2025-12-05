# 🤖 IcaBot Scaffolding: Laravel Governance Kit

[![GitHub license](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE.md)
[![Composer package](https://img.shields.io/packagist/v/icassatti/laravel-governance-scaffolding.svg?style=flat-square)](https://packagist.org/packages/icassatti/laravel-governance-scaffolding)

**Descrição:** Kit de Scaffolding Arquitetural projetado para modernizar e refatorar aplicações Laravel legadas. Implementa o padrão de governança **Controller → Service → Repository (C-S-R)**, **Bounded Contexts**, e adota a metodologia **AI-First Documentation** para guiar ferramentas de desenvolvimento inteligentes (como Copilot/Gemini).

## 🎯 Missão Principal

Facilitar a transição de projetos com *Controllers Gigantes* para uma arquitetura modular limpa e sustentável, garantindo que as regras de negócio residam nas **Service Classes**, e o acesso a dados nas **Repositories**.

---

## 🏗️ 1. Pré-requisitos

Este pacote faz parte do ecossistema de desenvolvimento "Icassatti Docker-First" e pressupõe a seguinte fundação:

* **Ambiente:** Docker-First (Comandos executados via `docker exec -it [container]`).
* **Framework:** Laravel 12+ (PHP 8.4+).
* **Governança Base:** É altamente recomendado ter o pacote `icassatti/laravel-boost` instalado, pois ele já prepara o ambiente para o desenvolvimento Pest PHP e MCP Server.

---

## 2. 🚀 Instalação e Customização (Docker-First)

A instalação deve ser feita no seu container de aplicação PHP (ex: `fveph4-app` ou `app`).

### Passo 2.1: Instalação do Pacote

Para projetos em desenvolvimento local (utilizando *path repository*):

```bash
# 1. Adicione a referência do path no composer.json do projeto de destino
# (Se estiver testando via "path repository")

# 2. Instale o kit dentro do seu container PHP
docker exec -it [nome_do_container_app] composer require icassatti/laravel-governance-scaffolding
```

### Passo 2.2: Execução da Entrevista de Governança

O comando `icabot:install` iniciará uma entrevista (prompt) para customizar o kit às necessidades do seu projeto, atualizando automaticamente os documentos de convenções.

```bash
# O comando que dispara a customização
docker exec -it [nome_do_container_app] php artisan icabot:install
```

As perguntas farão a customização nos seguintes pontos:
| Pergunta | Objetivo |
| :--- | :--- |
| **Nome do Projeto?** | Atualiza os documentos base. |
| **Frontend Stack?** | Ajusta referências na documentação (ex: Blade Puro, Vue/Inertia). |
| **Permitir `app/Actions`?** | Define a regra de **Anti-Pattern** no `docs/arch-kit/core/conventions.md`. |

---

## 3. 🗺️ Estrutura de Arquitetura e IA-First

Após a instalação, a arquitetura base do kit estará disponível e customizada:

### A. Estrutura de Pastas

As pastas essenciais para o padrão C-S-R e Modular serão criadas (se não existirem):
* `app/Services`
* `app/Repositories`
* **Scaffolding Base:** Stubs de `Service`, `Repository` e `RepositoryInterface` são publicados para guiar a criação de novos módulos.

### B. Documentação de Governança (AI-First)

Todos os documentos de arquitetura e convenções serão publicados na subpasta **`docs/arch-kit`** para evitar conflitos com a documentação existente.

* `docs/arch-kit/architecture/`: Regras de camadas.
* `docs/arch-kit/core/conventions.md`: Regras de nomenclatura e a regra customizada de *Actions*.

Além disso, um arquivo de contexto para ferramentas de IA será criado:

```bash
.github/copilot-instructions.icabot.md
```

Este arquivo deve ser referenciado pelas suas ferramentas de IA para garantir que todas as sugestões e refatorações de código sigam o novo padrão C-S-R do projeto.

---

## 📝 Contribuições e Licença

Contribuições, sugestões e issues são bem-vindas. Siga o padrão de código e as convenções de testes (Pest PHP, BDD/TDD) que este kit busca impor.

O IcaBot Scaffolding é licenciado sob a **MIT License**.
