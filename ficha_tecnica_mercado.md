
# O Mercado – Ficha Técnica.

## Processamento e Análises

1. Centralização dos dados das três planilhas em uma base de trabalho com a fórmula `IMPORTRANGE`.

2. Limpeza dos dados:
   - Valores nulos em `salario_anual_dolar` foram preenchidos com a média.
   - Valores nulos em `id_cliente` da planilha `transacoes` foram removidos com a fórmula:
     ```
     (=QUERY(IMPORTRANGE("link_planilha_transacoes"; "transacoes!A1:D"); "SELECT * WHERE Col2 IS NOT NULL"; 1)
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

6. Conversão para Scores (`1–4`) com base em `QUARTIL`. Segmentação em 6 grupos com base em Recência e média entre Frequência e Valor Monetário.  ![image](https://github.com/user-attachments/assets/d1462027-7c5c-4017-8749-fa075a0cd6e8)


7. Com todos os dados necessários prontos, estes foram visualizados e analisados no **Looker Studio** a partir da criação de um dashboard interativo. Aqui foram identificados os padrões, tendências e priorização dos segmentos. Atenção aqui para o fato de que nesta análise foi escolhido priorizar os segmentos por receita gerada e não pela quantidade de clientes. 

---

## Resultados e Observações / Insights

- A base demonstra uma queda expressiva nas transações. Em maio de 2022 houve um pico nas vendas e depois houve uma queda de mais de 50% até dezembro do mesmo ano. Isso pode indicar perda de engajamento, no entanto, a base de dados atual não permite investigar com precisão o porquê, mas o dado pede atenção. 

- Em geral a loja tem um público de ticket médio alto, com predominância da Geração X e Baby Boomers graduados, com parceiro e pelo menos 1 criança em casa. 
- Há uma forte concentração de vendas em vinhos e carnes indicando um possível posicionamento mais nichado, ou até mesmo uma falta de variedade na oferta. 
- 29% das vendas são feitas online, mostrando que o canal digital tem força - mas a loja física ainda é predominante. 
- A presença dos clientes na loja física demonstra um potencial para a oferta de um atendimento de excelência em conjunto com uma experiência diferenciada que fideliza esses clientes. 

- Reforçar o canal digital para o público que já o utiliza através de benefícios exclusivos. 

- Usar os dados comportamentais para campanhas com recomendações baseadas em últimas compras e frequência.
- Ao segmentar os clientes, e analisar quanto cada grupo contribui financeiramente, se observa os três grupos que mais demandam atenção e ação especial: **Precisam de Atenção**, **Promissores** e **Leais de Ouro**. Eles concentram o maior volume de receita e são excelentes alvos para retenção ou reengajamento. 

- Mesmo sendo o menor grupo, em termos de quantidade de clientes e gastos, os Recém-Chegados possuem um grande valor: representam potencial. Aqui é possível iniciar uma jornada de relacionamento com o intuito de fidelizar esses clientes. 

- Uma sugestão prática é a criação de um programa de fidelidade que siga a segmentação, oferecendo vantagens e experiências baseadas no grupo em o que cliente está inserido, isso promove a vontade de subir de grupo. 


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
