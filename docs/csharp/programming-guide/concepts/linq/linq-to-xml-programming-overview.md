---
title: "Visão geral da programação LINQ to XML (C#)"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
ms.assetid: 2dfa9b6f-5890-461d-b81c-316853c7f320
caps.latest.revision: 3
author: BillWagner
ms.author: wiwagn
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: bc22991f53920b045280d3e74b9b8dd73e63c944
ms.contentlocale: pt-br
ms.lasthandoff: 07/28/2017

---
# <a name="linq-to-xml-programming-overview-c"></a><span data-ttu-id="c36b8-102">Visão geral da programação LINQ to XML (C#)</span><span class="sxs-lookup"><span data-stu-id="c36b8-102">LINQ to XML Programming Overview (C#)</span></span>
<span data-ttu-id="c36b8-103">Estes tópicos fornecem informações de visão geral de alto nível sobre as classes [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], bem como informações detalhadas sobre três das classes mais importantes.</span><span class="sxs-lookup"><span data-stu-id="c36b8-103">These topics provide high-level overview information about the [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] classes, as well as detailed information about three of the most important classes.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="c36b8-104">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="c36b8-104">In This Section</span></span>  
  
|<span data-ttu-id="c36b8-105">Tópico</span><span class="sxs-lookup"><span data-stu-id="c36b8-105">Topic</span></span>|<span data-ttu-id="c36b8-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="c36b8-106">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="c36b8-107">Programação funcional versus Programação de procedimentos (LINQ to XML)</span><span class="sxs-lookup"><span data-stu-id="c36b8-107">Functional vs. Procedural Programming (LINQ to XML) (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/functional-vs-procedural-programming-linq-to-xml.md)|<span data-ttu-id="c36b8-108">Fornece uma visão de alto nível das duas abordagens de princípio para escrever aplicativos LINQ para XML.</span><span class="sxs-lookup"><span data-stu-id="c36b8-108">Provides a high level view of the two principle approaches to writing LINQ to XML applications.</span></span>|  
|[<span data-ttu-id="c36b8-109">Visão geral de classes LINQ to XML (C#)</span><span class="sxs-lookup"><span data-stu-id="c36b8-109">LINQ to XML Classes Overview (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/linq-to-xml-classes-overview.md)|<span data-ttu-id="c36b8-110">Fornece uma visão geral das classes [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)].</span><span class="sxs-lookup"><span data-stu-id="c36b8-110">Provides an overview of the [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] classes.</span></span>|  
|[<span data-ttu-id="c36b8-111">Visão geral da classe XElement (C#)</span><span class="sxs-lookup"><span data-stu-id="c36b8-111">XElement Class Overview (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/xelement-class-overview.md)|<span data-ttu-id="c36b8-112">Apresenta a classe <xref:System.Xml.Linq.XElement>, que representa elementos XML.</span><span class="sxs-lookup"><span data-stu-id="c36b8-112">Introduces the <xref:System.Xml.Linq.XElement> class, which represents XML elements.</span></span> <span data-ttu-id="c36b8-113"><xref:System.Xml.Linq.XElement> é uma das classes fundamentais na hierarquia de classes [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)].</span><span class="sxs-lookup"><span data-stu-id="c36b8-113"><xref:System.Xml.Linq.XElement> is one of the fundamental classes in the [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] class hierarchy.</span></span>|  
|[<span data-ttu-id="c36b8-114">Visão geral da classe XAttribute (C#)</span><span class="sxs-lookup"><span data-stu-id="c36b8-114">XAttribute Class Overview (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/xattribute-class-overview.md)|<span data-ttu-id="c36b8-115">Apresenta a classe <xref:System.Xml.Linq.XAttribute>, que representa atributos XML.</span><span class="sxs-lookup"><span data-stu-id="c36b8-115">Introduces the <xref:System.Xml.Linq.XAttribute> class, which represents XML attributes.</span></span>|  
|[<span data-ttu-id="c36b8-116">Visão geral da classe XDocument (C#)</span><span class="sxs-lookup"><span data-stu-id="c36b8-116">XDocument Class Overview (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/xdocument-class-overview.md)|<span data-ttu-id="c36b8-117">Apresenta a classe <xref:System.Xml.Linq.XDocument>, que representa documentos XML.</span><span class="sxs-lookup"><span data-stu-id="c36b8-117">Introduces the <xref:System.Xml.Linq.XDocument> class, which represents XML documents.</span></span>|  
|[<span data-ttu-id="c36b8-118">Como compilar exemplos de LINQ to XML (C#)</span><span class="sxs-lookup"><span data-stu-id="c36b8-118">How to: Build LINQ to XML Examples (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/how-to-build-linq-to-xml-examples.md)|<span data-ttu-id="c36b8-119">Contém as diretivas `Using` que são necessárias para compilar os exemplos de LINQ to XML.</span><span class="sxs-lookup"><span data-stu-id="c36b8-119">Contains the `Using` directives that are required to build the LINQ to XML examples.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="c36b8-120">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c36b8-120">See Also</span></span>  
 [<span data-ttu-id="c36b8-121">Guia de Programação (LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="c36b8-121">Programming Guide (LINQ to XML) (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/programming-guide-linq-to-xml.md)

