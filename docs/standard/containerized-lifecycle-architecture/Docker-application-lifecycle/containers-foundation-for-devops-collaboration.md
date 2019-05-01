---
title: Contêineres de base para colaboração de DevOps
description: Entenda o papel fundamental de contêineres para simplificar operações de desenvolvimento.
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 02/15/2019
ms.openlocfilehash: 4b40837bf2b74d801b9794c88e79eb03bcd72e95
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62012200"
---
# <a name="containers-as-the-foundation-for-devops-collaboration"></a>Contêineres de base para colaboração de DevOps

Pela natureza da tecnologia do Docker e contêineres, os desenvolvedores podem compartilhar seus softwares e dependências facilmente com operações de TI e ambientes de produção enquanto elimina a desculpa típicos de "funciona no meu computador". Contêineres de resolvem conflitos de aplicativos entre ambientes diferentes. Indiretamente, contêineres e Docker reúnem desenvolvedores e operações de TI mais próximo, tornando mais fácil para que eles possam colaborar com eficiência. Adotar o fluxo de trabalho de contêiner fornece muitos clientes com a continuidade de DevOps, eles já procurado, mas anteriormente para implantar por meio de uma configuração mais complexa para lançamento e compile pipelines. Contêineres simplificam os pipelines de build/teste/implantação em DevOps.

![Docker ajuda a criar pontes entre desenvolvedores e arquitetos na carga de trabalho de design/desenvolvimento e operações de TI na carga de trabalho de execução/monitorar/gerenciar](./media/image1.png)

**Figura 2-1.** Cargas de trabalho principais por "personas" no ciclo de vida de aplicativos em contêineres do Docker

Com contêineres do Docker, os desenvolvedores próprios o que está dentro do contêiner (aplicativo e serviço e dependências para estruturas e componentes) e como os contêineres e serviços se comportam em conjunto como um aplicativo composto por uma coleção de serviços. As interdependências de vários contêineres são definidas em uma `docker-compose.yml` arquivo ou o que poderia ser chamado uma *manifesto de implantação*. Enquanto isso, as equipes de operações de TI (gerenciamento e os profissionais de TI) podem se concentrar no gerenciamento dos ambientes de produção; infraestrutura; escalabilidade; monitoramento; e, em última análise, garantindo que os aplicativos estão entregando corretamente para os usuários finais, sem precisar saber o conteúdo de vários contêineres. Portanto, o nome "container," Recuperando a analogia com contêineres de envio do mundo real. Assim, os proprietários de conteúdo do contêiner precisam não referem-se em si com como o contêiner será enviado, os envio da empresa transportes e um contêiner do seu ponto de origem para seu destino sem saber ou se preocupar sobre o conteúdo. De maneira semelhante, os desenvolvedores podem criar e possui o conteúdo dentro de um contêiner de Docker sem a necessidade de se preocupar com os mecanismos de "transporte".

No pilar no lado esquerdo da Figura 2-1, os desenvolvedores de escrever em executar o código localmente em contêineres do Docker usando o Docker para Windows ou Mac. Elas definem o ambiente operacional para o código usando um Dockerfile que especifica o sistema operacional base para executar, bem como as etapas de build para compilar seu código em uma imagem do Docker. Os desenvolvedores definem como uma ou mais imagens interoperem usando mencionados anteriormente `docker-compose.yml` manifesto de implantação do arquivo. Conforme são concluídas local de desenvolvimento, eles enviar por push seu código de aplicativo e os arquivos de configuração do Docker para o repositório de código de sua escolha (ou seja, o repositório do Git).

O pilar de DevOps define os pipelines de CI (integração) do build – contínuo usando o Dockerfile fornecido no repositório do código. O sistema de CI efetua pull das imagens de contêiner base do registro do Docker selecionado e cria as imagens do Docker personalizadas para o aplicativo. As imagens, em seguida, são validadas e enviados por push ao registro do Docker usado para as implantações em vários ambientes.

O pilar à direita, gerencie equipes de operações implantado aplicativos e infraestrutura em produção enquanto monitora o ambiente e os aplicativos para que eles possam fornecer comentários e ideias para a equipe de desenvolvimento sobre como o aplicativo pode ser aprimorado. Aplicativos de contêiner normalmente são executados em produção usando orquestradores de contêiner.

As duas equipes estão colaborando por meio de uma plataforma fundamental (contêineres do Docker) que fornece uma separação de preocupações como um contrato, melhorando muito a colaboração de duas equipes no ciclo de vida do aplicativo. Os desenvolvedores possuem o conteúdo do contêiner, seu ambiente operacional e as interdependências de contêiner, ao passo que as equipes de operações levar as imagens criadas junto com o manifesto e executa-os em seu sistema de orquestração.

## <a name="challenges-in-application-life-cycle-when-using-docker"></a>Ciclo de desafios na vida de aplicativo ao usar o Docker.

Há muitas razões que aumentarão o número de aplicativos em contêineres nos próximos anos, e um dos seguintes motivos é que a criação de aplicativos baseados em microsserviços.

Durante os últimos 15 anos, o uso de serviços da web tem sido a base dos milhares de aplicativos e, provavelmente, depois de alguns anos, estamos encontrará a mesma situação com aplicativos baseados em microsserviços em execução em contêineres do Docker.

Também vale a pena mencionar que você também pode usar contêineres do Docker para aplicativos monolíticos e você ainda receber a maioria dos benefícios do Docker. Contêineres não estão direcionando apenas microsserviços.

O uso do Docker colocação em contêineres e microsserviços faz com que novos desafios no processo de desenvolvimento de suas organizações e, portanto, você precisa de uma estratégia sólida para manter vários contêineres e microsserviços em execução em sistemas de produção. Eventualmente, os aplicativos empresariais terá centenas ou milhares de contêineres/instâncias em execução na produção.

