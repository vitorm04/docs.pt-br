---
ms.openlocfilehash: a44458484ea09c566defeabc9b604bd55d994e93
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85617518"
---
### <a name="calls-to-systemwindowsinputpencontextdisable-on-touch-enabled-systems-may-throw-an-argumentexception"></a><span data-ttu-id="88787-101">Chamadas para System.Windows.Input.PenContext.Disable em sistemas habilitados para toque podem gerar ArgumentException</span><span class="sxs-lookup"><span data-stu-id="88787-101">Calls to System.Windows.Input.PenContext.Disable on touch-enabled systems may throw an ArgumentException</span></span>

#### <a name="details"></a><span data-ttu-id="88787-102">Detalhes</span><span class="sxs-lookup"><span data-stu-id="88787-102">Details</span></span>

<span data-ttu-id="88787-103">Em algumas circunstâncias, chamadas para o método interno **System.Windows.Intput.PenContext.Disable** em sistemas habilitados para toque podem gerar uma `T:System.ArgumentException` sem tratamento devido à reentrância.</span><span class="sxs-lookup"><span data-stu-id="88787-103">Under some circumstances, calls to the internal **System.Windows.Intput.PenContext.Disable** method on touch-enabled systems may throw an unhandled `T:System.ArgumentException` because of reentrancy.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="88787-104">Sugestão</span><span class="sxs-lookup"><span data-stu-id="88787-104">Suggestion</span></span>

<span data-ttu-id="88787-105">Esse problema foi resolvido no .NET Framework 4.7.</span><span class="sxs-lookup"><span data-stu-id="88787-105">This issue has been addressed in the .NET Framework 4.7.</span></span> <span data-ttu-id="88787-106">Para evitar a exceção, atualize para uma versão do .NET Framework a partir de 4.7.</span><span class="sxs-lookup"><span data-stu-id="88787-106">To prevent the exception, upgrade to a version of the .NET Framework starting with the .NET Framework 4.7.</span></span>

| <span data-ttu-id="88787-107">Name</span><span class="sxs-lookup"><span data-stu-id="88787-107">Name</span></span>    | <span data-ttu-id="88787-108">Valor</span><span class="sxs-lookup"><span data-stu-id="88787-108">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="88787-109">Escopo</span><span class="sxs-lookup"><span data-stu-id="88787-109">Scope</span></span>   | <span data-ttu-id="88787-110">Microsoft Edge</span><span class="sxs-lookup"><span data-stu-id="88787-110">Edge</span></span>        |
| <span data-ttu-id="88787-111">Versão</span><span class="sxs-lookup"><span data-stu-id="88787-111">Version</span></span> | <span data-ttu-id="88787-112">4.6.1</span><span class="sxs-lookup"><span data-stu-id="88787-112">4.6.1</span></span>       |
| <span data-ttu-id="88787-113">Type</span><span class="sxs-lookup"><span data-stu-id="88787-113">Type</span></span>    | <span data-ttu-id="88787-114">Redirecionando</span><span class="sxs-lookup"><span data-stu-id="88787-114">Retargeting</span></span> |
