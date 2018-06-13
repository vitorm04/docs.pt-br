---
title: Atributo cref (Guia de Programação em C#)
ms.date: 07/20/2015
helpviewer_keywords:
- cref [C#]
ms.assetid: 66a6b0e5-b961-4504-a461-3a4cf481fc8b
ms.openlocfilehash: a89c7170de956bae65f7018130ba27e61c076376
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33337019"
---
# <a name="cref-attribute-c-programming-guide"></a><span data-ttu-id="92918-102">Atributo cref (Guia de Programação em C#)</span><span class="sxs-lookup"><span data-stu-id="92918-102">cref Attribute (C# Programming Guide)</span></span>
<span data-ttu-id="92918-103">O atributo `cref` em uma marca de documentação XML significa “referência de código”.</span><span class="sxs-lookup"><span data-stu-id="92918-103">The `cref` attribute in an XML documentation tag means "code reference."</span></span> <span data-ttu-id="92918-104">Ele especifica que o texto interno da marca é um elemento de código, como um tipo, método ou propriedade.</span><span class="sxs-lookup"><span data-stu-id="92918-104">It specifies that the inner text of the tag is a code element, such as a type, method, or property.</span></span> <span data-ttu-id="92918-105">Ferramentas de documentação, como o [Sandcastle](https://github.com/EWSoftware/SHFB), usam os atributos `cref` para gerar automaticamente os hiperlinks para a página em que o tipo ou membro está documentado.</span><span class="sxs-lookup"><span data-stu-id="92918-105">Documentation tools like [Sandcastle](https://github.com/EWSoftware/SHFB) use the `cref` attributes to automatically generate hyperlinks to the page where the type or member is documented.</span></span>  
  
## <a name="example"></a><span data-ttu-id="92918-106">Exemplo</span><span class="sxs-lookup"><span data-stu-id="92918-106">Example</span></span>  
 <span data-ttu-id="92918-107">A exemplo a seguir mostra os atributos `cref` usados em marcas [\<see>](../../../csharp/programming-guide/xmldoc/see.md).</span><span class="sxs-lookup"><span data-stu-id="92918-107">The following example shows `cref` attributes used in [\<see>](../../../csharp/programming-guide/xmldoc/see.md) tags.</span></span>  
  
 [!code-csharp[csProgGuideDocComments#3](../../../csharp/programming-guide/xmldoc/codesnippet/CSharp/cref-attribute_1.cs)]  
  
 <span data-ttu-id="92918-108">Quando compilado, o programa produz o seguinte arquivo XML.</span><span class="sxs-lookup"><span data-stu-id="92918-108">When compiled, the program produces the following XML file.</span></span> <span data-ttu-id="92918-109">Observe que o atributo `cref` do método `GetZero`, por exemplo, foi transformado em `"M:TestNamespace.TestClass.GetZero"` pelo compilador.</span><span class="sxs-lookup"><span data-stu-id="92918-109">Notice that the `cref` attribute for the `GetZero` method, for example, has been transformed by the compiler to `"M:TestNamespace.TestClass.GetZero"`.</span></span> <span data-ttu-id="92918-110">O prefixo “M:” significa “método” e é uma convenção reconhecida por ferramentas de documentação como o Sandcastle.</span><span class="sxs-lookup"><span data-stu-id="92918-110">The "M:" prefix means "method" and is a convention that is recognized by documentation tools such as Sandcastle.</span></span> <span data-ttu-id="92918-111">Para obter uma lista completa de prefixos, consulte [Processando o Arquivo XML](../../../csharp/programming-guide/xmldoc/processing-the-xml-file.md).</span><span class="sxs-lookup"><span data-stu-id="92918-111">For a complete list of prefixes, see [Processing the XML File](../../../csharp/programming-guide/xmldoc/processing-the-xml-file.md).</span></span>  
  
```xml  
<?xml version="1.0"?>  
<doc>  
    <assembly>  
        <name>CRefTest</name>  
    </assembly>  
    <members>  
        <member name="T:TestNamespace.TestClass">  
            <summary>  
            TestClass contains cref examples.  
            </summary>  
        </member>  
        <member name="M:TestNamespace.TestClass.#ctor">  
            <summary>  
            This sample shows how to specify the <see cref="T:TestNamespace.TestClass"/> constructor as a cref attribute.   
            </summary>  
        </member>  
        <member name="M:TestNamespace.TestClass.#ctor(System.Int32)">  
            <summary>  
            This sample shows how to specify the <see cref="M:TestNamespace.TestClass.#ctor(System.Int32)"/> constructor as a cref attribute.   
            </summary>  
        </member>  
        <member name="M:TestNamespace.TestClass.GetZero">  
            <summary>  
            The GetZero method.  
            </summary>  
            <example>   
            This sample shows how to call the <see cref="M:TestNamespace.TestClass.GetZero"/> method.  
            <code>  
            class TestClass   
            {  
                static int Main()   
                {  
                    return GetZero();  
                }  
            }  
            </code>  
            </example>  
        </member>  
        <member name="M:TestNamespace.TestClass.GetGenericValue``1(``0)">  
            <summary>  
            The GetGenericValue method.  
            </summary>  
            <remarks>   
            This sample shows how to specify the <see cref="M:TestNamespace.TestClass.GetGenericValue``1(``0)"/> method as a cref attribute.  
            </remarks>  
        </member>  
        <member name="T:TestNamespace.GenericClass`1">  
            <summary>  
            GenericClass.  
            </summary>  
            <remarks>   
            This example shows how to specify the <see cref="T:TestNamespace.GenericClass`1"/> type as a cref attribute.  
            </remarks>  
        </member>  
    </members>    <members>  
        <member name="T:TestNamespace.TestClass">  
            <summary>  
            TestClass contains two cref examples.  
            </summary>  
        </member>  
        <member name="M:TestNamespace.TestClass.GetZero">  
            <summary>  
            The GetZero method.  
            </summary>  
            <example> This sample shows how to call the <see cref="M:TestNamespace.TestClass.GetZero"/> method.  
            <code>  
            class TestClass   
            {  
                static int Main()   
                {  
                    return GetZero();  
                }  
            }  
            </code>  
            </example>  
        </member>  
        <member name="M:TestNamespace.TestClass.GetGenericValue``1(``0)">  
            <summary>  
            The GetGenericValue method.  
            </summary>  
            <remarks>   
            This sample shows how to specify the <see cref="M:TestNamespace.TestClass.GetGenericValue``1(``0)"/> method as a cref attribute.  
            </remarks>  
        </member>  
        <member name="T:TestNamespace.GenericClass`1">  
            <summary>  
            GenericClass.  
            </summary>  
            <remarks>   
            This example shows how to specify the <see cref="T:TestNamespace.GenericClass`1"/> type as a cref attribute.  
            </remarks>  
        </member>  
    </members>  
</doc>  
```  
  
## <a name="see-also"></a><span data-ttu-id="92918-112">Consulte também</span><span class="sxs-lookup"><span data-stu-id="92918-112">See Also</span></span>  
 [<span data-ttu-id="92918-113">Comentários da documentação XML</span><span class="sxs-lookup"><span data-stu-id="92918-113">XML Documentation Comments</span></span>](../../../csharp/programming-guide/xmldoc/xml-documentation-comments.md)  
 [<span data-ttu-id="92918-114">Marcas recomendadas para comentários de documentação</span><span class="sxs-lookup"><span data-stu-id="92918-114">Recommended Tags for Documentation Comments</span></span>](../../../csharp/programming-guide/xmldoc/recommended-tags-for-documentation-comments.md)
