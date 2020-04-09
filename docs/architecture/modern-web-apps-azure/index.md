---
title: Arquitetar aplicativos Web modernos com o ASP.NET Core e o Azure
description: Um guia que fornece diretrizes de ponta a ponta para a criação de aplicativos Web monolíticos usando o ASP.NET Core e o Azure.
author: ardalis
ms.author: wiwagn
ms.date: 12/4/2019
ms.openlocfilehash: 18449ea02b7f9e89744a0f3088f80b7a51a807da
ms.sourcegitcommit: e3cbf26d67f7e9286c7108a2752804050762d02d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/09/2020
ms.locfileid: "80987888"
---
# <a name="architect-modern-web-applications-with-aspnet-core-and-azure"></a>Arquitetar Aplicativos Web Modernos com o ASP.NET Core e o Azure

![Imagem da capa do guia Architect Modern Web Applications.](./media/index/web-application-guide-cover-image.png)

**EDITION v3.1** - Atualizado para ASP.NET Núcleo 3.1

PUBLICADO POR

Divisão de Desenvolvedores Microsoft, equipes dos produtos .NET e Visual Studio

Uma divisão da Microsoft Corporation

One Microsoft Way

Redmond, Washington 98052-6399

Copyright © 2020 pela Microsoft Corporation

Todos os direitos reservados. Nenhuma parte do conteúdo deste guia pode ser reproduzida ou transmitida de nenhuma forma nem por nenhum meio sem a permissão por escrito do publicador.

Este livro é fornecido “no estado em que se encontra” e expressa os pontos de vista e as opiniões do autor. Os pontos de vista, as opiniões e as informações expressos neste guia, incluindo URLs e outras referências a sites da Internet, podem ser alteradas sem aviso prévio.

 Alguns exemplos aqui representados são fornecidos somente para fins de ilustração e são fictícios. Nenhuma associação ou conexão real é intencional ou deve ser inferida.

A Microsoft e as marcas listadas em https://www.microsoft.com na página da Web "Marcas" são marcas comerciais do grupo de empresas Microsoft.

Mac e macOS são marcas comerciais da Apple Inc.

O logotipo da baleia Docker é uma marca registrada da Docker, Inc. Usada por permissão.

Todas as outras marcas e logotipos são propriedade de seus respectivos proprietários.

Autor:

> **Steve "ardalis" Smith** – Arquiteto de software e instrutor – [Ardalis.com](https://ardalis.com)

Editores:

> **Maira Wenzel**

## <a name="introduction"></a>Introdução

O .NET Core e o ASP.NET Core oferecem várias vantagens sobre o desenvolvimento tradicional no .NET. Você deve usar o .NET Core para seus aplicativos de servidor se alguns ou todos os itens a seguir forem importantes para o sucesso do aplicativo:

- Suporte para plataforma cruzada.

- Uso de microsserviços.

- Uso de contêineres do Docker.

- Requisitos de alto desempenho e escalabilidade.

- Controle de versão lado a lado para versões do .NET por aplicativo no mesmo servidor.

Aplicativos .NET tradicionais poderão dar suporte a vários desses requisitos, porém o ASP.NET Core e .NET Core foram otimizados para proporcionar suporte aprimorado para os cenários acima.

Cada vez mais empresas estão optando por hospedar seus aplicativos Web na nuvem usando serviços como o Microsoft Azure. Considere hospedar seu aplicativo na nuvem se os seguintes itens forem importantes para seu aplicativo ou organização:

- Investimento reduzido nos custos de data center (hardware, software, espaço, utilitários, gerenciamento de servidor, etc.)

- Preços flexíveis (pague com base no uso, não pela capacidade ociosa).

- Confiabilidade extrema.

- Melhoria na mobilidade de aplicativo: altere facilmente onde e como seu aplicativo é implantado.

- Capacidade flexível: aumente ou reduza com base em necessidades reais.

A criação de aplicativos Web com o ASP.NET Core, hospedados no Azure, oferece várias vantagens competitivas em relação às alternativas tradicionais. O ASP.NET Core é otimizado para práticas de desenvolvimento de aplicativos Web e cenários de hospedagem em nuvem modernos. Neste guia, você aprenderá como arquitetar seus aplicativos ASP.NET Core para aproveitar melhor essas funcionalidades.

## <a name="purpose"></a>Finalidade

Este guia fornece orientação de ponta a ponta sobre a construção de aplicações web *monolíticas* usando ASP.NET Core e Azure. Nesse contexto, "monolítico" refere-se ao fato de que esses aplicativos são implantados como uma única unidade, não como uma coleção de serviços e aplicativos em interação.

Este guia é complementar ao [_" .NET Microservices. Arquitetura para aplicativos .NET contêiner_"](../microservices/index.md) que se concentra mais no Docker, Microservices e Deployment of Containers para hospedar aplicativos corporativos.

### <a name="net-microservices-architecture-for-containerized-net-applications"></a>Microsserviços do .NET. Arquitetura de aplicativos .NET em contêineres

- **e-book**  
  <https://aka.ms/MicroservicesEbook>
- **Aplicação de amostra**  
  <https://aka.ms/microservicesarchitecture>

## <a name="who-should-use-this-guide"></a>Quem deve usar este guia

O público-alvo principal deste guia são desenvolvedores, líderes de desenvolvimento e arquitetos interessados em compilar aplicativos Web modernos usando tecnologias e serviços da Microsoft na nuvem.

Um público-alvo secundário são os tomadores de decisões técnicas que já estão familiarizados com o ASP.NET ou com o Azure e estão buscando informações para saber se é interessante atualizar seus projetos novos ou existentes para o ASP.NET Core.

## <a name="how-you-can-use-this-guide"></a>Como você pode usar este guia

Este guia foi condensado em um documento relativamente pequeno que se concentra na compilação de aplicativos Web com tecnologias .NET modernas e o Microsoft Azure. Como tal, ele pode ser lido em sua totalidade para fornecer uma base de compreensão desses aplicativos e suas considerações técnicas. O guia, junto com seu aplicativo de exemplo, também pode servir como um ponto de partida ou de referência. Use o aplicativo de exemplo associado como um modelo para seus próprios aplicativos ou para ver como você poderia organizar os blocos do aplicativo. Confira os princípios do guia, a cobertura das opções de arquitetura e de tecnologia e as considerações de decisões ao ponderar essas opções para seu próprio aplicativo.

Fique à vontade para encaminhar este guia para sua equipe para ajudar a garantir um entendimento comum dessas considerações e oportunidades. Quando todas as pessoas trabalham com um conjunto comum de terminologia e de princípios subjacentes é mais fácil garantir a aplicação consistente dos padrões e das práticas de arquitetura.

## <a name="references"></a>Referências

- **Escolhendo entre o .NET Core e .NET Framework para aplicativos de servidor**  
  [https://docs.microsoft.com/dotnet/standard/choosing-core-framework-server](../../standard/choosing-core-framework-server.md)

>[!div class="step-by-step"]
>[Avançar](modern-web-applications-characteristics.md)
