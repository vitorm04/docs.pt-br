---
title: Digite suporte nas classes de System.Xml
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 63570538-06e3-4401-ad4d-ac50be90c7bf
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 954ff12ae1ac8b4d601c35fcd76ea35b2bb3acbf
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69939446"
---
# <a name="type-support-in-the-systemxml-classes"></a><span data-ttu-id="ad599-102">Digite suporte nas classes de System.Xml</span><span class="sxs-lookup"><span data-stu-id="ad599-102">Type Support in the System.Xml Classes</span></span>
<span data-ttu-id="ad599-103">No .NET Framework versão 2,0, as classes XML principais foram aprimoradas para incluir recursos de suporte de tipo.</span><span class="sxs-lookup"><span data-stu-id="ad599-103">In the .NET Framework version 2.0, the core XML classes have been enhanced to include type support features.</span></span> <span data-ttu-id="ad599-104"><xref:System.Xml.XmlReader>, <xref:System.Xml.XmlWriter>, e as classes de <xref:System.Xml.XPath.XPathNavigator> incluem recursos de suporte do tipo que incluem a capacidade de conversão entre tipos esquema XML e Common Language Runtime (CLR) tipos.</span><span class="sxs-lookup"><span data-stu-id="ad599-104">The <xref:System.Xml.XmlReader>, <xref:System.Xml.XmlWriter>, and <xref:System.Xml.XPath.XPathNavigator> classes include type support features including the ability to convert between XML Schema types and common language runtime (CLR) types.</span></span>  
  
 <span data-ttu-id="ad599-105">No .NET Framework versão 2,0, <xref:System.Xml.XmlReader>, <xref:System.Xml.XmlWriter>, e as classes de <xref:System.Xml.XPath.XPathNavigator> foram aprimorados para incluir recursos de suporte do tipo.</span><span class="sxs-lookup"><span data-stu-id="ad599-105">In the .NET Framework version 2.0, the <xref:System.Xml.XmlReader>, <xref:System.Xml.XmlWriter>, and <xref:System.Xml.XPath.XPathNavigator> classes have been enhanced to include type support features.</span></span>  
  
- <span data-ttu-id="ad599-106">As classes <xref:System.Xml.XmlReader> e <xref:System.Xml.XPath.XPathNavigator> incluem uma propriedade **SchemaInfo** que retorna informações de esquema em um nó.</span><span class="sxs-lookup"><span data-stu-id="ad599-106">The <xref:System.Xml.XmlReader> and <xref:System.Xml.XPath.XPathNavigator> classes each include a **SchemaInfo** property that returns the schema information on a node.</span></span>  
  
- <span data-ttu-id="ad599-107">**ReadContentAs** e **ReadElementContentAs** e os métodos na classe <xref:System.Xml.XmlReader> leem um valor de texto e o convertem em um valor de CLR em uma única chamada de método.</span><span class="sxs-lookup"><span data-stu-id="ad599-107">The **ReadContentAs** and **ReadElementContentAs** and methods on the <xref:System.Xml.XmlReader> class read a text value and convert it to a CLR value in a single method call.</span></span>  
  
- <span data-ttu-id="ad599-108">O método de <xref:System.Xml.XmlWriter.WriteValue%2A> na classe de <xref:System.Xml.XmlWriter> converter um tipo de CLR a um tipo de esquema XML para gravar XML.</span><span class="sxs-lookup"><span data-stu-id="ad599-108">The <xref:System.Xml.XmlWriter.WriteValue%2A> method on the <xref:System.Xml.XmlWriter> class converts a CLR type to an XML Schema type when writing out XML.</span></span>  
  
- <span data-ttu-id="ad599-109">As propriedades **ValueAs** e <xref:System.Xml.XPath.XPathNavigator.TypedValue%2A> na classe <xref:System.Xml.XPath.XPathNavigator> retornam um valor do nó e o convertem em um valor de CLR em uma única chamada de método.</span><span class="sxs-lookup"><span data-stu-id="ad599-109">The **ValueAs** and <xref:System.Xml.XPath.XPathNavigator.TypedValue%2A> properties on the <xref:System.Xml.XPath.XPathNavigator> class return a node value and convert it to a CLR value in a single method call.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="ad599-110">Na versão 1,0 do.NET Framework a classe de <xref:System.Xml.XmlConvert> foi necessária para converter entre o esquema XML e os tipos de CLR.</span><span class="sxs-lookup"><span data-stu-id="ad599-110">In the .NET Framework version 1.0 the <xref:System.Xml.XmlConvert> class was needed to convert between XML Schema and CLR types.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="ad599-111">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="ad599-111">In This Section</span></span>  
 [<span data-ttu-id="ad599-112">Mapeando tipos de dados XML para tipos CLR</span><span class="sxs-lookup"><span data-stu-id="ad599-112">Mapping XML Data Types to CLR Types</span></span>](../../../../docs/standard/data/xml/mapping-xml-data-types-to-clr-types.md)  
 <span data-ttu-id="ad599-113">Descreve os mapeamentos padrão de tipos de dados XML para tipos de CLR.</span><span class="sxs-lookup"><span data-stu-id="ad599-113">Describes the default mappings of XML data types to CLR types.</span></span>  
  
 [<span data-ttu-id="ad599-114">Notas de implementação de suporte de tipo XML</span><span class="sxs-lookup"><span data-stu-id="ad599-114">XML Type Support Implementation Notes</span></span>](../../../../docs/standard/data/xml/xml-type-support-implementation-notes.md)  
 <span data-ttu-id="ad599-115">Descreve alguns dos detalhes de implementação de suporte de tipo.</span><span class="sxs-lookup"><span data-stu-id="ad599-115">Discusses some of the type support implementation details.</span></span>  
  
 [<span data-ttu-id="ad599-116">Conversão de tipos de dados XML</span><span class="sxs-lookup"><span data-stu-id="ad599-116">Conversion of XML Data Types</span></span>](../../../../docs/standard/data/xml/conversion-of-xml-data-types.md)  
 <span data-ttu-id="ad599-117">Descreve como usar a classe de <xref:System.Xml.XmlConvert> para converter entre o esquema XML e os tipos de CLR.</span><span class="sxs-lookup"><span data-stu-id="ad599-117">Describes how to use the <xref:System.Xml.XmlConvert> class to convert between XML Schema and CLR types.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="ad599-118">Seções relacionadas</span><span class="sxs-lookup"><span data-stu-id="ad599-118">Related Sections</span></span>  
 [<span data-ttu-id="ad599-119">Acessando dados XML fortemente tipados usando o XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="ad599-119">Accessing Strongly Typed XML Data Using XPathNavigator</span></span>](../../../../docs/standard/data/xml/accessing-strongly-typed-xml-data-using-xpathnavigator.md)
