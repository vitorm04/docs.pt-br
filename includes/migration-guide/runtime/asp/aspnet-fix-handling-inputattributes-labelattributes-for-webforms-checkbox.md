---
ms.openlocfilehash: ae557ce57557d027dba35b7da213c08aee85f2c7
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85621909"
---
### <a name="aspnet-fix-handling-of-inputattributes-and-labelattributes-for-webforms-checkbox-control"></a><span data-ttu-id="bd8e7-101">ASP.NET Corrigir a manipulação de InputAttributes e LabelAttributes para controle CheckBox de WebForms</span><span class="sxs-lookup"><span data-stu-id="bd8e7-101">ASP.NET Fix handling of InputAttributes and LabelAttributes for WebForms CheckBox control</span></span>

#### <a name="details"></a><span data-ttu-id="bd8e7-102">Detalhes</span><span class="sxs-lookup"><span data-stu-id="bd8e7-102">Details</span></span>

<span data-ttu-id="bd8e7-103">Para aplicativos que direcionam o .NET Framework 4.7.2 e versões anteriores, <xref:System.Web.UI.WebControls.CheckBox.InputAttributes?displayProperty=nameWithType> e <xref:System.Web.UI.WebControls.CheckBox.LabelAttributes?displayProperty=nameWithType> programaticamente adicionados a um controle <xref:System.Web.UI.WebControls.CheckBox> de WebForms são perdidos após o postback.</span><span class="sxs-lookup"><span data-stu-id="bd8e7-103">For applications that target .NET Framework 4.7.2 and earlier versions, <xref:System.Web.UI.WebControls.CheckBox.InputAttributes?displayProperty=nameWithType> and <xref:System.Web.UI.WebControls.CheckBox.LabelAttributes?displayProperty=nameWithType> that are programmatically added to a WebForms <xref:System.Web.UI.WebControls.CheckBox> control are lost after postback.</span></span> <span data-ttu-id="bd8e7-104">Para aplicativos que direcionam o .NET Framework 4.8 ou versões posteriores, eles são preservados após o postback.</span><span class="sxs-lookup"><span data-stu-id="bd8e7-104">For applications that target .NET Framework 4.8 or later versions, they are preserved after postback.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="bd8e7-105">Sugestão</span><span class="sxs-lookup"><span data-stu-id="bd8e7-105">Suggestion</span></span>

<span data-ttu-id="bd8e7-106">Para o comportamento correto para restaurar atributos em postback, defina <code>targetFrameworkVersion</code> como 4.8 ou superior.</span><span class="sxs-lookup"><span data-stu-id="bd8e7-106">For the correct behavior for restoring attributes on postback, set the <code>targetFrameworkVersion</code> to 4.8 or higher.</span></span> <span data-ttu-id="bd8e7-107">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="bd8e7-107">For example:</span></span><pre><code class="lang-xml">&lt;configuration&gt;&#13;&#10;&lt;system.web&gt;&#13;&#10;&lt;httpRuntime targetFramework=&quot;4.8&quot;/&gt;&#13;&#10;&lt;/system.web&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre><span data-ttu-id="bd8e7-108">Defini-la como mais baixa ou não definir preserva o comportamento antigo incorreto.</span><span class="sxs-lookup"><span data-stu-id="bd8e7-108">Setting it lower, or not at all, preserves the old incorrect behavior.</span></span>

| <span data-ttu-id="bd8e7-109">Name</span><span class="sxs-lookup"><span data-stu-id="bd8e7-109">Name</span></span>    | <span data-ttu-id="bd8e7-110">Valor</span><span class="sxs-lookup"><span data-stu-id="bd8e7-110">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="bd8e7-111">Escopo</span><span class="sxs-lookup"><span data-stu-id="bd8e7-111">Scope</span></span>   |<span data-ttu-id="bd8e7-112">Unknown (desconhecido)</span><span class="sxs-lookup"><span data-stu-id="bd8e7-112">Unknown</span></span>|
|<span data-ttu-id="bd8e7-113">Versão</span><span class="sxs-lookup"><span data-stu-id="bd8e7-113">Version</span></span>|<span data-ttu-id="bd8e7-114">4.8</span><span class="sxs-lookup"><span data-stu-id="bd8e7-114">4.8</span></span>|
|<span data-ttu-id="bd8e7-115">Type</span><span class="sxs-lookup"><span data-stu-id="bd8e7-115">Type</span></span>|<span data-ttu-id="bd8e7-116">Runtime</span><span class="sxs-lookup"><span data-stu-id="bd8e7-116">Runtime</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="bd8e7-117">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="bd8e7-117">Affected APIs</span></span>

-<xref:System.Web.UI.WebControls.CheckBox?displayProperty=nameWithType></li></ul>|
