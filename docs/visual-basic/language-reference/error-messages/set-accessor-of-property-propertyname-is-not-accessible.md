---
title: "Acessador de propriedade &quot; set&quot; &quot;&lt;propertyname&gt;&quot; não está acessível | Documentos do Microsoft"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc31102
- bc31102
dev_langs:
- VB
helpviewer_keywords:
- BC31102
ms.assetid: 6f7b31b7-3656-4ae1-8851-90f5f4c6950a
caps.latest.revision: 9
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 3f47b231a5adfc505f01784f08869c806b5ecbe3
ms.contentlocale: pt-br
ms.lasthandoff: 04/12/2017

---
# <a name="39set39-accessor-of-property-39ltpropertynamegt39-is-not-accessible"></a><span data-ttu-id="8ac19-102">Acessador de propriedade ' set' '&lt;propertyname&gt;' não está acessível</span><span class="sxs-lookup"><span data-stu-id="8ac19-102">&#39;Set&#39; accessor of property &#39;&lt;propertyname&gt;&#39; is not accessible</span></span>
<span data-ttu-id="8ac19-103">Uma instrução tenta recuperar o valor de uma propriedade quando ela não tem acesso à propriedade `Set` procedimento.</span><span class="sxs-lookup"><span data-stu-id="8ac19-103">A statement attempts to store the value of a property when it does not have access to the property's `Set` procedure.</span></span>  
  
 <span data-ttu-id="8ac19-104">Se o [instrução Set](../../../visual-basic/language-reference/statements/set-statement.md) é marcado com um acesso mais restritivo do nível em que seu [declaração de propriedade](../../../visual-basic/language-reference/statements/property-statement.md), uma tentativa de definir o valor da propriedade pode falhar nos seguintes casos:</span><span class="sxs-lookup"><span data-stu-id="8ac19-104">If the [Set Statement](../../../visual-basic/language-reference/statements/set-statement.md) is marked with a more restrictive access level than its [Property Statement](../../../visual-basic/language-reference/statements/property-statement.md), an attempt to set the property value could fail in the following cases:</span></span>  
  
-   <span data-ttu-id="8ac19-105">O `Set` instrução é marcada [particular](../../../visual-basic/language-reference/modifiers/private.md) e o código de chamada está fora da classe ou estrutura na qual a propriedade está definida.</span><span class="sxs-lookup"><span data-stu-id="8ac19-105">The `Set` statement is marked [Private](../../../visual-basic/language-reference/modifiers/private.md) and the calling code is outside the class or structure in which the property is defined.</span></span>  
  
-   <span data-ttu-id="8ac19-106">O `Set` instrução é marcada [protegido](../../../visual-basic/language-reference/modifiers/protected.md) e o código de chamada é não na classe ou estrutura na qual a propriedade é definida, nem em uma classe derivada.</span><span class="sxs-lookup"><span data-stu-id="8ac19-106">The `Set` statement is marked [Protected](../../../visual-basic/language-reference/modifiers/protected.md) and the calling code is not in the class or structure in which the property is defined, nor in a derived class.</span></span>  
  
-   <span data-ttu-id="8ac19-107">O `Set` instrução é marcada [amigo](../../../visual-basic/language-reference/modifiers/friend.md) e o código de chamada não está no mesmo assembly no qual a propriedade está definida.</span><span class="sxs-lookup"><span data-stu-id="8ac19-107">The `Set` statement is marked [Friend](../../../visual-basic/language-reference/modifiers/friend.md) and the calling code is not in the same assembly in which the property is defined.</span></span>  
  
 <span data-ttu-id="8ac19-108">**ID do erro:** BC31102</span><span class="sxs-lookup"><span data-stu-id="8ac19-108">**Error ID:** BC31102</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="8ac19-109">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="8ac19-109">To correct this error</span></span>  
  
-   <span data-ttu-id="8ac19-110">Se você tiver o controle do código-fonte definindo a propriedade, considere declarando o `Set` procedimento com o mesmo nível de acesso que a própria propriedade.</span><span class="sxs-lookup"><span data-stu-id="8ac19-110">If you have control of the source code defining the property, consider declaring the `Set` procedure with the same access level as the property itself.</span></span>  
  
-   <span data-ttu-id="8ac19-111">Se você não tem controle do código-fonte definindo a propriedade, você deve restringir o `Set` procedimento nível de acesso mais que a própria propriedade, tente mover a instrução que define o valor da propriedade para uma região de código que tem um melhor acesso à propriedade.</span><span class="sxs-lookup"><span data-stu-id="8ac19-111">If you do not have control of the source code defining the property, or you must restrict the `Set` procedure access level more than the property itself, try to move the statement that sets the property value to a region of code that has better access to the property.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8ac19-112">Consulte também</span><span class="sxs-lookup"><span data-stu-id="8ac19-112">See Also</span></span>  
 <span data-ttu-id="8ac19-113">[Procedimentos de propriedade](../../../visual-basic/programming-guide/language-features/procedures/property-procedures.md) </span><span class="sxs-lookup"><span data-stu-id="8ac19-113">[Property Procedures](../../../visual-basic/programming-guide/language-features/procedures/property-procedures.md) </span></span>  
<span data-ttu-id="8ac19-114"> [Como declarar uma propriedade com níveis de acesso mistos](../../../visual-basic/programming-guide/language-features/procedures/how-to-declare-a-property-with-mixed-access-levels.md)</span><span class="sxs-lookup"><span data-stu-id="8ac19-114"> [How to: Declare a Property with Mixed Access Levels](../../../visual-basic/programming-guide/language-features/procedures/how-to-declare-a-property-with-mixed-access-levels.md)</span></span>
