---
title: "Visão geral (Visual Basic) de eixos do LINQ to XML | Documentos do Microsoft"
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
ms.assetid: 9161f151-cfa8-4408-94ba-08a9ba3a486d
caps.latest.revision: 4
author: dotnet-bot
ms.author: dotnetcontent
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: b127aa6b443e865c76831d886f110550ec785e9b
ms.lasthandoff: 03/13/2017


---
# <a name="linq-to-xml-axes-overview-visual-basic"></a>LINQ to XML visão geral dos eixos (Visual Basic)
Após criar uma árvore XML ou carregar um documento XML em uma árvore XML, você poderá consultá-la para localizar elementos e atributos, e recuperar seus valores. Você recupera coleções através de *métodos de eixo*, também chamado *eixos*. Alguns eixos são métodos de <xref:System.Xml.Linq.XElement>e <xref:System.Xml.Linq.XDocument>classes que retornam <xref:System.Collections.Generic.IEnumerable%601>coleções.</xref:System.Collections.Generic.IEnumerable%601> </xref:System.Xml.Linq.XDocument> </xref:System.Xml.Linq.XElement> Alguns eixos são métodos de extensão em que a <xref:System.Xml.Linq.Extensions>classe.</xref:System.Xml.Linq.Extensions> Os eixos implementados como métodos de extensão operam em coleções e retornam coleções.  
  
 Conforme descrito em [visão geral da classe XElement](http://msdn.microsoft.com/library/d35180fe-7016-4895-9bfc-ba1e3f7875ec), um <xref:System.Xml.Linq.XElement>objeto representa um nó de elemento único.</xref:System.Xml.Linq.XElement> O conteúdo de um elemento pode ser complexo (às vezes denominado conteúdo estruturado) ou pode ser um elemento simples. Um elemento simples pode ser vazio ou conter um valor. Se o nó contiver o conteúdo estruturado, você poderá usar os vários métodos de eixo para recuperar enumerações de elementos descendentes. Os métodos de eixo mais comumente usadas são <xref:System.Xml.Linq.XContainer.Elements%2A>e <xref:System.Xml.Linq.XContainer.Descendants%2A>.</xref:System.Xml.Linq.XContainer.Descendants%2A> </xref:System.Xml.Linq.XContainer.Elements%2A>  
  
 Além dos métodos de eixo, que retornam coleções, há mais dois métodos que você usará comumente [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] consultas. O <xref:System.Xml.Linq.XContainer.Element%2A>método retorna uma única <xref:System.Xml.Linq.XElement>.</xref:System.Xml.Linq.XElement> </xref:System.Xml.Linq.XContainer.Element%2A> O <xref:System.Xml.Linq.XElement.Attribute%2A>método retorna uma única <xref:System.Xml.Linq.XAttribute>.</xref:System.Xml.Linq.XAttribute> </xref:System.Xml.Linq.XElement.Attribute%2A>  
  
 Em várias circunstâncias, as consultas do [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)] fornecem a maneira mais eficiente de examinar uma árvore, extrair dados dela e transformá-la. [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)]consultas de operam em objetos que implementam <xref:System.Collections.Generic.IEnumerable%601>e o [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] eixos retorno <xref:System.Collections.Generic.IEnumerable%601>de <xref:System.Xml.Linq.XElement>coleções, e <xref:System.Collections.Generic.IEnumerable%601>de <xref:System.Xml.Linq.XAttribute>coleções.</xref:System.Xml.Linq.XAttribute> </xref:System.Collections.Generic.IEnumerable%601> </xref:System.Xml.Linq.XElement> </xref:System.Collections.Generic.IEnumerable%601> </xref:System.Collections.Generic.IEnumerable%601> Você precisa dessas coleções para executar suas consultas.  
  
 Além dos métodos de eixo que recuperam coleções de elementos e atributos, há métodos de eixo que permitem a você iterar na árvore detalhadamente. Por exemplo, em vez de tratar elementos e atributos, você pode trabalhar com os nós da árvore. Os nós são um nível mais refinado de granularidade do que os elementos e os atributos. Ao trabalhar com os nós, você pode examinar comentários XML, nós de texto, instruções de processamento e muito mais. Essa funcionalidade é importante, por exemplo, para alguém que estiver escrevendo em um processador de texto e deseja salvar documentos como XML. No entanto, a maioria dos programadores XML se preocupam basicamente com os elementos, os atributos e seus valores.  
  
