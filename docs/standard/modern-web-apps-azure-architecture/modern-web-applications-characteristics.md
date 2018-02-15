---
title: "Características de aplicativos web modernos"
description: "Projetar aplicativos Web modernos com ASP.NET Core e o Azure | características de aplicativos web modernos"
author: ardalis
ms.author: wiwagn
ms.date: 10/06/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: ecef23870ac547f4b4066628da71f8af98c91b27
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/23/2017
---
# <a name="characteristics-of-modern-web-applications"></a>Características de aplicativos Web modernos

> "… com o projeto correto, os recursos vêm barata. Essa abordagem é árdua, mas continua a ter êxito."  
> _\- Dennis Ritchie_

## <a name="summary"></a>Resumo

Aplicativos web modernos têm maior expectativas de usuário e demandas maiores do que nunca. Os aplicativos web de hoje devem estar disponíveis 24/7 de qualquer lugar no mundo e é utilizável de praticamente qualquer dispositivo ou o tamanho da tela. Aplicativos da Web devem ser seguro, flexível e escalonável para atender aos picos de demanda. Cada vez mais, os cenários complexos devem ser tratados pelo usuários experiências criadas no cliente usando JavaScript e se comunicando com eficiência por meio de APIs da web.

ASP.NET Core é otimizado para aplicativos web modernos e cenários de hospedagem em nuvem. O design modular permite que os aplicativos dependem somente os recursos que eles realmente de usar, melhorando o desempenho ao reduzir os requisitos de recursos de hospedagem e segurança do aplicativo.

## <a name="reference-application-eshoponweb"></a>Referência do aplicativo: eShopOnWeb

Este guia inclui um aplicativo de referência, *eShopOnWeb*, que demonstra alguns dos princípios e as recomendações. O aplicativo é um repositório online simple que oferece suporte à navegação por meio de um catálogo de camisas, canecas e outros itens de marketing. O aplicativo de referência é deliberadamente simple para torná-lo mais fácil de entender.

**Figura 2-1.** eShopOnWeb

![](./media/image2-1.png)

> ### <a name="reference-application"></a>Aplicativo de referência
> - **eShopOnWeb**  
> <https://github.com/dotnet/eShopOnWeb>

## <a name="cloud-hosted-and-scalable"></a>Hospedado na nuvem e escalonável

ASP.NET Core é otimizada para a nuvem (nuvem pública, nuvem privada, nuvem) porque é memória baixa e alta taxa de transferência. Menor volume de aplicativos do ASP.NET Core significa que você pode hospedar mais no mesmo hardware e pague menos recursos quando usando pagamento medida que vai hospedar os serviços de nuvem. A maior taxa de transferência significa que você pode atender mais clientes de um aplicativo que recebe o mesmo hardware, reduzindo ainda mais a necessidade de investir na infraestrutura de hospedagem e servidores.

## <a name="cross-platform"></a>Plataforma cruzada

ASP.NET Core é entre plataformas e podem ser executados em Linux e MacOS, bem como Windows. Isso abre muitas opções novas para desenvolvimento e implantação de aplicativos criados com o ASP.NET Core. Contêineres do docker, que são normalmente executadas Linux hoje, podem hospedar aplicativos ASP.NET Core, permitindo que eles tirar proveito dos benefícios do [contêineres e microservices](../microservices-architecture/index.md).

## <a name="modular-and-loosely-coupled"></a>Modulares e flexíveis

Pacotes do NuGet são objetos de primeira classe no núcleo do .NET e aplicativos ASP.NET Core consistem em muitas bibliotecas através do NuGet. Essa granularidade da funcionalidade ajuda a garantir aplicativos somente dependem e implantar a funcionalidade que realmente precisam, reduzindo sua área de superfície de vulnerabilidade espaço e segurança.

ASP.NET Core totalmente também dá suporte a injeção de dependência, internamente e no nível do aplicativo. Interfaces podem ter várias implementações que podem ser trocadas conforme necessário. Injeção de dependência permite aos aplicativos livremente algumas a essas interfaces, tornando mais fácil estender, manter e teste.

## <a name="easily-tested-with-automated-tests"></a>Facilmente testados com testes automatizados

