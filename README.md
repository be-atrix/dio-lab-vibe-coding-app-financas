# Conceito e PRD do app Conversa Financeira

Conversa Financeira propõe organizar receitas, gastos e metas por meio de linguagem natural. O MVP reduz o trabalho de preencher formulários, mas exige confirmação antes de registrar uma transação inferida pela IA.

## Problema e público

O público inicial são pessoas que desejam acompanhar gastos cotidianos e abandonam planilhas por dificuldade de manter o registro. A hipótese é que registrar um gasto pelo chat exige menos esforço e aumenta a frequência de uso. Essa hipótese precisa ser testada; não é uma conclusão de pesquisa com usuários.

## Prompt final para a IA

Crie o conceito e o plano de MVP do app Conversa Financeira, em português brasileiro. O usuário registra receitas e despesas por conversa, confirma os dados extraídos, acompanha um resumo mensal e define metas de economia. Entregue fluxo de telas, comportamento do agente, modelo de dados, regras de validação e plano de teste. Use linguagem simples e tom educativo.

O fluxo principal deve aceitar mensagens como “gastei 32,50 no almoço hoje”, extrair valor, tipo, categoria e data, apresentar esses campos para confirmação e registrar somente após o usuário confirmar. Se houver ambiguidade, pergunte antes de gravar. Ofereça edição e exclusão com desfazer. Não invente valores, datas ou transações ausentes. Respeite vírgula decimal e moeda BRL.

Mostre receitas, despesas e saldo do mês, com acesso aos lançamentos que compõem cada total. Permita filtrar por período e categoria. Uma meta contém nome, valor alvo, data desejada e valor acumulado. Sugestões de economia devem se basear em dados confirmados e mostrar o cálculo; o usuário decide se aceita. Não ofereça recomendações de investimentos ou promessas de rendimento.

As telas do MVP são apresentação, conversa e confirmação, lançamentos, resumo e metas. Use uma coluna no celular, rótulos acessíveis e contraste legível. Evite integração bancária, cartão e pagamentos nesta versão. Use apenas dados fictícios identificados como demonstração. Explique como separar dados por usuário caso haja persistência. Nunca coloque credenciais no frontend nem use dados financeiros reais para testar.

## Fluxo proposto

1. O usuário abre a conversa e informa um gasto.
2. O agente mostra os campos interpretados e pede confirmação.
3. O lançamento confirmado aparece na lista e atualiza o resumo.
4. O usuário revisa os gastos por categoria e define uma meta.
5. O agente calcula uma sugestão de economia e explica a origem dos números.

## Comportamento do agente

O agente atua como organizador de registros. “Ontem paguei uma conta” não basta para criar um gasto: ele deve perguntar o valor e a categoria. “Recebi 200 e gastei 40” produz duas propostas separadas. A soma de despesas não pode incluir uma receita como valor negativo sem explicação. O usuário sempre pode corrigir a interpretação.

## Plano de validação

| Caso | Resultado esperado |
| --- | --- |
| “Gastei 32,50 no almoço hoje” | Proposta de despesa de R$ 32,50, alimentação e data atual, aguardando confirmação |
| Mensagem sem valor | Pergunta de esclarecimento e nenhum registro |
| Receita de R$ 200 e gasto de R$ 40 | Dois lançamentos e saldo de R$ 160 |
| Corrigir um gasto para R$ 35 | Lista e totais atualizados sem duplicação |
| Meta de R$ 600 em três meses, sem valor inicial | Sugestão de R$ 200 por mês com cálculo explícito |

Em um piloto, medir tempo para registrar um gasto, proporção de interpretações corrigidas e número de registros repetidos na semana. Entrevistar usuários antes de concluir que a solução resolve o problema.

## Processo de criação com IA

O conceito, o PRD e o plano de validação foram preparados com assistência do Codex. A proposta inicial foi refinada para incluir confirmação de lançamentos, esclarecimento de ambiguidades, separação de receitas e despesas e cálculos explicados. Esses critérios tornam o conceito revisável antes de uma implementação.

A revisão complementar foi executada no GitHub Copilot em 13 de outubro de 2026. A resposta confirmou o fluxo de confirmação antes de persistir, edição sem duplicar, metas e cálculo explicado; também propôs um plano de validação com usuários. As métricas sugeridas são hipóteses, não resultados medidos. Voz e aprendizado automático sugeridos pela IA foram deixados fora do MVP para manter o escopo simples. O exemplo de prazo do Copilot exige conferir a data de referência antes de aplicar o cálculo. O Lovable apresentou um painel vazio após o login e não gerou uma aplicação.

## Reflexão sobre o processo

Definir exemplos concretos ajudou a transformar a ideia em requisitos verificáveis. A regra de confirmar o lançamento antes de salvar evita tratar uma interpretação probabilística como um fato financeiro. A separação entre proposta, registro confirmado e relatório tornou o fluxo mais claro.

O Copilot gerou uma revisão útil do conceito, enquanto o Lovable permaneceu indisponível nesta sessão. O plano de testes permanece uma proposta; não houve aplicação implementada nem validação com usuários. O aprendizado central é que instruções específicas precisam vir acompanhadas de critérios de aceitação e de uma descrição honesta do que foi executado.

## Escopo da entrega

Este é um projeto conceitual, conforme a opção sem código do desafio. Não representa um app publicado nem oferece aconselhamento financeiro.

## Evidência da interação

A captura abaixo registra a interação real com o GitHub Copilot. Ela documenta a revisão do conceito, não um app implementado.

![Revisão real do conceito pelo GitHub Copilot](https://github.com/user-attachments/assets/0246f7a1-0c1b-4102-b63f-b55fe019cec1)
