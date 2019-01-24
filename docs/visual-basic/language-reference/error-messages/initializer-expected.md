---
title: Inicializador esperado
ms.date: 07/20/2015
f1_keywords:
- vbc30996
- bc30996
helpviewer_keywords:
- BC30996
ms.assetid: 6e183fe0-8888-43ed-a062-01571079455f
ms.openlocfilehash: 1fa66a3c50b5c1eadd4c63b92c57ab60e1a11076
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54595988"
---
# <a name="initializer-expected"></a><span data-ttu-id="d4484-102">Inicializador esperado</span><span class="sxs-lookup"><span data-stu-id="d4484-102">Initializer expected</span></span>
<span data-ttu-id="d4484-103">Você tentou declarar uma instância de uma classe usando um inicializador de objeto no qual a lista de inicialização está vazia, conforme mostrado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="d4484-103">You have tried to declare an instance of a class by using an object initializer in which the initialization list is empty, as shown in the following example.</span></span>  
  
 `' Not valid.`  
  
 `' Dim aStudent As New Student With {}`  
  
 <span data-ttu-id="d4484-104">Pelo menos um campo ou propriedade deve ser inicializada na lista de inicializadores, conforme mostrado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="d4484-104">At least one field or property must be initialized in the initializer list, as shown in the following example.</span></span>  
  
 `Dim aStudent As New Student With {.year = "Senior"}`  
  
 <span data-ttu-id="d4484-105">**ID do erro:** BC30996</span><span class="sxs-lookup"><span data-stu-id="d4484-105">**Error ID:** BC30996</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="d4484-106">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="d4484-106">To correct this error</span></span>  
  
1.  <span data-ttu-id="d4484-107">Inicializar pelo menos um campo ou propriedade no inicializador, ou não usar um inicializador de objeto.</span><span class="sxs-lookup"><span data-stu-id="d4484-107">Initialize at least one field or property in the initializer, or do not use an object initializer.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d4484-108">Consulte também</span><span class="sxs-lookup"><span data-stu-id="d4484-108">See also</span></span>
- [<span data-ttu-id="d4484-109">Inicializadores de objeto: Tipos nomeados e anônimos</span><span class="sxs-lookup"><span data-stu-id="d4484-109">Object Initializers: Named and Anonymous Types</span></span>](../../../visual-basic/programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md)
- [<span data-ttu-id="d4484-110">Como: Declarar um objeto usando um inicializador de objeto</span><span class="sxs-lookup"><span data-stu-id="d4484-110">How to: Declare an Object by Using an Object Initializer</span></span>](../../../visual-basic/programming-guide/language-features/objects-and-classes/how-to-declare-an-object-by-using-an-object-initializer.md)
