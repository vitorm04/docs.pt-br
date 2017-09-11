---
title: Criando atributos personalizados (Visual Basic) | Documentos do Microsoft
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
ms.assetid: 5c9ef584-6c7c-496b-92a9-6e42f8d9ca28
caps.latest.revision: 3
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: fbfc3f84f6287d233d475f01869dab63b937a521
ms.contentlocale: pt-br
ms.lasthandoff: 04/12/2017

---
# <a name="creating-custom-attributes-visual-basic"></a><span data-ttu-id="9c2f7-102">Criando atributos personalizados (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9c2f7-102">Creating Custom Attributes (Visual Basic)</span></span>
<span data-ttu-id="9c2f7-103">Você pode criar seus próprios atributos personalizados, definindo uma classe de atributo, uma classe que deriva diretamente ou indiretamente de <xref:System.Attribute>, que faz com que identifica as definições de atributo nos metadados rápida e fácil.</xref:System.Attribute></span><span class="sxs-lookup"><span data-stu-id="9c2f7-103">You can create your own custom attributes by defining an attribute class, a class that derives directly or indirectly from <xref:System.Attribute>, which makes identifying attribute definitions in metadata fast and easy.</span></span> <span data-ttu-id="9c2f7-104">Suponha que você queira para tipos de marca com o nome do programador que escreveu o tipo.</span><span class="sxs-lookup"><span data-stu-id="9c2f7-104">Suppose you want to tag types with the name of the programmer who wrote the type.</span></span> <span data-ttu-id="9c2f7-105">Você pode definir um personalizado `Author` classe de atributo:</span><span class="sxs-lookup"><span data-stu-id="9c2f7-105">You might define a custom `Author` attribute class:</span></span>  
  
```vb  
<System.AttributeUsage(System.AttributeTargets.Class Or   
                       System.AttributeTargets.Struct)>   
Public Class Author  
    Inherits System.Attribute  
    Private name As String  
    Public version As Double  
    Sub New(ByVal authorName As String)  
        name = authorName  
        version = 1.0  
    End Sub  
End Class  
```  
  
 <span data-ttu-id="9c2f7-106">O nome da classe é o nome do atributo, `Author`.</span><span class="sxs-lookup"><span data-stu-id="9c2f7-106">The class name is the attribute's name, `Author`.</span></span> <span data-ttu-id="9c2f7-107">Ela é derivada de `System.Attribute`, portanto, é uma classe de atributo personalizado.</span><span class="sxs-lookup"><span data-stu-id="9c2f7-107">It is derived from `System.Attribute`, so it is a custom attribute class.</span></span> <span data-ttu-id="9c2f7-108">Parâmetros do construtor são parâmetros posicionais do atributo personalizado.</span><span class="sxs-lookup"><span data-stu-id="9c2f7-108">The constructor's parameters are the custom attribute's positional parameters.</span></span> <span data-ttu-id="9c2f7-109">Neste exemplo, `name` é um parâmetro posicional.</span><span class="sxs-lookup"><span data-stu-id="9c2f7-109">In this example, `name` is a positional parameter.</span></span> <span data-ttu-id="9c2f7-110">Quaisquer propriedades ou campos públicos de leitura / gravação são parâmetros nomeadas.</span><span class="sxs-lookup"><span data-stu-id="9c2f7-110">Any public read-write fields or properties are named parameters.</span></span> <span data-ttu-id="9c2f7-111">Nesse caso, `version` é o único parâmetro nomeado.</span><span class="sxs-lookup"><span data-stu-id="9c2f7-111">In this case, `version` is the only named parameter.</span></span> <span data-ttu-id="9c2f7-112">Observe o uso do `AttributeUsage` atributo para tornar o `Author` válido apenas na classe de atributo e `Structure` declarações.</span><span class="sxs-lookup"><span data-stu-id="9c2f7-112">Note the use of the `AttributeUsage` attribute to make the `Author` attribute valid only on class and `Structure` declarations.</span></span>  
  
 <span data-ttu-id="9c2f7-113">Você pode usar esse novo atributo da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="9c2f7-113">You could use this new attribute as follows:</span></span>  
  
