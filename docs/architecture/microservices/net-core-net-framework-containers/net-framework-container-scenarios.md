---
title: Quando escolher o .NET Framework para os contêineres do Docker
description: Arquitetura de microsserviços do .NET para aplicativos .NET em contêineres | Quando escolher o .NET Framework para os contêineres do Docker
ms.date: 01/30/2020
ms.openlocfilehash: dfb1e8883fc9c3d9235672bc2885858bfb64afa5
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/14/2020
ms.locfileid: "77501970"
---
# <a name="when-to-choose-net-framework-for-docker-containers"></a>Quando escolher o .NET Framework para os contêineres do Docker

Embora o .NET Core ofereça benefícios significativos para novos aplicativos e padrões de aplicativo, o .NET Framework continuará sendo uma boa escolha para muitos cenários existentes.

## <a name="migrating-existing-applications-directly-to-a-windows-server-container"></a>Migrando aplicativos existentes diretamente para um contêiner do Windows Server

Talvez convenha usar contêineres do Docker apenas para simplificar a implantação, mesmo se você não estiver criando microsserviços. Por exemplo, talvez convenha aprimorar seu fluxo de trabalho DevOps com o Docker — os contêineres podem oferecer ambientes de teste mais bem isolados e também podem eliminar problemas de implantação causados por dependências ausentes quando você muda para um ambiente de produção. Em casos assim, mesmo se você estiver implantando um aplicativo monolítico, faz sentido usar os contêineres do Docker e do Windows para seus aplicativos .NET Framework atuais.

Na maioria dos casos desse cenário, não será necessário migrar seus aplicativos existentes para o .NET Core; é possível usar contêineres do Docker que incluem o .NET Framework tradicional. Contudo, uma abordagem recomendada é usar o .NET Core ao estender um aplicativo existente, por exemplo, para gravar um novo serviço no ASP.NET Core.

## <a name="using-third-party-net-libraries-or-nuget-packages-not-available-for-net-core"></a>Usando bibliotecas .NET de terceiros ou pacotes NuGet não disponíveis para o .NET Core

Bibliotecas de terceiros estão rapidamente adotando [o .NET Standard](../../../standard/net-standard.md), que permite o compartilhamento de código em todos os sabores .NET, incluindo o .NET Core. Com o .NET Standard 2.0 e posterior, a compatibilidade de superfície da API entre diferentes frameworks tornou-se significativamente maior. Ainda mais, o .NET Core 2.x e os aplicativos mais novos também podem referenciar diretamente as bibliotecas do .NET Framework existentes (consulte [.NET Framework 4.6.1 com suporte ao .NET Standard 2.0](https://github.com/dotnet/standard/blob/master/docs/planning/netstandard-2.0/README.md#net-framework-461-supporting-net-standard-20)).

Além disso, o [Pacote de Compatibilidade do Windows](../../../core/porting/windows-compat-pack.md) amplia a superfície da API disponível para o .NET Standard 2.0 no Windows. Este pacote permite recompilar a maioria do código existente para o .NET Standard 2.x com pouca ou nenhuma modificação para ser executado no Windows.

No entanto, mesmo com essa progressão excepcional desde o .NET Standard 2.0 e o .NET Core 2.1, pode haver casos em que determinados pacotes NuGet precisam do Windows para serem executados e não dão suporte ao .NET Core. Se esses pacotes forem críticos ao aplicativo, será necessário usar o .NET Framework em contêineres do Windows.

## <a name="using-net-technologies-not-available-for-net-core"></a>Usando tecnologias do .NET não disponíveis para .NET Core

Algumas tecnologias .NET Framework não estão disponíveis na versão atual do .NET Core (versão 3.1 a partir desta redação). Alguns deles podem ficar disponíveis em versões posteriores, mas outros não se encaixam nos novos padrões de aplicativos visados pelo .NET Core e podem nunca estar disponíveis.

A lista a seguir mostra a maioria das tecnologias que não estão disponíveis no .NET Core 3.1:

- Web Forms do ASP.NET. Esta tecnologia só está disponível no .NET Framework. Atualmente, não há planos para trazer os Web Forms do ASP.NET para o .NET Core.

- Serviços WCF. Mesmo quando uma [biblioteca WCF-Client](https://github.com/dotnet/wcf) está disponível para consumir serviços WCF do .NET Core, a partir de fevereiro de 2020, a implementação do servidor WCF só está disponível no .NET Framework. Esse cenário pode ser considerado para versões futuras do .NET Core. Há, inclusive, algumas APIs consideradas para inclusão no [Pacote de Compatibilidade do Windows](../../../core/porting/windows-compat-pack.md).

- Serviços relacionados a fluxo de trabalho. O Windows WF (Workflow Foundation), os Serviços de fluxo de trabalho (WCF + WF em um único serviço) e o WCF Data Services (anteriormente conhecido como Serviços de Dados ADO.NET) só estão disponíveis no .NET Framework. No momento, não há planos para colocá-los no .NET Core.

Além das tecnologias listadas no roteiro oficial do [.NET Core,](https://github.com/dotnet/core/blob/master/roadmap.md)outros recursos podem ser portados para o .NET Core ou para a nova [plataforma unificada .NET](https://devblogs.microsoft.com/dotnet/introducing-net-5/). Você pode considerar participar das discussões no GitHub para que sua voz possa ser ouvida. E se você acha que algo está faltando, arquive um novo problema no repositório [Dotnet/runtime](https://github.com/dotnet/runtime/issues/new) GitHub.

## <a name="using-a-platform-or-api-that-doesnt-support-net-core"></a>Usando uma plataforma ou API que não suporta .NET Core

Algumas plataformas da Microsoft e de terceiros não suportam o .NET Core. Por exemplo, alguns serviços do Azure fornecem um SDK que ainda não está disponível para consumo no .NET Core. A maioria do Azure SDK deve eventualmente ser portada para .NET Core/Standard, mas alguns podem não por várias razões. Você pode ver os SDKs Disponíveis do Azure na página [Azure SDK Latest Releases.](https://azure.github.io/azure-sdk/releases/latest/index.html)

Enquanto isso, se qualquer plataforma ou o serviço no Azure ainda não der suporte ao .NET Core com sua API do cliente, será possível usar a API REST equivalente do serviço do Azure ou o SDK do cliente no .NET Framework.

### <a name="additional-resources"></a>Recursos adicionais

- **.NET Core Guide** \
  [https://docs.microsoft.com/dotnet/core/index](../../../core/index.md)

- **Portando do .NET Framework para .NET Core** \
  [https://docs.microsoft.com/dotnet/core/porting/index](../../../core/porting/index.md)

- **.NET Core no Guia Docker** \
  [https://docs.microsoft.com/dotnet/core/docker/introduction](../../../core/docker/introduction.md)

- **Visão geral dos componentes .NET** \
  [https://docs.microsoft.com/dotnet/standard/components](../../../standard/components.md)

>[!div class="step-by-step"]
>[Próximo](net-core-container-scenarios.md)
>[anterior](container-framework-choice-factors.md)
