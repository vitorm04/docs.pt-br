---
title: "Construção funcional (LINQ to XML) (C#)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-csharp
ms.topic: article
ms.assetid: 57a82bcf-de03-4f1c-a0c8-9a76e989d542
caps.latest.revision: "3"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: f357de98fae60b3d0b6548ef195b462b4e2f6a5a
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="functional-construction-linq-to-xml-c"></a><span data-ttu-id="c07c6-102">Construção funcional (LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="c07c6-102">Functional Construction (LINQ to XML) (C#)</span></span>
[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]<span data-ttu-id="c07c6-103"> fornece uma maneira eficiente de criar elementos XML chamada *construção funcional*.</span><span class="sxs-lookup"><span data-stu-id="c07c6-103"> provides a powerful way to create XML elements called *functional construction*.</span></span> <span data-ttu-id="c07c6-104">Construção funcional é a capacidade de criar uma árvore XML em uma única instrução.</span><span class="sxs-lookup"><span data-stu-id="c07c6-104">Functional construction is the ability to create an XML tree in a single statement.</span></span>  
  
 <span data-ttu-id="c07c6-105">Há vários recursos chave da interface de programação do [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] que permitem a construção funcional:</span><span class="sxs-lookup"><span data-stu-id="c07c6-105">There are several key features of the [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] programming interface that enable functional construction:</span></span>  
  
-   <span data-ttu-id="c07c6-106">O construtor <xref:System.Xml.Linq.XElement> utiliza vários tipos de argumentos para o conteúdo.</span><span class="sxs-lookup"><span data-stu-id="c07c6-106">The <xref:System.Xml.Linq.XElement> constructor takes various types of arguments for content.</span></span> <span data-ttu-id="c07c6-107">Por exemplo, você pode passar outro objeto <xref:System.Xml.Linq.XElement>, que se torna um elemento filho.</span><span class="sxs-lookup"><span data-stu-id="c07c6-107">For example, you can pass another <xref:System.Xml.Linq.XElement> object, which becomes a child element.</span></span> <span data-ttu-id="c07c6-108">Você pode passar um objeto <xref:System.Xml.Linq.XAttribute>, que se torna um atributo do elemento.</span><span class="sxs-lookup"><span data-stu-id="c07c6-108">You can pass an <xref:System.Xml.Linq.XAttribute> object, which becomes an attribute of the element.</span></span> <span data-ttu-id="c07c6-109">Ou você pode passar qualquer outro tipo de objeto, que é convertido em uma cadeia de caracteres e torna-se o conteúdo de texto do elemento.</span><span class="sxs-lookup"><span data-stu-id="c07c6-109">Or you can pass any other type of object, which is converted to a string and becomes the text content of the element.</span></span>  
  
-   <span data-ttu-id="c07c6-110">O construtor <xref:System.Xml.Linq.XElement> utiliza uma matriz de `params` do tipo <xref:System.Object>, para que você possa passar qualquer número de objetos para o construtor.</span><span class="sxs-lookup"><span data-stu-id="c07c6-110">The <xref:System.Xml.Linq.XElement> constructor takes a `params` array of type <xref:System.Object>, so that you can pass any number of objects to the constructor.</span></span> <span data-ttu-id="c07c6-111">Isso permite que você crie um elemento que tem o conteúdo complexo.</span><span class="sxs-lookup"><span data-stu-id="c07c6-111">This enables you to create an element that has complex content.</span></span>  
  
-   <span data-ttu-id="c07c6-112">Se um objeto implementar <xref:System.Collections.Generic.IEnumerable%601>, a coleção no objeto será enumerada, e todos os itens da coleção serão adicionados.</span><span class="sxs-lookup"><span data-stu-id="c07c6-112">If an object implements <xref:System.Collections.Generic.IEnumerable%601>, the collection in the object is enumerated, and all items in the collection are added.</span></span> <span data-ttu-id="c07c6-113">Se a coleção contiver objetos <xref:System.Xml.Linq.XElement> ou <xref:System.Xml.Linq.XAttribute>, cada item da coleção será adicionado separadamente.</span><span class="sxs-lookup"><span data-stu-id="c07c6-113">If the collection contains <xref:System.Xml.Linq.XElement> or <xref:System.Xml.Linq.XAttribute> objects, each item in the collection is added separately.</span></span> <span data-ttu-id="c07c6-114">Isso é importante porque permite que você passe os resultados de uma consulta [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] para o construtor.</span><span class="sxs-lookup"><span data-stu-id="c07c6-114">This is important because it lets you pass the results of a [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] query to the constructor.</span></span>  
  
 <span data-ttu-id="c07c6-115">Esses recursos permitem escrever código para criar uma árvore XML.</span><span class="sxs-lookup"><span data-stu-id="c07c6-115">These features enable you to write code to create an XML tree.</span></span> <span data-ttu-id="c07c6-116">A seguir está um exemplo:</span><span class="sxs-lookup"><span data-stu-id="c07c6-116">The following is an example:</span></span>  
  
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
  
 <span data-ttu-id="c07c6-117">Esses recursos também permitem que você escreva código que usa os resultados de consultas [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] quando cria uma árvore XML, da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="c07c6-117">These features also enable you to write code that uses the results of [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] queries when you create an XML tree, as follows:</span></span>  
  
```csharp  
XElement srcTree = new XElement("Root",  
    new XElement("Element", 1),  
    new XElement("Element", 2),  
    new XElement("Element", 3),  
    new XElement("Element", 4),  
    new XElement("Element", 5)  
);  
XElement xmlTree = new XElement("Root",  
    new XElement("Child", 1),  
    new XElement("Child", 2),  
    from el in srcTree.Elements()  
    where (int)el > 2  
    select el  
);  
Console.WriteLine(xmlTree);  
```  
  
 <span data-ttu-id="c07c6-118">Este exemplo gera a seguinte saída:</span><span class="sxs-lookup"><span data-stu-id="c07c6-118">This example produces the following output:</span></span>  
  
```xml  
<Root>  
  <Child>1</Child>  
  <Child>2</Child>  
  <Element>3</Element>  
  <Element>4</Element>  
  <Element>5</Element>  
</Root>  
```  
  
## <a name="see-also"></a><span data-ttu-id="c07c6-119">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c07c6-119">See Also</span></span>  
 [<span data-ttu-id="c07c6-120">Criando árvores XML (C#)</span><span class="sxs-lookup"><span data-stu-id="c07c6-120">Creating XML Trees (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/creating-xml-trees.md)
