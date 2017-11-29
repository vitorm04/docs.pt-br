---
title: Eixos integrados em linguagem Visual Basic (LINQ to XML)
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d450a556-a134-4261-b011-44e399660894
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: d648ba7c8710f73c4aeb8dad3983f219c5fe1815
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="language-integrated-axes-in-visual-basic-linq-to-xml"></a><span data-ttu-id="9fd9b-102">Eixos integrados em linguagem Visual Basic (LINQ to XML)</span><span class="sxs-lookup"><span data-stu-id="9fd9b-102">Language-Integrated Axes in Visual Basic (LINQ to XML)</span></span>
<span data-ttu-id="9fd9b-103">Esta seção descreve os recursos incorporados diretamente o [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] idioma para tornar mais fácil acessar o XML.</span><span class="sxs-lookup"><span data-stu-id="9fd9b-103">This section describes features built directly into the [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] language to make it easy to access XML.</span></span> <span data-ttu-id="9fd9b-104">Muitos dos exemplos o uso da documentação LINQ to XML esses eixos integrados de [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="9fd9b-104">Many of the examples in the LINQ to XML documentation use these integrated [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] axes.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="9fd9b-105">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="9fd9b-105">In This Section</span></span>  
  
|<span data-ttu-id="9fd9b-106">Tópico</span><span class="sxs-lookup"><span data-stu-id="9fd9b-106">Topic</span></span>|<span data-ttu-id="9fd9b-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="9fd9b-107">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="9fd9b-108">Propriedade do Eixo Filho XML</span><span class="sxs-lookup"><span data-stu-id="9fd9b-108">XML Child Axis Property</span></span>](../../../../visual-basic/language-reference/xml-axis/xml-child-axis-property.md)|<span data-ttu-id="9fd9b-109">Fornece acesso aos descendentes de um dos seguintes: um objeto de <xref:System.Xml.Linq.XElement> , um objeto de <xref:System.Xml.Linq.XDocument> , uma coleção de objetos <xref:System.Xml.Linq.XElement> , ou uma coleção de <xref:System.Xml.Linq.XDocument> objeto.</span><span class="sxs-lookup"><span data-stu-id="9fd9b-109">Provides access to the children of one of the following: an <xref:System.Xml.Linq.XElement> object, an <xref:System.Xml.Linq.XDocument> object, a collection of <xref:System.Xml.Linq.XElement> objects, or a collection of <xref:System.Xml.Linq.XDocument> objects.</span></span> <span data-ttu-id="9fd9b-110">Esse eixo é equivalente ao eixo de <xref:System.Xml.Linq.XContainer.Elements%2A> .</span><span class="sxs-lookup"><span data-stu-id="9fd9b-110">This axis is equivalent to the <xref:System.Xml.Linq.XContainer.Elements%2A> axis.</span></span>|  
|[<span data-ttu-id="9fd9b-111">Propriedade de Eixo Descendente XML</span><span class="sxs-lookup"><span data-stu-id="9fd9b-111">XML Descendant Axis Property</span></span>](../../../../visual-basic/language-reference/xml-axis/xml-descendant-axis-property.md)|<span data-ttu-id="9fd9b-112">Fornece acesso aos descendentes dos seguintes: um objeto de <xref:System.Xml.Linq.XElement> , um objeto de <xref:System.Xml.Linq.XDocument> , ou uma coleção de <xref:System.Xml.Linq.XElement> objeto.</span><span class="sxs-lookup"><span data-stu-id="9fd9b-112">Provides access to the descendants of the following: an <xref:System.Xml.Linq.XElement> object, an <xref:System.Xml.Linq.XDocument> object, or a collection of <xref:System.Xml.Linq.XElement> objects.</span></span> <span data-ttu-id="9fd9b-113">Esse eixo é equivalente ao eixo de <xref:System.Xml.Linq.XContainer.Descendants%2A> .</span><span class="sxs-lookup"><span data-stu-id="9fd9b-113">This axis is equivalent to the <xref:System.Xml.Linq.XContainer.Descendants%2A> axis.</span></span>|  
|[<span data-ttu-id="9fd9b-114">Propriedade de Eixo do Atributo XML</span><span class="sxs-lookup"><span data-stu-id="9fd9b-114">XML Attribute Axis Property</span></span>](../../../../visual-basic/language-reference/xml-axis/xml-attribute-axis-property.md)|<span data-ttu-id="9fd9b-115">Fornece acesso a um atributo de um objeto de <xref:System.Xml.Linq.XElement> .</span><span class="sxs-lookup"><span data-stu-id="9fd9b-115">Provides access to an attribute of an <xref:System.Xml.Linq.XElement> object.</span></span> <span data-ttu-id="9fd9b-116">Esse eixo é aproximadamente equivalente ao eixo de <xref:System.Xml.Linq.XElement.Attribute%2A> .</span><span class="sxs-lookup"><span data-stu-id="9fd9b-116">This axis is roughly equivalent to the <xref:System.Xml.Linq.XElement.Attribute%2A> axis.</span></span> <span data-ttu-id="9fd9b-117">Esse eixo difere do eixo de <xref:System.Xml.Linq.XElement.Attribute%2A> que retorna o valor do atributo, não um objeto de <xref:System.Xml.Linq.XAttribute> .</span><span class="sxs-lookup"><span data-stu-id="9fd9b-117">This axis differs from the <xref:System.Xml.Linq.XElement.Attribute%2A> axis in that it returns the value of the attribute, not an <xref:System.Xml.Linq.XAttribute> object.</span></span>|  
|[<span data-ttu-id="9fd9b-118">Propriedade do Indexador de Extensão</span><span class="sxs-lookup"><span data-stu-id="9fd9b-118">Extension Indexer Property</span></span>](../../../../visual-basic/language-reference/xml-axis/extension-indexer-property.md)|<span data-ttu-id="9fd9b-119">Fornece acesso aos elementos individuais em uma coleção.</span><span class="sxs-lookup"><span data-stu-id="9fd9b-119">Provides access to individual elements in a collection.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="9fd9b-120">Consulte também</span><span class="sxs-lookup"><span data-stu-id="9fd9b-120">See Also</span></span>  
 [<span data-ttu-id="9fd9b-121">Eixos LINQ to XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9fd9b-121">LINQ to XML Axes (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml-axes.md)
