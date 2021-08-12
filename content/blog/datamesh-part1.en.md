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

As well, there was a need to automate the way we identify patterns in our data without human intervention, so then we have **machine learning**. All of this fields are strongly related to data.
Even the data intake, storage and aggregation became so complex that it was needed to separate these processes into a separate field, which is data engineering. But before we talk about it, let's talk about the main reason why
we needed to separate it from the others in the first place: **big data**.

## Big Data

It's a study topic that's pretty much recent when compared to computer science in general, and it deals with high complexity data in, generally, 3 aspects (it's what we call the 3 Vs from Big Data):
![Diagrama dos 3Vs do Big Data](https://upload.wikimedia.org/wikipedia/commons/e/ee/Big_Data.png)
*Fonte: [Wikipédia](https://en.wikipedia.org/wiki/Big_data#/media/File:Big_Data.png)*

### Volume 
This Big Data's feature is about the huge volume that data can traffic through our networks or pipelines.

I guess we can recall that time when we used to think that *gigabytes* was a measurement of huge amount of data, specially when we had our HDDs with 250GB at best. This is no longer the norm, we are already at the *terabytes* realm and we want more!
Also, we can no longer say this feature is all about the storage size, but with it's speed as well. We already know that in the internet, there's about 100k *petabytes* being moved around per year and growing.

### Velocity
This feature is about the speed that data can traffic.

I explained before that since the beginning, we'd dealt with past data to support the organization's decision making. Now, with the whole world connected through the internet, everything
got faster. We can communicate faster and interact faster, so why doesn't organizations do the same when we apply this train of thought to their processes and data? We have much more
input than ever, and it's the beginning, since the IOT is starting to rise, so we'll have much more data incoming and being generated not only by we, the humans, but by devices.

### Variety
This feature is about the different kinds of data that we can handle.

Take a moment to appreciate the fact that, nowadays, there are some of our friendships that we communicate through memes. Yes, you read that right, through memes. This is something that wasn't
possible 20 years ago, and some might even eye-roll this fact and ask what's the point. It's not about the memes. We are using images and other kinds of data to communicate to our peers.
If we can extract value from text data, why can't we extract some insights from images, sounds, or blog posts? What if we could analyze and extract insights of them altogether?

Can you note the fact that data handling became a complex task to be dealt with nowadays? There's no way we could use traditional data analysis or handling from 20/30 years ago to the same
data ecosystem that we have nowadays. This is why the data mungling task is no longer the *obligation* of a data scientist, but in fact, to a data engineer. So let's talk about the data engineering.


## Data Engineering
It's a multidisciplinary topic that is about data and its infrastructure handling. The data, in this context, may be considered Big Data or not, but the concept applies to both ways.
We have multiple topics involved in the Data Engineering context:

- Distributed Computing: it's a distributed system's study area that regards the processes, tools and techniques applied to computing with multiple devices.
- Computer Netwroking: it's a study area of computing communication through all contexts.

There may be other areas related to it, but the fact is that, in the data context, all of them overlap and form what we understand as Data Engineering, which its purpose is to
study techniques and tools to handle and manipulate data.

Before all of this came to be what it is, a data scientist had to download raw data, or at best, download its sample to work on. Then, needed to load this data to clean, format, store this new
data into a database or such. AND then, it could make the analysis, IF, the data is structured. If the data is unstructured, you need to handle the datalake and extract data from text files, images, sounds, etc.

So let me ask you, kind reader: which value does a Data Scientist brings to the table in all of these processes?
The purpose of all of this ordeal is to extract insights from data in order to enable decision makers in an organization to take action upon it. Not only organizations, but ANYTHING
that's data-driven is supposed to have benefits over this. The process of handling the data and its infrastructure is not the most valuable asset of a data scientist, but the analysis to extract the insights in the data.

The main asset of a data engineer is the optimization of both data flow and handling, which is an important role as well as of a data scientist. Without the engineers, we'd not
have the infrastructure optimization to handle big data in any way, both storage or handling it (cleaning, parsing, filtering, etc). We can understand this concept as if it's like
*DevOps* applied to data. With everything regarding the theoretical aspect out of our way, we might be able to start talking about Data Mesh. Not there yet, we need to know
what a Data Pipeline is.

## Data Pipelining
You might be familiar with the CI/CD pipelines, if you ever worked with DevOps concepts along your career. The main purpose of the pipeline is to automate processes and tasks
regarding one's activities. So, intuitively, what's the main purpose of a data pipeline? Automate the data flow through the source to it's destination and make it ready for usage.

What are the steps for a data pipeline? Well, the main one is the ETL steps, which consists of Extract, Transform and Load.

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


