---
title: Conjuntos de nó nas transformações
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: ad034f0e-ff8b-4a71-9a4c-528c754263c4
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 8160ec37f097b688aa4263a442c08a031f2bfc0c
ms.sourcegitcommit: a8d3504f0eae1a40bda2b06bd441ba01f1631ef0
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/18/2019
ms.locfileid: "67170802"
---
# <a name="node-sets-in-transformations"></a><span data-ttu-id="c3566-102">Conjuntos de nó nas transformações</span><span class="sxs-lookup"><span data-stu-id="c3566-102">Node Sets in Transformations</span></span>
<span data-ttu-id="c3566-103">Conjuntos de nó é um dos quatro tipos de dados básicos que são retornados das expressões de idioma do caminho de XML (XPath).</span><span class="sxs-lookup"><span data-stu-id="c3566-103">Node sets are one of four basic data types that are returned from XML Path Language (XPath) expressions.</span></span> <span data-ttu-id="c3566-104">Um conjunto de nó, que é uma coleção não ordenada de nós sem duplicatas, criada na ordem de documento, pode ser atribuído a um variável em uma folha de estilos.</span><span class="sxs-lookup"><span data-stu-id="c3566-104">A node set, which is an unordered collection of nodes without duplicates, created in document order, can be assigned to a variable in a style sheet.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="c3566-105">A classe <xref:System.Xml.Xsl.XslTransform> está obsoleta no .NET Framework 2.0.</span><span class="sxs-lookup"><span data-stu-id="c3566-105">The <xref:System.Xml.Xsl.XslTransform> class is obsolete in the .NET Framework 2.0.</span></span> <span data-ttu-id="c3566-106">Você pode executar a linguagem XSL Transformations (XSLT) usando a classe <xref:System.Xml.Xsl.XslCompiledTransform>.</span><span class="sxs-lookup"><span data-stu-id="c3566-106">You can perform Extensible Stylesheet Language for Transformations (XSLT) transformations using the <xref:System.Xml.Xsl.XslCompiledTransform> class.</span></span> <span data-ttu-id="c3566-107">Confira [Usar a classe XslCompiledTransform](../../../../docs/standard/data/xml/using-the-xslcompiledtransform-class.md) e [Migrar da classe XslTransform](../../../../docs/standard/data/xml/migrating-from-the-xsltransform-class.md) para saber mais.</span><span class="sxs-lookup"><span data-stu-id="c3566-107">See [Using the XslCompiledTransform Class](../../../../docs/standard/data/xml/using-the-xslcompiledtransform-class.md) and [Migrating From the XslTransform Class](../../../../docs/standard/data/xml/migrating-from-the-xsltransform-class.md) for more information.</span></span>  
  
 <span data-ttu-id="c3566-108">Conjuntos de nó é um dos quatro tipos de dados básicos que são retornados de expressões XPath.</span><span class="sxs-lookup"><span data-stu-id="c3566-108">Node sets are one of four basic data types that are returned from XPath expressions.</span></span> <span data-ttu-id="c3566-109">Um conjunto de nó, que é uma coleção não ordenada de nós sem duplicatas, criada na ordem de documento, pode ser atribuído a um variável em uma folha de estilos.</span><span class="sxs-lookup"><span data-stu-id="c3566-109">A node set, which is an unordered collection of nodes without duplicates, created in document order, can be assigned to a variable in a style sheet.</span></span> <span data-ttu-id="c3566-110">Este conjunto de nó, que é um resultado de uma expressão XPath usado em um atributo de `select` em uma transformação, tem o mesmo comportamento que um nó definir o modelo de objeto (DOM) de documento XML.</span><span class="sxs-lookup"><span data-stu-id="c3566-110">This node set, which is a result of an XPath expression used in a `select` attribute in a transformation, has the same behavior as a node set from the XML Document Object Model (DOM).</span></span> <span data-ttu-id="c3566-111">Você pode navegar em um conjunto de nós usando um conjunto de métodos mostrados em [Navegação do nó usando XPathNavigator](../../../../docs/standard/data/xml/node-set-navigation-using-xpathnavigator.md), diferentemente de um fragmento de árvore de resultado, que usa <xref:System.Xml.XPath.XPathNodeIterator> para navegação.</span><span class="sxs-lookup"><span data-stu-id="c3566-111">You can navigate a node set using a set of methods shown in [Node Set Navigation Using XPathNavigator](../../../../docs/standard/data/xml/node-set-navigation-using-xpathnavigator.md), unlike a result tree fragment or result tree fragment, which uses the <xref:System.Xml.XPath.XPathNodeIterator> for navigation.</span></span>  
  
 <span data-ttu-id="c3566-112">O exemplo de código a seguir mostra como iterar sobre um nó definida quando um elemento de `variable` ou de `parameter` em uma folha de estilos é avaliada como um conjunto de nó.</span><span class="sxs-lookup"><span data-stu-id="c3566-112">The following code sample shows how to iterate over a node set when a `variable` or `parameter` element in a style sheet evaluates to a node set.</span></span>  
  
## <a name="style-sheet"></a><span data-ttu-id="c3566-113">Folha de Estilos</span><span class="sxs-lookup"><span data-stu-id="c3566-113">Style Sheet</span></span>  
  
```xml  
<xsl:stylesheet xmlns:xsl="http://www.w3.org/1999/XSL/Transform" version="1.0">  
  
    <xsl:variable name="x" select="bookstore/book/title"></xsl:variable>  
  
    <xsl:template match="/">  
        <xsl:for-each select="$x">  
            ******  
            <xsl:value-of select="."></xsl:value-of>  
            ******  
        </xsl:for-each>  
    </xsl:template>  
  
</xsl:stylesheet>  
```  
  
## <a name="input"></a><span data-ttu-id="c3566-114">Entrada</span><span class="sxs-lookup"><span data-stu-id="c3566-114">Input</span></span>  
  
```xml  
<bookstore>  
   <book style="autobiography">  
      <title>Seven Years in Trenton</title>  
   </book>  
  
   <book style="autobiography">  
      <title>Seven Years in Trenton2</title>  
   </book>  
  
   <book style="textbook">  
      <title>History of Trenton Vol 3</title>  
   </book>  
</bookstore>  
```  
  
## <a name="output"></a><span data-ttu-id="c3566-115">Saída</span><span class="sxs-lookup"><span data-stu-id="c3566-115">Output</span></span>  
  
```  
******  
Seven Years in Trenton  
******  
  
******  
Seven Years in Trenton2  
******  
  
******  
History of Trenton Vol 3  
******  
```  
  
## <a name="see-also"></a><span data-ttu-id="c3566-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c3566-116">See also</span></span>

- <xref:System.Xml.XPath.XPathNodeIterator>
- [<span data-ttu-id="c3566-117">Transformações XSLT com a classe XslTransform</span><span class="sxs-lookup"><span data-stu-id="c3566-117">XSLT Transformations with the XslTransform Class</span></span>](../../../../docs/standard/data/xml/xslt-transformations-with-the-xsltransform-class.md)
- [<span data-ttu-id="c3566-118">A classe XslTransform implementa o processador XSLT</span><span class="sxs-lookup"><span data-stu-id="c3566-118">XslTransform Class Implements the XSLT Processor</span></span>](../../../../docs/standard/data/xml/xsltransform-class-implements-the-xslt-processor.md)
