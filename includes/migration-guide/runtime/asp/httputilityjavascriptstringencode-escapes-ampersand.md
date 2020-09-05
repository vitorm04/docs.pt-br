---
ms.openlocfilehash: 12fb72d5ee9fc0d6c57899589cb2b0da7db41f4a
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/05/2020
ms.locfileid: "89497451"
---
### <a name="httputilityjavascriptstringencode-escapes-ampersand"></a><span data-ttu-id="78650-101">HttpUtility.JavaScriptStringEncode escapa o E comercial</span><span class="sxs-lookup"><span data-stu-id="78650-101">HttpUtility.JavaScriptStringEncode escapes ampersand</span></span>

#### <a name="details"></a><span data-ttu-id="78650-102">Detalhes</span><span class="sxs-lookup"><span data-stu-id="78650-102">Details</span></span>

<span data-ttu-id="78650-103">A partir do .NET Framework 4.5, <xref:System.Web.HttpUtility.JavaScriptStringEncode(System.String)?displayProperty=fullName> ignora o caractere E comercial (&amp;).</span><span class="sxs-lookup"><span data-stu-id="78650-103">Starting with the .NET Framework 4.5, <xref:System.Web.HttpUtility.JavaScriptStringEncode(System.String)?displayProperty=fullName> escapes the ampersand (&amp;) character.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="78650-104">Sugestão</span><span class="sxs-lookup"><span data-stu-id="78650-104">Suggestion</span></span>

<span data-ttu-id="78650-105">Se seu aplicativo depende do comportamento anterior desse método, você poderá adicionar uma definição aspnet:JavaScriptDoNotEncodeAmpersand ao [elemento appSettings do ASP.NET](https://docs.microsoft.com/previous-versions/aspnet/hh975440(v=vs.120)) no seu arquivo de configuração.</span><span class="sxs-lookup"><span data-stu-id="78650-105">If your app depends on the previous behavior of this method, you can add an aspnet:JavaScriptDoNotEncodeAmpersand setting to the [ASP.NET appSettings element](https://docs.microsoft.com/previous-versions/aspnet/hh975440(v=vs.120)) in your configuration file.</span></span>

| <span data-ttu-id="78650-106">Nome</span><span class="sxs-lookup"><span data-stu-id="78650-106">Name</span></span>    | <span data-ttu-id="78650-107">Valor</span><span class="sxs-lookup"><span data-stu-id="78650-107">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="78650-108">Escopo</span><span class="sxs-lookup"><span data-stu-id="78650-108">Scope</span></span>   |<span data-ttu-id="78650-109">Secundária</span><span class="sxs-lookup"><span data-stu-id="78650-109">Minor</span></span>|
|<span data-ttu-id="78650-110">Versão</span><span class="sxs-lookup"><span data-stu-id="78650-110">Version</span></span>|<span data-ttu-id="78650-111">4.5</span><span class="sxs-lookup"><span data-stu-id="78650-111">4.5</span></span>|
|<span data-ttu-id="78650-112">Tipo</span><span class="sxs-lookup"><span data-stu-id="78650-112">Type</span></span>|<span data-ttu-id="78650-113">Runtime</span><span class="sxs-lookup"><span data-stu-id="78650-113">Runtime</span></span>|

#### <a name="affected-apis"></a><span data-ttu-id="78650-114">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="78650-114">Affected APIs</span></span>

- <xref:System.Web.HttpUtility.JavaScriptStringEncode(System.String)?displayProperty=nameWithType>
- <xref:System.Web.HttpUtility.JavaScriptStringEncode(System.String,System.Boolean)?displayProperty=nameWithType>

<!--

#### Affected APIs

- `M:System.Web.HttpUtility.JavaScriptStringEncode(System.String)`
- `M:System.Web.HttpUtility.JavaScriptStringEncode(System.String,System.Boolean)`

-->
