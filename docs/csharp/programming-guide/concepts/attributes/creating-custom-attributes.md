---
title: Criando atributos personalizados (C#)
ms.date: 07/20/2015
ms.assetid: 500e1977-c6de-462d-abce-78a0eb1eda22
ms.openlocfilehash: 0277a88b7e5beda511f6490261a7009adcfed4ee
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54674629"
---
# <a name="creating-custom-attributes-c"></a><span data-ttu-id="1cfa7-102">Criando atributos personalizados (C#)</span><span class="sxs-lookup"><span data-stu-id="1cfa7-102">Creating Custom Attributes (C#)</span></span>
<span data-ttu-id="1cfa7-103">Você pode criar seus próprios atributos personalizados definindo uma classe de atributos, uma classe que deriva direta ou indiretamente de <xref:System.Attribute>, o que faz com que a identificação das definições de atributo nos metadados seja rápida e fácil.</span><span class="sxs-lookup"><span data-stu-id="1cfa7-103">You can create your own custom attributes by defining an attribute class, a class that derives directly or indirectly from <xref:System.Attribute>, which makes identifying attribute definitions in metadata fast and easy.</span></span> <span data-ttu-id="1cfa7-104">Suponha que você queira marcar tipos com o nome do programador que escreveu o tipo.</span><span class="sxs-lookup"><span data-stu-id="1cfa7-104">Suppose you want to tag types with the name of the programmer who wrote the type.</span></span> <span data-ttu-id="1cfa7-105">Você pode definir uma classe de atributos `Author` personalizada:</span><span class="sxs-lookup"><span data-stu-id="1cfa7-105">You might define a custom `Author` attribute class:</span></span>  
  
```csharp  
[System.AttributeUsage(System.AttributeTargets.Class |  
                       System.AttributeTargets.Struct)  
]  
public class Author : System.Attribute  
{  
    private string name;  
    public double version;  
  
    public Author(string name)  
    {  
        this.name = name;  
        version = 1.0;  
    }  
}  
```  
  
 <span data-ttu-id="1cfa7-106">O nome de classe será o nome do atributo, `Author`.</span><span class="sxs-lookup"><span data-stu-id="1cfa7-106">The class name is the attribute's name, `Author`.</span></span> <span data-ttu-id="1cfa7-107">Ela é derivada de `System.Attribute`, portanto, é uma classe de atributo personalizado.</span><span class="sxs-lookup"><span data-stu-id="1cfa7-107">It is derived from `System.Attribute`, so it is a custom attribute class.</span></span> <span data-ttu-id="1cfa7-108">Os parâmetros do construtor são parâmetros posicionais do atributo personalizado.</span><span class="sxs-lookup"><span data-stu-id="1cfa7-108">The constructor's parameters are the custom attribute's positional parameters.</span></span> <span data-ttu-id="1cfa7-109">Neste exemplo, `name` é um parâmetro posicional.</span><span class="sxs-lookup"><span data-stu-id="1cfa7-109">In this example, `name` is a positional parameter.</span></span> <span data-ttu-id="1cfa7-110">Quaisquer propriedades ou campos públicos de leitura/gravação são chamados de parâmetros.</span><span class="sxs-lookup"><span data-stu-id="1cfa7-110">Any public read-write fields or properties are named parameters.</span></span> <span data-ttu-id="1cfa7-111">Nesse caso, `version` é o único parâmetro nomeado.</span><span class="sxs-lookup"><span data-stu-id="1cfa7-111">In this case, `version` is the only named parameter.</span></span> <span data-ttu-id="1cfa7-112">Observe o uso do atributo `AttributeUsage` para tornar o atributo `Author` válido apenas na classe e nas declarações `struct`.</span><span class="sxs-lookup"><span data-stu-id="1cfa7-112">Note the use of the `AttributeUsage` attribute to make the `Author` attribute valid only on class and `struct` declarations.</span></span>  
  
 <span data-ttu-id="1cfa7-113">Você pode usar esse novo atributo da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="1cfa7-113">You could use this new attribute as follows:</span></span>  
  
```csharp  
[Author("P. Ackerman", version = 1.1)]  
class SampleClass  
{  
    // P. Ackerman's code goes here...  
}  
```  
  
 <span data-ttu-id="1cfa7-114">`AttributeUsage` tem um parâmetro nomeado, `AllowMultiple`, com o qual você pode fazer um atributo personalizado de uso único ou mulituso.</span><span class="sxs-lookup"><span data-stu-id="1cfa7-114">`AttributeUsage` has a named parameter, `AllowMultiple`, with which you can make a custom attribute single-use or multiuse.</span></span> <span data-ttu-id="1cfa7-115">No exemplo de código a seguir, um atributo multiuso é criado.</span><span class="sxs-lookup"><span data-stu-id="1cfa7-115">In the following code example, a multiuse attribute is created.</span></span>  
  
```csharp  
[System.AttributeUsage(System.AttributeTargets.Class |  
                       System.AttributeTargets.Struct,  
                       AllowMultiple = true)  // multiuse attribute  
]  
public class Author : System.Attribute  
```  
  
 <span data-ttu-id="1cfa7-116">No exemplo de código a seguir, vários atributos do mesmo tipo são aplicados a uma classe.</span><span class="sxs-lookup"><span data-stu-id="1cfa7-116">In the following code example, multiple attributes of the same type are applied to a class.</span></span>  
  
```csharp  
[Author("P. Ackerman", version = 1.1)]  
[Author("R. Koch", version = 1.2)]  
class SampleClass  
{  
    // P. Ackerman's code goes here...  
    // R. Koch's code goes here...  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="1cfa7-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="1cfa7-117">See also</span></span>

- <xref:System.Reflection>
- [<span data-ttu-id="1cfa7-118">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="1cfa7-118">C# Programming Guide</span></span>](../../../../csharp/programming-guide/index.md)
- [<span data-ttu-id="1cfa7-119">Escrevendo atributos personalizados</span><span class="sxs-lookup"><span data-stu-id="1cfa7-119">Writing Custom Attributes</span></span>](../../../../standard/attributes/writing-custom-attributes.md)
- [<span data-ttu-id="1cfa7-120">Reflexão (C#)</span><span class="sxs-lookup"><span data-stu-id="1cfa7-120">Reflection (C#)</span></span>](../../../../csharp/programming-guide/concepts/reflection.md)
- [<span data-ttu-id="1cfa7-121">Atributos (C#)</span><span class="sxs-lookup"><span data-stu-id="1cfa7-121">Attributes (C#)</span></span>](../../../../csharp/programming-guide/concepts/attributes/index.md)
- [<span data-ttu-id="1cfa7-122">Acessando atributos usando reflexão (C#)</span><span class="sxs-lookup"><span data-stu-id="1cfa7-122">Accessing Attributes by Using Reflection (C#)</span></span>](../../../../csharp/programming-guide/concepts/attributes/accessing-attributes-by-using-reflection.md)
- [<span data-ttu-id="1cfa7-123">AttributeUsage (C#)</span><span class="sxs-lookup"><span data-stu-id="1cfa7-123">AttributeUsage (C#)</span></span>](../../../../csharp/programming-guide/concepts/attributes/attributeusage.md)
