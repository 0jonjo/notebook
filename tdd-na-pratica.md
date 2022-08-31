# TreinaDev 8

# Ruby on Rails - Uma Abordagem prática com TDD

# Protocolo HTTP
Boa documentação: https://developer.mozilla.org/pt-BR/docs/Web/HTTP/Overview

# MVC
- https://developer.mozilla.org/en-US/docs/Glossary/MVC
- A view não é o próprio html final, ela produz esse html que será apresentado como resposta.
- O routes está no começo do processo, verifica se há rota para a requisição.
- Um exemplo de escrita das rotas:
get '/pedido', to: 'nome_do_controller#nome_da_action'
- Se action é vazia o Rails procurando automaticamente uma view com o mesmo nome.
- Na view:
Tag que não imprime: <% %>
Tag que imprime: <%= %>
- É necessário um @ na action (controller) para que ela esteja disponível na view. Exemplo: @pratos.each do 

# Testes
- http://www.extremeprogramming.org/rules/testfirst.html

# Sistema de controle de estoques
- Faz parte de um E-commerce com outro sistemas: pagamento, frete, etc.
- Galpões de estoque, fornecedores, pedidos que escolhe fornecedor, modelo, quantidade.
- Escolhe para qual galpão o pedido vai. 
- O sistema terá comunicação com outros, enviando e recebendo dados.
- Telas com imagens e listagens de itens dos galpões, pedidos (cada um com seu código), etc.

# Tela inicial
- Utiliza capybara e rspec
- Testes de aceitação ou sistema: simular a experência do usuário.
- Tripo A: Arrange (preparar), act (agir), assert (garantir) 
- https://github.com/rspec/rspec-rails
- Importante configuração no rack_test no rails_helper
config.before(type: :system) do
    driven_by(:rack_test)
  end

# Listar Galpões
- Ver os galões cadastrados.
- Nome, código (3 caracteres, 1 galpão por cidade), metragem e cidade.
- rails generate model cria o teste unitário automaticamente.
- schema.rb é um "retrato" atual do seu banco de dados.
- A view aceita escritas como
<% @warehouses.each do |warehouse| %>
    Name: <%= warehouse.name %>
<% end %>
- Lembrar de sempre fazer pelo menos dois testes: a situação que passa e a que não passa. A que há tal coisa e a que não há.

# Ver detalhes de um galpão
- Links:
https://guiarails.com.br/getting_started.html#mvc-e-voce-gerando-um-model
https://api.rubyonrails.org/classes/ActionView/Helpers/UrlHelper.html#method-i-link_to
- O usuário poder ver informações a mais sobre os galpões: endereço, descrição e CEP.
- Warehouse.create é o mesmo que fazer um .new e depois .save
- Alterando o banco a partir de uma migration:
rails g migration add_AQUI_QUALQUER_COISA_to_warehouse adress:string cep:string description:string
- Limitando rotas do CRUD:
resources :warehouses, only: [:show]
- Criar um link no index fazendo show de outro Model pegando o id do objeto
<%= link_to(warehouse.name, warehouse_path(warehouse.id)) %> 
- Lembrar que o controller é no plural: warehouses_controller.rb 
Caso contrário acontecem erros variados

# Melhorias no HTML e métodos de Models
- Inspeciona e vai em network, ver os caminhos relativos acionados.
- O layout application emoldura as outras views criadas. Lá ficam os metadados.
- Utiliza seções para organizar o conteúdo da página
- https://developer.mozilla.org/pt-BR/docs/Glossary/Semantics
- https://developer.mozilla.org/pt-BR/docs/Web/HTML

# Introdução a formulários
- Link indicado: https://developer.mozilla.org/pt-BR/docs/Learn/Forms/Your_first_form
- Tag <form> do html com diversos <input/>, há o disparo de uma requisição POST.
- A form é um agregador de tags input.
<form method="" action="">
- Importante ter a label informando o usuário o que ele tem que preencher em cada campo
<label for="linguagem">Linguagem</label>
<input type="text" name="linguagem" id="linguagem"/>
- O input garante o foco para o campo certo quando clicar em Linguagem.

# Cadastrando galpões 
- Link indicado: https://guiarails.com.br/form_helpers.html#trabalhando-com-objetos-model
- Formulário tem duas rotas, um get de declaração de intensão para ser preenchida (o formulário). A seguinda requesição http é um post, que joga o preenchido para o banco.
- Usar a seção API no site do Rails para opções mais complexas.
- Guia para o create no controler
1. Receber os dados enviados
2. Criar um novo galpão no bancos de dados
3. Redirecionar para a tela inicial ou outro lugar.
- Só as rotas get tem um html
- Atenção para como usar fazer o cabeçalho do form.

# Exibindo mensagens de sucesso
- Link sugeridos:
https://developer.mozilla.org/pt-BR/docs/Glossary/Idempotent
https://guiarails.com.br/action_controller_overview.html#sessao
https://guiarails.com.br/action_controller_overview.html#o-flash
- Coloca o aviso flash na action especifica do controller e também no application.html.erb, acima do yield.

# Validações
https://guiarails.com.br/active_record_validations.html
- Estrutura de validação via model
validates atributos, tipo_de_validacao: true
- Para ver se um objeto é válido no rails console: w.valid? 
- Ver quais os erros: w.erros. Se te atualizar tem que rodar novamente o valid? acima.
- O save, create, update só funciona se o validate? for true
- No model lembrar de por no new
def new
 @warehouse = Warehouse.new
end
Isso facilita o uso do form no new e edit, além de outros aspectos.
- Usar o flash.now para que o aviso de Galpão não cadastrado não passe para a prpróxima página carregada indevidamente. Isso ocorreria por conta do render :new não carregar uma nova requisição.

