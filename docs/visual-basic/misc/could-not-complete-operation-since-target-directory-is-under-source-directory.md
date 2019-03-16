---
title: Não foi possível concluir a operação, pois o diretório de destino está sob o diretório de origem
ms.date: 07/20/2015
f1_keywords:
- vbrIO_CyclicOperation
ms.assetid: 850d3a24-5d51-4ac8-a912-630efcd75278
ms.openlocfilehash: f53ad664b341d4db803dee1f0f008c3918d13d93
ms.sourcegitcommit: 5c1abeec15fbddcc7dbaa729fabc1f1f29f12045
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/15/2019
ms.locfileid: "58039432"
---
# <a name="could-not-complete-operation-since-target-directory-is-under-source-directory"></a><span data-ttu-id="f7cdd-102">Não foi possível concluir a operação, pois o diretório de destino está sob o diretório de origem</span><span class="sxs-lookup"><span data-stu-id="f7cdd-102">Could not complete operation since target directory is under source directory</span></span>
<span data-ttu-id="f7cdd-103">Uma operação cíclica falhou.</span><span class="sxs-lookup"><span data-stu-id="f7cdd-103">A cyclic operation has failed.</span></span> <span data-ttu-id="f7cdd-104">Ciclo de operações cíclicas e, portanto, não pode ser concluída.</span><span class="sxs-lookup"><span data-stu-id="f7cdd-104">Cyclic operations cycle and therefore cannot complete.</span></span> <span data-ttu-id="f7cdd-105">Por exemplo, o objeto A pode tentar herdar do objeto B, que por sua vez herda de objeto A.</span><span class="sxs-lookup"><span data-stu-id="f7cdd-105">For example, Object A may attempt to inherit from Object B, which in turn inherits from Object A.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="f7cdd-106">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="f7cdd-106">To correct this error</span></span>  
  
-   <span data-ttu-id="f7cdd-107">Ao herdar, certifique-se de que não há nenhuma referência cíclica.</span><span class="sxs-lookup"><span data-stu-id="f7cdd-107">When inheriting, make sure that there are no cyclic references.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f7cdd-108">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f7cdd-108">See also</span></span>

- [<span data-ttu-id="f7cdd-109">Tipos de Erro</span><span class="sxs-lookup"><span data-stu-id="f7cdd-109">Error Types</span></span>](../../visual-basic/programming-guide/language-features/error-types.md)
- [<span data-ttu-id="f7cdd-110">Usar pontos de interrupção no depurador do Visual Studio</span><span class="sxs-lookup"><span data-stu-id="f7cdd-110">Use breakpoints in the Visual Studio debugger</span></span>](/visualstudio/debugger/using-breakpoints)
