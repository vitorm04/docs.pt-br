---
title: Ferramentas adicionais da CLI
description: Uma visão geral das ferramentas adicionais que você pode instalar que oferecem suporte e estendem a funcionalidade do .NET Core.
author: mlacouture
ms.date: 12/02/2019
ms.custom: mvc
ms.openlocfilehash: 1f066523a24d4e1fd7aaaa5a19e8d6c9d72d35af
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75714529"
---
# <a name="net-core-additional-tools-overview"></a>Visão geral das ferramentas adicionais do .NET Core

Esta seção compila uma lista de ferramentas de suporte e estender a funcionalidade do .NET Core, além das ferramentas da [CLI (interface de linha de comando) do .NET Core](../tools/index.md).

## <a name="net-core-uninstall-tooluninstall-toolmd"></a>[Ferramenta de desinstalação do .NET Core](uninstall-tool.md)

A [ferramenta de desinstalação do .NET Core](https://dotnet.microsoft.com/download/dotnet-core/uninstall-tool) (`dotnet-core-uninstall`) permite limpar SDKs e tempos de execução do .NET Core em um sistema, de modo que apenas as versões especificadas permaneçam. Uma coleção de opções está disponível para especificar quais versões são desinstaladas.

## <a name="wcf-web-service-reference-toolwcf-web-service-reference-guidemd"></a>[Ferramenta WCF Web Service Reference](wcf-web-service-reference-guide.md)

O WCF (Windows Communication Foundation) Web Service Reference é um provedor de serviços conectados do Visual Studio que fez sua estreia no [Visual Studio 2017 versão 15.5](/visualstudio/releasenotes/vs2017-relnotes-v15.5#WCFTools). Essa ferramenta recupera metadados de um serviço Web na solução atual, em um local de rede ou em um arquivo WSDL. Ele gera um arquivo de origem compatível com o .NET Core, definindo uma classe proxy WCF com métodos que você pode usar para acessar as operações do serviço Web.

## <a name="wcf-dotnet-svcutil-tooldotnet-svcutil-guidemd"></a>[Ferramenta dotnet-svcutil do WCF](dotnet-svcutil-guide.md)

A ferramenta dotnet-SvcUtil do WCF (Windows Communication Foundation) é uma ferramenta de CLI do .NET Core que recupera metadados de um serviço Web em um local de rede ou em um arquivo WSDL. Ele gera um arquivo de origem compatível com o .NET Core, definindo uma classe proxy WCF com métodos que você pode usar para acessar as operações do serviço Web.

A ferramenta **dotnet-SvcUtil** é uma opção alternativa para o provedor de serviços conectados do Visual Studio [**Web Service Reference**](wcf-web-service-reference-guide.md) , que foi enviado pela primeira vez com o visual Studio 2017 versão 15,5. A ferramenta **dotnet-SvcUtil** , como uma ferramenta de CLI do .NET Core, está disponível para várias plataformas no Linux, no MacOS e no Windows.

## <a name="wcf-dotnet-svcutilxmlserializer-tooldotnet-svcutilxmlserializer-guidemd"></a>[Ferramenta dotnet-svcutil.xmlserializer da WCF](dotnet-svcutil.xmlserializer-guide.md)

No .NET Framework, é possível gerar previamente um assembly de serialização usando a ferramenta svcutil. O pacote do NuGet dotnet svcutil.xmlserializer fornece funcionalidade semelhante no .NET Core. Ele gera previamente o código de serialização C# para os tipos no aplicativo cliente, que são usados pelo Contrato de Serviço da WCF e podem ser serializados pelo <xref:System.Xml.Serialization.XmlSerializer>. Isso melhora o desempenho de inicialização da serialização de XML ao serializar ou desserializar objetos desses tipos.

## <a name="xml-serializer-generatorxml-serializer-generatormd"></a>[XML Serializer Generator](xml-serializer-generator.md)

Como o [XML Serializer Generator (sgen.exe)](../../standard/serialization/xml-serializer-generator-tool-sgen-exe.md) para o .NET Framework, o [pacote NuGet Microsoft.XmlSerializer.Generator](https://www.nuget.org/packages/Microsoft.XmlSerializer.Generator) é a solução para bibliotecas .NET Core e .NET Standard. Ele cria um assembly de serialização de XML para tipos contidos em um assembly a fim de melhorar o desempenho de inicialização da serialização de XML ao serializar ou desserializar objetos desses tipos usando <xref:System.Xml.Serialization.XmlSerializer>.
