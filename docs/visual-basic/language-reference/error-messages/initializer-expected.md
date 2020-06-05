---
title: Inicializador esperado
ms.date: 07/20/2015
f1_keywords:
- vbc30996
- bc30996
helpviewer_keywords:
- BC30996
ms.assetid: 6e183fe0-8888-43ed-a062-01571079455f
ms.openlocfilehash: 13fa8917f228661fc44f5e0920d91c596e250c38
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84402831"
---
# <a name="initializer-expected"></a><span data-ttu-id="f9b82-102">Inicializador esperado</span><span class="sxs-lookup"><span data-stu-id="f9b82-102">Initializer expected</span></span>
<span data-ttu-id="f9b82-103">Você tentou declarar uma instância de uma classe usando um inicializador de objeto no qual a lista de inicialização está vazia, conforme mostrado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="f9b82-103">You have tried to declare an instance of a class by using an object initializer in which the initialization list is empty, as shown in the following example.</span></span>  
  
 `' Not valid.`  
  
 `' Dim aStudent As New Student With {}`  
  
 <span data-ttu-id="f9b82-104">Pelo menos um campo ou propriedade deve ser inicializado na lista de inicializadores, conforme mostrado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="f9b82-104">At least one field or property must be initialized in the initializer list, as shown in the following example.</span></span>  
  
 `Dim aStudent As New Student With {.year = "Senior"}`  
  
 <span data-ttu-id="f9b82-105">**ID do erro:** BC30996</span><span class="sxs-lookup"><span data-stu-id="f9b82-105">**Error ID:** BC30996</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="f9b82-106">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="f9b82-106">To correct this error</span></span>  
  
1. <span data-ttu-id="f9b82-107">Inicialize pelo menos um campo ou propriedade no inicializador ou não use um inicializador de objeto.</span><span class="sxs-lookup"><span data-stu-id="f9b82-107">Initialize at least one field or property in the initializer, or do not use an object initializer.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f9b82-108">Confira também</span><span class="sxs-lookup"><span data-stu-id="f9b82-108">See also</span></span>

- [<span data-ttu-id="f9b82-109">Inicializadores de objeto: tipos nomeados e anônimos</span><span class="sxs-lookup"><span data-stu-id="f9b82-109">Object Initializers: Named and Anonymous Types</span></span>](../../programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md)
- [<span data-ttu-id="f9b82-110">Como declarar um objeto usando um inicializador de objeto</span><span class="sxs-lookup"><span data-stu-id="f9b82-110">How to: Declare an Object by Using an Object Initializer</span></span>](../../programming-guide/language-features/objects-and-classes/how-to-declare-an-object-by-using-an-object-initializer.md)
