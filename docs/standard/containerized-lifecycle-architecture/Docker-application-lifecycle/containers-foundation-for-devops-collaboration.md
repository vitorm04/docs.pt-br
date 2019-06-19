---
title: Contêineres de base para colaboração de DevOps
description: Entenda o papel fundamental dos contêineres para simplificar DevOps.
ms.date: 02/15/2019
ms.openlocfilehash: 37faf00f270414df363f36894317f31f81a2937e
ms.sourcegitcommit: 5bc85ad81d96b8dc2a90ce53bada475ee5662c44
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/13/2019
ms.locfileid: "65641301"
---
# <a name="containers-as-the-foundation-for-devops-collaboration"></a>Contêineres de base para colaboração de DevOps

Pela própria natureza dos contêineres e da tecnologia do Docker, os desenvolvedores podem compartilhar o software e as dependências facilmente com as operações de TI e os ambientes de produção e, ao mesmo tempo, eliminar a desculpa comum de que "funciona no meu computador". Os contêineres resolvem conflitos de aplicativo entre ambientes diferentes. Indiretamente, os contêineres e o Docker estreitam a relação entre os desenvolvedores e as operações de TI, facilitando uma colaboração eficiente. Adotar o fluxo de trabalho de contêiner oferece a vários clientes a continuidade de DevOps que eles buscam, mas tiveram que implantar anteriormente por meio de uma configuração mais complexa para versão e pipelines de build. Os contêineres simplificam os pipelines de build/teste/implantação no DevOps.

![O Docker ajuda a criar pontes entre o desenvolvedor e os arquitetos na carga de trabalho de desenvolvimento/design e as operações de TI na carga de trabalho de execução/monitoramento/gerenciamento](./media/image1.png)

**Figura 2-1.** Principais cargas de trabalho por "persona" no ciclo de vida dos aplicativos do Docker em contêineres

Com os contêineres do Docker, os desenvolvedores são os proprietários dos elementos do contêiner (aplicativo, serviço, dependências, estruturas e componentes) e são responsáveis pela maneira como os contêineres e os serviços se comportam juntos como um aplicativo composto por uma coleção de serviços. As interdependências de vários contêineres são definidas em um arquivo `docker-compose.yml` ou o que poderia ser chamado de *manifesto de implantação*. Enquanto isso, as equipes de operações de TI (profissionais e gerenciamento de TI) podem se concentrar no gerenciamento dos ambientes de produção, na infraestrutura, na escalabilidade, no monitoramento. Por fim, podem garantir que os aplicativos estão sendo entregues corretamente para os usuários finais sem precisar saber o conteúdo dos vários contêineres. Por isso o nome "contêiner", o que lembra a analogia com os contêineres de transporte da vida real. Dessa maneira, os proprietários do conteúdo do contêiner não precisam se preocupar com o modo de envio dele, e a transportadora conduz o contêiner do ponto de origem ao destino sem saber ou se preocupar com o conteúdo. De maneira semelhante, os desenvolvedores podem criar e serem proprietários do conteúdo de um contêiner do Docker sem precisar se preocupar com os mecanismos de "transporte".

No pilar do lado esquerdo da Figura 2-1, os desenvolvedores escrevem e executam código localmente nos contêineres do Docker for Windows ou Mac. Eles definem o ambiente operacional do código usando um Dockerfile que configura o sistema operacional de base para executar, bem como as etapas de build para criar o código em uma imagem do Docker. Os desenvolvedores definem como uma ou mais imagens interoperarão usando o arquivo `docker-compose.yml` do manifesto de implantação já mencionado. Conforme o desenvolvimento local é concluído, eles efetuam push do código do aplicativo e dos arquivos de configuração do Docker para o repositório de código escolhido (ou seja, o repositório do Git).

O pilar de DevOps define o build – pipelines de CI (integração contínua) usando o Dockerfile fornecido no repositório de código. O sistema de CI efetua pull das imagens de contêiner de base do Registro do Docker selecionado e cria as imagens personalizadas do Docker para o aplicativo. Em seguida, as imagens são validadas e efetua-se o push delas para o Registro do Docker usado para as implantações em vários ambientes.

No pilar à direita, as equipes de operações gerenciam os aplicativos e a infraestrutura implantados na produção e monitoram o ambiente e os aplicativos. Desse modo, é possível oferecer feedback e insights à equipe de desenvolvimento sobre como o aplicativo pode ser aprimorado. Os aplicativos de contêiner são normalmente executados na produção por meio de orquestradores de contêineres.

Ambas as equipes colaboram por meio de uma plataforma fundamental (os contêineres do Docker) que oferece a separação de preocupações como um contrato, além de melhorar muito a colaboração entre as duas equipes no ciclo de vida do aplicativo. Os desenvolvedores são proprietários do conteúdo do contêiner, do ambiente operacional e das interdependências do contêiner, ao passo que as equipes de operações usam as imagens criadas junto com o manifesto e as executam no sistema de orquestração.

## <a name="challenges-in-application-life-cycle-when-using-docker"></a>Desafios no ciclo de vida do aplicativo ao usar o Docker.

Há muitos motivos que aumentarão o número de aplicativos em contêiner nos próximos anos. Um deles é a criação de aplicativos baseados em microsserviços.

Durante os últimos 15 anos, o uso dos serviços Web foram a base de milhares de aplicativos. Provavelmente, após alguns anos, veremos a mesma situação com os aplicativos baseados em microsserviços em execução nos contêineres do Docker.

Também vale a pena mencionar que é possível usar os contêineres do Docker para aplicativos monolíticos e ainda aproveitar todos os benefícios do Docker. Os contêineres não usam só os microsserviços.

