---
title: Acessando atributos usando reflexão
ms.date: 07/20/2015
ms.assetid: c56e41da-5433-464f-a7bf-2a722e78bc9f
ms.openlocfilehash: 94352f07cf1f7e4a35f023503f138596ae5ac227
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74353551"
---
# <a name="accessing-attributes-by-using-reflection-visual-basic"></a><span data-ttu-id="87c49-102">Accessing Attributes by Using Reflection (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="87c49-102">Accessing Attributes by Using Reflection (Visual Basic)</span></span>

<span data-ttu-id="87c49-103">O fato de que você pode definir atributos personalizados e colocá-los em seu código-fonte seria de pouco valor sem alguma maneira de recuperar essas informações e tomar ação sobre elas.</span><span class="sxs-lookup"><span data-stu-id="87c49-103">The fact that you can define custom attributes and place them in your source code would be of little value without some way of retrieving that information and acting on it.</span></span> <span data-ttu-id="87c49-104">Por meio de reflexão, você pode recuperar as informações que foram definidas com atributos personalizados.</span><span class="sxs-lookup"><span data-stu-id="87c49-104">By using reflection, you can retrieve the information that was defined with custom attributes.</span></span> <span data-ttu-id="87c49-105">O método principal é o `GetCustomAttributes`, que retorna uma matriz de objetos que são equivalentes, em tempo de execução, aos atributos do código-fonte.</span><span class="sxs-lookup"><span data-stu-id="87c49-105">The key method is `GetCustomAttributes`, which returns an array of objects that are the run-time equivalents of the source code attributes.</span></span> <span data-ttu-id="87c49-106">Esse método tem várias versões sobrecarregadas.</span><span class="sxs-lookup"><span data-stu-id="87c49-106">This method has several overloaded versions.</span></span> <span data-ttu-id="87c49-107">Para obter mais informações, consulte <xref:System.Attribute>.</span><span class="sxs-lookup"><span data-stu-id="87c49-107">For more information, see <xref:System.Attribute>.</span></span>

<span data-ttu-id="87c49-108">Uma especificação de atributo, como:</span><span class="sxs-lookup"><span data-stu-id="87c49-108">An attribute specification such as:</span></span>

```vb
<Author("P. Ackerman", Version:=1.1)>
Class SampleClass
    ' P. Ackerman's code goes here...
End Class
```

 <span data-ttu-id="87c49-109">é conceitualmente equivalente a esta:</span><span class="sxs-lookup"><span data-stu-id="87c49-109">is conceptually equivalent to this:</span></span>

```vb
Dim anonymousAuthorObject As Author = New Author("P. Ackerman")
anonymousAuthorObject.version = 1.1
```

<span data-ttu-id="87c49-110">No entanto, o código não será executado até que `SampleClass` tenha os atributos consultados.</span><span class="sxs-lookup"><span data-stu-id="87c49-110">However, the code is not executed until `SampleClass` is queried for attributes.</span></span> <span data-ttu-id="87c49-111">Chamar `GetCustomAttributes` na `SampleClass` faz com que um objeto `Author` seja criado e inicializado como acima.</span><span class="sxs-lookup"><span data-stu-id="87c49-111">Calling `GetCustomAttributes` on `SampleClass` causes an `Author` object to be constructed and initialized as above.</span></span> <span data-ttu-id="87c49-112">Se a classe tiver outros atributos, outros objetos de atributo serão construídos de forma semelhante.</span><span class="sxs-lookup"><span data-stu-id="87c49-112">If the class has other attributes, other attribute objects are constructed similarly.</span></span> <span data-ttu-id="87c49-113">Então o `GetCustomAttributes` retornará o objeto `Author` e quaisquer outros objetos de atributo em uma matriz.</span><span class="sxs-lookup"><span data-stu-id="87c49-113">`GetCustomAttributes` then returns the `Author` object and any other attribute objects in an array.</span></span> <span data-ttu-id="87c49-114">Você poderá iterar sobre essa matriz, determinar quais atributos foram aplicados com base no tipo de cada elemento da matriz e extrair informações dos objetos de atributo.</span><span class="sxs-lookup"><span data-stu-id="87c49-114">You can then iterate over this array, determine what attributes were applied based on the type of each array element, and extract information from the attribute objects.</span></span>

