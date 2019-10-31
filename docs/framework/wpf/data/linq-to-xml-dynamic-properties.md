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
# <a name="linq-to-xml-dynamic-properties"></a>Propriedades dinâmicas do LINQ to XML

Esta seção fornece informações de referência sobre as propriedades dinâmicas em LINQ to XML. Especificamente, essas propriedades são expostos por classes de <xref:System.Xml.Linq.XAttribute> e de <xref:System.Xml.Linq.XElement> , que estão no espaço de <xref:System.Xml.Linq> .

Conforme explicado no tópico [Visão geral da associação de dados do WPF com o LINQ to XML](wpf-data-binding-with-linq-to-xml-overview.md), cada uma das propriedades dinâmicas é equivalente a um método ou uma propriedade pública padrão na mesma classe. Esses membros padrão devem ser usados para a maioria das finalidades; as propriedades dinâmicas são fornecidas especificamente para cenários de associação de dados LINQ to XML. Para obter mais informações sobre membros padrão dessas classes, consulte os tópicos de referência de <xref:System.Xml.Linq.XAttribute> e de <xref:System.Xml.Linq.XElement> .

Em relação a seus valores resolvidos, as propriedades dinâmicas nesta seção se enquadram em duas categorias:

- O simples, como as propriedades de `Value` classes de <xref:System.Xml.Linq.XAttribute> e de <xref:System.Xml.Linq.XElement> , que são consideradas como um único valor.

- Valores indexados, como as propriedades [Elementos](elements-xelement-dynamic-property.md) e [Descendentes](descendants-xelement-dynamic-property.md) de <xref:System.Xml.Linq.XElement>, que são resolvidas em um tipo de indexador. Para que os tipos do indexador são resolvidos com o valor desejado ou à coleção, um parâmetro expandido do nome deve ser-lhes passado.

Todas as propriedades dinâmicas que retornam um valor indexado do tipo <xref:System.Collections.Generic.IEnumerable%601> usam a execução adiada. Para obter mais informações sobre a execução adiada, confira [Introdução a consultas LINQ (C#)](../../../csharp/programming-guide/concepts/linq/introduction-to-linq-queries.md).

## <a name="reference"></a>Referência

- <xref:System.Xml.Linq>
- <xref:System.Xml.Linq.XElement?displayProperty=fullName>
- <xref:System.Xml.Linq.XAttribute?displayProperty=fullName>

## <a name="see-also"></a>Consulte também

- [Vinculação de dados do WPF com o LINQ to XML](wpf-data-binding-with-linq-to-xml-overview.md)
- [Associação de dados do WPF com LINQ to XML](wpf-data-binding-with-linq-to-xml-overview.md)
- [Introdução a consultas LINQ (C#)](../../../csharp/programming-guide/concepts/linq/introduction-to-linq-queries.md)
