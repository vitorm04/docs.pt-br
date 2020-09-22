---
title: Cláusula Of
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
ms.openlocfilehash: 0595356fb75fc0ac73a49622d71fe1d28fa7b648
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90865901"
---
# <a name="of-clause-visual-basic"></a><span data-ttu-id="459bf-102">Cláusula Of (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="459bf-102">Of Clause (Visual Basic)</span></span>

<span data-ttu-id="459bf-103">Apresenta uma `Of` cláusula, que identifica um *parâmetro de tipo* em uma classe *genérica* , estrutura, interface, delegado ou procedimento.</span><span class="sxs-lookup"><span data-stu-id="459bf-103">Introduces an `Of` clause, which identifies a *type parameter* on a *generic* class, structure, interface, delegate, or procedure.</span></span> <span data-ttu-id="459bf-104">Para obter informações sobre tipos genéricos, consulte [tipos genéricos em Visual Basic](../../programming-guide/language-features/data-types/generic-types.md).</span><span class="sxs-lookup"><span data-stu-id="459bf-104">For information on generic types, see [Generic Types in Visual Basic](../../programming-guide/language-features/data-types/generic-types.md).</span></span>  
  
## <a name="using-the-of-keyword"></a><span data-ttu-id="459bf-105">Usando a palavra-chave of</span><span class="sxs-lookup"><span data-stu-id="459bf-105">Using the Of Keyword</span></span>  

 <span data-ttu-id="459bf-106">O exemplo de código a seguir usa a `Of` palavra-chave para definir o contorno de uma classe que usa dois parâmetros de tipo.</span><span class="sxs-lookup"><span data-stu-id="459bf-106">The following code example uses the `Of` keyword to define the outline of a class that takes two type parameters.</span></span> <span data-ttu-id="459bf-107">Ele *restringe* o `keyType` parâmetro pela <xref:System.IComparable> interface, o que significa que o código de consumo deve fornecer um argumento de tipo que implementa <xref:System.IComparable> .</span><span class="sxs-lookup"><span data-stu-id="459bf-107">It *constrains* the `keyType` parameter by the <xref:System.IComparable> interface, which means the consuming code must supply a type argument that implements <xref:System.IComparable>.</span></span> <span data-ttu-id="459bf-108">Isso é necessário para que o `add` procedimento possa chamar o <xref:System.IComparable.CompareTo%2A?displayProperty=nameWithType> método.</span><span class="sxs-lookup"><span data-stu-id="459bf-108">This is necessary so that the `add` procedure can call the <xref:System.IComparable.CompareTo%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="459bf-109">Para obter mais informações sobre restrições, consulte [lista de tipos](type-list.md).</span><span class="sxs-lookup"><span data-stu-id="459bf-109">For more information on constraints, see [Type List](type-list.md).</span></span>  
  
```vb  
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
  
 <span data-ttu-id="459bf-110">Se você concluir a definição de classe anterior, poderá construir uma variedade de `dictionary` classes a partir dela.</span><span class="sxs-lookup"><span data-stu-id="459bf-110">If you complete the preceding class definition, you can construct a variety of `dictionary` classes from it.</span></span> <span data-ttu-id="459bf-111">Os tipos que você fornece `entryType` e `keyType` determinam que tipo de entrada a classe contém e que tipo de chave ela associa a cada entrada.</span><span class="sxs-lookup"><span data-stu-id="459bf-111">The types you supply to `entryType` and `keyType` determine what type of entry the class holds and what type of key it associates with each entry.</span></span> <span data-ttu-id="459bf-112">Devido à restrição, você deve fornecer a `keyType` um tipo que implementa <xref:System.IComparable> .</span><span class="sxs-lookup"><span data-stu-id="459bf-112">Because of the constraint, you must supply to `keyType` a type that implements <xref:System.IComparable>.</span></span>  
  
 <span data-ttu-id="459bf-113">O exemplo de código a seguir cria um objeto que contém `String` entradas e associa uma `Integer` chave a cada uma delas.</span><span class="sxs-lookup"><span data-stu-id="459bf-113">The following code example creates an object that holds `String` entries and associates an `Integer` key with each one.</span></span> <span data-ttu-id="459bf-114">`Integer` implementa <xref:System.IComparable> e, portanto, satisfaz a restrição em `keyType` .</span><span class="sxs-lookup"><span data-stu-id="459bf-114">`Integer` implements <xref:System.IComparable> and therefore satisfies the constraint on `keyType`.</span></span>  
  
```vb  
Dim d As New dictionary(Of String, Integer)  
```  
  
 <span data-ttu-id="459bf-115">A `Of` palavra-chave pode ser usada nesses contextos:</span><span class="sxs-lookup"><span data-stu-id="459bf-115">The `Of` keyword can be used in these contexts:</span></span>  
  
 [<span data-ttu-id="459bf-116">Instrução Class</span><span class="sxs-lookup"><span data-stu-id="459bf-116">Class Statement</span></span>](class-statement.md)  
  
 [<span data-ttu-id="459bf-117">Instrução Delegate</span><span class="sxs-lookup"><span data-stu-id="459bf-117">Delegate Statement</span></span>](delegate-statement.md)  
  
 [<span data-ttu-id="459bf-118">Instrução Function</span><span class="sxs-lookup"><span data-stu-id="459bf-118">Function Statement</span></span>](function-statement.md)  
  
 [<span data-ttu-id="459bf-119">Instrução Interface</span><span class="sxs-lookup"><span data-stu-id="459bf-119">Interface Statement</span></span>](interface-statement.md)  
  
 [<span data-ttu-id="459bf-120">Instrução Structure</span><span class="sxs-lookup"><span data-stu-id="459bf-120">Structure Statement</span></span>](structure-statement.md)  
  
 [<span data-ttu-id="459bf-121">Instrução Sub</span><span class="sxs-lookup"><span data-stu-id="459bf-121">Sub Statement</span></span>](sub-statement.md)  
  
## <a name="see-also"></a><span data-ttu-id="459bf-122">Confira também</span><span class="sxs-lookup"><span data-stu-id="459bf-122">See also</span></span>

- <xref:System.IComparable>
- [<span data-ttu-id="459bf-123">Lista de Tipos</span><span class="sxs-lookup"><span data-stu-id="459bf-123">Type List</span></span>](type-list.md)
- [<span data-ttu-id="459bf-124">Tipos genéricos no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="459bf-124">Generic Types in Visual Basic</span></span>](../../programming-guide/language-features/data-types/generic-types.md)
- [<span data-ttu-id="459bf-125">In</span><span class="sxs-lookup"><span data-stu-id="459bf-125">In</span></span>](../modifiers/in-generic-modifier.md)
- [<span data-ttu-id="459bf-126">Fora</span><span class="sxs-lookup"><span data-stu-id="459bf-126">Out</span></span>](../modifiers/out-generic-modifier.md)
