---
title: "Notas de implementação de suporte do tipo XML"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 26b071f3-1261-47ef-8690-0717f5cd93c1
caps.latest.revision: "2"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 5e99573fc3a82db7798426172a13a78e10c65636
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="xml-type-support-implementation-notes"></a><span data-ttu-id="56bb5-102">Notas de implementação de suporte do tipo XML</span><span class="sxs-lookup"><span data-stu-id="56bb5-102">XML Type Support Implementation Notes</span></span>
<span data-ttu-id="56bb5-103">Este tópico descreve alguns detalhes de implementação de que você deseja estar ciente.</span><span class="sxs-lookup"><span data-stu-id="56bb5-103">This topic describes some implementation details that you want to be aware of.</span></span>  
  
## <a name="list-mappings"></a><span data-ttu-id="56bb5-104">Mapeamentos de lista</span><span class="sxs-lookup"><span data-stu-id="56bb5-104">List Mappings</span></span>  
 <span data-ttu-id="56bb5-105">O <xref:System.Collections.IList>, <xref:System.Collections.ICollection>, <xref:System.Collections.IEnumerable>, **tipo []**, e <xref:System.String> tipos são usados para representar tipos de lista de linguagem XSD de definição de esquema XML.</span><span class="sxs-lookup"><span data-stu-id="56bb5-105">The <xref:System.Collections.IList>, <xref:System.Collections.ICollection>, <xref:System.Collections.IEnumerable>, **Type[]**, and <xref:System.String> types are used to represent XML Schema definition language (XSD) list types.</span></span>  
  
## <a name="union-mappings"></a><span data-ttu-id="56bb5-106">Mapeamentos de união</span><span class="sxs-lookup"><span data-stu-id="56bb5-106">Union Mappings</span></span>  
 <span data-ttu-id="56bb5-107">Os tipos de união são representados usando o tipo de <xref:System.Xml.Schema.XmlAtomicValue> ou de <xref:System.String> .</span><span class="sxs-lookup"><span data-stu-id="56bb5-107">Union types are represented using the <xref:System.Xml.Schema.XmlAtomicValue> or <xref:System.String> type.</span></span> <span data-ttu-id="56bb5-108">O tipo de origem ou o tipo de destino portanto deve ser sempre <xref:System.String> ou <xref:System.Xml.Schema.XmlAtomicValue>.</span><span class="sxs-lookup"><span data-stu-id="56bb5-108">The source type or the destination type must therefore always be either <xref:System.String> or <xref:System.Xml.Schema.XmlAtomicValue>.</span></span>  
  
 <span data-ttu-id="56bb5-109">Se o objeto de <xref:System.Xml.Schema.XmlSchemaDatatype> representa um tipo de lista o objeto converte o valor da cadeia de caracteres de entrada em uma lista de um ou mais objetos.</span><span class="sxs-lookup"><span data-stu-id="56bb5-109">If the <xref:System.Xml.Schema.XmlSchemaDatatype> object represents a list type the object converts the input string value to a list of one or more objects.</span></span> <span data-ttu-id="56bb5-110">Se <xref:System.Xml.Schema.XmlSchemaDatatype> representa um tipo de união então é feita uma tentativa de analisar o valor de entrada como um tipo de membro de união.</span><span class="sxs-lookup"><span data-stu-id="56bb5-110">If the <xref:System.Xml.Schema.XmlSchemaDatatype> represents a union type then an attempt is made to parse the input value as a member type of the union.</span></span> <span data-ttu-id="56bb5-111">Se a tentativa de análise falhar na conversão será tentada com o membro a seguir de união e assim por diante até que a conversão foi bem-sucedida, ou não há nenhum outro tipo do membro a tentar nesse caso, uma exceção é lançada.</span><span class="sxs-lookup"><span data-stu-id="56bb5-111">If the parse attempt fails then the conversion is attempted with the next member of the union and so on until the conversion is successful, or there are no other member types to try, in which case an exception is thrown.</span></span>  
  
## <a name="differences-between-clr-and-xml-data-types"></a><span data-ttu-id="56bb5-112">Diferenças entre tipos de dados de CLR e XML</span><span class="sxs-lookup"><span data-stu-id="56bb5-112">Differences Between CLR and XML Data Types</span></span>  
 <span data-ttu-id="56bb5-113">O exemplo a seguir descreve determinadas incompatíveis que podem ocorrer entre tipos de CLR e tipos de dados XML e como elas são tratadas.</span><span class="sxs-lookup"><span data-stu-id="56bb5-113">The following describes certain mismatches that can occur between CLR types and XML data types and how they are handled.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="56bb5-114">O prefixo de `xs` é mapeado para http://www.w3.org/2001/XMLSchema e o URI de namespace.</span><span class="sxs-lookup"><span data-stu-id="56bb5-114">The `xs` prefix is mapped to the http://www.w3.org/2001/XMLSchema and namespace URI.</span></span>  
  
