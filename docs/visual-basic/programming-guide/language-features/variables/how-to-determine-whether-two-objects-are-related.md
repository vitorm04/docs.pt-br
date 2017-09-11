---
title: "Como: determinar se dois objetos estão relacionados (Visual Basic) | Documentos do Microsoft"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- inheritance, Visual Basic objects
- objects [Visual Basic], inheritance
- object variables, determining relation
ms.assetid: da002e3f-6616-4bad-a229-f842d06652bb
caps.latest.revision: 7
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
ms.openlocfilehash: a102f0c846cb941f7855d67cfbffd3bcb84e1538
ms.contentlocale: pt-br
ms.lasthandoff: 04/12/2017

---
# <a name="how-to-determine-whether-two-objects-are-related-visual-basic"></a><span data-ttu-id="4d378-102">Como determinar se dois objetos estão relacionados (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="4d378-102">How to: Determine Whether Two Objects Are Related (Visual Basic)</span></span>
<span data-ttu-id="4d378-103">Você pode comparar dois objetos para determinar a relação, se houver, entre as classes no qual eles são criados.</span><span class="sxs-lookup"><span data-stu-id="4d378-103">You can compare two objects to determine the relationship, if any, between the classes from which they are created.</span></span> <span data-ttu-id="4d378-104">O <xref:System.Type.IsInstanceOfType%2A>método o <xref:System.Type?displayProperty=fullName>classe retorna `True` se a classe especificada herda da classe atual, ou se o tipo atual é uma interface com suporte a classe especificada.</xref:System.Type?displayProperty=fullName> </xref:System.Type.IsInstanceOfType%2A></span><span class="sxs-lookup"><span data-stu-id="4d378-104">The <xref:System.Type.IsInstanceOfType%2A> method of the <xref:System.Type?displayProperty=fullName> class returns `True` if the specified class inherits from the current class, or if the current type is an interface supported by the specified class.</span></span>  
  
### <a name="to-determine-if-one-object-inherits-from-another-objects-class-or-interface"></a><span data-ttu-id="4d378-105">Para determinar se um objeto herda da classe ou interface de outro objeto</span><span class="sxs-lookup"><span data-stu-id="4d378-105">To determine if one object inherits from another object's class or interface</span></span>  
  
1.  <span data-ttu-id="4d378-106">No objeto que você acha que podem ser do tipo base, chamar o <xref:System.Object.GetType%2A>método.</xref:System.Object.GetType%2A></span><span class="sxs-lookup"><span data-stu-id="4d378-106">On the object you think might be of the base type, invoke the <xref:System.Object.GetType%2A> method.</span></span>  
  
2.  <span data-ttu-id="4d378-107">Sobre o <xref:System.Type?displayProperty=fullName>objeto retornado por <xref:System.Object.GetType%2A>, chamar o <xref:System.Type.IsInstanceOfType%2A>método.</xref:System.Type.IsInstanceOfType%2A> </xref:System.Object.GetType%2A> </xref:System.Type?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="4d378-107">On the <xref:System.Type?displayProperty=fullName> object returned by <xref:System.Object.GetType%2A>, invoke the <xref:System.Type.IsInstanceOfType%2A> method.</span></span>  
  
3.  <span data-ttu-id="4d378-108">Na lista de argumentos para <xref:System.Type.IsInstanceOfType%2A>, especifique o objeto que você acha que pode ser do tipo derivado.</xref:System.Type.IsInstanceOfType%2A></span><span class="sxs-lookup"><span data-stu-id="4d378-108">In the argument list for <xref:System.Type.IsInstanceOfType%2A>, specify the object you think might be of the derived type.</span></span>  
  
     <span data-ttu-id="4d378-109"><xref:System.Type.IsInstanceOfType%2A>Retorna `True` se seu tipo de argumento herda o <xref:System.Type?displayProperty=fullName>tipo de objeto.</xref:System.Type?displayProperty=fullName></xref:System.Type.IsInstanceOfType%2A></span><span class="sxs-lookup"><span data-stu-id="4d378-109"><xref:System.Type.IsInstanceOfType%2A> returns `True` if its argument type inherits from the <xref:System.Type?displayProperty=fullName> object type.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4d378-110">Exemplo</span><span class="sxs-lookup"><span data-stu-id="4d378-110">Example</span></span>  
 <span data-ttu-id="4d378-111">O exemplo a seguir determina se um objeto representa uma classe derivada da classe de outro objeto.</span><span class="sxs-lookup"><span data-stu-id="4d378-111">The following example determines whether one object represents a class derived from another object's class.</span></span>  
  
```  
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
  
 <span data-ttu-id="4d378-112">Observe a colocação inesperada de variáveis de dois objeto na chamada para <xref:System.Type.IsInstanceOfType%2A>.</xref:System.Type.IsInstanceOfType%2A></span><span class="sxs-lookup"><span data-stu-id="4d378-112">Note the unexpected placement of the two object variables in the call to <xref:System.Type.IsInstanceOfType%2A>.</span></span> <span data-ttu-id="4d378-113">O tipo base suposto é usado para gerar o <xref:System.Type?displayProperty=fullName>classe e o tipo derivado suposto é passado como um argumento para o <xref:System.Type.IsInstanceOfType%2A>método.</xref:System.Type.IsInstanceOfType%2A> </xref:System.Type?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="4d378-113">The supposed base type is used to generate the <xref:System.Type?displayProperty=fullName> class, and the supposed derived type is passed as an argument to the <xref:System.Type.IsInstanceOfType%2A> method.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4d378-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="4d378-114">See Also</span></span>  
 <span data-ttu-id="4d378-115"><xref:System.Object.GetType%2A></xref:System.Object.GetType%2A></span><span class="sxs-lookup"><span data-stu-id="4d378-115"><xref:System.Object.GetType%2A></span></span>   
 <span data-ttu-id="4d378-116"><xref:System.Type?displayProperty=fullName></xref:System.Type?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="4d378-116"><xref:System.Type?displayProperty=fullName></span></span>   
 <span data-ttu-id="4d378-117"><xref:System.Type.IsInstanceOfType%2A></xref:System.Type.IsInstanceOfType%2A></span><span class="sxs-lookup"><span data-stu-id="4d378-117"><xref:System.Type.IsInstanceOfType%2A></span></span>   
<span data-ttu-id="4d378-118"> [Tipo de dados Object](../../../../visual-basic/language-reference/data-types/object-data-type.md) </span><span class="sxs-lookup"><span data-stu-id="4d378-118"> [Object Data Type](../../../../visual-basic/language-reference/data-types/object-data-type.md) </span></span>  
<span data-ttu-id="4d378-119"> [Variáveis de objeto](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md) </span><span class="sxs-lookup"><span data-stu-id="4d378-119"> [Object Variables](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md) </span></span>  
<span data-ttu-id="4d378-120"> [Valores de variáveis de objeto](../../../../visual-basic/programming-guide/language-features/variables/object-variable-values.md) </span><span class="sxs-lookup"><span data-stu-id="4d378-120"> [Object Variable Values](../../../../visual-basic/programming-guide/language-features/variables/object-variable-values.md) </span></span>  
<span data-ttu-id="4d378-121"> [Como determinar se dois objetos são idênticos](../../../../visual-basic/programming-guide/language-features/variables/how-to-determine-whether-two-objects-are-identical.md)</span><span class="sxs-lookup"><span data-stu-id="4d378-121"> [How to: Determine Whether Two Objects Are Identical](../../../../visual-basic/programming-guide/language-features/variables/how-to-determine-whether-two-objects-are-identical.md)</span></span>
