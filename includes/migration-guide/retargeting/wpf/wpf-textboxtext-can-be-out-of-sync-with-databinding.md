---
ms.openlocfilehash: d0de1a262d57c67dd4dfb258d5ac013af5d8783d
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85617112"
---
### <a name="wpf-textboxtext-can-be-out-of-sync-with-databinding"></a><span data-ttu-id="2c2c8-101">O TextBox.Text do WPF pode estar fora de sincronia com a associação de dados</span><span class="sxs-lookup"><span data-stu-id="2c2c8-101">WPF TextBox.Text can be out-of-sync with databinding</span></span>

#### <a name="details"></a><span data-ttu-id="2c2c8-102">Detalhes</span><span class="sxs-lookup"><span data-stu-id="2c2c8-102">Details</span></span>

<span data-ttu-id="2c2c8-103">Em alguns casos, a propriedade <xref:System.Windows.Controls.TextBox.Text> reflete um valor anterior do valor da propriedade vinculada se a propriedade é modificada durante uma operação de escrita de vinculação de dados.</span><span class="sxs-lookup"><span data-stu-id="2c2c8-103">In some cases, the <xref:System.Windows.Controls.TextBox.Text> property reflects a previous value of the databound property value if the property is modified during a databinding write operation.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="2c2c8-104">Sugestão</span><span class="sxs-lookup"><span data-stu-id="2c2c8-104">Suggestion</span></span>

<span data-ttu-id="2c2c8-105">Isso não deve ter nenhum impacto negativo.</span><span class="sxs-lookup"><span data-stu-id="2c2c8-105">This should have no negative impact.</span></span> <span data-ttu-id="2c2c8-106">No entanto, é possível restaurar o comportamento anterior ao definir a propriedade <xref:System.Windows.FrameworkCompatibilityPreferences.KeepTextBoxDisplaySynchronizedWithTextProperty> como `false`.</span><span class="sxs-lookup"><span data-stu-id="2c2c8-106">However, you can restore the previous behavior by setting the <xref:System.Windows.FrameworkCompatibilityPreferences.KeepTextBoxDisplaySynchronizedWithTextProperty> property to `false`.</span></span>

| <span data-ttu-id="2c2c8-107">Name</span><span class="sxs-lookup"><span data-stu-id="2c2c8-107">Name</span></span>    | <span data-ttu-id="2c2c8-108">Valor</span><span class="sxs-lookup"><span data-stu-id="2c2c8-108">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="2c2c8-109">Escopo</span><span class="sxs-lookup"><span data-stu-id="2c2c8-109">Scope</span></span>   | <span data-ttu-id="2c2c8-110">Microsoft Edge</span><span class="sxs-lookup"><span data-stu-id="2c2c8-110">Edge</span></span>        |
| <span data-ttu-id="2c2c8-111">Versão</span><span class="sxs-lookup"><span data-stu-id="2c2c8-111">Version</span></span> | <span data-ttu-id="2c2c8-112">4.5</span><span class="sxs-lookup"><span data-stu-id="2c2c8-112">4.5</span></span>         |
|<span data-ttu-id="2c2c8-113">Type</span><span class="sxs-lookup"><span data-stu-id="2c2c8-113">Type</span></span>|<span data-ttu-id="2c2c8-114">Redirecionando</span><span class="sxs-lookup"><span data-stu-id="2c2c8-114">Retargeting</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="2c2c8-115">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="2c2c8-115">Affected APIs</span></span>

- <xref:System.Windows.Controls.TextBox.Text?displayProperty=nameWithType>
