---
title: Serializar e desserializar JSON usando C#-.NET
ms.date: 01/10/2020
no-loc:
- System.Text.Json
- Newtonsoft.Json
helpviewer_keywords:
- JSON serialization
- serializing objects
- serialization
- objects, serializing
ms.openlocfilehash: 660a2831aa6a807486fc47eae880bcd11347c547
ms.sourcegitcommit: 00aa62e2f469c2272a457b04e66b4cc3c97a800b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/28/2020
ms.locfileid: "78159540"
---
# <a name="json-serialization-and-deserialization-marshalling-and-unmarshalling-in-net---overview"></a><span data-ttu-id="d0833-102">Serialização e desserialização JSON (empacotamento e desempacotamento) no .NET-visão geral</span><span class="sxs-lookup"><span data-stu-id="d0833-102">JSON serialization and deserialization (marshalling and unmarshalling) in .NET - overview</span></span>

<span data-ttu-id="d0833-103">O `System.Text.Json` namespace fornece a funcionalidade para serializar e desserializar de JavaScript Object Notation (JSON).</span><span class="sxs-lookup"><span data-stu-id="d0833-103">The `System.Text.Json` namespace provides functionality for serializing to and deserializing from JavaScript Object Notation (JSON).</span></span>

<span data-ttu-id="d0833-104">O design da biblioteca enfatiza o alto desempenho e a baixa alocação de memória em um amplo conjunto de recursos.</span><span class="sxs-lookup"><span data-stu-id="d0833-104">The library design emphasizes high performance and low memory allocation over an extensive feature set.</span></span> <span data-ttu-id="d0833-105">O suporte interno a UTF-8 otimiza o processo de leitura e gravação de texto JSON codificado como UTF-8, que é a codificação mais predominante para os dados na Web e nos arquivos no disco.</span><span class="sxs-lookup"><span data-stu-id="d0833-105">Built-in UTF-8 support optimizes the process of reading and writing JSON text encoded as UTF-8, which is the most prevalent encoding for data on the web and files on disk.</span></span>

<span data-ttu-id="d0833-106">A biblioteca também fornece classes para trabalhar com um modelo de objeto de documento (DOM) na memória.</span><span class="sxs-lookup"><span data-stu-id="d0833-106">The library also provides classes for working with an in-memory document object model (DOM).</span></span> <span data-ttu-id="d0833-107">Esse recurso permite o acesso aleatório somente leitura dos elementos em um arquivo JSON ou cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="d0833-107">This feature enables random read-only access of the elements in a JSON file or string.</span></span>

## <a name="how-to-get-the-library"></a><span data-ttu-id="d0833-108">Como obter a biblioteca</span><span class="sxs-lookup"><span data-stu-id="d0833-108">How to get the library</span></span>

* <span data-ttu-id="d0833-109">A biblioteca é interna como parte da estrutura compartilhada do [.NET Core 3,0](https://aka.ms/netcore3download) .</span><span class="sxs-lookup"><span data-stu-id="d0833-109">The library is built-in as part of the [.NET Core 3.0](https://aka.ms/netcore3download) shared framework.</span></span>
* <span data-ttu-id="d0833-110">Para outras estruturas de destino, instale o [System.Text.Json](https://www.nuget.org/packages/System.Text.Json) pacote NuGet.</span><span class="sxs-lookup"><span data-stu-id="d0833-110">For other target frameworks, install the [System.Text.Json](https://www.nuget.org/packages/System.Text.Json) NuGet package.</span></span> <span data-ttu-id="d0833-111">O pacote dá suporte a:</span><span class="sxs-lookup"><span data-stu-id="d0833-111">The package supports:</span></span>
  * <span data-ttu-id="d0833-112">.NET Standard 2,0 e versões posteriores</span><span class="sxs-lookup"><span data-stu-id="d0833-112">.NET Standard 2.0 and later versions</span></span>
  * <span data-ttu-id="d0833-113">.NET Framework 4.7.2 e versões posteriores</span><span class="sxs-lookup"><span data-stu-id="d0833-113">.NET Framework 4.7.2 and later versions</span></span>
  * <span data-ttu-id="d0833-114">.NET Core 2,0, 2,1 e 2,2</span><span class="sxs-lookup"><span data-stu-id="d0833-114">.NET Core 2.0, 2.1, and 2.2</span></span>

## <a name="additional-resources"></a><span data-ttu-id="d0833-115">Recursos adicionais</span><span class="sxs-lookup"><span data-stu-id="d0833-115">Additional resources</span></span>

* [<span data-ttu-id="d0833-116">Como usar a biblioteca</span><span class="sxs-lookup"><span data-stu-id="d0833-116">How to use the library</span></span>](system-text-json-how-to.md)
* <span data-ttu-id="d0833-117">[Como migrar doNewtonsoft.Json](system-text-json-migrate-from-newtonsoft-how-to.md)</span><span class="sxs-lookup"><span data-stu-id="d0833-117">[How to migrate from Newtonsoft.Json](system-text-json-migrate-from-newtonsoft-how-to.md)</span></span>
* [<span data-ttu-id="d0833-118">Como escrever conversores</span><span class="sxs-lookup"><span data-stu-id="d0833-118">How to write converters</span></span>](system-text-json-converters-how-to.md)
* <span data-ttu-id="d0833-119">[System.Text.Jsoncódigo-fonte](https://github.com/dotnet/runtime/tree/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json)</span><span class="sxs-lookup"><span data-stu-id="d0833-119">[System.Text.Json source code](https://github.com/dotnet/runtime/tree/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json)</span></span>
* <span data-ttu-id="d0833-120">[System.Text.JsonReferência de API](xref:System.Text.Json)</span><span class="sxs-lookup"><span data-stu-id="d0833-120">[System.Text.Json API reference](xref:System.Text.Json)</span></span>
* <span data-ttu-id="d0833-121">[System.Text.Json. Referência de API de serialização](xref:System.Text.Json.Serialization)</span><span class="sxs-lookup"><span data-stu-id="d0833-121">[System.Text.Json.Serialization API reference](xref:System.Text.Json.Serialization)</span></span>
<!-- * [Roadmap](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/roadmap/README.md)-->
