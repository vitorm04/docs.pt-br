---
title: LINQ para XML Annotations2
ms.date: 07/20/2015
ms.assetid: c3e8b3ff-fceb-4428-b0ca-1ed6f128aac8
ms.openlocfilehash: a7b81b8c1856c11cb0c5e777f31986a330cf115f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33644791"
---
# <a name="linq-to-xml-annotations"></a><span data-ttu-id="29754-102">Anotações LINQ to XML</span><span class="sxs-lookup"><span data-stu-id="29754-102">LINQ to XML Annotations</span></span>
<span data-ttu-id="29754-103">Anotações em [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] permitem associar qualquer objeto arbitrário de qualquer tipo arbitrário com qualquer componente XML em uma árvore XML.</span><span class="sxs-lookup"><span data-stu-id="29754-103">Annotations in [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] enable you to associate any arbitrary object of any arbitrary type with any XML component in an XML tree.</span></span>  
  
 <span data-ttu-id="29754-104">Para adicionar uma anotação a um componente XML, como <xref:System.Xml.Linq.XElement> ou <xref:System.Xml.Linq.XAttribute>, você chama o método de <xref:System.Xml.Linq.XObject.AddAnnotation%2A> .</span><span class="sxs-lookup"><span data-stu-id="29754-104">To add an annotation to an XML component, such as an <xref:System.Xml.Linq.XElement> or <xref:System.Xml.Linq.XAttribute>, you call the <xref:System.Xml.Linq.XObject.AddAnnotation%2A> method.</span></span> <span data-ttu-id="29754-105">Você recupera anotações pelo tipo.</span><span class="sxs-lookup"><span data-stu-id="29754-105">You retrieve annotations by type.</span></span>  
  
 <span data-ttu-id="29754-106">Observe que as anotações não são parte de infoset XML; não são serializados ou não estão desserializados.</span><span class="sxs-lookup"><span data-stu-id="29754-106">Note that annotations are not part of the XML infoset; they are not serialized or deserialized.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="29754-107">Métodos</span><span class="sxs-lookup"><span data-stu-id="29754-107">Methods</span></span>  
 <span data-ttu-id="29754-108">Você pode usar os seguintes métodos para trabalhar com anotações:</span><span class="sxs-lookup"><span data-stu-id="29754-108">You can use the following methods when working with annotations:</span></span>  
  
|<span data-ttu-id="29754-109">Método</span><span class="sxs-lookup"><span data-stu-id="29754-109">Method</span></span>|<span data-ttu-id="29754-110">Descrição</span><span class="sxs-lookup"><span data-stu-id="29754-110">Description</span></span>|  
|------------|-----------------|  
|<xref:System.Xml.Linq.XObject.AddAnnotation%2A>|<span data-ttu-id="29754-111">Adiciona um objeto à lista de anotação de <xref:System.Xml.Linq.XObject>.</span><span class="sxs-lookup"><span data-stu-id="29754-111">Adds an object to the annotation list of an <xref:System.Xml.Linq.XObject>.</span></span>|  
|<xref:System.Xml.Linq.XObject.Annotation%2A>|<span data-ttu-id="29754-112">Obtém o primeiro objeto de anotação do tipo especificado de <xref:System.Xml.Linq.XObject>.</span><span class="sxs-lookup"><span data-stu-id="29754-112">Gets the first annotation object of the specified type from an <xref:System.Xml.Linq.XObject>.</span></span>|  
|<xref:System.Xml.Linq.XObject.Annotations%2A>|<span data-ttu-id="29754-113">Obtém uma coleção de anotações do tipo especificado para <xref:System.Xml.Linq.XObject>.</span><span class="sxs-lookup"><span data-stu-id="29754-113">Gets a collection of annotations of the specified type for an <xref:System.Xml.Linq.XObject>.</span></span>|  
|<xref:System.Xml.Linq.XObject.RemoveAnnotations%2A>|<span data-ttu-id="29754-114">Remove as anotações do tipo especificado de <xref:System.Xml.Linq.XObject>.</span><span class="sxs-lookup"><span data-stu-id="29754-114">Removes the annotations of the specified type from an <xref:System.Xml.Linq.XObject>.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="29754-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="29754-115">See Also</span></span>  
 [<span data-ttu-id="29754-116">Avançada LINQ to XML programação (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="29754-116">Advanced LINQ to XML Programming (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/advanced-linq-to-xml-programming.md)
