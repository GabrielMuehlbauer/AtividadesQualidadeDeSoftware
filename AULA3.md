<h2>Anotações e atividades da aula de QA no Senac</h2>
<h3>7 Princípios de Teste:</h3> 
<ol>
<li>O teste mostra a presença de defeitos e não a sua ausência.</li>
<li>Testes exaustivos são impossíveis.</li>
<li>O teste inicial economiza tempo e dinheiro.</li>
<li>Defeitos se agrupam.</li>
<li>Cuidado com o paradoxo do pesticida.</li>
<li>O teste depende do contexto.</li>
<li>Ausência de erros é uma ilusão.</li>
</ol>

---

<h3>TDD: Desenvolvimento Orientado por Testes</h3>
<strong>Benefícios:</strong> Feedback rápido e contínuo, código limpo, segurança no refatoramento de código, maior produtividade e menor possibilidade de falhas. <br>

<h3>Teste Unitário</h3>

- Determinítico
- Atômico
- Isolado
- Rápido

O BDD (Desenvolvimento Orientado ao Comportamento) é um complemento ao TDD.

**dado** um determinado contexto, **quando** ocorrer algo, **então** se espera algo.

<h3>Atividade</h3>
Com base em uma rotina de CRUD de usuários (incluindo a função
Login) em um sistema Web simples, faça o BDD das rotinas do
sistema (CRUD + Login).
Salve separadamente no repositório. (Anote também os princípios
de teste).

R: 
### **Login**
**Dado** que o usuário está na página de login 
**Quando** ele insere o e-mail e a senha **e** clica no botão "Entrar" 
**Então** ele deve ser redirecionado para a página inicial do painel **e** deve ver a mensagem de boas-vindas. 

### **CREATE usuário**
**Dado** que o administrador está na página de "Novo Cadastro" 
**Quando** ele preenche os campos obrigatórios: Nome, E-mail e Senha **e** clica no botão "Salvar" 
**Então** o sistema deve exibir a mensagem "Usuário cadastrado com sucesso!" **E** o usuário cadastrado deve aparecer na lista de usuários ativos.

### **READ usuário** 
**Dado** que o administrador está na página de "Listagem de Usuários" 
**Quando** ele busca por um usuário **e** clica no ícone "Ver Detalhes" 
**Então** o sistema deve exibir uma tela com as informações completas daquele usuário.

### **UPDATE usuário** 
**Dado** que o administrador está visualizando os detalhes do usuário "Gabriel" 
**Quando** ele altera o campo "Nome" para "Gabriel Felipe" **e** clica em "Atualizar Cadastro" 
**Então** o sistema deve exibir a mensagem "Dados atualizados com sucesso!" **E** o nome do usuário na listagem deve constar como "Gabriel Felipe".

### **DELETE usuário** 
**Dado** que o administrador está na página de "Listagem de Usuários" 
**Quando** ele clica no ícone "Excluir" ao lado de um determinado usuário **e** confirma a exclusão no modal de aviso 
**Então** o sistema deve exibir a mensagem "Usuário removido." **E** o e-mail do usuário não deve mais aparecer na listagem.
