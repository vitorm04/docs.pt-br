---
title: Não é possível converter tipo anônimo em árvore de expressão porque ele contém um campo usado na inicialização de outro campo
ms.date: 07/20/2015
f1_keywords:
- bc36548
- vbc36548
helpviewer_keywords:
- BC36548
ms.assetid: 27de068f-080e-4160-86bf-1ec23fd1925a
ms.openlocfilehash: d43f6ef19591af326d06a4ce21194d8f9fa58c2b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33585470"
---
# <a name="cannot-convert-anonymous-type-to-expression-tree-because-it-contains-a-field-that-is-used-in-the-initialization-of-another-field"></a><span data-ttu-id="e37d7-102">Não é possível converter tipo anônimo em árvore de expressão porque ele contém um campo usado na inicialização de outro campo</span><span class="sxs-lookup"><span data-stu-id="e37d7-102">Cannot convert anonymous type to expression tree because it contains a field that is used in the initialization of another field</span></span>
<span data-ttu-id="e37d7-103">O compilador não aceitar a conversão de um anônimo em uma árvore de expressão quando uma propriedade do tipo anônimo é usada para inicializar outra propriedade do tipo anônimo.</span><span class="sxs-lookup"><span data-stu-id="e37d7-103">The compiler does not accept conversion of an anonymous to an expression tree when one property of the anonymous type is used to initialize another property of the anonymous type.</span></span> <span data-ttu-id="e37d7-104">Por exemplo, no código a seguir, `Prop1` é declarado na lista de inicialização e, em seguida, usado como o valor inicial de `Prop2`.</span><span class="sxs-lookup"><span data-stu-id="e37d7-104">For example, in the following code, `Prop1` is declared in the initialization list and then used as the initial value for `Prop2`.</span></span>  
  
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
  
 <span data-ttu-id="e37d7-105">**ID do erro:** BC36548</span><span class="sxs-lookup"><span data-stu-id="e37d7-105">**Error ID:** BC36548</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="e37d7-106">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="e37d7-106">To correct this error</span></span>  
  
-   <span data-ttu-id="e37d7-107">Atribuir o valor inicial de `Prop1` a uma variável local.</span><span class="sxs-lookup"><span data-stu-id="e37d7-107">Assign the initial value for `Prop1` to a local variable.</span></span> <span data-ttu-id="e37d7-108">Atribuir a variável a ambos `Prop1` e `Prop2`, conforme mostrado no código a seguir.</span><span class="sxs-lookup"><span data-stu-id="e37d7-108">Assign that variable to both `Prop1` and `Prop2`, as shown in the following code.</span></span>  
  
    ```  
    Sub Main()  
  
        Dim temp = 2  
        ExpressionExample(Function() New With {.Prop1 = temp, .Prop2 = temp})  
  
    End Sub  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="e37d7-109">Consulte também</span><span class="sxs-lookup"><span data-stu-id="e37d7-109">See Also</span></span>  
 [<span data-ttu-id="e37d7-110">Tipos Anônimos</span><span class="sxs-lookup"><span data-stu-id="e37d7-110">Anonymous Types</span></span>](../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)  
 [<span data-ttu-id="e37d7-111">Árvores de Expressão</span><span class="sxs-lookup"><span data-stu-id="e37d7-111">Expression Trees</span></span>](http://msdn.microsoft.com/library/fb1d3ed8-d5b0-4211-a71f-dd271529294b)  
 [<span data-ttu-id="e37d7-112">Como usar árvores de expressão para compilar consultas dinâmicas</span><span class="sxs-lookup"><span data-stu-id="e37d7-112">How to: Use Expression Trees to Build Dynamic Queries</span></span>](http://msdn.microsoft.com/library/1e37e0cc-eef3-48bb-8b69-3adabf322735)
