---
title: Eixos linguagem integrados no Visual Basic (LINQ to XML) | Documentos do Microsoft
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
ms.assetid: d450a556-a134-4261-b011-44e399660894
caps.latest.revision: 3
author: dotnet-bot
ms.author: dotnetcontent
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 7ca88aed0772f4fb93ab561af4bd9a1129cbf3c5
ms.contentlocale: pt-br
ms.lasthandoff: 04/12/2017


---
# <a name="language-integrated-axes-in-visual-basic-linq-to-xml"></a><span data-ttu-id="3780a-102">Eixos integrados em linguagem Visual Basic (LINQ to XML)</span><span class="sxs-lookup"><span data-stu-id="3780a-102">Language-Integrated Axes in Visual Basic (LINQ to XML)</span></span>
<span data-ttu-id="3780a-103">Esta seção descreve os recursos incorporados diretamente o [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] idioma para tornar mais fácil acessar o XML.</span><span class="sxs-lookup"><span data-stu-id="3780a-103">This section describes features built directly into the [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] language to make it easy to access XML.</span></span> <span data-ttu-id="3780a-104">Muitos dos exemplos o uso da documentação LINQ to XML esses eixos integrados de [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] .</span><span class="sxs-lookup"><span data-stu-id="3780a-104">Many of the examples in the LINQ to XML documentation use these integrated [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] axes.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="3780a-105">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="3780a-105">In This Section</span></span>  
  
|<span data-ttu-id="3780a-106">Tópico</span><span class="sxs-lookup"><span data-stu-id="3780a-106">Topic</span></span>|<span data-ttu-id="3780a-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="3780a-107">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="3780a-108">Propriedade do Eixo Filho XML</span><span class="sxs-lookup"><span data-stu-id="3780a-108">XML Child Axis Property</span></span>](../../../../visual-basic/language-reference/xml-axis/xml-child-axis-property.md)|<span data-ttu-id="3780a-109">Fornece acesso aos descendentes de um dos seguintes: um <xref:System.Xml.Linq.XElement>objeto, um <xref:System.Xml.Linq.XDocument>objeto, uma coleção de <xref:System.Xml.Linq.XElement>objetos ou uma coleção de <xref:System.Xml.Linq.XDocument>objetos.</xref:System.Xml.Linq.XDocument> </xref:System.Xml.Linq.XElement> </xref:System.Xml.Linq.XDocument> </xref:System.Xml.Linq.XElement></span><span class="sxs-lookup"><span data-stu-id="3780a-109">Provides access to the children of one of the following: an <xref:System.Xml.Linq.XElement> object, an <xref:System.Xml.Linq.XDocument> object, a collection of <xref:System.Xml.Linq.XElement> objects, or a collection of <xref:System.Xml.Linq.XDocument> objects.</span></span> <span data-ttu-id="3780a-110">Esse eixo é equivalente de <xref:System.Xml.Linq.XContainer.Elements%2A>eixo.</xref:System.Xml.Linq.XContainer.Elements%2A></span><span class="sxs-lookup"><span data-stu-id="3780a-110">This axis is equivalent to the <xref:System.Xml.Linq.XContainer.Elements%2A> axis.</span></span>|  
|[<span data-ttu-id="3780a-111">Propriedade de Eixo Descendente XML</span><span class="sxs-lookup"><span data-stu-id="3780a-111">XML Descendant Axis Property</span></span>](../../../../visual-basic/language-reference/xml-axis/xml-descendant-axis-property.md)|<span data-ttu-id="3780a-112">Fornece acesso aos descendentes dos seguintes: um <xref:System.Xml.Linq.XElement>objeto, um <xref:System.Xml.Linq.XDocument>objeto ou uma coleção de <xref:System.Xml.Linq.XElement>objetos.</xref:System.Xml.Linq.XElement> </xref:System.Xml.Linq.XDocument> </xref:System.Xml.Linq.XElement></span><span class="sxs-lookup"><span data-stu-id="3780a-112">Provides access to the descendants of the following: an <xref:System.Xml.Linq.XElement> object, an <xref:System.Xml.Linq.XDocument> object, or a collection of <xref:System.Xml.Linq.XElement> objects.</span></span> <span data-ttu-id="3780a-113">Esse eixo é equivalente de <xref:System.Xml.Linq.XContainer.Descendants%2A>eixo.</xref:System.Xml.Linq.XContainer.Descendants%2A></span><span class="sxs-lookup"><span data-stu-id="3780a-113">This axis is equivalent to the <xref:System.Xml.Linq.XContainer.Descendants%2A> axis.</span></span>|  
|[<span data-ttu-id="3780a-114">Propriedade de Eixo do Atributo XML</span><span class="sxs-lookup"><span data-stu-id="3780a-114">XML Attribute Axis Property</span></span>](../../../../visual-basic/language-reference/xml-axis/xml-attribute-axis-property.md)|<span data-ttu-id="3780a-115">Fornece acesso a um atributo de uma <xref:System.Xml.Linq.XElement>objeto.</xref:System.Xml.Linq.XElement></span><span class="sxs-lookup"><span data-stu-id="3780a-115">Provides access to an attribute of an <xref:System.Xml.Linq.XElement> object.</span></span> <span data-ttu-id="3780a-116">Esse eixo é aproximadamente equivalente para o <xref:System.Xml.Linq.XElement.Attribute%2A>eixo.</xref:System.Xml.Linq.XElement.Attribute%2A></span><span class="sxs-lookup"><span data-stu-id="3780a-116">This axis is roughly equivalent to the <xref:System.Xml.Linq.XElement.Attribute%2A> axis.</span></span> <span data-ttu-id="3780a-117">Esse eixo difere do <xref:System.Xml.Linq.XElement.Attribute%2A>eixo em que ele retorna o valor do atributo, não um <xref:System.Xml.Linq.XAttribute>objeto.</xref:System.Xml.Linq.XAttribute> </xref:System.Xml.Linq.XElement.Attribute%2A></span><span class="sxs-lookup"><span data-stu-id="3780a-117">This axis differs from the <xref:System.Xml.Linq.XElement.Attribute%2A> axis in that it returns the value of the attribute, not an <xref:System.Xml.Linq.XAttribute> object.</span></span>|  
|[<span data-ttu-id="3780a-118">Propriedade do Indexador de Extensão</span><span class="sxs-lookup"><span data-stu-id="3780a-118">Extension Indexer Property</span></span>](../../../../visual-basic/language-reference/xml-axis/extension-indexer-property.md)|<span data-ttu-id="3780a-119">Fornece acesso aos elementos individuais em uma coleção.</span><span class="sxs-lookup"><span data-stu-id="3780a-119">Provides access to individual elements in a collection.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="3780a-120">Consulte também</span><span class="sxs-lookup"><span data-stu-id="3780a-120">See Also</span></span>  
 [<span data-ttu-id="3780a-121">Eixos LINQ to XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3780a-121">LINQ to XML Axes (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml-axes.md)
