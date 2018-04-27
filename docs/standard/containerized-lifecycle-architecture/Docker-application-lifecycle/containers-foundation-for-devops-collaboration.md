---
title: Contêineres de base para colaboração de DevOps
description: Containerized Docker Application Lifecycle with Microsoft Platform and Tools (Ciclo de vida de aplicativo do Docker em contêineres com a plataforma e as ferramentas da Microsoft)
ms.prod: .net
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 09/22/2017
ms.topic: article
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: a6c33237d129fd269f2c0d1256b98be561673dce
ms.sourcegitcommit: 2e8acae16ae802f2d6d04e3ce0a6dbf04e476513
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2018
---
# <a name="containers-as-the-foundation-for-devops-collaboration"></a>Contêineres de base para colaboração de DevOps

Por natureza dos contêineres e tecnologia de Docker, os desenvolvedores podem compartilhar seus software e dependências facilmente com operações de TI e ambientes de produção, eliminando a desculpa típicos "funciona em Meu computador". Contêineres resolver conflitos de aplicativo entre ambientes diferentes. Indiretamente, contêineres e Docker reunir os desenvolvedores e as operações de TI mais próximo, tornando mais fácil para que eles possam colaborar de maneira efetiva. Adotar o fluxo de trabalho do contêiner fornece muitos clientes com a continuidade do DevOps eles tiver procurado mas tinha anteriormente implantar por meio de uma configuração mais complexa para a versão e criar pipelines. Contêineres simplificam os pipelines de criação/teste/implantação em DevOps.

![](./media/image1.png)

Figura 2-1: cargas de trabalho principal por "personas" no ciclo de vida de aplicativos em contêineres do Docker

Com contêineres do Docker, os desenvolvedores próprios o que está dentro do contêiner (aplicativo e serviço e as dependências para estruturas e componentes) e como os contêineres e os serviços se comportam em conjunto como um aplicativo composto por uma coleção de serviços. Interdependências de vários contêineres são definidas em um arquivo de docker compose.yml ou o que poderia ser chamado uma *o manifesto de implantação*. Enquanto isso, as equipes de operações de TI (gerenciamento e profissionais de TI) podem se concentrar no gerenciamento de ambientes de produção. infraestrutura; escalabilidade; monitoramento; e, por fim, garantindo que os aplicativos estão fornecendo corretamente para os usuários finais, sem a necessidade de conhecer o conteúdo dos vários contêineres. Portanto, o nome "contêiner," Cancelando a analogia para contêineres de envio do mundo real. Assim, os proprietários de conteúdo de um contêiner precisam não relacionados se como o contêiner será enviado e os transportes de empresa envio um contêiner de seu ponto de origem para o destino sem saber ou se preocupar com o conteúdo. De maneira semelhante, os desenvolvedores podem criar e possui o conteúdo dentro de um contêiner de Docker sem precisar se preocupar com os mecanismos de "transporte".

No pilar no lado esquerdo da Figura 2-1, os desenvolvedores gravam em executar o código localmente em contêineres do Docker usando o Docker para Windows ou Mac. Eles definem o ambiente operacional para o código usando um Dockerfile que especifica o sistema operacional base para ser executado, bem como as etapas de compilação para compilar seu código em uma imagem do Docker. Os desenvolvedores definem como as imagens de um ou mais interoperem usando o mencionados acima *docker compose.yml* o manifesto de implantação do arquivo. Conforme são concluídas seu desenvolvimento local, eles push seu código de aplicativo e os arquivos de configuração do Docker para o repositório de código de sua escolha (ou seja, o repositório do Git).

O pilar DevOps define pipelines compilação – Continuous Integration (CI) usando o Dockerfile fornecido no repositório de código. O sistema de CI extrai as imagens de contêiner base do registro Docker selecionado e cria as imagens do Docker personalizadas para o aplicativo. As imagens, em seguida, são validadas e enviados por push para o registro de Docker usado para implantações em vários ambientes.

Pilar à direita, gerenciar equipes de operações implantado aplicativos e infraestrutura de produção ao monitorar o ambiente e os aplicativos para que eles possam fornecer comentários e informações para a equipe de desenvolvimento sobre como o aplicativo pode ser aprimorado. Aplicativos de contêiner normalmente são executados na produção usando orchestrators do contêiner.

