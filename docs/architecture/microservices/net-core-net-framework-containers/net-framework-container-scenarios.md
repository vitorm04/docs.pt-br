---
title: Quando escolher o .NET Framework para os contêineres do Docker
description: Arquitetura de microsserviços do .NET para aplicativos .NET em contêineres | Quando escolher o .NET Framework para os contêineres do Docker
ms.date: 01/07/2019
ms.openlocfilehash: 8316d17aae09ddbd70bd80af4f06d8cb029f2752
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73093760"
---
# <a name="when-to-choose-net-framework-for-docker-containers"></a>Quando escolher o .NET Framework para os contêineres do Docker

Embora o .NET Core ofereça benefícios significativos para novos aplicativos e padrões de aplicativo, o .NET Framework continuará sendo uma boa escolha para muitos cenários existentes.

## <a name="migrating-existing-applications-directly-to-a-windows-server-container"></a>Migrando aplicativos existentes diretamente para um contêiner do Windows Server

Talvez convenha usar contêineres do Docker apenas para simplificar a implantação, mesmo se você não estiver criando microsserviços. Por exemplo, talvez convenha aprimorar seu fluxo de trabalho DevOps com o Docker — os contêineres podem oferecer ambientes de teste mais bem isolados e também podem eliminar problemas de implantação causados por dependências ausentes quando você muda para um ambiente de produção. Em casos assim, mesmo se você estiver implantando um aplicativo monolítico, faz sentido usar os contêineres do Docker e do Windows para seus aplicativos .NET Framework atuais.

Na maioria dos casos desse cenário, não será necessário migrar seus aplicativos existentes para o .NET Core; é possível usar contêineres do Docker que incluem o .NET Framework tradicional. Contudo, uma abordagem recomendada é usar o .NET Core ao estender um aplicativo existente, por exemplo, para gravar um novo serviço no ASP.NET Core.

## <a name="using-third-party-net-libraries-or-nuget-packages-not-available-for-net-core"></a>Usando bibliotecas .NET de terceiros ou pacotes NuGet não disponíveis para o .NET Core

