# RotaVision — Dados que você sente.

## 📦 Sobre o Projeto

RotaVision é um dashboard inteligente de monitoramento logístico desenvolvido para a **Fase 3 — Etapa 1** do Desafio dos Dados. A solução transforma dados brutos de entregas em insights acionáveis, permitindo que gestores identifiquem rapidamente:

- Transportadoras com maior índice de atraso
- Regiões geográficas críticas
- Entregas prioritárias para intervenção
- Tendências operacionais por meio de visualizações interativas

O projeto foi construído como uma aplicação web funcional em HTML/CSS/JavaScript puro, sem dependências externas além da biblioteca Chart.js para gráficos.

---

## 🧠 Lógica de Construção

### I. Identificação dos Atrasos

Os atrasos foram identificados por **comparação direta** entre dois campos de cada entrega:

```
delta = dias_reais - prazo_dias
```

- `delta > 0` → atraso
- `delta = 0` → entrega no prazo exato
- `delta < 0` → entrega antecipada

A partir desse delta, cada entrega recebeu uma classificação de criticidade:

| Delta | Classificação |
|-------|----------------|
| > 5 dias | Crítico |
| 1–5 dias | Alto risco |
| 0 dias | Atenção |
| < 0 dias | No prazo |

---

### II. Cálculos Realizados

Todos os cálculos foram implementados diretamente em JavaScript sobre a base de 10 entregas fornecida:

| Métrica | Cálculo |
|---------|---------|
| **Delta individual** | `real - prazo` |
| **Desvio percentual** | `(delta / prazo) × 100` |
| **% atraso por transportadora** | `(entregas_atrasadas / total_entregas) × 100` |
| **Média de dias de atraso** | `soma_dos_deltas / entregas_atrasadas` |
| **Score de risco** | `(pct_atraso × 0.6) + (desvio_proporcional_acumulado × 0.4)` normalizado entre 0–100 |

O Score de Risco foi concebido como um indicador sintético que combina **frequência** e **intensidade** dos atrasos por transportadora.

---

### III. Organização e Priorização das Informações

O dashboard segue uma **estrutura de funil — do geral para o específico**:

1. **KPIs macro** — leitura imediata da situação sem interação
2. **Comparativo individual** — cada entrega analisada isoladamente
3. **Ranking por transportadora** — agregação por operador logístico
4. **Análise regional** — identificação geográfica de problemas
5. **Score de risco** — métrica sintética para decisões contratuais
6. **Tabela priorizada** — ordenação padrão por maior atraso, com filtros por criticidade e transportadora

A priorização visual utiliza:
- Cores quentes (laranja/vermelho) para problemas graves
- Badges de criticidade na tabela
- Barras de progresso nos rankings e mapas
- Gauges semicirculares com transições suaves

> Um gestor consegue identificar o problema mais grave em menos de 5 segundos, mesmo sem interagir com os filtros.

---

## 🛠️ Tecnologias Utilizadas

| Tecnologia | Finalidade |
|------------|------------|
| HTML5 | Estrutura semântica da página |
| CSS3 | Estilização, animações, efeito granulado e design responsivo |
| JavaScript (ES6+) | Lógica de dados, manipulação do DOM, cálculos e interatividade |
| Chart.js | Gráficos complementares (não utilizado na versão final, mantido como fallback) |
| Google Fonts | Tipografia Space Grotesk e Inter |

---

## 📊 Funcionalidades do Dashboard

| Recurso | Descrição |
|---------|-----------|
| **KPIs animados** | Contagem progressiva de entregas, atrasos e maior desvio |
| **Gráfico de barras comparativo** | Prazo prometido vs. dias reais para cada entrega |
| **Ranking de transportadoras** | Ordenado por percentual de atraso |
| **Mapa regional interativo** | 5 regiões com cores proporcionais ao índice de atraso |
| **Score de risco com gauge** | 3 transportadoras avaliadas em semicírculo animado |
| **Tabela dinâmica** | Ordenação por qualquer coluna + filtros por status e transportadora |
| **Scroll reveal** | Animações de entrada conforme o usuário navega |
| **Canvas interativo no hero** | Linhas e pontos animados representando rotas |

---

## 👥 Equipe Nybble — ETEC Carapicuíba

| Membro | Papel |
|--------|-------|
| Elias Moraes | Data Engineer |
| Isabelly Miranda | UX & Frontend |
| Isabela Medeiros | Business Intelligence |
| Jullia Mendes | Product & Analytics |

---

## 🌐 Acesso ao Dashboard

O dashboard está hospedado e pode ser acessado via link público:

🔗 **[Clique aqui para acessar o RotaVision](#)** *(substituir pelo link real de publicação)*

> ⚠️ O link permanecerá ativo e funcional até o encerramento oficial do Desafio dos Dados.

---

## 📁 Estrutura do Projeto

```
/rota-vision/
├── index.html          # Dashboard completo (estilos + lógica + dados)
├── README.md           # Documentação do projeto
└── assets/             # (opcional) imagens e recursos estáticos
```

---

## 📝 Considerações Finais

O RotaVision foi desenvolvido com foco em **clareza analítica**, **usabilidade** e **tomada de decisão rápida**. A interface foi projetada para gestores logísticos que precisam identificar problemas sem recorrer a planilhas extensas ou relatórios manuais.

A base de dados utilizada é uma amostra simplificada para fins didáticos, mas a arquitetura do dashboard é escalável para volumes maiores de dados com a integração de um backend e banco de dados.

---

**RotaVision — Dados que você sente.**