---
title: "Delegar a classe&lt;classname&gt;&quot; não tem nenhum método Invoke, portanto, uma expressão desse tipo não pode ser o destino de uma chamada de método | Documentos do Microsoft"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc30220
- bc30220
dev_langs:
- VB
helpviewer_keywords:
- BC30220
ms.assetid: 6be0d61c-f2f9-4f9b-ab90-8871a0d7206d
caps.latest.revision: 10
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
ms.openlocfilehash: 54cd62bc2b4cafa89873728ba4e5b31c46f1aab1
ms.contentlocale: pt-br
ms.lasthandoff: 04/12/2017

---
# <a name="delegate-class-39ltclassnamegt39-has-no-invoke-method-so-an-expression-of-this-type-cannot-be-the-target-of-a-method-call"></a><span data-ttu-id="00ef4-102">Delegar a classe&lt;classname&gt;' não tem nenhum método Invoke, portanto, uma expressão desse tipo não pode ser o destino de uma chamada de método</span><span class="sxs-lookup"><span data-stu-id="00ef4-102">Delegate class &#39;&lt;classname&gt;&#39; has no Invoke method, so an expression of this type cannot be the target of a method call</span></span>
<span data-ttu-id="00ef4-103">Uma chamada para `Invoke` através de um delegado falhou porque `Invoke` não está implementado na classe de delegado.</span><span class="sxs-lookup"><span data-stu-id="00ef4-103">A call to `Invoke` through a delegate has failed because `Invoke` is not implemented on the delegate class.</span></span>  
  
 <span data-ttu-id="00ef4-104">**ID do erro:** BC30220</span><span class="sxs-lookup"><span data-stu-id="00ef4-104">**Error ID:** BC30220</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="00ef4-105">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="00ef4-105">To correct this error</span></span>  
  
1.  <span data-ttu-id="00ef4-106">Certifique-se de que uma instância da classe delegada foi criada com uma `Dim` de instrução e que um procedimento foi designado para o exemplo delegado com o `AddressOf` operador.</span><span class="sxs-lookup"><span data-stu-id="00ef4-106">Ensure that an instance of the delegate class has been created with a `Dim` statement and that a procedure has been assigned to the delegate instance with the `AddressOf` operator.</span></span>  
  
2.  <span data-ttu-id="00ef4-107">Localize o código que implementa a classe delegada e certifique-se de que ela implemente o `Invoke` procedimento.</span><span class="sxs-lookup"><span data-stu-id="00ef4-107">Locate the code that implements the delegate class and make sure it implements the `Invoke` procedure.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="00ef4-108">Consulte também</span><span class="sxs-lookup"><span data-stu-id="00ef4-108">See Also</span></span>  
 <span data-ttu-id="00ef4-109">[Delegados](../../../visual-basic/programming-guide/language-features/delegates/index.md) </span><span class="sxs-lookup"><span data-stu-id="00ef4-109">[Delegates](../../../visual-basic/programming-guide/language-features/delegates/index.md) </span></span>  
<span data-ttu-id="00ef4-110"> [Instrução delegate](../../../visual-basic/language-reference/statements/delegate-statement.md) </span><span class="sxs-lookup"><span data-stu-id="00ef4-110"> [Delegate Statement](../../../visual-basic/language-reference/statements/delegate-statement.md) </span></span>  
<span data-ttu-id="00ef4-111"> [Operador AddressOf](../../../visual-basic/language-reference/operators/addressof-operator.md) </span><span class="sxs-lookup"><span data-stu-id="00ef4-111"> [AddressOf Operator](../../../visual-basic/language-reference/operators/addressof-operator.md) </span></span>  
<span data-ttu-id="00ef4-112"> [Instrução Dim](../../../visual-basic/language-reference/statements/dim-statement.md)</span><span class="sxs-lookup"><span data-stu-id="00ef4-112"> [Dim Statement](../../../visual-basic/language-reference/statements/dim-statement.md)</span></span>
