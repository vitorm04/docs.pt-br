---
ms.openlocfilehash: 55a26f1ab27792cbedf3f31b797f37d3f768d51a
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/05/2020
ms.locfileid: "89497100"
---
### <a name="aspnet-fix-handling-of-inputattributes-and-labelattributes-for-webforms-checkbox-control"></a><span data-ttu-id="6127a-101">ASP.NET Corrigir a manipulação de InputAttributes e LabelAttributes para controle CheckBox de WebForms</span><span class="sxs-lookup"><span data-stu-id="6127a-101">ASP.NET Fix handling of InputAttributes and LabelAttributes for WebForms CheckBox control</span></span>

#### <a name="details"></a><span data-ttu-id="6127a-102">Detalhes</span><span class="sxs-lookup"><span data-stu-id="6127a-102">Details</span></span>

<span data-ttu-id="6127a-103">Para aplicativos que direcionam o .NET Framework 4.7.2 e versões anteriores, <xref:System.Web.UI.WebControls.CheckBox.InputAttributes?displayProperty=nameWithType> e <xref:System.Web.UI.WebControls.CheckBox.LabelAttributes?displayProperty=nameWithType> programaticamente adicionados a um controle <xref:System.Web.UI.WebControls.CheckBox> de WebForms são perdidos após o postback.</span><span class="sxs-lookup"><span data-stu-id="6127a-103">For applications that target .NET Framework 4.7.2 and earlier versions, <xref:System.Web.UI.WebControls.CheckBox.InputAttributes?displayProperty=nameWithType> and <xref:System.Web.UI.WebControls.CheckBox.LabelAttributes?displayProperty=nameWithType> that are programmatically added to a WebForms <xref:System.Web.UI.WebControls.CheckBox> control are lost after postback.</span></span> <span data-ttu-id="6127a-104">Para aplicativos que direcionam o .NET Framework 4.8 ou versões posteriores, eles são preservados após o postback.</span><span class="sxs-lookup"><span data-stu-id="6127a-104">For applications that target .NET Framework 4.8 or later versions, they are preserved after postback.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="6127a-105">Sugestão</span><span class="sxs-lookup"><span data-stu-id="6127a-105">Suggestion</span></span>

<span data-ttu-id="6127a-106">Para o comportamento correto para restaurar atributos em postback, defina <code>targetFrameworkVersion</code> como 4.8 ou superior.</span><span class="sxs-lookup"><span data-stu-id="6127a-106">For the correct behavior for restoring attributes on postback, set the <code>targetFrameworkVersion</code> to 4.8 or higher.</span></span> <span data-ttu-id="6127a-107">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="6127a-107">For example:</span></span><pre><code class="lang-xml">&lt;configuration&gt;&#13;&#10;&lt;system.web&gt;&#13;&#10;&lt;httpRuntime targetFramework=&quot;4.8&quot;/&gt;&#13;&#10;&lt;/system.web&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre><span data-ttu-id="6127a-108">Defini-la como mais baixa ou não definir preserva o comportamento antigo incorreto.</span><span class="sxs-lookup"><span data-stu-id="6127a-108">Setting it lower, or not at all, preserves the old incorrect behavior.</span></span>

| <span data-ttu-id="6127a-109">Nome</span><span class="sxs-lookup"><span data-stu-id="6127a-109">Name</span></span>    | <span data-ttu-id="6127a-110">Valor</span><span class="sxs-lookup"><span data-stu-id="6127a-110">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="6127a-111">Escopo</span><span class="sxs-lookup"><span data-stu-id="6127a-111">Scope</span></span>   |<span data-ttu-id="6127a-112">Desconhecido</span><span class="sxs-lookup"><span data-stu-id="6127a-112">Unknown</span></span>|
|<span data-ttu-id="6127a-113">Versão</span><span class="sxs-lookup"><span data-stu-id="6127a-113">Version</span></span>|<span data-ttu-id="6127a-114">4.8</span><span class="sxs-lookup"><span data-stu-id="6127a-114">4.8</span></span>|
|<span data-ttu-id="6127a-115">Tipo</span><span class="sxs-lookup"><span data-stu-id="6127a-115">Type</span></span>|<span data-ttu-id="6127a-116">Runtime</span><span class="sxs-lookup"><span data-stu-id="6127a-116">Runtime</span></span>|

#### <a name="affected-apis"></a><span data-ttu-id="6127a-117">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="6127a-117">Affected APIs</span></span>

- <xref:System.Web.UI.WebControls.CheckBox?displayProperty=nameWithType>

<!--

#### Affected APIs

- `T:System.Web.UI.WebControls.CheckBox`

-->