Bibliotecas de terceiros estão rapidamente adotando o [.NET Standard](../../../standard/net-standard.md), que permite o compartilhamento de código em todas as versões do .NET, incluindo o .NET Core. Com a Biblioteca 2.0 e posterior do .NET Standard, a compatibilidade da superfície de API tornou-se significativamente maior e, nos .NET Core 2.x, os aplicativos também podem referenciar diretamente bibliotecas do .NET Framework existentes (confira [.NET Framework 4.6.1 com suporte para .NET Standard 2.0](https://github.com/dotnet/standard/blob/master/docs/planning/netstandard-2.0/README.md#net-framework-461-supporting-net-standard-20)).

Além disso, o [Pacote de Compatibilidade do Windows](../../../core/porting/windows-compat-pack.md) foi lançado em novembro de 2017 para estender a superfície de API disponível para .NET Standard 2.0 no Windows. Este pacote permite recompilar a maioria do código existente para o .NET Standard 2.x com pouca ou nenhuma modificação para ser executado no Windows.

No entanto, mesmo com essa progressão excepcional desde o .NET Standard 2.0 e o .NET Core 2.1, pode haver casos em que determinados pacotes NuGet precisam do Windows para serem executados e não dão suporte ao .NET Core. Se esses pacotes forem críticos ao aplicativo, será necessário usar o .NET Framework em contêineres do Windows.

## <a name="using-net-technologies-not-available-for-net-core"></a>Usando tecnologias do .NET não disponíveis para .NET Core

Algumas tecnologias do .NET Framework não estão disponíveis na versão atual do .NET Core (versão 2.2 no momento da redação deste artigo). Algumas delas estarão disponíveis em versões posteriores do .NET Core (.NET Core 2.x), mas outras não se aplicam a novos padrões de aplicativos direcionados ao .NET Core e talvez nunca estejam disponíveis.

A lista a seguir mostra a maioria das tecnologias que não estão disponíveis no .NET Core 2.x:

- Web Forms do ASP.NET. Esta tecnologia só está disponível no .NET Framework. Atualmente, não há planos para trazer os Web Forms do ASP.NET para o .NET Core.

- Serviços WCF. Mesmo que uma [biblioteca de clientes WCF](https://github.com/dotnet/wcf) esteja disponível para consumir serviços WCF do .NET Core, desde meados de 2017, a implementação do servidor WCF está disponível apenas no .NET Framework. Esse cenário pode ser considerado para versões futuras do .NET Core. Há, inclusive, algumas APIs consideradas para inclusão no [Pacote de Compatibilidade do Windows](../../../core/porting/windows-compat-pack.md).

- Serviços relacionados a fluxo de trabalho. O Windows WF (Workflow Foundation), os Serviços de fluxo de trabalho (WCF + WF em um único serviço) e o WCF Data Services (anteriormente conhecido como Serviços de Dados ADO.NET) só estão disponíveis no .NET Framework. No momento, não há planos para colocá-los no .NET Core.

Além das tecnologias listadas no [roteiro oficial do .NET Core](https://github.com/aspnet/Home/wiki/Roadmap), talvez outros recursos sejam movidos para o .NET Core. Para obter uma lista completa, examine os itens marcados como [port-to-core](https://github.com/dotnet/corefx/issues?q=is%3Aopen+is%3Aissue+label%3Aport-to-core) no site do GitHub do CoreFX. Observe que esta lista não representa um compromisso da Microsoft de colocar esses componentes no .NET Core – os itens simplesmente capturam solicitações da comunidade. Se você se importar com qualquer um dos componentes listados acima, considere a possibilidade de participar de discussões no GitHub para que sua voz seja ouvida. E se você achar que algo está faltando, [envie uma nova questão no repositório do CoreFX](https://github.com/dotnet/corefx/issues/new).

Embora o .NET Core 3 (no momento da redação deste artigo, isso está nos trabalhos) vá incluir suporte para muitas APIs existentes do .NET Framework, elas são orientadas para área de trabalho, assim, no momento, não têm utilidade no mundo do contêiner.

## <a name="using-a-platform-or-api-that-does-not-support-net-core"></a>Usando uma plataforma ou uma API não compatível com o .NET Core

Algumas plataformas de terceiros ou da Microsoft não são compatíveis com o .NET Core. Por exemplo, alguns serviços do Azure oferecem um SDK que ainda não está disponível para consumo no .NET Core. Isso é temporário, porque todos os serviços do Azure eventualmente usarão o .NET Core. Por exemplo, o [SDK do DocumentDB do Azure para .NET Core](https://www.nuget.org/packages/Microsoft.Azure.DocumentDB.Core) foi lançado como uma versão prévia em 16 de novembro de 2016, mas agora está GA (geralmente disponível) como uma versão estável.

Enquanto isso, se qualquer plataforma ou o serviço no Azure ainda não der suporte ao .NET Core com sua API do cliente, será possível usar a API REST equivalente do serviço do Azure ou o SDK do cliente no .NET Framework.

### <a name="additional-resources"></a>Recursos adicionais

- **Guia do .NET Core**  
  [https://docs.microsoft.com/dotnet/core/index](../../../core/index.md)

- **Portabilidade do .NET Framework para .NET Core**  
  [https://docs.microsoft.com/dotnet/core/porting/index](../../../core/porting/index.md)

- **Guia do .NET Core no Docker** [https://docs.microsoft.com/dotnet/core/docker/introduction](../../../core/docker/introduction.md)

- **Visão Geral dos Componentes .NET**  
  [https://docs.microsoft.com/dotnet/standard/components](../../../standard/components.md)

>[!div class="step-by-step"]
>[Anterior](net-core-container-scenarios.md)
>[Próximo](container-framework-choice-factors.md)
