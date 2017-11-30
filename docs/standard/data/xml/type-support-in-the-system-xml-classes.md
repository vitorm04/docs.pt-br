---
title: Digite suporte nas classes de System.Xml
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 63570538-06e3-4401-ad4d-ac50be90c7bf
caps.latest.revision: "4"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 14821ef78f20d1ff303afacb42415e4017a92742
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="type-support-in-the-systemxml-classes"></a><span data-ttu-id="c2261-102">Digite suporte nas classes de System.Xml</span><span class="sxs-lookup"><span data-stu-id="c2261-102">Type Support in the System.Xml Classes</span></span>
<span data-ttu-id="c2261-103">No .NET Framework versão 2,0, as classes XML principais foram aprimoradas para incluir recursos de suporte de tipo.</span><span class="sxs-lookup"><span data-stu-id="c2261-103">In the .NET Framework version 2.0, the core XML classes have been enhanced to include type support features.</span></span> <span data-ttu-id="c2261-104"><xref:System.Xml.XmlReader>, <xref:System.Xml.XmlWriter>, e as classes de <xref:System.Xml.XPath.XPathNavigator> incluem recursos de suporte do tipo que incluem a capacidade de conversão entre tipos esquema XML e Common Language Runtime (CLR) tipos.</span><span class="sxs-lookup"><span data-stu-id="c2261-104">The <xref:System.Xml.XmlReader>, <xref:System.Xml.XmlWriter>, and <xref:System.Xml.XPath.XPathNavigator> classes include type support features including the ability to convert between XML Schema types and common language runtime (CLR) types.</span></span>  
  
 <span data-ttu-id="c2261-105">No .NET Framework versão 2,0, <xref:System.Xml.XmlReader>, <xref:System.Xml.XmlWriter>, e as classes de <xref:System.Xml.XPath.XPathNavigator> foram aprimorados para incluir recursos de suporte do tipo.</span><span class="sxs-lookup"><span data-stu-id="c2261-105">In the .NET Framework version 2.0, the <xref:System.Xml.XmlReader>, <xref:System.Xml.XmlWriter>, and <xref:System.Xml.XPath.XPathNavigator> classes have been enhanced to include type support features.</span></span>  
  
-   <span data-ttu-id="c2261-106">O <xref:System.Xml.XmlReader> e <xref:System.Xml.XPath.XPathNavigator> classes cada incluem um **SchemaInfo** propriedade que retorna as informações de esquema em um nó.</span><span class="sxs-lookup"><span data-stu-id="c2261-106">The <xref:System.Xml.XmlReader> and <xref:System.Xml.XPath.XPathNavigator> classes each include a **SchemaInfo** property that returns the schema information on a node.</span></span>  
  
-   <span data-ttu-id="c2261-107">O **ReadContentAs** e **ReadElementContentAs** e métodos de <xref:System.Xml.XmlReader> classe ler um valor de texto e convertê-lo em um valor CLR em uma única chamada de método.</span><span class="sxs-lookup"><span data-stu-id="c2261-107">The **ReadContentAs** and **ReadElementContentAs** and methods on the <xref:System.Xml.XmlReader> class read a text value and convert it to a CLR value in a single method call.</span></span>  
  
-   <span data-ttu-id="c2261-108">O método de <xref:System.Xml.XmlWriter.WriteValue%2A> na classe de <xref:System.Xml.XmlWriter> converter um tipo de CLR a um tipo de esquema XML para gravar XML.</span><span class="sxs-lookup"><span data-stu-id="c2261-108">The <xref:System.Xml.XmlWriter.WriteValue%2A> method on the <xref:System.Xml.XmlWriter> class converts a CLR type to an XML Schema type when writing out XML.</span></span>  
  
-   <span data-ttu-id="c2261-109">O **ValueAs** e <xref:System.Xml.XPath.XPathNavigator.TypedValue%2A> propriedades de <xref:System.Xml.XPath.XPathNavigator> classe retornar um valor de nó e convertê-lo em um valor CLR em uma única chamada de método.</span><span class="sxs-lookup"><span data-stu-id="c2261-109">The **ValueAs** and <xref:System.Xml.XPath.XPathNavigator.TypedValue%2A> properties on the <xref:System.Xml.XPath.XPathNavigator> class return a node value and convert it to a CLR value in a single method call.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="c2261-110">Na versão 1,0 do.NET Framework a classe de <xref:System.Xml.XmlConvert> foi necessária para converter entre o esquema XML e os tipos de CLR.</span><span class="sxs-lookup"><span data-stu-id="c2261-110">In the .NET Framework version 1.0 the <xref:System.Xml.XmlConvert> class was needed to convert between XML Schema and CLR types.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="c2261-111">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="c2261-111">In This Section</span></span>  
 [<span data-ttu-id="c2261-112">Mapeando tipos de dados XML para tipos CLR</span><span class="sxs-lookup"><span data-stu-id="c2261-112">Mapping XML Data Types to CLR Types</span></span>](../../../../docs/standard/data/xml/mapping-xml-data-types-to-clr-types.md)  
 <span data-ttu-id="c2261-113">Descreve os mapeamentos padrão de tipos de dados XML para tipos de CLR.</span><span class="sxs-lookup"><span data-stu-id="c2261-113">Describes the default mappings of XML data types to CLR types.</span></span>  
  
 [<span data-ttu-id="c2261-114">Notas de implementação de suporte de tipo XML</span><span class="sxs-lookup"><span data-stu-id="c2261-114">XML Type Support Implementation Notes</span></span>](../../../../docs/standard/data/xml/xml-type-support-implementation-notes.md)  
 <span data-ttu-id="c2261-115">Descreve alguns dos detalhes de implementação de suporte de tipo.</span><span class="sxs-lookup"><span data-stu-id="c2261-115">Discusses some of the type support implementation details.</span></span>  
  
 [<span data-ttu-id="c2261-116">Conversão de tipos de dados XML</span><span class="sxs-lookup"><span data-stu-id="c2261-116">Conversion of XML Data Types</span></span>](../../../../docs/standard/data/xml/conversion-of-xml-data-types.md)  
 <span data-ttu-id="c2261-117">Descreve como usar a classe de <xref:System.Xml.XmlConvert> para converter entre o esquema XML e os tipos de CLR.</span><span class="sxs-lookup"><span data-stu-id="c2261-117">Describes how to use the <xref:System.Xml.XmlConvert> class to convert between XML Schema and CLR types.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="c2261-118">Seções relacionadas</span><span class="sxs-lookup"><span data-stu-id="c2261-118">Related Sections</span></span>  
 [<span data-ttu-id="c2261-119">Acessando dados XML usando XPathNavigator fortemente tipados</span><span class="sxs-lookup"><span data-stu-id="c2261-119">Accessing Strongly Typed XML Data Using XPathNavigator</span></span>](../../../../docs/standard/data/xml/accessing-strongly-typed-xml-data-using-xpathnavigator.md)
