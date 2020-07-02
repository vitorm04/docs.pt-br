---
ms.openlocfilehash: 7e42a294b151d07a6fdc61308cdf92df7a31a1d6
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85614284"
---
### <a name="deflatestream-uses-native-apis-for-decompression"></a><span data-ttu-id="efcf7-101">O DeflateStream usa APIs nativas para descompactação</span><span class="sxs-lookup"><span data-stu-id="efcf7-101">DeflateStream uses native APIs for decompression</span></span>

#### <a name="details"></a><span data-ttu-id="efcf7-102">Detalhes</span><span class="sxs-lookup"><span data-stu-id="efcf7-102">Details</span></span>

<span data-ttu-id="efcf7-103">Começando com o .NET Framework 4.7.2, a implementação da descompactação na classe `T:System.IO.Compression.DeflateStream` foi alterada para usar APIs nativas do Windows por padrão.</span><span class="sxs-lookup"><span data-stu-id="efcf7-103">Starting with the .NET Framework 4.7.2, the implementation of decompression in the `T:System.IO.Compression.DeflateStream` class has changed to use native Windows APIs by default.</span></span> <span data-ttu-id="efcf7-104">Normalmente, isso resulta em uma melhoria significativa de desempenho.</span><span class="sxs-lookup"><span data-stu-id="efcf7-104">Typically, this results in a substantial performance improvement.</span></span> <span data-ttu-id="efcf7-105">Todos os aplicativos .NET direcionados ao .NET Framework versão 4.7.2 ou superior usam a implementação nativo. Essa alteração pode resultar em algumas diferenças no comportamento, que incluem:</span><span class="sxs-lookup"><span data-stu-id="efcf7-105">All .NET applications targeting the .NET Framework version 4.7.2 or higher use the native implementation.This change might result in some differences in behavior, which include:</span></span>

- <span data-ttu-id="efcf7-106">As mensagens de exceção podem ser diferentes.</span><span class="sxs-lookup"><span data-stu-id="efcf7-106">Exception messages may be different.</span></span> <span data-ttu-id="efcf7-107">No entanto, o tipo de exceção gerada permanece o mesmo.</span><span class="sxs-lookup"><span data-stu-id="efcf7-107">However, the type of exception thrown remains the same.</span></span>
- <span data-ttu-id="efcf7-108">Algumas situações especiais, como não ter memória suficiente para concluir uma operação, podem ser tratadas de maneira diferente.</span><span class="sxs-lookup"><span data-stu-id="efcf7-108">Some special situations, such as not having enough memory to complete an operation, may be handled differently.</span></span>
- <span data-ttu-id="efcf7-109">Existem diferenças conhecidas para analisar o cabeçalho gzip (observação: somente o `GZipStream` definido para descompactação é afetado):</span><span class="sxs-lookup"><span data-stu-id="efcf7-109">There are known differences for parsing gzip header (note: only `GZipStream` set for decompression is affected):</span></span>
- <span data-ttu-id="efcf7-110">As exceções durante a análise de cabeçalhos inválidos podem ser geradas em momentos diferentes.</span><span class="sxs-lookup"><span data-stu-id="efcf7-110">Exceptions when parsing invalid headers may be thrown at different times.</span></span>
- <span data-ttu-id="efcf7-111">A implementação nativa impõe que os valores de alguns sinalizadores reservados dentro do cabeçalho gzip (ou seja, [FLG](http://www.zlib.org/rfc-gzip.html#header-trailer)) são definidos de acordo com a especificação, o que pode causar a geração de uma exceção em casos em que, anteriormente, valores inválidos eram ignorados.</span><span class="sxs-lookup"><span data-stu-id="efcf7-111">The native implementation enforces that values for some reserved flags inside the gzip header (i.e. [FLG](http://www.zlib.org/rfc-gzip.html#header-trailer)) are set according to the specification, which may cause it to throw an exception where previously invalid values were ignored.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="efcf7-112">Sugestão</span><span class="sxs-lookup"><span data-stu-id="efcf7-112">Suggestion</span></span>

<span data-ttu-id="efcf7-113">Se a descompactação com as APIs nativas tiver prejudicado o comportamento do aplicativo, você poderá recusar esse recurso adicionando a opção `Switch.System.IO.Compression.DoNotUseNativeZipLibraryForDecompression` à seção `runtime` do arquivo app.config e configurando-a como `true`:</span><span class="sxs-lookup"><span data-stu-id="efcf7-113">If decompression with native APIs has adversely affected the behavior of your app, you can opt out of this feature by adding the `Switch.System.IO.Compression.DoNotUseNativeZipLibraryForDecompression` switch to the `runtime` section of your app.config file and setting it to `true`:</span></span>

```xml
<?xml version="1.0" encoding="utf-8" ?>
<configuration>
  <runtime>
    <AppContextSwitchOverrides value="Switch.System.IO.Compression.DoNotUseNativeZipLibraryForDecompression=true" />
  </runtime>
</configuration>
```

| <span data-ttu-id="efcf7-114">Name</span><span class="sxs-lookup"><span data-stu-id="efcf7-114">Name</span></span>    | <span data-ttu-id="efcf7-115">Valor</span><span class="sxs-lookup"><span data-stu-id="efcf7-115">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="efcf7-116">Escopo</span><span class="sxs-lookup"><span data-stu-id="efcf7-116">Scope</span></span>   | <span data-ttu-id="efcf7-117">Secundária</span><span class="sxs-lookup"><span data-stu-id="efcf7-117">Minor</span></span>       |
| <span data-ttu-id="efcf7-118">Versão</span><span class="sxs-lookup"><span data-stu-id="efcf7-118">Version</span></span> | <span data-ttu-id="efcf7-119">4.7.2</span><span class="sxs-lookup"><span data-stu-id="efcf7-119">4.7.2</span></span>       |
| <span data-ttu-id="efcf7-120">Type</span><span class="sxs-lookup"><span data-stu-id="efcf7-120">Type</span></span>    | <span data-ttu-id="efcf7-121">Redirecionando</span><span class="sxs-lookup"><span data-stu-id="efcf7-121">Retargeting</span></span> |

#### <a name="affected-apis"></a><span data-ttu-id="efcf7-122">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="efcf7-122">Affected APIs</span></span>

- <xref:System.IO.Compression.DeflateStream?displayProperty=nameWithType>
- <xref:System.IO.Compression.GZipStream?displayProperty=nameWithType>
