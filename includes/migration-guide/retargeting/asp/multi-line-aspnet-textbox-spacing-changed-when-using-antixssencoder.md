---
ms.openlocfilehash: e2bca42daebd25667ab2f312d5e59089b986503c
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59234589"
---
### <a name="multi-line-aspnet-textbox-spacing-changed-when-using-antixssencoder"></a><span data-ttu-id="d3de5-101">O espaçamento de TextBox do ASP.Net de várias linhas é alterado quando se usa AntiXSSEncoder</span><span class="sxs-lookup"><span data-stu-id="d3de5-101">Multi-line ASP.Net TextBox spacing changed when using AntiXSSEncoder</span></span>

|   |   |
|---|---|
|<span data-ttu-id="d3de5-102">Detalhes</span><span class="sxs-lookup"><span data-stu-id="d3de5-102">Details</span></span>|<span data-ttu-id="d3de5-103">No .NET Framework 4.0, linhas extras eram inseridas entre as linhas de uma caixa de texto de várias linhas no postback, se usando o <xref:System.Web.Security.AntiXss.AntiXssEncoder?displayProperty=name>.</span><span class="sxs-lookup"><span data-stu-id="d3de5-103">In .NET Framework 4.0, extra lines were inserted between lines of a multi-line text box on postback, if using the <xref:System.Web.Security.AntiXss.AntiXssEncoder?displayProperty=name>.</span></span> <span data-ttu-id="d3de5-104">No .NET Framework 4.5, essas quebras de linhas extras não são incluídas, mas somente se o aplicativo Web for direcionado ao .NET 4.5</span><span class="sxs-lookup"><span data-stu-id="d3de5-104">In .NET Framework 4.5, those extra line breaks are not included, but only if the web app is targeting .NET Framework 4.5</span></span>|
|<span data-ttu-id="d3de5-105">Sugestão</span><span class="sxs-lookup"><span data-stu-id="d3de5-105">Suggestion</span></span>|<span data-ttu-id="d3de5-106">Lembre-se de que os aplicativos web 4.0 redirecionados para o .NET Framework 4.5 podem ter caixas de texto multilinha melhoradas para não inserir quebras de linha extras.</span><span class="sxs-lookup"><span data-stu-id="d3de5-106">Be aware that 4.0 web apps retargeted to .NET Framework 4.5 may have multi-line text boxes improved to no longer insert extra line breaks.</span></span> <span data-ttu-id="d3de5-107">Se isso não for desejável, o aplicativo poderá ter o comportamento antigo durante a execução no .NET Framework 4.5 visando o .NET Framework 4.0.</span><span class="sxs-lookup"><span data-stu-id="d3de5-107">If this is not desirable, the app  can have the old behavior when running on .NET Framework 4.5 by targeting the .NET Framework 4.0.</span></span>|
|<span data-ttu-id="d3de5-108">Escopo</span><span class="sxs-lookup"><span data-stu-id="d3de5-108">Scope</span></span>|<span data-ttu-id="d3de5-109">Secundário</span><span class="sxs-lookup"><span data-stu-id="d3de5-109">Minor</span></span>|
|<span data-ttu-id="d3de5-110">Versão</span><span class="sxs-lookup"><span data-stu-id="d3de5-110">Version</span></span>|<span data-ttu-id="d3de5-111">4.5</span><span class="sxs-lookup"><span data-stu-id="d3de5-111">4.5</span></span>|
|<span data-ttu-id="d3de5-112">Tipo</span><span class="sxs-lookup"><span data-stu-id="d3de5-112">Type</span></span>|<span data-ttu-id="d3de5-113">Redirecionando</span><span class="sxs-lookup"><span data-stu-id="d3de5-113">Retargeting</span></span>|
