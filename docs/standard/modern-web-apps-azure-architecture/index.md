---
title: Arquitetar aplicativos Web modernos com o ASP.NET Core e o Azure
description: "Arquitetar aplicativos Web modernos com o ASP.NET Core e o Azure | Introdução"
author: ardalis
ms.author: wiwagn
ms.date: 10/06/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 44864274a86634c0199885b5507124f2f54ce0f6
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/23/2017
---
# <a name="architect-modern-web-applications-with-aspnet-core-and-azure"></a>Arquitetar Aplicativos Web Modernos com o ASP.NET Core e o Azure

O .NET Core e o ASP.NET Core oferecem várias vantagens sobre o desenvolvimento tradicional no .NET. Você deve usar o .NET Core para seus aplicativos de servidor se alguns ou todos os itens a seguir forem importantes para o sucesso do aplicativo:

-   Suporte de multiplaforma

-   Uso de microsserviços

-   Uso de contêineres do Docker

-   Requisitos de alto desempenho e escalabilidade

-   Controle de versão lado a lado de versões do .NET pelo aplicativo no mesmo servidor

Aplicativos .NET tradicionais poderão dar suporte a esses requisitos, porém o ASP.NET Core e .NET Core foram otimizados para proporcionar suporte aprimorado para os cenários acima.

Cada vez mais empresas estão optando por hospedar seus aplicativos Web na nuvem usando serviços como o Microsoft Azure. Considere hospedar seu aplicativo na nuvem se os seguintes itens forem importantes para seu aplicativo ou organização:

-   Investimento reduzido nos custos de data center (hardware, software, espaço, utilitários, etc.)

-   Preços flexíveis (pague com base no uso, não na capacidade ociosa)

-   Confiabilidade extrema

-   Melhoria na mobilidade de aplicativo; altere facilmente onde e como seu aplicativo é implantado

-   Capacidade flexível; expandir ou reduzir com base em necessidades reais

Compilar aplicativos Web com o ASP.NET Core, hospedado no Microsoft Azure, oferece várias vantagens competitivas sobre as alternativas tradicionais. O ASP.NET Core é otimizado para práticas de desenvolvimento de aplicativos Web e cenários de hospedagem em nuvem modernos. Neste guia, você aprenderá como arquitetar seus aplicativos do ASP.NET Core para aproveitar melhor essas funcionalidades.

## <a name="purpose"></a>Finalidade

Este guia fornece diretrizes ponta a ponta para a compilação de aplicativos Web monolíticos usando o ASP.NET Core e o Azure.

Este guia é um complemento para o “*Architecting and Developing Containerized and Microservice-based Applications with .NET*” (Arquitetura e desenvolvimento de aplicativos em contêineres e com microsserviços) que se concentra mais no Docker, Microsserviços e Implantação de Contêineres para hospedar aplicativos corporativos.

> ### <a name="architecting-and-developing-containerized-microservice-based-apps-in-net"></a>Arquitetura e desenvolvimento de aplicativos baseados em microsserviços em contêineres no .NET
> - **livro eletrônico**  
> <http://aka.ms/MicroservicesEbook>
> - **Aplicativo de exemplo**  
> <http://aka.ms/microservicesarchitecture>

## <a name="who-should-use-this-guide"></a>Quem deve usar este guia

O público-alvo principal deste guia são desenvolvedores, líderes de desenvolvimento e arquitetos interessados em compilar aplicativos Web modernos usando tecnologias e serviços da Microsoft na nuvem.

Um público-alvo secundário são os tomadores de decisões técnicas que já estão familiarizados com o ASP.NET e/ou o Azure e estão procurando informações sobre se faz sentido para atualizar para o ASP.NET Core para projetos novos ou existentes.

## <a name="how-you-can-use-this-guide"></a>Como você pode usar este guia

Este guia foi condensado em um documento relativamente pequeno que se concentra na compilação de aplicativos Web com tecnologias .NET modernas e o Microsoft Azure. Como tal, ele pode ser lido em sua totalidade para fornecer uma base de compreensão desses aplicativos e suas considerações técnicas. O guia, junto com seu aplicativo de exemplo, também pode servir como um ponto de partida ou de referência. Use o aplicativo de exemplo associado como um modelo para seus próprios aplicativos ou para ver como você poderia organizar os blocos do aplicativo. Consulte os princípios do guia, a cobertura da arquitetura, as opções de tecnologia e as considerações de decisões ao ponderar essas opções para seu próprio aplicativo.

Fique à vontade para encaminhar este guia para sua equipe para ajudar a garantir um entendimento comum dessas considerações e oportunidades. Ter todas as pessoas trabalhando em um conjunto comum de terminologia e princípios subjacentes ajudará a garantir a aplicação consistente dos padrões e práticas arquitetônicos.

## <a name="references"></a>Referências
- **Escolhendo entre o .NET Core e .NET Framework para aplicativos de servidor**  
<https://docs.microsoft.com/dotnet/articles/standard/choosing-core-framework-server>

>[!div class="step-by-step"]
[Next] (modern-web-applications-characteristics.md)
