---
title: "Visão geral sobre namespaces (LINQ to XML) | Documentos do Microsoft"
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
ms.assetid: b8eb31fa-4b26-4acf-8050-6e705687f458
caps.latest.revision: 3
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 7e9536615871b83099a11e46125ed85b44d9335d
ms.contentlocale: pt-br
ms.lasthandoff: 04/12/2017

---
# <a name="namespaces-overview-linq-to-xml"></a><span data-ttu-id="842e8-102">Visão geral sobre namespaces (LINQ to XML)</span><span class="sxs-lookup"><span data-stu-id="842e8-102">Namespaces Overview (LINQ to XML)</span></span>
<span data-ttu-id="842e8-103">Este tópico apresenta namespaces, a <xref:System.Xml.Linq.XName>classe e a <xref:System.Xml.Linq.XNamespace>classe.</xref:System.Xml.Linq.XNamespace> </xref:System.Xml.Linq.XName></span><span class="sxs-lookup"><span data-stu-id="842e8-103">This topic introduces namespaces, the <xref:System.Xml.Linq.XName> class, and the <xref:System.Xml.Linq.XNamespace> class.</span></span>  
  
## <a name="xml-names"></a><span data-ttu-id="842e8-104">Nomes XML</span><span class="sxs-lookup"><span data-stu-id="842e8-104">XML Names</span></span>  
 <span data-ttu-id="842e8-105">Os nomes XML são geralmente uma fonte de complexidade na programação XML.</span><span class="sxs-lookup"><span data-stu-id="842e8-105">XML names are often a source of complexity in XML programming.</span></span> <span data-ttu-id="842e8-106">Um nome de XML consiste em um namespace XML (também chamado um URI de um namespace XML) e um nome local.</span><span class="sxs-lookup"><span data-stu-id="842e8-106">An XML name consists of an XML namespace (also called an XML namespace URI) and a local name.</span></span> <span data-ttu-id="842e8-107">Um namespace XML é semelhante a um namespace em um programa baseadas em [!INCLUDE[dnprdnshort](../../../../csharp/getting-started/includes/dnprdnshort_md.md)].</span><span class="sxs-lookup"><span data-stu-id="842e8-107">An XML namespace is similar to a namespace in a [!INCLUDE[dnprdnshort](../../../../csharp/getting-started/includes/dnprdnshort_md.md)]-based program.</span></span> <span data-ttu-id="842e8-108">Permite que você determine exclusivamente os nomes de elementos e atributos.</span><span class="sxs-lookup"><span data-stu-id="842e8-108">It enables you to uniquely qualify the names of elements and attributes.</span></span> <span data-ttu-id="842e8-109">Isso ajuda a evitar conflitos de nome entre várias partes de um documento XML.</span><span class="sxs-lookup"><span data-stu-id="842e8-109">This helps avoid name conflicts between various parts of an XML document.</span></span> <span data-ttu-id="842e8-110">Quando você declarar um namespace XML, você pode selecionar um nome local que só deve ser exclusivo dentro desse namespace.</span><span class="sxs-lookup"><span data-stu-id="842e8-110">When you have declared an XML namespace, you can select a local name that only has to be unique within that namespace.</span></span>  
  
 <span data-ttu-id="842e8-111">Outro aspecto de nomes XML é XML *prefixos de namespace*.</span><span class="sxs-lookup"><span data-stu-id="842e8-111">Another aspect of XML names is XML *namespace prefixes*.</span></span> <span data-ttu-id="842e8-112">Os prefixos XML causam a maioria da complexidade de nomes XML.</span><span class="sxs-lookup"><span data-stu-id="842e8-112">XML prefixes cause most of the complexity of XML names.</span></span> <span data-ttu-id="842e8-113">Esses prefixos permite que você crie um atalho para um namespace XML, que faz o documento XML mais concisas e legível.</span><span class="sxs-lookup"><span data-stu-id="842e8-113">These prefixes enable you to create a shortcut for an XML namespace, which makes the XML document more concise and understandable.</span></span> <span data-ttu-id="842e8-114">No entanto, os prefixos XML depende do seu contexto para ter significado, que adiciona a complexidade.</span><span class="sxs-lookup"><span data-stu-id="842e8-114">However, XML prefixes depend on their context to have meaning, which adds complexity.</span></span> <span data-ttu-id="842e8-115">Por exemplo, o prefixo `aw` XML pode ser associado com a um namespace XML de uma parte de uma árvore XML, e com um outro namespace XML em uma parte diferente da árvore XML.</span><span class="sxs-lookup"><span data-stu-id="842e8-115">For example, the XML prefix `aw` could be associated with one XML namespace in one part of an XML tree, and with a different XML namespace in a different part of the XML tree.</span></span>  
  
 <span data-ttu-id="842e8-116">Ao usar [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] com literais XML e Visual Basic, você deve usar prefixos de namespace ao trabalhar com documentos em namespaces.</span><span class="sxs-lookup"><span data-stu-id="842e8-116">When using [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] with Visual Basic and XML literals, you must use namespace prefixes when working with documents in namespaces.</span></span>  
  
 <span data-ttu-id="842e8-117">Em [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)], a classe que representa nomes XML é <xref:System.Xml.Linq.XName>.</xref:System.Xml.Linq.XName></span><span class="sxs-lookup"><span data-stu-id="842e8-117">In [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)], the class that represents XML names is <xref:System.Xml.Linq.XName>.</span></span> <span data-ttu-id="842e8-118">Nomes XML aparece com frequência em todo o [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] API, e sempre que é necessário um nome XML, você encontrará um <xref:System.Xml.Linq.XName>parâmetro.</xref:System.Xml.Linq.XName></span><span class="sxs-lookup"><span data-stu-id="842e8-118">XML names appear frequently throughout the [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] API, and wherever an XML name is required, you will find an <xref:System.Xml.Linq.XName> parameter.</span></span> <span data-ttu-id="842e8-119">No entanto, raramente você trabalha diretamente com um <xref:System.Xml.Linq.XName>.</xref:System.Xml.Linq.XName></span><span class="sxs-lookup"><span data-stu-id="842e8-119">However, you rarely work directly with an <xref:System.Xml.Linq.XName>.</span></span> <span data-ttu-id="842e8-120"><xref:System.Xml.Linq.XName>contém uma conversão implícita de cadeia de caracteres.</xref:System.Xml.Linq.XName></span><span class="sxs-lookup"><span data-stu-id="842e8-120"><xref:System.Xml.Linq.XName> contains an implicit conversion from string.</span></span>  
  
 <span data-ttu-id="842e8-121">Para obter mais informações, consulte <xref:System.Xml.Linq.XNamespace>e <xref:System.Xml.Linq.XName>.</xref:System.Xml.Linq.XName> </xref:System.Xml.Linq.XNamespace></span><span class="sxs-lookup"><span data-stu-id="842e8-121">For more information, see <xref:System.Xml.Linq.XNamespace> and <xref:System.Xml.Linq.XName>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="842e8-122">Consulte também</span><span class="sxs-lookup"><span data-stu-id="842e8-122">See Also</span></span>  
 [<span data-ttu-id="842e8-123">Trabalhando com Namespaces XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="842e8-123">Working with XML Namespaces (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/working-with-xml-namespaces.md)
