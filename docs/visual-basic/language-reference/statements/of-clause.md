---
title: "Cláusula of (Visual Basic) | Documentos do Microsoft"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- Of
- vb.Of
- vb.of
dev_langs:
- VB
helpviewer_keywords:
- Of keyword
- arguments [Visual Basic], data types
- constraints, Visual Basic generic types
- generic parameters
- generics [Visual Basic], constraints
- parameters, type
- types [Visual Basic], generic
- parameters, generic
- type parameters
- data type arguments
ms.assetid: 0db8f65c-65af-4089-ab7f-6fcfecb60444
caps.latest.revision: 17
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
ms.openlocfilehash: 2c750b057449bb112bb6b33de061bd5ad61c6566
ms.contentlocale: pt-br
ms.lasthandoff: 04/12/2017

---
# <a name="of-clause-visual-basic"></a><span data-ttu-id="a7d38-102">Cláusula Of (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a7d38-102">Of Clause (Visual Basic)</span></span>
<span data-ttu-id="a7d38-103">Apresenta um `Of` cláusula que identifica uma *parâmetro de tipo* em uma *genérico* classe, estrutura, interface, representante ou procedimento.</span><span class="sxs-lookup"><span data-stu-id="a7d38-103">Introduces an `Of` clause, which identifies a *type parameter* on a *generic* class, structure, interface, delegate, or procedure.</span></span> <span data-ttu-id="a7d38-104">Para obter informações sobre tipos genéricos, consulte [tipos genéricos no Visual Basic](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md).</span><span class="sxs-lookup"><span data-stu-id="a7d38-104">For information on generic types, see [Generic Types in Visual Basic](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md).</span></span>  
  
## <a name="using-the-of-keyword"></a><span data-ttu-id="a7d38-105">Usando a palavra-chave Of</span><span class="sxs-lookup"><span data-stu-id="a7d38-105">Using the Of Keyword</span></span>  
 <span data-ttu-id="a7d38-106">O seguinte exemplo de código usa o `Of` palavra-chave para definir o contorno de uma classe que leva dois parâmetros de tipo.</span><span class="sxs-lookup"><span data-stu-id="a7d38-106">The following code example uses the `Of` keyword to define the outline of a class that takes two type parameters.</span></span> <span data-ttu-id="a7d38-107">Ele *restringe* o `keyType` parâmetro pela <xref:System.IComparable>interface, que significa que o código consumido deve fornecer um argumento de tipo que implementa <xref:System.IComparable>.</xref:System.IComparable> </xref:System.IComparable></span><span class="sxs-lookup"><span data-stu-id="a7d38-107">It *constrains* the `keyType` parameter by the <xref:System.IComparable> interface, which means the consuming code must supply a type argument that implements <xref:System.IComparable>.</span></span> <span data-ttu-id="a7d38-108">Isso é necessário para que o `add` procedimento pode chamar o <xref:System.IComparable.CompareTo%2A?displayProperty=fullName>método.</xref:System.IComparable.CompareTo%2A?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="a7d38-108">This is necessary so that the `add` procedure can call the <xref:System.IComparable.CompareTo%2A?displayProperty=fullName> method.</span></span> <span data-ttu-id="a7d38-109">Para obter mais informações sobre restrições, consulte [tipo lista](../../../visual-basic/language-reference/statements/type-list.md).</span><span class="sxs-lookup"><span data-stu-id="a7d38-109">For more information on constraints, see [Type List](../../../visual-basic/language-reference/statements/type-list.md).</span></span>  
  
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
  
 <span data-ttu-id="a7d38-110">Se você concluir a definição de classe anterior, você pode construir uma variedade de `dictionary` classes dela.</span><span class="sxs-lookup"><span data-stu-id="a7d38-110">If you complete the preceding class definition, you can construct a variety of `dictionary` classes from it.</span></span> <span data-ttu-id="a7d38-111">Os tipos que você fornece para `entryType` e `keyType` determinam que tipo de entrada a classe contém e o tipo de chave que ela associa a cada entrada.</span><span class="sxs-lookup"><span data-stu-id="a7d38-111">The types you supply to `entryType` and `keyType` determine what type of entry the class holds and what type of key it associates with each entry.</span></span> <span data-ttu-id="a7d38-112">Por causa da restrição, você deve fornecer a `keyType` um tipo que implementa <xref:System.IComparable>.</xref:System.IComparable></span><span class="sxs-lookup"><span data-stu-id="a7d38-112">Because of the constraint, you must supply to `keyType` a type that implements <xref:System.IComparable>.</span></span>  
  
 <span data-ttu-id="a7d38-113">O exemplo de código a seguir cria um objeto que contém `String` entradas e associa um `Integer` chave com cada um deles.</span><span class="sxs-lookup"><span data-stu-id="a7d38-113">The following code example creates an object that holds `String` entries and associates an `Integer` key with each one.</span></span> <span data-ttu-id="a7d38-114">`Integer`implementa <xref:System.IComparable>e portanto satisfaz a restrição em `keyType`.</xref:System.IComparable></span><span class="sxs-lookup"><span data-stu-id="a7d38-114">`Integer` implements <xref:System.IComparable> and therefore satisfies the constraint on `keyType`.</span></span>  
  
