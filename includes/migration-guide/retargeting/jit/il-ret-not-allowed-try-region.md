---
ms.openlocfilehash: 1687b1b9a1a6861f9569a0e29426de7f32ffc32b
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59803119"
---
### <a name="il-ret-not-allowed-in-a-try-region"></a><span data-ttu-id="841b6-101">IL ret não é permitido em uma região try</span><span class="sxs-lookup"><span data-stu-id="841b6-101">IL ret not allowed in a try region</span></span>

|   |   |
|---|---|
|<span data-ttu-id="841b6-102">Detalhes</span><span class="sxs-lookup"><span data-stu-id="841b6-102">Details</span></span>|<span data-ttu-id="841b6-103">Ao contrário do compilador Just-In-Time JIT64, o RyuJIT (usado no .NET Framework 4.6) não permite que uma instrução IL ret em uma região try.</span><span class="sxs-lookup"><span data-stu-id="841b6-103">Unlike the JIT64 just-in-time compiler, RyuJIT (used in .NET Framework 4.6) does not allow an IL ret instruction in a try region.</span></span> <span data-ttu-id="841b6-104">Retornar de uma região try não é permitido pela especificação ECMA-335, e nenhum compilador gerenciado conhecido gera tal IL.</span><span class="sxs-lookup"><span data-stu-id="841b6-104">Returning from a try region is disallowed by the ECMA-335 specification, and no known managed compiler generates such IL.</span></span> <span data-ttu-id="841b6-105">No entanto, o compilador JIT64 executará essa IL se ela for gerada usando emissão de reflexo.</span><span class="sxs-lookup"><span data-stu-id="841b6-105">However, the JIT64 compiler will execute such IL if it is generated using reflection emit.</span></span>|
|<span data-ttu-id="841b6-106">Sugestão</span><span class="sxs-lookup"><span data-stu-id="841b6-106">Suggestion</span></span>|<span data-ttu-id="841b6-107">Se um aplicativo estiver gerando uma IL que inclua um opcode ret em uma região try, o aplicativo poderá ser direcionado ao .NET Framework 4.5 para usar o JIT antigo e evitar essa interrupção.</span><span class="sxs-lookup"><span data-stu-id="841b6-107">If an app is generating IL that includes a ret opcode in a try region, the app may target .NET Framework 4.5 to use the old JIT and avoid this break.</span></span> <span data-ttu-id="841b6-108">Como alternativa, a IL gerada pode ser atualizado para retornar após a região try.</span><span class="sxs-lookup"><span data-stu-id="841b6-108">Alternatively, the generated IL may be updated to return after the try region.</span></span>|
|<span data-ttu-id="841b6-109">Escopo</span><span class="sxs-lookup"><span data-stu-id="841b6-109">Scope</span></span>|<span data-ttu-id="841b6-110">Microsoft Edge</span><span class="sxs-lookup"><span data-stu-id="841b6-110">Edge</span></span>|
|<span data-ttu-id="841b6-111">Versão</span><span class="sxs-lookup"><span data-stu-id="841b6-111">Version</span></span>|<span data-ttu-id="841b6-112">4.6</span><span class="sxs-lookup"><span data-stu-id="841b6-112">4.6</span></span>|
|<span data-ttu-id="841b6-113">Tipo</span><span class="sxs-lookup"><span data-stu-id="841b6-113">Type</span></span>|<span data-ttu-id="841b6-114">Redirecionando</span><span class="sxs-lookup"><span data-stu-id="841b6-114">Retargeting</span></span>|
