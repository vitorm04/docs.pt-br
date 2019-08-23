---
title: Criando atributos personalizados (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 5c9ef584-6c7c-496b-92a9-6e42f8d9ca28
ms.openlocfilehash: e4b55f92466fde47011937d08c946c9c75ca07b7
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69966328"
---
# <a name="creating-custom-attributes-visual-basic"></a><span data-ttu-id="81124-102">Criando atributos personalizados (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="81124-102">Creating Custom Attributes (Visual Basic)</span></span>
<span data-ttu-id="81124-103">Você pode criar seus próprios atributos personalizados definindo uma classe de atributos, uma classe que deriva direta ou indiretamente de <xref:System.Attribute>, o que faz com que a identificação das definições de atributo nos metadados seja rápida e fácil.</span><span class="sxs-lookup"><span data-stu-id="81124-103">You can create your own custom attributes by defining an attribute class, a class that derives directly or indirectly from <xref:System.Attribute>, which makes identifying attribute definitions in metadata fast and easy.</span></span> <span data-ttu-id="81124-104">Suponha que você queira marcar tipos com o nome do programador que escreveu o tipo.</span><span class="sxs-lookup"><span data-stu-id="81124-104">Suppose you want to tag types with the name of the programmer who wrote the type.</span></span> <span data-ttu-id="81124-105">Você pode definir uma classe de atributos `Author` personalizada:</span><span class="sxs-lookup"><span data-stu-id="81124-105">You might define a custom `Author` attribute class:</span></span>  
  
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
  
 <span data-ttu-id="81124-106">O nome de classe será o nome do atributo, `Author`.</span><span class="sxs-lookup"><span data-stu-id="81124-106">The class name is the attribute's name, `Author`.</span></span> <span data-ttu-id="81124-107">Ela é derivada de `System.Attribute`, portanto, é uma classe de atributo personalizado.</span><span class="sxs-lookup"><span data-stu-id="81124-107">It is derived from `System.Attribute`, so it is a custom attribute class.</span></span> <span data-ttu-id="81124-108">Os parâmetros do construtor são parâmetros posicionais do atributo personalizado.</span><span class="sxs-lookup"><span data-stu-id="81124-108">The constructor's parameters are the custom attribute's positional parameters.</span></span> <span data-ttu-id="81124-109">Neste exemplo, `name` é um parâmetro posicional.</span><span class="sxs-lookup"><span data-stu-id="81124-109">In this example, `name` is a positional parameter.</span></span> <span data-ttu-id="81124-110">Quaisquer propriedades ou campos públicos de leitura/gravação são chamados de parâmetros.</span><span class="sxs-lookup"><span data-stu-id="81124-110">Any public read-write fields or properties are named parameters.</span></span> <span data-ttu-id="81124-111">Nesse caso, `version` é o único parâmetro nomeado.</span><span class="sxs-lookup"><span data-stu-id="81124-111">In this case, `version` is the only named parameter.</span></span> <span data-ttu-id="81124-112">Observe o uso do atributo `AttributeUsage` para tornar o atributo `Author` válido apenas na classe e nas declarações `Structure`.</span><span class="sxs-lookup"><span data-stu-id="81124-112">Note the use of the `AttributeUsage` attribute to make the `Author` attribute valid only on class and `Structure` declarations.</span></span>  
  
 <span data-ttu-id="81124-113">Você pode usar esse novo atributo da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="81124-113">You could use this new attribute as follows:</span></span>  
  
```vb  
<Author("P. Ackerman", Version:=1.1)>   
Class SampleClass  
    ' P. Ackerman's code goes here...  
End Class  
```  
  
 <span data-ttu-id="81124-114">`AttributeUsage` tem um parâmetro nomeado, `AllowMultiple`, com o qual você pode fazer um atributo personalizado de uso único ou mulituso.</span><span class="sxs-lookup"><span data-stu-id="81124-114">`AttributeUsage` has a named parameter, `AllowMultiple`, with which you can make a custom attribute single-use or multiuse.</span></span> <span data-ttu-id="81124-115">No exemplo de código a seguir, um atributo multiuso é criado.</span><span class="sxs-lookup"><span data-stu-id="81124-115">In the following code example, a multiuse attribute is created.</span></span>  
  
```vb  
' multiuse attribute  
<System.AttributeUsage(System.AttributeTargets.Class Or   
                       System.AttributeTargets.Struct,   
                       AllowMultiple:=True)>   
Public Class Author  
    Inherits System.Attribute  
```  
  
 <span data-ttu-id="81124-116">No exemplo de código a seguir, vários atributos do mesmo tipo são aplicados a uma classe.</span><span class="sxs-lookup"><span data-stu-id="81124-116">In the following code example, multiple attributes of the same type are applied to a class.</span></span>  
  
```vb  
<Author("P. Ackerman", Version:=1.1),   
Author("R. Koch", Version:=1.2)>   
Class SampleClass  
    ' P. Ackerman's code goes here...  
    ' R. Koch's code goes here...  
End Class  
```  
  
> [!NOTE]
> <span data-ttu-id="81124-117">Se sua classe de atributos contém uma propriedade, essa propriedade deve ser de leitura/gravação.</span><span class="sxs-lookup"><span data-stu-id="81124-117">If your attribute class contains a property, that property must be read-write.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="81124-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="81124-118">See also</span></span>

- <xref:System.Reflection>
- [<span data-ttu-id="81124-119">Guia de programação do Visual Basic</span><span class="sxs-lookup"><span data-stu-id="81124-119">Visual Basic Programming Guide</span></span>](../../../../visual-basic/programming-guide/index.md)
- [<span data-ttu-id="81124-120">Escrevendo atributos personalizados</span><span class="sxs-lookup"><span data-stu-id="81124-120">Writing Custom Attributes</span></span>](../../../../standard/attributes/writing-custom-attributes.md)
- [<span data-ttu-id="81124-121">Reflexão (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="81124-121">Reflection (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/reflection.md)
- [<span data-ttu-id="81124-122">Atributos (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="81124-122">Attributes (Visual Basic)</span></span>](../../../../visual-basic/language-reference/attributes.md)
- [<span data-ttu-id="81124-123">Acessando atributos usando reflexão (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="81124-123">Accessing Attributes by Using Reflection (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/attributes/accessing-attributes-by-using-reflection.md)
- [<span data-ttu-id="81124-124">AttributeUsage (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="81124-124">AttributeUsage (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/attributes/attributeusage.md)