## <a name="example"></a><span data-ttu-id="87c49-115">Exemplo</span><span class="sxs-lookup"><span data-stu-id="87c49-115">Example</span></span>

<span data-ttu-id="87c49-116">Aqui está um exemplo completo.</span><span class="sxs-lookup"><span data-stu-id="87c49-116">Here is a complete example.</span></span> <span data-ttu-id="87c49-117">Um atributo personalizado é definido, aplicado a várias entidades e recuperado por meio da reflexão.</span><span class="sxs-lookup"><span data-stu-id="87c49-117">A custom attribute is defined, applied to several entities, and retrieved via reflection.</span></span>

```vb
' Multiuse attribute
<System.AttributeUsage(System.AttributeTargets.Class Or
                       System.AttributeTargets.Struct,
                       AllowMultiple:=True)>
Public Class Author
    Inherits System.Attribute
    Private name As String
    Public version As Double
    Sub New(ByVal authorName As String)
        name = authorName

        ' Default value
        version = 1.0
    End Sub

    Function GetName() As String
        Return name
    End Function
End Class

' Class with the Author attribute
<Author("P. Ackerman")>
Public Class FirstClass
End Class

' Class without the Author attribute
Public Class SecondClass
End Class

' Class with multiple Author attributes.
<Author("P. Ackerman"), Author("R. Koch", Version:=2.0)>
Public Class ThirdClass
End Class

Class TestAuthorAttribute
    Sub Main()
        PrintAuthorInfo(GetType(FirstClass))
        PrintAuthorInfo(GetType(SecondClass))
        PrintAuthorInfo(GetType(ThirdClass))
    End Sub

    Private Shared Sub PrintAuthorInfo(ByVal t As System.Type)
        System.Console.WriteLine("Author information for {0}", t)

        ' Using reflection
        Dim attrs() As System.Attribute = System.Attribute.GetCustomAttributes(t)

        ' Displaying output
        For Each attr In attrs
            Dim a As Author = CType(attr, Author)
            System.Console.WriteLine("   {0}, version {1:f}", a.GetName(), a.version)
        Next
    End Sub

    ' Output:
    '   Author information for FirstClass
    '     P. Ackerman, version 1.00
    ' Author information for SecondClass
    ' Author information for ThirdClass
    '  R. Koch, version 2.00
    '  P. Ackerman, version 1.00

End Class
```

## <a name="see-also"></a><span data-ttu-id="87c49-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="87c49-118">See also</span></span>

- <xref:System.Reflection>
- <xref:System.Attribute>
- [<span data-ttu-id="87c49-119">Guia de programação do Visual Basic</span><span class="sxs-lookup"><span data-stu-id="87c49-119">Visual Basic Programming Guide</span></span>](../../../../visual-basic/programming-guide/index.md)
- [<span data-ttu-id="87c49-120">Recuperando informações armazenadas em atributos</span><span class="sxs-lookup"><span data-stu-id="87c49-120">Retrieving Information Stored in Attributes</span></span>](../../../../standard/attributes/retrieving-information-stored-in-attributes.md)
- [<span data-ttu-id="87c49-121">Reflexão (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="87c49-121">Reflection (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/reflection.md)
- [<span data-ttu-id="87c49-122">Atributos (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="87c49-122">Attributes (Visual Basic)</span></span>](../../../../visual-basic/language-reference/attributes.md)
- [<span data-ttu-id="87c49-123">Criando atributos personalizados (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="87c49-123">Creating Custom Attributes (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/attributes/creating-custom-attributes.md)
