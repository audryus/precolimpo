# 🇧🇷 Preço Limpo

> **O imposto real que você paga — sem enganação.**

No Brasil, os impostos são divulgados como uma fração do preço final de venda. Isso cria uma ilusão: um produto com 33% de imposto *declarado* na nota fiscal, na prática, representa **51% de imposto sobre o custo real do produto**. O **Preço Limpo** calcula essa diferença e mostra a verdade ao consumidor.

---

## 🧮 A matemática por trás

O imposto declarado nas notas fiscais brasileiras é calculado **por dentro** (sobre o preço final), e não **por fora** (sobre o custo). Isso subestima sistematicamente a carga tributária real.

### Fórmulas

```
t  = I / P           → alíquota declarada (imposto sobre o preço final)
C  = P × (1 − t)     → custo real do produto (sem imposto)
I  = P − C           → valor do imposto em R$
τ  = I / C           → taxa real do imposto (sobre o custo)
```

### Exemplo prático (cupom de mercado)

| Campo | Valor |
|---|---|
| Valor total pago (P) | R$ 100,45 |
| Imposto declarado (I) | R$ 34,06 |
| Alíquota declarada | 33,91% |
| **Custo real (C)** | **R$ 66,39** |
| **Imposto real (τ = I/C)** | **51,30%** |

O consumidor pagou **R$ 34,06 de imposto sobre um produto que custou R$ 66,39** — ou seja, mais da metade do custo real foi para o Estado.

---

## ✨ Funcionalidades

- **Cálculo do imposto real total** a partir do valor pago e do imposto declarado
- **Detalhamento por esfera**: informe o imposto Federal e/ou Estadual separadamente para ver o imposto real de cada um
- **Sincronização automática de campos**:
  - Preencher Fed + Est → Total atualizado automaticamente
  - Preencher Total manualmente → Fed e Est são limpos
- **Suporte a padrão BR**: aceita vírgula (`,`) e ponto (`.`) como separador decimal
- **Aviso sobre IRPJ**: estimativa do imposto de renda empresarial embutido no custo restante, com valores para Simples Nacional (~4%) e Lucro Presumido (~6,73%)
- Layout **dark mode premium** com glassmorphism e animações

---

### Arquivos de configuração incluídos

| Arquivo | Finalidade |
|---|---|
| `_headers` | Headers HTTP de segurança (X-Frame-Options, CSP, etc.) |
| `_redirects` | Fallback SPA — todas as rotas servem `index.html` |

---

## 🛠️ Stack técnica

| Tecnologia | Uso |
|---|---|
| HTML5 | Estrutura semântica |
| JavaScript (vanilla) | Toda a lógica de cálculo — zero dependências |
| [DaisyUI v4](https://daisyui.com/) via CDN | Componentes de UI (tema `night`) |
| [Tailwind CSS](https://tailwindcss.com/) via CDN | Utilitários de estilo |
| [Inter](https://fonts.google.com/specimen/Inter) via Google Fonts | Tipografia |

Não há `package.json`, `node_modules`, bundler ou qualquer processo de build. O deploy é literalmente fazer upload de um HTML.

---

## 📁 Estrutura do projeto

```
precolimpo/
├── index.html      # Aplicação completa (HTML + CSS inline + JS inline)
├── _headers        # Headers de segurança para Cloudflare Pages
├── _redirects      # Redirect SPA fallback
└── README.md       # Este arquivo
```

---

## ⚠️ Sobre o IRPJ

O valor real do produto calculado pelo Preço Limpo **ainda inclui o IRPJ** — o Imposto de Renda da Pessoa Jurídica pago pelas empresas e repassado ao consumidor no preço. O app exibe uma estimativa desse imposto oculto com base no regime tributário:

| Regime | Alíquota estimada s/ faturamento |
|---|---|
| Simples Nacional (melhor caso) | ~4% |
| Lucro Presumido (melhor caso) | ~6,73% |

> Os valores são estimativas educativas e não substituem consultoria tributária especializada.

---

## 📜 Licença

MIT — use, modifique e distribua livremente.
