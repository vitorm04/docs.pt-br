---
title: XPathNodeIterator nas transformações
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: 2bc6ddc6-674a-4f75-b264-abc35e4e5857
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 6f71d409729707f4af93fd7f8d5b82a99404579b
ms.sourcegitcommit: 6eac9a01ff5d70c6d18460324c016a3612c5e268
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/17/2018
ms.locfileid: "45687590"
---
# <a name="xpathnodeiterator-in-transformations"></a><span data-ttu-id="0f6ee-102">XPathNodeIterator nas transformações</span><span class="sxs-lookup"><span data-stu-id="0f6ee-102">XPathNodeIterator in Transformations</span></span>
<span data-ttu-id="0f6ee-103"><xref:System.Xml.XPath.XPathNodeIterator> fornece métodos para iterar sobre um conjunto de nós criados como resultado de uma consulta de idioma do caminho de XML (XPath) ou de um fragmento da árvore de resultado convertida em um nó definido por meio do método nó- definido.</span><span class="sxs-lookup"><span data-stu-id="0f6ee-103">The <xref:System.Xml.XPath.XPathNodeIterator> provides methods to iterate over a set of nodes created as the result of an XML Path Language (XPath) query or a result tree fragment converted to a node set by use of the node-set method.</span></span> <span data-ttu-id="0f6ee-104"><xref:System.Xml.XPath.XPathNodeIterator> permite que você para iterar sobre os nós dentro desse conjunto de nó.</span><span class="sxs-lookup"><span data-stu-id="0f6ee-104">The <xref:System.Xml.XPath.XPathNodeIterator> enables you to iterate over the nodes within that node set.</span></span> <span data-ttu-id="0f6ee-105">Uma vez que um conjunto de nó é recuperado, a classe de <xref:System.Xml.XPath.XPathNodeIterator> fornece um cursor somente leitura, e somente para frente ao dataset selecionado de nós.</span><span class="sxs-lookup"><span data-stu-id="0f6ee-105">Once a node set is retrieved, the <xref:System.Xml.XPath.XPathNodeIterator> class provides a read-only, forward-only cursor to the selected set of nodes.</span></span> <span data-ttu-id="0f6ee-106">O nó é criado na ordem de documento, o que move em chamar esse método para o nó seguir na ordem de documento.</span><span class="sxs-lookup"><span data-stu-id="0f6ee-106">The node set is created in document order, so calling this method moves to the next node in document order.</span></span> <span data-ttu-id="0f6ee-107"><xref:System.Xml.XPath.XPathNodeIterator> não cria uma árvore de nós de todos os nós no dataset.</span><span class="sxs-lookup"><span data-stu-id="0f6ee-107"><xref:System.Xml.XPath.XPathNodeIterator> does not build a node tree of all the nodes in the set.</span></span> <span data-ttu-id="0f6ee-108">Em vez disso, fornece uma janela de único nó nos dados, expõe o nó subjacente que aponta para a medida que você se move ao redor de árvore.</span><span class="sxs-lookup"><span data-stu-id="0f6ee-108">Instead, it provides a single node window into the data, exposing the underlying node it points to as you move around in the tree.</span></span> <span data-ttu-id="0f6ee-109">Os métodos e propriedades disponíveis de classe de <xref:System.Xml.XPath.XPathNodeIterator> permite que você obtenha informações do nó atual.</span><span class="sxs-lookup"><span data-stu-id="0f6ee-109">The methods and properties available from the <xref:System.Xml.XPath.XPathNodeIterator> class enable you to get information from the current node.</span></span> <span data-ttu-id="0f6ee-110">Para obter uma lista de métodos e propriedades disponíveis, consulte <xref:System.Windows.Forms.ToolBar>.</span><span class="sxs-lookup"><span data-stu-id="0f6ee-110">For a list of the available methods and properties, see <xref:System.Windows.Forms.ToolBar>.</span></span>  
  
 <span data-ttu-id="0f6ee-111">Desde que <xref:System.Xml.XPath.XPathNodeIterator> se move sobre um conjunto de nós criados de uma consulta XPath e se avança apenas, a maneira para mover é usando o método <xref:System.Xml.XPath.XPathNodeIterator.MoveNext%2A> .</span><span class="sxs-lookup"><span data-stu-id="0f6ee-111">Since an <xref:System.Xml.XPath.XPathNodeIterator> moves over a set of nodes created from an XPath query and moves forward only, the way to move is by using the <xref:System.Xml.XPath.XPathNodeIterator.MoveNext%2A> method.</span></span> <span data-ttu-id="0f6ee-112">O tipo de retorno desse método é `Boolean`, retornando `true` se move para o nó selecionado seguinte, e `false` se não há mais nó selecionado.</span><span class="sxs-lookup"><span data-stu-id="0f6ee-112">The return type of this method is `Boolean`, returning `true` if it moves to the next selected node, and `false` if there are no more selected nodes.</span></span> <span data-ttu-id="0f6ee-113">Se retorna `true`, a lista a seguir mostra as propriedades disponíveis:</span><span class="sxs-lookup"><span data-stu-id="0f6ee-113">If it returns `true`, the following list shows the properties available:</span></span>  
  
