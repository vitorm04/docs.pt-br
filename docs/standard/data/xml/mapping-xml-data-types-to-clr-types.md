---
title: Tipos de dados XML de mapeamento para tipos de CLR
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: cabdfcad-f359-479b-b71c-8b2fad42ca49
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 48ec3a5b719b05112b257871f64a34f2bc21eeab
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57364132"
---
# <a name="mapping-xml-data-types-to-clr-types"></a><span data-ttu-id="0890f-102">Tipos de dados XML de mapeamento para tipos de CLR</span><span class="sxs-lookup"><span data-stu-id="0890f-102">Mapping XML Data Types to CLR Types</span></span>

<span data-ttu-id="0890f-103">A tabela a seguir descreve o mapeamento padrão entre os tipos de dados XML e o Common Language Runtime (CLR) tipos.</span><span class="sxs-lookup"><span data-stu-id="0890f-103">The following table describes the default mapping between the XML data types and the common language runtime (CLR) types.</span></span>

> [!NOTE]
> <span data-ttu-id="0890f-104">Os prefixos `xs` e `xdt` são mapeados para os URIs de namespace <https://www.w3.org/2001/XMLSchema> e <https://www.w3.org/2003/05/xpath-datatypes>, respectivamente.</span><span class="sxs-lookup"><span data-stu-id="0890f-104">The `xs` and the `xdt` prefixes are mapped to the <https://www.w3.org/2001/XMLSchema> and the <https://www.w3.org/2003/05/xpath-datatypes> namespace URIs respectively.</span></span>

|<span data-ttu-id="0890f-105">Tipo XML</span><span class="sxs-lookup"><span data-stu-id="0890f-105">XML Type</span></span>|<span data-ttu-id="0890f-106">Tipo CLR</span><span class="sxs-lookup"><span data-stu-id="0890f-106">CLR Type</span></span>|
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
|`xs:gMonth`|<xref:System.DateTime>|
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
|<span data-ttu-id="0890f-107">Nó de documentos</span><span class="sxs-lookup"><span data-stu-id="0890f-107">Document node</span></span>|<xref:System.Xml.XPath.XPathNavigator>|
|<span data-ttu-id="0890f-108">Nó de elemento</span><span class="sxs-lookup"><span data-stu-id="0890f-108">Element node</span></span>|<xref:System.Xml.XPath.XPathNavigator>|
|<span data-ttu-id="0890f-109">Nó de atributo</span><span class="sxs-lookup"><span data-stu-id="0890f-109">Attribute node</span></span>|<xref:System.Xml.XPath.XPathNavigator>|
|<span data-ttu-id="0890f-110">Nó de namespace</span><span class="sxs-lookup"><span data-stu-id="0890f-110">Namespace node</span></span>|<xref:System.Xml.XPath.XPathNavigator>|
|<span data-ttu-id="0890f-111">Nó de texto</span><span class="sxs-lookup"><span data-stu-id="0890f-111">Text node</span></span>|<xref:System.Xml.XPath.XPathNavigator>|
|<span data-ttu-id="0890f-112">Nó de comentário</span><span class="sxs-lookup"><span data-stu-id="0890f-112">Comment node</span></span>|<xref:System.Xml.XPath.XPathNavigator>|
|<span data-ttu-id="0890f-113">Nó de instrução de processamento</span><span class="sxs-lookup"><span data-stu-id="0890f-113">Processing instruction node</span></span>|<xref:System.Xml.XPath.XPathNavigator>|

## <a name="see-also"></a><span data-ttu-id="0890f-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="0890f-114">See also</span></span>

- <span data-ttu-id="0890f-115">[Type Support in the System.Xml Classes](../../../../docs/standard/data/xml/type-support-in-the-system-xml-classes.md) (Suporte a tipo nas classes System.XML)</span><span class="sxs-lookup"><span data-stu-id="0890f-115">[Type Support in the System.Xml Classes](../../../../docs/standard/data/xml/type-support-in-the-system-xml-classes.md)</span></span>
