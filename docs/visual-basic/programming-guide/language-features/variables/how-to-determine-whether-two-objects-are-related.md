---
title: 'Como: Determinar se dois objetos estão relacionados (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- inheritance [Visual Basic], Visual Basic objects
- objects [Visual Basic], inheritance
- object variables [Visual Basic], determining relation
ms.assetid: da002e3f-6616-4bad-a229-f842d06652bb
ms.openlocfilehash: 2b17be4ef5a7dabfc4779ab6f5675cc2baec9c3c
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/30/2019
ms.locfileid: "68626561"
---
# <a name="how-to-determine-whether-two-objects-are-related-visual-basic"></a><span data-ttu-id="266c0-102">Como: Determinar se dois objetos estão relacionados (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="266c0-102">How to: Determine Whether Two Objects Are Related (Visual Basic)</span></span>

<span data-ttu-id="266c0-103">Você pode comparar dois objetos para determinar a relação, se houver, entre as classes das quais elas são criadas.</span><span class="sxs-lookup"><span data-stu-id="266c0-103">You can compare two objects to determine the relationship, if any, between the classes from which they are created.</span></span> <span data-ttu-id="266c0-104">O <xref:System.Type.IsInstanceOfType%2A> método `True` da classe retorna se a classe especificada herda da classe atual ou se o tipo atual é uma interface com suporte da classe especificada. <xref:System.Type?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="266c0-104">The <xref:System.Type.IsInstanceOfType%2A> method of the <xref:System.Type?displayProperty=nameWithType> class returns `True` if the specified class inherits from the current class, or if the current type is an interface supported by the specified class.</span></span>

### <a name="to-determine-if-one-object-inherits-from-another-objects-class-or-interface"></a><span data-ttu-id="266c0-105">Para determinar se um objeto herda da classe ou interface de outro objeto</span><span class="sxs-lookup"><span data-stu-id="266c0-105">To determine if one object inherits from another object's class or interface</span></span>

1. <span data-ttu-id="266c0-106">No objeto que você acredita que pode ser do tipo base, invoque o <xref:System.Object.GetType%2A> método.</span><span class="sxs-lookup"><span data-stu-id="266c0-106">On the object you think might be of the base type, invoke the <xref:System.Object.GetType%2A> method.</span></span>

2. <span data-ttu-id="266c0-107">No objeto retornado por <xref:System.Object.GetType%2A>, invoque o <xref:System.Type.IsInstanceOfType%2A> método. <xref:System.Type?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="266c0-107">On the <xref:System.Type?displayProperty=nameWithType> object returned by <xref:System.Object.GetType%2A>, invoke the <xref:System.Type.IsInstanceOfType%2A> method.</span></span>

3. <span data-ttu-id="266c0-108">Na lista de argumentos para <xref:System.Type.IsInstanceOfType%2A>, especifique o objeto que você acredita que pode ser do tipo derivado.</span><span class="sxs-lookup"><span data-stu-id="266c0-108">In the argument list for <xref:System.Type.IsInstanceOfType%2A>, specify the object you think might be of the derived type.</span></span>

    <span data-ttu-id="266c0-109"><xref:System.Type.IsInstanceOfType%2A>retorna `True` se o tipo de argumento herda <xref:System.Type?displayProperty=nameWithType> do tipo de objeto.</span><span class="sxs-lookup"><span data-stu-id="266c0-109"><xref:System.Type.IsInstanceOfType%2A> returns `True` if its argument type inherits from the <xref:System.Type?displayProperty=nameWithType> object type.</span></span>

## <a name="example"></a><span data-ttu-id="266c0-110">Exemplo</span><span class="sxs-lookup"><span data-stu-id="266c0-110">Example</span></span>
 <span data-ttu-id="266c0-111">O exemplo a seguir determina se um objeto representa uma classe derivada da classe de outro objeto.</span><span class="sxs-lookup"><span data-stu-id="266c0-111">The following example determines whether one object represents a class derived from another object's class.</span></span>

```vb
Public Class baseClass
End Class
Public Class derivedClass : Inherits baseClass
End Class
Public Class testTheseClasses
    Public Sub seeIfRelated()
        Dim baseObj As Object = New baseClass()
        Dim derivedObj As Object = New derivedClass()
        Dim related As Boolean
        related = baseObj.GetType().IsInstanceOfType(derivedObj)
        MsgBox(CStr(related))
    End Sub
End Class
```

<span data-ttu-id="266c0-112">Observe o posicionamento inesperado das duas variáveis de objeto na chamada <xref:System.Type.IsInstanceOfType%2A>para.</span><span class="sxs-lookup"><span data-stu-id="266c0-112">Note the unexpected placement of the two object variables in the call to <xref:System.Type.IsInstanceOfType%2A>.</span></span> <span data-ttu-id="266c0-113">O tipo base esperado é usado para gerar a <xref:System.Type?displayProperty=nameWithType> classe e o tipo derivado esperado é passado como um argumento para o <xref:System.Type.IsInstanceOfType%2A> método.</span><span class="sxs-lookup"><span data-stu-id="266c0-113">The supposed base type is used to generate the <xref:System.Type?displayProperty=nameWithType> class, and the supposed derived type is passed as an argument to the <xref:System.Type.IsInstanceOfType%2A> method.</span></span>

## <a name="see-also"></a><span data-ttu-id="266c0-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="266c0-114">See also</span></span>

- <xref:System.Object.GetType%2A>
- <xref:System.Type?displayProperty=nameWithType>
- <xref:System.Type.IsInstanceOfType%2A>
- [<span data-ttu-id="266c0-115">Tipo de Dados Object</span><span class="sxs-lookup"><span data-stu-id="266c0-115">Object Data Type</span></span>](../../../../visual-basic/language-reference/data-types/object-data-type.md)
- [<span data-ttu-id="266c0-116">Variáveis de Objeto</span><span class="sxs-lookup"><span data-stu-id="266c0-116">Object Variables</span></span>](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md)
- [<span data-ttu-id="266c0-117">Valores de Variável de Objeto</span><span class="sxs-lookup"><span data-stu-id="266c0-117">Object Variable Values</span></span>](../../../../visual-basic/programming-guide/language-features/variables/object-variable-values.md)
- [<span data-ttu-id="266c0-118">Como: Determinar se dois objetos são idênticos</span><span class="sxs-lookup"><span data-stu-id="266c0-118">How to: Determine Whether Two Objects Are Identical</span></span>](../../../../visual-basic/programming-guide/language-features/variables/how-to-determine-whether-two-objects-are-identical.md)
