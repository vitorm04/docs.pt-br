---
title: '&#39;Obter&#39; acessador de propriedade &#39; &lt;propertyname&gt; &#39; não está acessível'
ms.date: 07/20/2015
f1_keywords:
- vbc31103
- bc31103
helpviewer_keywords:
- BC31103
ms.assetid: 3c346c32-7669-4b04-841d-7a9df9cb703e
ms.openlocfilehash: 0972c0909f8b07aa1c6700ec32d1a1ca55d00cc1
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33590199"
---
# <a name="39get39-accessor-of-property-39ltpropertynamegt39-is-not-accessible"></a><span data-ttu-id="38d60-102">&#39;Obter&#39; acessador de propriedade &#39; &lt;propertyname&gt; &#39; não está acessível</span><span class="sxs-lookup"><span data-stu-id="38d60-102">&#39;Get&#39; accessor of property &#39;&lt;propertyname&gt;&#39; is not accessible</span></span>
<span data-ttu-id="38d60-103">Uma declaração tenta recuperar o valor de uma propriedade quando ela não tem acesso para a propriedade `Get` procedimento.</span><span class="sxs-lookup"><span data-stu-id="38d60-103">A statement attempts to retrieve the value of a property when it does not have access to the property's `Get` procedure.</span></span>  
  
 <span data-ttu-id="38d60-104">Se o [obter instrução](../../../visual-basic/language-reference/statements/get-statement.md) está marcado com um acesso mais restritivo do nível em que seu [declaração de propriedade](../../../visual-basic/language-reference/statements/property-statement.md), uma tentativa de ler o valor da propriedade pode falhar nos seguintes casos:</span><span class="sxs-lookup"><span data-stu-id="38d60-104">If the [Get Statement](../../../visual-basic/language-reference/statements/get-statement.md) is marked with a more restrictive access level than its [Property Statement](../../../visual-basic/language-reference/statements/property-statement.md), an attempt to read the property value could fail in the following cases:</span></span>  
  
-   <span data-ttu-id="38d60-105">O `Get` instrução está marcado como [privada](../../../visual-basic/language-reference/modifiers/private.md) e o código de chamada está fora da classe ou estrutura na qual a propriedade está definida.</span><span class="sxs-lookup"><span data-stu-id="38d60-105">The `Get` statement is marked [Private](../../../visual-basic/language-reference/modifiers/private.md) and the calling code is outside the class or structure in which the property is defined.</span></span>  
  
-   <span data-ttu-id="38d60-106">O `Get` instrução está marcado como [protegidos](../../../visual-basic/language-reference/modifiers/protected.md) e o código de chamada é não na classe ou estrutura na qual a propriedade é definida, nem em uma classe derivada.</span><span class="sxs-lookup"><span data-stu-id="38d60-106">The `Get` statement is marked [Protected](../../../visual-basic/language-reference/modifiers/protected.md) and the calling code is not in the class or structure in which the property is defined, nor in a derived class.</span></span>  
  
-   <span data-ttu-id="38d60-107">O `Get` instrução está marcado como [Friend](../../../visual-basic/language-reference/modifiers/friend.md) e o código de chamada não está no mesmo assembly no qual a propriedade está definida.</span><span class="sxs-lookup"><span data-stu-id="38d60-107">The `Get` statement is marked [Friend](../../../visual-basic/language-reference/modifiers/friend.md) and the calling code is not in the same assembly in which the property is defined.</span></span>  
  
 <span data-ttu-id="38d60-108">**ID do erro:** BC31103</span><span class="sxs-lookup"><span data-stu-id="38d60-108">**Error ID:** BC31103</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="38d60-109">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="38d60-109">To correct this error</span></span>  
  
-   <span data-ttu-id="38d60-110">Se você tiver o controle do código-fonte definindo a propriedade, considere declarando o `Get` procedimento com o mesmo nível de acesso da propriedade.</span><span class="sxs-lookup"><span data-stu-id="38d60-110">If you have control of the source code defining the property, consider declaring the `Get` procedure with the same access level as the property itself.</span></span>  
  
-   <span data-ttu-id="38d60-111">Se você não tem controle do código-fonte definindo a propriedade, você deve restringir o `Get` procedimento nível de acesso mais que a própria propriedade, tente mover a declaração que lê o valor da propriedade para uma região de código que tem um acesso melhor para o propriedade.</span><span class="sxs-lookup"><span data-stu-id="38d60-111">If you do not have control of the source code defining the property, or you must restrict the `Get` procedure access level more than the property itself, try to move the statement that reads the property value to a region of code that has better access to the property.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="38d60-112">Consulte também</span><span class="sxs-lookup"><span data-stu-id="38d60-112">See Also</span></span>  
 [<span data-ttu-id="38d60-113">Procedimentos de Propriedade</span><span class="sxs-lookup"><span data-stu-id="38d60-113">Property Procedures</span></span>](../../../visual-basic/programming-guide/language-features/procedures/property-procedures.md)  
 [<span data-ttu-id="38d60-114">Como declarar uma propriedade com níveis de acesso mistos</span><span class="sxs-lookup"><span data-stu-id="38d60-114">How to: Declare a Property with Mixed Access Levels</span></span>](../../../visual-basic/programming-guide/language-features/procedures/how-to-declare-a-property-with-mixed-access-levels.md)
