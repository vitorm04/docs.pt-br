---
title: "Como preencher uma árvore XML com um XmlWriter (LINQ to XML) (C#)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-csharp
ms.topic: article
ms.assetid: cd5674d1-5c54-4efc-ba68-e23b2875295f
caps.latest.revision: "3"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 2df0626d0376973aeaa09876c6737c93dd671da4
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-populate-an-xml-tree-with-an-xmlwriter-linq-to-xml-c"></a><span data-ttu-id="884ce-102">Como preencher uma árvore XML com um XmlWriter (LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="884ce-102">How to: Populate an XML Tree with an XmlWriter (LINQ to XML) (C#)</span></span>
<span data-ttu-id="884ce-103">Uma maneira de preencher uma árvore XML é usar <xref:System.Xml.Linq.XContainer.CreateWriter%2A> para criar um <xref:System.Xml.XmlWriter> e escrever no <xref:System.Xml.XmlWriter>.</span><span class="sxs-lookup"><span data-stu-id="884ce-103">One way to populate an XML tree is to use <xref:System.Xml.Linq.XContainer.CreateWriter%2A> to create an <xref:System.Xml.XmlWriter>, and then write to the <xref:System.Xml.XmlWriter>.</span></span> <span data-ttu-id="884ce-104">A árvore XML é preenchida com todos os nós que são escritos no <xref:System.Xml.XmlWriter>.</span><span class="sxs-lookup"><span data-stu-id="884ce-104">The XML tree is populated with all nodes that are written to the <xref:System.Xml.XmlWriter>.</span></span>  
  
 <span data-ttu-id="884ce-105">Você normalmente usa este método quando usa [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] com outra classe que espera escrever em um <xref:System.Xml.XmlWriter>, por exemplo, <xref:System.Xml.Xsl.XslCompiledTransform>.</span><span class="sxs-lookup"><span data-stu-id="884ce-105">You would typically use this method when you use [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] with another class that expects to write to an <xref:System.Xml.XmlWriter>, such as <xref:System.Xml.Xsl.XslCompiledTransform>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="884ce-106">Exemplo</span><span class="sxs-lookup"><span data-stu-id="884ce-106">Example</span></span>  
 <span data-ttu-id="884ce-107">Um uso possível para <xref:System.Xml.Linq.XContainer.CreateWriter%2A> é ao chamar uma transformação XSLT.</span><span class="sxs-lookup"><span data-stu-id="884ce-107">One possible use for <xref:System.Xml.Linq.XContainer.CreateWriter%2A> is when invoking an XSLT transformation.</span></span> <span data-ttu-id="884ce-108">Este exemplo cria uma árvore XML, cria <xref:System.Xml.XmlReader> da árvore XML, cria um novo documento e, em seguida, cria <xref:System.Xml.XmlWriter> para gravar no novo documento.</span><span class="sxs-lookup"><span data-stu-id="884ce-108">This example creates an XML tree, creates an <xref:System.Xml.XmlReader> from the XML tree, creates a new document, and then creates an <xref:System.Xml.XmlWriter> to write into the new document.</span></span> <span data-ttu-id="884ce-109">Ele então chama a transformação XSLT, passando no <xref:System.Xml.XmlReader> e no <xref:System.Xml.XmlWriter>.</span><span class="sxs-lookup"><span data-stu-id="884ce-109">It then invokes the XSLT transformation, passing in <xref:System.Xml.XmlReader> and <xref:System.Xml.XmlWriter>.</span></span> <span data-ttu-id="884ce-110">Depois que a transformação for concluída com êxito, a nova árvore XML será preenchida com os resultados da transformação.</span><span class="sxs-lookup"><span data-stu-id="884ce-110">After the transformation successfully completes, the new XML tree is populated with the results of the transformation.</span></span>  
  
```csharp  
string xslMarkup = @"<?xml version='1.0'?>  
<xsl:stylesheet xmlns:xsl='http://www.w3.org/1999/XSL/Transform' version='1.0'>  
    <xsl:template match='/Parent'>  
        <Root>  
            <C1>  
            <xsl:value-of select='Child1'/>  
            </C1>  
            <C2>  
            <xsl:value-of select='Child2'/>  
            </C2>  
        </Root>  
    </xsl:template>  
</xsl:stylesheet>";  
  
XDocument xmlTree = new XDocument(  
    new XElement("Parent",  
        new XElement("Child1", "Child1 data"),  
        new XElement("Child2", "Child2 data")  
    )  
);  
  
XDocument newTree = new XDocument();  
using (XmlWriter writer = newTree.CreateWriter())  
{  
    // Load the style sheet.  
    XslCompiledTransform xslt = new XslCompiledTransform();  
    xslt.Load(XmlReader.Create(new StringReader(xslMarkup)));  
  
    // Execute the transformation and output the results to a writer.  
    xslt.Transform(xmlTree.CreateReader(), writer);  
}  
  
Console.WriteLine(newTree);  
```  
  
 <span data-ttu-id="884ce-111">Este exemplo gera a seguinte saída:</span><span class="sxs-lookup"><span data-stu-id="884ce-111">This example produces the following output:</span></span>  
  
```xml  
<Root>  
  <C1>Child1 data</C1>  
  <C2>Child2 data</C2>  
</Root>  
```  
  
## <a name="see-also"></a><span data-ttu-id="884ce-112">Consulte também</span><span class="sxs-lookup"><span data-stu-id="884ce-112">See Also</span></span>  
 <xref:System.Xml.Linq.XContainer.CreateWriter%2A>  
 <xref:System.Xml.XmlWriter>  
 <xref:System.Xml.Xsl.XslCompiledTransform>  
 [<span data-ttu-id="884ce-113">Criando árvores XML (C#)</span><span class="sxs-lookup"><span data-stu-id="884ce-113">Creating XML Trees (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/creating-xml-trees.md)
