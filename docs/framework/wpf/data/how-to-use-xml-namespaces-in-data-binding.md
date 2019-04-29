---
title: 'Como: Usar namespaces de XML na vinculação de dados'
ms.date: 03/30/2017
helpviewer_keywords:
- XML [WPF], namespaces
- data binding [WPF], XML namespaces
- namespaces [WPF], XML
ms.assetid: a47c832f-dc84-48f2-96d5-cde18fc4284b
ms.openlocfilehash: 38bf6e8f88b0325193d49148cd6c33031f7b0a6d
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61931905"
---
# <a name="how-to-use-xml-namespaces-in-data-binding"></a>Como: Usar namespaces de XML na vinculação de dados
## <a name="example"></a>Exemplo  
 Este exemplo mostra como lidar com namespaces especificados em seu [!INCLUDE[TLA#tla_xml](../../../../includes/tlasharptla-xml-md.md)] origem da associação.  
  
 Se sua [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] dados tem as seguintes [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] definição de namespace:  
  
 `<rss version="2.0" xmlns:dc="http://purl.org/dc/elements/1.1/">`  
  
 Você pode usar o <xref:System.Windows.Data.XmlNamespaceMapping> elemento para mapear o namespace para um <xref:System.Windows.Data.XmlNamespaceMapping.Prefix%2A>, conforme mostrado no exemplo a seguir. Você pode usar o <xref:System.Windows.Data.XmlNamespaceMapping.Prefix%2A> para referir-se a [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] namespace. O <xref:System.Windows.Controls.ListBox> neste exemplo exibe a *title* e *DC: Date* de cada *item*.  
  
 [!code-xaml[XmlnsBindSnippet#XmlNamespaceMapping](~/samples/snippets/csharp/VS_Snippets_Wpf/XmlnsBindSnippet/CS/Window1.xaml#xmlnamespacemapping)]  
  
 Observe que o <xref:System.Windows.Data.XmlNamespaceMapping.Prefix%2A> você especificar não precisa corresponder à usada na [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] de origem; se o prefixo for alterado no [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] fonte seu mapeamento ainda funciona.  
  
 Nesse exemplo específico, o [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] dados vêm de um serviço web, mas o <xref:System.Windows.Data.XmlNamespaceMapping> elemento também funciona com embutido [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] ou [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] dados em um arquivo incorporado.  
  
## <a name="see-also"></a>Consulte também

- [Associar dados XML usando um XMLDataProvider e consultas XPath](how-to-bind-to-xml-data-using-an-xmldataprovider-and-xpath-queries.md)
- [Visão geral da vinculação de dados](data-binding-overview.md)
- [Tópicos de instruções](data-binding-how-to-topics.md)
