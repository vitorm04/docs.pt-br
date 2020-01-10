---
title: Uso de System.XML
ms.date: 10/22/2008
ms.technology: dotnet-standard
ms.assetid: 82302f0d-a621-4c6f-b57d-999bd61f21a6
ms.openlocfilehash: c57f5451526094d58066d7d391f41795f17732de
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75709030"
---
# <a name="systemxml-usage"></a>Uso de System.XML
Esta seção fala sobre o uso de vários tipos que residem em namespaces <xref:System.Xml?displayProperty=nameWithType> que podem ser usados para representar dados XML.  
  
 **X DO NOT** usar <xref:System.Xml.XmlNode> ou <xref:System.Xml.XmlDocument> para representar dados XML. Favor usar instâncias de <xref:System.Xml.XPath.IXPathNavigable>, <xref:System.Xml.XmlReader>, <xref:System.Xml.XmlWriter>ou subtipos de <xref:System.Xml.Linq.XNode> em vez disso. `XmlNode` e `XmlDocument` não são projetados para exposição em APIs públicas.  
  
 **✓ DO** usar `XmlReader`, `IXPathNavigable`, ou subtipos `XNode` como entrada ou saída de membros que aceitam ou retornam XML.  
  
 Use essas abstrações em vez de `XmlDocument`, `XmlNode`ou <xref:System.Xml.XPath.XPathDocument>, porque isso dissocia os métodos de implementações específicas de um documento XML na memória e permite que eles trabalhem com fontes de dados XML virtuais que expõem `XNode`, `XmlReader`ou <xref:System.Xml.XPath.XPathNavigator>.  
  
 **X DO NOT** subclasse `XmlDocument` se você deseja criar um tipo que representa uma exibição XML de uma fonte de dados ou modelo de objeto subjacente.  
  
 *Partes © 2005, 2009 Microsoft Corporation. Todos os direitos reservados.*  
  
 *Reimpresso com permissão da Pearson Education, Inc. das [Diretrizes de Design do Framework: convenções, linguagens e padrões para bibliotecas do .NET reutilizável, 2ª edição](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) por Krzysztof Cwalina e Brad Abrams, publicado em 22 de outubro de 2008 por Addison-Wesley Professional como parte da série de desenvolvimento do Microsoft Windows.*  
  
## <a name="see-also"></a>Veja também

- [Diretrizes de design do Framework](../../../docs/standard/design-guidelines/index.md)
- [Diretrizes de uso](../../../docs/standard/design-guidelines/usage-guidelines.md)
