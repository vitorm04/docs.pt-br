---
title: Suporte à função msxsl:node-set()
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: d0cbf517-d9f6-4097-9851-4fa62903decd
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 7310d70aa695043a935f9bd74af8e8475eda73d4
ms.sourcegitcommit: a8d3504f0eae1a40bda2b06bd441ba01f1631ef0
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/18/2019
ms.locfileid: "67170873"
---
# <a name="support-for-the-msxslnode-set-function"></a><span data-ttu-id="2444a-102">Suporte à função msxsl:node-set()</span><span class="sxs-lookup"><span data-stu-id="2444a-102">Support for the msxsl:node-set() Function</span></span>
<span data-ttu-id="2444a-103">A função `msxsl:node-set` permite que você converta um fragmento da árvore de resultados em um conjunto de nós.</span><span class="sxs-lookup"><span data-stu-id="2444a-103">The `msxsl:node-set` function enables you to convert a result tree fragment into a node set.</span></span> <span data-ttu-id="2444a-104">O conjunto de nós resultante sempre contém um único nó e é o nó raiz da árvore.</span><span class="sxs-lookup"><span data-stu-id="2444a-104">The resulting node set always contains a single node and is the root node of the tree.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="2444a-105">A classe <xref:System.Xml.Xsl.XslTransform> está obsoleta no .NET Framework 2.0.</span><span class="sxs-lookup"><span data-stu-id="2444a-105">The <xref:System.Xml.Xsl.XslTransform> class is obsolete in the .NET Framework 2.0.</span></span> <span data-ttu-id="2444a-106">Você pode executar a linguagem XSL Transformations (XSLT) usando a classe <xref:System.Xml.Xsl.XslCompiledTransform>.</span><span class="sxs-lookup"><span data-stu-id="2444a-106">You can perform Extensible Stylesheet Language for Transformations (XSLT) transformations using the <xref:System.Xml.Xsl.XslCompiledTransform> class.</span></span> <span data-ttu-id="2444a-107">Confira [Usar a classe XslCompiledTransform](../../../../docs/standard/data/xml/using-the-xslcompiledtransform-class.md) e [Migrar da classe XslTransform](../../../../docs/standard/data/xml/migrating-from-the-xsltransform-class.md) para saber mais.</span><span class="sxs-lookup"><span data-stu-id="2444a-107">See [Using the XslCompiledTransform Class](../../../../docs/standard/data/xml/using-the-xslcompiledtransform-class.md) and [Migrating From the XslTransform Class](../../../../docs/standard/data/xml/migrating-from-the-xsltransform-class.md) for more information.</span></span>  
  
 <span data-ttu-id="2444a-108">A função `msxsl:node-set` permite que você converta um fragmento da árvore de resultados em um conjunto de nós.</span><span class="sxs-lookup"><span data-stu-id="2444a-108">The `msxsl:node-set` function enables you to convert a result tree fragment into a node set.</span></span> <span data-ttu-id="2444a-109">O conjunto de nós resultante sempre contém um único nó e é o nó raiz da árvore.</span><span class="sxs-lookup"><span data-stu-id="2444a-109">The resulting node set always contains a single node and is the root node of the tree.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2444a-110">Exemplo</span><span class="sxs-lookup"><span data-stu-id="2444a-110">Example</span></span>  
 <span data-ttu-id="2444a-111">No exemplo a seguir, `$var` é uma variável que é uma árvore de nós na folha de estilos.</span><span class="sxs-lookup"><span data-stu-id="2444a-111">In the following example, `$var` is a variable that is a node tree in the style sheet.</span></span> <span data-ttu-id="2444a-112">A instrução for-each combinada com a função `node-set` permite que o usuário itere sobre essa árvore de nós como um conjunto de nós.</span><span class="sxs-lookup"><span data-stu-id="2444a-112">The for-each statement combined with the `node-set` function allows the user to iterate over this node tree as a node set.</span></span>  
  
## <a name="nodesetxsl"></a><span data-ttu-id="2444a-113">nodeset.xsl</span><span class="sxs-lookup"><span data-stu-id="2444a-113">nodeset.xsl</span></span>  
  
```xml  
<xsl:stylesheet xmlns:xsl="http://www.w3.org/1999/XSL/Transform"  
                xmlns:msxsl="urn:schemas-microsoft-com:xslt"  
                xmlns:user="http://www.contoso.com"  
                version="1.0">  
    <xsl:variable name="books">  
        <book author="Michael Howard">Writing Secure Code</book>  
        <book author="Michael Kay">XSLT Reference</book>  
    </xsl:variable>  
  
    <xsl:template match="/">  
        <authors>  
            <xsl:for-each select="msxsl:node-set($books)/book">   
                <author><xsl:value-of select="@author"/></author>  
            </xsl:for-each>  
        </authors>  
    </xsl:template>  
</xsl:stylesheet>  
```  
  
## <a name="output"></a><span data-ttu-id="2444a-114">Saída</span><span class="sxs-lookup"><span data-stu-id="2444a-114">Output</span></span>  
 <span data-ttu-id="2444a-115">A saída da transformação é</span><span class="sxs-lookup"><span data-stu-id="2444a-115">The output of the transformation is</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<authors><author>Michael Howard</author><author>Michael Kay</author></authors>  
```  
  
## <a name="see-also"></a><span data-ttu-id="2444a-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="2444a-116">See also</span></span>

- [<span data-ttu-id="2444a-117">A classe XslTransform implementa o processador XSLT</span><span class="sxs-lookup"><span data-stu-id="2444a-117">XslTransform Class Implements the XSLT Processor</span></span>](../../../../docs/standard/data/xml/xsltransform-class-implements-the-xslt-processor.md)
