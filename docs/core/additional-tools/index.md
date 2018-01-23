---
title: Ferramentas adicionais do .NET Core
description: "Uma visão geral das ferramentas adicionais que oferecem suporte e estendem a funcionalidade do .NET Core."
author: mlacouture
manager: wpickett
ms.author: johalex
ms.date: 01/19/2018
ms.topic: article
ms.prod: .net-core
ms.custom: mvc
ms.openlocfilehash: eac67285500e62501f3bb552deaf5b07db609d4e
ms.sourcegitcommit: 8bde7a3432f30fc771079744955c75c58c4eb393
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/20/2018
---
# <a name="net-core-additional-tools"></a><span data-ttu-id="42c29-103">Ferramentas adicionais do .NET Core</span><span class="sxs-lookup"><span data-stu-id="42c29-103">.NET Core additional tools</span></span>
<span data-ttu-id="42c29-104">Esta seção compila uma lista de ferramentas de suporte e estender a funcionalidade do .NET Core, além das ferramentas da [CLI (interface de linha de comando) do .NET Core](..\tools\index.md).</span><span class="sxs-lookup"><span data-stu-id="42c29-104">This section compiles a list of tools that support and extend the .NET Core functionality, in addition to the [.NET Core command-line interface (CLI)](..\tools\index.md) tools.</span></span>

### <a name="wcf-web-service-reference-toolwcf-web-service-reference-guidemd"></a>[<span data-ttu-id="42c29-105">Ferramenta de Referência do Serviço Web do WCF</span><span class="sxs-lookup"><span data-stu-id="42c29-105">WCF Web Service Reference Tool</span></span>](wcf-web-service-reference-guide.md)
<span data-ttu-id="42c29-106">A Referência do Serviço Web do WCF é um provedor de serviços conectados do Visual Studio que fez sua estreia no [Visual Studio 2017 versão 15.5](https://www.visualstudio.com/news/releasenotes/vs2017-relnotes#WCFTools).</span><span class="sxs-lookup"><span data-stu-id="42c29-106">The WCF Web Service Reference is a Visual Studio connected service provider that made its debut in [Visual Studio 2017 version 15.5](https://www.visualstudio.com/news/releasenotes/vs2017-relnotes#WCFTools).</span></span> <span data-ttu-id="42c29-107">Essa ferramenta recupera metadados de um serviço Web na solução atual, em um local de rede ou de um arquivo WSDL e gera um arquivo de fonte compatível com o .NET Core que contém o código de proxy de cliente do Windows Communication Foundation (WCF) que você pode usar para acessar esse serviço Web.</span><span class="sxs-lookup"><span data-stu-id="42c29-107">This tool retrieves metadata from a web service in the current solution, on a network location, or from a WSDL file, and generates a .NET Core compatible source file containing Windows Communication Foundation (WCF) client proxy code that you can use to access the web service.</span></span>

### <a name="xml-serializer-generatorxmlserializergenerator-instructionsmd"></a>[<span data-ttu-id="42c29-108">XML Serializer Generator</span><span class="sxs-lookup"><span data-stu-id="42c29-108">XML Serializer Generator</span></span>](xmlserializergenerator-instructions.md)
<span data-ttu-id="42c29-109">Como o [XML Serializer Generator (sgen.exe)](../../standard/serialization/xml-serializer-generator-tool-sgen-exe.md) para o .NET Framework, o [pacote NuGet Microsoft.XmlSerializer.Generator](https://www.nuget.org/packages/Microsoft.XmlSerializer.Generator) é a solução para bibliotecas .NET Core e .NET Standard.</span><span class="sxs-lookup"><span data-stu-id="42c29-109">Like the [Xml Serializer Generator (sgen.exe)](../../standard/serialization/xml-serializer-generator-tool-sgen-exe.md) for the .NET Framework, the [Microsoft.XmlSerializer.Generator NuGet package](https://www.nuget.org/packages/Microsoft.XmlSerializer.Generator) is the solution for .NET Core and .NET Standard libraries.</span></span> <span data-ttu-id="42c29-110">Ele cria um assembly de serialização de XML para tipos contidos em um assembly para melhorar o desempenho de inicialização de serialização de XML ao serializar ou desserializar objetos desses tipos usando <xref:System.Xml.Serialization.XmlSerializer>.</span><span class="sxs-lookup"><span data-stu-id="42c29-110">It creates an XML serialization assembly for types contained in an assembly to improve the startup performance of XML serialization when serializing or de-serializing objects of those types using <xref:System.Xml.Serialization.XmlSerializer>.</span></span>
