---
title: Visão geral do LINQ to XML (C#)
ms.date: 10/30/2018
ms.assetid: 716b94d3-0091-4de1-8e05-41bc069fa9dd
ms.openlocfilehash: ec09984486710f29417615499e7b1c565b51b932
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54502202"
---
# <a name="linq-to-xml-overview-c"></a><span data-ttu-id="e5af1-102">Visão geral do LINQ to XML (C#)</span><span class="sxs-lookup"><span data-stu-id="e5af1-102">LINQ to XML Overview (C#)</span></span>
<span data-ttu-id="e5af1-103">O XML tem sido amplamente adotado como um modo de formatar dados em muitos contextos.</span><span class="sxs-lookup"><span data-stu-id="e5af1-103">XML has been widely adopted as a way to format data in many contexts.</span></span> <span data-ttu-id="e5af1-104">Por exemplo, você pode encontrar XML na Web, em arquivos de configuração, em arquivos do Microsoft Office Word e em bancos de dados.</span><span class="sxs-lookup"><span data-stu-id="e5af1-104">For example, you can find XML on the Web, in configuration files, in Microsoft Office Word files, and in databases.</span></span>  
  
 <span data-ttu-id="e5af1-105">O [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] é uma abordagem atualizada e redesenhada para a programação com XML.</span><span class="sxs-lookup"><span data-stu-id="e5af1-105">[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] is an up-to-date, redesigned approach to programming with XML.</span></span> <span data-ttu-id="e5af1-106">Ele oferece os recursos de modificação de documentos na memória do DOM (Document Object Model), bem como o suporte a expressões de consulta [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)].</span><span class="sxs-lookup"><span data-stu-id="e5af1-106">It provides the in-memory document modification capabilities of the Document Object Model (DOM), and supports [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] query expressions.</span></span> <span data-ttu-id="e5af1-107">Embora essas expressões de consulta sejam sintaticamente diferentes de XPath, elas oferecem uma funcionalidade semelhante.</span><span class="sxs-lookup"><span data-stu-id="e5af1-107">Although these query expressions are syntactically different from XPath, they provide similar functionality.</span></span>  
  
## <a name="linq-to-xml-developers"></a><span data-ttu-id="e5af1-108">Desenvolvedores em LINQ to XML</span><span class="sxs-lookup"><span data-stu-id="e5af1-108">LINQ to XML Developers</span></span>  
 <span data-ttu-id="e5af1-109">O [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] se destina a uma variedade de desenvolvedores.</span><span class="sxs-lookup"><span data-stu-id="e5af1-109">[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] targets a variety of developers.</span></span> <span data-ttu-id="e5af1-110">Para um desenvolvedor médio que deseja apenas ter algo concluído, o [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] torna o XML mais simples ao oferecer uma experiência de consulta que é semelhante ao SQL.</span><span class="sxs-lookup"><span data-stu-id="e5af1-110">For an average developer who just wants to get something done, [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] makes XML easier by providing a query experience that is similar to SQL.</span></span> <span data-ttu-id="e5af1-111">Com apenas um pouco de estudo, os programadores podem aprender a escrever consultas sucintas e eficientes na linguagem de programação de sua escolha.</span><span class="sxs-lookup"><span data-stu-id="e5af1-111">With just a bit of study, programmers can learn to write succinct and powerful queries in their programming language of choice.</span></span>  
  
 <span data-ttu-id="e5af1-112">Os desenvolvedores profissionais podem usar o [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] para aumentar consideravelmente sua produtividade.</span><span class="sxs-lookup"><span data-stu-id="e5af1-112">Professional developers can use [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] to greatly increase their productivity.</span></span> <span data-ttu-id="e5af1-113">Com o [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], eles podem escrever um código menor que seja mais expressivo, mais compacto e mais eficiente.</span><span class="sxs-lookup"><span data-stu-id="e5af1-113">With [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], they can write less code that is more expressive, more compact, and more powerful.</span></span> <span data-ttu-id="e5af1-114">Eles podem usar expressões de consulta de vários domínios de dados ao mesmo tempo.</span><span class="sxs-lookup"><span data-stu-id="e5af1-114">They can use query expressions from multiple data domains at the same time.</span></span>  
  
