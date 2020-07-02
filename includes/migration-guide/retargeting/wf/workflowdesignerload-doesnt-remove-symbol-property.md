---
ms.openlocfilehash: ddc98448101c65003001ad05e67f29d75d99ad44
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85616016"
---
### <a name="workflowdesignerload-doesnt-remove-symbol-property"></a><span data-ttu-id="0558e-101">WorkflowDesigner.Load não remove a propriedade de símbolo</span><span class="sxs-lookup"><span data-stu-id="0558e-101">WorkflowDesigner.Load doesn't remove symbol property</span></span>

#### <a name="details"></a><span data-ttu-id="0558e-102">Detalhes</span><span class="sxs-lookup"><span data-stu-id="0558e-102">Details</span></span>

<span data-ttu-id="0558e-103">Ao destinar para o .NET Framework 4.5 no designer de fluxo de trabalho e carregar um fluxo de trabalho 3.5 hospedado novamente com o método <xref:System.Activities.Presentation.WorkflowDesigner.Load>, uma <xref:System.Xaml.XamlDuplicateMemberException?displayProperty=fullName> é gerada durante o salvamento do fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="0558e-103">When targeting the .NET Framework 4.5 in the workflow designer, and loading a re-hosted 3.5 workflow with the <xref:System.Activities.Presentation.WorkflowDesigner.Load> method, a <xref:System.Xaml.XamlDuplicateMemberException?displayProperty=fullName> is thrown while saving the workflow.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="0558e-104">Sugestão</span><span class="sxs-lookup"><span data-stu-id="0558e-104">Suggestion</span></span>

<span data-ttu-id="0558e-105">Esse bug se manifesta somente no direcionamento do .NET Framework 4.5 no designer de fluxo de trabalho, de modo que a solução alternativa é definir o `WorkflowDesigner.Context.Services.GetService&lt;DesignerConfigurationService&gt;().TargetFrameworkName` para o .NET Framework 4.0. O problema também pode ser evitado usando o método <xref:System.Activities.Presentation.WorkflowDesigner.Load(System.String)> para carregar o fluxo de trabalho, em vez de <xref:System.Activities.Presentation.WorkflowDesigner.Load>.</span><span class="sxs-lookup"><span data-stu-id="0558e-105">This bug only manifests when targeting .NET Framework 4.5 in the workflow designer, so it can be worked around by setting the `WorkflowDesigner.Context.Services.GetService&lt;DesignerConfigurationService&gt;().TargetFrameworkName` to the 4.0 .NET Framework.Alternatively, the issue may be avoided by using the <xref:System.Activities.Presentation.WorkflowDesigner.Load(System.String)> method to load the workflow, instead of <xref:System.Activities.Presentation.WorkflowDesigner.Load>.</span></span>

| <span data-ttu-id="0558e-106">Name</span><span class="sxs-lookup"><span data-stu-id="0558e-106">Name</span></span>    | <span data-ttu-id="0558e-107">Valor</span><span class="sxs-lookup"><span data-stu-id="0558e-107">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="0558e-108">Escopo</span><span class="sxs-lookup"><span data-stu-id="0558e-108">Scope</span></span>   | <span data-ttu-id="0558e-109">Principal</span><span class="sxs-lookup"><span data-stu-id="0558e-109">Major</span></span>       |
| <span data-ttu-id="0558e-110">Versão</span><span class="sxs-lookup"><span data-stu-id="0558e-110">Version</span></span> | <span data-ttu-id="0558e-111">4.5</span><span class="sxs-lookup"><span data-stu-id="0558e-111">4.5</span></span>         |
| <span data-ttu-id="0558e-112">Type</span><span class="sxs-lookup"><span data-stu-id="0558e-112">Type</span></span>    | <span data-ttu-id="0558e-113">Redirecionando</span><span class="sxs-lookup"><span data-stu-id="0558e-113">Retargeting</span></span> |

#### <a name="affected-apis"></a><span data-ttu-id="0558e-114">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="0558e-114">Affected APIs</span></span>

- <xref:System.Activities.Presentation.WorkflowDesigner.Load?displayProperty=nameWithType>
