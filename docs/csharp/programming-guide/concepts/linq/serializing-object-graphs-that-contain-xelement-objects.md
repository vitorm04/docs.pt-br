---
title: "Serializando gráficos de objeto que contêm objetos de XElement (C#)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-csharp
ms.topic: article
ms.assetid: fcbc3951-3cc4-4d0f-9259-e97549ed68f0
caps.latest.revision: "3"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 8b7da4429360beb20fa304b592020d48666fe732
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="serializing-object-graphs-that-contain-xelement-objects-c"></a><span data-ttu-id="95f64-102">Serializando gráficos de objeto que contêm objetos de XElement (C#)</span><span class="sxs-lookup"><span data-stu-id="95f64-102">Serializing Object Graphs that Contain XElement Objects (C#)</span></span>
<span data-ttu-id="95f64-103">Este tópico apresenta o recurso de serializar os grafos de objeto que contêm referências a objetos do tipo <xref:System.Xml.Linq.XElement>.</span><span class="sxs-lookup"><span data-stu-id="95f64-103">This topic introduces the capability of serializing object graphs that contain references to objects of type <xref:System.Xml.Linq.XElement>.</span></span> <span data-ttu-id="95f64-104">Para facilitar esse tipo de serialização, <xref:System.Xml.Linq.XElement> implementa a interface de <xref:System.Xml.Serialization.IXmlSerializable> .</span><span class="sxs-lookup"><span data-stu-id="95f64-104">To facility this type of serializing, <xref:System.Xml.Linq.XElement> implements the <xref:System.Xml.Serialization.IXmlSerializable> interface.</span></span>  
  
 <span data-ttu-id="95f64-105">Observe que somente a classe de <xref:System.Xml.Linq.XElement> implementa a serialização.</span><span class="sxs-lookup"><span data-stu-id="95f64-105">Note that only the <xref:System.Xml.Linq.XElement> class implements serialization.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="95f64-106">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="95f64-106">In This Section</span></span>  
  
|<span data-ttu-id="95f64-107">Tópico</span><span class="sxs-lookup"><span data-stu-id="95f64-107">Topic</span></span>|<span data-ttu-id="95f64-108">Descrição</span><span class="sxs-lookup"><span data-stu-id="95f64-108">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="95f64-109">Como serializar usando XmlSerializer (C#)</span><span class="sxs-lookup"><span data-stu-id="95f64-109">How to: Serialize Using XmlSerializer (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/how-to-serialize-using-xmlserializer.md)|<span data-ttu-id="95f64-110">Demonstra como serializar usando <xref:System.Xml.Serialization.XmlSerializer>.</span><span class="sxs-lookup"><span data-stu-id="95f64-110">Demonstrates how to serialize using <xref:System.Xml.Serialization.XmlSerializer>.</span></span>|  
|[<span data-ttu-id="95f64-111">Como serializar usando DataContractSerializer (C#)</span><span class="sxs-lookup"><span data-stu-id="95f64-111">How to: Serialize Using DataContractSerializer (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/how-to-serialize-using-datacontractserializer.md)|<span data-ttu-id="95f64-112">Demonstra como serializar usando <xref:System.Runtime.Serialization.DataContractSerializer>.</span><span class="sxs-lookup"><span data-stu-id="95f64-112">Demonstrates how to serialize using <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="95f64-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="95f64-113">See Also</span></span>  
 [<span data-ttu-id="95f64-114">Programação LINQ to XML avançada (C#)</span><span class="sxs-lookup"><span data-stu-id="95f64-114">Advanced LINQ to XML Programming (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/advanced-linq-to-xml-programming.md)
