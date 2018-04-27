---
title: Uso de System. XML
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology: dotnet-standard
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 82302f0d-a621-4c6f-b57d-999bd61f21a6
caps.latest.revision: 4
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 7e90dea873a007c9f148228a2566ff22d91185a3
ms.sourcegitcommit: 2e8acae16ae802f2d6d04e3ce0a6dbf04e476513
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2018
---
# <a name="systemxml-usage"></a>Uso de System. XML
Esta seção fala sobre o uso de vários tipos que residem em <xref:System.Xml?displayProperty=nameWithType> namespaces que podem ser usados para representar dados XML.  
  
 **X não** usar <xref:System.Xml.XmlNode> ou <xref:System.Xml.XmlDocument> para representar dados XML. Favorecer usando as instâncias de <xref:System.Xml.XPath.IXPathNavigable>, <xref:System.Xml.XmlReader>, <xref:System.Xml.XmlWriter>, ou subtipos <xref:System.Xml.Linq.XNode> em vez disso. `XmlNode` e `XmlDocument` não são projetados para expor em APIs públicas.  
  
 **FAZER ✓** usar `XmlReader`, `IXPathNavigable`, ou subtipos `XNode` como entrada ou saída de membros que aceitam ou retornam XML.  
  
 Use essas abstrações em vez de `XmlDocument`, `XmlNode`, ou <xref:System.Xml.XPath.XPathDocument>, pois isso separa os métodos de implementações específicas de um documento XML na memória e permite trabalhar com fontes de dados XML virtuais que expõem `XNode` , `XmlReader`, ou <xref:System.Xml.XPath.XPathNavigator>.  
  
 **X não** subclasse `XmlDocument` se você deseja criar um tipo que representa uma exibição XML de uma fonte de dados ou modelo de objeto subjacente.  
  
 *Portions © 2005, 2009 Microsoft Corporation. Todos os direitos reservados.*  
  
 *Reimpressas pela permissão de Pearson educação, Inc. de [diretrizes de Design do Framework: convenções, linguagens e padrões para bibliotecas do .NET reutilizável, 2ª edição](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) por Krzysztof Cwalina e Brad Abrams, publicados 22 de outubro de 2008, Addison-Wesley Professional como parte da série de desenvolvimento do Microsoft Windows.*  
  
## <a name="see-also"></a>Consulte também  
 [Diretrizes de design do Framework](../../../docs/standard/design-guidelines/index.md)  
 [Diretrizes de uso](../../../docs/standard/design-guidelines/usage-guidelines.md)
