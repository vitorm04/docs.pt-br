---
ms.openlocfilehash: e600b8249096eecb13f63ea00343a771a8c12b60
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59803189"
---
### <a name="htmltextwriter-does-not-render-br-element-correctly"></a><span data-ttu-id="3b3d1-101">HtmlTextWriter não renderiza o elemento `<br/>` corretamente</span><span class="sxs-lookup"><span data-stu-id="3b3d1-101">HtmlTextWriter does not render `<br/>` element correctly</span></span>

|   |   |
|---|---|
|<span data-ttu-id="3b3d1-102">Detalhes</span><span class="sxs-lookup"><span data-stu-id="3b3d1-102">Details</span></span>|<span data-ttu-id="3b3d1-103">A partir do .NET Framework 4.6, chamar <xref:System.Web.UI.HtmlTextWriter.RenderBeginTag(System.String)> e <xref:System.Web.UI.HtmlTextWriter.RenderEndTag> com um elemento <code>&lt;BR /&gt;</code> vai inserir corretamente apenas um <code>&lt;BR /&gt;</code> (em vez de dois)</span><span class="sxs-lookup"><span data-stu-id="3b3d1-103">Beginning in the .NET Framework 4.6, calling <xref:System.Web.UI.HtmlTextWriter.RenderBeginTag(System.String)> and <xref:System.Web.UI.HtmlTextWriter.RenderEndTag> with a <code>&lt;BR /&gt;</code> element will correctly insert only one <code>&lt;BR /&gt;</code> (instead of two)</span></span>|
|<span data-ttu-id="3b3d1-104">Sugestão</span><span class="sxs-lookup"><span data-stu-id="3b3d1-104">Suggestion</span></span>|<span data-ttu-id="3b3d1-105">Se um aplicativo depender da marca <code>&lt;BR /&gt;</code> extra, <xref:System.Web.UI.HtmlTextWriter.RenderBeginTag(System.String)> deverá ser chamado uma segunda vez.</span><span class="sxs-lookup"><span data-stu-id="3b3d1-105">If an app depended on the extra <code>&lt;BR /&gt;</code> tag, <xref:System.Web.UI.HtmlTextWriter.RenderBeginTag(System.String)> should be called a second time.</span></span> <span data-ttu-id="3b3d1-106">Observe que essa alteração de comportamento afeta apenas aplicativos destinados ao .NET Framework 4.6 ou versões posteriores, de modo que outra opção é destinar a uma versão anterior do .NET Framework a fim de obter o comportamento antigo.</span><span class="sxs-lookup"><span data-stu-id="3b3d1-106">Note that this behavior change only affects apps that target the .NET Framework 4.6 or later, so another option is to target a previous version of the .NET Framework in order to get the old behavior.</span></span>|
|<span data-ttu-id="3b3d1-107">Escopo</span><span class="sxs-lookup"><span data-stu-id="3b3d1-107">Scope</span></span>|<span data-ttu-id="3b3d1-108">Microsoft Edge</span><span class="sxs-lookup"><span data-stu-id="3b3d1-108">Edge</span></span>|
|<span data-ttu-id="3b3d1-109">Versão</span><span class="sxs-lookup"><span data-stu-id="3b3d1-109">Version</span></span>|<span data-ttu-id="3b3d1-110">4.6</span><span class="sxs-lookup"><span data-stu-id="3b3d1-110">4.6</span></span>|
|<span data-ttu-id="3b3d1-111">Tipo</span><span class="sxs-lookup"><span data-stu-id="3b3d1-111">Type</span></span>|<span data-ttu-id="3b3d1-112">Redirecionando</span><span class="sxs-lookup"><span data-stu-id="3b3d1-112">Retargeting</span></span>|
|<span data-ttu-id="3b3d1-113">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="3b3d1-113">Affected APIs</span></span>|<ul><li><xref:System.Web.UI.HtmlTextWriter.RenderBeginTag(System.String)?displayProperty=nameWithType></li><li><xref:System.Web.UI.HtmlTextWriter.RenderBeginTag(System.Web.UI.HtmlTextWriterTag)?displayProperty=nameWithType></li></ul>|
