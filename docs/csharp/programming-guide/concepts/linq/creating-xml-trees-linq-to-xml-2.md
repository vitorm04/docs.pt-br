---
title: Criando árvores XML em C# (LINQ para XML)
ms.date: 08/31/2018
ms.assetid: cc74234a-0bac-4327-9c8c-5a2ead15b595
ms.openlocfilehash: a77171ebbc07e54f6988fb97aff197b4c6d31721
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/19/2019
ms.locfileid: "69594626"
---
# <a name="creating-xml-trees-in-c-linq-to-xml"></a><span data-ttu-id="22a1d-102">Criando árvores XML em C# (LINQ to XML)</span><span class="sxs-lookup"><span data-stu-id="22a1d-102">Creating XML trees in C# (LINQ to XML)</span></span>
<span data-ttu-id="22a1d-103">Esta seção fornece informações sobre a criação de árvores XML em C#.</span><span class="sxs-lookup"><span data-stu-id="22a1d-103">This section provides information about creating XML trees in C#.</span></span>  
  
 <span data-ttu-id="22a1d-104">Para obter informações sobre como usar os resultados de consultas LINQ como o conteúdo de um <xref:System.Xml.Linq.XElement>, consulte [Construção funcional (LINQ to XML) (C#)](./functional-construction-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="22a1d-104">For information about using the results of LINQ queries as the content for an <xref:System.Xml.Linq.XElement>, see [Functional Construction (LINQ to XML) (C#)](./functional-construction-linq-to-xml.md).</span></span>  
  
## <a name="constructing-elements"></a><span data-ttu-id="22a1d-105">Construindo elementos</span><span class="sxs-lookup"><span data-stu-id="22a1d-105">Constructing elements</span></span>
 <span data-ttu-id="22a1d-106">As assinaturas dos construtores <xref:System.Xml.Linq.XElement> e <xref:System.Xml.Linq.XAttribute> permitem que você passe o conteúdo do elemento ou atributo como argumentos para o construtor.</span><span class="sxs-lookup"><span data-stu-id="22a1d-106">The signatures of the <xref:System.Xml.Linq.XElement> and <xref:System.Xml.Linq.XAttribute> constructors let you pass the contents of the element or attribute as arguments to the constructor.</span></span> <span data-ttu-id="22a1d-107">Como um dos construtores recebe um número variável de argumentos, você pode passar qualquer número de elementos filhos.</span><span class="sxs-lookup"><span data-stu-id="22a1d-107">Because one of the constructors takes a variable number of arguments, you can pass any number of child elements.</span></span> <span data-ttu-id="22a1d-108">Naturalmente, cada um desses elementos filhos pode conter seus próprios elementos filhos.</span><span class="sxs-lookup"><span data-stu-id="22a1d-108">Of course, each of those child elements can contain their own child elements.</span></span> <span data-ttu-id="22a1d-109">Para qualquer elemento, você pode adicionar a quantidade desejada de atributos.</span><span class="sxs-lookup"><span data-stu-id="22a1d-109">For any element, you can add any number of attributes.</span></span>  
  
 <span data-ttu-id="22a1d-110">Ao adicionar objetos <xref:System.Xml.Linq.XNode> (inclusive <xref:System.Xml.Linq.XElement>) ou <xref:System.Xml.Linq.XAttribute>, se o novo conteúdo não tiver um pai, os objetos serão simplesmente anexados à árvore XML.</span><span class="sxs-lookup"><span data-stu-id="22a1d-110">When adding <xref:System.Xml.Linq.XNode> (including <xref:System.Xml.Linq.XElement>) or <xref:System.Xml.Linq.XAttribute> objects, if the new content has no parent, the objects are simply attached to the XML tree.</span></span> <span data-ttu-id="22a1d-111">Se o novo conteúdo já tiver um pai e fizer parte de outra árvore XML, o novo conteúdo será clonado, e o conteúdo recém-clonado será anexado à árvore XML.</span><span class="sxs-lookup"><span data-stu-id="22a1d-111">If the new content already is parented, and is part of another XML tree, the new content is cloned, and the newly cloned content is attached to the XML tree.</span></span> <span data-ttu-id="22a1d-112">O último exemplo deste tópico demonstra isso.</span><span class="sxs-lookup"><span data-stu-id="22a1d-112">The last example in this topic demonstrates this.</span></span>  
  
 <span data-ttu-id="22a1d-113">Para criar um `contacts`<xref:System.Xml.Linq.XElement>, você pode usar o seguinte código:</span><span class="sxs-lookup"><span data-stu-id="22a1d-113">To create a `contacts`<xref:System.Xml.Linq.XElement>, you could use the following code:</span></span>  
  
```csharp  
XElement contacts =  
    new XElement("Contacts",  
        new XElement("Contact",  
            new XElement("Name", "Patrick Hines"),   
            new XElement("Phone", "206-555-0144"),  
            new XElement("Address",  
                new XElement("Street1", "123 Main St"),  
                new XElement("City", "Mercer Island"),  
                new XElement("State", "WA"),  
                new XElement("Postal", "68042")  
            )  
        )  
    );  
```  
  
 <span data-ttu-id="22a1d-114">Se recuado corretamente, o código para criar objetos <xref:System.Xml.Linq.XElement> é muito parecido com a estrutura do XML subjacente.</span><span class="sxs-lookup"><span data-stu-id="22a1d-114">If indented properly, the code to construct <xref:System.Xml.Linq.XElement> objects closely resembles the structure of the underlying XML.</span></span>  
  
## <a name="xelement-constructors"></a><span data-ttu-id="22a1d-115">Construtores de XElement</span><span class="sxs-lookup"><span data-stu-id="22a1d-115">XElement constructors</span></span>  
 <span data-ttu-id="22a1d-116">A classe <xref:System.Xml.Linq.XElement> usa os seguintes construtores na construção funcional.</span><span class="sxs-lookup"><span data-stu-id="22a1d-116">The <xref:System.Xml.Linq.XElement> class uses the following constructors for functional construction.</span></span> <span data-ttu-id="22a1d-117">Observe que há outros construtores para <xref:System.Xml.Linq.XElement>, mas como eles não são usados na construção funcional, eles não são listados aqui.</span><span class="sxs-lookup"><span data-stu-id="22a1d-117">Note that there are some other constructors for <xref:System.Xml.Linq.XElement>, but because they are not used for functional construction they are not listed here.</span></span>  
  
|<span data-ttu-id="22a1d-118">Construtor</span><span class="sxs-lookup"><span data-stu-id="22a1d-118">Constructor</span></span>|<span data-ttu-id="22a1d-119">DESCRIÇÃO</span><span class="sxs-lookup"><span data-stu-id="22a1d-119">Description</span></span>|  
|-----------------|-----------------|  
|`XElement(XName name, object content)`|<span data-ttu-id="22a1d-120">Cria um <xref:System.Xml.Linq.XElement>.</span><span class="sxs-lookup"><span data-stu-id="22a1d-120">Creates an <xref:System.Xml.Linq.XElement>.</span></span> <span data-ttu-id="22a1d-121">O parâmetro `name` especifica o nome do elemento; `content` especifica o conteúdo do elemento.</span><span class="sxs-lookup"><span data-stu-id="22a1d-121">The `name` parameter specifies the name of the element; `content` specifies the content of the element.</span></span>|  
|`XElement(XName name)`|<span data-ttu-id="22a1d-122">Cria um <xref:System.Xml.Linq.XElement> com seu <xref:System.Xml.Linq.XName> inicializado para o nome especificado.</span><span class="sxs-lookup"><span data-stu-id="22a1d-122">Creates an <xref:System.Xml.Linq.XElement> with its <xref:System.Xml.Linq.XName> initialized to the specified name.</span></span>|  
|`XElement(XName name, params object[] content)`|<span data-ttu-id="22a1d-123">Cria um <xref:System.Xml.Linq.XElement> com seu <xref:System.Xml.Linq.XName> inicializado para o nome especificado.</span><span class="sxs-lookup"><span data-stu-id="22a1d-123">Creates an <xref:System.Xml.Linq.XElement> with its <xref:System.Xml.Linq.XName> initialized to the specified name.</span></span> <span data-ttu-id="22a1d-124">Os atributos e/ou elementos filhos são criados a partir do conteúdo da lista de parâmetros.</span><span class="sxs-lookup"><span data-stu-id="22a1d-124">The attributes and/or child elements are created from the contents of the parameter list.</span></span>|  
  
 <span data-ttu-id="22a1d-125">O parâmetro `content` é muito flexível.</span><span class="sxs-lookup"><span data-stu-id="22a1d-125">The `content` parameter is extremely flexible.</span></span> <span data-ttu-id="22a1d-126">Ele dá suporte a qualquer tipo de objeto que seja um filho válido de um <xref:System.Xml.Linq.XElement>.</span><span class="sxs-lookup"><span data-stu-id="22a1d-126">It supports any type of object that is a valid child of an <xref:System.Xml.Linq.XElement>.</span></span> <span data-ttu-id="22a1d-127">As seguintes regras se aplicam aos diferentes tipos de objetos passados neste parâmetro:</span><span class="sxs-lookup"><span data-stu-id="22a1d-127">The following rules apply to different types of objects passed in this parameter:</span></span>  
  
- <span data-ttu-id="22a1d-128">Uma cadeia de caracteres é adicionada como conteúdo de texto.</span><span class="sxs-lookup"><span data-stu-id="22a1d-128">A string is added as text content.</span></span>  
  
- <span data-ttu-id="22a1d-129">Um <xref:System.Xml.Linq.XElement> é adicionado como um elemento filho.</span><span class="sxs-lookup"><span data-stu-id="22a1d-129">An <xref:System.Xml.Linq.XElement> is added as a child element.</span></span>  
  
- <span data-ttu-id="22a1d-130">Um <xref:System.Xml.Linq.XAttribute> é adicionado como um atributo.</span><span class="sxs-lookup"><span data-stu-id="22a1d-130">An <xref:System.Xml.Linq.XAttribute> is added as an attribute.</span></span>  
  
- <span data-ttu-id="22a1d-131">Um <xref:System.Xml.Linq.XProcessingInstruction>, <xref:System.Xml.Linq.XComment> ou <xref:System.Xml.Linq.XText> é adicionado como conteúdo filho.</span><span class="sxs-lookup"><span data-stu-id="22a1d-131">An <xref:System.Xml.Linq.XProcessingInstruction>, <xref:System.Xml.Linq.XComment>, or <xref:System.Xml.Linq.XText> is added as child content.</span></span>  
  
- <span data-ttu-id="22a1d-132">Um <xref:System.Collections.IEnumerable> é enumerado, e essas regras são aplicadas recursivamente aos resultados.</span><span class="sxs-lookup"><span data-stu-id="22a1d-132">An <xref:System.Collections.IEnumerable> is enumerated, and these rules are applied recursively to the results.</span></span>  
  
- <span data-ttu-id="22a1d-133">Para qualquer outro tipo, seu método `ToString` é chamado e o resultado é adicionado como conteúdo de texto.</span><span class="sxs-lookup"><span data-stu-id="22a1d-133">For any other type, its `ToString` method is called and the result is added as text content.</span></span>  
  
### <a name="creating-an-xelement-with-content"></a><span data-ttu-id="22a1d-134">Criando um XElement com conteúdo</span><span class="sxs-lookup"><span data-stu-id="22a1d-134">Creating an XElement with content</span></span>  
 <span data-ttu-id="22a1d-135">Você pode criar um <xref:System.Xml.Linq.XElement> contendo o conteúdo simples com uma única chamada de método.</span><span class="sxs-lookup"><span data-stu-id="22a1d-135">You can create an <xref:System.Xml.Linq.XElement> that contains simple content with a single method call.</span></span> <span data-ttu-id="22a1d-136">Para fazer isso, especifique o conteúdo como o segundo parâmetro, como segue:</span><span class="sxs-lookup"><span data-stu-id="22a1d-136">To do this, specify the content as the second parameter, as follows:</span></span>  
  
```csharp  
XElement n = new XElement("Customer", "Adventure Works");  
Console.WriteLine(n);  
```  
  
 <span data-ttu-id="22a1d-137">Este exemplo gera a seguinte saída:</span><span class="sxs-lookup"><span data-stu-id="22a1d-137">This example produces the following output:</span></span>  
  
```xml  
<Customer>Adventure Works</Customer>  
```  
  
 <span data-ttu-id="22a1d-138">Você pode passar qualquer tipo de objeto como o conteúdo.</span><span class="sxs-lookup"><span data-stu-id="22a1d-138">You can pass any type of object as the content.</span></span> <span data-ttu-id="22a1d-139">Por exemplo, o seguinte código cria um elemento que contém um número de ponto flutuante como conteúdo:</span><span class="sxs-lookup"><span data-stu-id="22a1d-139">For example, the following code creates an element that contains a floating point number as content:</span></span>  
  
```csharp  
XElement n = new XElement("Cost", 324.50);  
Console.WriteLine(n);  
```  
  
 <span data-ttu-id="22a1d-140">Este exemplo gera a seguinte saída:</span><span class="sxs-lookup"><span data-stu-id="22a1d-140">This example produces the following output:</span></span>  
  
```xml  
<Cost>324.5</Cost>  
```  
  
 <span data-ttu-id="22a1d-141">O número de ponto flutuante foi convertido e passado para o construtor.</span><span class="sxs-lookup"><span data-stu-id="22a1d-141">The floating point number is boxed and passed in to the constructor.</span></span> <span data-ttu-id="22a1d-142">O número é convertido em uma cadeia de caracteres e usado como o conteúdo do elemento.</span><span class="sxs-lookup"><span data-stu-id="22a1d-142">The boxed number is converted to a string and used as the content of the element.</span></span>  
  
### <a name="creating-an-xelement-with-a-child-element"></a><span data-ttu-id="22a1d-143">Criando um XElement com um elemento filho</span><span class="sxs-lookup"><span data-stu-id="22a1d-143">Creating an XElement with a child element</span></span>  
 <span data-ttu-id="22a1d-144">Se você passar uma instância da classe <xref:System.Xml.Linq.XElement> para o argumento de conteúdo, o construtor criará um elemento com um elemento filho:</span><span class="sxs-lookup"><span data-stu-id="22a1d-144">If you pass an instance of the <xref:System.Xml.Linq.XElement> class for the content argument, the constructor creates an element with a child element:</span></span>  
  
```csharp  
XElement shippingUnit = new XElement("ShippingUnit",  
    new XElement("Cost", 324.50)  
);  
Console.WriteLine(shippingUnit);  
```  
  
 <span data-ttu-id="22a1d-145">Este exemplo gera a seguinte saída:</span><span class="sxs-lookup"><span data-stu-id="22a1d-145">This example produces the following output:</span></span>  
  
```xml  
<ShippingUnit>  
  <Cost>324.5</Cost>  
</ShippingUnit>  
```  
  
### <a name="creating-an-xelement-with-multiple-child-elements"></a><span data-ttu-id="22a1d-146">Criando um XElement com vários elementos filhos</span><span class="sxs-lookup"><span data-stu-id="22a1d-146">Creating an XElement with multiple child elements</span></span>  
 <span data-ttu-id="22a1d-147">Você pode passar um número de objetos <xref:System.Xml.Linq.XElement> para o conteúdo.</span><span class="sxs-lookup"><span data-stu-id="22a1d-147">You can pass in a number of <xref:System.Xml.Linq.XElement> objects for the content.</span></span> <span data-ttu-id="22a1d-148">Cada um dos objetos <xref:System.Xml.Linq.XElement> é incluído como um elemento filho.</span><span class="sxs-lookup"><span data-stu-id="22a1d-148">Each of the <xref:System.Xml.Linq.XElement> objects is included as a child element.</span></span>  
  
```csharp  
XElement address = new XElement("Address",  
    new XElement("Street1", "123 Main St"),  
    new XElement("City", "Mercer Island"),  
    new XElement("State", "WA"),  
    new XElement("Postal", "68042")  
);  
Console.WriteLine(address);  
```  
  
 <span data-ttu-id="22a1d-149">Este exemplo gera a seguinte saída:</span><span class="sxs-lookup"><span data-stu-id="22a1d-149">This example produces the following output:</span></span>  
  
```xml  
<Address>  
  <Street1>123 Main St</Street1>  
  <City>Mercer Island</City>  
  <State>WA</State>  
  <Postal>68042</Postal>  
</Address>  
```  
  
 <span data-ttu-id="22a1d-150">Por extensão ao exemplo anterior, você pode criar uma árvore XML inteira, desta forma:</span><span class="sxs-lookup"><span data-stu-id="22a1d-150">By extending the above example, you can create an entire XML tree, as follows:</span></span>  
  
```csharp  
XElement contacts =  
    new XElement("Contacts",  
        new XElement("Contact",  
            new XElement("Name", "Patrick Hines"),                                                   
            new XElement("Phone", "206-555-0144"),  
            new XElement("Address",  
                new XElement("Street1", "123 Main St"),  
                new XElement("City", "Mercer Island"),  
                new XElement("State", "WA"),  
                new XElement("Postal", "68042")  
            )  
        )  
    );  
Console.WriteLine(contacts);  
```  
  
 <span data-ttu-id="22a1d-151">Este exemplo gera a seguinte saída:</span><span class="sxs-lookup"><span data-stu-id="22a1d-151">This example produces the following output:</span></span>  
  
```xml  
<Contacts>  
  <Contact>  
    <Name>Patrick Hines</Name>  
    <Phone>206-555-0144</Phone>  
    <Address>  
      <Street1>123 Main St</Street1>  
      <City>Mercer Island</City>  
      <State>WA</State>  
      <Postal>68042</Postal>  
    </Address>  
  </Contact>  
</Contacts>  
```  

### <a name="creating-an-xelement-with-an-xattribute"></a><span data-ttu-id="22a1d-152">Criando um XElement com um XAttribute</span><span class="sxs-lookup"><span data-stu-id="22a1d-152">Creating an XElement with an XAttribute</span></span>
 <span data-ttu-id="22a1d-153">Se você passar uma instância da classe <xref:System.Xml.Linq.XAttribute> para o argumento de conteúdo, o construtor criará um elemento com um atributo:</span><span class="sxs-lookup"><span data-stu-id="22a1d-153">If you pass an instance of the <xref:System.Xml.Linq.XAttribute> class for the content argument, the constructor creates an element with an attribute:</span></span>

```csharp  
XElement phone = new XElement("Phone",  
    new XAttribute("Type", "Home"),  
    "555-555-5555");  
Console.WriteLine(phone);  
```  
  
 <span data-ttu-id="22a1d-154">Este exemplo gera a seguinte saída:</span><span class="sxs-lookup"><span data-stu-id="22a1d-154">This example produces the following output:</span></span>  
  
```xml  
<Phone Type="Home">555-555-5555</Phone>
```   

### <a name="creating-an-empty-element"></a><span data-ttu-id="22a1d-155">Criando um elemento vazio</span><span class="sxs-lookup"><span data-stu-id="22a1d-155">Creating an empty element</span></span>  
 <span data-ttu-id="22a1d-156">Para criar um <xref:System.Xml.Linq.XElement> vazio, você não passa conteúdo para o construtor.</span><span class="sxs-lookup"><span data-stu-id="22a1d-156">To create an empty <xref:System.Xml.Linq.XElement>, you do not pass any content to the constructor.</span></span> <span data-ttu-id="22a1d-157">O seguinte exemplo cria um elemento vazio:</span><span class="sxs-lookup"><span data-stu-id="22a1d-157">The following example creates an empty element:</span></span>  
  
```csharp  
XElement n = new XElement("Customer");  
Console.WriteLine(n);  
```  
  
 <span data-ttu-id="22a1d-158">Este exemplo gera a seguinte saída:</span><span class="sxs-lookup"><span data-stu-id="22a1d-158">This example produces the following output:</span></span>  
  
```xml  
<Customer />  
```  
  
### <a name="attaching-vs-cloning"></a><span data-ttu-id="22a1d-159">Clonagem vs. anexar</span><span class="sxs-lookup"><span data-stu-id="22a1d-159">Attaching vs. cloning</span></span>  
 <span data-ttu-id="22a1d-160">Conforme citado anteriormente, ao adicionar objetos <xref:System.Xml.Linq.XNode> (inclusive <xref:System.Xml.Linq.XElement>) ou <xref:System.Xml.Linq.XAttribute>, se o novo conteúdo não tiver um pai, os objetos serão simplesmente anexados à árvore XML.</span><span class="sxs-lookup"><span data-stu-id="22a1d-160">As mentioned previously, when adding <xref:System.Xml.Linq.XNode> (including <xref:System.Xml.Linq.XElement>) or <xref:System.Xml.Linq.XAttribute> objects, if the new content has no parent, the objects are simply attached to the XML tree.</span></span> <span data-ttu-id="22a1d-161">Se o novo conteúdo já tiver um pai e fizer parte de outra árvore XML, o novo conteúdo será clonado, e o conteúdo recém-clonado será anexado à árvore XML.</span><span class="sxs-lookup"><span data-stu-id="22a1d-161">If the new content already is parented and is part of another XML tree, the new content is cloned, and the newly cloned content is attached to the XML tree.</span></span>  

<span data-ttu-id="22a1d-162">O exemplo a seguir demonstra o comportamento quando você adiciona um elemento com uma relação de pai a uma árvore, e quando você adiciona um elemento sem relação de pai a uma árvore.</span><span class="sxs-lookup"><span data-stu-id="22a1d-162">The following example demonstrates the behavior when you add a parented element to a tree, and when you add an element with no parent to a tree.</span></span>

```csharp  
// Create a tree with a child element.  
XElement xmlTree1 = new XElement("Root",  
    new XElement("Child1", 1)  
);  
  
// Create an element that is not parented.  
XElement child2 = new XElement("Child2", 2);  
  
// Create a tree and add Child1 and Child2 to it.  
XElement xmlTree2 = new XElement("Root",  
    xmlTree1.Element("Child1"),  
    child2  
);  
  
// Compare Child1 identity.  
Console.WriteLine("Child1 was {0}",  
    xmlTree1.Element("Child1") == xmlTree2.Element("Child1") ?  
    "attached" : "cloned");  
  
// Compare Child2 identity.  
Console.WriteLine("Child2 was {0}",  
    child2 == xmlTree2.Element("Child2") ?  
    "attached" : "cloned");  

// The example displays the following output:  
//    Child1 was cloned  
//    Child2 was attached  
```

## <a name="see-also"></a><span data-ttu-id="22a1d-163">Consulte também</span><span class="sxs-lookup"><span data-stu-id="22a1d-163">See also</span></span>

- [<span data-ttu-id="22a1d-164">Criando árvores XML (C#)</span><span class="sxs-lookup"><span data-stu-id="22a1d-164">Creating XML Trees (C#)</span></span>](./linq-to-xml-overview.md)
