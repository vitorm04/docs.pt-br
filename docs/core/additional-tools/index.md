---
title: Ferramentas adicionais da CLI do .NET Core
description: Uma visão geral das ferramentas adicionais que você pode instalar que oferecem suporte e estendem a funcionalidade do .NET Core.
author: mlacouture
ms.date: 11/27/2018
ms.custom: mvc, seodec18
ms.openlocfilehash: 5f42cddc31204bba2aafaee0b909bbf92d232fde
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61644285"
---
# <a name="net-core-additional-tools-overview"></a>Visão geral das ferramentas adicionais do .NET Core

Esta seção compila uma lista de ferramentas de suporte e estender a funcionalidade do .NET Core, além das ferramentas da [CLI (interface de linha de comando) do .NET Core](../tools/index.md).

## <a name="wcf-web-service-reference-toolwcf-web-service-reference-guidemd"></a>[Ferramenta WCF Web Service Reference](wcf-web-service-reference-guide.md)

O WCF (Windows Communication Foundation) Web Service Reference é um provedor de serviços conectados do Visual Studio que fez sua estreia no [Visual Studio 2017 versão 15.5](/visualstudio/releasenotes/vs2017-relnotes-v15.5#WCFTools). Essa ferramenta recupera metadados de um serviço Web na solução atual, em um local de rede ou de um arquivo WSDL, e gera um arquivo de origem compatível com o .NET Core, definindo uma classe proxy do WCF com métodos que você pode usar para acessar as operações de serviço Web.

## <a name="wcf-dotnet-svcutil-tooldotnet-svcutil-guidemd"></a>[Ferramenta dotnet-svcutil do WCF](dotnet-svcutil-guide.md)

A ferramenta dotnet-svcutil do WCF (Windows Communication Foundation) é uma ferramenta da CLI do .NET Core que recupera metadados de um serviço Web em um local de rede ou de um arquivo WSDL e gera um arquivo de origem compatível com o .NET Core, definindo uma classe proxy do WCF com métodos que você pode usar para acessar as operações do serviço Web.
A ferramenta **dotnet-svcutil** é uma opção alternativa ao provedor de serviços conectados do Visual Studio [**WCF Web Service Reference**](wcf-web-service-reference-guide.md) que foi primeiramente fornecido com o Visual Studio 2017 v15.5. A ferramenta **dotnet-svcutil**, como uma ferramenta da CLI do .NET Core, é a multiplataforma disponível no Linux, no macOS e no Windows.

## <a name="wcf-dotnet-svcutilxmlserializer-tooldotnet-svcutilxmlserializer-guidemd"></a>[Ferramenta dotnet-svcutil.xmlserializer da WCF](dotnet-svcutil.xmlserializer-guide.md)

No .NET Framework, é possível gerar previamente um assembly de serialização usando a ferramenta svcutil. O pacote do NuGet dotnet svcutil.xmlserializer fornece funcionalidade semelhante no .NET Core. Ele gera previamente o código de serialização C# para os tipos no aplicativo cliente, que são usados pelo Contrato de Serviço da WCF e podem ser serializados pelo <xref:System.Xml.Serialization.XmlSerializer>. Isso melhora o desempenho de inicialização da serialização de XML ao serializar ou desserializar objetos desses tipos.

## <a name="xml-serializer-generatorxml-serializer-generatormd"></a>[XML Serializer Generator](xml-serializer-generator.md)

Como o [XML Serializer Generator (sgen.exe)](../../standard/serialization/xml-serializer-generator-tool-sgen-exe.md) para o .NET Framework, o [pacote NuGet Microsoft.XmlSerializer.Generator](https://www.nuget.org/packages/Microsoft.XmlSerializer.Generator) é a solução para bibliotecas .NET Core e .NET Standard. Ele cria um assembly de serialização de XML para tipos contidos em um assembly para melhorar o desempenho de inicialização de serialização de XML ao serializar ou desserializar objetos desses tipos usando <xref:System.Xml.Serialization.XmlSerializer>.