```vb  
<Author("P. Ackerman", Version:=1.1)>   
Class SampleClass  
    ' P. Ackerman's code goes here...  
End Class  
```  
  
 <span data-ttu-id="9c2f7-114">`AttributeUsage`tem um parâmetro nomeado, `AllowMultiple`, com o qual você pode fazer um atributo personalizado multiuse ou de uso único.</span><span class="sxs-lookup"><span data-stu-id="9c2f7-114">`AttributeUsage` has a named parameter, `AllowMultiple`, with which you can make a custom attribute single-use or multiuse.</span></span> <span data-ttu-id="9c2f7-115">No exemplo de código a seguir, um atributo multiuse é criado.</span><span class="sxs-lookup"><span data-stu-id="9c2f7-115">In the following code example, a multiuse attribute is created.</span></span>  
  
```vb  
' multiuse attribute  
<System.AttributeUsage(System.AttributeTargets.Class Or   
                       System.AttributeTargets.Struct,   
                       AllowMultiple:=True)>   
Public Class Author  
    Inherits System.Attribute  
```  
  
 <span data-ttu-id="9c2f7-116">No exemplo de código a seguir, vários atributos do mesmo tipo são aplicados a uma classe.</span><span class="sxs-lookup"><span data-stu-id="9c2f7-116">In the following code example, multiple attributes of the same type are applied to a class.</span></span>  
  
```vb  
<Author("P. Ackerman", Version:=1.1),   
Author("R. Koch", Version:=1.2)>   
Class SampleClass  
    ' P. Ackerman's code goes here...  
    ' R. Koch's code goes here...  
End Class  
```  
  
> [!NOTE]
>  <span data-ttu-id="9c2f7-117">Se sua classe de atributo contém uma propriedade, essa propriedade deve ser leitura / gravação.</span><span class="sxs-lookup"><span data-stu-id="9c2f7-117">If your attribute class contains a property, that property must be read-write.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9c2f7-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="9c2f7-118">See Also</span></span>  
 <span data-ttu-id="9c2f7-119"><xref:System.Reflection></xref:System.Reflection></span><span class="sxs-lookup"><span data-stu-id="9c2f7-119"><xref:System.Reflection></span></span>   
<span data-ttu-id="9c2f7-120"> [Guia de programação em Visual Basic](../../../../visual-basic/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="9c2f7-120"> [Visual Basic Programming Guide](../../../../visual-basic/programming-guide/index.md) </span></span>  
<span data-ttu-id="9c2f7-121"> [Escrevendo atributos personalizados](http://msdn.microsoft.com/library/97216f69-bde8-49fd-ac40-f18c500ef5dc) </span><span class="sxs-lookup"><span data-stu-id="9c2f7-121"> [Writing Custom Attributes](http://msdn.microsoft.com/library/97216f69-bde8-49fd-ac40-f18c500ef5dc) </span></span>  
<span data-ttu-id="9c2f7-122"> [Reflexão (Visual Basic)](../../../../visual-basic/programming-guide/concepts/reflection.md) </span><span class="sxs-lookup"><span data-stu-id="9c2f7-122"> [Reflection (Visual Basic)](../../../../visual-basic/programming-guide/concepts/reflection.md) </span></span>  
<span data-ttu-id="9c2f7-123"> [Atributos (Visual Basic)](../../../../visual-basic/language-reference/attributes.md) </span><span class="sxs-lookup"><span data-stu-id="9c2f7-123"> [Attributes (Visual Basic)](../../../../visual-basic/language-reference/attributes.md) </span></span>  
<span data-ttu-id="9c2f7-124"> [Acessando atributos usando reflexão (Visual Basic)](../../../../visual-basic/programming-guide/concepts/attributes/accessing-attributes-by-using-reflection.md) </span><span class="sxs-lookup"><span data-stu-id="9c2f7-124"> [Accessing Attributes by Using Reflection (Visual Basic)](../../../../visual-basic/programming-guide/concepts/attributes/accessing-attributes-by-using-reflection.md) </span></span>  
<span data-ttu-id="9c2f7-125"> [AttributeUsage (Visual Basic)](../../../../visual-basic/programming-guide/concepts/attributes/attributeusage.md)</span><span class="sxs-lookup"><span data-stu-id="9c2f7-125"> [AttributeUsage (Visual Basic)](../../../../visual-basic/programming-guide/concepts/attributes/attributeusage.md)</span></span>
