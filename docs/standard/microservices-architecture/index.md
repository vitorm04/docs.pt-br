---
title: Microsserviços do .NET. Arquitetura de aplicativos .NET em contêineres
description: Arquitetura de microsserviços do .NET para aplicativos .NET em contêineres | Parte inicial
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/26/2017
ms.openlocfilehash: d4499384d63f11a1d78d0aa84749aed8ea554794
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
![](./media/cover.png)

# <a name="net-microservices-architecture-for-containerized-net-applications"></a>Microsserviços do .NET. Arquitetura de aplicativos .NET em contêineres

DOWNLOAD disponível em: <https://aka.ms/microservicesebook>

PUBLICADO POR

Divisão de Desenvolvedores Microsoft, equipes dos produtos .NET e Visual Studio

Uma divisão da Microsoft Corporation

One Microsoft Way

Redmond, Washington 98052-6399

Copyright © 2017, Microsoft Corporation

Todos os direitos reservados. Nenhuma parte do conteúdo deste guia pode ser reproduzida ou transmitida de nenhuma forma nem por nenhum meio sem a permissão por escrito do publicador.

Este manual é fornecido "no estado em que se encontra" e expressa os pontos de vista e as opiniões do autor. Os pontos de vista, as opiniões e as informações expressos neste guia, incluindo URLs e outras referências a sites da Internet, podem ser alteradas sem aviso prévio.

Alguns exemplos aqui representados são fornecidos apenas para ilustração e são fictícios. Nenhuma associação ou conexão real é intencional ou deve ser deduzida.

A Microsoft e as marcas comerciais listadas em http://www.microsoft.com na página da Web “Marcas comerciais” são marcas comerciais do grupo de empresas da Microsoft.

Mac e macOS são marcas comerciais da Apple Inc.

O logotipo de baleia do Docker é uma marca registrada da Docker, Inc. usado mediante permissão.

Todas as outras marcas e logotipos são propriedade de seus respectivos proprietários.

Coautores:

> **Cesar de la Torre**. PM Sênior, equipe do produto .NET, Microsoft Corp.
>
> **Bill Wagner**. Desenvolvedor de Conteúdo Sênior, C+E, Microsoft Corp.
>
> **Mike Rousos**, Engenheiro de Software Principal, equipe DevDiv CAT, Microsoft

Editores:

> **Mike Pope**
>
> **Steve Hoag**

Participantes e revisores:

> **Jeffrey Richter**, engenheiro de software parceiro, equipe do Azure, Microsoft
>
> **Jimmy Bogard**, Arquiteto Chefe na Headspring
>
> **Udi Dahan**, Fundador e CEO, Particular Software
>
> **Jimmy Nilsson**, Cofundador e CEO da Factor10
>
> **Glenn Condron**. Gerente de Programa Sênior, equipe do ASP.NET
>
> **Mark Fussell**, PM Líder Principal, equipe do Azure Service Fabric, Microsoft
>
> **Diego Vega**, PM Líder, equipe do Entity Framework, Microsoft
>
> **Barry Dorrans**. Gerente de Programa de Segurança Sênior
>
> **Rowan Miller**. Gerente de Programa Sênior, Microsoft
>
> **Ankit Asthana**, Gerente de PM Principal, equipe do .NET, Microsoft
>
> **Scott Hunter**, PM Diretor de Parceiro, equipe do .NET, Microsoft
>
> **Dylan Reisenberger**, Arquiteto e Desenvolvedor Líder na Polly
>
> **Steve Smith**, Especialista e Instrutor em Software na ASPSmith Ltd.
>
> **Cooper Ian**, Arquiteto de Codificação na Brighter
>
> **Unai Zorrilla**, Arquiteto e Desenvolvedor Líder na Plain Concepts
>
> **Eduard Tomas**, Desenvolvedor Líder na Plain Concepts
>
> **Ramon Tomas**, Desenvolvedor na Plain Concepts
>
> **David Sanz**, Desenvolvedor na Plain Concepts
>
> **Javier Valero**, Diretor Executivo de Operações no Grupo Solutio
>
> **Pedro milho**. Consultor Sênior, Microsoft
>
> **Michael Friis**, Gerente de Produto, Docker Inc
>
> **Charles Lowell**, Engenheiro de Software, equipe do VS CAT, Microsoft

## <a name="introduction"></a>Introdução

As empresas estão cada vez mais percebendo a economia de custo, resolvendo problemas de implantação e melhorando as operações de produção e de DevOps usando os contêineres. A Microsoft tem lançando inovações de contêiner para Windows e Linux com a criação de produtos como o Serviço de Contêiner do Azure e o Azure Service Fabric e por meio de parcerias com líderes do setor como a Docker, a Mesosphere e a Kubernetes. Esses produtos oferecem soluções de contêiner que ajudam as empresas a criar e implantar aplicativos com a velocidade e a escala da nuvem, seja qual for a escolha de plataformas ou de ferramentas.

O Docker está se tornando o verdadeiro padrão no setor de contêineres, com suporte dos fornecedores mais significativos nos ecossistemas do Windows e do Linux. (A Microsoft é um dos principais fornecedores de nuvem com suporte para o Docker). No futuro, o Docker provavelmente será onipresente em qualquer datacenter na nuvem ou local.

