---
title: Referência de propriedades dinâmicas LINQ to XML
ms.date: 10/22/2019
ms.topic: reference
ms.openlocfilehash: 48b51e92eb78786b2cc189e3e7daa00875b41585
ms.sourcegitcommit: 5a28f8eb071fcc09b045b0c4ae4b96898673192e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2019
ms.locfileid: "73197045"
---
# <a name="linq-to-xml-dynamic-properties"></a><span data-ttu-id="a7609-102">Propriedades dinâmicas do LINQ to XML</span><span class="sxs-lookup"><span data-stu-id="a7609-102">LINQ to XML dynamic properties</span></span>

<span data-ttu-id="a7609-103">Esta seção fornece informações de referência sobre as propriedades dinâmicas em LINQ to XML.</span><span class="sxs-lookup"><span data-stu-id="a7609-103">This section provides reference information about the dynamic properties in LINQ to XML.</span></span> <span data-ttu-id="a7609-104">Especificamente, essas propriedades são expostos por classes de <xref:System.Xml.Linq.XAttribute> e de <xref:System.Xml.Linq.XElement> , que estão no espaço de <xref:System.Xml.Linq> .</span><span class="sxs-lookup"><span data-stu-id="a7609-104">Specifically, these properties are exposed by the <xref:System.Xml.Linq.XAttribute> and <xref:System.Xml.Linq.XElement> classes, which are in the <xref:System.Xml.Linq> namespace.</span></span>

<span data-ttu-id="a7609-105">Conforme explicado no tópico [Visão geral da associação de dados do WPF com o LINQ to XML](wpf-data-binding-with-linq-to-xml-overview.md), cada uma das propriedades dinâmicas é equivalente a um método ou uma propriedade pública padrão na mesma classe.</span><span class="sxs-lookup"><span data-stu-id="a7609-105">As explained in the topic [Overview of WPF data binding with LINQ to XML](wpf-data-binding-with-linq-to-xml-overview.md), each of the dynamic properties is equivalent to a standard public property or method in the same class.</span></span> <span data-ttu-id="a7609-106">Esses membros padrão devem ser usados para a maioria das finalidades; as propriedades dinâmicas são fornecidas especificamente para cenários de associação de dados LINQ to XML.</span><span class="sxs-lookup"><span data-stu-id="a7609-106">These standard members should be used for most purposes; dynamic properties are provided specifically for LINQ to XML data binding scenarios.</span></span> <span data-ttu-id="a7609-107">Para obter mais informações sobre membros padrão dessas classes, consulte os tópicos de referência de <xref:System.Xml.Linq.XAttribute> e de <xref:System.Xml.Linq.XElement> .</span><span class="sxs-lookup"><span data-stu-id="a7609-107">For more information about the standard members of these classes, see the <xref:System.Xml.Linq.XAttribute> and <xref:System.Xml.Linq.XElement> reference topics.</span></span>

<span data-ttu-id="a7609-108">Em relação a seus valores resolvidos, as propriedades dinâmicas nesta seção se enquadram em duas categorias:</span><span class="sxs-lookup"><span data-stu-id="a7609-108">With respect to their resolved values, the dynamic properties in this section fall into two categories:</span></span>

- <span data-ttu-id="a7609-109">O simples, como as propriedades de `Value` classes de <xref:System.Xml.Linq.XAttribute> e de <xref:System.Xml.Linq.XElement> , que são consideradas como um único valor.</span><span class="sxs-lookup"><span data-stu-id="a7609-109">Simple ones, such as the `Value` properties in the <xref:System.Xml.Linq.XAttribute> and <xref:System.Xml.Linq.XElement> classes, that resolve to a single value.</span></span>

- <span data-ttu-id="a7609-110">Valores indexados, como as propriedades [Elementos](elements-xelement-dynamic-property.md) e [Descendentes](descendants-xelement-dynamic-property.md) de <xref:System.Xml.Linq.XElement>, que são resolvidas em um tipo de indexador.</span><span class="sxs-lookup"><span data-stu-id="a7609-110">Indexed values, such as the [Elements](elements-xelement-dynamic-property.md) and [Descendants](descendants-xelement-dynamic-property.md) properties of <xref:System.Xml.Linq.XElement>, that resolve into an indexer type.</span></span> <span data-ttu-id="a7609-111">Para que os tipos do indexador são resolvidos com o valor desejado ou à coleção, um parâmetro expandido do nome deve ser-lhes passado.</span><span class="sxs-lookup"><span data-stu-id="a7609-111">For indexer types to be resolved to the desired value or collection, an expanded name parameter must be passed to them.</span></span>

<span data-ttu-id="a7609-112">Todas as propriedades dinâmicas que retornam um valor indexado do tipo <xref:System.Collections.Generic.IEnumerable%601> usam a execução adiada.</span><span class="sxs-lookup"><span data-stu-id="a7609-112">All the dynamic properties that return an indexed value of type <xref:System.Collections.Generic.IEnumerable%601> use deferred execution.</span></span> <span data-ttu-id="a7609-113">Para obter mais informações sobre a execução adiada, confira [Introdução a consultas LINQ (C#)](../../../csharp/programming-guide/concepts/linq/introduction-to-linq-queries.md).</span><span class="sxs-lookup"><span data-stu-id="a7609-113">For more information about deferred execution, see [Introduction to LINQ queries (C#)](../../../csharp/programming-guide/concepts/linq/introduction-to-linq-queries.md).</span></span>

## <a name="reference"></a><span data-ttu-id="a7609-114">Referência</span><span class="sxs-lookup"><span data-stu-id="a7609-114">Reference</span></span>

- <xref:System.Xml.Linq>
- <xref:System.Xml.Linq.XElement?displayProperty=fullName>
- <xref:System.Xml.Linq.XAttribute?displayProperty=fullName>

## <a name="see-also"></a><span data-ttu-id="a7609-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a7609-115">See also</span></span>

- [<span data-ttu-id="a7609-116">Vinculação de dados do WPF com o LINQ to XML</span><span class="sxs-lookup"><span data-stu-id="a7609-116">WPF data binding with LINQ to XML</span></span>](wpf-data-binding-with-linq-to-xml-overview.md)
- [<span data-ttu-id="a7609-117">Associação de dados do WPF com LINQ to XML</span><span class="sxs-lookup"><span data-stu-id="a7609-117">WPF data binding with LINQ to XML overview</span></span>](wpf-data-binding-with-linq-to-xml-overview.md)
- [<span data-ttu-id="a7609-118">Introdução a consultas LINQ (C#)</span><span class="sxs-lookup"><span data-stu-id="a7609-118">Introduction to LINQ queries (C#)</span></span>](../../../csharp/programming-guide/concepts/linq/introduction-to-linq-queries.md)
