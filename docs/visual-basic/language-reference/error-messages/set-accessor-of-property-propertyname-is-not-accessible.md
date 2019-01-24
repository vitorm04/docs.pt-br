---
title: '&#39;Defina&#39; acessador de propriedade &#39; &lt;propertyname&gt; &#39; não está acessível'
ms.date: 07/20/2015
f1_keywords:
- vbc31102
- bc31102
helpviewer_keywords:
- BC31102
ms.assetid: 6f7b31b7-3656-4ae1-8851-90f5f4c6950a
ms.openlocfilehash: a543506b06742f3ee9101edbac962e761ddd531d
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54606563"
---
# <a name="39set39-accessor-of-property-39ltpropertynamegt39-is-not-accessible"></a><span data-ttu-id="84046-102">&#39;Defina&#39; acessador de propriedade &#39; &lt;propertyname&gt; &#39; não está acessível</span><span class="sxs-lookup"><span data-stu-id="84046-102">&#39;Set&#39; accessor of property &#39;&lt;propertyname&gt;&#39; is not accessible</span></span>
<span data-ttu-id="84046-103">Uma declaração tenta armazenar o valor de uma propriedade quando ela não tem acesso para a propriedade `Set` procedimento.</span><span class="sxs-lookup"><span data-stu-id="84046-103">A statement attempts to store the value of a property when it does not have access to the property's `Set` procedure.</span></span>  
  
 <span data-ttu-id="84046-104">Se o [instrução Set](../../../visual-basic/language-reference/statements/set-statement.md) está marcada com um acesso mais restritivo nível que seus [instrução Property](../../../visual-basic/language-reference/statements/property-statement.md), uma tentativa para definir o valor da propriedade pode falhar nos seguintes casos:</span><span class="sxs-lookup"><span data-stu-id="84046-104">If the [Set Statement](../../../visual-basic/language-reference/statements/set-statement.md) is marked with a more restrictive access level than its [Property Statement](../../../visual-basic/language-reference/statements/property-statement.md), an attempt to set the property value could fail in the following cases:</span></span>  
  
-   <span data-ttu-id="84046-105">O `Set` declaração está marcada [privada](../../../visual-basic/language-reference/modifiers/private.md) e o código de chamada está fora da classe ou estrutura na qual a propriedade é definida.</span><span class="sxs-lookup"><span data-stu-id="84046-105">The `Set` statement is marked [Private](../../../visual-basic/language-reference/modifiers/private.md) and the calling code is outside the class or structure in which the property is defined.</span></span>  
  
-   <span data-ttu-id="84046-106">O `Set` declaração está marcada [protegido](../../../visual-basic/language-reference/modifiers/protected.md) e o código de chamada é não na classe ou estrutura na qual a propriedade é definida, nem em uma classe derivada.</span><span class="sxs-lookup"><span data-stu-id="84046-106">The `Set` statement is marked [Protected](../../../visual-basic/language-reference/modifiers/protected.md) and the calling code is not in the class or structure in which the property is defined, nor in a derived class.</span></span>  
  
-   <span data-ttu-id="84046-107">O `Set` declaração está marcada [amigo](../../../visual-basic/language-reference/modifiers/friend.md) e o código de chamada não está no mesmo assembly no qual a propriedade é definida.</span><span class="sxs-lookup"><span data-stu-id="84046-107">The `Set` statement is marked [Friend](../../../visual-basic/language-reference/modifiers/friend.md) and the calling code is not in the same assembly in which the property is defined.</span></span>  
  
 <span data-ttu-id="84046-108">**ID do erro:** BC31102</span><span class="sxs-lookup"><span data-stu-id="84046-108">**Error ID:** BC31102</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="84046-109">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="84046-109">To correct this error</span></span>  
  
-   <span data-ttu-id="84046-110">Se você tiver o controle do código-fonte definindo a propriedade, considere a possibilidade de declarar o `Set` procedimento com o mesmo nível de acesso que a própria propriedade.</span><span class="sxs-lookup"><span data-stu-id="84046-110">If you have control of the source code defining the property, consider declaring the `Set` procedure with the same access level as the property itself.</span></span>  
  
-   <span data-ttu-id="84046-111">Se você não tem controle do código-fonte definindo a propriedade, você deve restringir o `Set` procedimento de nível de acesso mais do que a própria propriedade, tente mover a instrução que define o valor da propriedade para uma região de código que tem um melhor acesso para o propriedade.</span><span class="sxs-lookup"><span data-stu-id="84046-111">If you do not have control of the source code defining the property, or you must restrict the `Set` procedure access level more than the property itself, try to move the statement that sets the property value to a region of code that has better access to the property.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="84046-112">Consulte também</span><span class="sxs-lookup"><span data-stu-id="84046-112">See also</span></span>
- [<span data-ttu-id="84046-113">Procedimentos de Propriedade</span><span class="sxs-lookup"><span data-stu-id="84046-113">Property Procedures</span></span>](../../../visual-basic/programming-guide/language-features/procedures/property-procedures.md)
- [<span data-ttu-id="84046-114">Como: Declarar uma propriedade com níveis de acesso mistos</span><span class="sxs-lookup"><span data-stu-id="84046-114">How to: Declare a Property with Mixed Access Levels</span></span>](../../../visual-basic/programming-guide/language-features/procedures/how-to-declare-a-property-with-mixed-access-levels.md)
