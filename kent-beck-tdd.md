# Notas -  Kent Beck - Test-Drive Development by Example, 2002

## Prefácio
- TDD é: escrever novas linhas somente se um teste falhar, eliminar duplicações.
- Isso se desdobra em: o design tem que ser orgânico, escrever seus próprios testes, um ambiente de desenvolvimento que dê respostas rápidas a pequenas mudança e design coeso, menos componentes agregados e fácil de produzir testes.
- Os três estágios: vermelho (teste não funciona), verde (teste funciona), refatoraçãoÇ eliminando duplicações.
- Requer: tentar várias vezes, ser comunicativo, obter feedback.
- Começar simples, escrever testes automáticos, refatorar e mudar o design.

## Introdução
- O ambiente do livro: experiência de crescimento constante do design do sistem, uma motivação para transformar esse sistema, oportunidade a partir da combinação de compreensão, confiaça nos testes, programa bem desenhado, linguagem de programação que permite isolar decisões de design e com poucas fontes de erros, esses fáceis de identificar.

## Parte 1: O exemplo do dinheiro
- Necessário: rapidamente criar um teste, rodar os testes e ver o novo falhar, realizar pequenas mudanças, rodar os testes e eles passarem, refatorar as duplicações.
- Importante atentar: como cada test cobre um pequeno incremento de funcionalidade, como mudanças pequenas e feias podem fazer o teste rodar, de quandoe quando rodar os testes, os pequenos passos de refatoração.
- Não se importa com a "estética", faz testes e soluções feias para depois ir refatorando.
- Cria constantes só para passar os testes, depois gradualmente substitui por variáveis.
- Utiliza uma to-do list e vai atualizando de acordo com avanços, novas ideias, etc.
- O foco no "código limpo que funciona". Para isso primeiro investe no funciona,só depois nas refatorações é que busca o "clean code".
- Ataca soluções óbvias nos testes, só depois vai incrementando as funcionalidades.
- Estratégias de testes: Fake it - faz funcionar com constantes só depois vai para as variáveis do código real. Implementação óbvia: as a implementação real do código.
- Já na triangulação atenta para que variáveis de instância do objeto "não" mudam. O foco é criar novos objetos a cada operação e fazer uma comparação entre eles. Criar um teste com valor que passe, outro com valor que não passe. A partir disso triangular uma solução mais adequada para aquela situação. **NECESSÁRIO REVISAR ESTE TEMA?**
- Na triagunlação, se generaliza o código a partir de dois exemplos ou mais. Isso gera duplicação? Sim, mas isso só será resolvido depois. 
- O design implica uma série de operações, no caso do livro, Value Object. Ele permie criar objetos simples com cópias de atributos sem permitir sua alteração.
- Para testes mais legíveis, escreve coma uma afirmativa verdadeira, não uma sequência de operações.
- Dois testes falhar de uma vez não é um bom sinal, está fora da lógica TDD.
- Partes rápidas do TDD: escrever o teste, compilar, ver falhar. Partes lentas: fazer funcionar, refatorar.
- Uma estratégia para fazer o teste passar logo é copiar e remodelar partes de código já prontas.
- Sem testes o suficiente, há menos confiança em se alterar o código.
- Escrever testes pensando em leitores futuros, mesmo que ele seja você mesmo daqui um tempo.
- Fazer experimentos comparativos entre TDD e seu estilo de programação atual.
- Atentar para a situação dos testes que não deviam passar, mas passam. Sinal que é necessário rescrever sua implementação.
- Qualidade de teste: eles não substituem outros tipos de teste - performance, estresse, usuabilidade.	
- Cobertura dos testes (% do código?) não mede sozinha a qualidade dos testes, mas é um começo. TDD mira cobrir 100% do código.
- Inserção de defeitos é outra estratégia, fazer o teste quebrar a partir da mudança de uma linha de código.
- Atentar apara a complexidade da lógica, isso acaba aparecendo nos testes.
- Lembrar das três estratégias de fazer um teste passar.
- Remover a duplicação entre test e código é um caminho de impulsionar e melhorar o design.
