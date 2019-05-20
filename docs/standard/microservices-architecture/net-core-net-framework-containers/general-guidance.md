---
title: Diretrizes gerais
description: Arquitetura de microsserviços do .NET para aplicativos .NET em contêineres | Diretrizes gerais
ms.date: 09/11/2018
ms.openlocfilehash: 0981cb16d5aa2036391caba0cf6ad3ac5c44ed6f
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65644142"
---
# <a name="general-guidance"></a>Diretrizes gerais

Esta seção oferece um resumo de quando escolher o .NET Core ou o .NET Framework. Fornecemos mais detalhes sobre essas opções nas seções a seguir.

Você deverá usar o .NET Core, com contêineres Linux ou do Windows, para seu aplicativo para servidores do Docker em contêineres quando:

- Você tiver necessidades de plataforma cruzada. Por exemplo, você desejar usar contêineres Linux e do Windows.

- Sua arquitetura de aplicativo for baseada em microsserviços.

- For necessário iniciar contêineres rapidamente e você desejar ocupar um espaço menor por contêiner para obter melhor densidade ou mais contêineres por unidade de hardware a fim de reduzir seus custos.

Em resumo, quando você cria novos aplicativos .NET em contêineres, você deve considerar o .NET Core como a opção padrão. Ela tem muitos benefícios e se ajusta melhor à filosofia e ao estilo de trabalho dos contêineres.

Um benefício adicional de usar o .NET Core é que você pode executar versões do .NET para aplicativos lado a lado dentro do mesmo computador. Esse benefício é mais importante para servidores ou VMs que não usam contêineres, porque os contêineres isolam as versões do .NET de que o aplicativo precisa. (Desde que sejam compatíveis com o sistema operacional subjacente.)

Você deverá usar o .NET Framework para seu aplicativo para servidores do Docker em contêineres quando:

- No momento, seu aplicativo usar o .NET Framework e tem fortes dependências no Windows.

- For necessário usar APIs do Windows não compatíveis com o .NET Core.

- For necessário usar bibliotecas .NET de terceiros ou pacotes NuGet não disponíveis para o .NET Core.

Usar o .NET Framework no Docker pode melhorar suas experiências de implantação minimizando os problemas de implantação. Este [cenário de "lift-and-shift"](https://aka.ms/liftandshiftwithcontainersebook) é importante para colocar aplicativos herdados em contêineres que foram desenvolvidos originalmente com o .NET Framework tradicional, como os serviços ASP.NET WebForms, aplicativos Web MVC ou WCF (Windows Communication Foundation).

### <a name="additional-resources"></a>Recursos adicionais

- **Livro eletrônico: Modernizar aplicativos .NET Framework existentes com o Azure e Contêineres do Windows**  
    https://aka.ms/liftandshiftwithcontainersebook

- **Aplicativos de exemplo: Modernização de aplicativos Web ASP.NET herdados usando Contêineres do Windows**  
    https://aka.ms/eshopmodernizing

>[!div class="step-by-step"]
>[Anterior](index.md)
>[Próximo](net-core-container-scenarios.md)
