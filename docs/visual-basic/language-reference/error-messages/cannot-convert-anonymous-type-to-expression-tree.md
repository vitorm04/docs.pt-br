---
title: Não é possível converter tipo anônimo em árvore de expressão porque ele contém um campo usado na inicialização de outro campo
ms.date: 07/20/2015
f1_keywords:
- bc36548
- vbc36548
helpviewer_keywords:
- BC36548
ms.assetid: 27de068f-080e-4160-86bf-1ec23fd1925a
ms.openlocfilehash: a6ddbaa358709fe306f1529112d1f2bd0a715a91
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54646935"
---
# <a name="cannot-convert-anonymous-type-to-expression-tree-because-it-contains-a-field-that-is-used-in-the-initialization-of-another-field"></a><span data-ttu-id="29178-102">Não é possível converter tipo anônimo em árvore de expressão porque ele contém um campo usado na inicialização de outro campo</span><span class="sxs-lookup"><span data-stu-id="29178-102">Cannot convert anonymous type to expression tree because it contains a field that is used in the initialization of another field</span></span>
<span data-ttu-id="29178-103">O compilador não aceita a conversão de um anônimo em uma árvore de expressão quando uma propriedade do tipo anônimo é usada para inicializar outra propriedade do tipo anônimo.</span><span class="sxs-lookup"><span data-stu-id="29178-103">The compiler does not accept conversion of an anonymous to an expression tree when one property of the anonymous type is used to initialize another property of the anonymous type.</span></span> <span data-ttu-id="29178-104">Por exemplo, no código a seguir, `Prop1` é declarado na lista de inicialização e, em seguida, usado como o valor inicial para `Prop2`.</span><span class="sxs-lookup"><span data-stu-id="29178-104">For example, in the following code, `Prop1` is declared in the initialization list and then used as the initial value for `Prop2`.</span></span>  
  
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
  
 <span data-ttu-id="29178-105">**ID do erro:** BC36548</span><span class="sxs-lookup"><span data-stu-id="29178-105">**Error ID:** BC36548</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="29178-106">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="29178-106">To correct this error</span></span>  
  
-   <span data-ttu-id="29178-107">Atribua o valor inicial para `Prop1` a uma variável local.</span><span class="sxs-lookup"><span data-stu-id="29178-107">Assign the initial value for `Prop1` to a local variable.</span></span> <span data-ttu-id="29178-108">Atribuir a variável a ambos `Prop1` e `Prop2`, conforme mostrado no código a seguir.</span><span class="sxs-lookup"><span data-stu-id="29178-108">Assign that variable to both `Prop1` and `Prop2`, as shown in the following code.</span></span>  
  
    ```  
    Sub Main()  
  
        Dim temp = 2  
        ExpressionExample(Function() New With {.Prop1 = temp, .Prop2 = temp})  
  
    End Sub  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="29178-109">Consulte também</span><span class="sxs-lookup"><span data-stu-id="29178-109">See also</span></span>

- [<span data-ttu-id="29178-110">Tipos anônimos (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="29178-110">Anonymous Types (Visual Basic)</span></span>](../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)
- [<span data-ttu-id="29178-111">Árvores de expressão (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="29178-111">Expression Trees (Visual Basic)</span></span>](../../programming-guide/concepts/expression-trees/index.md)
- [<span data-ttu-id="29178-112">Como: Usar árvores de expressão para compilar consultas dinâmicas (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="29178-112">How to: Use Expression Trees to Build Dynamic Queries (Visual Basic)</span></span>](../../programming-guide/concepts/expression-trees/how-to-use-expression-trees-to-build-dynamic-queries.md)