# Testes unitários
- Links indicados:
https://github.com/rspec/rspec-expectations
https://www.betterspecs.org/#describe
https://guides.rubyonrails.org/active_record_validations.html#uniqueness
- Verificam um único ponto do código
- Em linguagens orientadas a objeto, um método público é alvo de testes unitarios. 
- Da para testar isoladamente uma view, action, controller, etc. no Rails
- Conforme Test Driven Rails: os principais testes de uma aplicação devem levar em conta a percepção do usuário final. 
- Testes unitários ajudam a cobrir 100% do código sem prejudicar a performance.
- No teste unitário pensando em performance, não precisa salvar no banco de dados. Dai usar o new sem fazer o save no fim (também não usar o create, que é a junção dos dois).
- Para testar usando uniqueness dá para usar create no primeiro objeto (para estar no banco), new no segundo (para apenas testar se ele pode ser salvo).
- expect(warehouse).not_to be_valid (uma estratégia que ele pega o que vem depois do be e utiliza o método). Isso encurta o teste e deixa legível.

# Internacionalização i18n
- https://guides.rubyonrails.org/i18n.html
- https://github.com/svenfuchs/rails-i18n
- Permite escrever em várias línguas, pode incluir regras de localização (i10n): formato de datas, moedas, etc.
- A pasta initializers é onde o rails organiza para iniciar cada componente, evitar mexer lá sem um bom motivo.
- Qualquer coisa criada lá é iniciada junto do server, etc. Por isso jogar o locale.rb lá.
- m.erros.full_messages (para obter respostas mais amigáveis dos erros)
- gem rails-i18n, retirar de lá o arquivo só pt-BR

# Editar um galpão
- Nos testes em que for criar um objeto, usar create! (ele vai retornar o erro ao invés de simplesmente não salvar).
- Isso dá certeza que o objeto foi criado
- Atenção para ter sempre a id do objeto e fazer o método update especificando as mensagens flash corretamente, o flash.now quando apenas renderiza a página.

# Removendo repetições
https://guides.rubyonrails.org/action_controller_overview.html#filters
https://guides.rubyonrails.org/layouts_and_rendering.html#using-partials
- Uma estratégia é criar métodos privados para criar set_warehouse e em params.
- Assim eles não são acessáveis fora.
- Usa o before_action e only:[] para restringir que vai usar o set_warehouse.
- declarar método vazio com uma linha só: def show; end 

# Removendo galpões
https://guides.rubyonrails.org/active_record_basics.html#delete
https://api.rubyonrails.org/classes/ActionView/Helpers/UrlHelper.html#method-i-button_to
- o http pertmite que uma mesma rota tenha comportamentos diferentes de acordo com o verbo. È o caso das rotas get, patch, put, delete de um model
- Rails respeita o REST. 
- Uma boa prática: um GET deve ocorrer sem nenhum efeito colateral dentro da aplicação.
- Usamos o método destroy porque ele apaga dependências que tenham com aquele objeto, delete não apagaria.
- Sempre dá para pensar dois cenários de testes.

# CRUD Fornecedores
https://developer.mozilla.org/pt-BR/docs/Web/HTML/Element/nav
https://www.rubyguides.com/2019/05/rails-link_to-method/
- Fazer o CRUD completo de suppliers.
- separar os testes em pastas para organiza-los.
- Ver itens dos fornecedores para criar o model.
- Colocou o link para Fornecedores, colocou no application.html.erb, numa <nav> no header.
- Usou tabela para organizar a index dos suppliers.
- Nela o loop é sempre no corpo.
- É incomum ter o delete (destroy) em bancos de dados, é preferencial desativar o uso sem deletar um Forneceador, etc.

# Associações: belongs_to
https://guiarails.com.br/association_basics.html
https://guides.rubyonrails.org/active_record_migrations.html#references
- Associação conecta tabelas diferentes dentro do banco de dados através do id.
- Duas associações (métodos)  entre models no Rails: belongs_to (pertence a) e has_many 
- Um tipo especial de dados usado nas migrations, o references
- Model sempre é no singular, mas controller no plural
- Nos testes, terá que criar também um objeto do model associado. No exemplo: suppliers e product_models
- Na hora de criar models com peso, altura, largura, etc., escolher uma unidade de medida que evite decimais.
- rails g model product_model name:string weight:integer width:integer height:integer depth:integer sku:string supplier:references

# Formulários com associações
https://guides.rubyonrails.org/form_helpers.html#making-select-boxes-with-ease
https://api.rubyonrails.org/classes/ActionView/Helpers/FormOptionsHelper.html#method-i-collection_select
- não é prático respetir verificações já feitas em testes anteriores.
- select: cria uma lsita de opções (um valor e um texto para o usuário) 
- o mais comum na pasta locales é criar um arquivo para cada model 
- usa o collection_select helper: 3 atributos
  <div>
    <%= form.label :supplier_id %><br>
    <%= form.collection_select :supplier_id, @suppliers, :id, :brand_name %>
  </div>
- def new
    @suppliers = Supplier.all (usar isso no controller do Product Models para melhorar o formulário)

# Validação em formulários com select
- Evitar o formulário select com apenas uma opção. Criar uma segunda no teste para ver se efetivamente está dando select
- select first_supplier.brand_name, from: 'Supplier' (outro modo de escrever o mesmo no teste)
- Se já há testes unitários de valiação de campo em branco, não precisa fazer um para cada campo de sistema (isso deixaria pesado, basta um geral).
- Com o select da um erro quando se testa não preencher corretamente os validates do formulário.
- Para resolver esse problema, declarar o item do select também no create. No caso:
      else
        @suppliers = Supplier.all
        flash.now[:notice] = "Error: Product Model not registered." 
        render :new 
Apenas dentro do else para economizar recursos.

# Projeto logística e-commerces
- Diversas transportadoras cadastradas, preços e prazos variáveis.
- Opera a partir de ordem de serviços em que a entrega é rastreável através do seu código
- Oreços configuráveis de acordo com distância e dimensões da carga. Prazos também de acordo com a distância
- Administradores e usuários comuns. Os adm consultam orçamentos e emitem ordens de serviço para as transportadoras
- Possivelmente usar bootstrap, ideias de gems: kaminari, devise, talvez alguma de cnpj.

# Autenticação com Devise 
- https://developer.mozilla.org/pt-BR/docs/Web/HTTP/Authentication
- https://www.ruby-toolbox.com/
- https://github.com/heartcombo/devise#getting-started

