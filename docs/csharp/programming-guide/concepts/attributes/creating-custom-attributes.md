---
title: Criando atributos personalizados (C#)
description: Saiba como criar atributos personalizados em C# definindo uma classe de atributo que deriva da classe de atributo.
ms.date: 07/20/2015
ms.assetid: 500e1977-c6de-462d-abce-78a0eb1eda22
ms.openlocfilehash: 6946b707134b2bdbc245b8786f144517a5870440
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91202598"
---
# <a name="creating-custom-attributes-c"></a><span data-ttu-id="70b00-103">Criando atributos personalizados (C#)</span><span class="sxs-lookup"><span data-stu-id="70b00-103">Creating Custom Attributes (C#)</span></span>

<span data-ttu-id="70b00-104">Você pode criar seus próprios atributos personalizados definindo uma classe de atributos, uma classe que deriva direta ou indiretamente de <xref:System.Attribute>, o que faz com que a identificação das definições de atributo nos metadados seja rápida e fácil.</span><span class="sxs-lookup"><span data-stu-id="70b00-104">You can create your own custom attributes by defining an attribute class, a class that derives directly or indirectly from <xref:System.Attribute>, which makes identifying attribute definitions in metadata fast and easy.</span></span> <span data-ttu-id="70b00-105">Suponha que você queira marcar tipos com o nome do programador que escreveu o tipo.</span><span class="sxs-lookup"><span data-stu-id="70b00-105">Suppose you want to tag types with the name of the programmer who wrote the type.</span></span> <span data-ttu-id="70b00-106">Você pode definir uma classe de atributos `Author` personalizada:</span><span class="sxs-lookup"><span data-stu-id="70b00-106">You might define a custom `Author` attribute class:</span></span>  
  
```csharp  
[System.AttributeUsage(System.AttributeTargets.Class |  
                       System.AttributeTargets.Struct)  
]  
public class AuthorAttribute : System.Attribute  
{  
    private string name;  
    public double version;  
  
    public AuthorAttribute(string name)  
    {  
        this.name = name;  
        version = 1.0;  
    }  
}  
```  
  
 <span data-ttu-id="70b00-107">O nome da classe `AuthorAttribute` é o nome do atributo, `Author` mais o `Attribute` sufixo.</span><span class="sxs-lookup"><span data-stu-id="70b00-107">The class name `AuthorAttribute` is the attribute's name, `Author`, plus the `Attribute` suffix.</span></span> <span data-ttu-id="70b00-108">Ela é derivada de `System.Attribute`, portanto, é uma classe de atributo personalizado.</span><span class="sxs-lookup"><span data-stu-id="70b00-108">It is derived from `System.Attribute`, so it is a custom attribute class.</span></span> <span data-ttu-id="70b00-109">Os parâmetros do construtor são parâmetros posicionais do atributo personalizado.</span><span class="sxs-lookup"><span data-stu-id="70b00-109">The constructor's parameters are the custom attribute's positional parameters.</span></span> <span data-ttu-id="70b00-110">Neste exemplo, `name` é um parâmetro posicional.</span><span class="sxs-lookup"><span data-stu-id="70b00-110">In this example, `name` is a positional parameter.</span></span> <span data-ttu-id="70b00-111">Quaisquer propriedades ou campos públicos de leitura/gravação são chamados de parâmetros.</span><span class="sxs-lookup"><span data-stu-id="70b00-111">Any public read-write fields or properties are named parameters.</span></span> <span data-ttu-id="70b00-112">Nesse caso, `version` é o único parâmetro nomeado.</span><span class="sxs-lookup"><span data-stu-id="70b00-112">In this case, `version` is the only named parameter.</span></span> <span data-ttu-id="70b00-113">Observe o uso do atributo `AttributeUsage` para tornar o atributo `Author` válido apenas na classe e nas declarações `struct`.</span><span class="sxs-lookup"><span data-stu-id="70b00-113">Note the use of the `AttributeUsage` attribute to make the `Author` attribute valid only on class and `struct` declarations.</span></span>  
  
 <span data-ttu-id="70b00-114">Você pode usar esse novo atributo da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="70b00-114">You could use this new attribute as follows:</span></span>  
  
```csharp  
[Author("P. Ackerman", version = 1.1)]  
class SampleClass  
{  
    // P. Ackerman's code goes here...  
}  
```  
  
 <span data-ttu-id="70b00-115">`AttributeUsage` tem um parâmetro nomeado, `AllowMultiple`, com o qual você pode fazer um atributo personalizado de uso único ou mulituso.</span><span class="sxs-lookup"><span data-stu-id="70b00-115">`AttributeUsage` has a named parameter, `AllowMultiple`, with which you can make a custom attribute single-use or multiuse.</span></span> <span data-ttu-id="70b00-116">No exemplo de código a seguir, um atributo multiuso é criado.</span><span class="sxs-lookup"><span data-stu-id="70b00-116">In the following code example, a multiuse attribute is created.</span></span>  
  
```csharp  
[System.AttributeUsage(System.AttributeTargets.Class |  
                       System.AttributeTargets.Struct,  
                       AllowMultiple = true)  // multiuse attribute  
]  
public class AuthorAttribute : System.Attribute  
```  
  
 <span data-ttu-id="70b00-117">No exemplo de código a seguir, vários atributos do mesmo tipo são aplicados a uma classe.</span><span class="sxs-lookup"><span data-stu-id="70b00-117">In the following code example, multiple attributes of the same type are applied to a class.</span></span>  
  
```csharp  
[Author("P. Ackerman", version = 1.1)]  
[Author("R. Koch", version = 1.2)]  
class SampleClass  
{  
    // P. Ackerman's code goes here...  
    // R. Koch's code goes here...  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="70b00-118">Veja também</span><span class="sxs-lookup"><span data-stu-id="70b00-118">See also</span></span>

- <xref:System.Reflection>
- [<span data-ttu-id="70b00-119">Guia de programação C#</span><span class="sxs-lookup"><span data-stu-id="70b00-119">C# Programming Guide</span></span>](../../index.md)
- [<span data-ttu-id="70b00-120">Escrevendo atributos personalizados</span><span class="sxs-lookup"><span data-stu-id="70b00-120">Writing Custom Attributes</span></span>](../../../../standard/attributes/writing-custom-attributes.md)
- [<span data-ttu-id="70b00-121">Reflexão (C#)</span><span class="sxs-lookup"><span data-stu-id="70b00-121">Reflection (C#)</span></span>](../reflection.md)
- [<span data-ttu-id="70b00-122">Atributos (C#)</span><span class="sxs-lookup"><span data-stu-id="70b00-122">Attributes (C#)</span></span>](./index.md)
- [<span data-ttu-id="70b00-123">Acessando atributos usando reflexão (C#)</span><span class="sxs-lookup"><span data-stu-id="70b00-123">Accessing Attributes by Using Reflection (C#)</span></span>](./accessing-attributes-by-using-reflection.md)
- [<span data-ttu-id="70b00-124">AttributeUsage (C#)</span><span class="sxs-lookup"><span data-stu-id="70b00-124">AttributeUsage (C#)</span></span>](../../../language-reference/attributes/general.md)
