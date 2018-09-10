---
title: Escolher entre .NET Core e .NET Framework para aplicativos de servidor
description: Um guia sobre qual implementação de .NET você deve considerar ao compilar um aplicativo de servidor no .NET.
author: cartermp
ms.author: mairaw
ms.date: 06/19/2018
ms.openlocfilehash: dbb5bd21d2fa43167a9624be2baec3f591d10920
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/06/2018
ms.locfileid: "43864956"
---
# <a name="choosing-between-net-core-and-net-framework-for-server-apps"></a>Escolhendo entre o .NET Core e .NET Framework para aplicativos de servidor

Há duas implementações com suporte para a compilação de aplicativos de servidor com o .NET: .NET Framework e .NET Core. Ambas compartilham muitos dos mesmos componentes e você pode compartilhar código entre as duas. No entanto, há diferenças fundamentais entre as duas e sua escolha depende do que você deseja realizar.  Este artigo fornece diretrizes sobre quando usar cada uma.

Use o .NET Core para o aplicativo para servidores se:

* Você tiver necessidades de plataforma cruzada.
* Você estiver direcionando microsserviços.
* Você estiver usando contêineres do Docker.
* Você precisar de alto desempenho e sistemas escalonáveis.
* Você precisar de versões do .NET correspondentes a cada aplicativo.

Use o .NET Framework para o aplicativo para servidores se:

* Seu aplicativo usar o .NET Framework atualmente (a recomendação é estender em vez de migrar).
* Seu aplicativo usa bibliotecas .NET de terceiros ou pacotes NuGet não disponíveis para o .NET Core.
* Seu aplicativo usa tecnologias .NET que não estão disponíveis para o .NET Core.
* Seu aplicativo usa uma plataforma que não oferece suporte ao .NET Core.

## <a name="when-to-choose-net-core"></a>Quando escolher o .NET Core

As seguintes seções oferecem uma explicação mais detalhada sobre os motivos para escolher o .NET Core mencionados anteriormente.

### <a name="cross-platform-needs"></a>Necessidades de plataforma cruzada

Se seu aplicativo (web/serviço) precisa ser executado em várias plataformas (Windows, Linux e macOS), use o .NET Core.

