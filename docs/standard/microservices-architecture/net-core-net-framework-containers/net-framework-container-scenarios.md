---
title: "Quando escolher o .NET Framework para contêineres do Docker"
description: "Arquitetura de Microservices .NET para aplicativos .NET em contêineres | Quando escolher o .NET Framework para contêineres do Docker"
keywords: "Docker, Microsserviços, ASP.NET, Contêiner"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 10/18/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.openlocfilehash: 1bf1f055f040e7f3dc575b7a04140ebf0c599f98
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/22/2017
---
# <a name="when-to-choose-net-framework-for-docker-containers"></a>Quando escolher o .NET Framework para contêineres do Docker

Enquanto o .NET Core oferece benefícios significativos para novos aplicativos e padrões de aplicativo, do .NET Framework continuará a ser uma boa opção para muitos cenários existentes.

## <a name="migrating-existing-applications-directly-to-a-windows-server-container"></a>Migrar aplicativos existentes diretamente para um contêiner do Windows Server

Você talvez queira usar contêineres do Docker apenas para simplificar a implantação, mesmo se você não estiver criando microservices. Por exemplo, talvez você queira aumentar seu fluxo de trabalho de DevOps com o Docker, contêineres pode fornecer melhor teste isolada ambientes e também pode eliminar problemas de implantação causados por dependências ausentes, quando você move para um ambiente de produção. Em casos assim, mesmo se você estiver implantando um aplicativo monolítico, faz sentido usar Docker e contêineres do Windows para seus aplicativos do .NET Framework atuais.

Na maioria dos casos para esse cenário, você não precisará migrar seus aplicativos existentes para o núcleo do .NET; Você pode usar contêineres do Docker que incluem o tradicional do .NET Framework. No entanto, uma abordagem recomendada é usar o .NET Core como estender um aplicativo existente, como gravar um novo serviço no núcleo do ASP.NET.

## <a name="using-third-party-net-libraries-or-nuget-packages-not-available-for-net-core"></a>Usando bibliotecas .NET de terceiros ou pacotes do NuGet não está disponíveis para o .NET Core

Bibliotecas de terceiros estão adotando rapidamente o [.NET padrão](https://docs.microsoft.com/dotnet/standard/net-standard), que permite que o código de compartilhamento em todos os tipos do .NET, incluindo o .NET Core. Com o .NET padrão biblioteca 2.0 e além da superfície da API compatibilidade nas estruturas diferentes se tornou significativamente maior e no .NET Core 2.0 aplicativos podem também fazer referência direta bibliotecas existentes do .NET Framework (consulte [compatível shim](https://github.com/dotnet/standard/blob/master/docs/faq.md#how-does-net-standard-versioning-work)).

No entanto, mesmo com esse progressão excepcional desde padrão do .NET 2.0 e o núcleo do .NET 2.0, pode haver casos em que determinados pacotes do NuGet precisam a execução do Windows e podem não oferecer suporte a .NET Core. Se esses pacotes são essenciais para o seu aplicativo, você precisará usar o .NET Framework em contêineres do Windows.

## <a name="usingnet-technologies-not-available-for-net-core"></a>Tecnologias de Using.NET não está disponíveis para o .NET Core 

Algumas tecnologias do .NET Framework não estão disponíveis na versão atual do núcleo do .NET (versão 2.0 redação deste artigo). Algumas delas estarão disponíveis em versões posteriores do .NET Core (.NET Core 2. x), mas outras não se aplicam para o novo aplicativo padrões direcionados ao .NET Core e nunca podem estar disponíveis.

A lista a seguir mostra a maioria das tecnologias que não estão disponíveis no núcleo do .NET 2.0:

-   Web Forms do ASP.NET. Essa tecnologia só está disponível no .NET Framework. Atualmente, não há planos para trazer os Web Forms do ASP.NET para o .NET Core.

-   Serviços WCF. Mesmo quando um [biblioteca de cliente WCF](https://github.com/dotnet/wcf) está disponível para consumir os serviços WCF do .NET Core. Desde meados de 2017, a implementação do servidor WCF só está disponível no .NET Framework. Esse cenário pode ser considerado para futuras versões do .NET Core.

-   Serviços relacionados ao fluxo de trabalho. (Anteriormente conhecido como ADO.NET Data Services) do WCF Data Services, serviços de fluxo de trabalho (WCF + WF em um único serviço) e Windows Workflow Foundation (WF) só estão disponíveis no .NET Framework. Atualmente, não há nenhum plano para colocá-los em .NET Core.

Além das tecnologias listadas no oficial [roteiro .NET Core](https://github.com/aspnet/Home/wiki/Roadmap), outros recursos podem ser movidos para o .NET Core. Para obter uma lista completa, examine os itens marcados como [porta núcleo](https://github.com/dotnet/corefx/issues?q=is%3Aopen+is%3Aissue+label%3Aport-to-core) no site do CoreFX GitHub. Observe que essa lista não representa um compromisso da Microsoft para trazer esses componentes para .NET Core — os itens simplesmente capturar solicitações da comunidade. Se você gosta qualquer um dos componentes listados acima, considere participar de discussões no GitHub para que sua voz pode ser ouvido. E se você achar que algo está faltando, [envie uma nova questão no repositório do CoreFX](https://github.com/dotnet/corefx/issues/new).

## <a name="using-a-platform-or-api-that-does-not-support-net-core"></a>Usando uma plataforma ou uma API que não oferece suporte a .NET Core

Algumas plataformas de terceiros ou Microsoft não dão suporte a .NET Core. Por exemplo, alguns serviços do Azure fornecem um SDK que ainda não está disponível para consumo no .NET Core. Isso é temporário, porque todos os serviços do Azure ainda usará .NET Core. Por exemplo, o [SDK do DocumentDB do Azure para .NET Core](https://www.nuget.org/packages/Microsoft.Azure.DocumentDB.Core/1.2.1) foi lançado como uma visualização em 16 de novembro de 2016, mas agora está disponível (GA) como uma versão estável.

Enquanto isso, se qualquer plataforma ou o serviço no Azure ainda não dá suporte .NET Core com seu cliente de API, você pode usar a API REST equivalente do SDK de cliente ou o serviço do Azure no .NET Framework.

### <a name="additional-resources"></a>Recursos adicionais

-   **Guia de núcleo do .NET**
    [*https://docs.microsoft.com/dotnet/core/index*](https://docs.microsoft.com/dotnet/core/index)

-   **Movimentando do .NET Framework para .NET Core**
    [*https://docs.microsoft.com/dotnet/core/porting/index*](https://docs.microsoft.com/dotnet/core/porting/index)

-   **.NET framework no guia de Docker**
    [*https://docs.microsoft.com/dotnet/framework/docker/*](https://docs.microsoft.com/dotnet/framework/docker/)

-   **Visão geral dos componentes do .NET**
    [*https://docs.microsoft.com/dotnet/standard/components*](https://docs.microsoft.com/dotnet/standard/components)




>[!div class="step-by-step"]
[Anterior] (net-core-contêiner-scenarios.md) [Avançar] (contêiner-estrutura-escolha-factors.md)
