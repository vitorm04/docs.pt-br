---
title: Serializar e desserializar JSON C# usando-.net
ms.date: 01/10/2020
helpviewer_keywords:
- JSON serialization
- serializing objects
- serialization
- objects, serializing
ms.openlocfilehash: c05783963ba521109fb542f247ec9e62fdb5c2d9
ms.sourcegitcommit: dfad244ba549702b649bfef3bb057e33f24a8fb2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/12/2020
ms.locfileid: "75904638"
---
# <a name="json-serialization-and-deserialization-marshalling-and-unmarshalling-in-net---overview"></a><span data-ttu-id="59edd-102">Serialização e desserialização JSON (empacotamento e desempacotamento) no .NET-visão geral</span><span class="sxs-lookup"><span data-stu-id="59edd-102">JSON serialization and deserialization (marshalling and unmarshalling) in .NET - overview</span></span>

<span data-ttu-id="59edd-103">O namespace `System.Text.Json` fornece funcionalidade para serializar e desserializar de JavaScript Object Notation (JSON).</span><span class="sxs-lookup"><span data-stu-id="59edd-103">The `System.Text.Json` namespace provides functionality for serializing to and deserializing from JavaScript Object Notation (JSON).</span></span>

<span data-ttu-id="59edd-104">O design da biblioteca enfatiza o alto desempenho e a baixa alocação de memória em um amplo conjunto de recursos.</span><span class="sxs-lookup"><span data-stu-id="59edd-104">The library design emphasizes high performance and low memory allocation over an extensive feature set.</span></span> <span data-ttu-id="59edd-105">O suporte interno a UTF-8 otimiza o processo de leitura e gravação de texto JSON codificado como UTF-8, que é a codificação mais predominante para os dados na Web e nos arquivos no disco.</span><span class="sxs-lookup"><span data-stu-id="59edd-105">Built-in UTF-8 support optimizes the process of reading and writing JSON text encoded as UTF-8, which is the most prevalent encoding for data on the web and files on disk.</span></span>

<span data-ttu-id="59edd-106">A biblioteca também fornece classes para trabalhar com um modelo de objeto de documento (DOM) na memória.</span><span class="sxs-lookup"><span data-stu-id="59edd-106">The library also provides classes for working with an in-memory document object model (DOM).</span></span> <span data-ttu-id="59edd-107">Esse recurso permite o acesso aleatório somente leitura dos elementos em um arquivo JSON ou cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="59edd-107">This feature enables random read-only access of the elements in a JSON file or string.</span></span> 

## <a name="how-to-get-the-library"></a><span data-ttu-id="59edd-108">Como obter a biblioteca</span><span class="sxs-lookup"><span data-stu-id="59edd-108">How to get the library</span></span>

* <span data-ttu-id="59edd-109">A biblioteca é interna como parte da estrutura compartilhada do [.NET Core 3,0](https://aka.ms/netcore3download) .</span><span class="sxs-lookup"><span data-stu-id="59edd-109">The library is built-in as part of the [.NET Core 3.0](https://aka.ms/netcore3download) shared framework.</span></span>
* <span data-ttu-id="59edd-110">Para outras estruturas de destino, instale o pacote NuGet [System. Text. JSON](https://www.nuget.org/packages/System.Text.Json) .</span><span class="sxs-lookup"><span data-stu-id="59edd-110">For other target frameworks, install the [System.Text.Json](https://www.nuget.org/packages/System.Text.Json) NuGet package.</span></span> <span data-ttu-id="59edd-111">O pacote dá suporte a:</span><span class="sxs-lookup"><span data-stu-id="59edd-111">The package supports:</span></span>
  * <span data-ttu-id="59edd-112">.NET Standard 2,0 e versões posteriores</span><span class="sxs-lookup"><span data-stu-id="59edd-112">.NET Standard 2.0 and later versions</span></span>
  * <span data-ttu-id="59edd-113">.NET Framework 4.7.2 e versões posteriores</span><span class="sxs-lookup"><span data-stu-id="59edd-113">.NET Framework 4.7.2 and later versions</span></span>
  * <span data-ttu-id="59edd-114">.NET Core 2,0, 2,1 e 2,2</span><span class="sxs-lookup"><span data-stu-id="59edd-114">.NET Core 2.0, 2.1, and 2.2</span></span>

## <a name="additional-resources"></a><span data-ttu-id="59edd-115">Recursos adicionais</span><span class="sxs-lookup"><span data-stu-id="59edd-115">Additional resources</span></span>

* [<span data-ttu-id="59edd-116">Como usar a biblioteca</span><span class="sxs-lookup"><span data-stu-id="59edd-116">How to use the library</span></span>](system-text-json-how-to.md)
* [<span data-ttu-id="59edd-117">Como migrar do Newtonsoft. JSON</span><span class="sxs-lookup"><span data-stu-id="59edd-117">How to migrate from Newtonsoft.Json</span></span>](system-text-json-migrate-from-newtonsoft-how-to.md)
* [<span data-ttu-id="59edd-118">Como escrever conversores</span><span class="sxs-lookup"><span data-stu-id="59edd-118">How to write converters</span></span>](system-text-json-converters-how-to.md)
* [<span data-ttu-id="59edd-119">Código-fonte System. Text. JSON</span><span class="sxs-lookup"><span data-stu-id="59edd-119">System.Text.Json source code</span></span>](https://github.com/dotnet/runtime/tree/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json)
* [<span data-ttu-id="59edd-120">Referência da API System. Text. JSON</span><span class="sxs-lookup"><span data-stu-id="59edd-120">System.Text.Json API reference</span></span>](xref:System.Text.Json)
* [<span data-ttu-id="59edd-121">Referência da API System. Text. JSON. Serialization</span><span class="sxs-lookup"><span data-stu-id="59edd-121">System.Text.Json.Serialization API reference</span></span>](xref:System.Text.Json.Serialization)
<!-- * [Roadmap](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/roadmap/README.md)-->
