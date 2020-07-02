---
ms.openlocfilehash: 8f03e5166e7f1f598e9bba7fb8c550809f287b82
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85615588"
---
### <a name="htmltextwriter-does-not-render-br-element-correctly"></a><span data-ttu-id="01f0e-101">HtmlTextWriter não renderiza o elemento `<br/>` corretamente</span><span class="sxs-lookup"><span data-stu-id="01f0e-101">HtmlTextWriter does not render `<br/>` element correctly</span></span>

#### <a name="details"></a><span data-ttu-id="01f0e-102">Detalhes</span><span class="sxs-lookup"><span data-stu-id="01f0e-102">Details</span></span>

<span data-ttu-id="01f0e-103">A partir do .NET Framework 4.6, chamar <xref:System.Web.UI.HtmlTextWriter.RenderBeginTag(System.String)> e <xref:System.Web.UI.HtmlTextWriter.RenderEndTag> com um elemento `<BR />` vai inserir corretamente apenas um `<BR />` (em vez de dois)</span><span class="sxs-lookup"><span data-stu-id="01f0e-103">Beginning in the .NET Framework 4.6, calling <xref:System.Web.UI.HtmlTextWriter.RenderBeginTag(System.String)> and <xref:System.Web.UI.HtmlTextWriter.RenderEndTag> with a `<BR />` element will correctly insert only one `<BR />` (instead of two)</span></span>

#### <a name="suggestion"></a><span data-ttu-id="01f0e-104">Sugestão</span><span class="sxs-lookup"><span data-stu-id="01f0e-104">Suggestion</span></span>

<span data-ttu-id="01f0e-105">Se um aplicativo depender da marca `<BR />` extra, <xref:System.Web.UI.HtmlTextWriter.RenderBeginTag(System.String)> deverá ser chamado uma segunda vez.</span><span class="sxs-lookup"><span data-stu-id="01f0e-105">If an app depended on the extra `<BR />` tag, <xref:System.Web.UI.HtmlTextWriter.RenderBeginTag(System.String)> should be called a second time.</span></span> <span data-ttu-id="01f0e-106">Observe que essa alteração de comportamento afeta apenas aplicativos destinados ao .NET Framework 4.6 ou versões posteriores, de modo que outra opção é destinar a uma versão anterior do .NET Framework a fim de obter o comportamento antigo.</span><span class="sxs-lookup"><span data-stu-id="01f0e-106">Note that this behavior change only affects apps that target the .NET Framework 4.6 or later, so another option is to target a previous version of the .NET Framework in order to get the old behavior.</span></span>

| <span data-ttu-id="01f0e-107">Name</span><span class="sxs-lookup"><span data-stu-id="01f0e-107">Name</span></span>    | <span data-ttu-id="01f0e-108">Valor</span><span class="sxs-lookup"><span data-stu-id="01f0e-108">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="01f0e-109">Escopo</span><span class="sxs-lookup"><span data-stu-id="01f0e-109">Scope</span></span>   | <span data-ttu-id="01f0e-110">Microsoft Edge</span><span class="sxs-lookup"><span data-stu-id="01f0e-110">Edge</span></span>        |
| <span data-ttu-id="01f0e-111">Versão</span><span class="sxs-lookup"><span data-stu-id="01f0e-111">Version</span></span> | <span data-ttu-id="01f0e-112">4.6</span><span class="sxs-lookup"><span data-stu-id="01f0e-112">4.6</span></span>         |
| <span data-ttu-id="01f0e-113">Type</span><span class="sxs-lookup"><span data-stu-id="01f0e-113">Type</span></span>    | <span data-ttu-id="01f0e-114">Redirecionando</span><span class="sxs-lookup"><span data-stu-id="01f0e-114">Retargeting</span></span> |

#### <a name="affected-apis"></a><span data-ttu-id="01f0e-115">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="01f0e-115">Affected APIs</span></span>

- <xref:System.Web.UI.HtmlTextWriter.RenderBeginTag(System.String)?displayProperty=nameWithType>
- <xref:System.Web.UI.HtmlTextWriter.RenderBeginTag(System.Web.UI.HtmlTextWriterTag)?displayProperty=nameWithType>