```  
Dim d As New dictionary(Of String, Integer)  
```  
  
 <span data-ttu-id="a7d38-115">O `Of` palavra-chave pode ser usada nesses contextos:</span><span class="sxs-lookup"><span data-stu-id="a7d38-115">The `Of` keyword can be used in these contexts:</span></span>  
  
 [<span data-ttu-id="a7d38-116">Instrução Class</span><span class="sxs-lookup"><span data-stu-id="a7d38-116">Class Statement</span></span>](../../../visual-basic/language-reference/statements/class-statement.md)  
  
 [<span data-ttu-id="a7d38-117">Instrução Delegate</span><span class="sxs-lookup"><span data-stu-id="a7d38-117">Delegate Statement</span></span>](../../../visual-basic/language-reference/statements/delegate-statement.md)  
  
 [<span data-ttu-id="a7d38-118">Instrução Function</span><span class="sxs-lookup"><span data-stu-id="a7d38-118">Function Statement</span></span>](../../../visual-basic/language-reference/statements/function-statement.md)  
  
 [<span data-ttu-id="a7d38-119">Instrução Interface</span><span class="sxs-lookup"><span data-stu-id="a7d38-119">Interface Statement</span></span>](../../../visual-basic/language-reference/statements/interface-statement.md)  
  
 [<span data-ttu-id="a7d38-120">Instrução Structure</span><span class="sxs-lookup"><span data-stu-id="a7d38-120">Structure Statement</span></span>](../../../visual-basic/language-reference/statements/structure-statement.md)  
  
 [<span data-ttu-id="a7d38-121">Instrução Sub</span><span class="sxs-lookup"><span data-stu-id="a7d38-121">Sub Statement</span></span>](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
## <a name="see-also"></a><span data-ttu-id="a7d38-122">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a7d38-122">See Also</span></span>  
 <span data-ttu-id="a7d38-123"><xref:System.IComparable></xref:System.IComparable></span><span class="sxs-lookup"><span data-stu-id="a7d38-123"><xref:System.IComparable></span></span>   
<span data-ttu-id="a7d38-124"> [Lista de tipos](../../../visual-basic/language-reference/statements/type-list.md) </span><span class="sxs-lookup"><span data-stu-id="a7d38-124"> [Type List](../../../visual-basic/language-reference/statements/type-list.md) </span></span>  
<span data-ttu-id="a7d38-125"> [Tipos genéricos no Visual Basic](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md) </span><span class="sxs-lookup"><span data-stu-id="a7d38-125"> [Generic Types in Visual Basic](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md) </span></span>  
<span data-ttu-id="a7d38-126"> [Em](../../../visual-basic/language-reference/modifiers/in-generic-modifier.md) </span><span class="sxs-lookup"><span data-stu-id="a7d38-126"> [In](../../../visual-basic/language-reference/modifiers/in-generic-modifier.md) </span></span>  
<span data-ttu-id="a7d38-127"> [Out](../../../visual-basic/language-reference/modifiers/out-generic-modifier.md)</span><span class="sxs-lookup"><span data-stu-id="a7d38-127"> [Out](../../../visual-basic/language-reference/modifiers/out-generic-modifier.md)</span></span>
