---
title: "Acessor &quot; get&quot; da propriedade &quot;&lt;propertyname&gt;&quot; não está acessível | Documentos do Microsoft"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc31103
- bc31103
dev_langs:
- VB
helpviewer_keywords:
- BC31103
ms.assetid: 3c346c32-7669-4b04-841d-7a9df9cb703e
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
ms.openlocfilehash: 5c8dab2ce2c55405361db0200de3a24462782b6a
ms.contentlocale: pt-br
ms.lasthandoff: 04/12/2017

---
# <a name="39get39-accessor-of-property-39ltpropertynamegt39-is-not-accessible"></a><span data-ttu-id="dae17-102">Acessor ' get' da propriedade '&lt;propertyname&gt;' não está acessível</span><span class="sxs-lookup"><span data-stu-id="dae17-102">&#39;Get&#39; accessor of property &#39;&lt;propertyname&gt;&#39; is not accessible</span></span>
<span data-ttu-id="dae17-103">Uma declaração tenta recuperar o valor de uma propriedade quando ela não tem acesso à propriedade `Get` procedimento.</span><span class="sxs-lookup"><span data-stu-id="dae17-103">A statement attempts to retrieve the value of a property when it does not have access to the property's `Get` procedure.</span></span>  
  
 <span data-ttu-id="dae17-104">Se o [instrução Get](../../../visual-basic/language-reference/statements/get-statement.md) é marcado com um acesso mais restritivo do nível em que seu [declaração de propriedade](../../../visual-basic/language-reference/statements/property-statement.md), uma tentativa de ler o valor da propriedade pode falhar nos seguintes casos:</span><span class="sxs-lookup"><span data-stu-id="dae17-104">If the [Get Statement](../../../visual-basic/language-reference/statements/get-statement.md) is marked with a more restrictive access level than its [Property Statement](../../../visual-basic/language-reference/statements/property-statement.md), an attempt to read the property value could fail in the following cases:</span></span>  
  
-   <span data-ttu-id="dae17-105">O `Get` instrução é marcada [particular](../../../visual-basic/language-reference/modifiers/private.md) e o código de chamada está fora da classe ou estrutura na qual a propriedade está definida.</span><span class="sxs-lookup"><span data-stu-id="dae17-105">The `Get` statement is marked [Private](../../../visual-basic/language-reference/modifiers/private.md) and the calling code is outside the class or structure in which the property is defined.</span></span>  
  
-   <span data-ttu-id="dae17-106">O `Get` instrução é marcada [protegido](../../../visual-basic/language-reference/modifiers/protected.md) e o código de chamada é não na classe ou estrutura na qual a propriedade é definida, nem em uma classe derivada.</span><span class="sxs-lookup"><span data-stu-id="dae17-106">The `Get` statement is marked [Protected](../../../visual-basic/language-reference/modifiers/protected.md) and the calling code is not in the class or structure in which the property is defined, nor in a derived class.</span></span>  
  
-   <span data-ttu-id="dae17-107">O `Get` instrução é marcada [amigo](../../../visual-basic/language-reference/modifiers/friend.md) e o código de chamada não está no mesmo assembly no qual a propriedade está definida.</span><span class="sxs-lookup"><span data-stu-id="dae17-107">The `Get` statement is marked [Friend](../../../visual-basic/language-reference/modifiers/friend.md) and the calling code is not in the same assembly in which the property is defined.</span></span>  
  
 <span data-ttu-id="dae17-108">**ID do erro:** BC31103</span><span class="sxs-lookup"><span data-stu-id="dae17-108">**Error ID:** BC31103</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="dae17-109">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="dae17-109">To correct this error</span></span>  
  
-   <span data-ttu-id="dae17-110">Se você tiver o controle do código-fonte definindo a propriedade, considere declarando o `Get` procedimento com o mesmo nível de acesso que a própria propriedade.</span><span class="sxs-lookup"><span data-stu-id="dae17-110">If you have control of the source code defining the property, consider declaring the `Get` procedure with the same access level as the property itself.</span></span>  
  
-   <span data-ttu-id="dae17-111">Se você não tem controle do código-fonte definindo a propriedade, você deve restringir o `Get` procedimento nível de acesso mais que a própria propriedade, tente mover a declaração que lê o valor da propriedade para uma região de código que tem um melhor acesso à propriedade.</span><span class="sxs-lookup"><span data-stu-id="dae17-111">If you do not have control of the source code defining the property, or you must restrict the `Get` procedure access level more than the property itself, try to move the statement that reads the property value to a region of code that has better access to the property.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dae17-112">Consulte também</span><span class="sxs-lookup"><span data-stu-id="dae17-112">See Also</span></span>  
 <span data-ttu-id="dae17-113">[Procedimentos de propriedade](../../../visual-basic/programming-guide/language-features/procedures/property-procedures.md) </span><span class="sxs-lookup"><span data-stu-id="dae17-113">[Property Procedures](../../../visual-basic/programming-guide/language-features/procedures/property-procedures.md) </span></span>  
<span data-ttu-id="dae17-114"> [Como declarar uma propriedade com níveis de acesso mistos](../../../visual-basic/programming-guide/language-features/procedures/how-to-declare-a-property-with-mixed-access-levels.md)</span><span class="sxs-lookup"><span data-stu-id="dae17-114"> [How to: Declare a Property with Mixed Access Levels](../../../visual-basic/programming-guide/language-features/procedures/how-to-declare-a-property-with-mixed-access-levels.md)</span></span>