-   <xref:System.Xml.XPath.XPathNodeIterator.Current%2A>  
  
-   <xref:System.Xml.XPath.XPathNodeIterator.CurrentPosition%2A>  
  
-   <xref:System.Xml.XPath.XPathNodeIterator.Count%2A>  
  
 <span data-ttu-id="0f6ee-114">Quando você está examinando um nó definida pela primeira vez, uma chamada a <xref:System.Xml.XPath.XPathNodeIterator.MoveNext%2A> deve ser feito para posicionar <xref:System.Xml.XPath.XPathNodeIterator> no primeiro nó do dataset selecionado.</span><span class="sxs-lookup"><span data-stu-id="0f6ee-114">When you are looking at a node set for the first time, a call to <xref:System.Xml.XPath.XPathNodeIterator.MoveNext%2A> must be made to position the <xref:System.Xml.XPath.XPathNodeIterator> on the first node of the selected set.</span></span> <span data-ttu-id="0f6ee-115">Isso permite que um loop de quando é escrito.</span><span class="sxs-lookup"><span data-stu-id="0f6ee-115">This allows a while loop to be written.</span></span>  
  
 <span data-ttu-id="0f6ee-116">O exemplo de código a seguir mostra como passar <xref:System.Xml.XPath.XPathNodeIterator> a <xref:System.Xml.Xsl.XslTransform> como um parâmetro em <xref:System.Xml.Xsl.XsltArgumentList>.</span><span class="sxs-lookup"><span data-stu-id="0f6ee-116">The following code example shows how to pass an <xref:System.Xml.XPath.XPathNodeIterator> to an <xref:System.Xml.Xsl.XslTransform> as a parameter in the <xref:System.Xml.Xsl.XsltArgumentList>.</span></span> <span data-ttu-id="0f6ee-117">A entrada ao código é **books.xml**, e a folha de estilos é **text.xsl**.</span><span class="sxs-lookup"><span data-stu-id="0f6ee-117">The input to the code is **books.xml**, and the style sheet is **text.xsl**.</span></span> <span data-ttu-id="0f6ee-118">O arquivo **test.xml** é o <xref:System.Xml.XPath.XPathDocument>.</span><span class="sxs-lookup"><span data-stu-id="0f6ee-118">The file **test.xml** is the <xref:System.Xml.XPath.XPathDocument>.</span></span>  
  
```vb  
Imports System  
Imports System.IO  
Imports System.Xml  
Imports System.Xml.Xsl  
Imports System.Xml.XPath  
Imports System.Text  
  
Public Class sample  
  
   Public Shared Sub Main()  
      Dim Doc As New XPathDocument("books.xml")  
      Dim nav As XPathNavigator = Doc.CreateNavigator()  
      Dim Iterator As XPathNodeIterator = nav.Select("/bookstore/book")  
  
      Dim arg As New XsltArgumentList()  
      arg.AddParam("param1", "", Iterator)  
  
      Dim xslt As New XslTransform()  
      xslt.Load("test.xsl")  
  
      Dim xd As New XPathDocument("test.xml")  
  
      Dim strmTemp = New FileStream("out.xml", FileMode.Create, FileAccess.ReadWrite)  
      xslt.Transform(xd, arg, strmTemp, Nothing)  
   End Sub 'Main  
End Class 'sample  
```  
  
