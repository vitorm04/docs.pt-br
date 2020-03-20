---
ms.openlocfilehash: 19c613bf48479cb1e52531a4d6594db8ad89b8f3
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/15/2020
ms.locfileid: "67804678"
---
### <a name="workflowdesignerload-doesnt-remove-symbol-property"></a><span data-ttu-id="7fd66-101">WorkflowDesigner.Load não remove a propriedade de símbolo</span><span class="sxs-lookup"><span data-stu-id="7fd66-101">WorkflowDesigner.Load doesn't remove symbol property</span></span>

|   |   |
|---|---|
|<span data-ttu-id="7fd66-102">Detalhes</span><span class="sxs-lookup"><span data-stu-id="7fd66-102">Details</span></span>|<span data-ttu-id="7fd66-103">Ao destinar para o .NET Framework 4.5 no designer de fluxo de trabalho e carregar um fluxo de trabalho 3.5 hospedado novamente com o método <xref:System.Activities.Presentation.WorkflowDesigner.Load>, uma <xref:System.Xaml.XamlDuplicateMemberException?displayProperty=name> é gerada durante o salvamento do fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="7fd66-103">When targeting the .NET Framework 4.5 in the workflow designer, and loading a re-hosted 3.5 workflow with the <xref:System.Activities.Presentation.WorkflowDesigner.Load> method, a <xref:System.Xaml.XamlDuplicateMemberException?displayProperty=name> is thrown while saving the workflow.</span></span>|
|<span data-ttu-id="7fd66-104">Sugestão</span><span class="sxs-lookup"><span data-stu-id="7fd66-104">Suggestion</span></span>|<span data-ttu-id="7fd66-105">Esse bug se manifesta somente no direcionamento do .NET Framework 4.5 no designer de fluxo de trabalho, de modo que a solução alternativa é definir o <code>WorkflowDesigner.Context.Services.GetService&lt;DesignerConfigurationService&gt;().TargetFrameworkName</code> para o .NET Framework 4.0. O problema também pode ser evitado usando o método <xref:System.Activities.Presentation.WorkflowDesigner.Load(System.String)> para carregar o fluxo de trabalho, em vez de <xref:System.Activities.Presentation.WorkflowDesigner.Load>.</span><span class="sxs-lookup"><span data-stu-id="7fd66-105">This bug only manifests when targeting .NET Framework 4.5 in the workflow designer, so it can be worked around by setting the <code>WorkflowDesigner.Context.Services.GetService&lt;DesignerConfigurationService&gt;().TargetFrameworkName</code> to the 4.0 .NET Framework.Alternatively, the issue may be avoided by using the <xref:System.Activities.Presentation.WorkflowDesigner.Load(System.String)> method to load the workflow, instead of <xref:System.Activities.Presentation.WorkflowDesigner.Load>.</span></span>|
|<span data-ttu-id="7fd66-106">Escopo</span><span class="sxs-lookup"><span data-stu-id="7fd66-106">Scope</span></span>|<span data-ttu-id="7fd66-107">Principal</span><span class="sxs-lookup"><span data-stu-id="7fd66-107">Major</span></span>|
|<span data-ttu-id="7fd66-108">Versão</span><span class="sxs-lookup"><span data-stu-id="7fd66-108">Version</span></span>|<span data-ttu-id="7fd66-109">4.5</span><span class="sxs-lookup"><span data-stu-id="7fd66-109">4.5</span></span>|
|<span data-ttu-id="7fd66-110">Type</span><span class="sxs-lookup"><span data-stu-id="7fd66-110">Type</span></span>|<span data-ttu-id="7fd66-111">Redirecionando</span><span class="sxs-lookup"><span data-stu-id="7fd66-111">Retargeting</span></span>|
|<span data-ttu-id="7fd66-112">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="7fd66-112">Affected APIs</span></span>|<ul><li><xref:System.Activities.Presentation.WorkflowDesigner.Load?displayProperty=nameWithType></li></ul>|
