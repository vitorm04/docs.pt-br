---
ms.openlocfilehash: dfdb62e8dd6db67d4fd12aba93928f4615e3f284
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85614318"
---
### <a name="tabcontrol-selectionchanged-event-and-selectedcontent-property"></a><span data-ttu-id="ace3d-101">Evento TabControl SelectionChanged e propriedade SelectedContent</span><span class="sxs-lookup"><span data-stu-id="ace3d-101">TabControl SelectionChanged event and SelectedContent property</span></span>

#### <a name="details"></a><span data-ttu-id="ace3d-102">Detalhes</span><span class="sxs-lookup"><span data-stu-id="ace3d-102">Details</span></span>

<span data-ttu-id="ace3d-103">A partir do .NET Framework 4.7.1, um <xref:System.Windows.Controls.TabControl> atualiza o valor de sua propriedade <xref:System.Windows.Controls.TabControl.SelectedContent> antes de acionar o evento <xref:System.Windows.Controls.Primitives.Selector.SelectionChanged>, quando sua seleção é alterada. No .NET Framework 4.7 e em versões anteriores, a atualização de SelectedContent acontecia depois do evento.</span><span class="sxs-lookup"><span data-stu-id="ace3d-103">Starting with the .NET Framework 4.7.1, a <xref:System.Windows.Controls.TabControl> updates the value of its <xref:System.Windows.Controls.TabControl.SelectedContent> property before raising the <xref:System.Windows.Controls.Primitives.Selector.SelectionChanged> event, when its selection changes.In the .NET Framework 4.7 and earlier versions, the update to SelectedContent happened after the event.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="ace3d-104">Sugestão</span><span class="sxs-lookup"><span data-stu-id="ace3d-104">Suggestion</span></span>

<span data-ttu-id="ace3d-105">Aplicativos destinados ao .NET Framework 4.7.1 ou posteriores podem recusar essa alteração e usar o comportamento herdado adicionando o seguinte à seção `<runtime>` do arquivo de configuração de aplicativo:</span><span class="sxs-lookup"><span data-stu-id="ace3d-105">Apps that target the .NET Framework 4.7.1 or later can opt out of this change and use legacy behavior by adding the following to the `<runtime>` section of the application configuration file:</span></span>

<pre><code class="lang-xml">&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Windows.Controls.TabControl.SelectionPropertiesCanLagBehindSelectionChangedEvent=true&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;</code></pre>

<span data-ttu-id="ace3d-106">Aplicativos destinados ao .NET Framework 4.7 ou anteriores, mas que são executados no .NET Framework 4.7.1 ou posteriores podem habilitar o novo comportamento adicionando a seguinte linha à seção `<runtime>` do arquivo de configuração de aplicativo:</span><span class="sxs-lookup"><span data-stu-id="ace3d-106">Apps that target the .NET Framework 4.7 or earlier but are running on the .NET Framework 4.7.1 or later can enable the new behavior by adding the following line to the `<runtime>` section of the application .configuration file:</span></span>

<pre><code class="lang-xml">&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Windows.Controls.TabControl.SelectionPropertiesCanLagBehindSelectionChangedEvent=false&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;</code></pre>

| <span data-ttu-id="ace3d-107">Name</span><span class="sxs-lookup"><span data-stu-id="ace3d-107">Name</span></span>    | <span data-ttu-id="ace3d-108">Valor</span><span class="sxs-lookup"><span data-stu-id="ace3d-108">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="ace3d-109">Escopo</span><span class="sxs-lookup"><span data-stu-id="ace3d-109">Scope</span></span>   | <span data-ttu-id="ace3d-110">Secundária</span><span class="sxs-lookup"><span data-stu-id="ace3d-110">Minor</span></span>       |
| <span data-ttu-id="ace3d-111">Versão</span><span class="sxs-lookup"><span data-stu-id="ace3d-111">Version</span></span> | <span data-ttu-id="ace3d-112">4.7.1</span><span class="sxs-lookup"><span data-stu-id="ace3d-112">4.7.1</span></span>       |
| <span data-ttu-id="ace3d-113">Type</span><span class="sxs-lookup"><span data-stu-id="ace3d-113">Type</span></span>    | <span data-ttu-id="ace3d-114">Redirecionando</span><span class="sxs-lookup"><span data-stu-id="ace3d-114">Retargeting</span></span> |

#### <a name="affected-apis"></a><span data-ttu-id="ace3d-115">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="ace3d-115">Affected APIs</span></span>

- <xref:System.Windows.Controls.TabControl.SelectedContent?displayProperty=nameWithType>
- <xref:System.Windows.Controls.Primitives.Selector.SelectionChanged?displayProperty=nameWithType>