O uso dos contêineres do Docker e dos microsserviços gera novos desafios no processo de desenvolvimento das organizações. Portanto, é necessária uma sólida estratégia para manter vários contêineres e microsserviços em execução nos sistemas de produção. Por fim, os aplicativos empresariais terão centenas ou milhares de contêineres/instâncias em execução na produção.

Esses desafios criam demandas ao usar ferramentas de DevOps. Assim, será necessário definir novos processos nas atividades de DevOps e encontrar respostas para estes tipos de perguntas:

- Quais ferramentas podem ser usadas para desenvolvimento, CI/CD, gerenciamento e operações?

- Como minha empresa pode gerenciar erros nos contêineres ao executar na produção?

- Como alterar partes do software na produção com um tempo de inatividade mínimo?

- Como dimensionar e monitorar o sistema de produção?

- Como incluir teste e implantação de contêineres no pipeline de lançamento?

- Como usar ferramentas/plataformas open-source para contêineres no Microsoft Azure?

Se você conseguir responder a todas essas perguntas, estará mais bem preparado para migrar seus aplicativos (existentes ou novos) para os contêineres do Docker. 

## <a name="introduction-to-a-generic-end-to-end-docker-application-life-cycle-workflow"></a>Introdução a um fluxo de trabalho genérico de ponta a ponta do ciclo de vida do aplicativo do Docker

A Figura 2-2 apresenta um fluxo de trabalho mais detalhado do ciclo de vida de um aplicativo do Docker, concentrando-se nessa instância em atividades e ativos específicos de DevOps.

![Este diagrama mostra o "loop externo" de DevOps. Quando o código é enviado por push ao repositório, um pipeline de CI é iniciado, seguido pelo pipeline de CD, em que o aplicativo é implantado. As métricas coletadas dos aplicativos implantados são fornecidas para a carga de trabalho de desenvolvimento, na qual ocorre o "loop interno", para que as equipes de desenvolvimento tenham dados reais para responder às necessidades de negócios e dos usuários.](./media/image2.png)

**Figura 2-2**. Fluxo de trabalho de alto nível para o ciclo de vida do aplicativo em contêineres do Docker

Tudo começa com o desenvolvedor, que inicia a escrita do código no fluxo de trabalho do loop interno. É no loop interno que os desenvolvedores definem tudo o que acontece antes de efetuar push do código para o repositório (por exemplo, um sistema de controle do código-fonte, como o Git). Após a confirmação, o repositório dispara a CI (integração contínua) e o restante do fluxo de trabalho.

Basicamente, o loop interno consiste em etapas normais, como "código", "execução", "teste" e "depuração", além de outras etapas necessárias imediatamente antes de executar o aplicativo localmente. Esse é o processo do desenvolvedor para executar e testar o aplicativo como um contêiner do Docker. O fluxo de trabalho do loop interno será explicado nas seções a seguir.

Ao dar um passo para trás para analisar o fluxo de trabalho de ponta a ponta, o fluxo de trabalho de DevOps é mais que uma tecnologia ou um conjunto de ferramentas: é uma mentalidade que exige evolução cultural. São as pessoas, os processos e as ferramentas adequadas para acelerar e tornar mais previsível o ciclo de vida do aplicativo. As empresas que adotam um fluxo de trabalho em contêineres normalmente reestruturam suas organizações para representar as pessoas e os processos que combinam com ele.

Praticar DevOps pode ajudar as equipes a responder mais rápido às pressões competitivas ao substituir processos manuais suscetíveis a erro pela automação, o que resulta em rastreabilidade melhor e fluxos de trabalho reproduzíveis. As organizações também podem gerenciar ambientes com mais eficiência e economizar custos com uma combinação de recursos locais e em nuvem, além de ferramentas totalmente integradas.

Ao implantar o fluxo de trabalho DevOps para aplicativos do Docker, você verá que as tecnologias do Docker estão presentes na maioria das etapas do fluxo de trabalho, do desenvolvimento ao trabalhar no loop interno (código, execução, depuração), na fase de build-teste-CI e, por fim, na implantação dos contêineres nos ambientes de preparo e produção.

A melhoria das práticas de qualidade ajuda a identificar defeitos no início do ciclo de desenvolvimento, o que reduz o custo de corrigi-los. Ao incluir o ambiente e as dependências na imagem e adotar uma filosofia de implantação da mesma imagem em vários ambientes, você promove uma disciplina de extrair as configurações específicas do ambiente, o que torna as implantações mais confiáveis.

Os dados avançados obtidos por meio de uma instrumentação eficiente (monitoramento e diagnóstico) oferecem insights sobre os problemas de desempenho e o comportamento do usuário para orientar as futuras prioridades e investimentos.

O DevOps precisa ser considerado uma jornada, não um destino. Ele deve ser implementado incrementalmente por meio dos projetos de escopo adequado, em que você pode demonstrar sucesso, aprendizado e evolução.

## <a name="benefits-of-devops-for-containerized-applications"></a>Benefícios do DevOps para aplicativos em contêineres

Confira alguns dos mais importantes benefícios oferecidos por um fluxo de trabalho sólido de DevOps:

- Proporcionar um software de melhor qualidade, mais rápido e com conformidade melhor.

- Promover melhoria e ajustes contínuos mais cedo e de maneira mais econômica.

- Aumentar a transparência e a colaboração entre os stakeholders envolvidos na entrega e na operação do software.

- Controlar os custos, usar recursos provisionados de modo mais eficiente e minimizar os riscos de segurança.

- Bom plug and play com vários investimentos existentes de DevOps, incluindo os investimentos open-source.

>[!div class="step-by-step"]
>[Anterior](index.md)
>[Próximo](../Microsoft-platform-tools-containerized-apps/index.md)
