---
title: Inicializador esperado
ms.date: 07/20/2015
f1_keywords:
- vbc30996
- bc30996
helpviewer_keywords:
- BC30996
ms.assetid: 6e183fe0-8888-43ed-a062-01571079455f
ms.openlocfilehash: cbe77bab3e4f8bf2094c70c1c16d95ee897c729e
ms.sourcegitcommit: ff5a4eb5cffbcac9521bc44a907a118cd7e8638d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/17/2020
ms.locfileid: "92163006"
---
# <a name="bc30996-initializer-expected"></a><span data-ttu-id="6b703-102">BC30996: inicializador esperado</span><span class="sxs-lookup"><span data-stu-id="6b703-102">BC30996: Initializer expected</span></span>

<span data-ttu-id="6b703-103">Você tentou declarar uma instância de uma classe usando um inicializador de objeto no qual a lista de inicialização está vazia, conforme mostrado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="6b703-103">You have tried to declare an instance of a class by using an object initializer in which the initialization list is empty, as shown in the following example.</span></span>

 `' Not valid.`

 `' Dim aStudent As New Student With {}`

 <span data-ttu-id="6b703-104">Pelo menos um campo ou propriedade deve ser inicializado na lista de inicializadores, conforme mostrado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="6b703-104">At least one field or property must be initialized in the initializer list, as shown in the following example.</span></span>

 `Dim aStudent As New Student With {.year = "Senior"}`

 <span data-ttu-id="6b703-105">**ID do erro:** BC30996</span><span class="sxs-lookup"><span data-stu-id="6b703-105">**Error ID:** BC30996</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="6b703-106">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="6b703-106">To correct this error</span></span>

- <span data-ttu-id="6b703-107">Inicialize pelo menos um campo ou propriedade no inicializador ou não use um inicializador de objeto.</span><span class="sxs-lookup"><span data-stu-id="6b703-107">Initialize at least one field or property in the initializer, or do not use an object initializer.</span></span>

## <a name="see-also"></a><span data-ttu-id="6b703-108">Veja também</span><span class="sxs-lookup"><span data-stu-id="6b703-108">See also</span></span>

- [<span data-ttu-id="6b703-109">Inicializadores de objeto: tipos nomeados e anônimos</span><span class="sxs-lookup"><span data-stu-id="6b703-109">Object Initializers: Named and Anonymous Types</span></span>](../../programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md)
- [<span data-ttu-id="6b703-110">Como declarar um objeto usando um inicializador de objeto</span><span class="sxs-lookup"><span data-stu-id="6b703-110">How to: Declare an Object by Using an Object Initializer</span></span>](../../programming-guide/language-features/objects-and-classes/how-to-declare-an-object-by-using-an-object-initializer.md)
