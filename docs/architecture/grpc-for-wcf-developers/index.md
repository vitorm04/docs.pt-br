---
title: ASP.NET Core gRPC para desenvolvedores do WCF – gRPC para desenvolvedores do WCF
description: Introdução à criação de serviços gRPCs no ASP.NET Core 3,0 para desenvolvedores do WCF
ms.date: 09/02/2019
ms.openlocfilehash: 3ef513d2397b6f282591dfe6c9b25cd178372a28
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/12/2019
ms.locfileid: "73967745"
---
# <a name="aspnet-core-grpc-for-wcf-developers"></a>ASP.NET Core gRPC para desenvolvedores do WCF

![imagem da capa](./media/cover.png)

PUBLICADO POR

Divisão de Desenvolvedores Microsoft, equipes dos produtos .NET e Visual Studio

Uma divisão da Microsoft Corporation

Uma maneira de Microsoft

Redmond, Washington 98052-6399

Copyright © 2019, Microsoft Corporation

Todos os direitos reservados. Nenhuma parte do conteúdo deste guia pode ser reproduzida ou transmitida de nenhuma forma nem por nenhum meio sem a permissão por escrito do publicador.

Este manual é fornecido "no estado em que se encontra" e expressa os pontos de vista e as opiniões do autor. Os pontos de vista, as opiniões e as informações expressos neste guia, incluindo URLs e outras referências a sites da Internet, podem ser alteradas sem aviso prévio.

Alguns exemplos aqui representados são fornecidos apenas para ilustração e são fictícios. Nenhuma associação ou conexão real é intencional ou deve ser deduzida.

A Microsoft e as marcas comerciais listadas em https://www.microsoft.com na página da Web “Marcas comerciais” são marcas comerciais do grupo de empresas da Microsoft.

O logotipo de redistribuição do Docker é uma marca registrada do Docker, Inc. usada pela permissão.

Todas as outras marcas e logotipos são propriedade de seus respectivos proprietários.

Autor:

> **Mark** diretor técnico de Rendle – [recódigo Visual](https://visualrecode.com)
>
> **Miranda Steiner** – autor técnico

Editores:

> **Maira Wenzel** -Sr Content Developer-Microsoft

## <a name="introduction"></a>Introdução

o gRPC é uma estrutura moderna para a criação de serviços em rede e aplicativos distribuídos. Imagine o desempenho das associações NetTCP do WCF com a interoperabilidade entre plataformas do SOAP. o gRPC se baseia no HTTP/2 e no protocolo de codificação de mensagens Protobuf para fornecer comunicação de alto desempenho e baixa largura de banda entre aplicativos e serviços. Ele dá suporte à geração de código de servidor e cliente em plataformas e linguagens de programação mais populares, incluindo .NET, Java, Python, C++ node. js, ir e muito mais. Com o suporte de primeira classe para gRPC no ASP.NET Core 3,0, juntamente com as ferramentas e as bibliotecas existentes do gRPC para o .NET 4. x, achamos que é uma excelente alternativa ao WCF para equipes de desenvolvimento que buscam adotar o .NET Core em suas organizações.

## <a name="who-should-use-this-guide"></a>Quem deve usar este guia

Este guia foi escrito para desenvolvedores que trabalham em .NET Framework ou .NET Core que usaram anteriormente o WCF e que estão buscando migrar seus aplicativos para um ambiente de RPC moderno para .NET Core 3,0 e versões posteriores. O guia também pode ser usado mais geralmente para os desenvolvedores que estão atualizando ou considerando a atualização para o .NET Core 3,0 que desejam usar as ferramentas de gRPC internas.

## <a name="how-you-can-use-this-guide"></a>Como você pode usar este guia

Esta é uma breve introdução à criação de serviços gRPCs no ASP.NET Core 3,0 com referência específica ao WCF como uma plataforma análoga. Ele explica os princípios de gRPC, relacionando cada conceito aos recursos equivalentes do WCF e oferece orientação para migrar um aplicativo WCF existente para o gRPC. Ele também é útil para desenvolvedores que têm experiência com o WCF e procuram aprender a gRPC para criar novos serviços. Os aplicativos de exemplo podem ser usados como um modelo ou referência para seus próprios projetos, e você pode copiar e reutilizar o código do livro ou de seus exemplos.

Fique à vontade para encaminhar este guia para sua equipe para ajudar a garantir um entendimento comum dessas considerações e oportunidades. Quando todas as pessoas trabalham com um conjunto comum de terminologia e de princípios subjacentes é mais fácil garantir a aplicação consistente dos padrões e das práticas de arquitetura.

## <a name="references"></a>Referências

- **site da gRPC**  
  <https://grpc.io>
- **Escolhendo entre o .NET Core e .NET Framework para aplicativos de servidor**  
  <https://docs.microsoft.com/dotnet/standard/choosing-core-framework-server>

>[!div class="step-by-step"]
>[Avançar](introduction.md)
