# Fundamentos da Cultura DevOps - Alex Ferreira (Trilha DevOps do IA)
- dev (mudanças) x ops (estabilidade do sistema)
- Papel do ops: manter tudo estável, otimizar infraestrutura, melhorar e otimizar serviços.
- Ambos tem o objetivo de crescimento dos negócios.

## Definições
- DevOps tem várias definições: abordagem para preencher essa lacuna, forma de entregar software com dores e responsabilidades compartilhadas, uma metodologia que utiliza comunicação para integrar desenvolvedores e infraestrutura de TI.
- Segundo o Alex: é a prática de op. e des. juntos durante o ciclo de vida do serviço, desde o design e desenvolvimento até o suporte a produção.
- DevOps é cultura, mais do que um cargo em sí.
- É uma questão de confiança mais do que ferramentas ou processos (Patrick Debois).
- Princípios da cultura DevOps: Cultura, Automação, Medição e Compartilhamento (Sharing)
- Cultura: Pessoas > Processos > Ferramentas
- Relacionamentos e comunicação orgânicos e flúidos.
- O que pode ser automatizado: builds, deploys, testes, monitoramento, configurações, etc.
- Monitorar o que for possível: métricas compatíveis com o negócio, (capture, aprenda e melhore), métricas disponíveis para todos - elas facilitam o planejamento, análise de tendências, resolução de problemas.
- Uma das bases do DevOps é o manifesto ágil
- Outra base é o Lean: eliminar desperdício, amplificar aprendizado, decidir o mais tarde e o mais rápido possível, dar poderes ao time, construir integridade, visão do todo.

## O que não é
- DevOps não é? Não envolve apenas devs e admin de sistemas.
- Não é um cargo ou time, ou fazer todo o trabalho com metade das pessoas (dada a automação).
- Não exite um jeito certo ou errado de ser fazer DevOps, cada contexto é único.
- DevOps não é somente sobre automação e ferramentas, não é também somente "modinha" passageira.
- DevOps não é relevante apenas para startups e não há um prazo X ou Y para ser implatando em uma empresa (já que é uma cultura).
- Benefícios do DevOps: integração entre áreas, simplificação de processos, automação de tarefas, racionalização de processos, modernização, estímulo a colaboração.

## Ciclo de Vida: o cinto do batman
- Todas as fases de um projeto: codificação, construção do build, testes, release, deploy, operação, monitoramento, planejamento e retorna.
- Imagem do ciclo de vida devops.
- Dá um mapa de key devops patterns and pratices.

## Ferramentas básicas
- Linux: maioria esmagadora do mercado, notadamente em produção;
- Python: muitas ferramentas escritas nisso, serve para script e backend.
- Go: outra possibilidade relevante, diversas ferramentas utilizam.
- Cloud computing: AWS é um player importante a ser considerado.
- Pontos a considerar: provisionamento de VM, redes privadas, controle de acesso e segurança, distribuição de arquivos, métricas, balanceamento de carga, containers.

## Ferramentas
-programável, verificável, estável (o básico para automação)

## Ferramentas para configuração
- Configuração manual: pontos negativos são que humanos erram, não versionado, não reprodutível facilmente. Exemplo: ambiente de Dev,QA, Produção
- Infraestrutura como código: representar a estrutura para provisionar serviços. O código é versionável, reprodutível e possivelmente não introduz erros.
- Algumas ferramentas: terraform, Ansible, talvez o Puppet.
- No Terraform, um yaml descreve a infraestrutura que o serviço roda em cima: nuvem, container e afins.
- A ideia do Ansible é semelhante, como se fosse um script que define o que tu quer dentro dos servidores. Fazer um set específico dentro de uma VM por exemplo.
- No exemplo de uma casa: o terraform seria a base, a estrutura da casa no Ansible e o teto seria a aplicação.

## Ferramentos para versionamento e empacotamento
- Git
- Empacotar implica numa forma de manter em produção;
- Influenciado por servidores da aplicação, ideal se houvesse padronização.
- Docker: os containers são fechados. Na base está a infraestrutura, acima o sistema operacional host, o docker e acima os apps em containers.
- Quem se preocupa com o que tem dentro do container é o desenvolvedor
- Paradigma serveless: não há preocupação com a infraestrutura	

## Ferramentas de implantação e execução
- Deploy em produção é uma tarefa difícil
- Diferenças são o problema: ambiente, configuração, usuários
- Infraestrutura como código ajuda
- O processo de implantação deve ser versionado
- Jekins: rodar os testes, pipelines, CI/CD
- Kubernetes: executar containers, orquestração
- Amazon ECS: executar cotainers

# Ferramentas de monitoramento
- Métricas precisam ser coletadas
- Aplicações cada vez mais complexas e com infraestrutura complexa
- Ter um único ponto de monitoramento facilita a operação
- ELK, Prometheus

# Dúvidas e questões
- Recomendação de relatório global sobre DevOps
- Livro Manual DevOps