Além disso, a arquitetura de [microsserviços](https://martinfowler.com/articles/microservices.html) está despontando como uma abordagem importante para aplicativos críticos distribuídos. Em uma arquitetura baseada em microsserviço, o aplicativo é criado em uma coleção de serviços que podem ser desenvolvidos, testados, implantados e ter as versões controladas de forma independente.

## <a name="about-this-guide"></a>Sobre este guia

Este guia é uma introdução ao desenvolvimento de aplicativos com base em microsserviços e ao gerenciamento deles usando contêineres. Ele discute as abordagens de design de arquitetura e de implementação usando o .NET Core e os contêineres do Docker. Para facilitar a introdução aos contêineres e microsserviços, o guia concentra-se em um aplicativo de referência em contêineres e baseado em microsserviços que você pode explorar. O aplicativo de exemplo está disponível no repositório [eShopOnContainers](https://github.com/dotnet-architecture/eShopOnContainers) do GitHub.

Este guia fornece diretrizes básicas de desenvolvimento e de arquitetura principalmente no nível do ambiente de desenvolvimento com foco em duas tecnologias: Docker e .NET Core. Nossa intenção é que você leia este guia, ao pensar sobre o design do aplicativo sem focar a infraestrutura (nuvem ou local) do ambiente de produção. Você tomará decisões sobre a infraestrutura mais tarde, quando criar seus aplicativos prontos para produção. Portanto, este guia tem a intenção de ser independente da infraestrutura e mais centrado no ambiente de desenvolvimento.

Depois de estudar este guia, a próxima etapa será saber mais sobre os microsserviços pronto para produção no Microsoft Azure.

## <a name="what-this-guide-does-not-cover"></a>O que este guia não cobre

Este guia não se concentra no ciclo de vida do aplicativo, em DevOps, nos pipelines de CI/CD nem no trabalho da equipe. O guia complementar [Containerized Docker Application Lifecycle with Microsoft Platform and Tools](https://aka.ms/dockerlifecycleebook) (Ciclo de vida de aplicativo do Docker em contêineres com a plataforma e as ferramentas da Microsoft) trata desse assunto. O guia atual também não fornece detalhes de implementação na infraestrutura do Azure, como informações sobre orquestradores específicos.

### <a name="additional-resources"></a>Recursos adicionais

-   **Ciclo de vida de aplicativo do Docker em contêineres com a plataforma e as ferramentas da Microsoft** (e-book para download)[*https://aka.ms/dockerlifecycleebook*](https://aka.ms/dockerlifecycleebook)

## <a name="who-should-use-this-guide"></a>Quem deve usar este guia

Escrevemos este guia para desenvolvedores e arquitetos de solução que são novos no desenvolvimento de aplicativos com base no Docker e em arquitetura baseada em microsserviços. Este guia será indicado para você se desejar saber como arquitetar, projetar e implementar aplicativos de prova de conceito com tecnologias de desenvolvimento da Microsoft (com foco especial no .NET Core) e com contêineres do Docker.

Esse guia também será útil se você for um tomador de decisões técnicas, como um arquiteto corporativo que deseja ter uma visão geral da arquitetura e da tecnologia antes de decidir qual abordagem selecionar para aplicativos distribuídos novos e modernos.

### <a name="how-to-use-this-guide"></a>Como usar este guia

A primeira parte deste guia apresenta os contêineres do Docker, discute como escolher entre o .NET Core e o .NET Framework como estrutura de desenvolvimento e fornece uma visão geral sobre microsserviços. Este conteúdo é para arquitetos e tomadores de decisões técnicas que desejam ter uma visão geral, mas que não precisam se concentrar nos detalhes da implementação de código.

A segunda parte do guia de começa com a seção [Processo de desenvolvimento de aplicativos baseados no Docker](#ch_dev_process_for_docker_based_apps). Ela se concentra nos padrões de desenvolvimento e de microsserviços para implementar aplicativos que usam o .NET Core e o Docker. Esta seção será de interesse especial para desenvolvedores e arquitetos que desejam se concentrar no código, nos padrões e nos detalhes de implementação.

## <a name="related-microservice-and-container-based-reference-application-eshoponcontainers"></a>Aplicativo de referência baseado em contêiner e em microsserviço: eShopOnContainers

O aplicativo eShopOnContainers é um aplicativo de referência do .NET Core e de microsserviços que foi projetado para ser implantado usando contêineres do Docker. O aplicativo consiste em vários subsistemas, incluindo vários front-ends de interface do usuário de loja virtual (um aplicativo Web e um aplicativo móvel nativo). Ele também inclui os microsserviços e os contêineres de back-end de todas as operações do servidor necessárias.

O código-fonte desse aplicativo baseado em contêineres e de microsserviço é de software livre e está disponível no repositório [eShopOnContainers](http://aka.ms/MicroservicesArchitecture) do GitHub.

## <a name="send-us-your-feedback"></a>Envie-nos seus comentários!

Escrevemos este guia para ajudá-lo a entender a arquitetura de aplicativos em contêineres e de microsserviços no .NET. O guia e o aplicativo de referência relacionado continuarão sendo desenvolvidos, portanto seus comentários são bem-vindos! Se você tiver comentários sobre como este guia poderá ser melhorado, envie-os para:

[dotnet-architecture-ebooks-feedback@service.microsoft.com](mailto:dotnet-architecture-ebooks-feedback@service.microsoft.com)

>[!div class="step-by-step"]
[Next] (container-docker-introduction/index.md)
