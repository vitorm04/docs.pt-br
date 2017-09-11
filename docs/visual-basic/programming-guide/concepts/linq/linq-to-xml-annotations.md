---
title: LINQ to XML Annotations2 | Documentos do Microsoft
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
ms.assetid: c3e8b3ff-fceb-4428-b0ca-1ed6f128aac8
caps.latest.revision: 3
author: dotnet-bot
ms.author: dotnetcontent
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 97f5386630ba687e4401ee0cfb70f7170e273a53
ms.contentlocale: pt-br
ms.lasthandoff: 04/12/2017


---
# <a name="linq-to-xml-annotations"></a><span data-ttu-id="93c49-102">Anotações LINQ to XML</span><span class="sxs-lookup"><span data-stu-id="93c49-102">LINQ to XML Annotations</span></span>
<span data-ttu-id="93c49-103">Anotações em [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] permite associar qualquer objeto arbitrário de qualquer tipo arbitrário com qualquer componente XML em uma árvore XML.</span><span class="sxs-lookup"><span data-stu-id="93c49-103">Annotations in [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] enable you to associate any arbitrary object of any arbitrary type with any XML component in an XML tree.</span></span>  
  
 <span data-ttu-id="93c49-104">Para adicionar uma anotação a um componente XML, como um <xref:System.Xml.Linq.XElement>ou <xref:System.Xml.Linq.XAttribute>, chamar o <xref:System.Xml.Linq.XObject.AddAnnotation%2A>método.</xref:System.Xml.Linq.XObject.AddAnnotation%2A> </xref:System.Xml.Linq.XAttribute> </xref:System.Xml.Linq.XElement></span><span class="sxs-lookup"><span data-stu-id="93c49-104">To add an annotation to an XML component, such as an <xref:System.Xml.Linq.XElement> or <xref:System.Xml.Linq.XAttribute>, you call the <xref:System.Xml.Linq.XObject.AddAnnotation%2A> method.</span></span> <span data-ttu-id="93c49-105">Você recupera anotações pelo tipo.</span><span class="sxs-lookup"><span data-stu-id="93c49-105">You retrieve annotations by type.</span></span>  
  
 <span data-ttu-id="93c49-106">Observe que as anotações não são parte de infoset XML; não são serializados ou não estão desserializados.</span><span class="sxs-lookup"><span data-stu-id="93c49-106">Note that annotations are not part of the XML infoset; they are not serialized or deserialized.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="93c49-107">Métodos</span><span class="sxs-lookup"><span data-stu-id="93c49-107">Methods</span></span>  
 <span data-ttu-id="93c49-108">Você pode usar os seguintes métodos para trabalhar com anotações:</span><span class="sxs-lookup"><span data-stu-id="93c49-108">You can use the following methods when working with annotations:</span></span>  
  
|<span data-ttu-id="93c49-109">Método</span><span class="sxs-lookup"><span data-stu-id="93c49-109">Method</span></span>|<span data-ttu-id="93c49-110">Descrição</span><span class="sxs-lookup"><span data-stu-id="93c49-110">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="93c49-111"><xref:System.Xml.Linq.XObject.AddAnnotation%2A></xref:System.Xml.Linq.XObject.AddAnnotation%2A></span><span class="sxs-lookup"><span data-stu-id="93c49-111"><xref:System.Xml.Linq.XObject.AddAnnotation%2A></span></span>|<span data-ttu-id="93c49-112">Adiciona um objeto à lista de anotação de <xref:System.Xml.Linq.XObject>.</xref:System.Xml.Linq.XObject></span><span class="sxs-lookup"><span data-stu-id="93c49-112">Adds an object to the annotation list of an <xref:System.Xml.Linq.XObject>.</span></span>|  
|<span data-ttu-id="93c49-113"><xref:System.Xml.Linq.XObject.Annotation%2A></xref:System.Xml.Linq.XObject.Annotation%2A></span><span class="sxs-lookup"><span data-stu-id="93c49-113"><xref:System.Xml.Linq.XObject.Annotation%2A></span></span>|<span data-ttu-id="93c49-114">Obtém o primeiro objeto de anotação do tipo especificado de <xref:System.Xml.Linq.XObject>.</xref:System.Xml.Linq.XObject></span><span class="sxs-lookup"><span data-stu-id="93c49-114">Gets the first annotation object of the specified type from an <xref:System.Xml.Linq.XObject>.</span></span>|  
|<span data-ttu-id="93c49-115"><xref:System.Xml.Linq.XObject.Annotations%2A></xref:System.Xml.Linq.XObject.Annotations%2A></span><span class="sxs-lookup"><span data-stu-id="93c49-115"><xref:System.Xml.Linq.XObject.Annotations%2A></span></span>|<span data-ttu-id="93c49-116">Obtém uma coleção de anotações do tipo especificado para <xref:System.Xml.Linq.XObject>.</xref:System.Xml.Linq.XObject></span><span class="sxs-lookup"><span data-stu-id="93c49-116">Gets a collection of annotations of the specified type for an <xref:System.Xml.Linq.XObject>.</span></span>|  
|<span data-ttu-id="93c49-117"><xref:System.Xml.Linq.XObject.RemoveAnnotations%2A></xref:System.Xml.Linq.XObject.RemoveAnnotations%2A></span><span class="sxs-lookup"><span data-stu-id="93c49-117"><xref:System.Xml.Linq.XObject.RemoveAnnotations%2A></span></span>|<span data-ttu-id="93c49-118">Remove as anotações do tipo especificado de <xref:System.Xml.Linq.XObject>.</xref:System.Xml.Linq.XObject></span><span class="sxs-lookup"><span data-stu-id="93c49-118">Removes the annotations of the specified type from an <xref:System.Xml.Linq.XObject>.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="93c49-119">Consulte também</span><span class="sxs-lookup"><span data-stu-id="93c49-119">See Also</span></span>  
 [<span data-ttu-id="93c49-120">Avançada LINQ to XML programação (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="93c49-120">Advanced LINQ to XML Programming (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/advanced-linq-to-xml-programming.md)
