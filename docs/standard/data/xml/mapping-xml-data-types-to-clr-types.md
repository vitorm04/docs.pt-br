---
title: Tipos de dados XML de mapeamento para tipos de CLR
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: cabdfcad-f359-479b-b71c-8b2fad42ca49
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 9cff30147da82896fb3a757ba2fed16d794ec3c9
ms.sourcegitcommit: 6eac9a01ff5d70c6d18460324c016a3612c5e268
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/16/2018
ms.locfileid: "45673838"
---
# <a name="mapping-xml-data-types-to-clr-types"></a><span data-ttu-id="3a7ec-102">Tipos de dados XML de mapeamento para tipos de CLR</span><span class="sxs-lookup"><span data-stu-id="3a7ec-102">Mapping XML Data Types to CLR Types</span></span>
<span data-ttu-id="3a7ec-103">A tabela a seguir descreve o mapeamento padrão entre os tipos de dados XML e o Common Language Runtime (CLR) tipos.</span><span class="sxs-lookup"><span data-stu-id="3a7ec-103">The following table describes the default mapping between the XML data types and the common language runtime (CLR) types.</span></span>  
  
## <a name="the-following-table-describes-the-default-mappings-of-an-xml-data-type-to-a-clr-type"></a><span data-ttu-id="3a7ec-104">A tabela a seguir descreve os mapeamentos padrão de um tipo de dados XML para um tipo de CLR.</span><span class="sxs-lookup"><span data-stu-id="3a7ec-104">The following table describes the default mappings of an XML data type to a CLR type.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="3a7ec-105">Os prefixos `xs` e `xdt` são mapeados para os URIs de namespace http://www.w3.org/2001/XMLSchema e http://www.w3.org/2003/05/xpath-datatypes, respectivamente.</span><span class="sxs-lookup"><span data-stu-id="3a7ec-105">The `xs` and the `xdt` prefixes are mapped to the http://www.w3.org/2001/XMLSchema and the http://www.w3.org/2003/05/xpath-datatypes namespace URIs respectively.</span></span>  
  
|<span data-ttu-id="3a7ec-106">Tipo XML</span><span class="sxs-lookup"><span data-stu-id="3a7ec-106">XML Type</span></span>|<span data-ttu-id="3a7ec-107">Tipo CLR</span><span class="sxs-lookup"><span data-stu-id="3a7ec-107">CLR Type</span></span>|  
|--------------|--------------|  
|`xs:anyURI`|<xref:System.Uri>|  
|`xs:base64Binary`|`Byte[]`|  
|`xs:boolean`|<xref:System.Boolean>|  
|`xs:byte`|<xref:System.SByte>|  
|`xs:date`|<xref:System.DateTime>|  
|`xs:dateTime`|<xref:System.DateTime>|  
|`xs:decimal`|<xref:System.Decimal>|  
|`xs:double`|<xref:System.Double>|  
|`xs:duration`|<xref:System.TimeSpan>|  
|`xs:ENTITIES`|`String[]`|  
|`xs:ENTITY`|<xref:System.String>|  
|`xs:float`|<xref:System.Single>|  
|`xs:gDay`|<xref:System.DateTime>|  
|`xs:gMonthDay`|<xref:System.DateTime>|  
|`xs:gYear`|<xref:System.DateTime>|  
|`xs:gYearMonth`|<xref:System.DateTime>|  
|`xs:hexBinary`|`Byte[]`|  
|`xs:ID`|<xref:System.String>|  
|`xs:IDREF`|<xref:System.String>|  
|`xs:IDREFS`|`String[]`|  
|`xs:int`|<xref:System.Int32>|  
|`xs:integer`|<xref:System.Decimal>|  
|`xs:language`|<xref:System.String>|  
|`xs:long`|<xref:System.Int64>|  
|`xs:gMmonth`|<xref:System.DateTime>|  
|`xs:Name`|<xref:System.String>|  
|`xs:NCName`|<xref:System.String>|  
|`xs:negativeInteger`|<xref:System.Decimal>|  
|`xs:NMTOKEN`|<xref:System.String>|  
|`xs:NMTOKENS`|`String[]`|  
|`xs:nonNegativeInteger`|<xref:System.Decimal>|  
|`xs:nonPositiveInteger`|<xref:System.Decimal>|  
|`xs:normalizedString`|<xref:System.String>|  
|`xs:NOTATION`|<xref:System.Xml.XmlQualifiedName>|  
|`xs:positiveInteger`|<xref:System.Decimal>|  
|`xs:QName`|<xref:System.Xml.XmlQualifiedName>|  
|`xs:short`|<xref:System.Int16>|  
|`xs:string`|<xref:System.String>|  
|`xs:time`|<xref:System.DateTime>|  
|`xs:token`|<xref:System.String>|  
|`xs:unsignedByte`|<xref:System.Byte>|  
|`xs:unsignedInt`|<xref:System.UInt32>|  
|`xs:unsignedLong`|<xref:System.UInt64>|  
|`xs:unsignedShort`|<xref:System.UInt16>|  
|`xdt:dayTimeDuration`|<xref:System.TimeSpan>|  
|`xdt:yearMonthDuration`|<xref:System.TimeSpan>|  
|`xdt:untypedAtomic`|<xref:System.String>|  
|`xdt:anyAtomicType`|<xref:System.Object>|  
|`xs:anySimpleType`|<xref:System.String>|  
|<span data-ttu-id="3a7ec-108">Nó de documentos</span><span class="sxs-lookup"><span data-stu-id="3a7ec-108">Document node</span></span>|<xref:System.Xml.XPath.XPathNavigator>|  
|<span data-ttu-id="3a7ec-109">Nó de elemento</span><span class="sxs-lookup"><span data-stu-id="3a7ec-109">Element node</span></span>|<xref:System.Xml.XPath.XPathNavigator>|  
|<span data-ttu-id="3a7ec-110">Nó de atributo</span><span class="sxs-lookup"><span data-stu-id="3a7ec-110">Attribute node</span></span>|<xref:System.Xml.XPath.XPathNavigator>|  
|<span data-ttu-id="3a7ec-111">Nó de namespace</span><span class="sxs-lookup"><span data-stu-id="3a7ec-111">Namespace node</span></span>|<xref:System.Xml.XPath.XPathNavigator>|  
|<span data-ttu-id="3a7ec-112">Nó de texto</span><span class="sxs-lookup"><span data-stu-id="3a7ec-112">Text node</span></span>|<xref:System.Xml.XPath.XPathNavigator>|  
|<span data-ttu-id="3a7ec-113">Nó de comentário</span><span class="sxs-lookup"><span data-stu-id="3a7ec-113">Comment node</span></span>|<xref:System.Xml.XPath.XPathNavigator>|  
|<span data-ttu-id="3a7ec-114">Nó de instrução de processamento</span><span class="sxs-lookup"><span data-stu-id="3a7ec-114">Processing instruction node</span></span>|<xref:System.Xml.XPath.XPathNavigator>|  
  
## <a name="see-also"></a><span data-ttu-id="3a7ec-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="3a7ec-115">See also</span></span>

- <span data-ttu-id="3a7ec-116">[Type Support in the System.Xml Classes](../../../../docs/standard/data/xml/type-support-in-the-system-xml-classes.md) (Suporte a tipo nas classes System.XML)</span><span class="sxs-lookup"><span data-stu-id="3a7ec-116">[Type Support in the System.Xml Classes](../../../../docs/standard/data/xml/type-support-in-the-system-xml-classes.md)</span></span>
