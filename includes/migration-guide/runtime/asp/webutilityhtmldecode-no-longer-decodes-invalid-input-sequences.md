---
ms.openlocfilehash: 0b7d6d9543035ab0a8fdda675ae71572ace12a1f
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85619768"
---
### <a name="webutilityhtmldecode-no-longer-decodes-invalid-input-sequences"></a><span data-ttu-id="a108c-101">WebUtility.HtmlDecode não decodifica mais sequências de entrada inválidas</span><span class="sxs-lookup"><span data-stu-id="a108c-101">WebUtility.HtmlDecode no longer decodes invalid input sequences</span></span>

#### <a name="details"></a><span data-ttu-id="a108c-102">Detalhes</span><span class="sxs-lookup"><span data-stu-id="a108c-102">Details</span></span>

<span data-ttu-id="a108c-103">Por padrão, os métodos de decodificação não decodificam mais uma sequência de entrada válida em uma cadeia de caracteres UTF-16 inválida.</span><span class="sxs-lookup"><span data-stu-id="a108c-103">By default, decoding methods no longer decode an invalid input sequence into an invalid UTF-16 string.</span></span> <span data-ttu-id="a108c-104">Em vez disso, eles retornam a entrada original.</span><span class="sxs-lookup"><span data-stu-id="a108c-104">Instead, they return the original input.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="a108c-105">Sugestão</span><span class="sxs-lookup"><span data-stu-id="a108c-105">Suggestion</span></span>

<span data-ttu-id="a108c-106">A alteração na saída do decodificador deve importar somente se você armazenar dados binários em vez de dados UTF-16 em cadeias de caracteres.</span><span class="sxs-lookup"><span data-stu-id="a108c-106">The change in decoder output should matter only if you store binary data instead of UTF-16 data in strings.</span></span> <span data-ttu-id="a108c-107">Para controlar explicitamente esse comportamento, defina o atributo <code>aspnet:AllowRelaxedUnicodeDecoding</code> do elemento [appSettings](~/docs/framework/configure-apps/file-schema/appsettings/index.md) como <code>true</code> para habilitar o comportamento herdado ou como <code>false</code> para habilitar o comportamento atual.</span><span class="sxs-lookup"><span data-stu-id="a108c-107">To explicitly control this behavior, set the <code>aspnet:AllowRelaxedUnicodeDecoding</code> attribute of the [appSettings](~/docs/framework/configure-apps/file-schema/appsettings/index.md) element to <code>true</code> to enable legacy behavior or to <code>false</code> to enable the current behavior.</span></span>

| <span data-ttu-id="a108c-108">Name</span><span class="sxs-lookup"><span data-stu-id="a108c-108">Name</span></span>    | <span data-ttu-id="a108c-109">Valor</span><span class="sxs-lookup"><span data-stu-id="a108c-109">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="a108c-110">Escopo</span><span class="sxs-lookup"><span data-stu-id="a108c-110">Scope</span></span>   |<span data-ttu-id="a108c-111">Secundária</span><span class="sxs-lookup"><span data-stu-id="a108c-111">Minor</span></span>|
|<span data-ttu-id="a108c-112">Versão</span><span class="sxs-lookup"><span data-stu-id="a108c-112">Version</span></span>|<span data-ttu-id="a108c-113">4.5</span><span class="sxs-lookup"><span data-stu-id="a108c-113">4.5</span></span>|
|<span data-ttu-id="a108c-114">Type</span><span class="sxs-lookup"><span data-stu-id="a108c-114">Type</span></span>|<span data-ttu-id="a108c-115">Runtime</span><span class="sxs-lookup"><span data-stu-id="a108c-115">Runtime</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="a108c-116">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="a108c-116">Affected APIs</span></span>

-<xref:System.Net.WebUtility.HtmlDecode(System.String)?displayProperty=nameWithType></li><li><xref:System.Net.WebUtility.HtmlDecode(System.String,System.IO.TextWriter)?displayProperty=nameWithType></li><li><xref:System.Net.WebUtility.UrlDecode(System.String)?displayProperty=nameWithType></li></ul>|
