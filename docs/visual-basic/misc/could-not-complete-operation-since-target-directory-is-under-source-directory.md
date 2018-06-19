---
title: Não foi possível concluir a operação porque o diretório de destino está no diretório de origem
ms.date: 07/20/2015
f1_keywords:
- vbrIO_CyclicOperation
ms.assetid: 850d3a24-5d51-4ac8-a912-630efcd75278
ms.openlocfilehash: 68217023a980891200c18b5536ef902574d36257
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33638506"
---
# <a name="could-not-complete-operation-since-target-directory-is-under-source-directory"></a><span data-ttu-id="b2fa6-102">Não foi possível concluir a operação porque o diretório de destino está no diretório de origem</span><span class="sxs-lookup"><span data-stu-id="b2fa6-102">Could not complete operation since target directory is under source directory</span></span>
<span data-ttu-id="b2fa6-103">Uma operação cíclica falhou.</span><span class="sxs-lookup"><span data-stu-id="b2fa6-103">A cyclic operation has failed.</span></span> <span data-ttu-id="b2fa6-104">Ciclo de operações cíclicas e, portanto, não é possível concluir.</span><span class="sxs-lookup"><span data-stu-id="b2fa6-104">Cyclic operations cycle and therefore cannot complete.</span></span> <span data-ttu-id="b2fa6-105">Por exemplo, o objeto A pode tentar herdar do objeto B, que por sua vez, herda do objeto A.</span><span class="sxs-lookup"><span data-stu-id="b2fa6-105">For example, Object A may attempt to inherit from Object B, which in turn inherits from Object A.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="b2fa6-106">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="b2fa6-106">To correct this error</span></span>  
  
-   <span data-ttu-id="b2fa6-107">Ao herdar, certifique-se de que não há nenhuma referência cíclica.</span><span class="sxs-lookup"><span data-stu-id="b2fa6-107">When inheriting, make sure that there are no cyclic references.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b2fa6-108">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b2fa6-108">See Also</span></span>  
 [<span data-ttu-id="b2fa6-109">Tipos de Erro</span><span class="sxs-lookup"><span data-stu-id="b2fa6-109">Error Types</span></span>](../../visual-basic/programming-guide/language-features/error-types.md)  
 [<span data-ttu-id="b2fa6-110">Noções básicas de depuração: pontos de interrupção</span><span class="sxs-lookup"><span data-stu-id="b2fa6-110">Debugging Basics: Breakpoints</span></span>](http://msdn.microsoft.com/library/752a02c2-0ac7-4c8b-aa1b-4b2b3b21152e)