Esses desafios de criam novas demandas ao usar as ferramentas do DevOps, então você terá que definir novos processos em suas atividades de DevOps e Encontre respostas para esse tipo de perguntas:

- Quais ferramentas posso usar para o desenvolvimento, para operações, gerenciamento e CI/CD?

- Como minha empresa gerenciar erros em contêineres quando em execução na produção?

- Como podemos alterar partes do nosso software em produção com mínimo tempo de inatividade?

- Como podemos dimensionar e como podemos monitorar nosso sistema de produção?

- Como podemos incluir testes e implantação de contêineres em nosso pipeline de lançamento?

- Como podemos usar as ferramentas de código-fonte aberto/plataformas para contêineres no Microsoft Azure?

Se você pode responder a todas essas perguntas, você estará melhor preparado para mover seus aplicativos (aplicativos novos ou existentes) para contêineres do Docker. 

## <a name="introduction-to-a-generic-end-to-end-docker-application-life-cycle-workflow"></a>Introdução a um workflow de ciclo de vida do aplicativo de Docker ponta a ponta genérico

Figura 2-2 apresenta um fluxo de trabalho mais detalhado para um ciclo de vida do aplicativo do Docker, concentrando-se nessa instância de ativos e atividades específicas de DevOps.

![Este diagrama mostra o "loop externo" do DevOps. Quando o código for enviado para o repositório, um pipeline de CI é iniciado, em seguida, começa o pipeline de CD, onde o aplicativo é implantado. As métricas coletadas de aplicativos implantados são retornem para a carga de trabalho de desenvolvimento, onde ocorre o "loop interno", para que as equipes de desenvolvimento tenham dados reais para responder às necessidades de negócios e de usuário.](./media/image2.png)

**Figura 2-2.** Fluxo de trabalho de alto nível para o ciclo de vida do aplicativo em contêineres de Docker

Tudo começa com o desenvolvedor, que começa a gravar código no fluxo de trabalho de loop interno. O estágio de loop interno é onde os desenvolvedores definem tudo o que acontece antes de enviar o código para o repositório de código (por exemplo, um controle sistema de origem como Git). Depois que ele foi confirmada, o repositório de disparadores CI (integração contínua) e o restante do fluxo de trabalho.

Basicamente, o loop interno consiste em etapas típicas, como "código", "run", "test" e "debug", além de etapas adicionais necessárias imediatamente antes de executar o aplicativo localmente. Isso é o processo do desenvolvedor para executar e testar o aplicativo como um contêiner do Docker. O fluxo de trabalho de loop interno será explicado nas seções a seguir.

Dando um passo atrás para examinar o fluxo de trabalho de extremidade ao final, o fluxo de trabalho de DevOps é mais do que uma tecnologia ou um conjunto de ferramentas: é uma mentalidade que exige a evolução cultura. É um pessoas, processos e as ferramentas apropriadas para tornar o seu ciclo de vida do aplicativo mais rápido e previsível. As empresas que adotam um fluxo de trabalho em contêineres normalmente reestruturar suas organizações para representar pessoas e processos que correspondam ao fluxo de trabalho em contêineres.

Praticar o DevOps pode ajudar as equipes respondem com mais rapidez em conjunto para as pressões competitivas, substituindo os processos manuais propensos a erro com a automação, o que resulta em fluxos de trabalho repetíveis e rastreabilidade aprimorada. As organizações também podem gerenciar ambientes com mais eficiência e perceber economias de custos com uma combinação de recursos de nuvem e locais, bem como ferramentas totalmente integradas.

Ao implementar seu fluxo de trabalho de DevOps para aplicativos do Docker, você verá que as tecnologias de Docker estão presentes em quase todos os estágios do fluxo de trabalho, com a sua caixa de desenvolvimento enquanto estiver trabalhando no loop interno (código, executar, depurar), a fase de compilação de teste de CI e, Por fim, a implantação desses contêineres para ambientes de preparo e produção.

Melhoria de práticas de qualidade ajuda a identificar defeitos no início do ciclo de desenvolvimento, o que reduz o custo de corrigi-los. Incluindo o ambiente e as dependências da imagem e adotar uma filosofia de implantar a mesma imagem em vários ambientes, você promove uma disciplina de extrair as configurações de ambiente específicas que torna as implantações mais confiáveis.

Dados avançados obtidos por meio da instrumentação efetivada (monitoramento e diagnóstico) fornecem informações sobre problemas de desempenho e comportamento do usuário para orientar os investimentos e prioridades futuras.

DevOps deve ser considerado uma jornada, não um destino. Ele deve ser implementado incrementalmente por projetos adequadamente no escopo do qual você pode demonstrar o sucesso, aprender e evoluir.

## <a name="benefits-of-devops-for-containerized-applications"></a>Benefícios do DevOps para aplicativos em contêineres

Aqui estão alguns dos mais importantes benefícios fornecidos por um fluxo de trabalho de DevOps sólido:

- Entregar software de melhor qualidade, com mais rapidez e melhor conformidade.

- Promova ajustes e melhoria contínua anteriormente e mais econômica.

- Aumente a transparência e colaboração entre participantes envolvidos na entrega e software operacional.

- Controle os custos e utilizar os recursos provisionados com mais eficiência enquanto minimiza os riscos de segurança.

- Plug and play bem com muitos dos seus investimentos existentes em DevOps, incluindo os investimentos em código-fonte aberto.

>[!div class="step-by-step"]
>[Anterior](index.md)
>[Próximo](../Microsoft-platform-tools-containerized-apps/index.md)
