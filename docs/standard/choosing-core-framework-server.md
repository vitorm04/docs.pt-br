---
title: Escolhendo entre o .NET Core e .NET Framework para aplicativos de servidor
description: "Um guia sobre qual tipo de .NET você deve considerar ao compilar um aplicativo de servidor no .NET."
keywords: .NET, .NET Core, .NET Framework
author: cartermp
manager: wpickett
ms.author: phcart
ms.date: 11/16/2016
ms.topic: article
ms.prod: .net-core
ms.technology: .net-core-technologies
ms.devlang: dotnet
ms.assetid: 155553e4-89a2-418d-be88-4e75f6c3cc69
translationtype: Human Translation
ms.sourcegitcommit: d6ce9e3dd3c1189f35d147d140bb45095b3d77a5
ms.openlocfilehash: a0563f7437711ddbee309803e97ab653aa160337

---

# <a name="choosing-between-net-core-and-net-framework-for-server-apps"></a>Escolhendo entre o .NET Core e .NET Framework para aplicativos de servidor

Há duas opções com suporte de tempo de execução para a compilação de aplicativos de servidor com o .NET: .NET Framework e .NET Core. Ambos compartilham muitos dos mesmos componentes da plataforma .NET e você pode compartilhar códigos entre os dois. No entanto, há diferenças fundamentais entre os dois e sua escolha dependerá do que você deseja realizar.  Este artigo diretrizes sobre quando usar cada um.

Você deve usar o .NET Core para o aplicativo para servidores se:

* Você tiver necessidades de plataforma cruzada.
* Você estiver direcionando microsserviços.
* Você estiver usando contêineres do Docker.
* Você precisar de alto desempenho e sistemas escalonáveis.
* Você precisar de lado a lado de versões do .NET por aplicativo.

Você deve usar o .NET Framework para o aplicativo para servidores se:

* Seu aplicativo usar o .NET Framework atualmente (a recomendação é estender em vez de migrar)
* Você precisar usar bibliotecas .NET de terceiros ou pacotes NuGet não disponíveis para o .NET Core.
* Você precisar usar as tecnologias do .NET que não estão disponíveis para .NET Core.
* Você precisar usar uma plataforma que não oferece suporte a .NET Core.

## <a name="when-to-choose-net-core"></a>Quando escolher o .NET Core

A seguir está uma explicação mais detalhada dos motivos para escolher o .NET Core mencionados anteriormente.

### <a name="cross-platform-needs"></a>Necessidades de plataforma cruzada

Evidentemente, se o seu objetivo é ter um aplicativo (Web/serviço) que possa de ser executado entre plataformas (Windows, Linux e macOS), a melhor opção é o .NET Core.

