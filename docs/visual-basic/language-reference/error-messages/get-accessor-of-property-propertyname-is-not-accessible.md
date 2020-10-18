---
title: O acessador 'Get' da propriedade '<propertyname>' não está acessível
ms.date: 07/20/2015
f1_keywords:
- vbc31103
- bc31103
helpviewer_keywords:
- BC31103
ms.assetid: 3c346c32-7669-4b04-841d-7a9df9cb703e
ms.openlocfilehash: bd6830e16ba3d1f76c61519b4456832a2efec716
ms.sourcegitcommit: ff5a4eb5cffbcac9521bc44a907a118cd7e8638d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/17/2020
ms.locfileid: "92162902"
---
# <a name="bc31103-get-accessor-of-property-propertyname-is-not-accessible"></a><span data-ttu-id="fa789-102">BC31103: o acessador ' Get ' da propriedade ' \<propertyname> ' não está acessível</span><span class="sxs-lookup"><span data-stu-id="fa789-102">BC31103: 'Get' accessor of property '\<propertyname>' is not accessible</span></span>

<span data-ttu-id="fa789-103">Uma instrução tenta recuperar o valor de uma propriedade quando ela não tem acesso ao procedimento da propriedade `Get` .</span><span class="sxs-lookup"><span data-stu-id="fa789-103">A statement attempts to retrieve the value of a property when it does not have access to the property's `Get` procedure.</span></span>

 <span data-ttu-id="fa789-104">Se a [instrução Get](../statements/get-statement.md) for marcada com um nível de acesso mais restritivo do que sua [instrução Property](../statements/property-statement.md), uma tentativa de ler o valor da propriedade poderá falhar nos seguintes casos:</span><span class="sxs-lookup"><span data-stu-id="fa789-104">If the [Get Statement](../statements/get-statement.md) is marked with a more restrictive access level than its [Property Statement](../statements/property-statement.md), an attempt to read the property value could fail in the following cases:</span></span>

- <span data-ttu-id="fa789-105">A `Get` instrução é marcada como [particular](../modifiers/private.md) e o código de chamada está fora da classe ou estrutura na qual a propriedade é definida.</span><span class="sxs-lookup"><span data-stu-id="fa789-105">The `Get` statement is marked [Private](../modifiers/private.md) and the calling code is outside the class or structure in which the property is defined.</span></span>

- <span data-ttu-id="fa789-106">A `Get` instrução é marcada como [protegida](../modifiers/protected.md) e o código de chamada não está na classe ou estrutura na qual a propriedade é definida, nem em uma classe derivada.</span><span class="sxs-lookup"><span data-stu-id="fa789-106">The `Get` statement is marked [Protected](../modifiers/protected.md) and the calling code is not in the class or structure in which the property is defined, nor in a derived class.</span></span>

- <span data-ttu-id="fa789-107">A `Get` instrução é marcada como [Friend](../modifiers/friend.md) e o código de chamada não está no mesmo assembly no qual a propriedade é definida.</span><span class="sxs-lookup"><span data-stu-id="fa789-107">The `Get` statement is marked [Friend](../modifiers/friend.md) and the calling code is not in the same assembly in which the property is defined.</span></span>

 <span data-ttu-id="fa789-108">**ID do erro:** BC31103</span><span class="sxs-lookup"><span data-stu-id="fa789-108">**Error ID:** BC31103</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="fa789-109">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="fa789-109">To correct this error</span></span>

- <span data-ttu-id="fa789-110">Se você tiver controle do código-fonte que define a propriedade, considere declarar o `Get` procedimento com o mesmo nível de acesso que a própria propriedade.</span><span class="sxs-lookup"><span data-stu-id="fa789-110">If you have control of the source code defining the property, consider declaring the `Get` procedure with the same access level as the property itself.</span></span>

- <span data-ttu-id="fa789-111">Se você não tem controle do código-fonte que define a propriedade ou deve restringir o nível de `Get` acesso do procedimento mais do que a propriedade em si, tente mover a instrução que lê o valor da propriedade para uma região de código que tenha melhor acesso à propriedade.</span><span class="sxs-lookup"><span data-stu-id="fa789-111">If you do not have control of the source code defining the property, or you must restrict the `Get` procedure access level more than the property itself, try to move the statement that reads the property value to a region of code that has better access to the property.</span></span>

## <a name="see-also"></a><span data-ttu-id="fa789-112">Veja também</span><span class="sxs-lookup"><span data-stu-id="fa789-112">See also</span></span>

- [<span data-ttu-id="fa789-113">Procedimentos de propriedade</span><span class="sxs-lookup"><span data-stu-id="fa789-113">Property Procedures</span></span>](../../programming-guide/language-features/procedures/property-procedures.md)
- [<span data-ttu-id="fa789-114">Como declarar uma propriedade com níveis de acesso mistos</span><span class="sxs-lookup"><span data-stu-id="fa789-114">How to: Declare a Property with Mixed Access Levels</span></span>](../../programming-guide/language-features/procedures/how-to-declare-a-property-with-mixed-access-levels.md)
