## Desafio: Implementação de Práticas DevOps em um Ambiente Empresarial Fictício

### Diagnóstico Cultural
Foi possível fazer o diagnostico levando em consideração esses pontos:
- A empresa possui um projeto Sistema de Gestão de Vendas(que é LEGADO) e dentre seus 14 desenvolvedores, possui apenas 1 com conhecimento em Delphi, linguagem que esse projeto utiliza, logo, pensamentos que somente esse desenvolvedor trabalha nesse projeto, que nos indica uma redundância no time e a existência da Síndrome da Pessoa Herói dentro dessa empresa.
- A equipe de operações lida frequentemente com o problemas de escalabilidade e desempenho, logo, nos induz pensar que a empresa atua de forma reativa, com pouca ou talvez nenhuma manifestação de interesses em mitigar falhas que frequentemente acontecem.
- Tempo médio entre a entrega do código e o deploy é de 2 dias, um tempo significativamente alto e combinado com a informação de que, a equipe de operação realiza os testes, podemos supor que há uma falta de contexto da funcionalidade entrega, colaborando para a centralização do conhecimento.
- Os dados de desempenho nos mostram que a que a equipe de operação utiliza trabalho manual e que a taxa de sucesso é de apenas 80%, que justifica o tempo entrega da entrega até o deploy ser significativamente alto. Esses indícios mostram práticas que atrasam o processo da empresa.
- Os testes são realizados **em produção, após o deploy**, o que caracteriza uma prática inadequada e crítica. Além disso, o próprio processo de deploy já apresenta um tempo elevado, com média de dois dias entre a entrega do código e a disponibilização em produção. Dessa forma, mesmo quando o deploy é considerado bem-sucedido, eventuais erros são identificados **tardiamente**, já no ambiente produtivo, quando o impacto é maior. Caso um erro seja detectado, observa-se ainda um tempo médio de recuperação (MTTR) de 4 horas, indicando demora significativa na correção. Após essa correção, presume-se a necessidade de um novo deploy, o que novamente incorre no mesmo tempo médio de dois dias. Esse ciclo evidencia uma **combinação de más práticas e gargalos operacionais**, que mantém a equipe ocupada com tarefas repetitivas, manuais e corretivas, atrasando a entrega de valor e dificultando a melhoria contínua.

Com base no diagnóstico apresentado, é possível concluir que há uma **necessidade clara da implementação da cultura DevOps** na empresa.

### Automação (A de CALMS):
#### Proposta de solução de automação
Diante do diagnóstico cultural apresentado, a automação do **processo de deploy e testes** se mostra essencial para reduzir gargalos operacionais, minimizar falhas humanas e antecipar a detecção de erros no ciclo de desenvolvimento.

A solução proposta consiste na **implementação de um pipeline de Integração Contínua e Entrega Contínua (CI/CD)**, no qual:
- O código desenvolvido é integrado automaticamente a um repositório central.
- Testes automatizados (unitários e de integração) são executados **antes do deploy**.
- O deploy passa a ser realizado de forma automatizada e padronizada, reduzindo a dependência de processos manuais.
- Ambientes intermediários (como homologação ou staging) são utilizados para validação prévia, evitando testes diretos em produção.

Essa abordagem permite que erros sejam identificados **mais cedo no processo**, reduzindo o impacto em produção, o número de incidentes pós-deploy e o tempo médio de recuperação (MTTR).

#### Plano de implementação da automação e mitigação de resistências
1. Criação e padronização da documentação pós-desenvolvimento
	- Descrição do comportamento esperado
	- Fluxos principais e casos de erro
	- Dependências técnicas
	- Impactos em produção
	- Instruções básicas de validação

2. Padronização do processo de entrega
	- Definição clara das etapas: desenvolvimento → testes → deploy.
	- Alinhamento entre desenvolvimento e operações sobre responsabilidades.
	- Estabelecimento de critérios de aceite baseados na documentação criada.

3. Introdução progressiva da automação
	- Início da automação pelos **testes automatizados**, ainda fora do ambiente de produção.
	- Implementação gradual do deploy automatizado.
	- Manutenção temporária de validações manuais para aumentar a confiança no processo.

4. Capacitação e redução de resistências
	- Treinamentos básicos sobre CI/CD e testes automatizados.
	- Envolvimento da equipe de operações na definição do pipeline.
	- Comunicação clara de que a automação **apoia** o trabalho humano, em vez de substituí-lo.

5. Monitoramento e melhoria contínua
	- Acompanhamento de métricas (tempo de deploy, falhas, MTTR).
	- Ajustes progressivos no pipeline.
	- Remoção gradual de etapas manuais conforme a maturidade aumenta.

