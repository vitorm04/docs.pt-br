---
title: Como usar namespaces XML na vinculação de dados
ms.date: 03/30/2017
helpviewer_keywords:
- XML [WPF], namespaces
- data binding [WPF], XML namespaces
- namespaces [WPF], XML
ms.assetid: a47c832f-dc84-48f2-96d5-cde18fc4284b
ms.openlocfilehash: 9d8ddc5445bac28c68cd6cc99acf3313613a8c7f
ms.sourcegitcommit: 82f94a44ad5c64a399df2a03fa842db308185a76
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/25/2019
ms.locfileid: "72919661"
---
# <a name="how-to-use-xml-namespaces-in-data-binding"></a>Como usar namespaces XML na vinculação de dados
## <a name="example"></a>Exemplo
 Este exemplo mostra como tratar namespaces especificados em sua fonte de associação de [!INCLUDE[TLA#tla_xml](../../../../includes/tlasharptla-xml-md.md)].

 Se seus dados de [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] tiverem a seguinte definição de namespace [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)]:

 `<rss version="2.0" xmlns:dc="http://purl.org/dc/elements/1.1/">`

 Você pode usar o elemento <xref:System.Windows.Data.XmlNamespaceMapping> para mapear o namespace para um <xref:System.Windows.Data.XmlNamespaceMapping.Prefix%2A>, como no exemplo a seguir. Em seguida, você pode usar o <xref:System.Windows.Data.XmlNamespaceMapping.Prefix%2A> para fazer referência ao namespace [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)]. O <xref:System.Windows.Controls.ListBox> neste exemplo exibe o *título* e o *DC: data* de cada *Item*.

 [!code-xaml[XmlnsBindSnippet#XmlNamespaceMapping](~/samples/snippets/csharp/VS_Snippets_Wpf/XmlnsBindSnippet/CS/Window1.xaml#xmlnamespacemapping)]

 Observe que o <xref:System.Windows.Data.XmlNamespaceMapping.Prefix%2A> especificado não precisa corresponder ao usado na fonte de [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)]; Se o prefixo for alterado na fonte de [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)], seu mapeamento ainda funcionará.

 Neste exemplo específico, os dados de [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] vêm de um serviço Web, mas o elemento <xref:System.Windows.Data.XmlNamespaceMapping> também funciona com dados embutidos [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] ou [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] em um arquivo inserido.

## <a name="see-also"></a>Consulte também

- [Associar dados XML usando um XMLDataProvider e consultas XPath](how-to-bind-to-xml-data-using-an-xmldataprovider-and-xpath-queries.md)
- [Visão geral da vinculação de dados](data-binding-overview.md)
- [Tópicos explicativos](data-binding-how-to-topics.md)
