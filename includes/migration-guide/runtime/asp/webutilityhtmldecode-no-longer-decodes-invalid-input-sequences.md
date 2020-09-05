---
ms.openlocfilehash: ef3114a4eb9f62030c3ec36d3b463d07ccd59f6d
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/05/2020
ms.locfileid: "89497388"
---
### <a name="webutilityhtmldecode-no-longer-decodes-invalid-input-sequences"></a><span data-ttu-id="2e45c-101">WebUtility.HtmlDecode não decodifica mais sequências de entrada inválidas</span><span class="sxs-lookup"><span data-stu-id="2e45c-101">WebUtility.HtmlDecode no longer decodes invalid input sequences</span></span>

#### <a name="details"></a><span data-ttu-id="2e45c-102">Detalhes</span><span class="sxs-lookup"><span data-stu-id="2e45c-102">Details</span></span>

<span data-ttu-id="2e45c-103">Por padrão, os métodos de decodificação não decodificam mais uma sequência de entrada válida em uma cadeia de caracteres UTF-16 inválida.</span><span class="sxs-lookup"><span data-stu-id="2e45c-103">By default, decoding methods no longer decode an invalid input sequence into an invalid UTF-16 string.</span></span> <span data-ttu-id="2e45c-104">Em vez disso, eles retornam a entrada original.</span><span class="sxs-lookup"><span data-stu-id="2e45c-104">Instead, they return the original input.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="2e45c-105">Sugestão</span><span class="sxs-lookup"><span data-stu-id="2e45c-105">Suggestion</span></span>

<span data-ttu-id="2e45c-106">A alteração na saída do decodificador deve importar somente se você armazenar dados binários em vez de dados UTF-16 em cadeias de caracteres.</span><span class="sxs-lookup"><span data-stu-id="2e45c-106">The change in decoder output should matter only if you store binary data instead of UTF-16 data in strings.</span></span> <span data-ttu-id="2e45c-107">Para controlar explicitamente esse comportamento, defina o atributo <code>aspnet:AllowRelaxedUnicodeDecoding</code> do elemento [appSettings](~/docs/framework/configure-apps/file-schema/appsettings/index.md) como <code>true</code> para habilitar o comportamento herdado ou como <code>false</code> para habilitar o comportamento atual.</span><span class="sxs-lookup"><span data-stu-id="2e45c-107">To explicitly control this behavior, set the <code>aspnet:AllowRelaxedUnicodeDecoding</code> attribute of the [appSettings](~/docs/framework/configure-apps/file-schema/appsettings/index.md) element to <code>true</code> to enable legacy behavior or to <code>false</code> to enable the current behavior.</span></span>

| <span data-ttu-id="2e45c-108">Nome</span><span class="sxs-lookup"><span data-stu-id="2e45c-108">Name</span></span>    | <span data-ttu-id="2e45c-109">Valor</span><span class="sxs-lookup"><span data-stu-id="2e45c-109">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="2e45c-110">Escopo</span><span class="sxs-lookup"><span data-stu-id="2e45c-110">Scope</span></span>   |<span data-ttu-id="2e45c-111">Secundária</span><span class="sxs-lookup"><span data-stu-id="2e45c-111">Minor</span></span>|
|<span data-ttu-id="2e45c-112">Versão</span><span class="sxs-lookup"><span data-stu-id="2e45c-112">Version</span></span>|<span data-ttu-id="2e45c-113">4.5</span><span class="sxs-lookup"><span data-stu-id="2e45c-113">4.5</span></span>|
|<span data-ttu-id="2e45c-114">Tipo</span><span class="sxs-lookup"><span data-stu-id="2e45c-114">Type</span></span>|<span data-ttu-id="2e45c-115">Runtime</span><span class="sxs-lookup"><span data-stu-id="2e45c-115">Runtime</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="2e45c-116">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="2e45c-116">Affected APIs</span></span>

- <xref:System.Net.WebUtility.HtmlDecode(System.String)?displayProperty=nameWithType>
- <xref:System.Net.WebUtility.HtmlDecode(System.String,System.IO.TextWriter)?displayProperty=nameWithType>
- <xref:System.Net.WebUtility.UrlDecode(System.String)?displayProperty=nameWithType>

<!--

#### Affected APIs

- `M:System.Net.WebUtility.HtmlDecode(System.String)`
- `M:System.Net.WebUtility.HtmlDecode(System.String,System.IO.TextWriter)`
- `M:System.Net.WebUtility.UrlDecode(System.String)`

-->
