---
title: Serializando gráficos de objeto que contêm objetos de XElement (C#)
ms.date: 07/20/2015
ms.assetid: fcbc3951-3cc4-4d0f-9259-e97549ed68f0
ms.openlocfilehash: f51a026642563e1c1690d9a49220aae462840211
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33338901"
---
# <a name="serializing-object-graphs-that-contain-xelement-objects-c"></a><span data-ttu-id="9e731-102">Serializando gráficos de objeto que contêm objetos de XElement (C#)</span><span class="sxs-lookup"><span data-stu-id="9e731-102">Serializing Object Graphs that Contain XElement Objects (C#)</span></span>
<span data-ttu-id="9e731-103">Este tópico apresenta o recurso de serializar os grafos de objeto que contêm referências a objetos do tipo <xref:System.Xml.Linq.XElement>.</span><span class="sxs-lookup"><span data-stu-id="9e731-103">This topic introduces the capability of serializing object graphs that contain references to objects of type <xref:System.Xml.Linq.XElement>.</span></span> <span data-ttu-id="9e731-104">Para facilitar esse tipo de serialização, <xref:System.Xml.Linq.XElement> implementa a interface de <xref:System.Xml.Serialization.IXmlSerializable> .</span><span class="sxs-lookup"><span data-stu-id="9e731-104">To facility this type of serializing, <xref:System.Xml.Linq.XElement> implements the <xref:System.Xml.Serialization.IXmlSerializable> interface.</span></span>  
  
 <span data-ttu-id="9e731-105">Observe que somente a classe de <xref:System.Xml.Linq.XElement> implementa a serialização.</span><span class="sxs-lookup"><span data-stu-id="9e731-105">Note that only the <xref:System.Xml.Linq.XElement> class implements serialization.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="9e731-106">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="9e731-106">In This Section</span></span>  
  
|<span data-ttu-id="9e731-107">Tópico</span><span class="sxs-lookup"><span data-stu-id="9e731-107">Topic</span></span>|<span data-ttu-id="9e731-108">Descrição</span><span class="sxs-lookup"><span data-stu-id="9e731-108">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="9e731-109">Como serializar usando XmlSerializer (C#)</span><span class="sxs-lookup"><span data-stu-id="9e731-109">How to: Serialize Using XmlSerializer (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/how-to-serialize-using-xmlserializer.md)|<span data-ttu-id="9e731-110">Demonstra como serializar usando <xref:System.Xml.Serialization.XmlSerializer>.</span><span class="sxs-lookup"><span data-stu-id="9e731-110">Demonstrates how to serialize using <xref:System.Xml.Serialization.XmlSerializer>.</span></span>|  
|[<span data-ttu-id="9e731-111">Como serializar usando DataContractSerializer (C#)</span><span class="sxs-lookup"><span data-stu-id="9e731-111">How to: Serialize Using DataContractSerializer (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/how-to-serialize-using-datacontractserializer.md)|<span data-ttu-id="9e731-112">Demonstra como serializar usando <xref:System.Runtime.Serialization.DataContractSerializer>.</span><span class="sxs-lookup"><span data-stu-id="9e731-112">Demonstrates how to serialize using <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="9e731-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="9e731-113">See Also</span></span>  
 [<span data-ttu-id="9e731-114">Programação LINQ to XML avançada (C#)</span><span class="sxs-lookup"><span data-stu-id="9e731-114">Advanced LINQ to XML Programming (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/advanced-linq-to-xml-programming.md)
