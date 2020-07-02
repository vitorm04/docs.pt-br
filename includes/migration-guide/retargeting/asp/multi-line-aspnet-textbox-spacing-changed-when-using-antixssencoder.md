---
ms.openlocfilehash: 150b98255b3075a8fe8cad60ce234206b788a5f5
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85617105"
---
### <a name="multi-line-aspnet-textbox-spacing-changed-when-using-antixssencoder"></a><span data-ttu-id="983a2-101">O espaçamento de TextBox do ASP.Net de várias linhas é alterado quando se usa AntiXSSEncoder</span><span class="sxs-lookup"><span data-stu-id="983a2-101">Multi-line ASP.Net TextBox spacing changed when using AntiXSSEncoder</span></span>

#### <a name="details"></a><span data-ttu-id="983a2-102">Detalhes</span><span class="sxs-lookup"><span data-stu-id="983a2-102">Details</span></span>

<span data-ttu-id="983a2-103">No .NET Framework 4.0, linhas extras eram inseridas entre as linhas de uma caixa de texto de várias linhas no postback, se usando o <xref:System.Web.Security.AntiXss.AntiXssEncoder?displayProperty=fullName>.</span><span class="sxs-lookup"><span data-stu-id="983a2-103">In .NET Framework 4.0, extra lines were inserted between lines of a multi-line text box on postback, if using the <xref:System.Web.Security.AntiXss.AntiXssEncoder?displayProperty=fullName>.</span></span> <span data-ttu-id="983a2-104">No .NET Framework 4.5, essas quebras de linhas extras não são incluídas, mas somente se o aplicativo Web for direcionado ao .NET 4.5</span><span class="sxs-lookup"><span data-stu-id="983a2-104">In .NET Framework 4.5, those extra line breaks are not included, but only if the web app is targeting .NET Framework 4.5</span></span>

#### <a name="suggestion"></a><span data-ttu-id="983a2-105">Sugestão</span><span class="sxs-lookup"><span data-stu-id="983a2-105">Suggestion</span></span>

<span data-ttu-id="983a2-106">Lembre-se de que os aplicativos web 4.0 redirecionados para o .NET Framework 4.5 podem ter caixas de texto multilinha melhoradas para não inserir quebras de linha extras.</span><span class="sxs-lookup"><span data-stu-id="983a2-106">Be aware that 4.0 web apps retargeted to .NET Framework 4.5 may have multi-line text boxes improved to no longer insert extra line breaks.</span></span> <span data-ttu-id="983a2-107">Se isso não for desejável, o aplicativo poderá ter o comportamento antigo durante a execução no .NET Framework 4.5 visando o .NET Framework 4.0.</span><span class="sxs-lookup"><span data-stu-id="983a2-107">If this is not desirable, the app  can have the old behavior when running on .NET Framework 4.5 by targeting the .NET Framework 4.0.</span></span>

| <span data-ttu-id="983a2-108">Name</span><span class="sxs-lookup"><span data-stu-id="983a2-108">Name</span></span>    | <span data-ttu-id="983a2-109">Valor</span><span class="sxs-lookup"><span data-stu-id="983a2-109">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="983a2-110">Escopo</span><span class="sxs-lookup"><span data-stu-id="983a2-110">Scope</span></span>   | <span data-ttu-id="983a2-111">Secundária</span><span class="sxs-lookup"><span data-stu-id="983a2-111">Minor</span></span>       |
| <span data-ttu-id="983a2-112">Versão</span><span class="sxs-lookup"><span data-stu-id="983a2-112">Version</span></span> | <span data-ttu-id="983a2-113">4.5</span><span class="sxs-lookup"><span data-stu-id="983a2-113">4.5</span></span>         |
| <span data-ttu-id="983a2-114">Type</span><span class="sxs-lookup"><span data-stu-id="983a2-114">Type</span></span>    | <span data-ttu-id="983a2-115">Redirecionando</span><span class="sxs-lookup"><span data-stu-id="983a2-115">Retargeting</span></span> |