# Autenticação: logout e cadastro
- https://api.rubyonrails.org/classes/ActionView/Helpers/UrlHelper.html#method-i-button_to 
- https://css-tricks.com/a-complete-guide-to-links-and-buttons/
- https://github.com/heartcombo/devise#strong-parameters
- No Rails 7, agora para sair não se utiliza mais o Link to e sim:
<%= button_to 'Logout Admin', destroy_admin_session_path, method: :delete %>
- Houve um problema (erro do rails)  na hora de criar usuário entre o Rails 7 e o Devise que não aparece nos testes. Resolvi pesquisando que é preciso por no botão de criar User/Admin etc.
<%= f.submit "Sign up", data: { turbo: false } %>
- Interessante usar o autofocus para já abrir o formulário centrado no campo que você apontar. Só por autofocus: true no formulário.
- Interessante o Rails ter um field no forms para cada coisa: text, email, password_field, etc.
- Um outro modo para usar no  Assert dos testes:
user = User.last
expect(user.name).to eq 'Maria' 
- Para acrescentar campos no devise além do email e senha é necessário modificar no application controller conforme a documentação dele. 

# Bloqueando visitantes com rotas
- https://github.com/heartcombo/devise#controller-filters-and-helpers
- https://github.com/heartcombo/devise/wiki/How-To:-Define-resource-actions-that-require-authentication-using-routes.rb
- https://github.com/heartcombo/devise/wiki/How-To:-Test-with-Capybara
- Cria de cara um teste que prova que não é possivel acessar sem estar autenticado.
- O devise joga de volta para o root_path se a pessoa não puder acessar a página em questão.
- Dá para fazer de dois modos, pelo controller e pelo model.
- Dá para exigir autenticação em tudo jogando o before_action :authenticate_admin! direto no ApplicationController
- Outro modo de exigir o login é pelas rotas. Como um projeto de estudo deixei as duas opções ativas sem se anularem ou dar erro.

# Model de Preços
- Nome: freight prices
- Configurar preços por km por faixas: f1 até f8?
- Os preços da faixa é um float.
- Lembrar de por um km mínima para entregas
- Os preços são postos por cada transportadora. 
- É o user quem cadastra o preço nas faixas.
- Seria útil explicar os preços na tela de cadastro de algum modo.