## <a name="what-is-linq-to-xml"></a><span data-ttu-id="e5af1-115">O que é o LINQ to XML?</span><span class="sxs-lookup"><span data-stu-id="e5af1-115">What Is LINQ to XML?</span></span>  
 <span data-ttu-id="e5af1-116">O [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] é uma interface de programação XML na memória e habilitada para LINQ que permite que você trabalhe com XML de dentro das linguagens de programação [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)].</span><span class="sxs-lookup"><span data-stu-id="e5af1-116">[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] is a LINQ-enabled, in-memory XML programming interface that enables you to work with XML from within the [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] programming languages.</span></span>  
  
 <span data-ttu-id="e5af1-117">O [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] é como o DOM (Modelo de Objeto do Documento) no sentido de levar o documento XML para a memória.</span><span class="sxs-lookup"><span data-stu-id="e5af1-117">[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] is like the Document Object Model (DOM) in that it brings the XML document into memory.</span></span> <span data-ttu-id="e5af1-118">Você pode consultar e modificar o documento e, depois de modificá-lo, pode salvá-lo em um arquivo ou serializá-lo e enviá-lo pela Internet.</span><span class="sxs-lookup"><span data-stu-id="e5af1-118">You can query and modify the document, and after you modify it you can save it to a file or serialize it and send it over the Internet.</span></span> <span data-ttu-id="e5af1-119">No entanto, [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] é diferente do DOM: Ele fornece um novo modelo de objeto mais leve e mais fácil de se trabalhar e que aproveita as funcionalidades de linguagem em C#.</span><span class="sxs-lookup"><span data-stu-id="e5af1-119">However, [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] differs from DOM: It provides a new object model that is lighter weight and easier to work with, and that takes advantage of language features in C#.</span></span>  
  
 <span data-ttu-id="e5af1-120">A vantagem mais importante do [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] é sua integração com o [!INCLUDE[vbteclinqext](~/includes/vbteclinqext-md.md)].</span><span class="sxs-lookup"><span data-stu-id="e5af1-120">The most important advantage of [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] is its integration with [!INCLUDE[vbteclinqext](~/includes/vbteclinqext-md.md)].</span></span> <span data-ttu-id="e5af1-121">Essa integração permite que você escreva consultas no documento XML na memória para recuperar coleções de elementos e atributos.</span><span class="sxs-lookup"><span data-stu-id="e5af1-121">This integration enables you to write queries on the in-memory XML document to retrieve collections of elements and attributes.</span></span> <span data-ttu-id="e5af1-122">O recurso de consulta do [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] é comparável em funcionalidade (embora não em sintaxe) a XPath e XQuery.</span><span class="sxs-lookup"><span data-stu-id="e5af1-122">The query capability of [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] is comparable in functionality (although not in syntax) to XPath and XQuery.</span></span> <span data-ttu-id="e5af1-123">A integração de [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] no C# oferece tipagem mais forte, verificação em tempo de compilação e melhor suporte de depuração.</span><span class="sxs-lookup"><span data-stu-id="e5af1-123">The integration of [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] in C# provides stronger typing, compile-time checking, and improved debugger support.</span></span>  
  
 <span data-ttu-id="e5af1-124">Outra vantagem do [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] é a capacidade de usar resultados da consulta como parâmetros para construtores de objeto <xref:System.Xml.Linq.XElement> e <xref:System.Xml.Linq.XAttribute>, o que permite uma abordagem eficiente para a criação de árvores XML.</span><span class="sxs-lookup"><span data-stu-id="e5af1-124">Another advantage of [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] is the ability to use query results as parameters to <xref:System.Xml.Linq.XElement> and <xref:System.Xml.Linq.XAttribute> object constructors enables a powerful approach to creating XML trees.</span></span> <span data-ttu-id="e5af1-125">Essa abordagem, chamada de *construção funcional*, permite que os desenvolvedores transformem com facilidade árvores XML de uma forma em outra.</span><span class="sxs-lookup"><span data-stu-id="e5af1-125">This approach, called *functional construction*, enables developers to easily transform XML trees from one shape to another.</span></span>  
  
 <span data-ttu-id="e5af1-126">Por exemplo, você pode ter uma ordem de compra XML típica, conforme descrito em [Arquivo XML de exemplo: Ordem de compra típica (LINQ to XML)](sample-xml-file-typical-purchase-order-linq-to-xml-1.md).</span><span class="sxs-lookup"><span data-stu-id="e5af1-126">For example, you might have a typical XML purchase order as described in [Sample XML File: Typical Purchase Order (LINQ to XML)](sample-xml-file-typical-purchase-order-linq-to-xml-1.md).</span></span> <span data-ttu-id="e5af1-127">Usando o [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], você poderia executar a consulta a seguir para obter o valor do atributo de número de peça para cada elemento de item na ordem de compra:</span><span class="sxs-lookup"><span data-stu-id="e5af1-127">By using [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], you could run the following query to obtain the part number attribute value for every item element in the purchase order:</span></span>  
  
