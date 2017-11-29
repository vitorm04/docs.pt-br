---
title: Criando atributos personalizados (C#)
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-csharp
ms.topic: article
ms.assetid: 500e1977-c6de-462d-abce-78a0eb1eda22
caps.latest.revision: "3"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 38bdedb352cc79f7a4cc3d08eb6138e7d994514b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="creating-custom-attributes-c"></a><span data-ttu-id="d62c0-102">Criando atributos personalizados (C#)</span><span class="sxs-lookup"><span data-stu-id="d62c0-102">Creating Custom Attributes (C#)</span></span>
<span data-ttu-id="d62c0-103">Você pode criar seus próprios atributos personalizados definindo uma classe de atributos, uma classe que deriva direta ou indiretamente de <xref:System.Attribute>, o que faz com que a identificação das definições de atributo nos metadados seja rápida e fácil.</span><span class="sxs-lookup"><span data-stu-id="d62c0-103">You can create your own custom attributes by defining an attribute class, a class that derives directly or indirectly from <xref:System.Attribute>, which makes identifying attribute definitions in metadata fast and easy.</span></span> <span data-ttu-id="d62c0-104">Suponha que você queira marcar tipos com o nome do programador que escreveu o tipo.</span><span class="sxs-lookup"><span data-stu-id="d62c0-104">Suppose you want to tag types with the name of the programmer who wrote the type.</span></span> <span data-ttu-id="d62c0-105">Você pode definir uma classe de atributos `Author` personalizada:</span><span class="sxs-lookup"><span data-stu-id="d62c0-105">You might define a custom `Author` attribute class:</span></span>  
  
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
  
 <span data-ttu-id="d62c0-106">O nome de classe será o nome do atributo, `Author`.</span><span class="sxs-lookup"><span data-stu-id="d62c0-106">The class name is the attribute's name, `Author`.</span></span> <span data-ttu-id="d62c0-107">Ela é derivada de `System.Attribute`, portanto, é uma classe de atributo personalizado.</span><span class="sxs-lookup"><span data-stu-id="d62c0-107">It is derived from `System.Attribute`, so it is a custom attribute class.</span></span> <span data-ttu-id="d62c0-108">Os parâmetros do construtor são parâmetros posicionais do atributo personalizado.</span><span class="sxs-lookup"><span data-stu-id="d62c0-108">The constructor's parameters are the custom attribute's positional parameters.</span></span> <span data-ttu-id="d62c0-109">Neste exemplo, `name` é um parâmetro posicional.</span><span class="sxs-lookup"><span data-stu-id="d62c0-109">In this example, `name` is a positional parameter.</span></span> <span data-ttu-id="d62c0-110">Quaisquer propriedades ou campos públicos de leitura/gravação são chamados de parâmetros.</span><span class="sxs-lookup"><span data-stu-id="d62c0-110">Any public read-write fields or properties are named parameters.</span></span> <span data-ttu-id="d62c0-111">Nesse caso, `version` é o único parâmetro nomeado.</span><span class="sxs-lookup"><span data-stu-id="d62c0-111">In this case, `version` is the only named parameter.</span></span> <span data-ttu-id="d62c0-112">Observe o uso do atributo `AttributeUsage` para tornar o atributo `Author` válido apenas na classe e nas declarações `struct`.</span><span class="sxs-lookup"><span data-stu-id="d62c0-112">Note the use of the `AttributeUsage` attribute to make the `Author` attribute valid only on class and `struct` declarations.</span></span>  
  
 <span data-ttu-id="d62c0-113">Você pode usar esse novo atributo da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="d62c0-113">You could use this new attribute as follows:</span></span>  
  
```csharp  
[Author("P. Ackerman", version = 1.1)]  
class SampleClass  
{  
    // P. Ackerman's code goes here...  
}  
```  
  
 <span data-ttu-id="d62c0-114">`AttributeUsage` tem um parâmetro nomeado, `AllowMultiple`, com o qual você pode fazer um atributo personalizado de uso único ou mulituso.</span><span class="sxs-lookup"><span data-stu-id="d62c0-114">`AttributeUsage` has a named parameter, `AllowMultiple`, with which you can make a custom attribute single-use or multiuse.</span></span> <span data-ttu-id="d62c0-115">No exemplo de código a seguir, um atributo multiuso é criado.</span><span class="sxs-lookup"><span data-stu-id="d62c0-115">In the following code example, a multiuse attribute is created.</span></span>  
  
```csharp  
[System.AttributeUsage(System.AttributeTargets.Class |  
                       System.AttributeTargets.Struct,  
                       AllowMultiple = true)  // multiuse attribute  
]  
public class Author : System.Attribute  
```  
  
 <span data-ttu-id="d62c0-116">No exemplo de código a seguir, vários atributos do mesmo tipo são aplicados a uma classe.</span><span class="sxs-lookup"><span data-stu-id="d62c0-116">In the following code example, multiple attributes of the same type are applied to a class.</span></span>  
  
```csharp  
[Author("P. Ackerman", version = 1.1)]  
[Author("R. Koch", version = 1.2)]  
class SampleClass  
{  
    // P. Ackerman's code goes here...  
    // R. Koch's code goes here...  
}  
```  
  
> [!NOTE]
>  <span data-ttu-id="d62c0-117">Se sua classe de atributos contém uma propriedade, essa propriedade deve ser de leitura/gravação.</span><span class="sxs-lookup"><span data-stu-id="d62c0-117">If your attribute class contains a property, that property must be read-write.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d62c0-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="d62c0-118">See Also</span></span>  
 <xref:System.Reflection>  
 [<span data-ttu-id="d62c0-119">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="d62c0-119">C# Programming Guide</span></span>](../../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="d62c0-120">Escrevendo atributos personalizados</span><span class="sxs-lookup"><span data-stu-id="d62c0-120">Writing Custom Attributes</span></span>](../../../../standard/attributes/writing-custom-attributes.md)  
 [<span data-ttu-id="d62c0-121">Reflexão (C#)</span><span class="sxs-lookup"><span data-stu-id="d62c0-121">Reflection (C#)</span></span>](../../../../csharp/programming-guide/concepts/reflection.md)  
 [<span data-ttu-id="d62c0-122">Atributos (C#)</span><span class="sxs-lookup"><span data-stu-id="d62c0-122">Attributes (C#)</span></span>](../../../../csharp/programming-guide/concepts/attributes/index.md)  
 [<span data-ttu-id="d62c0-123">Acessando atributos usando reflexão (C#)</span><span class="sxs-lookup"><span data-stu-id="d62c0-123">Accessing Attributes by Using Reflection (C#)</span></span>](../../../../csharp/programming-guide/concepts/attributes/accessing-attributes-by-using-reflection.md)  
 [<span data-ttu-id="d62c0-124">AttributeUsage (C#)</span><span class="sxs-lookup"><span data-stu-id="d62c0-124">AttributeUsage (C#)</span></span>](../../../../csharp/programming-guide/concepts/attributes/attributeusage.md)
