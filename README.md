# Escalas Neuromusculares · Dr. Igor Campana

## O que é
As **Escalas Neuromusculares** é uma aplicação web progressiva (PWA) desenvolvida para auxiliar médicos neurologistas no cálculo rápido e preciso de escores clínicos durante a avaliação de pacientes com doenças neuromusculares.

## Para que serve
A ferramenta resolve o problema da fragmentação e dificuldade de cálculo manual de escalas complexas (como MGC ou ALSFRS-R). Ela centraliza as principais métricas clínicas em uma interface otimizada para dispositivos móveis, permitindo gerar um texto formatado para cópia imediata no prontuário eletrônico.

## Quem usa e como
- **Usuário:** Médicos neurologistas e residentes.
- **Fluxo:**
  1. O médico seleciona a escala desejada na barra lateral.
  2. Preenche os campos conforme a avaliação clínica ou relato do paciente.
  3. O sistema calcula o escore em tempo real.
  4. Após preencher todos os itens, o botão "Copiar para prontuário" é liberado.
  5. O médico cola o resultado (com data e detalhes) diretamente no sistema do hospital/clínica.

## Stack técnica
- **Frontend:** HTML5, CSS3 (Vanilla) e JavaScript (Vanilla).
- **PWA:** Service Workers para funcionamento offline e Manifesto para instalação como App.
- **Tipografia:** DM Serif Display (Títulos) e DM Sans (Corpo).
- **Cores Principais:** `#0f3540` (Primary Dark), `#1a5c6a` (Teal), `#e07b3b` (Accent).

## Estrutura de arquivos
- `index.html`: Arquivo único contendo toda a interface, estilos e lógica das escalas (SCALES object).
- `manifest.json`: Configurações de instalação da PWA.
- `sw.js`: Service Worker para cache de assets e funcionamento offline.
- `icon-512.png`: Ícone do aplicativo.

## Como rodar localmente
1. Basta abrir o arquivo `index.html` em qualquer navegador moderno.
2. Para testar as funcionalidades de PWA (instalação e cache), é recomendado utilizar um servidor local (ex: `Live Server` do VS Code ou `python -m http.server`).

## Decisões técnicas importantes
- **Single File Architecture:** Toda a lógica e estilo estão concentrados no `index.html` para facilitar o funcionamento offline e garantir que todos os dados necessários sejam carregados de uma vez.
- **Zero Dependências:** Não utiliza frameworks externos para garantir performance máxima em dispositivos móveis antigos.
- **State Management:** Utiliza um objeto `states` simples para rastrear as respostas em tempo real sem persistência em banco de dados (focado em privacidade e agilidade).

## Funcionalidades implementadas
### Escalas Disponíveis:
- [x] **MG-ADL:** Atividades de vida diária na Miastenia Gravis.
- [x] **MGC:** Myasthenia Gravis Composite (escore misto).
- [x] **MGFA:** Classificação clínica da MG.
- [x] **INCAT:** Escala de incapacidade para neuropatias inflamatórias.
- [x] **I-RODS:** Escala de Rasch para neuropatias.
- [x] **ALSFRS-R:** Escala funcional revisada para ELA.

### Recursos:
- [x] Cálculo automático de score.
- [x] Barra de progresso por itens.
- [x] Gerador de texto para prontuário (Copy to Clipboard).
- [x] Suporte a PWA (Installable/Offline).
- [x] Banner de instalação específico para iOS.

## Para a IA que vai assumir este projeto
**Contexto:** Este projeto é uma ferramenta clínica de alta precisão. Os valores de "s" (score) no objeto `SCALES` seguem rigorosamente os manuais médicos de cada escala.

**Padrões adotados:**
- Identidade visual baseada em tons de Teal (`#0f3540`) e Branco, com fontes Google.
- Comentários em português para facilitar a leitura do Dr. Igor.
- Lógica de escala baseada em objetos JSON (`SCALES`) para facilitar a adição de novas patologias.

**Não alterar sem discussão:**
- A pontuação máxima (`maxScore`) e os pesos de cada item (algumas escalas como MGC não possuem pesos uniformes).
- O fluxo de liberação do botão "Copiar" (deve sempre exigir 100% de preenchimento).