```csharp
// Load the XML file from our project directory containing the purchase orders
var filename = "PurchaseOrder.xml";
var currentDirectory = Directory.GetCurrentDirectory();
var purchaseOrderFilepath = Path.Combine(currentDirectory, filename);

XElement purchaseOrder = XElement.Load($"{purchaseOrderFilepath}");

IEnumerable<string> partNos =  from item in purchaseOrder.Descendants("Item")  
                               select (string) item.Attribute("PartNumber");  
``` 
<span data-ttu-id="e5af1-128">Isso pode ser regravado no formulário de sintaxe do método:</span><span class="sxs-lookup"><span data-stu-id="e5af1-128">This can be rewritten in method syntax form:</span></span>

```csharp
IEnumerable<string> partNos = purchaseOrder.Descendants("Item").Select(x => (string) x.Attribute("PartNumber"));
```

<span data-ttu-id="e5af1-129">Como outro exemplo, você poderia querer uma lista, classificada por número de peça, dos itens com um valor maior que $ 100.</span><span class="sxs-lookup"><span data-stu-id="e5af1-129">As another example, you might want a list, sorted by part number, of the items with a value greater than $100.</span></span> <span data-ttu-id="e5af1-130">Para obter essas informações, você poderia executar a seguinte consulta:</span><span class="sxs-lookup"><span data-stu-id="e5af1-130">To obtain this information, you could run the following query:</span></span>  
  
```csharp 
// Load the XML file from our project directory containing the purchase orders
var filename = "PurchaseOrder.xml";
var currentDirectory = Directory.GetCurrentDirectory();
var purchaseOrderFilepath = Path.Combine(currentDirectory, filename);

XElement purchaseOrder = XElement.Load($"{purchaseOrderFilepath}");

IEnumerable<XElement> pricesByPartNos =  from item in purchaseOrder.Descendants("Item")  
                                 where (int) item.Element("Quantity") * (decimal) item.Element("USPrice") > 100  
                                 orderby (string)item.Element("PartNumber")  
                                 select item;  
```  

<span data-ttu-id="e5af1-131">Outra vez, isso pode ser regravado no formulário de sintaxe do método:</span><span class="sxs-lookup"><span data-stu-id="e5af1-131">Again, this can be rewritten in method syntax form:</span></span>

```csharp
IEnumerable<XElement> pricesByPartNos = purchaseOrder.Descendants("Item")
                                        .Where(item => (int)item.Element("Quantity") * (decimal)item.Element("USPrice") > 100)
                                        .OrderBy(order => order.Element("PartNumber"));
```

 <span data-ttu-id="e5af1-132">Além desses recursos de [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)], o [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] oferece uma interface de programação XML aprimorada.</span><span class="sxs-lookup"><span data-stu-id="e5af1-132">In addition to these [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] capabilities, [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] provides an improved XML programming interface.</span></span> <span data-ttu-id="e5af1-133">Usando o [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], você pode:</span><span class="sxs-lookup"><span data-stu-id="e5af1-133">Using [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], you can:</span></span>  
  
-   <span data-ttu-id="e5af1-134">Carregar XML de [arquivos](how-to-load-xml-from-a-file.md) ou [fluxos](how-to-stream-xml-fragments-from-an-xmlreader.md).</span><span class="sxs-lookup"><span data-stu-id="e5af1-134">Load XML from [files](how-to-load-xml-from-a-file.md) or [streams](how-to-stream-xml-fragments-from-an-xmlreader.md).</span></span>  
  
