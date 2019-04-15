---
ms.openlocfilehash: 3cd5052dffcb059c240a310e0b89384f28409264
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59234336"
---
### <a name="calls-to-systemwindowsinputpencontextdisable-on-touch-enabled-systems-may-throw-an-argumentexception"></a><span data-ttu-id="b25d5-101">Chamadas para System.Windows.Input.PenContext.Disable em sistemas habilitados para toque podem gerar ArgumentException</span><span class="sxs-lookup"><span data-stu-id="b25d5-101">Calls to System.Windows.Input.PenContext.Disable on touch-enabled systems may throw an ArgumentException</span></span>

|   |   |
|---|---|
|<span data-ttu-id="b25d5-102">Detalhes</span><span class="sxs-lookup"><span data-stu-id="b25d5-102">Details</span></span>|<span data-ttu-id="b25d5-103">Em algumas circunstâncias, chamadas para o método interno <strong>System.Windows.Intput.PenContext.Disable</strong> em sistemas habilitados para toque podem gerar uma <code>T:System.ArgumentException</code> sem tratamento devido à reentrância.</span><span class="sxs-lookup"><span data-stu-id="b25d5-103">Under some circumstances, calls to the internal <strong>System.Windows.Intput.PenContext.Disable</strong> method on touch-enabled systems may throw an unhandled <code>T:System.ArgumentException</code> because of reentrancy.</span></span>|
|<span data-ttu-id="b25d5-104">Sugestão</span><span class="sxs-lookup"><span data-stu-id="b25d5-104">Suggestion</span></span>|<span data-ttu-id="b25d5-105">Esse problema foi resolvido no .NET Framework 4.7.</span><span class="sxs-lookup"><span data-stu-id="b25d5-105">This issue has been addressed in the .NET Framework 4.7.</span></span> <span data-ttu-id="b25d5-106">Para evitar a exceção, atualize para uma versão do .NET Framework a partir de 4.7.</span><span class="sxs-lookup"><span data-stu-id="b25d5-106">To prevent the exception, upgrade to a version of the .NET Framework starting with the .NET Framework 4.7.</span></span>|
|<span data-ttu-id="b25d5-107">Escopo</span><span class="sxs-lookup"><span data-stu-id="b25d5-107">Scope</span></span>|<span data-ttu-id="b25d5-108">Microsoft Edge</span><span class="sxs-lookup"><span data-stu-id="b25d5-108">Edge</span></span>|
|<span data-ttu-id="b25d5-109">Versão</span><span class="sxs-lookup"><span data-stu-id="b25d5-109">Version</span></span>|<span data-ttu-id="b25d5-110">4.6.1</span><span class="sxs-lookup"><span data-stu-id="b25d5-110">4.6.1</span></span>|
|<span data-ttu-id="b25d5-111">Tipo</span><span class="sxs-lookup"><span data-stu-id="b25d5-111">Type</span></span>|<span data-ttu-id="b25d5-112">Redirecionando</span><span class="sxs-lookup"><span data-stu-id="b25d5-112">Retargeting</span></span>|
