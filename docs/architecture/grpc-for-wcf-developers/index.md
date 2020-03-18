---
title: ASP.NET Core gRPC para Desenvolvedores WCF - gRPC para Desenvolvedores WCF
description: Introdução à construção de serviços gRPC em ASP.NET Core 3.0 para desenvolvedores WCF
ms.date: 09/02/2019
ms.openlocfilehash: 40307124c521659a00339884bacf48881fa3e048
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/15/2020
ms.locfileid: "77543229"
---
# <a name="aspnet-core-grpc-for-wcf-developers"></a>ASP.NET Core gRPC para desenvolvedores do WCF

![imagem da capa](./media/cover.png)

PUBLICADO POR

Divisão de Desenvolvedores Microsoft, equipes dos produtos .NET e Visual Studio

Uma divisão da Microsoft Corporation

One Microsoft Way

Redmond, Washington 98052-6399

Copyright © 2019, Microsoft Corporation

Todos os direitos reservados. Nenhuma parte do conteúdo deste guia pode ser reproduzida ou transmitida de nenhuma forma nem por nenhum meio sem a permissão por escrito do publicador.

Este manual é fornecido "no estado em que se encontra" e expressa os pontos de vista e as opiniões do autor. Os pontos de vista, as opiniões e as informações expressos neste guia, incluindo URLs e outras referências a sites da Internet, podem ser alteradas sem aviso prévio.

 Alguns exemplos aqui representados são fornecidos somente para fins de ilustração e são fictícios. Nenhuma associação ou conexão real é intencional ou deve ser inferida.

A Microsoft e as marcas comerciais listadas em https://www.microsoft.com na página da Web “Marcas comerciais” são marcas comerciais do grupo de empresas da Microsoft.

O logotipo da baleia Docker é uma marca registrada da Docker, Inc. Usada por permissão.

Todas as outras marcas e logotipos são propriedade de seus respectivos proprietários.

Autores:

> **Mark Rendle** - Diretor Técnico - [Recode Visual](https://visualrecode.com)
>
> **Miranda Steiner** - Autor Técnico

Editor:

> **Maira Wenzel** - Sr. Content Developer - Microsoft

## <a name="introduction"></a>Introdução

gRPC é uma estrutura moderna para a construção de serviços em rede e aplicativos distribuídos. Imagine o desempenho das ligações NetTCP da Windows Communication Foundation (WCF), combinadas com a interoperabilidade multiplataforma do SOAP. O gRPC é baseado em HTTP/2 e no protocolo de codificação de mensagens Protobuf para fornecer comunicação de alto desempenho e baixa largura de banda entre aplicativos e serviços. Ele suporta a geração de código de servidor e cliente nas linguagens e plataformas de programação mais populares, incluindo .NET, Java, Python, Node.js, Go e C++. Com o suporte de primeira classe para o gRPC em ASP.NET Core 3.0, ao lado das ferramentas e bibliotecas gRPC existentes para .NET 4.x, é uma excelente alternativa ao WCF para equipes de desenvolvimento que buscam adotar o .NET Core em suas organizações.

## <a name="who-should-use-this-guide"></a>Quem deve usar este guia

Este guia foi escrito para desenvolvedores que trabalham em .NET Framework ou .NET Core que já usaram o WCF, e que estão buscando migrar seus aplicativos para um ambiente RPC moderno para versões .NET Core 3.0 e posteriores. De forma mais geral, se você estiver atualizando ou considerando atualizar para .NET Core 3.0, e quiser usar as ferramentas gRPC incorporadas, este guia também é útil.

## <a name="how-you-can-use-this-guide"></a>Como você pode usar este guia

Esta é uma breve introdução à construção de serviços gRPC em ASP.NET Núcleo 3.0, com referência particular ao WCF como uma plataforma análoga. Ele explica os princípios do gRPC, relacionando cada conceito às características equivalentes do WCF, e oferece orientação para migrar uma aplicação wcf existente para gRPC. Também é útil para desenvolvedores que têm experiência com WCF e estão procurando aprender gRPC para construir novos serviços. Você pode usar os aplicativos de amostra como um modelo ou referência para seus próprios projetos, e você está livre para copiar e reutilizar códigos do livro ou suas amostras.

Fique à vontade para encaminhar este guia para sua equipe para ajudar a garantir um entendimento comum dessas considerações e oportunidades. Ter todos trabalhando a partir de um conjunto comum de termos e princípios subjacentes ajuda a garantir a aplicação consistente de padrões e práticas arquitetônicas.

## <a name="references"></a>Referências

- **site gRPC**
  <https://grpc.io>
- **Escolhendo entre o .NET Core e o .NET Framework para aplicativos de servidor**
  <https://docs.microsoft.com/dotnet/standard/choosing-core-framework-server>

>[!div class="step-by-step"]
>[Avançar](introduction.md)
