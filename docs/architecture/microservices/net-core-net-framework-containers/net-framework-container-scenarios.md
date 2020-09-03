---
title: Quando escolher o .NET Framework para os contêineres do Docker
description: Arquitetura de microsserviços do .NET para aplicativos .NET em contêineres | Quando escolher o .NET Framework para os contêineres do Docker
ms.date: 01/30/2020
ms.openlocfilehash: 116ba02878a60487f1af3c2b2e084307fad29618
ms.sourcegitcommit: b1f4756120deaecb8b554477bb040620f69a4209
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/03/2020
ms.locfileid: "89414416"
---
# <a name="when-to-choose-net-framework-for-docker-containers"></a>Quando escolher o .NET Framework para os contêineres do Docker

Embora o .NET Core ofereça benefícios significativos para novos aplicativos e padrões de aplicativo, o .NET Framework continuará sendo uma boa escolha para muitos cenários existentes.

## <a name="migrating-existing-applications-directly-to-a-windows-server-container"></a>Migrando aplicativos existentes diretamente para um contêiner do Windows Server

Talvez convenha usar contêineres do Docker apenas para simplificar a implantação, mesmo se você não estiver criando microsserviços. Por exemplo, talvez convenha aprimorar seu fluxo de trabalho DevOps com o Docker — os contêineres podem oferecer ambientes de teste mais bem isolados e também podem eliminar problemas de implantação causados por dependências ausentes quando você muda para um ambiente de produção. Em casos assim, mesmo se você estiver implantando um aplicativo monolítico, faz sentido usar os contêineres do Docker e do Windows para seus aplicativos .NET Framework atuais.

Na maioria dos casos desse cenário, não será necessário migrar seus aplicativos existentes para o .NET Core; é possível usar contêineres do Docker que incluem o .NET Framework tradicional. Contudo, uma abordagem recomendada é usar o .NET Core ao estender um aplicativo existente, por exemplo, para gravar um novo serviço no ASP.NET Core.

## <a name="using-third-party-net-libraries-or-nuget-packages-not-available-for-net-core"></a>Usando bibliotecas .NET de terceiros ou pacotes NuGet não disponíveis para o .NET Core

As bibliotecas de terceiros estão adotando rapidamente [.net Standard](../../../standard/net-standard.md), o que permite o compartilhamento de código em todos os tipos .net, incluindo o .NET Core. Com o .NET Standard 2,0 e posterior, a compatibilidade da superfície de API em diferentes estruturas se tornou significativamente maior. Ainda mais, o .NET Core 2. x e os aplicativos mais recentes também podem fazer referência direta a bibliotecas de .NET Framework existentes (Confira [.NET Framework 4.6.1 com suporte a .NET Standard 2,0](https://github.com/dotnet/standard/blob/master/docs/planning/netstandard-2.0/README.md#net-framework-461-supporting-net-standard-20)).

Além disso, o [pacote de compatibilidade do Windows](../../../core/porting/windows-compat-pack.md) estende a superfície de API disponível para .net Standard 2,0 no Windows. Este pacote permite recompilar a maioria do código existente para o .NET Standard 2.x com pouca ou nenhuma modificação para ser executado no Windows.

No entanto, mesmo com essa progressão excepcional desde o .NET Standard 2.0 e o .NET Core 2.1, pode haver casos em que determinados pacotes NuGet precisam do Windows para serem executados e não dão suporte ao .NET Core. Se esses pacotes forem críticos ao aplicativo, será necessário usar o .NET Framework em contêineres do Windows.

## <a name="using-net-technologies-not-available-for-net-core"></a>Usando tecnologias do .NET não disponíveis para .NET Core

Algumas tecnologias .NET Framework não estão disponíveis na versão atual do .NET Core (versão 3,1 no momento da elaboração deste artigo). Alguns deles podem ser disponibilizados em versões posteriores, mas outros não se ajustam aos novos padrões de aplicativo destinados ao .NET Core e podem nunca estar disponíveis.

A lista a seguir mostra a maioria das tecnologias que não estão disponíveis no .NET Core 3,1:

- Web Forms do ASP.NET. Esta tecnologia só está disponível no .NET Framework. Atualmente, não há planos para trazer os Web Forms do ASP.NET para o .NET Core.

- Serviços WCF. Mesmo quando uma [biblioteca de cliente WCF](https://github.com/dotnet/wcf) está disponível para consumir serviços WCF do .NET Core, a partir de fev-2020, a implementação do servidor WCF só está disponível no .NET Framework. Esse cenário pode ser considerado para versões futuras do .NET Core. Há, inclusive, algumas APIs consideradas para inclusão no [Pacote de Compatibilidade do Windows](../../../core/porting/windows-compat-pack.md).

- Serviços relacionados a fluxo de trabalho. O Windows WF (Workflow Foundation), os Serviços de fluxo de trabalho (WCF + WF em um único serviço) e o WCF Data Services (anteriormente conhecido como Serviços de Dados ADO.NET) só estão disponíveis no .NET Framework. No momento, não há planos para colocá-los no .NET Core.

Além das tecnologias listadas no roteiro oficial do [.NET Core](https://github.com/dotnet/core/blob/master/roadmap.md), outros recursos podem ser portados para o .NET Core ou para a nova [plataforma .net unificada](https://devblogs.microsoft.com/dotnet/introducing-net-5/). Você pode considerar participar das discussões no GitHub para que sua voz possa ser ouvida. E se você acreditar que algo está faltando, execute um novo problema no repositório do GitHub [dotnet/tempo de execução](https://github.com/dotnet/runtime/issues/new) .

## <a name="using-a-platform-or-api-that-doesnt-support-net-core"></a>Usando uma plataforma ou API que não dá suporte ao .NET Core

Algumas plataformas da Microsoft e de terceiros não oferecem suporte ao .NET Core. Por exemplo, alguns serviços do Azure fornecem um SDK que ainda não está disponível para consumo no .NET Core. A maioria dos SDK do Azure deve, eventualmente, ser portado para o .NET Core/Standard, mas alguns podem não por vários motivos. Você pode ver os SDKs do Azure disponíveis na página [versões mais recentes do SDK do Azure](https://azure.github.io/azure-sdk/releases/latest/index.html) .

Enquanto isso, se qualquer plataforma ou o serviço no Azure ainda não der suporte ao .NET Core com sua API do cliente, será possível usar a API REST equivalente do serviço do Azure ou o SDK do cliente no .NET Framework.

### <a name="additional-resources"></a>Recursos adicionais

- **Conceitos básicos do .NET** \
  [https://docs.microsoft.com/dotnet/fundamentals](../../../fundamentals/index.yml)

- **Portando de .NET Framework para o .NET Core** \
  [https://docs.microsoft.com/dotnet/core/porting/index](../../../core/porting/index.md)

- **.NET Core no guia do Docker** \
  [https://docs.microsoft.com/dotnet/core/docker/introduction](../../../core/docker/introduction.md)

- **Visão geral dos componentes .NET** \
  [https://docs.microsoft.com/dotnet/standard/components](../../../standard/components.md)

>[!div class="step-by-step"]
>[Anterior](net-core-container-scenarios.md) 
> [Avançar](container-framework-choice-factors.md)
