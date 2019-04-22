---
title: Cláusula Of (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- Of
- vb.Of
- vb.of
helpviewer_keywords:
- Of keyword [Visual Basic]
- arguments [Visual Basic], data types
- constraints, Visual Basic generic types
- generic parameters
- generics [Visual Basic], constraints
- parameters [Visual Basic], type
- types [Visual Basic], generic
- parameters [Visual Basic], generic
- type parameters
- data type arguments
ms.assetid: 0db8f65c-65af-4089-ab7f-6fcfecb60444
ms.openlocfilehash: 880570c714292b0c11eef4e2cd4c4b410bb075f1
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "58823435"
---
# <a name="of-clause-visual-basic"></a><span data-ttu-id="76631-102">Cláusula Of (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="76631-102">Of Clause (Visual Basic)</span></span>
<span data-ttu-id="76631-103">Apresenta uma `Of` cláusula, que identifica uma *parâmetro de tipo* em uma *genérico* classe, estrutura, interface, delegado ou procedimento.</span><span class="sxs-lookup"><span data-stu-id="76631-103">Introduces an `Of` clause, which identifies a *type parameter* on a *generic* class, structure, interface, delegate, or procedure.</span></span> <span data-ttu-id="76631-104">Para obter informações sobre tipos genéricos, consulte [tipos genéricos no Visual Basic](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md).</span><span class="sxs-lookup"><span data-stu-id="76631-104">For information on generic types, see [Generic Types in Visual Basic](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md).</span></span>  
  
## <a name="using-the-of-keyword"></a><span data-ttu-id="76631-105">Usando a palavra-chave</span><span class="sxs-lookup"><span data-stu-id="76631-105">Using the Of Keyword</span></span>  
 <span data-ttu-id="76631-106">O seguinte exemplo de código usa o `Of` palavra-chave para definir o contorno de uma classe que usa dois parâmetros de tipo.</span><span class="sxs-lookup"><span data-stu-id="76631-106">The following code example uses the `Of` keyword to define the outline of a class that takes two type parameters.</span></span> <span data-ttu-id="76631-107">Ele *restringe* o `keyType` parâmetro com o <xref:System.IComparable> interface, o que significa que o código de consumo deve fornecer um argumento de tipo que implementa <xref:System.IComparable>.</span><span class="sxs-lookup"><span data-stu-id="76631-107">It *constrains* the `keyType` parameter by the <xref:System.IComparable> interface, which means the consuming code must supply a type argument that implements <xref:System.IComparable>.</span></span> <span data-ttu-id="76631-108">Isso é necessário para que o `add` procedimento pode chamar o <xref:System.IComparable.CompareTo%2A?displayProperty=nameWithType> método.</span><span class="sxs-lookup"><span data-stu-id="76631-108">This is necessary so that the `add` procedure can call the <xref:System.IComparable.CompareTo%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="76631-109">Para obter mais informações sobre restrições, consulte [lista de tipos](../../../visual-basic/language-reference/statements/type-list.md).</span><span class="sxs-lookup"><span data-stu-id="76631-109">For more information on constraints, see [Type List](../../../visual-basic/language-reference/statements/type-list.md).</span></span>  
  
```  
Public Class Dictionary(Of entryType, keyType As IComparable)  
    Public Sub add(ByVal e As entryType, ByVal k As keyType)  
        Dim dk As keyType  
        If k.CompareTo(dk) = 0 Then  
        End If  
    End Sub  
    Public Function find(ByVal k As keyType) As entryType  
    End Function  
End Class  
```  
  
 <span data-ttu-id="76631-110">Se você concluir a definição de classe anterior, você pode construir uma variedade de `dictionary` classes dele.</span><span class="sxs-lookup"><span data-stu-id="76631-110">If you complete the preceding class definition, you can construct a variety of `dictionary` classes from it.</span></span> <span data-ttu-id="76631-111">Os tipos que você fornece ao `entryType` e `keyType` determinar que tipo de entrada a classe contém e o tipo de chave associa a cada entrada.</span><span class="sxs-lookup"><span data-stu-id="76631-111">The types you supply to `entryType` and `keyType` determine what type of entry the class holds and what type of key it associates with each entry.</span></span> <span data-ttu-id="76631-112">Por causa da restrição, você deve fornecer a `keyType` um tipo que implementa <xref:System.IComparable>.</span><span class="sxs-lookup"><span data-stu-id="76631-112">Because of the constraint, you must supply to `keyType` a type that implements <xref:System.IComparable>.</span></span>  
  
 <span data-ttu-id="76631-113">O exemplo de código a seguir cria um objeto que retém `String` entradas e associa um `Integer` chave com cada um deles.</span><span class="sxs-lookup"><span data-stu-id="76631-113">The following code example creates an object that holds `String` entries and associates an `Integer` key with each one.</span></span> <span data-ttu-id="76631-114">`Integer` implementa <xref:System.IComparable> e, portanto, satisfaz a restrição em `keyType`.</span><span class="sxs-lookup"><span data-stu-id="76631-114">`Integer` implements <xref:System.IComparable> and therefore satisfies the constraint on `keyType`.</span></span>  
  
```  
Dim d As New dictionary(Of String, Integer)  
```  
  
 <span data-ttu-id="76631-115">O `Of` palavra-chave pode ser usada nesses contextos:</span><span class="sxs-lookup"><span data-stu-id="76631-115">The `Of` keyword can be used in these contexts:</span></span>  
  
 [<span data-ttu-id="76631-116">Instrução Class</span><span class="sxs-lookup"><span data-stu-id="76631-116">Class Statement</span></span>](../../../visual-basic/language-reference/statements/class-statement.md)  
  
 [<span data-ttu-id="76631-117">Instrução Delegate</span><span class="sxs-lookup"><span data-stu-id="76631-117">Delegate Statement</span></span>](../../../visual-basic/language-reference/statements/delegate-statement.md)  
  
 [<span data-ttu-id="76631-118">Instrução Function</span><span class="sxs-lookup"><span data-stu-id="76631-118">Function Statement</span></span>](../../../visual-basic/language-reference/statements/function-statement.md)  
  
 [<span data-ttu-id="76631-119">Instrução Interface</span><span class="sxs-lookup"><span data-stu-id="76631-119">Interface Statement</span></span>](../../../visual-basic/language-reference/statements/interface-statement.md)  
  
 [<span data-ttu-id="76631-120">Instrução Structure</span><span class="sxs-lookup"><span data-stu-id="76631-120">Structure Statement</span></span>](../../../visual-basic/language-reference/statements/structure-statement.md)  
  
 [<span data-ttu-id="76631-121">Instrução Sub</span><span class="sxs-lookup"><span data-stu-id="76631-121">Sub Statement</span></span>](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
## <a name="see-also"></a><span data-ttu-id="76631-122">Consulte também</span><span class="sxs-lookup"><span data-stu-id="76631-122">See also</span></span>

- <xref:System.IComparable>
- [<span data-ttu-id="76631-123">Lista de Tipos</span><span class="sxs-lookup"><span data-stu-id="76631-123">Type List</span></span>](../../../visual-basic/language-reference/statements/type-list.md)
- [<span data-ttu-id="76631-124">Tipos genéricos no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="76631-124">Generic Types in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)
- [<span data-ttu-id="76631-125">In</span><span class="sxs-lookup"><span data-stu-id="76631-125">In</span></span>](../../../visual-basic/language-reference/modifiers/in-generic-modifier.md)
- [<span data-ttu-id="76631-126">Saída</span><span class="sxs-lookup"><span data-stu-id="76631-126">Out</span></span>](../../../visual-basic/language-reference/modifiers/out-generic-modifier.md)
