---
ms.openlocfilehash: 358103d5816eb61c88738e9626fb02c563b507f8
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85617115"
---
### <a name="workflow-30-types-are-obsolete"></a><span data-ttu-id="a8c8c-101">Os tipos do WorkFlow 3.0 estão obsoletos</span><span class="sxs-lookup"><span data-stu-id="a8c8c-101">WorkFlow 3.0 types are obsolete</span></span>

#### <a name="details"></a><span data-ttu-id="a8c8c-102">Detalhes</span><span class="sxs-lookup"><span data-stu-id="a8c8c-102">Details</span></span>

<span data-ttu-id="a8c8c-103">As APIs (aquelas do namespace System.Workflow) do WWF (Windows Workflow Foundation) 3.0 agora estão obsoletas.</span><span class="sxs-lookup"><span data-stu-id="a8c8c-103">Windows Workflow Foundation (WWF) 3.0 APIs (those from the System.Workflow namespace) are now obsolete.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="a8c8c-104">Sugestão</span><span class="sxs-lookup"><span data-stu-id="a8c8c-104">Suggestion</span></span>

<span data-ttu-id="a8c8c-105">Agora devem ser usadas as novas APIs (em System.Activities) do WWF 4.0.</span><span class="sxs-lookup"><span data-stu-id="a8c8c-105">New WWF 4.0 APIs (in System.Activities) should be used instead.</span></span> <span data-ttu-id="a8c8c-106">Um exemplo de como usar as novas APIs pode ser encontrado [aqui](~/docs/framework/windows-workflow-foundation/how-to-update-the-definition-of-a-running-workflow-instance.md), e outras diretrizes estão disponíveis [aqui](https://docs.microsoft.com/archive/blogs/workflowteam/wf3-types-marked-obsolete-in-net-4-5).</span><span class="sxs-lookup"><span data-stu-id="a8c8c-106">An example of using the new APIs can be found [here](~/docs/framework/windows-workflow-foundation/how-to-update-the-definition-of-a-running-workflow-instance.md) and further guidance is available [here](https://docs.microsoft.com/archive/blogs/workflowteam/wf3-types-marked-obsolete-in-net-4-5).</span></span> <span data-ttu-id="a8c8c-107">Como alternativa, uma vez que as APIs do WWF 3.0 ainda têm suporte, elas poderão ser usadas, e o aviso de hora da compilação deve ser evitado suprimindo-o ou usando um compilador mais antigo.</span><span class="sxs-lookup"><span data-stu-id="a8c8c-107">Alternatively, since the WWF 3.0 APIs are still supported, they may be used and the build-time warning avoided either by suppressing it or by using an older compiler.</span></span>

| <span data-ttu-id="a8c8c-108">Name</span><span class="sxs-lookup"><span data-stu-id="a8c8c-108">Name</span></span>    | <span data-ttu-id="a8c8c-109">Valor</span><span class="sxs-lookup"><span data-stu-id="a8c8c-109">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="a8c8c-110">Escopo</span><span class="sxs-lookup"><span data-stu-id="a8c8c-110">Scope</span></span>   | <span data-ttu-id="a8c8c-111">Principal</span><span class="sxs-lookup"><span data-stu-id="a8c8c-111">Major</span></span>       |
| <span data-ttu-id="a8c8c-112">Versão</span><span class="sxs-lookup"><span data-stu-id="a8c8c-112">Version</span></span> | <span data-ttu-id="a8c8c-113">4.5</span><span class="sxs-lookup"><span data-stu-id="a8c8c-113">4.5</span></span>         |
| <span data-ttu-id="a8c8c-114">Type</span><span class="sxs-lookup"><span data-stu-id="a8c8c-114">Type</span></span>    | <span data-ttu-id="a8c8c-115">Redirecionando</span><span class="sxs-lookup"><span data-stu-id="a8c8c-115">Retargeting</span></span> |
