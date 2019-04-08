---
ms.openlocfilehash: 0778285ef1b5702bd79743038a1bd21ba04612d6
ms.sourcegitcommit: 0aca6c5d166d7961a1e354c248495645b97a1dc5
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/01/2019
ms.locfileid: "58760949"
---
### <a name="calls-to-systemwindowsinputpencontextdisable-on-touch-enabled-systems-may-throw-an-argumentexception"></a><span data-ttu-id="37735-101">Chamadas para System.Windows.Input.PenContext.Disable em sistemas habilitados para toque podem gerar ArgumentException</span><span class="sxs-lookup"><span data-stu-id="37735-101">Calls to System.Windows.Input.PenContext.Disable on touch-enabled systems may throw an ArgumentException</span></span>

|   |   |
|---|---|
|<span data-ttu-id="37735-102">Detalhes</span><span class="sxs-lookup"><span data-stu-id="37735-102">Details</span></span>|<span data-ttu-id="37735-103">Em algumas circunstâncias, chamadas para o método interno <strong>System.Windows.Intput.PenContext.Disable</strong> em sistemas habilitados para toque podem gerar uma <code>T:System.ArgumentException</code> sem tratamento devido à reentrância.</span><span class="sxs-lookup"><span data-stu-id="37735-103">Under some circumstances, calls to the internal <strong>System.Windows.Intput.PenContext.Disable</strong> method on touch-enabled systems may throw an unhandled <code>T:System.ArgumentException</code> because of reentrancy.</span></span>|
|<span data-ttu-id="37735-104">Sugestão</span><span class="sxs-lookup"><span data-stu-id="37735-104">Suggestion</span></span>|<span data-ttu-id="37735-105">Esse problema foi resolvido no .NET Framework 4.7.</span><span class="sxs-lookup"><span data-stu-id="37735-105">This issue has been addressed in the .NET Framework 4.7.</span></span> <span data-ttu-id="37735-106">Para evitar a exceção, atualize para uma versão do .NET Framework a partir de 4.7.</span><span class="sxs-lookup"><span data-stu-id="37735-106">To prevent the exception, upgrade to a version of the .NET Framework starting with the .NET Framework 4.7.</span></span>|
|<span data-ttu-id="37735-107">Escopo</span><span class="sxs-lookup"><span data-stu-id="37735-107">Scope</span></span>|<span data-ttu-id="37735-108">Microsoft Edge</span><span class="sxs-lookup"><span data-stu-id="37735-108">Edge</span></span>|
|<span data-ttu-id="37735-109">Versão</span><span class="sxs-lookup"><span data-stu-id="37735-109">Version</span></span>|<span data-ttu-id="37735-110">4.6.1</span><span class="sxs-lookup"><span data-stu-id="37735-110">4.6.1</span></span>|
|<span data-ttu-id="37735-111">Tipo</span><span class="sxs-lookup"><span data-stu-id="37735-111">Type</span></span>|<span data-ttu-id="37735-112">Redirecionando</span><span class="sxs-lookup"><span data-stu-id="37735-112">Retargeting</span></span>|

