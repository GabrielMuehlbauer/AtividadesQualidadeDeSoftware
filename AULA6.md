# Análise de Riscos

Nós sabemos que é necessário
- Entendimento dos Requesitos
- Planejamento de testes
- Ambiente de testes
- Testes de unidade
- Testes de integração
- Testes funcionais
- Testes de segurança
- Testes de desempenho
- Testes de usabilidade
- Testes de regressão
- Relatórios e acompanhamento

## Risco

Risco não é certeza é probabilidade + severidade

Matriz de Risco: Probabilidade x Impacto/Severidade

Estratégia de Mitigação: O que fazer para corrigir. 

Nem todo risco é um bug.

Risco Técnico: API Lenta
Risco de Negócio: Perda financeira
Risco Operacional: Backup falhou
Risco Humano: Erro de deploy

*Não existe risco zero, mas reduzir a probabilidade ou impacto.*

# Respostas do Exercício de Riscos

### Cenário 1: Interrupção Temporária do Serviço devido a Manutenção Programada

- **Probabilidade:** E (Justificativa: Como é uma manutenção programada, a interrupção do serviço é um evento planejado e certo de ocorrer ).
- **Impacto:** 2 (Justificativa: A acessibilidade é afetada temporariamente, porém o cenário deixa claro que ocorre sem danos permanentes aos dados ou ao sistema ).
- **Matriz do Risco:** E2 - Médio
- **Testes utilizados:** Teste funcional e Automação (para testes de Regressão)
- **Estratégia de mitigação:** Executar a manutenção programada em horários de menor tráfego de usuários. Enviar comunicados prévios aos clientes sobre a janela de inatividade para gerenciar expectativas e reduzir chamados de suporte. Validar o sistema pós-manutenção com testes de regressão automatizados para garantir a integridade das funções.
- **Tipos de Risco:** Operacional: O processo da janela de manutenção pode sofrer desvios, como um backup preventivo que falhou antes do início da atualização. Humano: A equipe técnica pode cometer algum deslize durante o procedimento, como um erro de deploy que prolongue a interrupção. Técnico: A manutenção pode gerar efeitos colaterais no sistema ao retornar, como deixar uma API lenta ou causar indisponibilidade em outros serviços integrados. Negócio: O tempo de interrupção pode se converter em perda financeira temporária, já que os clientes estarão impossibilitados de usar o serviço no período.

### Cenário 2: Vulnerabilidade de Segurança Descoberta em uma Dependência de Terceiros

- **Probabilidade:** C (Justificativa: Como a biblioteca é de terceiros, você não tem controle sobre o código fonte dela, tornando possível que vulnerabilidades existam ou sejam descobertas ao longo do tempo).
- **Impacto:** 5 (Justificativa: O texto menciona explicitamente que é uma vulnerabilidade "crítica" e que permite o acesso a "dados sensíveis" , o que representa o grau máximo de impacto na matriz ).
- **Matriz do Risco:** C5 - Muito Alto
- **Testes utilizados:** Teste de Segurança (como o Pentest) e Teste de Integração  (para validar se a aplicação continua funcionando após a atualização ou remoção da biblioteca).
- **Estratégia de mitigação:** Realizar a atualização imediata da biblioteca para uma versão que contenha o patch (correção) de segurança. Caso não exista correção disponível, avaliar a substituição da biblioteca por uma alternativa segura ou isolar/desativar a funcionalidade temporariamente. Implementar práticas de desenvolvimento seguro, como testes de segurança regulares automatizados (ferramentas de varredura de dependências) para detectar esses problemas precocemente.
- **Tipos de Risco:** Técnico: Falha arquitetural ou falha de código presente dentro da biblioteca externa, que compromete a barreira de segurança da sua aplicação. Operacional: O vazamento das informações sensíveis dos clientes, o que pode interromper a operação normal enquanto a equipe de resposta a incidentes atua. Negócio: Risco altíssimo de perda financeira , processos judiciais, multas governamentais (como as da LGPD) e danos irreparáveis à reputação e credibilidade da instituição financeira.

### Cenário 3: Erro de Interface do Usuário que Causa Confusão entre os Usuários

- **Probabilidade:** C (Justificativa: Alterações de design e fluxos de tela frequentemente causam algum grau de estranheza inicial. Se a mudança for feita sem uma pesquisa prévia robusta, é bem possível que gere confusão).
- **Impacto:** 3 (Justificativa: Embora a experiência do cliente seja prejudicada, o cenário destaca explicitamente que o erro "não afeta a funcionalidade básica do aplicativo").
- **Matriz do Risco:** C3 - Médio
- **Testes utilizados:** Teste de usabilidade  (para avaliar como usuários reais interagem com a nova tela) e Teste funcional  (para garantir que, mesmo confusos, os botões e formulários executam o que deveriam).
- **Estratégia de mitigação:** Validar qualquer grande alteração de design através de testes de usabilidade (como testes A/B ou lançamento para um grupo pequeno de usuários beta) antes de liberar para todo o público. Adicionar tooltips (dicas visuais na tela) ou um breve tutorial de "Veja o que mudou" no primeiro acesso após a atualização, ajudando a guiar o usuário na nova interface.
- **Tipos de Risco:** Humano: O usuário interpreta incorretamente as mensagens, os novos botões ou os fluxos de navegação devido à interface confusa. Operacional: Como mencionado nos slides, "uma interface confusa pode gerar milhares de chamados", o que sobrecarrega a equipe de suporte e atendimento ao cliente da instituição financeira. Técnico: Implementação de componentes visuais sem a aplicação de boas práticas de UX/UI ou ausência de padronização visual clara. Negócio: A frustração contínua dos clientes pode gerar reclamações públicas (como nas lojas de aplicativos) e reduzir a conversão de uso das funcionalidades do aplicativo.

### Cenário 4: Falha em Processo de Backup de Dados

- **Probabilidade:** C (Justificativa: Em uma instituição financeira, espera-se que a infraestrutura seja robusta, tornando esse evento menos frequente, porém falhas sistêmicas são sempre possíveis de ocorrer no ciclo de vida de um software).
- **Impacto:** 5 (Justificativa: A perda "significativa de dados" bancários de usuários é catastrófica, impedindo o funcionamento das operações básicas e destruindo a confiança no negócio).
- **Matriz do Risco:** C5 - Muito Alto
- **Testes utilizados:** Teste operacional (para validar a execução da rotina de cópia) e Teste de recuperação/restauração (para garantir que os arquivos de backup gerados não estão corrompidos e podem ser restaurados a tempo).
- **Estratégia de mitigação:** Implementar alertas e monitoramento em tempo real para as rotinas de backup. Aplicar políticas de redundância de dados (como manter cópias em servidores físicos e isoladas em nuvem) e agendar testes periódicos de restauração para atestar a eficácia e a agilidade do processo.
- **Tipos de Risco:** Operacional: A rotina diária ou o procedimento de salvaguarda não foi executado corretamente, caracterizando uma falha direta de operação (como o exemplo "Backup falhou" citado no material). Negócio: A perda de dados resulta em perda financeira maciça, possíveis processos judiciais e multas de órgãos reguladores. Técnico: A falha pode ter origem em um problema físico de hardware ou em um erro no script automatizado de cópia. Humano: Um profissional da equipe de infraestrutura pode ter configurado a rotina incorretamente ou excluído o volume de destino por acidente.