# Feira Tecnológica de Inovação

## Enredo
A escola está organizando uma **Feira Tecnológica de Inovação**, onde diversos projetos de diferentes áreas serão apresentados.  
O sistema que deve ser desenvolvido em **Java** tem como objetivo **gerenciar os projetos expostos** e também registrar as **avaliações feitas pelos avaliadores convidados**.

## Regras gerais
### Todo Projeto tem:
- Nome do projeto
- Nome do responsável
- Instituição de origem
- Espaço reservado na feira

### Tipos de Projeto
**Projeto de Robótica**  
- quantidade de sensores utilizados  
- hardware utilizado (Arduino, ESP32, Raspberry Pi etc.)  
- software utilizado (IDE Arduino, ROS etc.)  
- linguagem de programação utilizada  

**Projeto de Software**  
- linguagem de programação principal  
- plataforma de desenvolvimento (Web, Mobile, Desktop)  
- framework ou biblioteca usada  

**Projeto de Ciências**  
- tema da pesquisa  
- origem da pesquisa (laboratório da escola, universidade parceira etc.)  
- área científica (Biologia, Física, Química etc.)  

### Avaliação
- Cada **Avaliador** tem:
  - nome  
  - especialidade (Robótica, Software, Ciências etc.)
 




# Campeonato Esportivo

## Enredo
Uma universidade está organizando um campeonato esportivo entre diferentes modalidades.  
O sistema deve ser desenvolvido em Java para gerenciar os times participantes, os árbitros responsáveis e as partidas realizadas.

## Estrutura do Sistema
- **Time (classe base):**
  - nome
  - instituição de origem
  - número de jogadores

- **Time de Futebol (subclasse):**
  - técnico responsável
  - número de reservas

- **Time de Vôlei (subclasse):**
  - altura média dos jogadores
  - quantidade de sets jogados

- **Time de Basquete (subclasse):**
  - altura média dos jogadores
  - capitão do time

- **Árbitro:**
  - nome
  - modalidade em que atua
  - anos de experiência

- **Partida:**
  - time1
  - time2
  - árbitro responsável
  - resultado final

## O que deve ser entregue
- Criar pelo menos um time de cada modalidade.  
- Criar árbitros.  
- Simular pelo menos duas partidas, mostrando:
  - informações dos times,
  - árbitro responsável,
  - resultado final.


- Cada avaliador pode atribuir **uma nota** a um projeto.  
- O Projeto deve registrar **o nome do avaliador e a nota atribuída**.


# Agência de Viagens

## Enredo
Uma agência de viagens deseja informatizar o cadastro de pacotes turísticos e os guias responsáveis por cada viagem.  
O sistema deve ser desenvolvido em Java para registrar os pacotes disponíveis e exibir suas informações.

## Estrutura do Sistema
- **Pacote (classe base):**
  - destino
  - duração em dias
  - preço

- **Pacote Nacional (subclasse):**
  - estado de destino
  - transporte utilizado

- **Pacote Internacional (subclasse):**
  - país de destino
  - necessidade de visto (sim/não)

- **Pacote de Aventura (subclasse):**
  - nível de dificuldade
  - equipamento incluso (sim/não)

- **Guia:**
  - nome
  - idioma que fala
  - anos de experiência

## O que deve ser entregue
- Criar pelo menos um pacote de cada tipo.  
- Associar cada pacote a um guia de turismo.  
- Mostrar no console:
  - informações do pacote,
  - dados do guia responsável.


# Biblioteca Digital

## Enredo
Uma universidade deseja informatizar sua biblioteca digital.  
O sistema deve ser desenvolvido em Java para cadastrar obras e organizar os empréstimos feitos pelos usuários.

## Estrutura do Sistema
- **Obra (classe base):**
  - título
  - autor
  - ano de publicação

- **Livro (subclasse):**
  - número de páginas
  - gênero literário

- **Revista (subclasse):**
  - edição
  - área (ciências, tecnologia, cultura etc.)

- **Artigo Científico (subclasse):**
  - conferência/jornal publicado
  - DOI

- **Usuário:**
  - nome
  - matrícula
  - curso

- **Empréstimo:**
  - obra emprestada
  - usuário responsável
  - data do empréstimo
  - data de devolução

## O que deve ser entregue
- Criar pelo menos um objeto de cada tipo de obra.  
- Criar usuários.  
- Realizar empréstimos e exibir no console:
  - dados da obra,
  - informações do usuário,
  - datas de empréstimo e devolução.

