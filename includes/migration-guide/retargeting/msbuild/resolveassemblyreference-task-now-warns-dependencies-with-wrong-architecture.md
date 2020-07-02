---
ms.openlocfilehash: 4d410811095786b33580d25f6c6eab3ac2f27148
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85616018"
---
### <a name="resolveassemblyreference-task-now-warns-of-dependencies-with-the-wrong-architecture"></a><span data-ttu-id="dcd17-101">A tarefa ResolveAssemblyReference agora avisa sobre dependências com arquitetura incorreta</span><span class="sxs-lookup"><span data-stu-id="dcd17-101">ResolveAssemblyReference task now warns of dependencies with the wrong architecture</span></span>

#### <a name="details"></a><span data-ttu-id="dcd17-102">Detalhes</span><span class="sxs-lookup"><span data-stu-id="dcd17-102">Details</span></span>

<span data-ttu-id="dcd17-103">A tarefa emite um aviso, MSB3270, que indica que uma referência ou qualquer uma de suas dependências não corresponde à arquitetura do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="dcd17-103">The task emits a warning, MSB3270, which indicates that a reference or any of its dependencies does not match the app's architecture.</span></span> <span data-ttu-id="dcd17-104">Por exemplo, isso ocorrerá se um aplicativo que tenha sido compilado com a opção `AnyCPU` incluir uma referência x86.</span><span class="sxs-lookup"><span data-stu-id="dcd17-104">For example, this occurs if an app that was compiled with the `AnyCPU` option includes an x86 reference.</span></span> <span data-ttu-id="dcd17-105">Esse cenário pode resultar em uma falha do aplicativo no tempo de execução (nesse caso, se o aplicativo for implantado como um processo x64).</span><span class="sxs-lookup"><span data-stu-id="dcd17-105">Such a scenario could result in an app failure at run time (in this case, if the app is deployed as an x64 process).</span></span>

#### <a name="suggestion"></a><span data-ttu-id="dcd17-106">Sugestão</span><span class="sxs-lookup"><span data-stu-id="dcd17-106">Suggestion</span></span>

<span data-ttu-id="dcd17-107">Há duas áreas de impacto:</span><span class="sxs-lookup"><span data-stu-id="dcd17-107">There are two areas of impact:</span></span>

- <span data-ttu-id="dcd17-108">A recompilação gerencia os avisos que não foram exibidos quando o aplicativo foi compilado com uma versão anterior do MSBuild.</span><span class="sxs-lookup"><span data-stu-id="dcd17-108">Recompilation generates warnings that did not appear when the app was compiled under a previous version of MSBuild.</span></span> <span data-ttu-id="dcd17-109">Entretanto, como o aviso identifica uma possível fonte de falha no runtime, ele deve ser investigado e resolvido.</span><span class="sxs-lookup"><span data-stu-id="dcd17-109">However, because the warning identifies a possible source of runtime failure, it should be investigated and addressed.</span></span>
- <span data-ttu-id="dcd17-110">Se os avisos forem tratados como erros, o aplicativo não será compilado.</span><span class="sxs-lookup"><span data-stu-id="dcd17-110">If warnings are treated as errors, the app will fail to compile.</span></span>

| <span data-ttu-id="dcd17-111">Name</span><span class="sxs-lookup"><span data-stu-id="dcd17-111">Name</span></span>    | <span data-ttu-id="dcd17-112">Valor</span><span class="sxs-lookup"><span data-stu-id="dcd17-112">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="dcd17-113">Escopo</span><span class="sxs-lookup"><span data-stu-id="dcd17-113">Scope</span></span>   | <span data-ttu-id="dcd17-114">Secundária</span><span class="sxs-lookup"><span data-stu-id="dcd17-114">Minor</span></span>       |
| <span data-ttu-id="dcd17-115">Versão</span><span class="sxs-lookup"><span data-stu-id="dcd17-115">Version</span></span> | <span data-ttu-id="dcd17-116">4.5.1</span><span class="sxs-lookup"><span data-stu-id="dcd17-116">4.5.1</span></span>       |
| <span data-ttu-id="dcd17-117">Type</span><span class="sxs-lookup"><span data-stu-id="dcd17-117">Type</span></span>    | <span data-ttu-id="dcd17-118">Redirecionando</span><span class="sxs-lookup"><span data-stu-id="dcd17-118">Retargeting</span></span> |
