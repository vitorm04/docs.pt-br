---
title: .NET Core e software livre
ms.date: 03/30/2017
ms.assetid: e6bd4655-ce37-4003-8462-468a6fe2c40f
ms.openlocfilehash: bed5bb6aad5f3e651f7c4c0651a2365f17eb8a0b
ms.sourcegitcommit: 1c1a1f9ec0bd1efb3040d86a79f7ee94e207cca5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/03/2020
ms.locfileid: "80635290"
---
# <a name="net-core-and-open-source"></a>.NET Core e software livre

Este artigo fornece uma breve visão geral do que é o .NET Core e mostra como você pode encontrar mais informações. Para encontrar a lista completa de documentação para .NET Core, visite o [guia .NET Core](../../core/index.yml).

## <a name="what-is-net-core"></a>O que é o .NET Core?  

.NET Core é uma implementação geral, modular, multiplataforma e código aberto do .NET Standard. Ele contém muitas das mesmas APIs que o .NET Framework (mas o .NET Core é um conjunto menor) e inclui componentes de tempo de execução, framework, compilador e ferramentas que suportam uma variedade de sistemas operacionais e alvos de chip. A implementação do .NET Core foi conduzida principalmente por cargas de trabalho ASP.NET Core, mas também pela necessidade e desejo de ter uma implementação mais moderna. Ele pode ser usado em cenários de dispositivos, nuvem e incrustados/IoT.  
  
Para começar com o .NET Core, visite o tutorial .NET [Hello World em 10 minutos](https://dotnet.microsoft.com/learn/dotnet/hello-world-tutorial/intro).  
  
As principais características do .NET Core são:
  
- **Plataforma cruzada:** o .NET Core fornece uma funcionalidade essencial para implementação de recursos de aplicativo necessários, e reutilização desse código independentemente de seu destino de plataforma. Atualmente, suporta três sistemas operacionais principais (OS): Windows, Linux e macOS. Você pode escrever aplicativos e bibliotecas que são executados sem modificações em sistemas operacionais com suporte. Para ver a lista de sistemas operacionais com suporte, visite [Roteiro do .NET Core](https://github.com/dotnet/core/blob/master/roadmap.md).
  
- **Software livre:** o .NET Core é um dos muitos projetos sob a administração do [.NET Foundation](https://www.dotnetfoundation.org/) e está disponível no [GitHub](https://github.com/).  Ter o .NET Core como um projeto de código-fonte aberto promove um processo de desenvolvimento mais transparente e uma comunidade ativa e dedicada.  
  
- **Implantação flexível:** há duas maneiras de implantar seu aplicativo: implantação dependente da estrutura ou implantação independente. Com a implantação dependente da estrutura, apenas as dependências de seu aplicativo e de terceiros serão instaladas, e seu aplicativo dependerá da presença de uma versão de todo o sistema do .NET Core. Com a implantação independente, a versão do .NET Core usada para compilar seu aplicativo também será implantada junto com as dependências de seu aplicativo e de terceiros, e poderá ser executada lado a lado com outras versões. Para saber mais, confira [Implantação de aplicativos .NET Core](../../core/deploying/index.md).

- **Modular:** o .NET Core é modular, pois é liberado por meio do NuGet em pacotes de assembly menores. Em vez de um grande conjunto que contém a maior parte da funcionalidade principal, o .NET Core é disponibilizado como pacotes menores e centrados em recursos. Essa modularidade permite um modelo de desenvolvimento mais ágil para nós e permite que você otimize seu aplicativo para incluir apenas os pacotes NuGet que você precisa. Os benefícios de uma área de superfície menor do aplicativo incluem segurança mais rigorosa, manutenção reduzida, desempenho aprimorado e redução dos custos em um modelo de pagamento “pague pelo que usar”.  
  
## <a name="the-net-core-platform"></a>A plataforma .NET Core
  
A plataforma .NET Core é composta por vários componentes, incluindo os compiladores gerenciados, o tempo de execução, as bibliotecas de classe base e vários modelos de aplicativos, como ASP.NET Core. Você pode aprender mais sobre os diferentes componentes e ficar engajado visitando os seguintes repositórios do [GitHub:](https://github.com/)  
  
- [.NET Core home](https://github.com/dotnet/core)  
  
- [Tempo de execução - plataforma .NET Core e tempo de execução](https://github.com/dotnet/runtime)  
  
- [CLI - Ferramentas da interface de linha de comando do .NET Core](https://github.com/dotnet/cli)  
  
- [Roslyn - Plataforma do Compilador .NET](https://github.com/dotnet/roslyn)  
  
- [ASP.NET Core](https://github.com/dotnet/aspnetcore)  
  
## <a name="see-also"></a>Confira também

- [Tutorial .NET - Hello World em 10 minutos](https://dotnet.microsoft.com/learn/dotnet/hello-world-tutorial/intro)
- [Guia do .NET Core](../../core/index.yml)
- [ASP.NET Core docs](/aspnet/core/)
