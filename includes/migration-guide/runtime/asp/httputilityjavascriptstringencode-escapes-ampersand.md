---
ms.openlocfilehash: d587e542a72d584502ac3ac892619cc38b88ef77
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85619765"
---
### <a name="httputilityjavascriptstringencode-escapes-ampersand"></a><span data-ttu-id="9ceb3-101">HttpUtility.JavaScriptStringEncode escapa o E comercial</span><span class="sxs-lookup"><span data-stu-id="9ceb3-101">HttpUtility.JavaScriptStringEncode escapes ampersand</span></span>

#### <a name="details"></a><span data-ttu-id="9ceb3-102">Detalhes</span><span class="sxs-lookup"><span data-stu-id="9ceb3-102">Details</span></span>

<span data-ttu-id="9ceb3-103">A partir do .NET Framework 4.5, <xref:System.Web.HttpUtility.JavaScriptStringEncode(System.String)?displayProperty=fullName> ignora o caractere E comercial (&amp;).</span><span class="sxs-lookup"><span data-stu-id="9ceb3-103">Starting with the .NET Framework 4.5, <xref:System.Web.HttpUtility.JavaScriptStringEncode(System.String)?displayProperty=fullName> escapes the ampersand (&amp;) character.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="9ceb3-104">Sugestão</span><span class="sxs-lookup"><span data-stu-id="9ceb3-104">Suggestion</span></span>

<span data-ttu-id="9ceb3-105">Se seu aplicativo depende do comportamento anterior desse método, você poderá adicionar uma definição aspnet:JavaScriptDoNotEncodeAmpersand ao [elemento appSettings do ASP.NET](https://docs.microsoft.com/previous-versions/aspnet/hh975440(v=vs.120)) no seu arquivo de configuração.</span><span class="sxs-lookup"><span data-stu-id="9ceb3-105">If your app depends on the previous behavior of this method, you can add an aspnet:JavaScriptDoNotEncodeAmpersand setting to the [ASP.NET appSettings element](https://docs.microsoft.com/previous-versions/aspnet/hh975440(v=vs.120)) in your configuration file.</span></span>

| <span data-ttu-id="9ceb3-106">Name</span><span class="sxs-lookup"><span data-stu-id="9ceb3-106">Name</span></span>    | <span data-ttu-id="9ceb3-107">Valor</span><span class="sxs-lookup"><span data-stu-id="9ceb3-107">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="9ceb3-108">Escopo</span><span class="sxs-lookup"><span data-stu-id="9ceb3-108">Scope</span></span>   |<span data-ttu-id="9ceb3-109">Secundária</span><span class="sxs-lookup"><span data-stu-id="9ceb3-109">Minor</span></span>|
|<span data-ttu-id="9ceb3-110">Versão</span><span class="sxs-lookup"><span data-stu-id="9ceb3-110">Version</span></span>|<span data-ttu-id="9ceb3-111">4.5</span><span class="sxs-lookup"><span data-stu-id="9ceb3-111">4.5</span></span>|
|<span data-ttu-id="9ceb3-112">Type</span><span class="sxs-lookup"><span data-stu-id="9ceb3-112">Type</span></span>|<span data-ttu-id="9ceb3-113">Runtime</span><span class="sxs-lookup"><span data-stu-id="9ceb3-113">Runtime</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="9ceb3-114">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="9ceb3-114">Affected APIs</span></span>

-<xref:System.Web.HttpUtility.JavaScriptStringEncode(System.String)?displayProperty=nameWithType></li><li><xref:System.Web.HttpUtility.JavaScriptStringEncode(System.String,System.Boolean)?displayProperty=nameWithType></li></ul>|
