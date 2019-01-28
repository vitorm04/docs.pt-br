---
title: Anotações LINQ to XML 3
ms.date: 07/20/2015
ms.assetid: 54e7b9d0-07f5-488f-9065-b6e6b870f810
ms.openlocfilehash: 753fc656d78f2cefde98a8cbfb48713c7a107f77
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54676712"
---
# <a name="linq-to-xml-annotations"></a><span data-ttu-id="1c649-102">Anotações LINQ to XML</span><span class="sxs-lookup"><span data-stu-id="1c649-102">LINQ to XML Annotations</span></span>
<span data-ttu-id="1c649-103">Anotações em [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] permitem associar qualquer objeto arbitrário de qualquer tipo arbitrário com qualquer componente XML em uma árvore XML.</span><span class="sxs-lookup"><span data-stu-id="1c649-103">Annotations in [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] enable you to associate any arbitrary object of any arbitrary type with any XML component in an XML tree.</span></span>  
  
 <span data-ttu-id="1c649-104">Para adicionar uma anotação a um componente XML, como <xref:System.Xml.Linq.XElement> ou <xref:System.Xml.Linq.XAttribute>, você chama o método de <xref:System.Xml.Linq.XObject.AddAnnotation%2A> .</span><span class="sxs-lookup"><span data-stu-id="1c649-104">To add an annotation to an XML component, such as an <xref:System.Xml.Linq.XElement> or <xref:System.Xml.Linq.XAttribute>, you call the <xref:System.Xml.Linq.XObject.AddAnnotation%2A> method.</span></span> <span data-ttu-id="1c649-105">Você recupera anotações pelo tipo.</span><span class="sxs-lookup"><span data-stu-id="1c649-105">You retrieve annotations by type.</span></span>  
  
 <span data-ttu-id="1c649-106">Observe que as anotações não são parte de infoset XML; não são serializados ou não estão desserializados.</span><span class="sxs-lookup"><span data-stu-id="1c649-106">Note that annotations are not part of the XML infoset; they are not serialized or deserialized.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="1c649-107">Métodos</span><span class="sxs-lookup"><span data-stu-id="1c649-107">Methods</span></span>  
 <span data-ttu-id="1c649-108">Você pode usar os seguintes métodos para trabalhar com anotações:</span><span class="sxs-lookup"><span data-stu-id="1c649-108">You can use the following methods when working with annotations:</span></span>  
  
|<span data-ttu-id="1c649-109">Método</span><span class="sxs-lookup"><span data-stu-id="1c649-109">Method</span></span>|<span data-ttu-id="1c649-110">Descrição</span><span class="sxs-lookup"><span data-stu-id="1c649-110">Description</span></span>|  
|------------|-----------------|  
|<xref:System.Xml.Linq.XObject.AddAnnotation%2A>|<span data-ttu-id="1c649-111">Adiciona um objeto à lista de anotação de <xref:System.Xml.Linq.XObject>.</span><span class="sxs-lookup"><span data-stu-id="1c649-111">Adds an object to the annotation list of an <xref:System.Xml.Linq.XObject>.</span></span>|  
|<xref:System.Xml.Linq.XObject.Annotation%2A>|<span data-ttu-id="1c649-112">Obtém o primeiro objeto de anotação do tipo especificado de <xref:System.Xml.Linq.XObject>.</span><span class="sxs-lookup"><span data-stu-id="1c649-112">Gets the first annotation object of the specified type from an <xref:System.Xml.Linq.XObject>.</span></span>|  
|<xref:System.Xml.Linq.XObject.Annotations%2A>|<span data-ttu-id="1c649-113">Obtém uma coleção de anotações do tipo especificado para <xref:System.Xml.Linq.XObject>.</span><span class="sxs-lookup"><span data-stu-id="1c649-113">Gets a collection of annotations of the specified type for an <xref:System.Xml.Linq.XObject>.</span></span>|  
|<xref:System.Xml.Linq.XObject.RemoveAnnotations%2A>|<span data-ttu-id="1c649-114">Remove as anotações do tipo especificado de <xref:System.Xml.Linq.XObject>.</span><span class="sxs-lookup"><span data-stu-id="1c649-114">Removes the annotations of the specified type from an <xref:System.Xml.Linq.XObject>.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="1c649-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="1c649-115">See also</span></span>

- [<span data-ttu-id="1c649-116">Programação LINQ to XML avançada (C#)</span><span class="sxs-lookup"><span data-stu-id="1c649-116">Advanced LINQ to XML Programming (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/advanced-linq-to-xml-programming.md)
