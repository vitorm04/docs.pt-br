---
ms.openlocfilehash: 8b0617d8f021a9534289fd7ae8539cd054684862
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59234588"
---
### <a name="wpf-textboxtext-can-be-out-of-sync-with-databinding"></a><span data-ttu-id="6f508-101">O TextBox.Text do WPF pode estar fora de sincronia com a associação de dados</span><span class="sxs-lookup"><span data-stu-id="6f508-101">WPF TextBox.Text can be out-of-sync with databinding</span></span>

|   |   |
|---|---|
|<span data-ttu-id="6f508-102">Detalhes</span><span class="sxs-lookup"><span data-stu-id="6f508-102">Details</span></span>|<span data-ttu-id="6f508-103">Em alguns casos, a propriedade <xref:System.Windows.Controls.TextBox.Text> reflete um valor anterior do valor da propriedade vinculada se a propriedade é modificada durante uma operação de escrita de vinculação de dados.</span><span class="sxs-lookup"><span data-stu-id="6f508-103">In some cases, the <xref:System.Windows.Controls.TextBox.Text> property reflects a previous value of the databound property value if the property is modified during a databinding write operation.</span></span>|
|<span data-ttu-id="6f508-104">Sugestão</span><span class="sxs-lookup"><span data-stu-id="6f508-104">Suggestion</span></span>|<span data-ttu-id="6f508-105">Isso não deve ter nenhum impacto negativo.</span><span class="sxs-lookup"><span data-stu-id="6f508-105">This should have no negative impact.</span></span> <span data-ttu-id="6f508-106">No entanto, é possível restaurar o comportamento anterior ao definir a propriedade <xref:System.Windows.FrameworkCompatibilityPreferences.KeepTextBoxDisplaySynchronizedWithTextProperty> como <code>false</code>.</span><span class="sxs-lookup"><span data-stu-id="6f508-106">However, you can restore the previous behavior by setting the <xref:System.Windows.FrameworkCompatibilityPreferences.KeepTextBoxDisplaySynchronizedWithTextProperty> property to <code>false</code>.</span></span>|
|<span data-ttu-id="6f508-107">Escopo</span><span class="sxs-lookup"><span data-stu-id="6f508-107">Scope</span></span>|<span data-ttu-id="6f508-108">Microsoft Edge</span><span class="sxs-lookup"><span data-stu-id="6f508-108">Edge</span></span>|
|<span data-ttu-id="6f508-109">Versão</span><span class="sxs-lookup"><span data-stu-id="6f508-109">Version</span></span>|<span data-ttu-id="6f508-110">4.5</span><span class="sxs-lookup"><span data-stu-id="6f508-110">4.5</span></span>|
|<span data-ttu-id="6f508-111">Tipo</span><span class="sxs-lookup"><span data-stu-id="6f508-111">Type</span></span>|<span data-ttu-id="6f508-112">Redirecionando</span><span class="sxs-lookup"><span data-stu-id="6f508-112">Retargeting</span></span>|
|<span data-ttu-id="6f508-113">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="6f508-113">Affected APIs</span></span>|<ul><li><xref:System.Windows.Controls.TextBox.Text?displayProperty=nameWithType></li></ul>|