## <a name="methods-for-retrieving-a-collection-of-elements"></a>Métodos para recuperar uma coleção de elementos  
 A seguir está um resumo dos métodos da <xref:System.Xml.Linq.XElement>classe (ou suas classes base) que você chamar um <xref:System.Xml.Linq.XElement>para retornar uma coleção de elementos.</xref:System.Xml.Linq.XElement> </xref:System.Xml.Linq.XElement>  
  
|Método|Descrição|  
|------------|-----------------|  
|<xref:System.Xml.Linq.XNode.Ancestors%2A?displayProperty=fullName></xref:System.Xml.Linq.XNode.Ancestors%2A?displayProperty=fullName>|Retorna um <xref:System.Collections.Generic.IEnumerable%601>de <xref:System.Xml.Linq.XElement>dos ancestrais desse elemento.</xref:System.Xml.Linq.XElement> </xref:System.Collections.Generic.IEnumerable%601> Uma sobrecarga retorna um <xref:System.Collections.Generic.IEnumerable%601> <xref:System.Xml.Linq.XElement>dos ancestrais que têm o <xref:System.Xml.Linq.XName>.</xref:System.Xml.Linq.XName> especificado</xref:System.Xml.Linq.XElement> </xref:System.Collections.Generic.IEnumerable%601>|  
|<xref:System.Xml.Linq.XContainer.Descendants%2A?displayProperty=fullName></xref:System.Xml.Linq.XContainer.Descendants%2A?displayProperty=fullName>|Retorna um <xref:System.Collections.Generic.IEnumerable%601>de <xref:System.Xml.Linq.XElement>os descendentes desse elemento.</xref:System.Xml.Linq.XElement> </xref:System.Collections.Generic.IEnumerable%601> Uma sobrecarga retorna um <xref:System.Collections.Generic.IEnumerable%601>dos <xref:System.Xml.Linq.XElement>descendentes que têm o <xref:System.Xml.Linq.XName>.</xref:System.Xml.Linq.XName> especificado</xref:System.Xml.Linq.XElement> </xref:System.Collections.Generic.IEnumerable%601>|  
|<xref:System.Xml.Linq.XContainer.Elements%2A?displayProperty=fullName></xref:System.Xml.Linq.XContainer.Elements%2A?displayProperty=fullName>|Retorna um <xref:System.Collections.Generic.IEnumerable%601>de <xref:System.Xml.Linq.XElement>dos elementos filho desse elemento.</xref:System.Xml.Linq.XElement> </xref:System.Collections.Generic.IEnumerable%601> Uma sobrecarga retorna um <xref:System.Collections.Generic.IEnumerable%601> <xref:System.Xml.Linq.XElement>dos elementos filho que têm o <xref:System.Xml.Linq.XName>.</xref:System.Xml.Linq.XName> especificado</xref:System.Xml.Linq.XElement> </xref:System.Collections.Generic.IEnumerable%601>|  
|<xref:System.Xml.Linq.XNode.ElementsAfterSelf%2A?displayProperty=fullName></xref:System.Xml.Linq.XNode.ElementsAfterSelf%2A?displayProperty=fullName>|Retorna um <xref:System.Collections.Generic.IEnumerable%601>de <xref:System.Xml.Linq.XElement>os elementos que vêm após esse elemento.</xref:System.Xml.Linq.XElement> </xref:System.Collections.Generic.IEnumerable%601> Uma sobrecarga retorna um <xref:System.Collections.Generic.IEnumerable%601>dos <xref:System.Xml.Linq.XElement>elementos após esse elemento que tem o <xref:System.Xml.Linq.XName>.</xref:System.Xml.Linq.XName> especificado</xref:System.Xml.Linq.XElement> </xref:System.Collections.Generic.IEnumerable%601>|  
|<xref:System.Xml.Linq.XNode.ElementsBeforeSelf%2A?displayProperty=fullName></xref:System.Xml.Linq.XNode.ElementsBeforeSelf%2A?displayProperty=fullName>|Retorna um <xref:System.Collections.Generic.IEnumerable%601>de <xref:System.Xml.Linq.XElement>os elementos que vêm antes desse elemento.</xref:System.Xml.Linq.XElement> </xref:System.Collections.Generic.IEnumerable%601> Uma sobrecarga retorna um <xref:System.Collections.Generic.IEnumerable%601>dos <xref:System.Xml.Linq.XElement>elementos antes desse elemento que tem o <xref:System.Xml.Linq.XName>.</xref:System.Xml.Linq.XName> especificado</xref:System.Xml.Linq.XElement> </xref:System.Collections.Generic.IEnumerable%601>|  
|<xref:System.Xml.Linq.XElement.AncestorsAndSelf%2A?displayProperty=fullName></xref:System.Xml.Linq.XElement.AncestorsAndSelf%2A?displayProperty=fullName>|Retorna um <xref:System.Collections.Generic.IEnumerable%601>de <xref:System.Xml.Linq.XElement>desse elemento e seus ancestrais.</xref:System.Xml.Linq.XElement> </xref:System.Collections.Generic.IEnumerable%601> Uma sobrecarga retorna um <xref:System.Collections.Generic.IEnumerable%601>dos <xref:System.Xml.Linq.XElement>elementos que têm o <xref:System.Xml.Linq.XName>.</xref:System.Xml.Linq.XName> especificado</xref:System.Xml.Linq.XElement> </xref:System.Collections.Generic.IEnumerable%601>|  
|<xref:System.Xml.Linq.XElement.DescendantsAndSelf%2A?displayProperty=fullName></xref:System.Xml.Linq.XElement.DescendantsAndSelf%2A?displayProperty=fullName>|Retorna um <xref:System.Collections.Generic.IEnumerable%601>de <xref:System.Xml.Linq.XElement>desse elemento e seus descendentes.</xref:System.Xml.Linq.XElement> </xref:System.Collections.Generic.IEnumerable%601> Uma sobrecarga retorna um <xref:System.Collections.Generic.IEnumerable%601>dos <xref:System.Xml.Linq.XElement>elementos que têm o <xref:System.Xml.Linq.XName>.</xref:System.Xml.Linq.XName> especificado</xref:System.Xml.Linq.XElement> </xref:System.Collections.Generic.IEnumerable%601>|  
  
