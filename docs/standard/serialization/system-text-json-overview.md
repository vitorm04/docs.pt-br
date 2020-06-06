---
title: Serializar e desserializar JSON usando C#-.NET
description: Esta visão geral descreve a System.Text.Json funcionalidade de namespace para serialização e desserialização do JSON no .net.
ms.date: 01/10/2020
no-loc:
- System.Text.Json
- Newtonsoft.Json
helpviewer_keywords:
- JSON serialization
- serializing objects
- serialization
- objects, serializing
ms.openlocfilehash: 909d979d46b30939e304af071de65d230febd92d
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/06/2020
ms.locfileid: "83380132"
---
# <a name="json-serialization-and-deserialization-marshalling-and-unmarshalling-in-net---overview"></a><span data-ttu-id="f8595-103">Serialização e desserialização JSON (empacotamento e desempacotamento) no .NET-visão geral</span><span class="sxs-lookup"><span data-stu-id="f8595-103">JSON serialization and deserialization (marshalling and unmarshalling) in .NET - overview</span></span>

<span data-ttu-id="f8595-104">O `System.Text.Json` namespace fornece a funcionalidade para serializar e desserializar de JavaScript Object Notation (JSON).</span><span class="sxs-lookup"><span data-stu-id="f8595-104">The `System.Text.Json` namespace provides functionality for serializing to and deserializing from JavaScript Object Notation (JSON).</span></span>

<span data-ttu-id="f8595-105">O design da biblioteca enfatiza o alto desempenho e a baixa alocação de memória em um amplo conjunto de recursos.</span><span class="sxs-lookup"><span data-stu-id="f8595-105">The library design emphasizes high performance and low memory allocation over an extensive feature set.</span></span> <span data-ttu-id="f8595-106">O suporte interno a UTF-8 otimiza o processo de leitura e gravação de texto JSON codificado como UTF-8, que é a codificação mais predominante para os dados na Web e nos arquivos no disco.</span><span class="sxs-lookup"><span data-stu-id="f8595-106">Built-in UTF-8 support optimizes the process of reading and writing JSON text encoded as UTF-8, which is the most prevalent encoding for data on the web and files on disk.</span></span>

<span data-ttu-id="f8595-107">A biblioteca também fornece classes para trabalhar com um modelo de objeto de documento (DOM) na memória.</span><span class="sxs-lookup"><span data-stu-id="f8595-107">The library also provides classes for working with an in-memory document object model (DOM).</span></span> <span data-ttu-id="f8595-108">Esse recurso permite o acesso aleatório somente leitura dos elementos em um arquivo JSON ou cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="f8595-108">This feature enables random read-only access of the elements in a JSON file or string.</span></span>

## <a name="how-to-get-the-library"></a><span data-ttu-id="f8595-109">Como obter a biblioteca</span><span class="sxs-lookup"><span data-stu-id="f8595-109">How to get the library</span></span>

* <span data-ttu-id="f8595-110">A biblioteca é interna como parte da estrutura compartilhada do [.NET Core 3,0](https://aka.ms/netcore3download) .</span><span class="sxs-lookup"><span data-stu-id="f8595-110">The library is built-in as part of the [.NET Core 3.0](https://aka.ms/netcore3download) shared framework.</span></span>
* <span data-ttu-id="f8595-111">Para outras estruturas de destino, instale o [System.Text.Json](https://www.nuget.org/packages/System.Text.Json) pacote NuGet.</span><span class="sxs-lookup"><span data-stu-id="f8595-111">For other target frameworks, install the [System.Text.Json](https://www.nuget.org/packages/System.Text.Json) NuGet package.</span></span> <span data-ttu-id="f8595-112">O pacote dá suporte a:</span><span class="sxs-lookup"><span data-stu-id="f8595-112">The package supports:</span></span>
  * <span data-ttu-id="f8595-113">.NET Standard 2,0 e versões posteriores</span><span class="sxs-lookup"><span data-stu-id="f8595-113">.NET Standard 2.0 and later versions</span></span>
  * <span data-ttu-id="f8595-114">.NET Framework 4.7.2 e versões posteriores</span><span class="sxs-lookup"><span data-stu-id="f8595-114">.NET Framework 4.7.2 and later versions</span></span>
  * <span data-ttu-id="f8595-115">.NET Core 2,0, 2,1 e 2,2</span><span class="sxs-lookup"><span data-stu-id="f8595-115">.NET Core 2.0, 2.1, and 2.2</span></span>

## <a name="additional-resources"></a><span data-ttu-id="f8595-116">Recursos adicionais</span><span class="sxs-lookup"><span data-stu-id="f8595-116">Additional resources</span></span>

* [<span data-ttu-id="f8595-117">Como usar a biblioteca</span><span class="sxs-lookup"><span data-stu-id="f8595-117">How to use the library</span></span>](system-text-json-how-to.md)
* <span data-ttu-id="f8595-118">[Como migrar doNewtonsoft.Json](system-text-json-migrate-from-newtonsoft-how-to.md)</span><span class="sxs-lookup"><span data-stu-id="f8595-118">[How to migrate from Newtonsoft.Json](system-text-json-migrate-from-newtonsoft-how-to.md)</span></span>
* [<span data-ttu-id="f8595-119">Como escrever conversores</span><span class="sxs-lookup"><span data-stu-id="f8595-119">How to write converters</span></span>](system-text-json-converters-how-to.md)
* <span data-ttu-id="f8595-120">[System.Text.Jsoncódigo-fonte](https://github.com/dotnet/runtime/tree/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json)</span><span class="sxs-lookup"><span data-stu-id="f8595-120">[System.Text.Json source code](https://github.com/dotnet/runtime/tree/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json)</span></span>
* <span data-ttu-id="f8595-121">[System.Text.JsonReferência de API](xref:System.Text.Json)</span><span class="sxs-lookup"><span data-stu-id="f8595-121">[System.Text.Json API reference](xref:System.Text.Json)</span></span>
* <span data-ttu-id="f8595-122">[System.Text.Json. Referência de API de serialização](xref:System.Text.Json.Serialization)</span><span class="sxs-lookup"><span data-stu-id="f8595-122">[System.Text.Json.Serialization API reference](xref:System.Text.Json.Serialization)</span></span>
<!-- * [Roadmap](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/roadmap/README.md)-->