O .NET Core também oferece suporte aos sistemas operacionais mencionados anteriormente e a sua estação de trabalho de desenvolvimento. O Visual Studio fornece um Ambiente De Desenvolvimento Integrado (IDE) do Windows.  Também é possível usar o código do Visual Studio no macOS, Linux e Windows, que oferecem suporte completo ao .NET Core, incluindo IntelliSense e depuração. Você também pode direcionar o .NET Core com a maioria dos editores de terceiros, como Sublime, Emacs, VI e pode obter o IntelliSense de editor usando o projeto de software livre [Omnisharp](http://www.omnisharp.net/). Também é possível evitar utilizar editores de código e usar diretamente as ferramentas de linha de comando do .NET Core, disponíveis para todas as plataformas com suporte.

### <a name="microservices-architecture"></a>Arquitetura de microsserviços

O .NET Core é a melhor escolha caso você esteja adotando um sistema baseado em microsserviços, composto por vários microsserviços independentes, dinamicamente escalonáveis, com ou sem estado. O .NET Core é leve e sua superfície de API pode ser minimizada de acordo com o escopo do microsserviço. Uma arquitetura de microsserviços também permite combinar tecnologias através de um limite de serviço, permitindo uma aceitação gradual do .NET Core para novos microsserviços que vivem em conjunto com outros microsserviços ou serviços desenvolvidos com o .NET Framework, Java, Ruby ou outras tecnologias monolíticas.

Você pode usar muitas plataformas de infraestrutura. Para sistemas de microsserviço grandes e complexos, é possível usar a [Azure Service Fabric](https://azure.microsoft.com/en-us/services/service-fabric/). Para microsserviços sem monitoração de estado, também é possível usar outros produtos como o [Serviço de Aplicativo do Azure](https://azure.microsoft.com/en-us/services/app-service/). Alternativas de microsserviços baseadas em Docker também se adaptam a qualquer tipo de abordagem de microsserviços, conforme explicado a seguir. Todas essas plataformas oferecem suporte ao .NET Core e são ideais para hospedar microsserviços.

### <a name="containers"></a>Contêineres

Contêineres são usados em conjunto com uma arquitetura de microsserviços, embora também possam ser usados para colocar em contêineres aplicativos Web ou serviços que sigam qualquer padrão de arquitetura. Você poderá usar os contêineres do .NET Framework para Windows, mas a natureza leve e a modularidade do .NET Core o torna perfeito para contêineres.  Ao criar e implantar um contêiner, o tamanho da imagem é muito menor com o .NET Core do que com o .NET Framework.  Como ele é multiplataforma, é possível implantar aplicativos de servidor para contêineres do Docker do Linux, por exemplo.

Você pode hospedar contêineres de Docker em sua própria infraestrutura do Windows ou Linux, ou usar um serviço de nuvem como [Serviço de Contêiner do Azure](https://azure.microsoft.com/en-us/services/container-service/), que pode gerenciar, organizar e dimensionar seu aplicativo baseado em contêiner na nuvem.

### <a name="a-need-for-high-performance-and-scalable-systems"></a>Necessidade de alto desempenho e sistemas escaláveis

Quando o seu sistema precisa do melhor desempenho e escalabilidade possíveis, o .NET Core e o ASP.NET Core são as melhores opções. O ASP.NET Core supera o ASP.NET por um fator de 10 e isso leva a outras tecnologias de indústria populares para microsserviços, como servlets Java, Go e node.js.

Isso é especialmente relevante para arquiteturas de microsserviços, em que é possível executar centenas de microsserviços. Com o ASP.NET Core, você poderia executar seu sistema com um número menor de servidores/VMs, economizando custos em infraestrutura e hospedagem.

### <a name="a-need-for-side-by-side-of-net-versions-per-application-level"></a>Necessidade de lado a lado de versões do .NET por nível de aplicativo

Se você quiser instalar aplicativos com dependências em versões diferentes de estruturas no .NET, use o .NET Core, que fornece 100% de lado a lado. A fácil instalação lado a lado de diferentes versões do .NET Core no mesmo computador permite que você tenha vários serviços no mesmo servidor, cada um em sua própria versão do .NET Core, eliminando os riscos e economizando em atualizações de aplicativos e operações de TI.

## <a name="when-to-choose-net-framework"></a>Quando escolher o .NET Framework

Embora o .NET Core ofereça benefícios significativos para novos aplicativos e padrões de aplicativo, o .NET Framework continuará a ser a escolha natural para muitos cenários existentes e, como tal, ele não ser substituído pelo .NET Core para todos os aplicativos de servidor.

### <a name="current-net-framework-applications"></a>Aplicativos .NET Framework atuais

Na maioria dos casos, não é necessário migrar aplicativos existentes para o .NET Core. Em vez disso, uma abordagem recomendada é usar o .NET Core ao estender um aplicativo existente, por exemplo, para gravar um novo serviço Web no ASP.NET Core.

### <a name="a-need-to-use-third-party-net-libraries-or-nuget-packages-not-available-for-net-core"></a>Necessidade de usar bibliotecas .NET de terceiros ou pacotes NuGet não disponíveis para o .NET Core

Bibliotecas estão rapidamente adotando o .NET Standard, que permite o compartilhamento de código em todas as versões do .NET, incluindo o .NET Core. Com o .NET Standard 2.0, isso será ainda mais fácil, pois a superfície da API do .NET Core crescerá significativamente e os aplicativos do .NET podem usar diretamente as bibliotecas existentes do .NET Framework. No entanto, essa transição não será imediata, portanto, é recomendável verificar as bibliotecas específicas exigidas pelo seu aplicativo antes de tomar uma decisão ou outra.

### <a name="a-need-to-use-net-technologies-not-available-for-net-core"></a>Necessidade de usar as tecnologias do .NET que não estão disponíveis para .NET Core

Algumas tecnologias do .NET Framework não estão disponíveis no .NET Core. Algumas delas estará disponíveis em versões posteriores do .NET Core, mas outras não se aplicam a novos padrões de aplicativos direcionados ao .NET Core e nunca estarão disponíveis. A lista a seguir mostra as tecnologias mais comuns não encontradas no .NET Core 1.0:

* Aplicativos Web Forms do ASP.NET: o Web Forms do ASP.NET só está disponível no .NET Framework, então não é possível usar o ASP.NET Core / .NET Core nesse cenário. Atualmente, não há planos para trazer os Web Forms do ASP.NET para o .NET Core.

* Aplicativos de páginas da Web do ASP.NET: as páginas da Web ASP.NET não estão incluídas no ASP.NET Core 1.0, embora haja planos para incluí-las em uma versão futura, conforme explicado no [Roteiro do .NET Core](https://github.com/aspnet/Home/wiki/Roadmap).

* Implementação de servidor/cliente ASP.NET SignalR. No período de versão do .NET Core 1.0 (junho de 2016), o ASP.NET SignalR não está disponível para ASP.NET Core (nem para cliente ou servidor), embora haja planos para incluí-lo em uma versão futura, conforme explicado no [Roteiro do .NET Core](https://github.com/aspnet/Home/wiki/Roadmap). O estado de visualização está disponível nos repositórios GitHub do [Servidor](https://github.com/aspnet/SignalR-Server) e da [Biblioteca de Cliente](https://github.com/aspnet/SignalR-Client-Net).

* Implementação de serviços do WCF. Mesmo quando houver uma [Biblioteca de Cliente WCF](https://github.com/dotnet/wcf) para consumir serviços WCF no .NET Core, a partir de junho de 2016, a implementação de servidor do WCF só estará disponível no .NET Framework. Esse cenário não é parte do plano atual para o .NET Core, mas ele está sendo considerado para o futuro.

* Serviços relacionados ao fluxo de trabalho: Windows Workflow Foundation (WF), Workflow Services (WCF + WF em um único serviço) e WCF Data Services (anteriormente conhecido como "ADO.NET Data Services") só estão disponíveis no .NET Framework e não há planos para colocá-los no .NET Core.

* Suporte de linguagem: não há suporte para ferramentas do Visual Basic e do F# no .NET Core, mas ambos terão suporte no Visual Studio 2017 e versões posteriores do Visual Studio.

Além do roteiro oficial, há outras estruturas para serem movidas para o .NET Core – Para obter uma lista completa, dê uma olhada nos problemas de CoreFX marcados como [port-to-core](https://github.com/dotnet/corefx/issues?q=is%3Aopen+is%3Aissue+label%3Aport-to-core). Observe que essa lista não representa um compromisso da Microsoft de trazer esses componentes para o .NET Core — eles simplesmente estão captando o desejo da comunidade. Dito isso, se você se importa com qualquer um dos componentes listados acima, considere a possibilidade de participar de discussões no GitHub para que sua voz seja ouvida. E se você achar que algo está faltando, [envie uma nova questão no repositório do CoreFX](https://github.com/dotnet/corefx/issues/new).

### <a name="a-need-to-use-a-platform-that-doesnt-support-net-core"></a>Necessidade de usar uma plataforma que não oferece suporte a .NET Core

Algumas plataformas de terceiros ou da Microsoft não oferecem suporte a .NET Core. Por exemplo, alguns serviços do Azure, como Reliable Services de Serviço de Monitoração com Estado de Malha e Reliable Actors da Malha de Serviço requerem o .NET Framework. Alguns outros serviços fornecem uma SDK ainda não estão disponível para consumo no .NET Core. Esta é uma circunstância transitória, pois todos os serviços do Azure usam o .NET Core. Enquanto isso, você sempre pode usar a API REST equivalente em vez do SDK do cliente.

## <a name="further-resources"></a>Recursos adicionais

* [Guia do .NET Core](../core/index.md)
* [Portabilidade do .NET Framework para .NET Core](../core/porting/index.md)
* [.NET Framework no Guia do Docker](../framework/index.md)
* [Visão Geral dos Componentes .NET](components.md)


<!--HONumber=Nov16_HO3-->