## <a name="method-for-retrieving-a-single-element"></a>Método para recuperar um único elemento  
 O método a seguir recupera um único filho de um <xref:System.Xml.Linq.XElement>objeto.</xref:System.Xml.Linq.XElement>  
  
|Método|Descrição|  
|------------|-----------------|  
|<xref:System.Xml.Linq.XContainer.Element%2A?displayProperty=fullName>|Retorna o primeiro filho <xref:System.Xml.Linq.XElement>que tem o <xref:System.Xml.Linq.XName>.</xref:System.Xml.Linq.XName> especificado do objeto</xref:System.Xml.Linq.XElement>|  
  
## <a name="method-for-retrieving-a-collection-of-attributes"></a>Método para recuperar uma coleção de atributos  
 O método a seguir recupera atributos de uma <xref:System.Xml.Linq.XElement>objeto.</xref:System.Xml.Linq.XElement>  
  
|Método|Descrição|  
|------------|-----------------|  
|<xref:System.Xml.Linq.XElement.Attributes%2A?displayProperty=fullName></xref:System.Xml.Linq.XElement.Attributes%2A?displayProperty=fullName>|Retorna um <xref:System.Collections.Generic.IEnumerable%601>de <xref:System.Xml.Linq.XAttribute>de todos os atributos.</xref:System.Xml.Linq.XAttribute> </xref:System.Collections.Generic.IEnumerable%601>|  
  
## <a name="method-for-retrieving-a-single-attribute"></a>Método para recuperar um único atributo  
 O método a seguir recupera um único atributo de uma <xref:System.Xml.Linq.XElement>objeto.</xref:System.Xml.Linq.XElement>  
  
|Método|Descrição|  
|------------|-----------------|  
|<xref:System.Xml.Linq.XElement.Attribute%2A?displayProperty=fullName>|Retorna o <xref:System.Xml.Linq.XAttribute>que foi especificado <xref:System.Xml.Linq.XName>.</xref:System.Xml.Linq.XName> </xref:System.Xml.Linq.XAttribute>|  
  
## <a name="see-also"></a>Consulte também  
 [Eixos LINQ to XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml-axes.md)
