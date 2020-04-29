---
title: Escolher entre .NET Core e .NET Framework para aplicativos de servidor
description: Um guia para ajudá-lo a decidir qual implementação do .NET usar ao criar um aplicativo de servidor.
author: cartermp
ms.date: 04/28/2020
ms.openlocfilehash: 30157276bce53ed44dca5b660172e5556dab14f8
ms.sourcegitcommit: 1cb64b53eb1f253e6a3f53ca9510ef0be1fd06fe
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/29/2020
ms.locfileid: "82507436"
---
# <a name="net-core-vs-net-framework-for-server-apps"></a>.NET Core versus .NET Framework para aplicativos de servidor

Há duas implementações de .NET com suporte para a criação de aplicativos do lado do servidor: .NET Framework e .NET Core. Ambas compartilham muitos dos mesmos componentes e você pode compartilhar código entre as duas. No entanto, há diferenças fundamentais entre as duas e sua escolha depende do que você deseja realizar. Este artigo diretrizes sobre quando usar cada um.

Use o .NET Core para o aplicativo para servidores se:

- Você tiver necessidades de plataforma cruzada.
- Você está direcionando para os microserviços.
- Você está usando contêineres do Docker.
- Você precisar de alto desempenho e sistemas escalonáveis.
- Você precisar de versões do .NET correspondentes a cada aplicativo.

Use o .NET Framework para o aplicativo para servidores se:

- Seu aplicativo usar o .NET Framework atualmente (a recomendação é estender em vez de migrar).
- Seu aplicativo usa bibliotecas .NET de terceiros ou pacotes NuGet não disponíveis para o .NET Core.
- Seu aplicativo usa tecnologias .NET que não estão disponíveis para o .NET Core.
- Seu aplicativo usa uma plataforma que não oferece suporte ao .NET Core. Windows, macOS e Linux dão suporte ao .NET Core.

## <a name="when-to-choose-net-core"></a>Quando escolher o .NET Core

As seguintes seções oferecem uma explicação mais detalhada sobre os motivos para escolher o .NET Core mencionados anteriormente.

### <a name="cross-platform-needs"></a>Necessidades de plataforma cruzada

Se seu aplicativo (web/serviço) precisa ser executado em várias plataformas (Windows, Linux e macOS), use o .NET Core.

