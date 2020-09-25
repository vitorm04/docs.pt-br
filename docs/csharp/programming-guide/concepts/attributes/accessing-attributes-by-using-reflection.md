---
title: Acessando atributos usando reflexão (C#)
description: Use a reflexão para obter informações definidas com atributos personalizados em C# usando o método GetCustomAttributes.
ms.date: 07/20/2015
ms.assetid: dce3a696-4ceb-489a-b5e4-322a83052f18
ms.openlocfilehash: 2ed4e844d1c98bcf265572f201bce6679fd642e9
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91202624"
---
# <a name="accessing-attributes-by-using-reflection-c"></a><span data-ttu-id="a63c4-103">Acessando atributos usando reflexão (C#)</span><span class="sxs-lookup"><span data-stu-id="a63c4-103">Accessing Attributes by Using Reflection (C#)</span></span>

<span data-ttu-id="a63c4-104">O fato de que você pode definir atributos personalizados e colocá-los em seu código-fonte seria de pouco valor sem alguma maneira de recuperar essas informações e tomar ação sobre elas.</span><span class="sxs-lookup"><span data-stu-id="a63c4-104">The fact that you can define custom attributes and place them in your source code would be of little value without some way of retrieving that information and acting on it.</span></span> <span data-ttu-id="a63c4-105">Por meio de reflexão, você pode recuperar as informações que foram definidas com atributos personalizados.</span><span class="sxs-lookup"><span data-stu-id="a63c4-105">By using reflection, you can retrieve the information that was defined with custom attributes.</span></span> <span data-ttu-id="a63c4-106">O método principal é o `GetCustomAttributes`, que retorna uma matriz de objetos que são equivalentes, em tempo de execução, aos atributos do código-fonte.</span><span class="sxs-lookup"><span data-stu-id="a63c4-106">The key method is `GetCustomAttributes`, which returns an array of objects that are the run-time equivalents of the source code attributes.</span></span> <span data-ttu-id="a63c4-107">Esse método tem várias versões sobrecarregadas.</span><span class="sxs-lookup"><span data-stu-id="a63c4-107">This method has several overloaded versions.</span></span> <span data-ttu-id="a63c4-108">Para obter mais informações, consulte <xref:System.Attribute>.</span><span class="sxs-lookup"><span data-stu-id="a63c4-108">For more information, see <xref:System.Attribute>.</span></span>  
  
 <span data-ttu-id="a63c4-109">Uma especificação de atributo, como:</span><span class="sxs-lookup"><span data-stu-id="a63c4-109">An attribute specification such as:</span></span>  
  
```csharp  
[Author("P. Ackerman", version = 1.1)]  
class SampleClass  
```  
  
 <span data-ttu-id="a63c4-110">é conceitualmente equivalente a esta:</span><span class="sxs-lookup"><span data-stu-id="a63c4-110">is conceptually equivalent to this:</span></span>  
  
```csharp  
Author anonymousAuthorObject = new Author("P. Ackerman");  
anonymousAuthorObject.version = 1.1;  
```  
  
 <span data-ttu-id="a63c4-111">No entanto, o código não será executado até que `SampleClass` tenha os atributos consultados.</span><span class="sxs-lookup"><span data-stu-id="a63c4-111">However, the code is not executed until `SampleClass` is queried for attributes.</span></span> <span data-ttu-id="a63c4-112">Chamar `GetCustomAttributes` na `SampleClass` faz com que um objeto `Author` seja criado e inicializado como acima.</span><span class="sxs-lookup"><span data-stu-id="a63c4-112">Calling `GetCustomAttributes` on `SampleClass` causes an `Author` object to be constructed and initialized as above.</span></span> <span data-ttu-id="a63c4-113">Se a classe tiver outros atributos, outros objetos de atributo serão construídos de forma semelhante.</span><span class="sxs-lookup"><span data-stu-id="a63c4-113">If the class has other attributes, other attribute objects are constructed similarly.</span></span> <span data-ttu-id="a63c4-114">Então o `GetCustomAttributes` retornará o objeto `Author` e quaisquer outros objetos de atributo em uma matriz.</span><span class="sxs-lookup"><span data-stu-id="a63c4-114">`GetCustomAttributes` then returns the `Author` object and any other attribute objects in an array.</span></span> <span data-ttu-id="a63c4-115">Você poderá iterar sobre essa matriz, determinar quais atributos foram aplicados com base no tipo de cada elemento da matriz e extrair informações dos objetos de atributo.</span><span class="sxs-lookup"><span data-stu-id="a63c4-115">You can then iterate over this array, determine what attributes were applied based on the type of each array element, and extract information from the attribute objects.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a63c4-116">Exemplo</span><span class="sxs-lookup"><span data-stu-id="a63c4-116">Example</span></span>  

 <span data-ttu-id="a63c4-117">Aqui está um exemplo completo.</span><span class="sxs-lookup"><span data-stu-id="a63c4-117">Here is a complete example.</span></span> <span data-ttu-id="a63c4-118">Um atributo personalizado é definido, aplicado a várias entidades e recuperado por meio da reflexão.</span><span class="sxs-lookup"><span data-stu-id="a63c4-118">A custom attribute is defined, applied to several entities, and retrieved via reflection.</span></span>  
  
```csharp  
// Multiuse attribute.  
[System.AttributeUsage(System.AttributeTargets.Class |  
                       System.AttributeTargets.Struct,  
                       AllowMultiple = true)  // Multiuse attribute.  
]  
public class Author : System.Attribute  
{  
    string name;  
    public double version;  
  
    public Author(string name)  
    {  
        this.name = name;  
  
        // Default value.  
        version = 1.0;  
    }  
  
    public string GetName()  
    {  
        return name;  
    }  
}  
  
// Class with the Author attribute.  
[Author("P. Ackerman")]  
public class FirstClass  
{  
    // ...  
}  
  
// Class without the Author attribute.  
public class SecondClass  
{  
    // ...  
}  
  
// Class with multiple Author attributes.  
[Author("P. Ackerman"), Author("R. Koch", version = 2.0)]  
public class ThirdClass  
{  
    // ...  
}  
  
class TestAuthorAttribute  
{  
    static void Test()  
    {  
        PrintAuthorInfo(typeof(FirstClass));  
        PrintAuthorInfo(typeof(SecondClass));  
        PrintAuthorInfo(typeof(ThirdClass));  
    }  
  
    private static void PrintAuthorInfo(System.Type t)  
    {  
        System.Console.WriteLine("Author information for {0}", t);  
  
        // Using reflection.  
        System.Attribute[] attrs = System.Attribute.GetCustomAttributes(t);  // Reflection.  
  
        // Displaying output.  
        foreach (System.Attribute attr in attrs)  
        {  
            if (attr is Author)  
            {  
                Author a = (Author)attr;  
                System.Console.WriteLine("   {0}, version {1:f}", a.GetName(), a.version);  
            }  
        }  
    }  
}  
/* Output:  
    Author information for FirstClass  
       P. Ackerman, version 1.00  
    Author information for SecondClass  
    Author information for ThirdClass  
       R. Koch, version 2.00  
       P. Ackerman, version 1.00  
*/  
```  
  
## <a name="see-also"></a><span data-ttu-id="a63c4-119">Veja também</span><span class="sxs-lookup"><span data-stu-id="a63c4-119">See also</span></span>

- <xref:System.Reflection>
- <xref:System.Attribute>
- [<span data-ttu-id="a63c4-120">Guia de programação C#</span><span class="sxs-lookup"><span data-stu-id="a63c4-120">C# Programming Guide</span></span>](../../index.md)
- [<span data-ttu-id="a63c4-121">Recuperando informações armazenadas em atributos</span><span class="sxs-lookup"><span data-stu-id="a63c4-121">Retrieving Information Stored in Attributes</span></span>](../../../../standard/attributes/retrieving-information-stored-in-attributes.md)
- [<span data-ttu-id="a63c4-122">Reflexão (C#)</span><span class="sxs-lookup"><span data-stu-id="a63c4-122">Reflection (C#)</span></span>](../reflection.md)
- [<span data-ttu-id="a63c4-123">Atributos (C#)</span><span class="sxs-lookup"><span data-stu-id="a63c4-123">Attributes (C#)</span></span>](./index.md)
- [<span data-ttu-id="a63c4-124">Criando atributos personalizados (C#)</span><span class="sxs-lookup"><span data-stu-id="a63c4-124">Creating Custom Attributes (C#)</span></span>](./creating-custom-attributes.md)
