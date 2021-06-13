---
title: Olá! Mais um reboot do blog
summary: Vou falar de como é rebootar mais um blog e de quebra ensino como criar um usando o Hugo.
publishDate: 2021-05-24
images:
  - /img/post-hello/hello.png
slug: hello-world-pt-br
tags: ["general"]
aliases: [
  "/blog/hello-world-pt-br"
]
draft: false

---

Pessoas! Estou aqui novamente, tentando manter isto daqui.

Bem, antigamente eu fiquei bastante conflitado em querer manter ou pelo menos registrar o meu conhecimento
ou o processo da aquisição do conhecimento, pois não é algo que eu almeijava, ou pelo menos não
me sentia confortável em fazê-lo. Imagine o quão assustador é estar sujeito a julgamento sobre as suas
habilidades na internet. Assustador, né não?

Bem, nem tanto.

Eu havia sido diagnosticado com depressão e afins há muitos anos atrás, demorei pelo menos 6 anos
para conseguir um tratamento adequado e humanizado. Hoje em dia, estou lidando bastante bem com tudo isso. Com
uma mentalidade mais adulta e razoável, deixando para trás uma bagagem emocional inútil e também com novas
ferramentas e pensamentos para lidar com a vida. Isso é assunto para um outro post, mas posso dizer que
me encontro em condições para começar novamente e trazer algo com a minha perspectiva, sem medo e sem ressentimentos.

## Razões em começar com isso novamente

Isso varia de pessoa pra pessoa. Não são todos que vão querer fazer blogs, se expor e trazer algo para
os outros. O meu intuito, de verdade, não está em me expor como pessoa ou ser, grosseiramente falando,
"influencer". Eu andei lendo a respeito do [Learn in Public](https://segredo.dev/aprenda-em-publico/) e como podemos aproveitar
deste conceito para aprendermos mais (obrigado pela recomendação, [Gilson](https://github.com/gilsondev)). 

Eu naturalmente gosto de estudar a respeito de TI, 
tem muita parada que eu já fiz que foi bacana e também várias coisas que eu presenciei que poderia tomar nota, 
mas pelo menos 60% se perdeu no tanto que a gente "tem por garantido" a nossa memória. E fora que é muito difícil
também descrever as coisas das quais você já fez e o que você está fazendo hoje em dia. 
Com isso, eu queria compartilhar e descarregar uma memória do que eu já fiz e o que estou fazendo hoje em dia.
E também praticar em ensinar os outros a fazerem o mesmo que eu fiz. 

Mas não se enganem. Não quero soar altruísta falando desta forma. Eu acho que o que posso
resumir quanto as minhas razões, são pelo menos:

- Aprender mais;
- Diminuir minhas fraquezas, praticando-as.

## E como eu posso fazer o mesmo?

Eu recomendo fortemente que vocês leiam a respeito do [Learn in Public](https://segredo.dev/aprenda-em-publico/), pois é o que
me motivou a seguir com isso.

A primeira coisa que vocês precisam ter em mente é no porquê vocês querem fazer isso e se apoiar nisso.
É muito fácil querer fama, dinheiro e atenção, não precisa nem de criar um blog com conteúdo sério
para fazer isso. Procure uma razão "intrisseca" do que você quer fazer.

- Você quer realmente aprender sobre os assuntos que você quer dominar?
- Você quer ajudar outras pessoas com conteúdo que você queria quando estava começando?
- Na real, faça sem pensar no porquê você quer fazer isso. Talvez você pegue o jeito da coisa.

Bem, mas uma coisa é fato. Você nunca vai saber se vai gostar se você não sentar e fazer isso 
acontecer. E para isso, vou te dar uma ajudinha! :)

## Como criar um blog usando Hugo?

Antigamente, eu estava usando o Jekyll para criar o meu blog. Inicialmente, parecia ser
uma boa, mas me incomoda usar algo que foi criado em uma linguagem e eu não ter o saco
para aprender, como Ruby. Eu não conseguia extender os projetos e também tinha bastante carência
de temas do Jekyll com relação a outras engines de páginas estáticas.

O [Hugo](https://gohugo.io/) caiu como uma luva! Eu estava começando a criar um projeto Wagtail,
que um dia irei tirar um tempo para mostrar como que se cria um projeto e afins, mas achei um pouco
overkill para criar uma página de blog e curricular. Logo, precisava de algo como o Hugo. E junto
com o tema "[colordrop](https://github.com/humrochagf/colordrop)" criado por um camarada chamado Humberto, 
ficou show de bola!

Vou mostrar como instalar e criar um blog com o tema colordrop. Eu estou usando um exemplo para Arch Linux que usa o pacman.

[Baixe](https://gohugo.io/getting-started/installing) o Hugo para sua distribuição preferida ou pro Windows:

{{< highlight console >}}
$ sudo pacman -Syu hugo
{{</highlight>}}

Depois crie o seu diretório para o blog e digite hugo. Para usar o tema "colordrop", teremos
também de importar o tema como submódulo do seu repositório.

{{< highlight console >}}
$ mkdir meu-blog 
$ git init 
$ hugo
$ git submodule add git@github.com:humrochagf/colordrop.git themes/colordrop
{{</highlight>}}

Em seu arquivo de configuração do blog, adicione o colordrop como tema.

{{< highlight yaml "hl_lines=4">}}
baseURL: https://damazio.dev/
DefaultContentLanguage: en
title: Carlos Damázio
theme: colordrop
enableRobotsTXT: true
{{< / highlight>}}

Rode o server do Hugo e veja a mágica acontecer. Acesse o http://localhost:1313.

{{< highlight console >}}
$ hugo server -D
{{< / highlight >}}

Não esqueça de importar um repositório remoto pro seu repositório local e commite tudo o que fez até agora.

{{< highlight console >}}
$ git remote add origin git@github.com:seu_username/seu_repo.git
$ git add -A
$ git commit -m "feat: initial blog structure"
$ git push origin main
{{< / highlight >}}

Pronto, você conseguiu criar um blog somente pra você! Claro, temos bastantes outras coisas
para fazer antes de você conseguir colocar isso no ar. Mas se você já quiser ir indo ver
isso, recomendo usar o [Netlify](https://app.netlify.com/).

Bem, foi bastante coisa pra uma introdução do meu blog. Mas é uma pequena amostra do que eu poderei
trazer aqui. No mais, nos vemos nos próximos posts ai! Tá vindo muita coisa boa por aqui! ;)
