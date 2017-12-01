---
title: "Quando escolher o núcleo do .NET para contêineres do Docker"
description: "Arquitetura de Microservices .NET para aplicativos .NET em contêineres | Quando escolher o núcleo do .NET para contêineres do Docker"
keywords: "Docker, Microsserviços, ASP.NET, Contêiner"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 10/18/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.openlocfilehash: b7e2322bab7937c41d4659fefef11c8937d5eae7
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/22/2017
---
# <a name="when-to-choose-net-core-for-docker-containers"></a>Quando escolher o núcleo do .NET para contêineres do Docker

A natureza modularidade e leve do .NET Core torna perfeito para contêineres. Quando você implanta e inicia um contêiner, sua imagem é muito menor com .NET Core que com o .NET Framework. Por outro lado, para usar o .NET Framework para um contêiner, você deve basear sua imagem na imagem do Windows Server Core, que é muito maior do que o Windows Nano Server ou imagens do Linux que você usa para .NET Core.

Além disso, o .NET Core é entre plataformas, portanto você pode implantar aplicativos de servidor com imagens de contêiner do Windows ou do Linux. No entanto, se você estiver usando o .NET Framework tradicional, você só pode implantar imagens com base no Windows Server Core.

A seguir está uma explicação mais detalhada do motivo escolher o núcleo do .NET.

## <a name="developing-and-deploying-cross-platform"></a>Desenvolvimento e implantação de várias plataformas

Claramente, se seu objetivo é ter um aplicativo (aplicativo da web ou serviço) que pode ser executados em várias plataformas com suporte pelo Docker (Linux e Windows), a opção certa é .NET Core, porque somente o .NET Framework dá suporte ao Windows.

.NET core também suporta macOS como uma plataforma de desenvolvimento. No entanto, quando você implanta os contêineres em um host do Docker, que hospedam (atualmente) deve ser baseado em Linux ou Windows. Por exemplo, em um ambiente de desenvolvimento, você pode usar uma VM do Linux em execução em um Mac.

[O Visual Studio](https://www.visualstudio.com/) fornece um ambiente de desenvolvimento integrado (IDE) para Windows e dá suporte ao desenvolvimento de Docker. 

[O Visual Studio para Mac](https://www.visualstudio.com/vs/visual-studio-mac/) é um IDE, evolução de Xamarin Studio, em execução no macOS e suporta Docker desde meados de 2017.

Você também pode usar [código do Visual Studio](https://code.visualstudio.com/) (VS código) em macOS, Linux e Windows. Código do VS dá suporte total ao .NET Core, incluindo IntelliSense e depuração. Porque o código do VS é um editor leve, você pode usá-lo a desenvolver aplicativos em contêineres no Mac em conjunto com a CLI do Docker e o [ferramentas de interface de linha de comando (CLI) do .NET Core](https://docs.microsoft.com/dotnet/core/tools/?tabs=netcore2x). Você também pode direcionar o .NET Core com editores de terceiros mais como texto Sublime, Emacs, vi e o projeto de OmniSharp do código-fonte aberto que dá suporte ao IntelliSense para linguagens .NET. Além dos IDEs e editores, você pode usar o .NET Core CLI para todas as plataformas com suporte.

## <a name="using-containers-for-new-green-field-projects"></a>Usando contêineres para novos projetos ("verde-field")

Contêineres são usados em conjunto com uma arquitetura microservices, embora também possa ser usados para coloca os aplicativos web ou serviços que seguem o padrão de qualquer arquitetura. Você pode usar o .NET Framework em contêineres do Windows, mas a modularidade e natureza leve do .NET Core torna perfeito para contêineres e microservices arquiteturas. Quando você cria e implanta um contêiner, sua imagem é muito menor com .NET Core que com o .NET Framework.

## <a name="creating-and-deploying-microservices-on-containers"></a>Criando e implantando microservices em contêineres

Você pode usar o tradicional do .NET Framework para a criação de aplicativos com base em microservices (sem contêineres) usando processos simples. Dessa forma, porque o .NET Framework já está instalado e compartilhado entre processos, os processos são claras e rápido para iniciar. No entanto, se você estiver usando contêineres, a imagem para o .NET Framework tradicional também se baseia no Windows Server Core e que facilita muito grande para uma abordagem microservices em contêineres.

Por outro lado, o .NET Core é o candidato melhor se você está adotando um sistema orientado a microservices com base em contêineres, como .NET Core é simples. Além disso, suas imagens de contêineres relacionados, a imagem do Linux ou a imagem do Windows Nano, são lean e pequenas tornar claro de contêineres e rápido para iniciar.

Um microsserviço deve ser tão pequenas quanto possível: para ser claro quando girando, com um espaço pequeno, com um pequeno limitada contexto, para representar uma pequena área de preocupações e ser capaz de iniciar e parar rápida. Para esses requisitos, você desejará usar imagens de contêiner de pequeno e rápido para instanciar como a imagem de contêiner do .NET Core.

Uma arquitetura de microservices também permite combinar as tecnologias em um limite de serviço. Isso permite que uma migração gradual para .NET Core para o novo microservices que funcionam em conjunto com outros microservices ou com serviços desenvolvidos com Node.js, Python, Java, GoLang ou outras tecnologias.

## <a name="deploying-high-density-in-scalable-systems"></a>Implantação de alta densidade em sistemas escalonáveis

Quando o sistema baseado em contêiner precisa a densidade possível melhor granularidade e o desempenho, o .NET Core e ASP.NET Core são as melhores opções. ASP.NET Core é até dez vezes mais rápido do que o ASP.NET no .NET Framework tradicional e leva outras tecnologias de setor populares para microservices como servlets Java, vá e Node. js.

Isso é especialmente relevante para arquiteturas de microservices, onde você pode ter centenas de microservices (contêineres) em execução. Com imagens ASP.NET Core (com base no tempo de execução do .NET Core) no Linux ou Windows Nano, você pode executar o sistema com um número menor de servidores ou máquinas virtuais, por fim, os custos de infraestrutura e hospedagem.


>[!div class="step-by-step"]
[Anterior] (geral-guidance.md) [Avançar] (net-framework-contêiner-scenarios.md)
