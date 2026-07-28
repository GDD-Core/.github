# GDD-Core

Test bed do Agentix: esteiras simuladas BIAtech, apps demo e o Nexus real na
VPS. Templates de esteira também aparecem em Actions → New workflow.

## Começando um projeto novo — welcome kits

Cada kit é um repositório-template que já vem com a esteira ligada, os arquivos
de qualidade da org e um serviço mínimo que compila, testa e passa nos gates.
Clone, rode `.\tools\init.ps1 -Nome <sua-app>` e siga o `WELCOME.md`.

| Kit | Para quê | Deploy |
|---|---|---|
| [`starter-srv-java`](https://github.com/GDD-Core/starter-srv-java) | Serviço Java (Spring Boot 3.5 / Java 21, reator de 2 módulos) | GitOps + ArgoCD |
| [`starter-bff-node`](https://github.com/GDD-Core/starter-bff-node) | BFF Node (NestJS 11 / Node 22) | GitOps + ArgoCD |
| [`starter-python-sim`](https://github.com/GDD-Core/starter-python-sim) | Simulador/utilitário Python | GitOps + ArgoCD |
| [`starter-fed-react`](https://github.com/GDD-Core/starter-fed-react) | Front-end React 18 + Vite | Storage Account (`$web`) |
| [`starter-fed-vue`](https://github.com/GDD-Core/starter-fed-vue) | Front-end Vue 3 + Vite | Storage Account (`$web`) |
| [`starter-fed-angular`](https://github.com/GDD-Core/starter-fed-angular) | Front-end Angular 22 | Storage Account (`$web`) |
| [`starter-api-axway`](https://github.com/GDD-Core/starter-api-axway) | API declarada por OpenAPI | Axway API Manager |
| [`starter-mon-ant`](https://github.com/GDD-Core/starter-mon-ant) | Monolito Ant (WAR/EAR) | WebSphere |
| [`starter-bat-iws`](https://github.com/GDD-Core/starter-bat-iws) | Job batch (PIP) | IWS |
| [`starter-config`](https://github.com/GDD-Core/starter-config) | Repositório `<app>-config` avulso | — |

Os três primeiros criam **dois** repositórios: o de código e o `<app>-config`,
onde o job `gitops` commita o manifesto renderizado. É esse commit que
efetivamente faz o deploy.

Actions está desligado **nos kits** de propósito: eles não devem rodar a própria
esteira e publicar artefato com o nome placeholder. Os repositórios criados a
partir deles nascem normais.

## Esteiras

Os reusable workflows e as composite actions vivem em
[`esteiras-workflows`](https://github.com/GDD-Core/esteiras-workflows); os
callers copiáveis, em
[`esteiras-callers`](https://github.com/GDD-Core/esteiras-callers). O repo
`esteiras` foi dividido nesses dois e arquivado.

Para ensaiar falhas, use a variável `SIM_FALHA` — 91 valores, cada um com a
mensagem verbatim do erro real da base de conhecimento.