Aplicativos do ASP.NET Core oferecem suporte a testes de unidade e seus acoplamento e suporte para inclusões de dependência torna mais fácil alternar preocupações de infraestrutura com implementações de falsas para fins de teste. ASP.NET Core também é fornecida uma TestServer que pode ser usado para hospedar aplicativos na memória. Testes funcionais podem fazer solicitações para esse servidor na memória, exercer a pilha do aplicativo completo (incluindo middleware, roteamento, associação de modelos, filtros, etc.) e receber uma resposta, tudo em uma fração do tempo necessário para hospedar o aplicativo em um servidor real e fazer solicitações por meio da camada de rede. Esses testes são especialmente fácil de escrever e valiosos, APIs, que são mais importantes em aplicativos web modernos.

## <a name="traditional-and-spa-behaviors-supported"></a>Tradicional e comportamentos do SPA com suporte

Aplicativos web tradicionais envolvido pequeno comportamento do lado do cliente, mas em vez disso, tem baseava-se no servidor para todas as consultas, navegação e atualizações para que o aplicativo pode precisar fazer. Cada nova operação feita pelo usuário deve ser convertida em uma nova solicitação da web, com o resultado sendo uma recarga de página inteira no navegador do usuário final. Estruturas de Model-View-Controller (MVC) clássico normalmente siga essa abordagem, com cada nova solicitação correspondente a uma ação de controlador diferente, que por sua vez trabalhar com um modelo e retornar uma exibição. Algumas operações individuais em uma determinada página podem ser aprimoradas com funcionalidade AJAX (JavaScript assíncrono e XML), mas a arquitetura geral do aplicativo usado muitas diferentes modos de exibição do MVC e pontos de extremidade de URL.

Aplicativos de página única (SPAs), por outro lado, envolvem muito poucos gerado dinamicamente no lado do servidor de página for carregada (se houver). Muitos SPAs são inicializados em um arquivo HTML estático que carrega as bibliotecas JavaScript necessárias para iniciar e executar o aplicativo. Esses aplicativos fazer uso intenso de APIs da web para suas necessidades de dados e podem fornecer que experiências de usuário muito mais rico.

Muitos aplicativos web envolvem uma combinação de comportamento do aplicativo da web tradicional (normalmente de conteúdo) e SPAs (para interatividade). Dá suporte a principal do ASP.NET MVC e APIs da web no mesmo aplicativo, usando o mesmo conjunto de ferramentas e bibliotecas do framework de base.

## <a name="simple-development-and-deployment"></a>Implantação e desenvolvimento simple

Aplicativos do ASP.NET Core podem ser escritos usando editores de texto simples e interfaces de linha de comando ou ambientes de desenvolvimento completo como o Visual Studio. Aplicativos monolíticos normalmente são implantados em um único ponto de extremidade. Implantações facilmente podem ser automatizadas para ocorrer como parte de uma integração contínua (CI) e pipeline de fornecimento contínuo (CD). Além das ferramentas de CI/CD tradicionais, o Windows Azure tem suporte integrado para repositórios git e pode implantar automaticamente atualizações conforme elas são feitas para um branch git especificado ou uma marca.

## <a name="traditional-aspnet-and-web-forms"></a>ASP.NET tradicional e formulários da Web

Além do ASP.NET Core, tradicional ASP.NET 4. x continua a ter uma plataforma robusta e confiável para a criação de aplicativos web. Dá suporte ao ASP.NET MVC e a API da Web modelos de desenvolvimento, bem como os formulários da Web, que é adequado para desenvolvimento de aplicativo avançado baseado em página e apresenta um ecossistema de componente de terceiros avançados. Windows Azure tem um excelente suporte permanente para aplicativos do ASP.NET 4. x e muitos desenvolvedores estão familiarizados com esta plataforma.

> ### <a name="references--modern-web-applications"></a>Referências – aplicativos Web modernos
> - **Introdução ao ASP.NET Core**  
> <https://docs.microsoft.com/aspnet/core/>
> - **Seis chave benefícios do ASP.NET Core que tornam diferentes e melhor**  
> <https://blog.trigent.com/six-key-benefits-of-asp-net-core-1-0-which-make-it-different-better/>
> - **Teste no núcleo do ASP.NET**  
> <https://docs.microsoft.com/aspnet/core/testing/>

>[!div class="step-by-step"]
[Anterior] (index.md) [Avançar] (choose-between-traditional-web-and-single-page-apps.md)