A automação do processo de deploy e testes, por meio da adoção de pipelines de CI/CD, é fundamental para antecipar a detecção de erros, reduzir falhas humanas e eliminar gargalos operacionais. 

### Mensuração e Compartilhamento de Conhecimento (M e S de CALMS)

#### Métricas para avaliar o impacto da automação (Measurement)
Para avaliar a efetividade da automação do processo de deploy e testes, devem ser adotadas métricas que reflitam **eficiência, qualidade e confiabilidade** do processo. As principais métricas propostas são:

- **Lead Time de Deploy**  
    Mede o tempo entre a entrega do código e o deploy em produção.  
    _Objetivo:_ reduzir o tempo médio atual de 2 dias.
    
- **Taxa de sucesso dos deploys**  
    Percentual de deploys realizados sem necessidade de rollback ou correção imediata.  
    _Objetivo:_ aumentar a taxa atual de 80%.
    
- **Número de incidentes pós-deploy**  
    Quantidade de falhas detectadas após a disponibilização em produção.  
    _Objetivo:_ reduzir a média atual de 2 incidentes por semana.
    
- **MTTR (Mean Time To Recovery)**  
    Tempo médio necessário para recuperar o sistema após um incidente.  
    _Objetivo:_ reduzir o MTTR atual de 4 horas.
    
- **Cobertura de testes automatizados**  
    Percentual de funcionalidades cobertas por testes automatizados.  
    _Objetivo:_ garantir que erros sejam detectados antes do deploy em produção.

#### Plano de compartilhamento de conhecimento e cultura colaborativa (Sharing)
Para garantir que as melhorias implementadas sejam sustentáveis, é fundamental promover o **compartilhamento de conhecimento** e o aprendizado contínuo entre as equipes.

1. Centralização e acesso à documentação
	- Manter a documentação técnica e funcional em um repositório acessível a todos.
	- Atualizar a documentação sempre que novas funcionalidades ou mudanças forem implementadas.
	- Utilizar a documentação como referência oficial para testes, deploys e manutenção.

2. Disseminação do conhecimento sobre o pipeline
	- Documentar o funcionamento do pipeline de CI/CD.
	- Garantir que tanto desenvolvimento quanto operações compreendam todas as etapas do processo automatizado.
	- Reduzir dependência de indivíduos específicos.

3. Práticas de aprendizado contínuo
	- Realizar reuniões periódicas de retrospectiva para discutir incidentes, falhas e melhorias.
	- Compartilhar lições aprendidas a partir de falhas, adotando uma abordagem sem culpabilização.
	- Incentivar a troca de experiências entre as equipes.

4. Fortalecimento da colaboração entre Dev e Ops
	- Promover a responsabilidade compartilhada pelo ciclo de vida do software.
	- Envolver ambas as equipes no acompanhamento das métricas.
	- Estimular uma cultura de melhoria contínua baseada em dados.

### Três Maneiras
 1. Primeira Maneira (Acelerar o Fluxo):
	Oportunidades identificadas:
	- Deploy manual e não padronizado.
	- Testes realizados apenas após o deploy em produção.
	- Alto tempo médio entre entrega do código e deploy (2 dias).
	- Retrabalho frequente devido a falhas pós-deploy.
	
	Ações propostas:
	-  Automatização do processo de deploy por meio de pipelines de CI/CD.
	- Execução de testes automatizados antes da liberação em produção.
	- Introdução de ambientes intermediários para validação.
	- Padronização do fluxo de entrega, reduzindo variações e dependência de ações manuais.

  2. Segunda Maneira (Ampliar Feedback)
	  Mecanismos de feedback propostos:
	 - Feedback automático dos testes durante o pipeline de CI/CD.
	 - Monitoramento contínuo dos sistemas após o deploy.
	 - Análise periódica de métricas como taxa de falhas, incidentes e MTTR.
	 - Compartilhamento dos resultados das métricas entre desenvolvimento e operações.

3. Terceira Maneira (Experimentar e Aprender):
	Práticas propostas:
	- Implementação gradual das automações, começando por projetos menos críticos.
	- Realização de retrospectivas periódicas para análise de falhas e incidentes.
	- Adoção de uma cultura de post-mortem sem culpabilização.
	- Estímulo à troca de conhecimento entre as equipes.

De forma integrada, a aplicação dos princípios do CALMS e das Três Maneiras do DevOps permite que a empresa evolua de um modelo manual, reativo e fragmentado para um fluxo contínuo, colaborativo e orientado à melhoria contínua. Essa transformação não apenas reduz falhas e gargalos operacionais, como também promove maior previsibilidade, qualidade e entrega de valor ao cliente.