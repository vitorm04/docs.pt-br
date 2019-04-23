---
ms.openlocfilehash: 8b2a01eb6dfdd5bd2bcbef6014d4edeb3ec82ac1
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59803190"
---
### <a name="winforms-checkforoverflowunderflow-property-is-now-true-for-systemdrawing"></a><span data-ttu-id="19122-101">A propriedade CheckForOverflowUnderflow do WinForm agora é true para System.Drawing</span><span class="sxs-lookup"><span data-stu-id="19122-101">WinForm's CheckForOverflowUnderflow property is now true for System.Drawing</span></span>

|   |   |
|---|---|
|<span data-ttu-id="19122-102">Detalhes</span><span class="sxs-lookup"><span data-stu-id="19122-102">Details</span></span>|<span data-ttu-id="19122-103">A propriedade CheckForOverflowUnderflow do o assembly System.Drawing.dll está definida como true.</span><span class="sxs-lookup"><span data-stu-id="19122-103">The CheckForOverflowUnderflow property for the System.Drawing.dll assembly is set to true.</span></span>|
|<span data-ttu-id="19122-104">Sugestão</span><span class="sxs-lookup"><span data-stu-id="19122-104">Suggestion</span></span>|<span data-ttu-id="19122-105">Anteriormente, quando os estouros ocorriam, o resultado teria sido truncado silenciosamente.</span><span class="sxs-lookup"><span data-stu-id="19122-105">Previously when overflows occurred, the result would be silently truncated.</span></span> <span data-ttu-id="19122-106">Agora, uma exceção <xref:System.OverflowException?displayProperty=name> é gerada.</span><span class="sxs-lookup"><span data-stu-id="19122-106">Now an <xref:System.OverflowException?displayProperty=name> exception is thrown.</span></span>|
|<span data-ttu-id="19122-107">Escopo</span><span class="sxs-lookup"><span data-stu-id="19122-107">Scope</span></span>|<span data-ttu-id="19122-108">Microsoft Edge</span><span class="sxs-lookup"><span data-stu-id="19122-108">Edge</span></span>|
|<span data-ttu-id="19122-109">Versão</span><span class="sxs-lookup"><span data-stu-id="19122-109">Version</span></span>|<span data-ttu-id="19122-110">4.5</span><span class="sxs-lookup"><span data-stu-id="19122-110">4.5</span></span>|
|<span data-ttu-id="19122-111">Tipo</span><span class="sxs-lookup"><span data-stu-id="19122-111">Type</span></span>|<span data-ttu-id="19122-112">Tempo de execução</span><span class="sxs-lookup"><span data-stu-id="19122-112">Runtime</span></span>|
