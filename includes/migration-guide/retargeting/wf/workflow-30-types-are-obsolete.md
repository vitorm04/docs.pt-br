---
ms.openlocfilehash: 1f85b1ce95ca07329aff77af4ec894622e0818d1
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90606593"
---
### <a name="workflow-30-types-are-obsolete"></a><span data-ttu-id="3a3f3-101">Os tipos do WorkFlow 3.0 estão obsoletos</span><span class="sxs-lookup"><span data-stu-id="3a3f3-101">WorkFlow 3.0 types are obsolete</span></span>

#### <a name="details"></a><span data-ttu-id="3a3f3-102">Detalhes</span><span class="sxs-lookup"><span data-stu-id="3a3f3-102">Details</span></span>

<span data-ttu-id="3a3f3-103">As APIs (aquelas do namespace System.Workflow) do WWF (Windows Workflow Foundation) 3.0 agora estão obsoletas.</span><span class="sxs-lookup"><span data-stu-id="3a3f3-103">Windows Workflow Foundation (WWF) 3.0 APIs (those from the System.Workflow namespace) are now obsolete.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="3a3f3-104">Sugestão</span><span class="sxs-lookup"><span data-stu-id="3a3f3-104">Suggestion</span></span>

<span data-ttu-id="3a3f3-105">Agora devem ser usadas as novas APIs (em System.Activities) do WWF 4.0.</span><span class="sxs-lookup"><span data-stu-id="3a3f3-105">New WWF 4.0 APIs (in System.Activities) should be used instead.</span></span> <span data-ttu-id="3a3f3-106">Um exemplo de como usar as novas APIs pode ser encontrado [aqui](~/docs/framework/windows-workflow-foundation/how-to-update-the-definition-of-a-running-workflow-instance.md), e outras diretrizes estão disponíveis [aqui](/archive/blogs/workflowteam/wf3-types-marked-obsolete-in-net-4-5).</span><span class="sxs-lookup"><span data-stu-id="3a3f3-106">An example of using the new APIs can be found [here](~/docs/framework/windows-workflow-foundation/how-to-update-the-definition-of-a-running-workflow-instance.md) and further guidance is available [here](/archive/blogs/workflowteam/wf3-types-marked-obsolete-in-net-4-5).</span></span> <span data-ttu-id="3a3f3-107">Como alternativa, uma vez que as APIs do WWF 3.0 ainda têm suporte, elas poderão ser usadas, e o aviso de hora da compilação deve ser evitado suprimindo-o ou usando um compilador mais antigo.</span><span class="sxs-lookup"><span data-stu-id="3a3f3-107">Alternatively, since the WWF 3.0 APIs are still supported, they may be used and the build-time warning avoided either by suppressing it or by using an older compiler.</span></span>

| <span data-ttu-id="3a3f3-108">Name</span><span class="sxs-lookup"><span data-stu-id="3a3f3-108">Name</span></span>    | <span data-ttu-id="3a3f3-109">Valor</span><span class="sxs-lookup"><span data-stu-id="3a3f3-109">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="3a3f3-110">Escopo</span><span class="sxs-lookup"><span data-stu-id="3a3f3-110">Scope</span></span>   | <span data-ttu-id="3a3f3-111">Principal</span><span class="sxs-lookup"><span data-stu-id="3a3f3-111">Major</span></span>       |
| <span data-ttu-id="3a3f3-112">Versão</span><span class="sxs-lookup"><span data-stu-id="3a3f3-112">Version</span></span> | <span data-ttu-id="3a3f3-113">4.5</span><span class="sxs-lookup"><span data-stu-id="3a3f3-113">4.5</span></span>         |
| <span data-ttu-id="3a3f3-114">Tipo</span><span class="sxs-lookup"><span data-stu-id="3a3f3-114">Type</span></span>    | <span data-ttu-id="3a3f3-115">Redirecionando</span><span class="sxs-lookup"><span data-stu-id="3a3f3-115">Retargeting</span></span> |
