---
title: Ferramentas adicionais
description: Uma visão geral das ferramentas adicionais que você pode instalar que oferecem suporte e estendem a funcionalidade do .NET Core.
author: mlacouture
ms.date: 02/13/2020
ms.custom: mvc
ms.openlocfilehash: c0224a1cc6cbb9ae6fa88e5f869c47a1e84289e0
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/15/2020
ms.locfileid: "77451519"
---
# <a name="net-core-additional-tools-overview"></a>Visão geral das ferramentas adicionais do .NET Core

Esta seção compila uma lista de ferramentas que suportam e ampliam a funcionalidade .NET Core, além do .NET Core CLI.

## <a name="net-core-uninstall-tool"></a>Ferramenta de Desinstalação do .NET Core

A [ferramenta de desinstalação](https://github.com/dotnet/cli-lab/releases) do núcleo .NET permite`dotnet-core-uninstall`limpar SDKs e Runtimes do .NET Core em um sistema de tal forma que apenas as versões especificadas permaneçam. Uma coleção de opções está disponível para especificar quais versões estão desinstaladas.

## <a name="net-core-diagnostic-tools"></a>.NET Core ferramentas de diagnóstico

[dotnet-counters](../diagnostics/dotnet-counters.md) é uma ferramenta de monitoramento de desempenho para monitoramento de saúde de primeiro nível e investigação de desempenho.

[dotnet-dump](../diagnostics/dotnet-dump.md) fornece uma maneira de coletar e analisar dumps do núcleo do Windows e Linux sem um depurador nativo.

[dotnet-trace](../diagnostics/dotnet-trace.md) coleta dados de criação de perfil do seu aplicativo que podem ajudar em cenários onde você precisa descobrir o que faz com que um aplicativo seja lento.

## <a name="wcf-web-service-reference-tool"></a>Ferramenta de referência de serviço web WCF

A ferramenta de referência [de serviçoweb](wcf-web-service-reference-guide.md) wcf (Windows Communication Foundation) é um provedor de serviços conectado do Visual Studio que fez sua estreia no [Visual Studio 2017 versão 15.5](/visualstudio/releasenotes/vs2017-relnotes-v15.5#WCFTools). Esta ferramenta recupera metadados de um serviço web na solução atual, em um local de rede ou a partir de um arquivo WSDL. Ele gera um arquivo de origem compatível com o .NET Core, definindo uma classe proxy WCF com métodos que você pode usar para acessar as operações de serviço web.

## <a name="wcf-dotnet-svcutil-tool"></a>Ferramenta dotnet-svcutil do WCF

A [ferramenta Dotnet-svcutil](dotnet-svcutil-guide.md) wcf é uma ferramenta .NET que recupera metadados de um serviço web em um local de rede ou de um arquivo WSDL. Ele gera um arquivo de origem compatível com o .NET Core, definindo uma classe proxy WCF com métodos que você pode usar para acessar as operações de serviço web.

A ferramenta **dotnet-svcutil** é uma alternativa ao provedor de serviços conectados Visual Studio, [**que**](wcf-web-service-reference-guide.md) foi enviado pela primeira vez com o Visual Studio 2017 versão 15.5. A ferramenta **dotnet-svcutil,** como uma ferramenta .NET, está disponível no Linux, macOS e Windows.

## <a name="wcf-dotnet-svcutilxmlserializer-tool"></a>Ferramenta dotnet-svcutil.xmlserializer da WCF

No .NET Framework, é possível gerar previamente um assembly de serialização usando a ferramenta svcutil. A [ferramenta dotnet-svcutil.xmlserializer](dotnet-svcutil.xmlserializer-guide.md) WCF fornece funcionalidade semelhante no .NET Core. Ele gera previamente o código de serialização C# para os tipos no aplicativo cliente, que são usados pelo Contrato de Serviço da WCF e podem ser serializados pelo <xref:System.Xml.Serialization.XmlSerializer>. Isso melhora o desempenho de inicialização da serialização de XML ao serializar ou desserializar objetos desses tipos.

## <a name="xml-serializer-generator"></a>Gerador de serializador de XML

Como o [XML Serializer Generator (sgen.exe)](../../standard/serialization/xml-serializer-generator-tool-sgen-exe.md) para o .NET Framework, o [pacote NuGet Microsoft.XmlSerializer.Generator](https://www.nuget.org/packages/Microsoft.XmlSerializer.Generator) é a solução para bibliotecas .NET Core e .NET Standard. Ele cria um assembly de serialização de XML para tipos contidos em um assembly a fim de melhorar o desempenho de inicialização da serialização de XML ao serializar ou desserializar objetos desses tipos usando <xref:System.Xml.Serialization.XmlSerializer>.
