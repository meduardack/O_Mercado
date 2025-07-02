
# O Mercado – Ficha Técnica

## Projeto  
**O Mercado – Segmentação de base de clientes**

---

## Cenário
- O mercado não conhece mais o perfil dos seus clientes;  
- O ambiente está mais competitivo e os clientes mudaram suas preferências;  
- Eles querem fidelizar os clientes mas não sabem como.

---

## Objetivo  
Compreender o perfil e comportamento dos clientes da loja **"O Mercado"** por meio da segmentação baseada em **RFM**:
- Identificar diferentes perfis de consumidores (em grupos);  
- Identificar onde priorizar os esforços;  
- Apoiar estratégias de marketing e retenção por meio do conhecimento dos clientes (informações ocultas);  
- Identificar insights para tomada de decisões mais eficazes (ex: características de oferta de produtos).

---

## Ferramentas e Tecnologias  
- **Google Sheets** – limpeza, organização e análise dos dados  
- **Looker Studio** – criação de dashboard, gráficos e análises visuais  
- **Google Slides** – apresentação dos resultados

---

## Processamento e Análises

1. Centralização dos dados das três planilhas em uma base de trabalho com a fórmula `IMPORTRANGE`.

2. Limpeza dos dados:
   - Valores nulos em `salario_anual_dolar` foram preenchidos com a média.
   - Valores nulos em `id_cliente` da planilha `transacoes` foram removidos com a fórmula:
     ```
     =QUERY(IMPORTRANGE("link_planilha_transacoes"; "transacoes!A1:D"); "SELECT * WHERE Col2 IS NOT NULL"; 1)
     ```
   - Duplicidades na planilha `resumo_compras` foram identificadas via formatação condicional e removidas com `UNIQUE`.
   - Outliers em `ano_nascimento` foram mantidos por representarem uma parcela ínfima.

3. Enriquecimento:
   - A partir de `transacoes` (`transacoes_raw`) criou-se a aba `transacoes_filtradas` com base nos `id_cliente`. Variáveis: `n_compras`, `ultima_compra`, `preferencia`.
   - De `resumo_compras`, criou-se `compras_filtradas`. Variáveis: `total_gasto`, `media_por_compra`, `produto_mais_comprado`.
   - De `clientes` (`clientes_raw_`), criou-se `clientes_filtrados`. Variáveis: `idade`, `qts_criancas`, `possui_parceiro`, `geracao`, média salarial preenchendo nulos.

4. Organização final na aba `base_principal`, com fórmulas aplicadas: `SE`, `INDEX+MATCH`, `PROCV`.  
   **Nota**: dificuldades com intervalos solucionadas com uso do `F4` para fixar células.

5. Análise **RFM** utilizando: `CONT.SE`, `DIAS360`, `SOMA`, `PROCV`.

6. Conversão para Scores (`1–4`) com base em `QUARTIL`. Segmentação em 6 grupos com base em Recência e média entre Frequência e Valor Monetário.

7. Visualização dos dados no **Looker Studio** em um dashboard interativo.

---

## Resultados e Observações / Insights

- Queda de mais de 50% nas transações após pico em maio/2022.
- Público predominante: ticket médio alto, Geração X e Baby Boomers, com graduação, parceiro e filhos.
- Vendas concentradas em vinhos e carnes.
- 29% das vendas são online – canal físico ainda predominante.
- Potencial de fidelização com atendimento presencial diferenciado.
- Reforço ao canal digital com benefícios exclusivos.
- Uso de dados comportamentais para campanhas personalizadas.
- Grupos prioritários: **Precisam de Atenção**, **Promissores**, **Leais de Ouro**.
- Grupo **Recém-Chegados** tem grande potencial para fidelização.
- Sugestão: criar programa de fidelidade baseado na segmentação.

---

## Perfis da Segmentação / Ações Recomendadas

1. **Leais de Ouro**
   - Alto gasto, alta frequência, compras recentes.
   - Engajamento crescente, grupo mais valioso.
   - Ação: experiências exclusivas, brindes, acesso antecipado, comunicação premium.

2. **Potenciais de Ouro**
   - Alta recência, boas médias de frequência e valor.
   - Prontos para crescer na fidelização.
   - Ação: comunicação de reconhecimento, vantagens progressivas, convite ao programa.

3. **Promissores**
   - Boa frequência e valor, engajamento recente.
   - Quase se tornando Leais.
   - Ação: campanhas de recompra, cupons, kits promocionais, incentivo ao avanço.

4. **Precisam de Atenção**
   - Já foram engajados, redução nas compras.
   - Em queda acentuada.
   - Ação: reengajamento rápido com ofertas personalizadas, reforço emocional.

5. **Recém-Chegados**
   - Primeiras compras recentes, pouco histórico.
   - Alto potencial de fidelização.
   - Ação: plano de boas-vindas, tutoriais, brindes, relacionamento desde o início.

6. **Hibernando**
   - Compras antigas e pouco frequentes.
   - Desengajados há meses.
   - Ação: reativação direta com ofertas especiais. Se inativos, ações de baixo custo.

---

## Limitações / Próximos Passos

- Ausência de variáveis como sexo, endereço, ocupação.
- Falta de dados comportamentais fora da compra (visitas, canais de origem).
- Sem cruzamento direto entre valor da compra e `id_transacao` (limita leitura temporal).
- Inserção futura de informações internas (promoções, variações de preços).
- Coleta de dados deve ser ampliada com foco estratégico em fidelização.
- Manter a base atualizada sempre.

---

## Links de Interesse

- [Planilha O Mercado – Google Sheets](https://docs.google.com/spreadsheets/d/1rVBJBRYqAeitUALBxqQ_Z38FA-_gL4Opw0XzYJLBc_o/edit?usp=sharing)  
- [Dashboard Analítica – O Mercado (Looker Studio)](https://lookerstudio.google.com/reporting/5fee2aee-4e19-425c-9682-6fd1f998b334)

---

*Maria Eduarda Carvalho – Jornada de Dados 2025.1*