# Criando um pedido
- Uma tela mais complexa, com models e conexões diversas entre eles.
- Perspectiva incremental: primeiro só com usuário, galpão e fornecedor. Só depois vai colocar os pedidos.
- Quando tem select, cria no teste um segundo item para ver se está selecionando o certo. Usa o not_to para testar justamente isso.
- No teste usa um select mais simples de escrever: 
select warehouse.name, from 'Galpão Destino'
- No formulário usa f.collection_select :warehouse_id, @warehouses, :id, :name
- Pesquisar o uso de collection_select nos formulários.
- O model Order tem várias associações, sempre no singular: warehouse:references supplier:references user:references.
- Usa estimated_delivery_date:date (aqui pega só uma data, poderia ser datetime para data e hora).
- Lida com o erro de map, dá porque a variável warehouses estava nula, preencheu isso dentro do model.
- Quando a rota é post (não get) o capybara não procura uma html para exibir e sim um endereço para te mandar (um html).
- No model ele pega o user usando @oder.user = current_user
- Diferença entre new_user_path (caminho relativo dentro da aplicação) e new_user_url (endereço completo http://localhost:3000/users/...)
- No path copia o que está na barra do seu navegador: google.com, vai para google.com/users/...
- URL é usado para sair do site que você está.
- Usa dois <%= %> numa linha só:
<%= order.user.name %> - <%= order.user.email %>
- Usa localize para ajustar a data de entrega no formulário:
I18n.localize(@order.estimated_delivery_date, format: :long)
- Para ir além do padrão, consultar o rails.pt-BR no locales que é de onde ele está tirando esse formato default, long, etc.
- Faz um teste que o usuário não ta logado, ai segue o padrão de criar ou logar usuário do devise.

# Melhorias na exibição
- https://dev.to/risafj/the-basics-of-rails-i18n-translate-errors-models-and-attributes-84d#1
- https://edgeapi.rubyonrails.org/classes/ActionView/Helpers/FormHelper.html#method-i-date_field
- Usa have_link no Capybara nos testes. Consultar artigo do CampusCode (principais links do capybara)
expect(page).to have_link('Galpões & Estoque", href: root_path)
- Faz um bloco no layout usando o link to para ser ao mesmo tempo h1 e link o título da página
<%= link_to root_path do %>
  <h1>Título da página</h1>
<% end %>
- Pode passar tudo, imagem, div, etc.
- Ajustes na exibição do collection_select. Para isso faz um teste unitário para testar a exibição completa. Ele testa um nome método da classe warehouse.
- Cria o método direto dentro do model. Pode ser útil para o calcpace versão site.
def full_description 
  "#(code) - #(name)"
end
- No teste disso basta usar User.new e similares porque ganha em velocidade de execução.
- A partir de então esse método pode ser usado na view:
<%= f.collection_select :supplier_id, @suppliers, :id, :full_description %
- Troca text_field por date_field, um ajuste para melhorar a usabilidade. Ambos são entendidos como strings.
- Padrão para criar novos arquivos de tradução em locales: order.pt-BR.yml (nome do model.lingua.yml)
- Pensando em expansibilidade, é interessante usar i18n o máximo possível no código.
- Usando a documentação acima: o <h1> seria Order.model_name.human ou Order.human_attribute_name("warehouse_id") </h1>

# Criando um código automático para o pedido 
- https://guides.rubyonrails.org/active_record_callbacks.html
- https://ruby-doc.org/stdlib-2.7.0/libdoc/securerandom/rdoc/SecureRandom.html
- https://github.com/rspec/rspec-mocks#method-stubs
- Gerar esse código tem que ser no Model, para garantir que mesmo usando Rails console ele precisa ser criado.
- Começando colocando um atributo no model a partir de uma migration. Começa com um teste unitário. 
- Um pouco diferente os expects, para ver especificamente o código da vaga de emprego.
- Vai usar o callback. O rails checa se tem alguma regra específica escrita no Model antes de suas ações, criar, salvar, apagar, etc.
- Usa o self no método no model e o método securerandom alphanumeric
- Para os testes, passa um allow assegurando o que vira pelo método (isso permite testar o que está sendo efetivamente exibido). 
- Usa before_valitation no lugar de before_create para poder testar corrretamente as validações e não quebrar os testes em cadeia.

# Validações personalizadas 
- https://guides.rubyonrails.org/active_record_validations.html#performing-custom-validations
- https://api.rubyonrails.org/classes/ActiveModel/Errors.html
- Fazer validações nos testes mais específicas, exemplo:
expect(order.erros.include? :estimated_delivery_date).to be true
- Dá para economizar linhas testando exclusivamente um aspecto, exemplo:
order = Order.new(:estitamed_delivery_date: '')
order.valid?
result = order.erros.include?(:estimated_delivery_date)
expect(result).to be true
- Método 5.days.ago (hour, etc.) e 1.month.from_now para auxiliar a trabalhar com tempo. Isso para os testes continuarem válidos.
- Necessário criar uma validação personalizada para garantir que não hajam pedidos/;vagas de empresa cadastradas com datas passadas. Há diversos modos de fazer isso, vai na estratégia do custom method no Model.
-       it "can't be in past" do
        job =  Job.new(date: 10.day.ago)
        job.valid?
        result = job.errors.include?(:date)
        expect(result).to be true               
      end
- A validação tem um detalhe, não tem o s:
validate :job_date_is_future
- O Rails sempre executa todas as validações. Por isso sempre garantir que o campo não está vazio.
- Recomenda fazer testes da borda: um antes, um na data e um depois.

# Busca de Pedidos - Parte 1
- Lembrar que nos controllers, quando você tem um collection select e faz um if else, no else tem  que popular novamente as variáveis para o formulário continuar funcionando.
- Utilizou within('header nav') no teste para pesquisar especificamente no nav dentro do header
- Utiliza o form_with para criar a pesquisa no menu.
- https://guiarails.com.br/form_helpers.html#formulario-de-pesquisa-generica
- Usar o método get garante todos os parâmetros vão estar na barra de endereço, é útil no compartilhamento de links.
- Evitar criar rotas fora do resources
- https://guides.rubyonrails.org/routing.html#adding-more-restful-actions
  <% if user_signed_in? || headhunter_signed_in? %>
    <%= form_with(url: search_jobs_path, method: :get) do |f| %>
      <%= f.label :query, 'Search Job' %>
      <%= f.text_field :query %>
      <%= f.submit 'Search' %>
    <% end %>  
  <% end %>
- V:ai criar a view do search e os respectivos atributos dentro do método no job_controller
- https://guiarails.com.br/active_record_querying.html#recuperando-objetos-do-banco-de-dados 
- Métodos indicados como mais importantes: find, distinct, order, select, where
- Vai usar o find_by para pegar o primeiro objeto que tenham os parâmetros utilizados.
- Como ficou em search.html.erb
<% if @job.present? %>
   <p>1 job found.</p>
   <dt>Code</dt>
   <dd><%= @job.code %></dd>
   <dt>Title</dt>
   <dd><%= @job.title %></dd>
<% end %>

# Busca de Pedidos (parte 2)
- https://www.w3schools.com/sql/default.asp
- https://www.rubyguides.com/2019/07/rails-where-method/
- No find_by você pode passar outros parâmetros.
Exemplo: Order.find_by(warehouse_id: 3, estimated_delivery_date: Date.parse('2022-05-28'))
- Na prática, where é mais completo. Permite uma busca com dados imcompletos do objeto.
- O where devolve uma coleção de objetos que atendam a consulta específica, mesmo que seja apenas um.
- Um uso mais abrangente do where:
User.where("name LIKE ?", "%#{'A'}%")
- No caso, todos que tenham A em algum lugar no name. O % é o caractere cooringa.
- Sugere testar busca com pelos menos 3 itens, incluindo itens que estejam selecionados pela busca e outros não.
- @jobs = Job.where("code LIKE ?", "%#{@code}%")
- Como vai retornar uma coleção, job virou jobs
- Quando aplicou o I18n para resolver o singular e plural nos resultados: pedido e pedidos a depender do resultado. Mostra que da para usar t() no lugar de I18n.translate

# Pedidos de um usuário
- Autenticação tem haver com login, autorização se tão user/admin/etc. tem autorização para tal ação.
- https://guiarails.com.br/association_basics.html#referencia-da-associacao-has-many
- https://guides.rubyonrails.org/layouts_and_rendering.html#rendering-collections
-eO index não é obrigatoriamente para listar tudo, pode ser usado para fazer index parciais.
- Reduz consideravelmente o código trazendo a busca das applies para dentro do controller
  def index
    if user_signed_in?
      @applies = current_user.applies.page(params[:page]) 
    else
      @applies = Apply.page(params[:page])
    end
  end

e utilizando uma partial sempre que precisar listar a apply

<% if @applies.any? %>
  <% @applies.each do |apply| %>
     <%= render apply %>
  <% end %>  
<% else %>  
  <p>There aren't any apply.</p>
<% end %>

e a apply.html.erb

<%= link_to apply do %>
  <dt>Apply ID<dt> 
  <dd><%= apply.id %></dd>
  <dt>Job Title</dt> 
  <dd><%= apply.job.title %></dd>
  <dt>User E-mail</dt> 
  <dd><%= apply.user_email %></dd>
<% end %>

# Autorização ao editar um pedido
- https://relishapp.com/rspec/rspec-rails/docs/request-specs/request-spec
- No show não costuma se usar a estratégia da partial utilizada no video anterior.
- Faz no controller um modo do usuário só ver sua própria apply etc.
  def show
    @apply = Apply.find(params[:id])
    if user_signed_in? && @apply.user != current_user
      flash[:alert] = 'You do not have access to this apply.'
      redirect_to root_path
    end     
  end
- Ajusta para 1day_from_tomorrow não exibir também o time no datetime:
1.day.from_now.to_date
- Como proteger então as métodos sem tela? Teste de request.
- Usa a documentação do link para montar um teste básico numa pasta request dentro de spec.
- Quando há dois redirects em um metodo no controller, o rails exige que um tenha return antes para garantir que termine ali o código, sem fazer o proximo redirect_to

# Adcionando status a um pedido 
https://api.rubyonrails.org/v5.1/classes/ActiveRecord/Enum.html
- Em banco de dados, uma busca por valores numéricos é mais eficiente
- No entanto, usar números no meio de condições prejudica a legibilidade do código.
- Os chamados Magic Numbers são uma prática ruim de programação
- O enum, enumerares, junta o melhor dos mundos, para o banco é número, no código é texto.
- Ele cria enum de status com espaços entre os números para no futuro ter espaço entre eles para mais status. Exemplo:
enum status {pending: 0, delivered: 5, canceled: 9}
- rails routes | grep orders
- Exemplo de chamada do terminal que filtra apenas as rotas com orders.
- novo_pedido.canceled! (isso atualizaria o status do pedido na marra, a não ser que tivesse algum erro no pedido.
- A classe também ganha métodos. Um é Order.peding que é igual a Order.all.where(status: 0) ou :peding 
- Outra consulta interessante: Joao.orders.delivered
- Não aconselha se fazer mudança de status usando as rotas de edição, deixa isso para um erro do usuário, algo assim.
- Cria uma rota nova para fazer o post de mudança do status: post 'drafted', on: :member
- No controller
  def published
    if @job.published!
      redirect_to @job
    else
      flash.now[:alert] = "Job Opening was not edited."
      render :new 
    end  
  end	 

na view faz a chave seletora de quais botões aparecem com <% if @job.published %>

# Itens de um pedido
https://guiarails.com.br/association_basics.html#a-associacao-has-many-through
- A estratégia utilizada é similar a da join tables, mas vai fazer um model de associação para poder colocar mais informações além dos ids que pretender reunir
- Assim pode também fazer novos atributos, validações, criar métodos específicos, etc.
- Esse model que referencia os dois como has_many, se utilizar o has_many: orders throught: :order_items permite acessar a outra ponta. No exemplo da documentação.
class Physician < ApplicationRecord
  has_many :appointments
  has_many :patients, through: :appointments
end

class Appointment < ApplicationRecord
  belongs_to :physician
  belongs_to :patient
end

class Patient < ApplicationRecord
  has_many :appointments
  has_many :physicians, through: :appointments
end
- Permite o rails acessar dados da classe na outra ponta. Por exemplo: em quais médicos o paciente é vinculado?

# Cadastrar itens ao pedido
https://guiarails.com.br/routing.html#nested-resources-recursos-aninhados
https://guiarails.com.br/association_basics.html#metodos-adicionados-por-has-many
https://solidfoundationwebdev.com/posts/using-build-or-new-on-a-has_one-assoication-in-rails
- A estratégia foi criar a proposal dentro do apply usando associações e diversos atalhos que has_many e has_one permite utilizar.
resources :applies do
  resources :proposals, only: [:show, :new, :create, :edit, :update, :destroy]
end 
- Há métodos que facilitam a construção dos controllers e das views que vale a pena se aprofundar nas documentações.

# Entrada de produtos no estoque
Aciona uma contagem dentro do teste system para ver se algo foi adcionado no banco de dados. Exemplo:
expect(StockProduct.count).to eq 5
estoque = StockProduct.where(product_model: product, warehouse: warehouse).count
expect(estoque).to eq 5
- Ai vê se eles foram criados e se foram efetivmente para o lugar certo, o estoque.
- Isso é interessante para ver se algo foi efetivamente salvo no banco. Ou o inverso, garantir que após deletado seja zero.
- No controller ele utiliza o .times do para criar a quantidade certa de produtos no estoque. Exemplo:
@order.order_items.each do |item|
  item.quantity.times do
    StockProduct.create!(order: @order, product_model: item.product_model, warehouse: @order.warehouse)
   end
end

# BUG ao atualizar pedidos + código automático para o produto em estoque 
- Descobre que o código de um pedido tem um bug que ele muda a cada vez que há um update no pedido.
- Dica interessante, quando achar um bug, fazer um teste que prove que o bug existe.
 it "and it can't change after an update" do
   job = Job.create!(title: 'Job Opening Test', description: 'Lorem ipsum dolor sit amet', skills: 'Nam mattis, felis ut adipiscing.', salary: '99',
company: 'Acme', level: 'Junior', place: 'Test', date: 1.month.from_now)
  result = job.code 
  job.update!(company: "Test")
  expect(result).not_to be_empty
  expect(result).to eq job.code
end
- A solução é simples, dizer ao Model que o método de gerar o código só será rodado na criação do pedido:
before_validation :generate_code, on: :create

# Listado o estoque de um galpão
- https://guides.rubyonrails.org/active_record_querying.html#group
- Um modo simples de criar algo nos testes
3.times {StockProduct.create!(order: order, warehouse: w, product_model: produto_tv)} 
- Utiliza o group para ficar no Controller views que tenham a quantidade e o modelo de um produto específico no estoque.
@stocks = @warehouse.stock_products.group(:product_model).count
- Já na view:
<% @stocks.each_pair do |pm, quantity| %>
  <%= quantity %> x <%= pm.sku %> 
<% end %>

# Saída de itens do estoque 
https://guides.rubyonrails.org/association_basics.html#the-has-one-association
https://api.rubyonrails.org/classes/ActiveRecord/Associations/ClassMethods.html
- A solução para indicar destino de produtos de estoque é criar um Model de Destino que está ligado a um StockProduct através do has_one
- O rails testa os input de um formulário se são condizentes com o que está no model
- Cria uma rota post dentro da view do galpão para se mandar os produtos. No controller:
resources :warehouses do
  resources :stock_product_destinations, only [:create]
end
- Na view
<%= form_with(url: warehouse_stock_product_destinations_path(@warehouse.id)) do |f| %>
  <%= f.label(:product_model_id, 'Item para Saída' %>
  <%= f.collection_select(>product_model_id, @product_models, :id, :sku) %>
<% end %>
- Detalhe importante, é um formulário de URL que está na view de @warehouse. Usou isso porque vai receber uma informação que não faz parte desse módel. Não é o mais indicado mas é possível quando necesssário.
- No StockModelDestinationsController:
def create

end
- Seria interessante um teste para não poder selecionar produtos que não estejam em certo estoque. Ajustar isso em @product_models no controller, uma query espefícica. 
- Uma boa prática de ensino: troca os nomes das variáveis por x e y em algum momento para ficar mais claro e fugir do warehouse: warehouse, product_model: product_model. Depois volta aos nomes originais.
- Vai usar o missing (disponível desde o rails 6) para buscar para seleção produtos que ainda não foram enviados.
@stocks = @warehouse.stock_products.where.missing(:stock_product_destination).group(:product_model).count
- Para fins didáticos, ver o uso de expressões como semântica e sintaxe.
- Organiza a página retirando divs e colocando <section id="stock_destination">, uma possibilidade interessante para o AllJobs
- Usa a section no teste para deixa-lo mais específico utilizando o seletor css:
within("section#stock_product") do
  expect(page).to have content....
end
- Cria um método no model StockProduct para saber se ele está mesmo disponível ou se já foi despachado para um lugar:
def available?
  stock_product_destination.nil? 
end

# APIs: introdução e detalhes de um galpão
- Application programming interface: uma forma simplificada de executar códigos de uma aplicação
- Um método de ruby faz parte da API da linguagem
- uma gem pode ter sua api, um botão na tela é uma api
- Mais comum hoje é falar em API Web
- É utilizado para integrações entre duas ou mais aplicações
- O formato mais comum hoje são as REST APIs: conjunto de boas práticas, usam http como procotolo, dados são retornados em algum padrão, sendo JSON o mais popular.
- Serão criados controllers separados com uma herança específica que indica ao Rails ser uma API. Além disso na aplicação sem ser API é interessante ter mais telas.
- Numa API se dá mais atenção ao status, o retorno, HTTP.
- Uma gem de JSON para ver mais a frente é a JBuilder
- Boas práticas das APIs: versionamento (v1/products/1... v2/products/2...).
- É comum ter mais de uma versão em funcionamento ao mesmo tempo.
- Outra pŕatica: documentação explicando os resultados das requisições.
- APIs são vias de mão dupla: implementação para expor dados e outra para consumir dados.
- Testes de API são testes de request simulando um acesso externo a sua aplicação que não passa pela interfaces, sem passar pelas telas, etc.
- Importante por "job.id" nos testes porque nem todo banco de dados é como o SQL e reseta quando termina o teste.
- A variável de resposta é expect(response)...
      get "/api/v1/jobs/#{job.id}"
      expect(response).to have_http_status(200)
      expect(response.content_type).to include 'application/json'
      expect(response.body).to include("Test")
- o rails routes -g job faz o recorte das rotas apenas com job dentro.
- Nas rotas:
  namespace :api do
    namespace :v1 do
      resources :jobs, only: [:show]
    end  
  end
- Vai separar os controllers e rotas da API e da aplicação.
- Uma vez criada a rota, cria o controller seguindo uma estrutura de pastas determinada já na rota: controllers/api/v1/ e o controller em si jobs_controller.rb
- Dentro dele, conforme a documentação do rails guides
class Api::V1::JobsController < ActionController::API
  def show
    @job = Job.find(params[:id])
    render json: @job  
  end 
end
- Para consultar os status HTTP
https://developer.mozilla.org/pt-BR/docs/Web/HTTP/Status
- Usa um comando para transformar o JSON em hash e testar melhor. Dai modifica o teste
json_response = JSON.parse(response.body)

      expect(json_response["title"]).to include("Job Opening Test 123")
      expect(json_response["description"]).to include("Lorem ipsum dolor sit amet") 

# APIs: listando todos galpões 
https://guru-sp.github.io/tutorial_ruby/excecoes.html
- Começa ensinando a cortar as informações não consideradas necessárias. No teste: expect(json_response.keys).not_to include("created_at")
- No controller
  def show
    @job = Job.find(params[:id])
    render status: 200, json: @job.as_json(except: [:created_at,:updated_at])  
  end 
- Detalhe importante, um render não acaba a execução de um código. Por isso, dois renders ou mais em um controller pode dar erro dele não saber que resposta dar.
- Isso por o render deixa a resposta na mão pronta, caso não aconteça nada de novo na execução do código, essa resposta é devolvida.
  def show
    @job = Job.find_by(id: params[:id])
    if @job.nil?
      render status: 404, json: @job
    else
      render status: 200, json: @job.as_json(except: [:created_at,:updated_at])
    end    
  end 
end
- A diferença do find_by nesse caso é se não achar ele retorna nil. A partir desse nil é que ta jogando o 404.
- Fazendo de outro modo:
  def show
    begin
      @job = Job.find(params[:id])
      render status: 200, json: @job.as_json(except: [:created_at,:updated_at])
    rescue
      render status: 404, json: @job  
    end    
  end 
- Nessa opção há tratamento de erro.
- Cada operação da API, cada rota é um endpoint.
- A rota index é semelhante, só que com @jobs.
- Dá para selecionar o modo como ele lança os jobs no JSON. Por exemplo:
@jobs = Job.all.order(:title)
      render status: 200, json: @jobs.as_json(except: [:created_at,:updated_at]
- Nos testes:
      expect(json_response.length).to eq 2
      expect(json_response.first["title"]).to eq('Job Opening Test 123')
      expect(json_response.last["title"]).to eq('Job Opening Test 456')
- O teste se não há jobs é diferente:
    it "return empty - there aren't jobs" do   
      get "/api/v1/jobs/"

      expect(response.status).to eq 200
      expect(response.content_type).to eq("application/json; charset=utf-8") 

      json_response = JSON.parse(response.body)
      expect(json_response).to eq []
    end

# APIs: Criando galpões e tratando erros 
- Status 201 ou :created - indica que algo foi criado através de um POST.
- Um método útil no teste: expect(response).to have_http_status(201)
- Testou se apareceu cada detalhe do job recem-criado, já que se trata de uma ação POST
- Quando usa ! em ações como job.save!, ele para e avisa o que deu errado.
- No controller:
  def create
    @job = Job.new(job_params)
    if @job.save
      render status: 201, json: @job  
    end
  end
- Já as informações enviadas para criar o teste são chamados de payload:
job_params = { job: { title: 'Job Opening Test 123', ...  date:  } }
- Usa o erro 412 de Precondition Failed para o erro em que as informações não vem completas para o POST ser processado. Usa a documentação da Mozilla para consultar os status disponíveis.
- Como fazer que a api devolva os erros? Usando a mesma tática do outro controller  def create
    @job = Job.new(job_params)
    if @job.save
      render status: 201, json: @job  
    else
      render status: 412, json: { errors: @job.errors.full_messages }
    end
  end
- No outro teste ele faz um post que vai dar erro interno da aplicação, não do dusuário. Nesse sentido, um erro genérico da família 500.
- Para isso vai usar um mock para forçar no teste algo dar errado.
- https://github.com/rspec/rspec-mocks
-     it "without sucess - internal error" do
      allow(Job).to receive(:new).and_raise(ActiveRecord::ActiveRecordError)
- No controller acrescenta um rescue (mesma estratégia já utilizada anteriormente:
  def create
    begin
      @job = Job.new(job_params)
      if @job.save
        render status: 201, json: @job  
      else
        render status: 412, json: { errors: @job.errors.full_messages }
      end
    rescue
      render status: 500, json: @job
    end    
  end
- Faz um teste semelhante no index para mostrar uma forma de refatorar essa solução begin/rescue.
- No começo do controller:
rescue_from ActiveRecord::ActiveRecordError, with: :return_500
  rescue_from ActiveRecord::RecordNotFound, with: :return_404 
- Como método privado:
def return_404
  render status: 404, json: @job
def return_500
  render status: 500, json: @job
end
- No caso, escolheu uma classe genérica de erros para abranger vários erros específicos que herdam dela. Para dar certo primeiro o erro genérico, depois o mais específico. 
- Utilizou o que está na documentação: https://edgeapi.rubyonrails.org/classes/ActiveSupport/Rescuable/ClassMethods.html
- A estratégia indicada de refatoração é criar um controller só para comportar esses erros e os controllers da api herdarem dele.

# Consumindo APIs: Lista de Galpões 
- Utiliza o curl no terminal para testar o consumo da API:
 curl http://[::1]:3000/api/v1/jobs/1
- https://www.campuscode.com.br/conteudos/comandos-curl-para-testar-requisicoes-api
- Também utiliza a extensão do Firefox https://addons.mozilla.org/en-US/firefox/addon/rester/
- Atenção para as "" na hora de fazer um POST. Exemplo:
{ "job": { "title": "Job Opening Test 123", "description": "Lorem ipsum dolor sit amet", "skills": "Nam mattis, felis ut adipiscing.", "salary": "99",  "company": "Acme", "level": "Junior", "place": "Remote Job", "date": "" } }
- É possível postar também via curl:
curl -X POST -H "Content-Type: application/json" -d '{"job": { "title": "Job Opening Test 123"...} }' http://[::1]:3000/api/v1/jobs/
- Algumas questões relativas a API ser de mão dupla: parte das API são pagas, elas ficam em manutenção em algum momento, há limitações de uso, e queremos testar o cenário para além do sucesso.
- Vai utilizar um novo projeto rails (sem model, apenas consome do projeto atual) e a gem Faraday para facilitar as chamadas http
- O projeto teve que ser criado com todas as configurações para rodar o rspec-rails e capybara.
- Vai criando na mão e dando rspec a cada comando até ter pelo menos o erro da action, ai já ta garantido que a criação da rota e do controller está correta.
- O objetivo: conectar na API, acessar o endpoint de jobs, receber o JSON, tratar o JSON.
- Por que não usar a biblioteca padrão do ruby nesse caso? Porque ela devolve tudo em um padrão de string.
- https://lostisland.github.io/faraday/usage/
- https://campuscode.com.br/conteudos/tdd-com-ruby-on-rails-e-faraday
- Como não sobem duas aplicações rails na mesma porta 3000, quando subir os dois é necessario passar um para a porta 4000, como? rails server -p 4000.
- Para os testes, vai usar o mock para pegar uma resposta "fake", guardada na pasta spec/support/json/response.json
- No caso, cria um arquivo json que simula a resposta.
- Ele cria um double (entre dublê e dúbio) da resposta.
- No teste dessa segunda applicação:
it "and see jobs with sucess" do
    json_data = File.read(Rails.root.join('spec/support/json/jobs.json'))
    fake_response = double("faraday_response", status: 200, body: json_data)
    allow(Faraday).to receive(:get).with('http://localhost:4000/api/v1/jobs').and_return(fake_response)
    
    visit root_path
    expect(page).to have_content "SEEJOBS"
    expect(page).to have_content "Job Opening Test 123"
    expect(page).to have_content "1"
    expect(page).to have_content "Ykeabwhq"
    expect(page).to have_content "Job Opening Test 456"
    expect(page).to have_content "2"
    expect(page).to have_content "Kl92zlzt"
  end

  it "and do not see any jobs" do
    fake_response = double("faraday_response", status: 200, body: "[]")
    allow(Faraday).to receive(:get).with('http://localhost:4000/api/v1/jobs').and_return(fake_response)
    
    visit root_path
    expect(page).to have_content "SEEJOBS"
    expect(page).to have_content "No Job Openings found."
  end  
- Já no controller:
class JobsController < ApplicationController
  def index
    response = Faraday.get('http://localhost:4000/api/v1/jobs')
    @jobs = JSON.parse(response.body)
  end    
end
- Na view:
<h1>SEEJOBS</h1>

<% if @jobs.empty? %>
  <p>No Job Openings found.</p>
<% end %>

<% @jobs.each do |j| %>
<div>
  <%= j["id"] %>
  <%= j["title"] %>
  <%= j["code"] %>
</div>
<% end %>

# Consumindo APIs: detalhes de um galpão 
- Utiliza a mesma estratégia de mocks, só que dessa vez 2. Também acrescenta um notice caso não encontre o galpão pedido, e redireciona para o root_path.
- Assim como em um projeto rails comum cria rotas, view, etc.
- No teste:
    json_data = File.read(Rails.root.join('spec/support/json/jobs.json'))
    fake_response = double("faraday_response", status: 200, body: json_data)
    allow(Faraday).to receive(:get).with('http://localhost:4000/api/v1/jobs').and_return(fake_response)

    json_data = File.read(Rails.root.join('spec/support/json/job.json'))
    fake_job = double("faraday_response_job", status: 200, body: json_data)
    allow(Faraday).to receive(:get).with('http://localhost:4000/api/v1/jobs/1').and_return(fake_job)
    
    visit root_path
    click_on "Job Opening Test 123"

    expect(page).to have_content "Job Ykeabwhq"
    expect(page).to have_content "Title: Job Opening Test 123"
    expect(page).to have_content "ID: 1
- No teste caso não encontre, procura um notice e o double vazio é um {}, não uma array de objetos
    json_data = File.read(Rails.root.join('spec/support/json/jobs.json'))
    fake_response = double("faraday_response", status: 200, body: json_data)
    allow(Faraday).to receive(:get).with('http://localhost:4000/api/v1/jobs').and_return(fake_response)

    fake_job = double("faraday_response_job", status: 500, body: '{}')
    allow(Faraday).to receive(:get).with('http://localhost:4000/api/v1/jobs/1').and_return(fake_job)
    
    visit root_path
    click_on "Job Opening Test 123"

    expect(current_path).to eq(root_path)
    expect(page).to have_content "No Job Opening found."
- No controller, pega se vai pegar os dados ou não pelo response.status
  def show
    id = params[:id]
    response = Faraday.get("http://localhost:4000/api/v1/jobs/#{id}")
    if response.status == 200
     @job = JSON.parse(response.body)
    else
      redirect_to root_path, notice: "No Job Opening found."
    end   
  end

# Consumindo APIs: isolando o código em Models 
- Quer refatorar o controller e views da segunda aplicação, a de consumo de API
- Deixar mais próximo de uma aplicação Rails comum, para isso vai criar um Model- Models são abstrações, servem para organizar nossa cabeça e não obrigatoriamente precisam herdar de algum lugar.
- Utiliza keyword arguments e um atrr_acessor nessa classe para facilitar a escrita, passa parâmetros nomeados
https://campuscode.com.br/conteudos/usando-keyword-arguments
	- Cria classe para organizar o código e ficar mais fácil construir algo sobre ele, estratégia "semelhante" ao que aparece no livro do Why.
- Ele isolou a lógica dentro do model, para simplificar a escrita em outras partes.
- Quando você usa essa estratégia de trazer para um model parte dos códigos da API, abre a possibilidade de fazer mais testes de Model também. Um aspecto relevante que evita carregar os testes de sistema.
- Permite também melhorar os testes de sistema, já que o mock está dentro do model.
- O model de "apoio" criado:
class Job

  attr_accessor :id, :title, :description, :skills, :salary, :company, :level, :place, :date, :code, :job_status
  
  def initialize(id: ,title: , description: , skills: , salary: , company: , level: , place: , date: , code: , job_status: )
    @id = id
    @title = title
    @description = description
    @skills = skills
    @salary = salary
    @company = company
    @level = level
    @place = place
    @date = date
    @code = code
    @job_status = job_status
  end

  def self.all
    jobs = []
    response = Faraday.get('http://localhost:4000/api/v1/jobs')
    if response.status == 200
      data = JSON.parse(response.body)
      data.each do |j|
        jobs << Job.new(id: j["id"], title: j["title"], description: j["description"], skills: j["skills"], salary: j["salary"], company: j["company"], level: j["level"], place: j["place"], date: j["date"], code: j["code"], job_status: j["job_status"])
      end
    end  
    jobs       
  end
end 

- Refatorando o index do controller:
class JobsController < ApplicationController
  def index
    @jobs = Job.all
  end   
- O teste do model com acesso ao index e o sem conseguir acessar a api:

describe Job do
  context ".all" do
    it "return all with sucess" do
      json_data = File.read(Rails.root.join('spec/support/json/jobs.json'))
      fake_response = double("faraday_response", status: 200, body: json_data)
      allow(Faraday).to receive(:get).with('http://localhost:4000/api/v1/jobs').and_return(fake_response)
      result = Job.all
      expect(result.length).to eq 2
      expect(result[0].id).to eq 1
      expect(result[0].title).to eq  "Job Opening Test 123"
      expect(result[0].description).to eq "Lorem ipsum"
      expect(result[0].skills).to eq "Nam mattis"
      expect(result[0].salary).to eq "99.0"
      expect(result[0].company).to eq "Acme"
      expect(result[0].level).to eq "Junior"
      expect(result[0].place).to eq "Remote"
      expect(result[0].date).to eq "2022-08-31"
      expect(result[0].code).to eq "Ykeabwhq"
      expect(result[0].job_status).to eq "draft"
      expect(result[1].id).to eq 2
      expect(result[1].title).to eq  "Job Opening Test 456"
      expect(result[1].code).to eq "Kl92zlzt"
    end

    it "return nothing if API unavailable" do
      fake_response = double("faraday_resp", status: 500, body: "{'error': 'test error'}")
      allow(Faraday).to receive(:get).with('http://localhost:4000/api/v1/jobs').and_return(fake_response) 
      result = Job.all
      expect(result).to eq []
    end
  end 
end

- Atenção para que já há refatoração no primeiro teste de System, simplificando a lógica do arrange dos testes:

it "and see jobs index with sucess" do
    jobs = []
    jobs << Job.new(id: 1, title: "Job Opening Test 123", description: "description", 
                      skills: "skills", salary: "99.0", company: "Acme", 
                      level: "Junior", place: "Remote", date: "2099-08-01", 
                      code: "Ykeabwhq", job_status: "draft")
    jobs << Job.new(id: 2, title: "Job Opening Test 456", description: "description", 
                      skills: "skills", salary: "99.0", company: "Acme", 
                      level: "Junior", place: "Remote", date: "2099-08-01", 
                      code: "Kl92zlzt", job_status: "draft")
    allow(Job).to receive(:all).and_return(jobs)

    visit root_path
    expect(page).to have_content "SEEJOBS"
    expect(page).to have_content "Job Opening Test 123"
    expect(page).to have_content "1"
    expect(page).to have_content "Ykeabwhq"
    expect(page).to have_content "Job Opening Test 456"
    expect(page).to have_content "2"
    expect(page).to have_content "Kl92zlzt"
  end



