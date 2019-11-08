---
title: Como usar namespaces XML na vinculação de dados
ms.date: 03/30/2017
helpviewer_keywords:
- XML [WPF], namespaces
- data binding [WPF], XML namespaces
- namespaces [WPF], XML
ms.assetid: a47c832f-dc84-48f2-96d5-cde18fc4284b
ms.openlocfilehash: f6e6e042fa5583fcf91bd15c524537490fb6670c
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/07/2019
ms.locfileid: "73740580"
---
# <a name="how-to-use-xml-namespaces-in-data-binding"></a>Como usar namespaces XML na vinculação de dados
## <a name="example"></a>Exemplo
 Este exemplo mostra como tratar namespaces especificados em sua origem de associação XML.

 Se os dados XML tiverem a seguinte definição de namespace XML:

 `<rss version="2.0" xmlns:dc="http://purl.org/dc/elements/1.1/">`

 Você pode usar o elemento <xref:System.Windows.Data.XmlNamespaceMapping> para mapear o namespace para um <xref:System.Windows.Data.XmlNamespaceMapping.Prefix%2A>, como no exemplo a seguir. Você pode usar o <xref:System.Windows.Data.XmlNamespaceMapping.Prefix%2A> para se referir ao namespace XML. O <xref:System.Windows.Controls.ListBox> neste exemplo exibe o *título* e o *DC: data* de cada *Item*.

 [!code-xaml[XmlnsBindSnippet#XmlNamespaceMapping](~/samples/snippets/csharp/VS_Snippets_Wpf/XmlnsBindSnippet/CS/Window1.xaml#xmlnamespacemapping)]

 Observe que o <xref:System.Windows.Data.XmlNamespaceMapping.Prefix%2A> especificado não precisa corresponder ao usado na origem XML; Se o prefixo for alterado na origem XML, seu mapeamento ainda funcionará.

 Neste exemplo específico, os dados XML vêm de um serviço Web, mas o elemento <xref:System.Windows.Data.XmlNamespaceMapping> também funciona com dados XML ou XML embutidos em um arquivo inserido.

## <a name="see-also"></a>Consulte também

- [Associar dados XML usando um XMLDataProvider e consultas XPath](how-to-bind-to-xml-data-using-an-xmldataprovider-and-xpath-queries.md)
- [Visão geral da vinculação de dados](../../../desktop-wpf/data/data-binding-overview.md)
- [Tópicos explicativos](data-binding-how-to-topics.md)
