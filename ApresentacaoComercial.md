# Reunião Comercial -  Sistema de Remuneração


## Tópicos
• Overview do projeto;

• O que entregamos, e  o que está planejado para entregar;

## Primeira entrega

Em fevereiro houve uma entrega do MVP, do cálculo de remuneração, com cadastro dos parâmetrode remuneração, de empréstimo para REFIM; Alguns cálculos não é o SCAC que faz sozinho, mas em conjunto com outros sistemas, incluindo o função; Foi também o cálculo do diferido manutenção;


## Glossário util

### SPB

Sistema de pagamento bancário.

### REFIN OU Cálculo Unitário
Refin: Refinanciamento. É o valor cálculado para o novo contrato que vai ser gerado para o refinanciamento. O correspondente recebe um percentual de remuneração em cima da venda que ele fez.

O valor pago ao correspondente é parametrizado, e pode ser feito em faixas (até 50 parcelas, 15% por exemplo).

Parte do valor é pago a vista (por exigência do banco central), que é parâmetrizado (o campo remuneração originação), que é no máximo 6%.

O valor restante, de 14%, vai ser diferido. Dividido em 96 parcelas, durante a vida do contrato.

Exemplo: 500 reais o valor líquido de um contrato novo.
6% ele recebe avista, 30 reais.
14% de 500 - 70 reais em 96 parcelas.

Esse cálculo unitário pode ser parametrizado ao nível de correspondente, produto. "Super flexível".

### Diferido manutenção

Outra modalidade de cálculo.
Feita quando um cliente quer refinanciar um contrato que já foi refinanciando.

Exemplo:

José da Silva sauro possui 3 contratos:

Correspondente		Contrato 	Valor 		Parcelas
2020 				A 			110,00		50
4040				B 			50,00		35
1010				C 			20,00		20

Com o diferido manutenção, ao refinanciar, o correspondente 2020, 4040 e 1010 ainda receberiam uma parte desse valor ainda. Hoje, ele tem uma faixa de redutor, que é parametrizável, para perder uma porcentagem do valor. Esse é o fator redutor diferido manutenção.

É parametrizável apenas por convênio, no momento.


### Convênio

É um acordo feito com uma entidade. São os órgãos. Exemplo: Corpo de bombeiros.

### Operação

Tipo de "evento", como empréstimo ou cartão.

### Tipo de operação

Refim, Recompra, Portabilidade.

### Modalidade

Classificação dos produtos.

### Produto

Nome do produto. Ex: "Contrato do INSS, Promoções, campanhas"


### Legado

São vários sitemas integrados. Segue alguns:

- SCAC: O scac continua no ar, e ele efetuas os pagamentos. O nosso objetivo é substituir 
- SCCD;
- Função: Contábil e correspondentes. O responsável é o Marco; O contrato nasce como uma proposta no função, passando pela esteira. E depois passa por diversos sistemas;
- CEC;


### Sistemas Orienta


Disponibilizamos uma API de prévia de cálculo de remuneração. 
Correspondentes acessam ele. O Marco visualiza por ele;


## Sistema de remuneração - Entrega 2

### Entregue:

Gestão de parâmetros;
Gestão de correspondentes;
Aprovação de pagamento;


### Em andamento:

Realizar o fechamento diário para pagamento;
Gerar arquivo diariamente CRK Gestão (TED ao correspondente)
Contabilizar diariamente movimentação do pagamento

### Para produzir:

Relatórios financeiros
Relatórios contábil
Gerar arquivo diariamente CRK Contábil (Movimentação contas contábeis)


## Provisionar:


Reservar o dinheiro para pagamentos efetuados pelo banco. 
A provisão reserva o valor para uma conta definida no evento.

A conta origem/destino esta definida no roteiro contábil.
Pra cada tipo de evento, existe um roteiro.

## Contabilização de provisão

Buscar todos os eventos contábeis que tenham tipo de evento provisão.
Consultar tipo de lançamentos dos Eventos contábeis para provisão. (Crédito e Remuneração a vista por enquanto)
Buscar lançamentos com status em aberto e sem status de contabilização (nulo ou erro)
Se for liberado o pagamento do contrato ao cliente,  é verificado se o evento e roteiro estão cadastrados. A data que é utilizada é a data de liberação contrato. Essa data é utilizada para filtrar qual o roteiro contábil está válido naquela data.
É gerado o registro de contabilização com as contas cadastradas no roteiro contábil buscado.
