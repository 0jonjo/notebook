# Dragon Rentals

## 07/07/2021

- O foco da semana será entender o que é open-source
- Revolucionary OS - filme sobre Linux
- Ver os vídeos, quando terminar dar um like

## 14/07/2021

- Ruby prefere snake_case
- Ela é duck typing
- As classes em Ruby tem o to_s
- Tarefa: clonar o código, criar um branch, mandar o branch com seu nome no método hi e mandar o pull request e deletar a branch.

# 21/07/2021

- git fetch --all --prune específico de manhã
- vendo todo o processo do git
- commits que efetivamente fala o que está fazendo
- git push origin <branch criada>

# 28/07/2021

- Pensar no usuário, na visão dele, tentar prever o funcionamento
- É um erro de design ter um programa que permite o usuário "fazer cagada"
- A aplicação tem que ser pensada no usuário
- Indicação: Incrivelmente simples, ebook na Amazon
Guessing Game do Marcelo
- Usa espaçamento no puts para deixar as informações visualmente melhor 
- O /n representa o Enter, o chomp no gets.chomp ele remove o Enter
- Uso do puts e prints de forma estratégica
- loop do - executa infinito
- atenção ao rand, rand(10) não inclui o próprio 10
- numero_secreto if numero_secreto.zero?
- em Ruby, a legibilidade do código é essencial 
- 99 Bottles of Ruby, livro, indicação, Sandy Mets
https://sandimetz.com/99bottles-sample-ruby
- Os commits precisam ser mais descritivos
- Vamos utilizar o livro "Conhecendo Ruby" até a página 144 neste curso
- Próxima semana terá um convidado que mudou de área depois dos 40 anos.
- Tarefa da semana: criar em grupo uma calculadora
1. Escrever o código em modo Ruby efetivamente  - "pesquisar isso na net:"
2. Tem que ser grupo efetivamente, commits de pessoas diferentes
3. Dê atenção ao usuário, a avaliação será uma criança de 9 anos.
4. Tentar mandar até segunda a noite.

# 11/08/2021

