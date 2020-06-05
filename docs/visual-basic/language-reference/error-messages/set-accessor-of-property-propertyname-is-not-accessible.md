---
title: O acessador 'Set' da propriedade '<propertyname>' não está acessível
ms.date: 07/20/2015
f1_keywords:
- vbc31102
- bc31102
helpviewer_keywords:
- BC31102
ms.assetid: 6f7b31b7-3656-4ae1-8851-90f5f4c6950a
ms.openlocfilehash: 077533a5b1fe241b61ded9516ad8f450d7dbbf5e
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84400338"
---
# <a name="set-accessor-of-property-propertyname-is-not-accessible"></a><span data-ttu-id="80c01-102">O acessador 'Set' da propriedade '\<propertyname>' não está acessível</span><span class="sxs-lookup"><span data-stu-id="80c01-102">'Set' accessor of property '\<propertyname>' is not accessible</span></span>
<span data-ttu-id="80c01-103">Uma instrução tenta armazenar o valor de uma propriedade quando não tem acesso ao procedimento da propriedade `Set` .</span><span class="sxs-lookup"><span data-stu-id="80c01-103">A statement attempts to store the value of a property when it does not have access to the property's `Set` procedure.</span></span>  
  
 <span data-ttu-id="80c01-104">Se a [instrução SET](../statements/set-statement.md) for marcada com um nível de acesso mais restritivo do que sua [instrução Property](../statements/property-statement.md), uma tentativa de definir o valor da propriedade poderá falhar nos seguintes casos:</span><span class="sxs-lookup"><span data-stu-id="80c01-104">If the [Set Statement](../statements/set-statement.md) is marked with a more restrictive access level than its [Property Statement](../statements/property-statement.md), an attempt to set the property value could fail in the following cases:</span></span>  
  
- <span data-ttu-id="80c01-105">A `Set` instrução é marcada como [particular](../modifiers/private.md) e o código de chamada está fora da classe ou estrutura na qual a propriedade é definida.</span><span class="sxs-lookup"><span data-stu-id="80c01-105">The `Set` statement is marked [Private](../modifiers/private.md) and the calling code is outside the class or structure in which the property is defined.</span></span>  
  
- <span data-ttu-id="80c01-106">A `Set` instrução é marcada como [protegida](../modifiers/protected.md) e o código de chamada não está na classe ou estrutura na qual a propriedade é definida, nem em uma classe derivada.</span><span class="sxs-lookup"><span data-stu-id="80c01-106">The `Set` statement is marked [Protected](../modifiers/protected.md) and the calling code is not in the class or structure in which the property is defined, nor in a derived class.</span></span>  
  
- <span data-ttu-id="80c01-107">A `Set` instrução é marcada como [Friend](../modifiers/friend.md) e o código de chamada não está no mesmo assembly no qual a propriedade é definida.</span><span class="sxs-lookup"><span data-stu-id="80c01-107">The `Set` statement is marked [Friend](../modifiers/friend.md) and the calling code is not in the same assembly in which the property is defined.</span></span>  
  
 <span data-ttu-id="80c01-108">**ID do erro:** BC31102</span><span class="sxs-lookup"><span data-stu-id="80c01-108">**Error ID:** BC31102</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="80c01-109">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="80c01-109">To correct this error</span></span>  
  
- <span data-ttu-id="80c01-110">Se você tiver controle do código-fonte que define a propriedade, considere declarar o `Set` procedimento com o mesmo nível de acesso que a própria propriedade.</span><span class="sxs-lookup"><span data-stu-id="80c01-110">If you have control of the source code defining the property, consider declaring the `Set` procedure with the same access level as the property itself.</span></span>  
  
- <span data-ttu-id="80c01-111">Se você não tem controle do código-fonte que define a propriedade ou deve restringir o nível de `Set` acesso do procedimento mais do que a propriedade em si, tente mover a instrução que define o valor da propriedade para uma região de código que tenha acesso melhor à propriedade.</span><span class="sxs-lookup"><span data-stu-id="80c01-111">If you do not have control of the source code defining the property, or you must restrict the `Set` procedure access level more than the property itself, try to move the statement that sets the property value to a region of code that has better access to the property.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="80c01-112">Confira também</span><span class="sxs-lookup"><span data-stu-id="80c01-112">See also</span></span>

- [<span data-ttu-id="80c01-113">Procedimentos de propriedade</span><span class="sxs-lookup"><span data-stu-id="80c01-113">Property Procedures</span></span>](../../programming-guide/language-features/procedures/property-procedures.md)
- [<span data-ttu-id="80c01-114">Como declarar uma propriedade com níveis de acesso mistos</span><span class="sxs-lookup"><span data-stu-id="80c01-114">How to: Declare a Property with Mixed Access Levels</span></span>](../../programming-guide/language-features/procedures/how-to-declare-a-property-with-mixed-access-levels.md)