### <a name="systemtimespan-and-xsduration"></a><span data-ttu-id="56bb5-115">System.TimeSpan e xs:duration</span><span class="sxs-lookup"><span data-stu-id="56bb5-115">System.TimeSpan and xs:duration</span></span>  
 <span data-ttu-id="56bb5-116">O tipo de `xs:duration` é ordenada parcialmente em que há determinados valores de duração que são diferentes mas equivalente.</span><span class="sxs-lookup"><span data-stu-id="56bb5-116">The `xs:duration` type is partially ordered in that there are certain duration values that are different but equivalent.</span></span> <span data-ttu-id="56bb5-117">Isso significa que para o valor do tipo de `xs:duration` como 1 mês (P1M) está menos de 32 dias (P32D), maior que 27 dias (P27D) e equivalente a 28, 29 ou 30 dias.</span><span class="sxs-lookup"><span data-stu-id="56bb5-117">This means that for the `xs:duration` type value such as 1 month (P1M) is less than 32 days (P32D), larger than 27 days (P27D) and equivalent to 28, 29 or 30 days.</span></span>  
  
 <span data-ttu-id="56bb5-118">A classe de <xref:System.TimeSpan> não suporta este pedido parcial.</span><span class="sxs-lookup"><span data-stu-id="56bb5-118">The <xref:System.TimeSpan> class does not support this partial ordering.</span></span> <span data-ttu-id="56bb5-119">Em vez disso, escolher um número específico de dias para 1 e 1 ano mês; 365 dias e 30 dias respectivamente.</span><span class="sxs-lookup"><span data-stu-id="56bb5-119">Instead, it picks a specific number of days for 1 year and 1 month; 365 days and 30 days respectively.</span></span>  
  
 <span data-ttu-id="56bb5-120">Para obter mais informações sobre o tipo de `xs:duration` , consulte a parte 2 de Esquema XML do W3C: Recomendação de tipos de dados em http://www.w3.org/TR/xmlschema-2/.</span><span class="sxs-lookup"><span data-stu-id="56bb5-120">For more information on the `xs:duration` type, see the W3C XML Schema Part 2: Datatypes Recommendation at http://www.w3.org/TR/xmlschema-2/.</span></span>  
  
### <a name="xstime-gregorian-date-types-and-systemdatetime"></a><span data-ttu-id="56bb5-121">xs:time, tipos gregorianos de data, e System.DateTime</span><span class="sxs-lookup"><span data-stu-id="56bb5-121">xs:time, Gregorian Date Types, and System.DateTime</span></span>  
 <span data-ttu-id="56bb5-122">Quando um valor de `xs:time` é mapeado para um objeto de <xref:System.DateTime> , o campo de <xref:System.DateTime.MinValue> é usado para inicializar propriedades de data do objeto de <xref:System.DateTime> (como <xref:System.DateTime.Year%2A>, <xref:System.DateTime.Month%2A>, e <xref:System.DateTime.Day%2A>) para o valor possível com o menor de <xref:System.DateTime> .</span><span class="sxs-lookup"><span data-stu-id="56bb5-122">When an `xs:time` value is mapped to a <xref:System.DateTime> object, the <xref:System.DateTime.MinValue> field is used to initialize the date properties of the <xref:System.DateTime> object (such as <xref:System.DateTime.Year%2A>, <xref:System.DateTime.Month%2A>, and <xref:System.DateTime.Day%2A>) to the smallest possible <xref:System.DateTime> value.</span></span>  
  
 <span data-ttu-id="56bb5-123">Da mesma forma, as instâncias de `xs:gMonth`, `xs:gDay`, `xs:gYear`, `xs:gYearMonth` e `xs:gMonthDay` também são mapeados para um objeto de <xref:System.DateTime> .</span><span class="sxs-lookup"><span data-stu-id="56bb5-123">Similarly, instances of `xs:gMonth`, `xs:gDay`, `xs:gYear`, `xs:gYearMonth` and `xs:gMonthDay` are also mapped to a <xref:System.DateTime> object.</span></span> <span data-ttu-id="56bb5-124">As propriedades não usado no objeto de <xref:System.DateTime> são inicializadas àquelas de <xref:System.DateTime.MinValue>.</span><span class="sxs-lookup"><span data-stu-id="56bb5-124">Unused properties on the <xref:System.DateTime> object are initialized to those from <xref:System.DateTime.MinValue>.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="56bb5-125">Você não pode depender no valor de <xref:System.DateTime.Year%2A?displayProperty=nameWithType> quando o conteúdo está digitado como `xs:gMonthDay`.</span><span class="sxs-lookup"><span data-stu-id="56bb5-125">You cannot rely on the <xref:System.DateTime.Year%2A?displayProperty=nameWithType> value when the content is typed as `xs:gMonthDay`.</span></span> <span data-ttu-id="56bb5-126">O valor de <xref:System.DateTime.Year%2A?displayProperty=nameWithType> é sempre definido como 1904 nesse caso.</span><span class="sxs-lookup"><span data-stu-id="56bb5-126">The <xref:System.DateTime.Year%2A?displayProperty=nameWithType> value is always set to 1904 in this case.</span></span>  
  
### <a name="xsanyuri-and-systemuri"></a><span data-ttu-id="56bb5-127">xs:anyURI e System.Uri</span><span class="sxs-lookup"><span data-stu-id="56bb5-127">xs:anyURI and System.Uri</span></span>  
 <span data-ttu-id="56bb5-128">Quando uma instância de `xs:anyURI` que representa o URL relativa é mapeada a <xref:System.Uri>, o objeto de <xref:System.Uri> não tem URI base.</span><span class="sxs-lookup"><span data-stu-id="56bb5-128">When an instance of `xs:anyURI` that represents a relative URI is mapped to a <xref:System.Uri>, the <xref:System.Uri> object does not have a base URI.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="56bb5-129">Consulte também</span><span class="sxs-lookup"><span data-stu-id="56bb5-129">See Also</span></span>  
 <span data-ttu-id="56bb5-130">[Type Support in the System.Xml Classes](../../../../docs/standard/data/xml/type-support-in-the-system-xml-classes.md) (Suporte a tipo nas classes System.XML)</span><span class="sxs-lookup"><span data-stu-id="56bb5-130">[Type Support in the System.Xml Classes](../../../../docs/standard/data/xml/type-support-in-the-system-xml-classes.md)</span></span>