O .NET Core dá suporte aos sistemas operacionais mencionados anteriormente como sua estação de trabalho de desenvolvimento. O Visual Studio fornece um IDE (ambiente de desenvolvimento integrado) para Windows e macOS. Você também pode usar o Visual Studio Code, que é executado no Windows, Linux e macOS. O Visual Studio Code dá suporte ao .NET Core, incluindo IntelliSense e depuração. A maioria dos editores de terceiros, como Sublime, Emacs e VI, trabalham com o .NET Core. Esses editores de terceiros obtém o IntelliSense do editor usando o [Omnisharp](https://www.omnisharp.net/). Você também pode evitar qualquer editor de código e usar diretamente o [CLI do .NET Core](../core/tools/index.md), disponível para todas as plataformas com suporte.

### <a name="microservices-architecture"></a>Arquitetura de microsserviços

Uma arquitetura de microsserviços possibilita uma combinação de tecnologias em um limite de serviço. Essa combinação de tecnologias permite uma adoção gradual do .NET Core para novos microsserviços que funcionam com outros serviços ou microsserviços. Por exemplo, você pode combinar microsserviços ou serviços desenvolvidos com .NET Framework, Java, Ruby ou outras tecnologias monolíticas.

Há muitas plataformas de infraestrutura disponíveis. O [Azure Service Fabric](https://azure.microsoft.com/services/service-fabric/) é criado para sistemas de microsserviço grandes e complexos. O [Serviço de Aplicativo do Azure](https://azure.microsoft.com/services/app-service/) é uma boa escolha para microsserviços sem monitoração de estado. Alternativas de microsserviços baseadas em Docker se adaptam a qualquer tipo de abordagem de microsserviços, conforme explicado na seção [Contêineres](#containers). Todas essas plataformas oferecem suporte ao .NET Core e são ideais para hospedar microsserviços.

Para obter mais informações sobre a arquitetura de microserviços, consulte [microservices do .net. Arquitetura para aplicativos .NET em contêineres](../architecture/microservices/index.md).

### <a name="containers"></a>Contêineres

Os contêineres são frequentemente usados em conjunto com uma arquitetura de microsserviços. Os contêineres também podem ser usados para colocar em contêiner os aplicativos ou serviços Web que seguem qualquer padrão de arquitetura. O .NET Framework pode ser usado em contêineres do Windows, mas a modularidade e a natureza leve do .NET Core o tornam uma opção melhor para contêineres. Ao criar e implantar um contêiner, o tamanho de sua imagem será muito menor com o .NET Core que com o .NET Framework. Como ele é multiplataforma, é possível implantar aplicativos para servidores em contêineres do Docker do Linux, por exemplo.

Os contêineres do Docker podem ser hospedados em sua própria infraestrutura do Windows ou do Linux ou em um serviço de nuvem, como o [Serviço de Kubernetes do Azure](https://azure.microsoft.com/services/kubernetes-service/). O Serviço de Kubernetes do Azure pode gerenciar, orquestrar e dimensionar aplicativos baseados em contêiner na nuvem.

### <a name="high-performance-and-scalable-systems"></a>Sistemas escalonáveis e de alto desempenho

Quando o seu sistema precisa do melhor desempenho e escalabilidade possíveis, o .NET Core e o ASP.NET Core são as melhores opções. O runtime do servidor de alto desempenho para Windows Server e Linux tornam o .NET uma estrutura da Web de desempenho superior nas [avaliações da TechEmpower](https://www.techempower.com/benchmarks/#hw=ph&test=plaintext).

O desempenho e a escalabilidade são especialmente relevantes para arquiteturas de microsserviços, nas quais centenas de microsserviços podem estar em execução. Com o ASP.NET Core, os sistemas são executados com um número bem menor de servidores/VMs (Máquinas Virtuais). A redução em servidores/VMs gera economia em infraestrutura e hospedagem.

### <a name="side-by-side-net-versions-per-application-level"></a>Versões do .NET lado a lado por nível de aplicativo

Para instalar aplicativos com dependências em diferentes versões do .NET, é recomendável o .NET Core. O .NET Core dá suporte à instalação lado a lado de diferentes versões do tempo de execução do .NET Core no mesmo computador. Essa instalação lado a lado permite vários serviços no mesmo servidor, cada um em sua própria versão do .NET Core. Ela também reduz os riscos e gera economia financeira nas operações de TI e atualizações de aplicativo.

A instalação lado a lado não é possível com .NET Framework. É um componente do Windows, e apenas uma versão pode existir em um computador de cada vez. Cada versão do .NET Framework substitui a versão anterior. Se você instalar um novo aplicativo direcionado a uma versão mais recente do .NET Framework, poderá interromper os aplicativos existentes que são executados no computador, pois a versão anterior foi substituída.

## <a name="when-to-choose-net-framework"></a>Quando escolher o .NET Framework

O .NET Core oferece benefícios significativos para novos aplicativos e padrões de aplicativo. No entanto, .NET Framework continua sendo a escolha natural para muitos cenários existentes e, dessa forma, .NET Framework não é substituído pelo .NET Core para todos os aplicativos de servidor.

### <a name="current-net-framework-applications"></a>Aplicativos .NET Framework atuais

Na maioria dos casos, não é necessário migrar aplicativos existentes para o .NET Core. Em vez disso, uma abordagem recomendada é usar o .NET Core ao estender um aplicativo existente, por exemplo, para gravar um novo serviço Web no ASP.NET Core.

### <a name="aspnet-core-on-net-framework"></a>ASP.NET Core em .NET Framework

Para obter informações sobre o suporte para ASP.NET Core no .NET Framework, consulte a [política de suporte do .NET Core](https://dotnet.microsoft.com/platform/support/policy/dotnet-core).

### <a name="third-party-libraries-or-nuget-packages-not-available-for-net-core"></a>Bibliotecas de terceiros ou pacotes NuGet não disponíveis para o .NET Core

As bibliotecas estão rapidamente adotando o .NET Standard. O .NET Standard permite o compartilhamento de código em todas as implementações do .NET, incluindo o .NET Core. Com o .NET Standard 2.0, isso é ainda mais fácil:

- A superfície de API se tornou muito maior.
- Ele introduziu um modo de compatibilidade .NET Framework.

  Esse modo de compatibilidade permite que os projetos do .NET Standard e do .NET Core referenciem bibliotecas do .NET Framework. Para saber mais sobre o modo de compatibilidade, consulte o [Comunicado do .NET Standard 2.0](https://devblogs.microsoft.com/dotnet/announcing-net-standard-2-0/).

Você precisa usar .NET Framework apenas nos casos em que as bibliotecas ou os pacotes NuGet usam tecnologias que não estão disponíveis no .NET Standard ou no .NET Core.

### <a name="net-technologies-not-available-for-net-core"></a>Tecnologias .NET não disponíveis para o .NET Core

Algumas tecnologias do .NET Framework não estão disponíveis no .NET Core. Algumas delas poderão ser disponibilizadas em versões posteriores do .NET Core. Outras não se aplicam aos novos padrões de aplicativo direcionados pelo .NET Core e podem não ser mais disponibilizadas. A lista a seguir mostra as tecnologias mais comuns não encontradas no .NET Core:

- ASP.NET Web Forms aplicativos: ASP.NET Web Forms estão disponíveis apenas no .NET Framework. O ASP.NET Core não pode ser usado para Web Forms do ASP.NET. Não há planos para trazer os Web Forms do ASP.NET para o .NET Core.

- Aplicativos de páginas da Web do ASP.NET: as páginas da Web do ASP.NET não estão incluídas no ASP.NET Core.

- Implementação de serviços do WCF. Mesmo quando há uma [biblioteca de cliente WCF](https://github.com/dotnet/wcf) para consumir serviços do WCF do .NET Core, a implementação do servidor WCF está disponível atualmente apenas no .NET Framework. Esse cenário não faz parte do plano atual para o .NET Core, mas está sendo considerado para o futuro.

- Serviços relacionados a fluxo de trabalho: Windows Workflow Foundation (WF), serviços de fluxo de trabalho (WCF + WF em um único serviço) e WCF Data Services (anteriormente conhecidos como "serviços de dados ADO.NET") estão disponíveis somente no .NET Framework. Não há planos para trazer essas tecnologias para o .NET Core.

- Suporte de linguagem: atualmente há suporte para Visual Basic e F# no .NET Core, mas não para todos os tipos de projeto. Para obter uma lista de modelos de projeto com suporte, consulte [Opções de modelo para o dotnet new](../core/tools/dotnet-new.md#arguments).

### <a name="platform-doesnt-support-net-core"></a>A plataforma não dá suporte ao .NET Core

Algumas plataformas de terceiros ou da Microsoft não oferecem suporte a .NET Core. Alguns serviços do Azure fornecem um SDK que ainda não está disponível para ser consumido no .NET Core. Esta é uma circunstância transitória, pois todos os serviços do Azure usam o .NET Core. Enquanto isso, você pode usar a API REST equivalente em vez do SDK do cliente.

## <a name="see-also"></a>Confira também

- [Escolher entre o ASP.NET e o ASP.NET Core](/aspnet/core/choose-aspnet-framework)
- [ASP.NET Core direcionado para o .NET Framework](/aspnet/core/introduction-to-aspnet-core#aspnet-core-targeting-net-framework)
- [Frameworks de destino](frameworks.md)
- [Guia do .NET Core](../core/index.yml)
- [Portabilidade do .NET Framework para o .NET Core](../core/porting/index.md)
- [Introdução ao .NET e ao Docker](../core/docker/introduction.md)
- [Visão Geral dos Componentes do .NET](components.md)
- [Microserviços .NET. Arquitetura para aplicativos .NET em contêineres](../architecture/microservices/index.md)
