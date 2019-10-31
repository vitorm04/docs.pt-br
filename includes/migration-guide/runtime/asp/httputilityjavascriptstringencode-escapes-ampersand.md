---
ms.openlocfilehash: 0056baa1e5f0cdc5bfcf8b0e83c9490ec5722926
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59235101"
---
### <a name="httputilityjavascriptstringencode-escapes-ampersand"></a><span data-ttu-id="180b7-101">HttpUtility.JavaScriptStringEncode escapa o E comercial</span><span class="sxs-lookup"><span data-stu-id="180b7-101">HttpUtility.JavaScriptStringEncode escapes ampersand</span></span>

|   |   |
|---|---|
|<span data-ttu-id="180b7-102">Detalhes</span><span class="sxs-lookup"><span data-stu-id="180b7-102">Details</span></span>|<span data-ttu-id="180b7-103">A partir do .NET Framework 4.5, <xref:System.Web.HttpUtility.JavaScriptStringEncode(System.String)?displayProperty=name> ignora o caractere E comercial (&amp;).</span><span class="sxs-lookup"><span data-stu-id="180b7-103">Starting with the .NET Framework 4.5, <xref:System.Web.HttpUtility.JavaScriptStringEncode(System.String)?displayProperty=name> escapes the ampersand (&amp;) character.</span></span>|
|<span data-ttu-id="180b7-104">Sugestão</span><span class="sxs-lookup"><span data-stu-id="180b7-104">Suggestion</span></span>|<span data-ttu-id="180b7-105">Se seu aplicativo depende do comportamento anterior desse método, você poderá adicionar uma definição aspnet:JavaScriptDoNotEncodeAmpersand ao [elemento appSettings do ASP.NET](https://docs.microsoft.com/previous-versions/aspnet/hh975440(v=vs.120)) no seu arquivo de configuração.</span><span class="sxs-lookup"><span data-stu-id="180b7-105">If your app depends on the previous behavior of this method, you can add an aspnet:JavaScriptDoNotEncodeAmpersand setting to the [ASP.NET appSettings element](https://docs.microsoft.com/previous-versions/aspnet/hh975440(v=vs.120)) in your configuration file.</span></span>|
|<span data-ttu-id="180b7-106">Escopo</span><span class="sxs-lookup"><span data-stu-id="180b7-106">Scope</span></span>|<span data-ttu-id="180b7-107">Secundário</span><span class="sxs-lookup"><span data-stu-id="180b7-107">Minor</span></span>|
|<span data-ttu-id="180b7-108">Versão</span><span class="sxs-lookup"><span data-stu-id="180b7-108">Version</span></span>|<span data-ttu-id="180b7-109">4.5</span><span class="sxs-lookup"><span data-stu-id="180b7-109">4.5</span></span>|
|<span data-ttu-id="180b7-110">Tipo</span><span class="sxs-lookup"><span data-stu-id="180b7-110">Type</span></span>|<span data-ttu-id="180b7-111">Tempo de execução</span><span class="sxs-lookup"><span data-stu-id="180b7-111">Runtime</span></span>|
|<span data-ttu-id="180b7-112">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="180b7-112">Affected APIs</span></span>|<ul><li><xref:System.Web.HttpUtility.JavaScriptStringEncode(System.String)?displayProperty=nameWithType></li><li><xref:System.Web.HttpUtility.JavaScriptStringEncode(System.String,System.Boolean)?displayProperty=nameWithType></li></ul>|
