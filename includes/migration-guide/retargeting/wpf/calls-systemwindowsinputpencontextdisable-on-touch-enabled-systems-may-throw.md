---
ms.openlocfilehash: 6bb8c87af66e744514fb43e628c6423487342ac2
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/15/2020
ms.locfileid: "72887724"
---
### <a name="calls-to-systemwindowsinputpencontextdisable-on-touch-enabled-systems-may-throw-an-argumentexception"></a><span data-ttu-id="1eec9-101">Chamadas para System.Windows.Input.PenContext.Disable em sistemas habilitados para toque podem gerar ArgumentException</span><span class="sxs-lookup"><span data-stu-id="1eec9-101">Calls to System.Windows.Input.PenContext.Disable on touch-enabled systems may throw an ArgumentException</span></span>

|   |   |
|---|---|
|<span data-ttu-id="1eec9-102">Detalhes</span><span class="sxs-lookup"><span data-stu-id="1eec9-102">Details</span></span>|<span data-ttu-id="1eec9-103">Em algumas circunstâncias, chamadas para o método interno **System.Windows.Intput.PenContext.Disable** em sistemas habilitados para toque podem gerar uma <code>T:System.ArgumentException</code> sem tratamento devido à reentrância.</span><span class="sxs-lookup"><span data-stu-id="1eec9-103">Under some circumstances, calls to the internal **System.Windows.Intput.PenContext.Disable** method on touch-enabled systems may throw an unhandled <code>T:System.ArgumentException</code> because of reentrancy.</span></span>|
|<span data-ttu-id="1eec9-104">Sugestão</span><span class="sxs-lookup"><span data-stu-id="1eec9-104">Suggestion</span></span>|<span data-ttu-id="1eec9-105">Esse problema foi resolvido no .NET Framework 4.7.</span><span class="sxs-lookup"><span data-stu-id="1eec9-105">This issue has been addressed in the .NET Framework 4.7.</span></span> <span data-ttu-id="1eec9-106">Para evitar a exceção, atualize para uma versão do .NET Framework a partir de 4.7.</span><span class="sxs-lookup"><span data-stu-id="1eec9-106">To prevent the exception, upgrade to a version of the .NET Framework starting with the .NET Framework 4.7.</span></span>|
|<span data-ttu-id="1eec9-107">Escopo</span><span class="sxs-lookup"><span data-stu-id="1eec9-107">Scope</span></span>|<span data-ttu-id="1eec9-108">Microsoft Edge</span><span class="sxs-lookup"><span data-stu-id="1eec9-108">Edge</span></span>|
|<span data-ttu-id="1eec9-109">Versão</span><span class="sxs-lookup"><span data-stu-id="1eec9-109">Version</span></span>|<span data-ttu-id="1eec9-110">4.6.1</span><span class="sxs-lookup"><span data-stu-id="1eec9-110">4.6.1</span></span>|
|<span data-ttu-id="1eec9-111">Type</span><span class="sxs-lookup"><span data-stu-id="1eec9-111">Type</span></span>|<span data-ttu-id="1eec9-112">Redirecionando</span><span class="sxs-lookup"><span data-stu-id="1eec9-112">Retargeting</span></span>|