Dois agrupamentos são colaborando por meio de uma plataforma de base (contêineres do Docker) que fornece uma separação de preocupações como um contrato, ao mesmo tempo, melhorando a colaboração as duas equipes no ciclo de vida do aplicativo. Os desenvolvedores possuem o conteúdo do contêiner, o ambiente operacional e as interdependências de contêiner, enquanto as equipes de operações levar as imagens internas junto com o manifesto e executa-los em seu sistema de orquestração.

## <a name="introduction-to-a-generic-end-to-end-docker-application-life-cycle-workflow"></a>Introdução a um genérico fluxo de trabalho ciclo de vida ponta a ponta Docker aplicativo

Figura 2-2 apresenta um fluxo de trabalho mais detalhado de um ciclo de vida do aplicativo do Docker, focando nesta instância ativos e atividades específicas do DevOps.

![](./media/image2.png)

Figura 2-2: ciclo de vida do aplicativo em contêineres de fluxo de trabalho de alto nível para o Docker

Tudo começa com o desenvolvedor, o que inicia a escrever o código no loop interno de fluxo de trabalho. O estágio de loop interna é onde os desenvolvedores definir tudo o que acontece antes de enviar o código para o repositório de código (por exemplo, um controle sistema de origem como Git). Depois que ele é confirmado, o repositório dispara CI (integração contínua) e o restante do fluxo de trabalho.

Basicamente, o loop interno consiste em etapas típicas como "código", "run", "test" e "depuração", além de etapas adicionais diretamente antes de executar o aplicativo localmente. Isso é quando o desenvolvedor é executado e testa o aplicativo como um contêiner do Docker. O fluxo de trabalho do loop interno será explicado nas seções a seguir.

Recuperando uma etapa para examinar o fluxo de trabalho de ponta a, o fluxo de trabalho de DevOps é mais de uma tecnologia ou um conjunto de ferramentas: modo de pensar que requer a evolução cultura. É pessoas, processos e as ferramentas apropriadas para fazer o seu ciclo de vida do aplicativo mais rápido e previsível. As empresas que adotam um fluxo de trabalho em contêineres normalmente reestruturar suas organizações para representar pessoas e processos que correspondam o fluxo de trabalho em contêineres.

Praticar DevOps pode ajudar a equipes a responder com mais rapidez juntos pressões de concorrência, substituindo processos manuais propensos a erro com a automação, o que resulta em maior capacidade de acompanhamento e fluxos de trabalho reproduzíveis. As organizações também podem gerenciar ambientes com mais eficiência e obter economia com uma combinação de recursos de nuvem e local, bem como ferramentas integradas.

Ao implementar o fluxo de trabalho para aplicativos de Docker DevOps, você verá que tecnologias do Docker estão presentes em quase todas as etapas do fluxo de trabalho, de sua caixa de desenvolvimento enquanto estiver trabalhando no loop interno (código, executar, depurar,) para a fase de compilação de teste de CI e, claro, em produção e em ambientes de preparo e ao implantar os contêineres a esses ambientes.

Aperfeiçoamento das práticas de qualidade ajuda a identificar os defeitos no início do ciclo de desenvolvimento, o que reduz o custo de corrigi-los. Incluindo o ambiente e as dependências da imagem e adotando uma filosofia de implantar a mesma imagem em vários ambientes, é possível promover uma disciplina de extrair as configurações específicas do ambiente fazer implantações mais confiável.

Dados ricos obtidos por meio de instrumentação efetivada (monitoramento e diagnóstico) fornecem uma visão problemas de desempenho e o comportamento do usuário para orientar investimentos e prioridades futuras.

DevOps deve ser considerada uma viagem, não um destino. Ele deve ser implementado incrementalmente projetos adequadamente no escopo do qual você pode demonstrar sucesso, aprender e evoluir.

## <a name="benefits-of-devops-for-containerized-applications"></a>Benefícios do DevOps para aplicativos em contêineres

Aqui estão alguns dos principais benefícios fornecidos por um fluxo de trabalho DevOps sólido:

-   Entregar software de melhor qualidade, mais rápido e melhor conformidade

-   Unidade ajustes e a melhoria contínua anteriormente e mais economia

-   Aumentar a transparência e a colaboração entre os participantes envolvidos na entrega e software operacional

-   Controlar os custos e utilizar recursos provisionados com mais eficiência e minimizar os riscos de segurança

-   Plug and play bem com muitos dos seus investimentos existentes em DevOps, incluindo investimentos em código-fonte aberto

>[!div class="step-by-step"]
[Anterior] (index.md) [Avançar] (... /Microsoft-Platform-Tools-containerized-Apps/index.MD)
