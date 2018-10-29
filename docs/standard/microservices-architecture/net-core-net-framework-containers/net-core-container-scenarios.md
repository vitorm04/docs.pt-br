---
title: Quando escolher o .NET Core para os contêineres do Docker
description: Arquitetura de microsserviços do .NET para aplicativos .NET em contêineres | Quando escolher o .NET Core para os contêineres do Docker
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 09/11/2018
ms.openlocfilehash: fa5efd3c2478965ef01efc39b57918ec2d35962a
ms.sourcegitcommit: 8c28ab17c26bf08abbd004cc37651985c68841b8
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/08/2018
ms.locfileid: "48873369"
---
# <a name="when-to-choose-net-core-for-docker-containers"></a>Quando escolher o .NET Core para os contêineres do Docker

A modularidade e a natureza leve do .NET Core torna-o perfeito para contêineres. Ao implantar e iniciar um contêiner, sua imagem é muito menor com o .NET Core do que com o .NET Framework. Por outro lado, para usar o .NET Framework para um contêiner, é necessário basear sua imagem na imagem do Windows Server Core, que é muito mais pesada do que as imagens do Windows Nano Server ou Linux que você usa para o .NET Core.

Além disso, o .NET Core é multiplataforma, portanto, é possível implantar aplicativos de servidor com imagens de contêiner do Windows ou Linux. No entanto, se você estiver usando o .NET Framework tradicional, só poderá implantar imagens baseadas no Windows Server Core.

A seguir há uma explicação mais detalhada do porquê escolher o .NET Core.

## <a name="developing-and-deploying-cross-platform"></a>Desenvolvendo e implantando uma multiplataforma

Claramente, se sua meta for ter um aplicativo (serviço ou aplicativo Web) que possa ser executado em várias plataformas compatíveis com o Docker (Linux e Windows), a escolha correta será o .NET Core, porque o .NET Framework é compatível somente com o Windows.

O .NET Core também é compatível com o macOS como uma plataforma de desenvolvimento. No entanto, quando você implanta contêineres em um host do Docker, esse host deve (atualmente) ser baseado em Linux ou Windows. Por exemplo, em um ambiente de desenvolvimento, você pode usar uma VM Linux em execução em um Mac.

O [Visual Studio](https://www.visualstudio.com/vs/) fornece um IDE (ambiente de desenvolvimento integrado) para Windows e é compatível com o desenvolvimento do Docker.

O [Visual Studio para Mac](https://www.visualstudio.com/vs/visual-studio-mac/) é um IDE, a evolução do Xamarin Studio, que é executada em macOS e dá suporte ao desenvolvimento de aplicativos baseados em Docker. Essa deve ser a opção preferencial para desenvolvedores que trabalham em computadores Mac que queiram usar um IDE avançado.

Também é possível usar o [Visual Studio Code](https://code.visualstudio.com/) (VS Code) no macOS, Linux e Windows. O VS Code é totalmente compatível com o .NET Core, incluindo IntelliSense e depuração. Como o VS Code é um editor leve, é possível usá-lo para desenvolver aplicativos em contêineres no Mac em conjunto com a CLI do Docker e com a [CLI (interface de linha de comando) do .NET Core](https://docs.microsoft.com/dotnet/core/tools/?tabs=netcore2x). Também é possível direcionar o .NET Core com a maioria dos editores de terceiros, como Sublime, Emacs, vi e o projeto OmniSharp de software livre, que também fornece suporte ao IntelliSense.

Além dos IDEs e dos editores, é possível usar a [CLI do .NET Core](https://docs.microsoft.com/dotnet/core/tools/?tabs=netcore2x) para todas as plataformas compatíveis.

## <a name="using-containers-for-new-green-field-projects"></a>Usando contêineres para novos projetos ("campo verde")

Contêineres são comumente usados em conjunto com uma arquitetura de microsserviços, embora também possam ser usados para colocar em contêineres aplicativos Web ou serviços que sigam qualquer padrão de arquitetura. É possível usar o .NET Framework em contêineres do Windows, mas a modularidade e a natureza leve do .NET Core torna-o perfeito para contêineres e arquiteturas de microsserviços. Quando você cria e implanta um contêiner, sua imagem é muito menor com o .NET Core do que com o .NET Framework.

## <a name="creating-and-deploying-microservices-on-containers"></a>Criando e implantando microsserviços em contêineres

É possível usar o .NET Framework tradicional para criar aplicativos baseados em microsserviços (sem contêineres) usando processos simples. Dessa forma, como o .NET Framework já está instalado e já é compartilhado entre processos, os processos são leves inicializam rapidamente. No entanto, se você estiver usando contêineres, a imagem do .NET Framework tradicional também será baseada no Windows Server Core e isso a tornará muito pesada para uma abordagem de microsserviços em contêineres.

Por outro lado, o .NET Core é o melhor candidato se você está adotando um sistema orientado a microsserviços baseado em contêineres, porque o .NET Core é leve. Além disso, suas imagens de contêineres relacionadas, a imagem do Linux ou a imagem do Windows Nano, são enxutas e pequenas, tornando os contêineres leves e rápidos para inicializar.

Um microsserviço deve ser o menor possível: ser leve ao iniciar, ocupar um pequeno espaço, ter um Contexto limitado pequeno (confira DDD, [Design Voltado a Domínio](https://en.wikipedia.org/wiki/Domain-driven_design)), para representar uma pequena área de preocupações e ser capaz de ser iniciado e interrompido rapidamente. Para esses requisitos, você desejará usar imagens de contêiner pequenas e cuja instância é fácil de criar, como a imagem de contêiner do .NET Core.

Uma arquitetura de microsserviços também permite uma combinação de tecnologias em um limite de serviço. Isso permite uma migração gradual para o .NET Core para novos microsserviços que funcionam em conjunto com outros microsserviços ou com serviços desenvolvidos com o Node.js, Python, Java, GoLang ou outras tecnologias.

## <a name="deploying-high-density-in-scalable-systems"></a>Implantando alta densidade em sistemas escalonáveis

Quando seu sistema baseado em contêiner precisar da melhor densidade, granularidade e desempenho possíveis, o .NET Core e o ASP.NET Core são suas melhores opções. O ASP.NET Core é até dez vezes mais rápido do que o ASP.NET no .NET Framework tradicional e lidera outras tecnologias populares do setor para microsserviços, como Java servlets, Go e Node.js.

Isso é especialmente relevante para arquiteturas de microsserviços, em que você poderia ter centenas de microsserviços (contêineres) em execução. Com imagens do ASP.NET Core (baseadas no tempo de execução do .NET Core) no Linux ou Windows Nano, é possível executar seu sistema com um número muito menor de servidores ou VMs, economizando custos em infraestrutura e hospedagem.


>[!div class="step-by-step"]
[Anterior](general-guidance.md)
[Próximo](net-framework-container-scenarios.md)
