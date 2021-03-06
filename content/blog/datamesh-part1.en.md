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
*Fonte: [Wikip??dia](https://en.wikipedia.org/wiki/Big_data#/media/File:Big_Data.png)*

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
?? o processo de extra????o dos dados brutos que iremos retirar da origem, podendo ser um banco de dados, rede social, sensores e dentre outros. Todo sistema tem, ou deveria ter, um *escapamento* aos dados com rela????o ao seu funcionamento e a????es tomadas
dentro destes. Geralmente, estes dados s??o carregados dentro de uma ??rea de staging, como se fosse um *parquinho* dos engenheiros de dados para poder manipular os dados.

### Transformar
?? o processo de transformar os dados brutos, que est??o muitas vezes em formatos n??o leg??veis para an??lises, em dados refinados e prontos para uso.
S??o dados que podem muitas vezes serem *parseados* ou *agregados*, para facilitar a manipula????o e retirar m??tricas com base categ??rica.

### Carregar
Estes dados transformados precisam ser carregados em uma base onde os cientistas, analistas e engenheiros podem consultar os dados para serem trabalhados por eles.
Tem-se uma infinidade de bancos de dados, basta pegar o que faz mais sentido ao neg??cio da organiza????o.

Bem, entendido estes conceitos, voc??s devem estar se perguntando, ou pelo menos com este mon??logo na cabe??a...

> *Voc?? passou 15 minutos explicando TUDO, menos Data Mesh. O que diab??isso e qual problema que ele resolve??????*

Vamos pra isso ent??o.

## Data Mesh

?? uma proposta arquitetural de um projeto de dados que foca da descentraliza????o da
??rea de dados de uma organiza????o em m??ltiplas ??reas de dom??nios. Este modelo visa em tentar fazer o mesmo que temos com
DevOps: desburocratizar o processo de automa????o do fluxo de trabalho dos profissionais de dados.

Um grande problema que enfrentamos na ??rea de TI como um todo s??o os chamados *silos*. E o que ?? um silo?
Vou falar de uma forma que ?? simples e n??o deixa de ser verdade:

> *Silo, na ??rea de Tecnologia da Informa????o, ?? a burocratiza????o do fluxo de trabalho*.

Vou mostrar um di??logo bastante comum na nossa ??rea e, principalmente, se voc?? j?? chegou a trabalhar com ??reas bastante burocr??ticas. Se voc?? n??o chegou a trabalhar
nisso ainda, preste aten????o, pois quando ouvir algo similar, isso deve soar como alerta vermelho:

> *Juliana trabalha em uma grande empresa de tecnologia na equipe de dados. Ela ?? gigante, onde assume todo o trabalho que tem dados envolvidos. Toda a infraestrutura como
> as pipelines de dados, eles s??o os guardi??es e a vanguarda dos insights, risos.*
>
> *Como funciona o trabalho da equipe de Juliana? Simples. Todas as vezes que voc?? quiser disponibilizar os seus dados brutos para serem formatados ao seu gosto, basta mandar um
> chamado para a equipe que eles ir??o atend??-lo. Mas certifique-se que os dados estejam formatados pr??viamente em um tipo de formato j?? suportado, para facilitar o trabalho
> de todos, n??o? N??s sabemos que n??o funciona assim. Caso voc?? tenha dados em um formato n??o especificado, isso acaba virando uma nova feature para implementar o fluxo de ETL.*
>
> *Temos as hist??rias de usu??rios sobre as demandas que estes requerem da equipe. Qual ?? o contexto e dom??nio do demandante? O que seriam estes dados? O que extrair? Estes dados v??o ser disponibilizados em Data Lake
> ou vai pro Data Warehouse? ?? em tempo real ou podemos fazer processamento em batch? Quem vai precisar de acessar esses dados e quais ??reas podem fazer uso disto?*
>
> *Al??m disso, Juliana vai ter que se preocupar com a disponibiliza????o de todos os dados. Se uma pipeline ETL precisa ser inserida, todos os componentes da infraestrutura tem de ser alterados para suportar
> a nova feature, ou talvez seja necess??rio reinici??-los. Ela sai ?? copa para tomar um caf?? e percebe que est?? com uma bomba rel??gio em suas m??os.*

Grande parte das pessoas n??o s??o gerentes, mas este exemplo certamente pode ser familiar. Voc?? tem um setor gigantesco respons??vel por tudo e todos. Voc?? fica respons??vel pelos produtos de outras
equipes e ainda ?? culpado pela inefici??ncia do processo. E vamos olhar o lado do cliente: promessas n??o cumpridas de uma ??rea que vendeu uma solu????o de dados que potencialmente alavancaria os seus servi??os ?? organiza????o
e aos clientes externos.

Com tudo isso, some a falta do *ownership* de seus dados e tamb??m h?? a desautoriza????o de implementar as suas pr??prias solu????es frente a burocracia, **fica extremamente frustrante a situa????o**. O que poderia dar errado? Se voc?? n??o entendeu o ponto at?? agora, sugiro que leia um livro chamado [O Projeto F??nix (The Phoenix Project)](https://www.amazon.com.br/projeto-f%C3%AAnix-comemorativa-romance-neg%C3%B3cio/dp/8550814067/ref=sr_1_3?dchild=1&qid=1623593261&refinements=p_27%3AGene+Kim&s=books&sr=1-3)
escrito por Gene Kim, Kevin Behr e George Spafford (tem o [The Unicorn Project](https://www.amazon.com/Unicorn-Project-Developers-Disruption-Thriving-ebook/dp/B07QT9QR41), a vers??o *canon* do livro que ?? bem mais atual, mas s?? achei em ingl??s, caso tenham interesse).

![Book](https://m.media-amazon.com/images/P/B08S6PY4ZM.01._SCLZZZZZZZ_SX500_.jpg)
*Fonte: [Amazon](https://www.amazon.com.br/projeto-f%C3%AAnix-comemorativa-romance-neg%C3%B3cio/dp/8550814067/ref=sr_1_3?dchild=1&qid=1623593261&refinements=p_27%3AGene+Kim&s=books&sr=1-3)*

A grande proposta desta arquitetura ?? a quebra dos silos. E eu mostro rapidamente uma compara????o de arquiteturas de dados j?? conhecidas no mercado com rela????o a esta.

### Proposta de quebra dos silos: ??reas de dom??nio e plataforma

A quest??o ?? a seguinte: diferentes ??reas da TI, com suas opera????es e servi??os, emitem dados que podem ser ??teis ??
organiza????o, oferecendo valios??ssimos insights. A ??nica barreira que impede isso ?? a burocratiza????o que leva a falta de comunica????o,
quebra de expectativas e afins. Ao inv??s disso, por que a equipe n??o poder lidar diretamente com os pr??prios dados e disponibilizar da forma que conv??m aos seus clientes?

Porque tamb??m devemos nos perguntar: quem tem maior dom??nio dos dados? N??o seria a ??rea de dom??nio destes dados? ?? essa tamb??m a import??ncia da multidisciplinaridade
das equipes, trazendo m??ltiplos pontos de vistas que podem somar em nosso trabalho!

Eu vou admitir, esta parte em que falo de Data Mesh ?? bastante influenciada por um artigo que li no blog do Martin Fowler *[How to Move Beyond a Monolithic Data Lake to a Distributed Data Mesh](https://martinfowler.com/articles/data-monolith-to-mesh.html)*
escrito por Zhamak Dehghani. N??o h?? muito tempo em que este conceito apareceu, gra??as a ela, fazendo com que este modelo seja recomendado pela ThoughtWorks em seu [Technology Radar](https://www.thoughtworks.com/radar/techniques/data-mesh).
Vou pegar emprestado alguns diagramas que ela fez a respeito das problem??ticas da n??o ado????o desta arquitetura e da ado????o da mesma no artigo escrito por ela.

![Plataforma de dados centralizada](https://martinfowler.com/articles/data-monolith-to-mesh/no-domain-data-platform.png)
Veja que uma equipe ?? respons??vel por dados de TODOS os dom??nios que emitem dados e que querem trabalhar com eles.
A n??o quebra de dom??nios leva com que a ??rea demore para reagir as mudan??as da organiza????o. H?? novas features a serem trabalhadas. Novas fontes de dados surgem a cada instante e novos consumidores est??o ai querendo uma fatia do bolo.

![ETL](https://martinfowler.com/articles/data-monolith-to-mesh/functional-decomposition.png)
Este silo gigante oferece um produto que ??, b??sicamente falando, uma pipeline de dados, ou ETL, enfim. O interessante ?? que
n??o se permite outro tipo de produto a n??o ser isso, pois quem define as regras ?? a pr??pria plataforma. Se voc?? tiver tipos
de dados que voc?? s?? vai poder conseguir entregar se a plataforma criar um Socket Server para receber isso? Boa sorte, sua
feature vai estar no final de um Backlog cheio de d??bito t??cnico, issues a serem resolvidas, won't do e won't fix e ~~sonhos de
domina????o mundial de outros clientes~~.

![Equipes](https://martinfowler.com/articles/data-monolith-to-mesh/siloed-teams.png)
O problema est?? nisso, tem uma equipe hyper especializada em dados, fechada em seu pr??prio mundo ditando regras para plataforma.
Nesta equipe, ?? quase imposs??vel empatizar com todos os clientes, pois s??o centenas de ??reas que querem receber insights de seus dados.
Cada qual com sua necessidade.

A proposta para resolver isso seria implementando uma Data Mesh.

![Data Mesh](https://martinfowler.com/articles/data-monolith-to-mesh/data-mesh.png)
Cada equipe, dona de sua origem, ?? dona de seu pr??prio fluxo de trabalho. A pipeline est?? livre de interven????o alheia. E a equipe
de Engenharia de Dados est?? desafogada para poder trabalhar e entregar o seu valor ?? organiza????o! O ??nico acoplamento criado ?? a infraestrutura
que a Engenharia de Dados ir?? prover aos dom??nios, mas estes n??o gerenciar??o mais os dados.

Observem que os dom??nios se conversam, podendo puxar insights dos dados de outros dom??nios ou at?? mesmo criando-os correlacionados entre s??.
E a equipe destes dom??nios s??o compostas por membros multidisciplinares, at?? mesmo tendo os engenheiros de dados para trabalhar com estes e implementar
as pipelines!

Para finalizar, pois este artigo t?? muito longo (perd??o), quero falar de outros modelos que eu pesquisei de
arquitetura.

## Arquiteturas alternativas: Lambda e Kappa

Eu devo salientar de que eu n??o sou a pessoa mais experiente da mesa para trazer assuntos de arquitetura,
por isso eu me baseio muito em estudo e experimentos que fa??o. Mas devo dizer que sou uma pessoa multidisciplinar,
pois eu tamb??m sou desenvolvedor de software e tamb??m trabalhei como DevOps. 

Existe um conceito em DevOps chamado *Service Mesh*, que ?? uma camada na infraestrutura que suporta os microsservi??os, que ?? um modelo arquitetural de quebra de silos das aplica????es.
E a proposta da Service Mesh e adicionar propriedades a arquitetura importantes que possibilitam as opera????es da organiza????o de escalarem. Recomendo a leitura dos artigos
da [Red Hat](https://www.redhat.com/en/topics/microservices/what-is-a-service-mesh), [Nginx](https://www.nginx.com/blog/what-is-a-service-mesh/)
e [Istio](https://istio.io/latest/about/service-mesh/).

Todos os conceitos s??o baseados em uma arquitetura de microsservi??os, que n??o ?? exatamente o que uma arquitetura Lambda e Kappa oferecem.
Ambos s??o diferentes apenas no quesito de processamento. Na arquitetura Lambda, ?? uma pipeline de dados que separa o processamento batch e streaming em dois
componentes diferentes, aumentando a carga cognitiva com rela????o a arquitetura do sistema. J?? na arquitetura Kappa, podemos utilizar um componente de processamento
h??brido para processar ambos os dados.

Recomendo a leitura da [arquitetura Kappa](http://milinda.pathirage.org/kappa-architecture.com/) e a [Lambda](https://en.wikipedia.org/wiki/Lambda_architecture). Estas duas arquiteturas, apesar de resolverem problemas, ??bviamente, n??o resolvem o problema de acoplamento e silos que o
data mesh prop??e resolver.

## O projeto ambicioso

Eu n??o sei quantos posts esse projeto ir?? necessitar para ser esclarecido em quesito de implementa????o, mas nada ser?? baseado em achismo. Como em metodologia cient??fica, vamos usar as seguintes etapas:

1. Observa????o
2. Elabora????o do problemas
3. Hip??teses
4. Experimentos
5. An??lise
6. Conclus??o

E prometo que:

- Explicarei v??rios componentes que iremos usar e quais problemas eles resolvem;
- Benchmark destes componentes ser??o feitos;
- Vai ter c??digo para ser implementado;
- Vai ter infraestrutura para colocar de p??;
- S?? ser?? utilizado componente Open-Source.

## Conclus??o

Eu sei que o post foi longo e eu agrade??o muito por voc?? ter chegado ao final! Se voc?? chegou ao fim, por favor,
deem o seu feedback a respeito deste post. Podem encontrar os meus contatos pelo meu pr??prio blog.

A respeito do projeto, a pr??xima etapa ser?? de defini????o do que iremos fazer de implementa????o pr??tica e come??aremos com
a ingest??o dos dados.

Espero que voc??s gostem dessa s??rie assim como estou gostando de escrever a respeito. At?? a pr??xima! ;)


