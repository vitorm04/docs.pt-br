---
ms.openlocfilehash: faf9459ab9002e6149560e2a3452265fa246bf6b
ms.sourcegitcommit: ef86c24c418439b8bb5e3e7d64bbdbe5e11c3e9c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/21/2020
ms.locfileid: "88720172"
---
### <a name="uri-paths-with-non-ascii-characters-parse-correctly-on-unix"></a><span data-ttu-id="270d2-101">Caminhos de URI com caracteres não ASCII são analisados corretamente no UNIX</span><span class="sxs-lookup"><span data-stu-id="270d2-101">URI paths with non-ASCII characters parse correctly on Unix</span></span>

<span data-ttu-id="270d2-102">Um bug foi corrigido na <xref:System.Uri?displayProperty=fullName> classe, de modo que os caminhos de URI absolutos que contêm caracteres não-ASCII agora são analisados corretamente em plataformas UNIX.</span><span class="sxs-lookup"><span data-stu-id="270d2-102">A bug was fixed in the <xref:System.Uri?displayProperty=fullName> class such that absolute URI paths that contain non-ASCII characters now parse correctly on Unix platforms.</span></span>

#### <a name="change-description"></a><span data-ttu-id="270d2-103">Descrição das alterações</span><span class="sxs-lookup"><span data-stu-id="270d2-103">Change description</span></span>

<span data-ttu-id="270d2-104">Nas versões anteriores do .NET, caminhos de URI absolutos que contêm caracteres não ASCII são analisados incorretamente em plataformas UNIX e os segmentos do caminho são duplicados.</span><span class="sxs-lookup"><span data-stu-id="270d2-104">In previous versions of .NET, absolute URI paths that contain non-ASCII characters are parsed incorrectly on Unix platforms, and segments of the path are duplicated.</span></span> <span data-ttu-id="270d2-105">(Caminhos absolutos são aqueles que começam com "/".) O problema de análise foi corrigido para o .NET 5,0.</span><span class="sxs-lookup"><span data-stu-id="270d2-105">(Absolute paths are those that start with "/".) The parsing issue has been fixed for .NET 5.0.</span></span> <span data-ttu-id="270d2-106">Se você mudar de uma versão anterior do .NET para o .NET 5,0 ou posterior, você obterá valores diferentes produzidos por <xref:System.Uri.AbsoluteUri?displayProperty=nameWithType> , <xref:System.Uri.ToString?displayProperty=nameWithType> e outros <xref:System.Uri> Membros.</span><span class="sxs-lookup"><span data-stu-id="270d2-106">If you move from a previous version of .NET to .NET 5.0 or later, you'll get different values produced by <xref:System.Uri.AbsoluteUri?displayProperty=nameWithType>, <xref:System.Uri.ToString?displayProperty=nameWithType>, and other <xref:System.Uri> members.</span></span>

<span data-ttu-id="270d2-107">Considere a saída do código a seguir quando executada no UNIX.</span><span class="sxs-lookup"><span data-stu-id="270d2-107">Consider the output of the following code when run on Unix.</span></span>

```csharp
var myUri = new Uri("/üri");

Console.WriteLine($"AbsoluteUri: {myUri.AbsoluteUri}");
Console.WriteLine($"ToString: {myUri.ToString()}");
```

<span data-ttu-id="270d2-108">Saída na versão anterior do .NET:</span><span class="sxs-lookup"><span data-stu-id="270d2-108">Output on previous .NET version:</span></span>

```text
AbsoluteUri: /%C3%BCri/%C3%BCri
ToString: /üri/üri
```

<span data-ttu-id="270d2-109">Saída no .NET 5,0 ou versão posterior:</span><span class="sxs-lookup"><span data-stu-id="270d2-109">Output on .NET 5.0 or later version:</span></span>

```text
AbsoluteUri: /%C3%BCri
ToString: /üri
```

#### <a name="version-introduced"></a><span data-ttu-id="270d2-110">Versão introduzida</span><span class="sxs-lookup"><span data-stu-id="270d2-110">Version introduced</span></span>

<span data-ttu-id="270d2-111">5,0</span><span class="sxs-lookup"><span data-stu-id="270d2-111">5.0</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="270d2-112">Ação recomendada</span><span class="sxs-lookup"><span data-stu-id="270d2-112">Recommended action</span></span>

<span data-ttu-id="270d2-113">Se você tiver um código que espera e contas para os segmentos de caminho duplicados, você pode remover esse código.</span><span class="sxs-lookup"><span data-stu-id="270d2-113">If you have code that expects and accounts for the duplicated path segments, you can remove that code.</span></span>

#### <a name="category"></a><span data-ttu-id="270d2-114">Categoria</span><span class="sxs-lookup"><span data-stu-id="270d2-114">Category</span></span>

<span data-ttu-id="270d2-115">Bibliotecas principais do .NET</span><span class="sxs-lookup"><span data-stu-id="270d2-115">Core .NET libraries</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="270d2-116">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="270d2-116">Affected APIs</span></span>

- <xref:System.Uri?displayProperty=fullName>

<!--

#### Affected APIs

- `T:System.Uri`

-->