```csharp  
using System;  
using System.IO;  
using System.Xml;  
using System.Xml.Xsl;  
using System.Xml.XPath;  
using System.Text;  
  
public class sample  
{  
    public static void Main()  
    {  
        XPathDocument Doc = new XPathDocument("books.xml");  
        XPathNavigator nav = Doc.CreateNavigator();  
        XPathNodeIterator Iterator = nav.Select("/bookstore/book");  
  
        XsltArgumentList arg = new XsltArgumentList();  
        arg.AddParam("param1", "", Iterator);  
  
        XslTransform xslt = new XslTransform();  
        xslt.Load("test.xsl");  
  
        XPathDocument xd = new XPathDocument("test.xml");  
  
        Stream strmTemp = new FileStream("out.xml", FileMode.Create, FileAccess.ReadWrite);  
        xslt.Transform(xd, arg, strmTemp, null);  
    }  
}  
```  
  
## <a name="booksxml"></a><span data-ttu-id="0f6ee-119">books.xml</span><span class="sxs-lookup"><span data-stu-id="0f6ee-119">books.xml</span></span>  
  
```xml  
<?xml version='1.0'?>  
<!-- This file represents a fragment of a book store inventory database. -->  
<bookstore specialty="novel">  
    <book style="autobiography">  
    <title>Seven Years in Trenton</title>  
        <author>  
            <first-name>Jay</first-name>  
            <last-name>Adams</last-name>  
            <award>Trenton Literary Review Honorable Mention</award>  
            <country>USA</country>  
        </author>  
        <price>12</price>  
    </book>  
    <book style="textbook">  
        <title>History of Trenton</title>  
        <author>  
            <first-name>Kim</first-name>  
            <last-name>Akers</last-name>  
            <publication>  
                Selected Short Stories of  
                <first-name>Scott</first-name>  
                <last-name>Bishop</last-name>  
                <country>US</country>  
            </publication>  
        </author>  
        <price>55</price>  
    </book>  
</bookstore>  
```  
  
## <a name="testxsl"></a><span data-ttu-id="0f6ee-120">test.xsl</span><span class="sxs-lookup"><span data-stu-id="0f6ee-120">test.xsl</span></span>  
  
```xml  
<xsl:stylesheet version="1.0" xmlns:xsl="http://www.w3.org/1999/XSL/Transform"  
xmlns:msxsl="urn:schemas-microsoft-com:xslt" exclude-result-prefixes="msxsl">  
  
<xsl:output method="xml" indent="yes"/>  
<xsl:param name="param1"/>  
  
<xsl:template match="/">  
    <out>  
        <xsl:for-each select="$param1/title">  
            <title><xsl:value-of select="."/></title>  
        </xsl:for-each>  
    </out>  
</xsl:template>  
  
</xsl:stylesheet>  
```  
  
## <a name="testxml"></a><span data-ttu-id="0f6ee-121">test.xml</span><span class="sxs-lookup"><span data-stu-id="0f6ee-121">test.xml</span></span>  
  
```xml  
<Title attr="Test">this is a test</Title>  
```  
  
## <a name="output-outxml"></a><span data-ttu-id="0f6ee-122">Saída (out.xml)</span><span class="sxs-lookup"><span data-stu-id="0f6ee-122">Output (out.xml)</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<out>  
  <title>Seven Years in Trenton</title>  
  <title>History of Trenton</title>  
</out>  
```  
  
## <a name="see-also"></a><span data-ttu-id="0f6ee-123">Consulte também</span><span class="sxs-lookup"><span data-stu-id="0f6ee-123">See also</span></span>

- [<span data-ttu-id="0f6ee-124">A classe XslTransform implementa o processador XSLT</span><span class="sxs-lookup"><span data-stu-id="0f6ee-124">XslTransform Class Implements the XSLT Processor</span></span>](../../../../docs/standard/data/xml/xsltransform-class-implements-the-xslt-processor.md)
