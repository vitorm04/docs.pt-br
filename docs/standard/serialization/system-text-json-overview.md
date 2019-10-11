---
title: Serializar e desserializar JSON C# usando-.net
author: tdykstra
ms.author: tdykstra
ms.date: 09/16/2019
helpviewer_keywords:
- JSON serialization
- serializing objects
- serialization
- objects, serializing
ms.assetid: 4d1111c0-9447-4231-a997-96a2b74b3453
ms.openlocfilehash: 5ce98a7908470a402779436db43333d46f5101fc
ms.sourcegitcommit: dfd612ba454ce775a766bcc6fe93bc1d43dfda47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/09/2019
ms.locfileid: "72180149"
---
# <a name="json-serialization-in-net---overview"></a><span data-ttu-id="616bc-102">Serialização JSON no .NET-visão geral</span><span class="sxs-lookup"><span data-stu-id="616bc-102">JSON serialization in .NET - overview</span></span>

<span data-ttu-id="616bc-103">O namespace `System.Text.Json` fornece funcionalidade para serializar e desserializar de JavaScript Object Notation (JSON).</span><span class="sxs-lookup"><span data-stu-id="616bc-103">The `System.Text.Json` namespace provides functionality for serializing to and deserializing from JavaScript Object Notation (JSON).</span></span>

<span data-ttu-id="616bc-104">O design da biblioteca enfatiza o alto desempenho e a baixa alocação de memória em um amplo conjunto de recursos.</span><span class="sxs-lookup"><span data-stu-id="616bc-104">The library design emphasizes high performance and low memory allocation over an extensive feature set.</span></span> <span data-ttu-id="616bc-105">O suporte interno a UTF-8 otimiza o processo de leitura e gravação de texto JSON codificado como UTF-8, que é a codificação mais predominante para os dados na Web e nos arquivos no disco.</span><span class="sxs-lookup"><span data-stu-id="616bc-105">Built-in UTF-8 support optimizes the process of reading and writing JSON text encoded as UTF-8, which is the most prevalent encoding for data on the web and files on disk.</span></span>

<span data-ttu-id="616bc-106">A biblioteca também fornece classes para trabalhar com um modelo de objeto de documento (DOM) na memória.</span><span class="sxs-lookup"><span data-stu-id="616bc-106">The library also provides classes for working with an in-memory document object model (DOM).</span></span> <span data-ttu-id="616bc-107">Esse recurso permite o acesso aleatório somente leitura dos elementos em um arquivo JSON ou cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="616bc-107">This feature enables random read-only access of the elements in a JSON file or string.</span></span> 

## <a name="how-to-get-the-library"></a><span data-ttu-id="616bc-108">Como obter a biblioteca</span><span class="sxs-lookup"><span data-stu-id="616bc-108">How to get the library</span></span>

* <span data-ttu-id="616bc-109">A biblioteca é interna como parte da estrutura compartilhada do [.NET Core 3,0](https://aka.ms/netcore3download) .</span><span class="sxs-lookup"><span data-stu-id="616bc-109">The library is built-in as part of the [.NET Core 3.0](https://aka.ms/netcore3download) shared framework.</span></span>
* <span data-ttu-id="616bc-110">Para outras estruturas de destino, instale o pacote NuGet [System. Text. JSON](https://www.nuget.org/packages/System.Text.Json) .</span><span class="sxs-lookup"><span data-stu-id="616bc-110">For other target frameworks, install the [System.Text.Json](https://www.nuget.org/packages/System.Text.Json) NuGet package.</span></span> <span data-ttu-id="616bc-111">O pacote dá suporte a:</span><span class="sxs-lookup"><span data-stu-id="616bc-111">The package supports:</span></span>
  * <span data-ttu-id="616bc-112">.NET Standard 2,0 e versões posteriores</span><span class="sxs-lookup"><span data-stu-id="616bc-112">.NET Standard 2.0 and later versions</span></span>
  * <span data-ttu-id="616bc-113">.NET Framework 4.6.1 e versões posteriores</span><span class="sxs-lookup"><span data-stu-id="616bc-113">.NET Framework 4.6.1 and later versions</span></span>
  * <span data-ttu-id="616bc-114">.NET Core 2,0, 2,1 e 2,2</span><span class="sxs-lookup"><span data-stu-id="616bc-114">.NET Core 2.0, 2.1, and 2.2</span></span>

## <a name="additional-resources"></a><span data-ttu-id="616bc-115">Recursos adicionais</span><span class="sxs-lookup"><span data-stu-id="616bc-115">Additional resources</span></span>

* [<span data-ttu-id="616bc-116">Como usar a biblioteca</span><span class="sxs-lookup"><span data-stu-id="616bc-116">How to use the library</span></span>](system-text-json-how-to.md)
* [<span data-ttu-id="616bc-117">Código-fonte</span><span class="sxs-lookup"><span data-stu-id="616bc-117">Source code</span></span>](https://github.com/dotnet/corefx/tree/master/src/System.Text.Json)
* [<span data-ttu-id="616bc-118">Referência de API</span><span class="sxs-lookup"><span data-stu-id="616bc-118">API reference</span></span>](xref:System.Text.Json)
* [<span data-ttu-id="616bc-119">Roadmap</span><span class="sxs-lookup"><span data-stu-id="616bc-119">Roadmap</span></span>](https://github.com/dotnet/corefx/blob/master/src/System.Text.Json/roadmap/README.md)
* <span data-ttu-id="616bc-120">Problemas do GitHub no repositório dotnet/corefx</span><span class="sxs-lookup"><span data-stu-id="616bc-120">GitHub issues in the dotnet/corefx repository</span></span>
  * [<span data-ttu-id="616bc-121">Discussão sobre o desenvolvimento de System. Text. JSON</span><span class="sxs-lookup"><span data-stu-id="616bc-121">Discussion about the development of System.Text.Json</span></span>](https://github.com/dotnet/corefx/issues/33115)
  * [<span data-ttu-id="616bc-122">Todos os problemas de System. Text. JSON</span><span class="sxs-lookup"><span data-stu-id="616bc-122">All System.Text.Json issues</span></span>](https://github.com/dotnet/corefx/issues?q=is%3Aopen+is%3Aissue+label%3Aarea-System.Text.Json)
  * [<span data-ttu-id="616bc-123">Problemas de System. Text. JSON rotulados como JSON-funcionalidade-doc</span><span class="sxs-lookup"><span data-stu-id="616bc-123">System.Text.Json issues labeled json-functionality-doc</span></span>](https://github.com/dotnet/corefx/labels/json-functionality-doc)
