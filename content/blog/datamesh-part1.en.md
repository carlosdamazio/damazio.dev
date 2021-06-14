---
title: Data Mesh - Concepts [Part 1]
summary: This is the start of a blog post series regarding data mesh. In this post, we are going to discuss concepts and then we jump into the architectural aspect of it.
publishDate: 2021-05-25
images:
  - /img/post-datamesh-part-1/datamesh-part1-title.png
slug: datamesh-part-1
tags: ["data engineering", "theoretical", "architecture"]
aliases: [
  "/blog/datamesh-part-1"
]
draft: true

---

Hey, y'all!

In this post, I'll be starting an ambitious project: a blogging series about data mesh, from zero to hero. What you may expect? 

- Initially, I'll be introducing some important concepts about the data mesh, from data pipeline to its steps in-depth.
- Right after, we're going to discuss the architectural aspects of the data mesh and some of the alternatives, like Kappa and Lambda architectures.

We might agree that theoretical aspect is boring and we should skip it?

No, we need to discuss it, because otherwise, none of the implementation is going to make sense, neither the architecture. It's extremely necessary to go into it
in order to have a more in-depth discussion about it.

## Project's main deliverable
Our main objective with this series is to deliver a use case of Data Meshing and answer if it is, or not, the state-of-the-art architecture for data projects in an organization. 

With the definitions and expectations out of our way, we'll need a starting point. We all know that the data field is mostly known by the data science branch. But there's another branch that
doesn't receive as much attention as it should be: Data Engineering. So, yeah, the infrastructure part of the whole ordeal became so complex that it became impossible for the data scientist
to deal with it, because this process itself is not a valuable deliverable for the scientist as the insights that he/she can bring to an organization.

## Data Field Overview
We can agree that the data field is NOT a computer science's formal study field like AI or Algorithms, but it overlaps with some of them like Statistics, Linear Algebra, Databases, Algorithms and Data Structures.

I'm not going in-depth of how everything in Data Engineering or Data Science came to be, but my research indicates that the first studies that talks about data in our context comes from the 80's with Kimball's and Inmon's approaches to
*data warehouse* as decision's supporting systems for organizations, in which **business intelligence** covers most of this part.

We assume that business intelligence deals with decisions based on past data on a reactive way. As the time passes by, there was a need to deal with past behavior AND identify patterns using scientific analysis along with statistics. 
With that, data science was born.

As well, there was a need to automate the way we identify patterns in our data without human intervention

## Big Data

