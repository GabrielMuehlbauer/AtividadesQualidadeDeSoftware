# Níveis de Testes #

## Teste de Componentes ##
O teste de componente (também conhecido como teste de unidade ou módulo) se concentra em componentes que são testáveis
separadamente.

**Exemplo:** Testar isoladamente uma função no código que calcula o valor de frete de uma compra (ex: `calcularFrete()`), verificando se o retorno numérico está correto em diferentes regiões.

### Defeitos Típicos e Falhas ###
- Funcionalidade incorreta
- Problemas no fluxo de dados
- Código e lógica incorretos

## Teste de Integração ##
O teste de integração se concentra nas interações entre componentes ou sistemas.

**Exemplo:** Verificar se a tela de finalização de compra do site consegue enviar as informações corretamente e sem perda de dados para a API de pagamentos externa.

### Defeitos Típicos e Falhas ###
- Dados incorretos, dados ausentes ou codificação de dados incorreta.
- Sequenciamento ou temporização incorretos de chamadas de interface.
- Incompatibilidade de interface.
- Falhas na comunicação entre componentes.
- Falha de comunicação não manipulada ou tratada de forma errada entre
componentes.
- Suposições incorretas sobre o significado, as unidades ou limites dos dados que estão sendo transmitidos entre os componentes.

## Teste de Sistema ##
O teste de sistema se concentra no comportamento e nas capacidades de todo um sistema ou produto, geralmente considerando as execuções das tarefas de ponta a ponta do sistema e os comportamentos não funcionais exibidos ao executar tais tarefas.

**Exemplo:** Realizar um fluxo completo num e-commerce de ponta a ponta: criar uma nova conta, buscar o produto, adicionar ao carrinho, pagar com cartão e confirmar o recebimento do e-mail de sucesso.

### Defeitos Típicos e Falhas ###
- Cálculos incorretos.
- Comportamento funcional ou não funcional do sistema incorreto ou inesperado.
- Controle e/ou fluxos de dados dentro do sistema incorretos.
- Falha na execução correta e completa de tarefas funcionais de ponta a ponta.
- Falha do sistema em funcionar adequadamente no(s) ambiente(s) de produção.
- Falha do sistema para funcionar conforme descrito nos manuais do sistema e do
usuário.

## Teste de Aceite ##
O teste de aceite, como o teste do sistema, geralmente se concentra no comportamento e na capacidade de todo um sistema ou produto. Formas comuns de testes de aceite incluem o seguinte:
- Teste de aceite do usuário: com o usuário, simulando uso real;
- Teste de aceite operacional: com o time, simulando “devops” em ambiente similar a prod;
- Teste de aceite contratual e regulatório: com todos para atender a contrato ou ao gov;
- Teste Alfa e Beta: Alfa o usuário testa em “desenvolvimento”, Beta o usuário testa após o desenvolvimento, como prod.

**Exemplo:** Uma versão "Beta" de um novo aplicativo de transporte é disponibilizada para um pequeno grupo de motoristas reais para atestar se o app atende bem às suas necessidades diárias antes do grande lançamento.

### Defeitos Típicos e Falhas ###
- Fluxos de trabalho do sistema não atendem aos requisitos do negócio ou do usuário.
- Regras de negócios não são implementadas corretamente.
- O sistema não satisfaz os requisitos contratuais ou regulatórios.
- Falhas não funcionais, como vulnerabilidades de segurança, eficiência de
desempenho inadequada sob altas cargas ou operação inadequada em uma plataforma suportada.

# Tipos de Teste #
- **Teste Funcional:** avaliam as funções que o sistema deve executar. **Exemplo:** Confirmar se clicar no botão de "Criar Usuário" realmente insere o novo registro no banco de dados.
- **Teste Não Funcional:** avaliam as características de sistemas e de softwares, como usabilidade, eficiência de desempenho ou segurança. **Exemplo:** Validar se a tela principal demora menos de 2 segundos para carregar num cenário de pico de acessos.
- **Teste Caixa-Branca:** voltado para a cobertura de código. **Exemplo:** O desenvolvedor cria um script que passa por todos os laços de repetição e cenários lógicos (`if/else`) construídos na arquitetura da função.
- **Teste Caixa-Preta:** focam nas funcionalidades e requisitos (entradas/saídas) sem conhecimento do código, ideal para validar a experiência do usuário. **Exemplo:** O testador preenche as informações de um formulário e clica em "Salvar", avaliando unicamente se a mensagem de sucesso aparece corretamente na interface.
- **Teste Relacionado à Mudança:** executados apenas quando são feitas alterações em um sistema, para confirmar se atende a demanda. **Exemplo:** Após os desenvolvedores atualizarem o framework da aplicação, realiza-se um teste de regressão no Login para garantir que a mudança não o quebrou.

***É possivel executar qualquer tipo de teste em qualquer nível de teste.***

# Tecnicas de Teste #
## Caixa-Preta ##
- Particionamento de equivalência: **Exemplo:** Para um campo numérico que aceita de 18 a 60 anos, testam-se o 30 (classe válida) e o 10 (classe inválida), assumindo que o resultado de suas execuções será igual para o resto do grupo de números.
- Análise de valor limite: **Exemplo:** No mesmo campo que exige idade de 18 a 60 anos, testam-se apenas os extremos exatos e seus limites próximos para verificar quebras: 17, 18, 60 e 61.
- Teste de tabela de decisão: **Exemplo:** Cruzar em uma tabela se o cliente é "Assinante VIP" (Sim/Não) e se tem "Cupom de 10%" (Sim/Não) para validar os descontos para cada uma das quatro regras de negócio combinadas.
- Teste de transição de estado: **Exemplo:** Simular e conferir se o andamento de um pedido online transita corretamente do status "Aguardando Pagamento" -> "Pago" -> "Enviado".
- Teste de caso de uso: **Exemplo:** Seguir estritamente o manual e as etapas pré-definidas que um cliente comum faria ao tentar pedir o estorno de uma compra.

## Caixa-Branca ##
- Teste e cobertura de instruções: **Exemplo:** Assegurar que os testes passem obrigatoriamente por todas as linhas de código escritas no componente pelo menos uma vez.
- Teste de decisão e cobertura: **Exemplo:** Em verificações lógicas no código (um `if`, por exemplo), assegurar que os testes forcem o resultado de Verdadeiro e também de Falso para validar ambas as reações.
- O valor da instrução e teste de decisão: **Exemplo:** Analisar matematicamente os relatórios de cobertura para verificar se a profundidade e a quantidade de cenários alcançados pelos testes unitários conferem confiança suficiente para lançar a versão.

## Baseadas na experiência ##
- Suposição de erro: **Exemplo:** Baseado em experiências passadas, um QA preenche propositalmente a data "29/02" em um ano não bissexto porque já supõe que o software poderá travar se os desenvolvedores não o tiverem tratado.
- Teste exploratório: **Exemplo:** O testador navega no sistema recém-criado sem um roteiro engessado, descobrindo organicamente as funcionalidades e planejando casos de uso variados na mesma medida que explora a tela.
- Teste baseado em lista de verificação: **Exemplo:** Utilizar um checklist simples (ex: "checar alinhamento", "validar em mobile", "testar no Safari") como um guia rápido para garantir que as revisões triviais de interface foram feitas.


Erro(engano humano) <br>
Defeito(Inconsistência, código errado) <br>
Falha(comportamento inesperedo, consequência do defeito)

**Quando for indicar um erro leve uma dúvida, não uma acusação.**