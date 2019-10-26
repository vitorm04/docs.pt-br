---
ms.openlocfilehash: 6bb8c87af66e744514fb43e628c6423487342ac2
ms.sourcegitcommit: 337bdc5a463875daf2cc6883e5a2da97d56f5000
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/24/2019
ms.locfileid: "72887724"
---
### <a name="calls-to-systemwindowsinputpencontextdisable-on-touch-enabled-systems-may-throw-an-argumentexception"></a><span data-ttu-id="b5bb8-101">Chamadas para System.Windows.Input.PenContext.Disable em sistemas habilitados para toque podem gerar ArgumentException</span><span class="sxs-lookup"><span data-stu-id="b5bb8-101">Calls to System.Windows.Input.PenContext.Disable on touch-enabled systems may throw an ArgumentException</span></span>

|   |   |
|---|---|
|<span data-ttu-id="b5bb8-102">Detalhes</span><span class="sxs-lookup"><span data-stu-id="b5bb8-102">Details</span></span>|<span data-ttu-id="b5bb8-103">Em algumas circunstâncias, chamadas para o método interno **System.Windows.Intput.PenContext.Disable** em sistemas habilitados para toque podem gerar uma <code>T:System.ArgumentException</code> sem tratamento devido à reentrância.</span><span class="sxs-lookup"><span data-stu-id="b5bb8-103">Under some circumstances, calls to the internal **System.Windows.Intput.PenContext.Disable** method on touch-enabled systems may throw an unhandled <code>T:System.ArgumentException</code> because of reentrancy.</span></span>|
|<span data-ttu-id="b5bb8-104">Sugestão</span><span class="sxs-lookup"><span data-stu-id="b5bb8-104">Suggestion</span></span>|<span data-ttu-id="b5bb8-105">Esse problema foi resolvido no .NET Framework 4.7.</span><span class="sxs-lookup"><span data-stu-id="b5bb8-105">This issue has been addressed in the .NET Framework 4.7.</span></span> <span data-ttu-id="b5bb8-106">Para evitar a exceção, atualize para uma versão do .NET Framework a partir de 4.7.</span><span class="sxs-lookup"><span data-stu-id="b5bb8-106">To prevent the exception, upgrade to a version of the .NET Framework starting with the .NET Framework 4.7.</span></span>|
|<span data-ttu-id="b5bb8-107">Escopo</span><span class="sxs-lookup"><span data-stu-id="b5bb8-107">Scope</span></span>|<span data-ttu-id="b5bb8-108">Borda</span><span class="sxs-lookup"><span data-stu-id="b5bb8-108">Edge</span></span>|
|<span data-ttu-id="b5bb8-109">Version</span><span class="sxs-lookup"><span data-stu-id="b5bb8-109">Version</span></span>|<span data-ttu-id="b5bb8-110">4.6.1</span><span class="sxs-lookup"><span data-stu-id="b5bb8-110">4.6.1</span></span>|
|<span data-ttu-id="b5bb8-111">Digite</span><span class="sxs-lookup"><span data-stu-id="b5bb8-111">Type</span></span>|<span data-ttu-id="b5bb8-112">Redirecionando</span><span class="sxs-lookup"><span data-stu-id="b5bb8-112">Retargeting</span></span>|