-rubygems.org - o tesouro da linguagem
- bundler trabalha com o rubygems - relacioado ao Gemfile
- https://www.rubydoc.info/gems/cpf_cnpj/0.5.0 
- bundle exec ruby cpf.rb
- Hashs e arrays
puts array.empty? 
array.include? 'Paulo'
array.inspect ["Impressão da estrutura com dados relevantes]"
array << 'Marcelo' 
array.push 100
array.insert(0, "Teste) // Coloca algo no começo do array, posição zero
array.delete_at(2) // Apaga na posição 2
array.delete(100)
- https://ruby-doc.org/core-3.0.2/Array.html
- ATIVIDADE
Criar uma agenda com diversas possibilidades de uso, conforme está no Slack
Dois grupos de 9

# 18/08/2021
- a importância de aprender a dividir tarefas, organização de empresas
- perguntar, aprender as regras do negócio
- Sinatra, framework
- Duas atividades:
1. Grupo: Modificar a agenda para conversar com o banco de dados, sqlite. 
2. Individual: fazer Hello World! usando o sinatra. Fazer o P fazer Hello World! usando o sinatra. Fazer o PR.
- Palestra João (Campus Code) 
1. Saber resolver problemas (não só código pequeno, mas legível)
2. Ter controle, saber a lógica (saber o que cada coisa faz)
3. Entender a dinâmica das empresas, as estruturas dos times de desenvolvimento
4. O foco é resolver problemas
5. Desenvolver habilidades de comunicação (não-violenta, escrita, oral, etc.)
6. Saber explicar/saber responder sobre o que você faz e precisa
7. Pesquisar sobre processos de onboarding
https://about.gitlab.com/handbook/people-group/general-onboarding/
8. Tentar achar equilíbrio entre lugar que acolha e te desafie (o segundo é a prioridade para quem ta começando)

# 23/08/2021
- Atenção ao uso do git add --all na hora de enviar os commits
- loop do e break (para sair), uso interessante
- O padrão ruby é mesmo dois espaços
- lista_compras.each do |item|
puts 'Item: #{item}'
end
Forma interessante de exibir a lista
- lista_compras.delete(item), simplificou o deletar
- Por um puts '' no fim para ficar mais fácil ler a lista
- Usar o sort para deixar a lista em ordem alfabética
- git status para ver o que foi modificado

# 25/08/2021
- Tabela com comandos SQL: https://pbs.twimg.com/media/E7h1FevWYAQx2zo.jpg
- O Rails tem gems especificas para lidar com banco de dados e afins
- Atenção as camadas entre o backend e o banco de dados: ActiveRecord, ORM, driver (na última aula foi o a gem do SQLite)
- Da para configuar o rails já na criação: no rails new
- Dica de comando útil: git reset -hard HEAD
ATIVIDADES
- Rodar, fuçar no rails criado na aula
- Ler o material de referência. 

# 01/09/2021
- Deixar o projeto do blog pessoal público no Github
- Próxima semana começar atividades individuais no board da DragonRentals
- Terminar tutorial blog do grupo3

# 08/09/2021
- Projeto DragonRentals usa divise para e-mail e senha do usuário e simple_form (confirmar isso)
- Ler as documentações dessas gems, muito usadas
- Só os usuários logados podem criar posts 
- Temos que resolver as imperfeições do sistema
- Sprints semanais e daily nos grupos
- O yield no layout é onde será renderizado efetivameente quem usar o layout
- todo layout que começa com _ é uma partial
- A dica da "batata" para exibir rotas em Rails quando precisar
- No PR marcar alguém de fora do grupo
- Usar o rails test

# 15/09/2021
- Quem abre o PR, faz o merge
- Sempre esperar os 2 codereviewers para dar merge
- Usar a nova coluna do board: review
- Bootstrap, bootrails (fazer o tutorial, criar um to-do ou outro projeto)
- Por no seu github pessoal como portfólio

# 29/09/2021
- Uso da ferramenta de bug do rails clicando no canto da tela.
- Usou o byebug no controller index, a partir da ativação vocÊ trabalha no console, lembrar de usar o save! no fim.
- Serve para debugar, mas também fazer código
- params guarda os parametros utilizados na requisição
- Nunca mandar um byebug para produção sem querer
- Realizar as tarefas de tradução (na página) e adicionar o bootstrap (esperar fazer no projeto como um todo antes das partes específicas)

# 06/09/2021
- Rebase, auxiliar em parte do projeto a partir de 8 novembro, usará TDD
- Pegar parte da turma para entrar como JR na rebase, 90 dias sem pressão.
- Em paralelo até dezembro
- Rack: compilador de requisições, está entre o Puma e o Rails
- Devise importante, controla autenticações e permissionamento, é baseado no hack
- Atividade: criar uma aplicação rails com divise a partir de um tutorial
- O Wiki, get start do repositório no Github.
- Estratégia dos bancos: acesso a informações sigilosas por sessão (provar que você é você)
- Já autenticação por terceiros (Google, Facebook e afins) é OAuth (padrão de autenticação)
- O usuário pode ser uma pessoa (mas também um site, aplicativo de celular, etc.)
- O divise é bem complexo, tem vários módulos, a atividade da semana é se aprofundar nisso.

# 13/09/2021

- Sidekiq, gem de background job. Prawnpdf, gem para impressão e afins em pdf.
- Modules, encapsulamento.
- Os controllers do projeto Rails, são exemplos de módulos.
- Paginação: importante organizar na view. Gem Kaminari
- Exercício durante a aula: codando todos juntos fazendo a paginação usando o Kaminari na página Dragões.
- Ter preocupações do usuário, boa parte delas fora dos rails. Usar gems de terceiros.
- Processamento em background.
- Fazer aplicação rails, 3 grupos, usar sidekick (um worker que vai ser agendado para ser utilizado depois que for feito uma ação web.). Background job, processamento assíncrono.

# 20/10/2021
- Relatos da aula passada
- Backend com o aumento da complexidade se dividiu em especializações
- A infraestrutura fica a cargo de um profissional específico
- Devops é uma cultura, operações com desenvolvimento. Dev com mais acesso (controlado) a infraestrutura e afins
- SRE, engenharia de confiabilidade de sites
- Caminhos para por o site no ar: servidos físico (Digital Ocean, AWS, Azure, etc.) e Paas - Plataform as a service (AWS Cloudformation, Google GCP, Heroku) 
- Colocar projeto individual no ar usando o Heroku (ver documentação no dev center)

# 27/10/2021
- Heroku carrega no modo produção os arquivos uma vez só na memória, só muda se você subir novamente o arquivo.
- Usar heroku log (cliente local) para ver erros etc. Se tiver mais de uma aplicação dizer qual.
- Usar heroku rails db:migrate quando subir as aplicações.
- Deploy: empacotar máquina e mandar para um servidor.
- Heroku faz o meio de campo entre o código e o servido. Ele faz a avaliação das dependências (no caso do RoR, avalia o Gemfile.lock)
- O Blue Green Deployment (link da Redhat postado pelo Marcelo)
- Container: encapsulamento, mais leve e aproveita recursos da máquina
- OCL padroniza os sistemas de containers
- Próxima semana sem encontro presencial: continuar a colocar uma aplicação heroku no ar.
- Atuação do João da CampusCode no projeto em novembro

# 10/11/2021
- João, fundador da CampusCode, que usam Ruby on Rails
- Chama o curso do Marcelo de mentoria
- Fazer o mês final como os treinamentos da casa: projeto, currículo, feedback
- TDD, desenvolvimento orientado a testes, suma importância para a comunidade Rails
- Fluxo de testes em Rails, dando dicas, etc.
- TDD é um comportamento
- Pedir uma leitura de TDD para o João
- Escrever um conjunto mínimo de testes como Júnior.
- Exemplo: usuário logado criar algo, fazer dois testes, um para logado ou um sem ser
- Fazendo o projeto novo, o padrão do teste é o minitest, a comunidade usa mais o rspec
- Deu um bin/setup para testar
- Livro do Mauricio Anish, livro sobre TDD (ver depois)
- Usando a gem rspec-rails (teste unitário). Permite testar tudo no programa.
- Pode criar pastas dentro do spec
- Vamos começar com system
- Exemplo: visitando_visita_homepage_spec.rb (geralmente se escreve tudo em inglês)
- Inicializa rails_helper.rb no começo
- No teste em si continua a frase "e visita a welcome message"
- TDD com baby steps, ajuda a se localizar e compreender a situação.
- Roda o rspec o tempo todo para entender melhor.
- Tudo que você cria no banco de dados em um teste acaba automaticamente. A não ser que você defina que persista.
- Test Driven Rails, escrever o teste figindo que é o usuário usando o capybara
- Capybara testes como usuário navegando pela aplicação

# 17/11/2021
- Vai fazer o TDD de um formulário.
- João vai revisar o projeto e dar feedback.
- Mandar o link do github quando começar, por e-mail
- Foca em fazer funcionalidade (um fluxo que funcione)
- Tente escrever o máximo de testes que conseguir (quase tudo pode ser testado com o capybara)
- Dá para fazer um por linha.
- Fazer até o item 10 para ter o feedback.
- Fazer um organograma (usar o quadro do Github)
- Focar no código nesse momento (usar SQLite3)
- Ir atualizando o README constantemente
- Recomenda usar o Bootstrap
- Telas difíceis: por  destaque (por em algum canto isso), comentário no perfil e enviar proposta.
- Code_saga, ver uma trilha de desafios de testes (não pode subir no Github depois)
- Mandar email no chat do slack
-  Técnicas dos 3 As (Arrange - preparar, Act - agir/interagir, Assert - validar)
- Vale comentar os testes com os As, mais fáceis os 2
- Ver a página do CampusCode sobre capybara
- Cada teste, testa apenas uma coisa.
- Os testes se complementam
- Usar esse projeto de estudo como modelo para a atividade
- Rascunhar é relevante
- Sair sempre do root_path para fazer os testes e implantar funcionalidade
- O capybara não testa se você salvou, ele funciona como um navegador.
- Dica: não deixar rotas soltas, sem uso
- Toda rota GET o Rails procura por uma View
- Usar o TDD em um projeto antigo para aprender a testar

# 01/12/21
- Gems de teste indicadas SimpleCov e Shoulda Matchers 
- Fazer entrevista, mandar mensagem para o João 
- 3As: Arrange, Act, Assert
- Um negócio interessante, quando logar aparecer o email do usuário logado.
- Sumir o botão login e fica o logout
- Os nomes de Classe são considerados constantes em ruby
- ver as flash messages do devise para por no layout do projeto.
- Usar a </nav> na hora de fazer o Menu na root_path
- Passou o menu para o layout da app, no body
- Usar path na aplicação e URL (endereço completo) para fora. Exemplo: um email.- Não deixar rotas expostas, performance e segurança em jogo
- Gerar views do devise para poder editar
- Usou a tag span para por o email na tela 
- Interessante esses testes de não achar tal coisa, reforça as coisas bem.
- before_action é um filter
- É obrigatório fazer o teste do usuário deslogado tentando entrar em tela em questão. 
- Como fazer um teste passar justamente porque queriamos que ele tivesse falha
-  Teste de Capybara são caros (usa mais tempo para testar)
- Vai nos rails helper e coloca a linha do Devise com Capybara, para pegar os testes dele e simplificar
- A linha do login_as tem que vir antes do visit root_path
- Joao Almeida não usa before each, prefere testes auto contidos.
- Quando dois links iguais se repetem numa tela, é problema nos testes.
- Uma saída é pegar ou criar uma id para os botões e identifica-los.
 id: "login_button"
- Ou usar o within: within("form") do click_on "Login"
- Isso é um css selector, pode pesquisar no w3 sobre isso
- Usa before_action nos controller pode passar métodos escritos no próprio controller ou no maior que é o application_controller.rb
- SimpleCov dá o percentual de cobertura em cada parte
- Usar validates nos models e aprender sobre testes unitários
- ShouldaMatches ele ajuda nos testes unitários de belongs_to e afins
- O feedback do projeto final tem que ser pedido
- Fazer o CodeSaga depois.                   

# Trabalho final
- Para continuar o tutorial necessário mexer no Devise para criar o model User
- Ver como escrever user_id e job_id como parâmetros permitidos no controller Applies 
- Model JobOffer belongs_to :jobs belongs_to :user belongs_to :headhunter headhuntercomment:text useraccept:boolean userreturn:text   
