---
ms.openlocfilehash: b648aee35ff44730f545f0fa06f4e0a86615dece
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90606903"
---
### <a name="httputilityjavascriptstringencode-escapes-ampersand"></a><span data-ttu-id="fb06a-101">HttpUtility.JavaScriptStringEncode escapa o E comercial</span><span class="sxs-lookup"><span data-stu-id="fb06a-101">HttpUtility.JavaScriptStringEncode escapes ampersand</span></span>

#### <a name="details"></a><span data-ttu-id="fb06a-102">Detalhes</span><span class="sxs-lookup"><span data-stu-id="fb06a-102">Details</span></span>

<span data-ttu-id="fb06a-103">A partir do .NET Framework 4.5, <xref:System.Web.HttpUtility.JavaScriptStringEncode(System.String)?displayProperty=fullName> ignora o caractere E comercial (&amp;).</span><span class="sxs-lookup"><span data-stu-id="fb06a-103">Starting with the .NET Framework 4.5, <xref:System.Web.HttpUtility.JavaScriptStringEncode(System.String)?displayProperty=fullName> escapes the ampersand (&amp;) character.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="fb06a-104">Sugestão</span><span class="sxs-lookup"><span data-stu-id="fb06a-104">Suggestion</span></span>

<span data-ttu-id="fb06a-105">Se seu aplicativo depende do comportamento anterior desse método, você poderá adicionar uma definição aspnet:JavaScriptDoNotEncodeAmpersand ao [elemento appSettings do ASP.NET](/previous-versions/aspnet/hh975440(v=vs.120)) no seu arquivo de configuração.</span><span class="sxs-lookup"><span data-stu-id="fb06a-105">If your app depends on the previous behavior of this method, you can add an aspnet:JavaScriptDoNotEncodeAmpersand setting to the [ASP.NET appSettings element](/previous-versions/aspnet/hh975440(v=vs.120)) in your configuration file.</span></span>

| <span data-ttu-id="fb06a-106">Name</span><span class="sxs-lookup"><span data-stu-id="fb06a-106">Name</span></span>    | <span data-ttu-id="fb06a-107">Valor</span><span class="sxs-lookup"><span data-stu-id="fb06a-107">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="fb06a-108">Escopo</span><span class="sxs-lookup"><span data-stu-id="fb06a-108">Scope</span></span>   |<span data-ttu-id="fb06a-109">Secundária</span><span class="sxs-lookup"><span data-stu-id="fb06a-109">Minor</span></span>|
|<span data-ttu-id="fb06a-110">Versão</span><span class="sxs-lookup"><span data-stu-id="fb06a-110">Version</span></span>|<span data-ttu-id="fb06a-111">4.5</span><span class="sxs-lookup"><span data-stu-id="fb06a-111">4.5</span></span>|
|<span data-ttu-id="fb06a-112">Tipo</span><span class="sxs-lookup"><span data-stu-id="fb06a-112">Type</span></span>|<span data-ttu-id="fb06a-113">Runtime</span><span class="sxs-lookup"><span data-stu-id="fb06a-113">Runtime</span></span>|

#### <a name="affected-apis"></a><span data-ttu-id="fb06a-114">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="fb06a-114">Affected APIs</span></span>

- <xref:System.Web.HttpUtility.JavaScriptStringEncode(System.String)?displayProperty=nameWithType>
- <xref:System.Web.HttpUtility.JavaScriptStringEncode(System.String,System.Boolean)?displayProperty=nameWithType>

<!--

#### Affected APIs

- `M:System.Web.HttpUtility.JavaScriptStringEncode(System.String)`
- `M:System.Web.HttpUtility.JavaScriptStringEncode(System.String,System.Boolean)`

-->
