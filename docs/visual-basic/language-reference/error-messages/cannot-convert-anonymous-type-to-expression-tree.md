---
title: "Não é possível converter tipo anônimo em árvore de expressão porque ele contém um campo que é usado na inicialização de outro campo | Documentos do Microsoft"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- bc36548
- vbc36548
dev_langs:
- VB
helpviewer_keywords:
- BC36548
ms.assetid: 27de068f-080e-4160-86bf-1ec23fd1925a
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
ms.openlocfilehash: aa12d35db0144ac3504bcc8297a24023f5a8751f
ms.contentlocale: pt-br
ms.lasthandoff: 04/12/2017

---
# <a name="cannot-convert-anonymous-type-to-expression-tree-because-it-contains-a-field-that-is-used-in-the-initialization-of-another-field"></a><span data-ttu-id="196b9-102">Não é possível converter tipo anônimo em árvore de expressão porque ele contém um campo usado na inicialização de outro campo</span><span class="sxs-lookup"><span data-stu-id="196b9-102">Cannot convert anonymous type to expression tree because it contains a field that is used in the initialization of another field</span></span>
<span data-ttu-id="196b9-103">O compilador não aceita conversão de um anônimo em uma árvore de expressão quando uma propriedade do tipo anônimo é usada para inicializar outra propriedade do tipo anônimo.</span><span class="sxs-lookup"><span data-stu-id="196b9-103">The compiler does not accept conversion of an anonymous to an expression tree when one property of the anonymous type is used to initialize another property of the anonymous type.</span></span> <span data-ttu-id="196b9-104">Por exemplo, no código a seguir, `Prop1` é declarado na lista de inicialização e, em seguida, usado como o valor inicial para `Prop2`.</span><span class="sxs-lookup"><span data-stu-id="196b9-104">For example, in the following code, `Prop1` is declared in the initialization list and then used as the initial value for `Prop2`.</span></span>  
  
```vb  
Module M2  
  
    Sub ExpressionExample(Of T)(ByVal x As Expressions.Expression(Of Func(Of T)))  
    End Sub  
  
    Sub Main()  
        ' The following line causes the error.  
        ' ExpressionExample(Function() New With {.Prop1 = 2, .Prop2 = .Prop1})  
  
    End Sub  
End Module  
```  
  
 <span data-ttu-id="196b9-105">**ID do erro:** BC36548</span><span class="sxs-lookup"><span data-stu-id="196b9-105">**Error ID:** BC36548</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="196b9-106">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="196b9-106">To correct this error</span></span>  
  
-   <span data-ttu-id="196b9-107">Atribua o valor inicial para `Prop1` a uma variável local.</span><span class="sxs-lookup"><span data-stu-id="196b9-107">Assign the initial value for `Prop1` to a local variable.</span></span> <span data-ttu-id="196b9-108">Atribuir a variável a ambos `Prop1` e `Prop2`, conforme mostrado no código a seguir.</span><span class="sxs-lookup"><span data-stu-id="196b9-108">Assign that variable to both `Prop1` and `Prop2`, as shown in the following code.</span></span>  
  
    ```  
    Sub Main()  
  
        Dim temp = 2  
        ExpressionExample(Function() New With {.Prop1 = temp, .Prop2 = temp})  
  
    End Sub  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="196b9-109">Consulte também</span><span class="sxs-lookup"><span data-stu-id="196b9-109">See Also</span></span>  
 <span data-ttu-id="196b9-110">[Tipos anônimos](../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md) </span><span class="sxs-lookup"><span data-stu-id="196b9-110">[Anonymous Types](../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md) </span></span>  
<span data-ttu-id="196b9-111"> [Árvores de expressão](http://msdn.microsoft.com/library/fb1d3ed8-d5b0-4211-a71f-dd271529294b) </span><span class="sxs-lookup"><span data-stu-id="196b9-111"> [Expression Trees](http://msdn.microsoft.com/library/fb1d3ed8-d5b0-4211-a71f-dd271529294b) </span></span>  
<span data-ttu-id="196b9-112"> [Como usar árvores de expressão para compilar consultas dinâmicas](http://msdn.microsoft.com/library/1e37e0cc-eef3-48bb-8b69-3adabf322735)</span><span class="sxs-lookup"><span data-stu-id="196b9-112"> [How to: Use Expression Trees to Build Dynamic Queries](http://msdn.microsoft.com/library/1e37e0cc-eef3-48bb-8b69-3adabf322735)</span></span>