O .NET Core dá suporte aos sistemas operacionais mencionados anteriormente como sua estação de trabalho de desenvolvimento. O Visual Studio fornece um IDE (ambiente de desenvolvimento integrado) para Windows e macOS. Você também pode usar o Visual Studio Code, que é executado no Windows, Linux e macOS. O Visual Studio Code dá suporte ao .NET Core, incluindo IntelliSense e depuração. A maioria dos editores de terceiros, como Sublime, Emacs e VI, trabalham com o .NET Core. Esses editores de terceiros obtém o IntelliSense do editor usando o [Omnisharp](https://www.omnisharp.net/). Também é possível evitar o uso de editores de código e usar diretamente as [ferramentas de CLI do .NET Core](../core/tools/index.md), disponíveis para todas as plataformas com suporte.

### <a name="microservices-architecture"></a>Arquitetura de microsserviços

Uma arquitetura de microsserviços possibilita uma combinação de tecnologias em um limite de serviço. Essa combinação de tecnologias permite uma adoção gradual do .NET Core para novos microsserviços que funcionam com outros serviços ou microsserviços. Por exemplo, você pode combinar microsserviços ou serviços desenvolvidos com .NET Framework, Java, Ruby ou outras tecnologias monolíticas.

Há muitas plataformas de infraestrutura disponíveis. O [Azure Service Fabric](https://azure.microsoft.com/services/service-fabric/) é criado para sistemas de microsserviço grandes e complexos. O [Serviço de Aplicativo do Azure](https://azure.microsoft.com/services/app-service/) é uma boa escolha para microsserviços sem monitoração de estado. Alternativas de microsserviços baseadas em Docker se adaptam a qualquer tipo de abordagem de microsserviços, conforme explicado na seção [Contêineres](#containers). Todas essas plataformas oferecem suporte ao .NET Core e são ideais para hospedar microsserviços.

Para obter mais informações sobre a arquitetura de microsserviços, consulte [Microsserviços do .NET. Arquitetura para aplicativos .NET em contêineres](microservices-architecture/index.md).

### <a name="containers"></a>Contêineres

Os contêineres são frequentemente usados em conjunto com uma arquitetura de microsserviços. Os contêineres também podem ser usados para colocar em contêiner os aplicativos ou serviços Web que seguem qualquer padrão de arquitetura. O .NET Framework pode ser usado em contêineres do Windows, mas a modularidade e a natureza leve do .NET Core o tornam uma opção melhor para contêineres. Ao criar e implantar um contêiner, o tamanho de sua imagem será muito menor com o .NET Core que com o .NET Framework. Como ele é multiplataforma, é possível implantar aplicativos para servidores em contêineres do Docker do Linux, por exemplo.

Os contêineres do Docker podem ser hospedados em sua própria infraestrutura do Windows ou do Linux ou em um serviço de nuvem, como o [Serviço de Contêiner do Azure](https://azure.microsoft.com/services/container-service/). O Serviço de Contêiner do Azure pode gerenciar, orquestrar e dimensionar aplicativos baseados em contêiner na nuvem.

### <a name="a-need-for-high-performance-and-scalable-systems"></a>Uma necessidade de alto desempenho e sistemas escalonáveis

Quando o seu sistema precisa do melhor desempenho e escalabilidade possíveis, o .NET Core e o ASP.NET Core são as melhores opções. O tempo de execução do servidor de alto desempenho para Windows Server e Linux tornam o .NET uma estrutura da Web de desempenho superior nas [avaliações da TechEmpower](https://www.techempower.com/benchmarks/#hw=ph&test=plaintext).

O desempenho e a escalabilidade são especialmente relevantes para arquiteturas de microsserviços, nas quais centenas de microsserviços podem estar em execução. Com o ASP.NET Core, os sistemas são executados com um número bem menor de servidores/VMs (Máquinas Virtuais). A redução em servidores/VMs gera economia em infraestrutura e hospedagem.

### <a name="a-need-for-side-by-side-of-net-versions-per-application-level"></a>Necessidade de lado a lado de versões do .NET por nível de aplicativo

Para instalar aplicativos com dependências em diferentes versões do .NET, é recomendável o .NET Core. O .NET core oferece instalação lado a lado de versões diferentes do tempo de execução do .NET Core no mesmo computador. Essa instalação lado a lado permite vários serviços no mesmo servidor, cada um em sua própria versão do .NET Core. Ela também reduz os riscos e gera economia financeira nas operações de TI e atualizações de aplicativo.

## <a name="when-to-choose-net-framework"></a>Quando escolher o .NET Framework

O .NET Core oferece benefícios significativos para novos aplicativos e padrões de aplicativo. No entanto, o .NET Framework continua sendo a escolha natural para muitos cenários existentes e, portanto, não é substituído pelo .NET Core em todos os aplicativos para servidores.

### <a name="current-net-framework-applications"></a>Aplicativos .NET Framework atuais

Na maioria dos casos, não é necessário migrar aplicativos existentes para o .NET Core. Em vez disso, uma abordagem recomendada é usar o .NET Core ao estender um aplicativo existente, por exemplo, para gravar um novo serviço Web no ASP.NET Core.

### <a name="a-need-to-use-third-party-net-libraries-or-nuget-packages-not-available-for-net-core"></a>Necessidade de usar bibliotecas .NET de terceiros ou pacotes NuGet não disponíveis para o .NET Core

As bibliotecas estão rapidamente adotando o .NET Standard. O .NET Standard permite o compartilhamento de código entre todas as implementações do .NET, incluindo o .NET Core. Com o .NET Standard 2.0, isso é ainda mais fácil:

- A superfície de API se tornou muito maior. 
- Foi introduzido um modo de compatibilidade do .NET Framework. Este modo de compatibilidade permite que os projetos do .NET Standard/.NET Core referenciem bibliotecas do .NET Framework. Para saber mais sobre o modo de compatibilidade, consulte o [Comunicado do .NET Standard 2.0](https://blogs.msdn.microsoft.com/dotnet/2017/08/14/announcing-net-standard-2-0/).

Portanto, apenas nos casos em que as bibliotecas ou pacotes NuGet usarem tecnologias que não estão disponíveis no .NET Standard/.NET Core, você precisará usar o .NET Framework.

### <a name="a-need-to-use-net-technologies-not-available-for-net-core"></a>Necessidade de usar as tecnologias do .NET que não estão disponíveis para .NET Core

Algumas tecnologias do .NET Framework não estão disponíveis no .NET Core. Algumas delas poderão ser disponibilizadas em versões posteriores do .NET Core. Outras não se aplicam aos novos padrões de aplicativo direcionados pelo .NET Core e podem não ser mais disponibilizadas. A lista a seguir mostra as tecnologias mais comuns não encontradas no .NET Core:

* Aplicativos de Web Forms do ASP.NET: Web Forms do ASP.NET só estão disponíveis no .NET Framework. O ASP.NET Core não pode ser usado para Web Forms do ASP.NET. Não há planos para trazer os Web Forms do ASP.NET para o .NET Core.

* Aplicativos de páginas da Web do ASP.NET: as páginas da Web do ASP.NET não estão incluídas no ASP.NET Core. As [páginas Razor](/aspnet/core/mvc/razor-pages/) do ASP.NET Core têm muitas semelhanças com páginas da Web.

* Implementação de serviços do WCF. Mesmo que haja uma [Biblioteca de Cliente WCF](https://github.com/dotnet/wcf) para consumir serviços WCF no .NET Core, a implementação de servidor do WCF só está disponível no .NET Framework no momento. Esse cenário não é parte do plano atual para o .NET Core, mas ele está sendo considerado para o futuro.

* Serviços relacionados a fluxo de trabalho: o Windows WF (Workflow Foundation), os Serviços de fluxo de trabalho (WCF + WF em um único serviço) e o WCF Data Services (anteriormente conhecido como "ADO.NET Data Services") só estão disponíveis no .NET Framework.  Não há planos para trazer WF/WCF+WF/WCF Data Services para o .NET Core.

* Suporte de linguagem: atualmente há suporte para Visual Basic e F# no .NET Core, mas não para todos os tipos de projeto. Para obter uma lista de modelos de projeto com suporte, consulte [Opções de modelo para o dotnet new](../core/tools/dotnet-new.md#arguments).

Além do roteiro oficial, há outras estruturas a serem transferidas para o .NET Core. Para obter uma lista completa, consulte os problemas de CoreFX marcados como [port-to-core](https://github.com/dotnet/corefx/issues?q=is%3Aopen+is%3Aissue+label%3Aport-to-core). Essa lista não representa um compromisso da Microsoft para levar esses componentes para o .NET Core. Ela simplesmente captura o desejo da comunidade para que isso seja feito. Se você se importa com qualquer um dos componentes marcados como `port-to-core`, participe das discussões no GitHub. E se você acha que algo está faltando, envie uma nova questão no [repositório do CoreFX](https://github.com/dotnet/corefx/issues/new).

### <a name="a-need-to-use-a-platform-that-doesnt-support-net-core"></a>Necessidade de usar uma plataforma que não oferece suporte a .NET Core

Algumas plataformas de terceiros ou da Microsoft não oferecem suporte a .NET Core. Por exemplo, alguns serviços do Azure, como Reliable Services de Serviço de Monitoração com Estado de Malha e Reliable Actors da Malha de Serviço requerem o .NET Framework. Alguns outros serviços fornecem uma SDK ainda não estão disponível para consumo no .NET Core. Esta é uma circunstância transitória, pois todos os serviços do Azure usam o .NET Core. Enquanto isso, você sempre pode usar a API REST equivalente em vez do SDK do cliente.

## <a name="see-also"></a>Consulte também

* [Escolher entre o ASP.NET e o ASP.NET Core](/aspnet/core/choose-aspnet-framework)
* [Estruturas de destino](frameworks.md)
* [Guia do .NET Core](../core/index.md)  
* [Portabilidade do .NET Framework para .NET Core](../core/porting/index.md)  
* [.NET Framework no Guia do Docker](../framework/docker/index.md)  
* [Visão Geral dos Componentes .NET](components.md)  
* [Microsserviços .NET. Arquitetura para aplicativos .NET em contêineres](microservices-architecture/index.md)