É uma área de estudo na computação que é bastante recente que lida em como lidamos com dados que necessáriamente possuem complexidade em 3 aspectos, que podem estar presentes em conjunto ou não, com os quais chamamos de *3Vs*.
![Diagrama dos 3Vs do Big Data](https://upload.wikimedia.org/wikipedia/commons/e/ee/Big_Data.png)
*Fonte: [Wikipédia](https://en.wikipedia.org/wiki/Big_data#/media/File:Big_Data.png)*

### Volume 
Este aspecto em Big Data diz respeito ao grande volume de dados manipulados e armazenados.

Lembra quando achávamos o *gigabyte* uma ordem de grandeza estrondante? Pois é, agora básicamente podemos comprar discos rígidos e SSDs nas ordens de *terabyte* por troco de pão.
Não podemos falar somente do armazenamento, mas sim de quanto de volume é trafegado nos nossos sistemas de dados. Hoje, é sabido que na internet é trafegado mais de 100.000 *petabytes*, ou seja: mais de 100.000.000.000 *gigabytes*.

### Velocidade
Este aspecto em Big Data diz a respeito da velocidade e frequência com as quais manipulamos os dados.

Além de termos que lidar com dados em grandes volumes, temos que lidar com estes em bastante velocidade.
Eu citei que antes a gente lidava com dados do passado para tomar decisões em organizações, mas com o advento da globalização e internet, todo o mundo se acelerou, literalmente, em tudo. Com mais dados armazenados e com necessidade de processamento cada
vez mais rápido, não podemos mais confiar em processamento *batch* (em lote), dando mais espaço para processamento em tempo real até mesmo para prever com precisão o que acontecerá no futuro.

### Variedade
Este aspecto em Big Data diz a respeito da variedade de dados com os quais manipulamos.

Observe como a gente se relaciona hoje em dia na internet: no Twitter, Instagram, Telegram e afins. Tem amizades que a gente se comunica através de memes, de imagens. Como poderíamos ter previsto este tipo de comunicação há 20 anos atrás.
Óbviamente, eu nunca iria previr porque eu tinha 5 anos de idade, mas a grande maioria das pessoas não previam isso acontecer. Na internet, mais do que simplesmente falando que está sendo trafegado uma cadeia de bytes para todos os lados (leia-se texto), está sendo trafegado imagens, e-mails,
mensagens de voz, vídeos, planilhas. Quanto mais dados puderem ser analisados, maiores serão as chances de sucesso de uma organização.


Percebe como a forma que manipulamos os dados hoje em dia pode ser algo bastante complexo? Não são cabíveis os métodos tradicionais de analisar e processar os dados, nem mesmo os de armazenamento. Para lidar com essa complexidade, foi necessário retirar das mãos dos analistas e cientistas de dados esta responsabilidade e criar uma nova área de estudos com relação a isso.

## Engenharia de dados
É uma área multidisciplinar de estudos a respeito dos métodos e ferramentas de manipulação de dados, que podem ser considerados Big Data ou não. Novamente, é uma área totalmente multidisciplinar, pois tem-se vários aspectos envolvidos, como por exemplo:

- Computação distribuída: área de estudos dos sistemas distribuídos, que consiste de computadores interligados por redes diferentes.
- Rede de computadores: área de estudos de comunicação entre os computadores em mais variados aspectos.

Podem haver outras áreas relacionadas, mas o importante é notar que a engenharia de dados é um *overlap* de várias áreas com o objetivo de estudar métodos e ferramentas para manipular dados.

Antigamente, havia-se o tempo em que, manualmente, tínhamos que fazer um cientista de dados baixar dados brutos, carregá-los em uma ferramenta
para poder limpar, formatar, para depois serem aplicados os trabalhos de análise. Até porque hoje em dia, os dados não são apenas jogados em um
banco de dados estruturado (SQL) e ser feliz. Dependendo do volume, há a necessidade de particionar as tabelas, reindexar e dentre outros processos
para assegurar a persistência de dados. Naturalmente, com o aumento dos dados e complexidade, fica ainda mais complicado de consultar e armazenar os dados.

E falamos isso somente de SQL, agora imagine os NoSQL, onde podemos guardar QUALQUER COISA. O que um cientista de dados entrega de valor tendo que lidar com esse tanto de complexidade?
O valor que este entrega são insights que terá nos dados, não em como otimizar a manipulação destes.

Agora, um verdadeiro entregável na área de engenharia de dados estão na otimização do fluxo de dados e na sua manipulação. Podemos falar que seria como um *DevOps* dos dados.
E é nisso que quero chegar como o menor componente entregável de um "Data Mesh".

## Pipeline de dados
Quem já trabalhou com DevOps está familiarizado com o conceito de Pipeline CI/CD. O principal objetivo de uma Pipeline é
automatizar etapas de trabalho para um determinado processo, como no caso, o processo de Integração Contínua e Entrega Contínua: o famoso *deploy*.

O objetivo principal de uma pipeline de dados é automatizar o fluxo de dados no contexto de uma organização. Como os dados estarão disponíveis
a estas com o objetivo de poder tirar vantagem em um ambiente extremamente competitivo? Com um processo automatizado e otimizado com a velocidade adequada ao fluxo destes dados.

Conhece-se o processo de ETL como *Extract, Transform and Load*: Extrair, Transformar e Carregar. E sim, é o exemplo de etapas de uma Pipeline de Dados.

![ETL](https://www.sas.com/pt_br/insights/data-management/o-que-e-etl/_jcr_content/par/styledcontainer_bb5a/par/styledcontainer_6014/par/image_b840.img.png/1533588841097.png)
*Fonte: [SAS](https://www.sas.com/pt_br/insights/data-management/o-que-e-etl.html)*

### Extrair
É o processo de extração dos dados brutos que iremos retirar da origem, podendo ser um banco de dados, rede social, sensores e dentre outros. Todo sistema tem, ou deveria ter, um *escapamento* aos dados com relação ao seu funcionamento e ações tomadas
dentro destes. Geralmente, estes dados são carregados dentro de uma área de staging, como se fosse um *parquinho* dos engenheiros de dados para poder manipular os dados.

### Transformar
É o processo de transformar os dados brutos, que estão muitas vezes em formatos não legíveis para análises, em dados refinados e prontos para uso.
São dados que podem muitas vezes serem *parseados* ou *agregados*, para facilitar a manipulação e retirar métricas com base categórica.

### Carregar
Estes dados transformados precisam ser carregados em uma base onde os cientistas, analistas e engenheiros podem consultar os dados para serem trabalhados por eles.
Tem-se uma infinidade de bancos de dados, basta pegar o que faz mais sentido ao negócio da organização.

Bem, entendido estes conceitos, vocês devem estar se perguntando, ou pelo menos com este monólogo na cabeça...

> *Você passou 15 minutos explicando TUDO, menos Data Mesh. O que diabéisso e qual problema que ele resolve??????*

Vamos pra isso então.

## Data Mesh

É uma proposta arquitetural de um projeto de dados que foca da descentralização da
área de dados de uma organização em múltiplas áreas de domínios. Este modelo visa em tentar fazer o mesmo que temos com
DevOps: desburocratizar o processo de automação do fluxo de trabalho dos profissionais de dados.

Um grande problema que enfrentamos na área de TI como um todo são os chamados *silos*. E o que é um silo?
Vou falar de uma forma que é simples e não deixa de ser verdade:

> *Silo, na área de Tecnologia da Informação, é a burocratização do fluxo de trabalho*.

Vou mostrar um diálogo bastante comum na nossa área e, principalmente, se você já chegou a trabalhar com áreas bastante burocráticas. Se você não chegou a trabalhar
nisso ainda, preste atenção, pois quando ouvir algo similar, isso deve soar como alerta vermelho:

> *Juliana trabalha em uma grande empresa de tecnologia na equipe de dados. Ela é gigante, onde assume todo o trabalho que tem dados envolvidos. Toda a infraestrutura como
> as pipelines de dados, eles são os guardiões e a vanguarda dos insights, risos.*
>
> *Como funciona o trabalho da equipe de Juliana? Simples. Todas as vezes que você quiser disponibilizar os seus dados brutos para serem formatados ao seu gosto, basta mandar um
> chamado para a equipe que eles irão atendê-lo. Mas certifique-se que os dados estejam formatados préviamente em um tipo de formato já suportado, para facilitar o trabalho
> de todos, não? Nós sabemos que não funciona assim. Caso você tenha dados em um formato não especificado, isso acaba virando uma nova feature para implementar o fluxo de ETL.*
>
> *Temos as histórias de usuários sobre as demandas que estes requerem da equipe. Qual é o contexto e domínio do demandante? O que seriam estes dados? O que extrair? Estes dados vão ser disponibilizados em Data Lake
> ou vai pro Data Warehouse? É em tempo real ou podemos fazer processamento em batch? Quem vai precisar de acessar esses dados e quais áreas podem fazer uso disto?*
>
> *Além disso, Juliana vai ter que se preocupar com a disponibilização de todos os dados. Se uma pipeline ETL precisa ser inserida, todos os componentes da infraestrutura tem de ser alterados para suportar
> a nova feature, ou talvez seja necessário reiniciá-los. Ela sai à copa para tomar um café e percebe que está com uma bomba relógio em suas mãos.*

Grande parte das pessoas não são gerentes, mas este exemplo certamente pode ser familiar. Você tem um setor gigantesco responsável por tudo e todos. Você fica responsável pelos produtos de outras
equipes e ainda é culpado pela ineficiência do processo. E vamos olhar o lado do cliente: promessas não cumpridas de uma área que vendeu uma solução de dados que potencialmente alavancaria os seus serviços à organização
e aos clientes externos.

Com tudo isso, some a falta do *ownership* de seus dados e também há a desautorização de implementar as suas próprias soluções frente a burocracia, **fica extremamente frustrante a situação**. O que poderia dar errado? Se você não entendeu o ponto até agora, sugiro que leia um livro chamado [O Projeto Fênix (The Phoenix Project)](https://www.amazon.com.br/projeto-f%C3%AAnix-comemorativa-romance-neg%C3%B3cio/dp/8550814067/ref=sr_1_3?dchild=1&qid=1623593261&refinements=p_27%3AGene+Kim&s=books&sr=1-3)
escrito por Gene Kim, Kevin Behr e George Spafford (tem o [The Unicorn Project](https://www.amazon.com/Unicorn-Project-Developers-Disruption-Thriving-ebook/dp/B07QT9QR41), a versão *canon* do livro que é bem mais atual, mas só achei em inglês, caso tenham interesse).

![Book](https://m.media-amazon.com/images/P/B08S6PY4ZM.01._SCLZZZZZZZ_SX500_.jpg)
*Fonte: [Amazon](https://www.amazon.com.br/projeto-f%C3%AAnix-comemorativa-romance-neg%C3%B3cio/dp/8550814067/ref=sr_1_3?dchild=1&qid=1623593261&refinements=p_27%3AGene+Kim&s=books&sr=1-3)*

A grande proposta desta arquitetura é a quebra dos silos. E eu mostro rapidamente uma comparação de arquiteturas de dados já conhecidas no mercado com relação a esta.

### Proposta de quebra dos silos: áreas de domínio e plataforma

A questão é a seguinte: diferentes áreas da TI, com suas operações e serviços, emitem dados que podem ser úteis à
organização, oferecendo valiosíssimos insights. A única barreira que impede isso é a burocratização que leva a falta de comunicação,
quebra de expectativas e afins. Ao invés disso, por que a equipe não poder lidar diretamente com os próprios dados e disponibilizar da forma que convém aos seus clientes?

Porque também devemos nos perguntar: quem tem maior domínio dos dados? Não seria a área de domínio destes dados? É essa também a importância da multidisciplinaridade
das equipes, trazendo múltiplos pontos de vistas que podem somar em nosso trabalho!

Eu vou admitir, esta parte em que falo de Data Mesh é bastante influenciada por um artigo que li no blog do Martin Fowler *[How to Move Beyond a Monolithic Data Lake to a Distributed Data Mesh](https://martinfowler.com/articles/data-monolith-to-mesh.html)*
escrito por Zhamak Dehghani. Não há muito tempo em que este conceito apareceu, graças a ela, fazendo com que este modelo seja recomendado pela ThoughtWorks em seu [Technology Radar](https://www.thoughtworks.com/radar/techniques/data-mesh).
Vou pegar emprestado alguns diagramas que ela fez a respeito das problemáticas da não adoção desta arquitetura e da adoção da mesma no artigo escrito por ela.

![Plataforma de dados centralizada](https://martinfowler.com/articles/data-monolith-to-mesh/no-domain-data-platform.png)
Veja que uma equipe é responsável por dados de TODOS os domínios que emitem dados e que querem trabalhar com eles.
A não quebra de domínios leva com que a área demore para reagir as mudanças da organização. Há novas features a serem trabalhadas. Novas fontes de dados surgem a cada instante e novos consumidores estão ai querendo uma fatia do bolo.

![ETL](https://martinfowler.com/articles/data-monolith-to-mesh/functional-decomposition.png)
Este silo gigante oferece um produto que é, básicamente falando, uma pipeline de dados, ou ETL, enfim. O interessante é que
não se permite outro tipo de produto a não ser isso, pois quem define as regras é a própria plataforma. Se você tiver tipos
de dados que você só vai poder conseguir entregar se a plataforma criar um Socket Server para receber isso? Boa sorte, sua
feature vai estar no final de um Backlog cheio de débito técnico, issues a serem resolvidas, won't do e won't fix e ~~sonhos de
dominação mundial de outros clientes~~.

![Equipes](https://martinfowler.com/articles/data-monolith-to-mesh/siloed-teams.png)
O problema está nisso, tem uma equipe hyper especializada em dados, fechada em seu próprio mundo ditando regras para plataforma.
Nesta equipe, é quase impossível empatizar com todos os clientes, pois são centenas de áreas que querem receber insights de seus dados.
Cada qual com sua necessidade.

A proposta para resolver isso seria implementando uma Data Mesh.

![Data Mesh](https://martinfowler.com/articles/data-monolith-to-mesh/data-mesh.png)
Cada equipe, dona de sua origem, é dona de seu próprio fluxo de trabalho. A pipeline está livre de intervenção alheia. E a equipe
de Engenharia de Dados está desafogada para poder trabalhar e entregar o seu valor à organização! O único acoplamento criado é a infraestrutura
que a Engenharia de Dados irá prover aos domínios, mas estes não gerenciarão mais os dados.

Observem que os domínios se conversam, podendo puxar insights dos dados de outros domínios ou até mesmo criando-os correlacionados entre sí.
E a equipe destes domínios são compostas por membros multidisciplinares, até mesmo tendo os engenheiros de dados para trabalhar com estes e implementar
as pipelines!

Para finalizar, pois este artigo tá muito longo (perdão), quero falar de outros modelos que eu pesquisei de
arquitetura.

## Arquiteturas alternativas: Lambda e Kappa

Eu devo salientar de que eu não sou a pessoa mais experiente da mesa para trazer assuntos de arquitetura,
por isso eu me baseio muito em estudo e experimentos que faço. Mas devo dizer que sou uma pessoa multidisciplinar,
pois eu também sou desenvolvedor de software e também trabalhei como DevOps. 

Existe um conceito em DevOps chamado *Service Mesh*, que é uma camada na infraestrutura que suporta os microsserviços, que é um modelo arquitetural de quebra de silos das aplicações.
E a proposta da Service Mesh e adicionar propriedades a arquitetura importantes que possibilitam as operações da organização de escalarem. Recomendo a leitura dos artigos
da [Red Hat](https://www.redhat.com/en/topics/microservices/what-is-a-service-mesh), [Nginx](https://www.nginx.com/blog/what-is-a-service-mesh/)
e [Istio](https://istio.io/latest/about/service-mesh/).

Todos os conceitos são baseados em uma arquitetura de microsserviços, que não é exatamente o que uma arquitetura Lambda e Kappa oferecem.
Ambos são diferentes apenas no quesito de processamento. Na arquitetura Lambda, é uma pipeline de dados que separa o processamento batch e streaming em dois
componentes diferentes, aumentando a carga cognitiva com relação a arquitetura do sistema. Já na arquitetura Kappa, podemos utilizar um componente de processamento
híbrido para processar ambos os dados.

Recomendo a leitura da [arquitetura Kappa](http://milinda.pathirage.org/kappa-architecture.com/) e a [Lambda](https://en.wikipedia.org/wiki/Lambda_architecture). Estas duas arquiteturas, apesar de resolverem problemas, óbviamente, não resolvem o problema de acoplamento e silos que o
data mesh propõe resolver.

## O projeto ambicioso

Eu não sei quantos posts esse projeto irá necessitar para ser esclarecido em quesito de implementação, mas nada será baseado em achismo. Como em metodologia científica, vamos usar as seguintes etapas:

1. Observação
2. Elaboração do problemas
3. Hipóteses
4. Experimentos
5. Análise
6. Conclusão

E prometo que:

- Explicarei vários componentes que iremos usar e quais problemas eles resolvem;
- Benchmark destes componentes serão feitos;
- Vai ter código para ser implementado;
- Vai ter infraestrutura para colocar de pé;
- Só será utilizado componente Open-Source.

## Conclusão

Eu sei que o post foi longo e eu agradeço muito por você ter chegado ao final! Se você chegou ao fim, por favor,
deem o seu feedback a respeito deste post. Podem encontrar os meus contatos pelo meu próprio blog.

A respeito do projeto, a próxima etapa será de definição do que iremos fazer de implementação prática e começaremos com
a ingestão dos dados.

Espero que vocês gostem dessa série assim como estou gostando de escrever a respeito. Até a próxima! ;)


