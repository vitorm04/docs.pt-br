---
title: "&#39; Definir &#39; acessador de propriedade &#39; &lt;propertyname&gt;&#39; não está acessível"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc31102
- bc31102
helpviewer_keywords: BC31102
ms.assetid: 6f7b31b7-3656-4ae1-8851-90f5f4c6950a
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 9256a09b719ad3890e1d7c2cc23ffb0d40eec62f
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="39set39-accessor-of-property-39ltpropertynamegt39-is-not-accessible"></a><span data-ttu-id="f03ad-102">&#39; Definir &#39; acessador de propriedade &#39; &lt;propertyname&gt;&#39; não está acessível</span><span class="sxs-lookup"><span data-stu-id="f03ad-102">&#39;Set&#39; accessor of property &#39;&lt;propertyname&gt;&#39; is not accessible</span></span>
<span data-ttu-id="f03ad-103">Uma declaração tenta recuperar o valor de uma propriedade quando ela não tem acesso para a propriedade `Set` procedimento.</span><span class="sxs-lookup"><span data-stu-id="f03ad-103">A statement attempts to store the value of a property when it does not have access to the property's `Set` procedure.</span></span>  
  
 <span data-ttu-id="f03ad-104">Se o [instrução Set](../../../visual-basic/language-reference/statements/set-statement.md) está marcado com um acesso mais restritivo do nível em que seu [declaração de propriedade](../../../visual-basic/language-reference/statements/property-statement.md), uma tentativa de definir o valor da propriedade pode falhar nos seguintes casos:</span><span class="sxs-lookup"><span data-stu-id="f03ad-104">If the [Set Statement](../../../visual-basic/language-reference/statements/set-statement.md) is marked with a more restrictive access level than its [Property Statement](../../../visual-basic/language-reference/statements/property-statement.md), an attempt to set the property value could fail in the following cases:</span></span>  
  
-   <span data-ttu-id="f03ad-105">O `Set` instrução está marcado como [privada](../../../visual-basic/language-reference/modifiers/private.md) e o código de chamada está fora da classe ou estrutura na qual a propriedade está definida.</span><span class="sxs-lookup"><span data-stu-id="f03ad-105">The `Set` statement is marked [Private](../../../visual-basic/language-reference/modifiers/private.md) and the calling code is outside the class or structure in which the property is defined.</span></span>  
  
-   <span data-ttu-id="f03ad-106">O `Set` instrução está marcado como [protegidos](../../../visual-basic/language-reference/modifiers/protected.md) e o código de chamada é não na classe ou estrutura na qual a propriedade é definida, nem em uma classe derivada.</span><span class="sxs-lookup"><span data-stu-id="f03ad-106">The `Set` statement is marked [Protected](../../../visual-basic/language-reference/modifiers/protected.md) and the calling code is not in the class or structure in which the property is defined, nor in a derived class.</span></span>  
  
-   <span data-ttu-id="f03ad-107">O `Set` instrução está marcado como [Friend](../../../visual-basic/language-reference/modifiers/friend.md) e o código de chamada não está no mesmo assembly no qual a propriedade está definida.</span><span class="sxs-lookup"><span data-stu-id="f03ad-107">The `Set` statement is marked [Friend](../../../visual-basic/language-reference/modifiers/friend.md) and the calling code is not in the same assembly in which the property is defined.</span></span>  
  
 <span data-ttu-id="f03ad-108">**ID do erro:** BC31102</span><span class="sxs-lookup"><span data-stu-id="f03ad-108">**Error ID:** BC31102</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="f03ad-109">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="f03ad-109">To correct this error</span></span>  
  
-   <span data-ttu-id="f03ad-110">Se você tiver o controle do código-fonte definindo a propriedade, considere declarando o `Set` procedimento com o mesmo nível de acesso da propriedade.</span><span class="sxs-lookup"><span data-stu-id="f03ad-110">If you have control of the source code defining the property, consider declaring the `Set` procedure with the same access level as the property itself.</span></span>  
  
-   <span data-ttu-id="f03ad-111">Se você não tem controle do código-fonte definindo a propriedade, você deve restringir o `Set` procedimento nível de acesso mais que a própria propriedade, tente mover a declaração que define o valor da propriedade a uma região de código que tem um acesso melhor para o propriedade.</span><span class="sxs-lookup"><span data-stu-id="f03ad-111">If you do not have control of the source code defining the property, or you must restrict the `Set` procedure access level more than the property itself, try to move the statement that sets the property value to a region of code that has better access to the property.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f03ad-112">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f03ad-112">See Also</span></span>  
 [<span data-ttu-id="f03ad-113">Procedimentos de Propriedade</span><span class="sxs-lookup"><span data-stu-id="f03ad-113">Property Procedures</span></span>](../../../visual-basic/programming-guide/language-features/procedures/property-procedures.md)  
 [<span data-ttu-id="f03ad-114">Como declarar uma propriedade com níveis de acesso mistos</span><span class="sxs-lookup"><span data-stu-id="f03ad-114">How to: Declare a Property with Mixed Access Levels</span></span>](../../../visual-basic/programming-guide/language-features/procedures/how-to-declare-a-property-with-mixed-access-levels.md)
