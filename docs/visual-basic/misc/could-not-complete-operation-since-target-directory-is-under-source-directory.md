---
title: Não foi possível concluir a operação porque o diretório de destino está sob o diretório de origem
ms.date: 07/20/2015
f1_keywords:
- vbrIO_CyclicOperation
ms.assetid: 850d3a24-5d51-4ac8-a912-630efcd75278
ms.openlocfilehash: 46ec7ae452d4f8259d0f8ca3a896d1b29151ed61
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84376736"
---
# <a name="could-not-complete-operation-since-target-directory-is-under-source-directory"></a><span data-ttu-id="35e00-102">Não foi possível concluir a operação porque o diretório de destino está sob o diretório de origem</span><span class="sxs-lookup"><span data-stu-id="35e00-102">Could not complete operation since target directory is under source directory</span></span>
<span data-ttu-id="35e00-103">Falha em uma operação cíclica.</span><span class="sxs-lookup"><span data-stu-id="35e00-103">A cyclic operation has failed.</span></span> <span data-ttu-id="35e00-104">Ciclo de operações cíclicas e, portanto, não pode ser concluído.</span><span class="sxs-lookup"><span data-stu-id="35e00-104">Cyclic operations cycle and therefore cannot complete.</span></span> <span data-ttu-id="35e00-105">Por exemplo, o objeto A pode tentar herdar do objeto B, que por sua vez é herdado do objeto A.</span><span class="sxs-lookup"><span data-stu-id="35e00-105">For example, Object A may attempt to inherit from Object B, which in turn inherits from Object A.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="35e00-106">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="35e00-106">To correct this error</span></span>  
  
- <span data-ttu-id="35e00-107">Ao herdar, verifique se não há referências cíclicas.</span><span class="sxs-lookup"><span data-stu-id="35e00-107">When inheriting, make sure that there are no cyclic references.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="35e00-108">Confira também</span><span class="sxs-lookup"><span data-stu-id="35e00-108">See also</span></span>

- [<span data-ttu-id="35e00-109">Tipos de erro</span><span class="sxs-lookup"><span data-stu-id="35e00-109">Error Types</span></span>](../programming-guide/language-features/error-types.md)
- [<span data-ttu-id="35e00-110">Usar pontos de interrupção no depurador do Visual Studio</span><span class="sxs-lookup"><span data-stu-id="35e00-110">Use breakpoints in the Visual Studio debugger</span></span>](/visualstudio/debugger/using-breakpoints)
