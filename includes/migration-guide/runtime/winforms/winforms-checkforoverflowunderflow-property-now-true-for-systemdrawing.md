---
ms.openlocfilehash: 8b2a01eb6dfdd5bd2bcbef6014d4edeb3ec82ac1
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "66379617"
---
### <a name="winforms-checkforoverflowunderflow-property-is-now-true-for-systemdrawing"></a><span data-ttu-id="9a9d8-101">A propriedade CheckForOverflowUnderflow do WinForm agora é true para System.Drawing</span><span class="sxs-lookup"><span data-stu-id="9a9d8-101">WinForm's CheckForOverflowUnderflow property is now true for System.Drawing</span></span>

|   |   |
|---|---|
|<span data-ttu-id="9a9d8-102">Detalhes</span><span class="sxs-lookup"><span data-stu-id="9a9d8-102">Details</span></span>|<span data-ttu-id="9a9d8-103">A propriedade CheckForOverflowUnderflow do o assembly System.Drawing.dll está definida como true.</span><span class="sxs-lookup"><span data-stu-id="9a9d8-103">The CheckForOverflowUnderflow property for the System.Drawing.dll assembly is set to true.</span></span>|
|<span data-ttu-id="9a9d8-104">Sugestão</span><span class="sxs-lookup"><span data-stu-id="9a9d8-104">Suggestion</span></span>|<span data-ttu-id="9a9d8-105">Anteriormente, quando os estouros ocorriam, o resultado teria sido truncado silenciosamente.</span><span class="sxs-lookup"><span data-stu-id="9a9d8-105">Previously when overflows occurred, the result would be silently truncated.</span></span> <span data-ttu-id="9a9d8-106">Agora, uma exceção <xref:System.OverflowException?displayProperty=name> é gerada.</span><span class="sxs-lookup"><span data-stu-id="9a9d8-106">Now an <xref:System.OverflowException?displayProperty=name> exception is thrown.</span></span>|
|<span data-ttu-id="9a9d8-107">Escopo</span><span class="sxs-lookup"><span data-stu-id="9a9d8-107">Scope</span></span>|<span data-ttu-id="9a9d8-108">Microsoft Edge</span><span class="sxs-lookup"><span data-stu-id="9a9d8-108">Edge</span></span>|
|<span data-ttu-id="9a9d8-109">Versão</span><span class="sxs-lookup"><span data-stu-id="9a9d8-109">Version</span></span>|<span data-ttu-id="9a9d8-110">4.5</span><span class="sxs-lookup"><span data-stu-id="9a9d8-110">4.5</span></span>|
|<span data-ttu-id="9a9d8-111">Tipo</span><span class="sxs-lookup"><span data-stu-id="9a9d8-111">Type</span></span>|<span data-ttu-id="9a9d8-112">Tempo de execução</span><span class="sxs-lookup"><span data-stu-id="9a9d8-112">Runtime</span></span>|
