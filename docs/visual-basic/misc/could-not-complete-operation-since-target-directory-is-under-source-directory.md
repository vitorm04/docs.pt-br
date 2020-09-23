---
title: Não foi possível concluir a operação porque o diretório de destino está sob o diretório de origem
ms.date: 07/20/2015
f1_keywords:
- vbrIO_CyclicOperation
ms.assetid: 850d3a24-5d51-4ac8-a912-630efcd75278
ms.openlocfilehash: d159b9bb3a765a2fefe99fa15dff42e979fda9e3
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/23/2020
ms.locfileid: "91079133"
---
# <a name="could-not-complete-operation-since-target-directory-is-under-source-directory"></a><span data-ttu-id="18e03-102">Não foi possível concluir a operação porque o diretório de destino está sob o diretório de origem</span><span class="sxs-lookup"><span data-stu-id="18e03-102">Could not complete operation since target directory is under source directory</span></span>

<span data-ttu-id="18e03-103">Falha em uma operação cíclica.</span><span class="sxs-lookup"><span data-stu-id="18e03-103">A cyclic operation has failed.</span></span> <span data-ttu-id="18e03-104">Ciclo de operações cíclicas e, portanto, não pode ser concluído.</span><span class="sxs-lookup"><span data-stu-id="18e03-104">Cyclic operations cycle and therefore cannot complete.</span></span> <span data-ttu-id="18e03-105">Por exemplo, o objeto A pode tentar herdar do objeto B, que por sua vez é herdado do objeto A.</span><span class="sxs-lookup"><span data-stu-id="18e03-105">For example, Object A may attempt to inherit from Object B, which in turn inherits from Object A.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="18e03-106">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="18e03-106">To correct this error</span></span>  
  
- <span data-ttu-id="18e03-107">Ao herdar, verifique se não há referências cíclicas.</span><span class="sxs-lookup"><span data-stu-id="18e03-107">When inheriting, make sure that there are no cyclic references.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="18e03-108">Confira também</span><span class="sxs-lookup"><span data-stu-id="18e03-108">See also</span></span>

- [<span data-ttu-id="18e03-109">Tipos de erro</span><span class="sxs-lookup"><span data-stu-id="18e03-109">Error Types</span></span>](../programming-guide/language-features/error-types.md)
- [<span data-ttu-id="18e03-110">Usar pontos de interrupção no depurador do Visual Studio</span><span class="sxs-lookup"><span data-stu-id="18e03-110">Use breakpoints in the Visual Studio debugger</span></span>](/visualstudio/debugger/using-breakpoints)
