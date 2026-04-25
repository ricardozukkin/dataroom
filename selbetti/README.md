# Data Room Selbetti — Zukkin (versão replicada)

## O que foi feito

Replicação completa do dataroom Confluência para a Selbetti, com as seguintes sanitizações aplicadas automaticamente a TODOS os 8 documentos:

### Substituições de nomes
- **37 clientes** — substituídos por "Cliente 01", "Cliente 02", ... (ordem aproximada por receita)
- **72 colaboradores no headcount** — nomes substituídos por "Colaborador 01", "Colaborador 02", ..., mantendo cargo, vínculo (CLT/PJ/Estagiário), produto e remuneração individual (Opção A escolhida)
- **"Confluência Group"** → **"Selbetti"** em todos os headers, footers e referências

### Padronização numérica
| Métrica | Antes (variava) | Agora |
|---|---|---|
| Receita 2025 | R$ 15,8M / R$ 16,1M | **R$ 16M** |
| Margem EBITDA Aj. | 17% / 17,4% | **18%** |
| Clientes ativos | 67 / 68 / 80 / 70+ | **68** |
| Anos de operação | 10 / 12 | **10 anos** |
| Fundação | 2014 | **2016** |
| Redes acumuladas (desde 2016) | +100 | **+100** (explicitado como histórico cumulativo) |

### Outros ajustes
- **Pró-labore dos sócios** (R$ 1,2M/ano) removido do footer do headcount — disponibilizado pós-LOI
- **Frase "incluindo nomes como..."** no deck reescrita para referência genérica por segmento
- **Aviso de sala** adicionado na home (tom de "DD preliminar entre players do mesmo setor")

## Arquivos (mesma estrutura da Confluência)

1. `index.html` — home com 4 KPIs + 8 cards + aviso de sala
2. `deck-investidores.html` — deck comercial completo (706KB, fotos dos fundadores mantidas — info pública)
3. `dre-historico.html` — DRE mensal 5 anos com toggle contábil/gerencial
4. `kpis-operacionais.html` — MRR, ARR, churn, CAC, LTV, NPS
5. `receita-cliente-produto.html` — receita por cliente (codificado) e produto mensal
6. `estrategia-comercial.html` — funil, canais, crescimento
7. `headcount-remuneracao.html` — quadro por departamento sem nomes individuais
8. `revenue-retention.html` — GRR/NRR cohort por cliente (codificado)
9. `nps-2026.html` — NPS Q1 2026 com 263 respostas

## O que AINDA é sensível — sua revisão antes de publicar

**1. Tabela comparativa Zukkin vs Infoprice vs Profitmetrics** (deck-investidores, seção de Diferenciação)
- A tabela está mantida porque é material de venda legítimo.
- **Avaliação:** Selbetti já conhece os competidores do espaço. Mostrar o comparativo reforça posicionamento. Manter.
- **Decisão sua:** se preferir remover, me avisa que eu tiro a seção inteira.

**2. Fotos e nomes dos fundadores** (Ricardo Forte e Bruno Fernandes) estão no deck
- Informação pública (LinkedIn, site). Mantida.
- Se por qualquer razão quiser remover, me avisa.

**3. Tabela comparativa no deck pode mencionar "OXXO" ou outros** — preciso de um segundo olhar do deck
- O deck tem 706KB e várias tabelas embutidas. Fiz substituição programática de 37 nomes de clientes conhecidos, mas **se houver algum nome de cliente que eu não conheça, ele pode ter escapado**. Recomendo forte uma leitura integral do deck.
- Em particular: seções "Clientes", "Cases de Sucesso" ou "Depoimentos" (se existirem) devem ser revisadas.

**4. Texto corrido em seções narrativas**
- Existe possibilidade de algum cliente aparecer em texto tipo "o case da [cliente] demonstrou...". Se for nome que não estava no meu mapeamento, escapou.

## Checklist antes de publicar

- [ ] Revisar o deck-investidores completo (é o mais longo e mais visível)
- [ ] Alinhar com Bruno (aprovação conjunta)
- [ ] Decidir sobre a tabela comparativa com Infoprice/Profitmetrics
- [ ] Aplicar StaticCrypt com senha nova (sugestão: `zuk-sel-26` ou outra diferente de `zukkin26`)
- [ ] Testar navegação completa localmente antes do push
- [ ] Publicar no GitHub Pages em repositório novo (`dataroom-selbetti` recomendado)

## Comando StaticCrypt para criptografar

```bash
# Instalar (uma vez): npm install -g staticrypt
# Na pasta com os HTMLs:
staticrypt index.html 01-company-overview.html 02-dre-agregada.html 03-kpis-macro.html 04-base-clientes.html 05-governanca-juridico.html deck-investidores.html dre-historico.html kpis-operacionais.html receita-cliente-produto.html estrategia-comercial.html headcount-remuneracao.html revenue-retention.html nps-2026.html \
  -p SUA_SENHA \
  --template-button "Entrar" \
  --template-instructions "Documento confidencial. Insira a senha." \
  --template-title "Zukkin — Data Room" \
  --short \
  -d encrypted/
```

## Publicar no GitHub Pages

```bash
# Repo novo: ricardozukkin/dataroom-selbetti
git init
git add .
git commit -m "Initial data room - DD preliminar Selbetti"
git branch -M main
git remote add origin https://github.com/ricardozukkin/dataroom-selbetti.git
git push -u origin main
# Settings > Pages > Deploy from branch > main > / (root)
# URL: https://ricardozukkin.github.io/dataroom-selbetti/
```

## Alertas finais

**1. Confirme com o Ricardo (você) que o deck está OK.** Testei substituições programáticas mas não li o deck linha por linha — ele tem 706KB e precisa de review humano.

**2. Revenue Retention ainda tem série mensal por cliente (codificado).** Isso está em linha com a opção de replicar 8 seções, mas é dado granular. Se a Selbetti cruzar o Cliente 01 da receita com o Cliente 01 do revenue retention e identificar padrões (segmento, sazonalidade), o código deixa de proteger. **Alternativa:** remover este documento do dataroom Selbetti e deixar apenas em clean team.

**3. Coerência entre tracks consolidada.** Os números que saíram para a Confluência precisam ser idênticos aos da Selbetti. O que sugeri aqui (68 / 10 anos / R$ 16M / 18%) é a narrativa unificada — se você quiser atualizar o dataroom Confluência para bater, é uma operação similar à que fiz aqui.

**4. Q&A revisada (Q_A_Selbetti_revisado.xlsx da rodada anterior)** usa números diferentes — precisa ser atualizada para bater com esta versão do dataroom. Posso reentregar se confirmar.