-   <span data-ttu-id="e5af1-135">Serializar o XML em arquivos ou fluxos.</span><span class="sxs-lookup"><span data-stu-id="e5af1-135">Serialize XML to files or streams.</span></span>  
  
-   <span data-ttu-id="e5af1-136">Crie XML a partir do zero usando a construção funcional.</span><span class="sxs-lookup"><span data-stu-id="e5af1-136">Create XML from scratch by using functional construction.</span></span>  
  
-   <span data-ttu-id="e5af1-137">Consultar o XML usando eixos do tipo XPath.</span><span class="sxs-lookup"><span data-stu-id="e5af1-137">Query XML using XPath-like axes.</span></span>  
  
-   <span data-ttu-id="e5af1-138">Manipular a árvore XML na memória usando métodos como <xref:System.Xml.Linq.XContainer.Add%2A>, <xref:System.Xml.Linq.XNode.Remove%2A>, <xref:System.Xml.Linq.XNode.ReplaceWith%2A> e <xref:System.Xml.Linq.XElement.SetValue%2A>.</span><span class="sxs-lookup"><span data-stu-id="e5af1-138">Manipulate the in-memory XML tree by using methods such as <xref:System.Xml.Linq.XContainer.Add%2A>, <xref:System.Xml.Linq.XNode.Remove%2A>, <xref:System.Xml.Linq.XNode.ReplaceWith%2A>, and <xref:System.Xml.Linq.XElement.SetValue%2A>.</span></span>  
  
-   <span data-ttu-id="e5af1-139">Validar árvores XML usando XSD.</span><span class="sxs-lookup"><span data-stu-id="e5af1-139">Validate XML trees using XSD.</span></span>  
  
-   <span data-ttu-id="e5af1-140">Usar uma combinação desses recursos para transformar árvores XML de uma forma em outra.</span><span class="sxs-lookup"><span data-stu-id="e5af1-140">Use a combination of these features to transform XML trees from one shape into another.</span></span>  
  
## <a name="creating-xml-trees"></a><span data-ttu-id="e5af1-141">Criando árvores XML</span><span class="sxs-lookup"><span data-stu-id="e5af1-141">Creating XML Trees</span></span>  
 <span data-ttu-id="e5af1-142">Uma das vantagens mais significativas da programação com [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] é que é fácil criar árvores XML.</span><span class="sxs-lookup"><span data-stu-id="e5af1-142">One of the most significant advantages of programming with [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] is that it is easy to create XML trees.</span></span> <span data-ttu-id="e5af1-143">Por exemplo, para criar uma árvore XML pequena, você pode escrever código da seguinte forma:</span><span class="sxs-lookup"><span data-stu-id="e5af1-143">For example, to create a small XML tree, you can write code as follows:</span></span>  
  
```csharp  
XElement contacts =  
new XElement("Contacts",  
    new XElement("Contact",  
        new XElement("Name", "Patrick Hines"),  
        new XElement("Phone", "206-555-0144",   
            new XAttribute("Type", "Home")),  
        new XElement("phone", "425-555-0145",  
            new XAttribute("Type", "Work")),  
        new XElement("Address",  
            new XElement("Street1", "123 Main St"),  
            new XElement("City", "Mercer Island"),  
            new XElement("State", "WA"),  
            new XElement("Postal", "68042")  
        )  
    )  
);  
```  
  
 <span data-ttu-id="e5af1-144">Para obter mais informações, consulte [Criando árvores XML (C#)](../../../../csharp/programming-guide/concepts/linq/creating-xml-trees.md).</span><span class="sxs-lookup"><span data-stu-id="e5af1-144">For more information, see [Creating XML Trees (C#)](../../../../csharp/programming-guide/concepts/linq/creating-xml-trees.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e5af1-145">Consulte também</span><span class="sxs-lookup"><span data-stu-id="e5af1-145">See also</span></span>

- <xref:System.Xml.Linq>
- [<span data-ttu-id="e5af1-146">Introdução (LINQ to XML)</span><span class="sxs-lookup"><span data-stu-id="e5af1-146">Getting Started (LINQ to XML)</span></span>](../../../../csharp/programming-guide/concepts/linq/getting-started-linq-to-xml.md)
