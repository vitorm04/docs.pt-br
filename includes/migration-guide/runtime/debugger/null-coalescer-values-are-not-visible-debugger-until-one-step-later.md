---
ms.openlocfilehash: 22f8e3bb1ba72379b3f5fc87a077e5fe57f89bf8
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59235029"
---
### <a name="null-coalescer-values-are-not-visible-in-debugger-until-one-step-later"></a><span data-ttu-id="7c645-101">Valores nulos de união não são visíveis no depurador até uma etapa posterior</span><span class="sxs-lookup"><span data-stu-id="7c645-101">Null coalescer values are not visible in debugger until one step later</span></span>

|   |   |
|---|---|
|<span data-ttu-id="7c645-102">Detalhes</span><span class="sxs-lookup"><span data-stu-id="7c645-102">Details</span></span>|<span data-ttu-id="7c645-103">Um bug no .NET Framework 4.5 faz com que os valores definidos por meio de uma operação de união nula não fiquem visíveis no depurador imediatamente após a operação de atribuição ser executada na versão de 64 bits do Framework.</span><span class="sxs-lookup"><span data-stu-id="7c645-103">A bug in the .NET Framework 4.5 causes values set via a null coalescing operation to not be visible in the debugger immediately after the assignment operation is executed when running on the 64-bit version of the Framework.</span></span>|
|<span data-ttu-id="7c645-104">Sugestão</span><span class="sxs-lookup"><span data-stu-id="7c645-104">Suggestion</span></span>|<span data-ttu-id="7c645-105">Colocar um tempo adicional no depurador fará com que o valor do local/campo seja atualizado corretamente.</span><span class="sxs-lookup"><span data-stu-id="7c645-105">Stepping one additional time in the debugger will cause the local/field's value to be correctly updated.</span></span> <span data-ttu-id="7c645-106">Além disso, esse problema foi corrigido no .NET Framework 4.6 e pode ser resolvido com o upgrade para essa versão do .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="7c645-106">Also, this issue has been fixed in the .NET Framework 4.6; upgrading to that version of the Framework should solve the issue.</span></span>|
|<span data-ttu-id="7c645-107">Escopo</span><span class="sxs-lookup"><span data-stu-id="7c645-107">Scope</span></span>|<span data-ttu-id="7c645-108">Microsoft Edge</span><span class="sxs-lookup"><span data-stu-id="7c645-108">Edge</span></span>|
|<span data-ttu-id="7c645-109">Versão</span><span class="sxs-lookup"><span data-stu-id="7c645-109">Version</span></span>|<span data-ttu-id="7c645-110">4.5</span><span class="sxs-lookup"><span data-stu-id="7c645-110">4.5</span></span>|
|<span data-ttu-id="7c645-111">Tipo</span><span class="sxs-lookup"><span data-stu-id="7c645-111">Type</span></span>|<span data-ttu-id="7c645-112">Tempo de execução</span><span class="sxs-lookup"><span data-stu-id="7c645-112">Runtime</span></span>|
