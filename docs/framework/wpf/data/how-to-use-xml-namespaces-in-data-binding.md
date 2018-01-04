---
title: "Como usar namespaces XML na vinculação de dados"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- XML [WPF], namespaces
- data binding [WPF], XML namespaces
- namespaces [WPF], XML
ms.assetid: a47c832f-dc84-48f2-96d5-cde18fc4284b
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: f23e041a1e6b283cfe5308d6aef861f1fc757a7d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-use-xml-namespaces-in-data-binding"></a>Como usar namespaces XML na vinculação de dados
## <a name="example"></a>Exemplo  
 Este exemplo mostra como lidar com namespaces especificados em seu [!INCLUDE[TLA#tla_xml](../../../../includes/tlasharptla-xml-md.md)] fonte da associação.  
  
 Se seu [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] dados tem as seguintes [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] definição de namespace:  
  
 `<rss version="2.0" xmlns:dc="http://purl.org/dc/elements/1.1/">`  
  
 Você pode usar o <xref:System.Windows.Data.XmlNamespaceMapping> elemento para mapear o namespace para um <xref:System.Windows.Data.XmlNamespaceMapping.Prefix%2A>, conforme mostrado no exemplo a seguir. Você pode usar o <xref:System.Windows.Data.XmlNamespaceMapping.Prefix%2A> para referir-se a [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] namespace. O <xref:System.Windows.Controls.ListBox> neste exemplo exibe o *título* e *DC: Date* de cada *item*.  
  
 [!code-xaml[XmlnsBindSnippet#XmlNamespaceMapping](../../../../samples/snippets/csharp/VS_Snippets_Wpf/XmlnsBindSnippet/CS/Window1.xaml#xmlnamespacemapping)]  
  
 Observe que o <xref:System.Windows.Data.XmlNamespaceMapping.Prefix%2A> você especificar não precisa corresponder à usada no [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] fonte; se o prefixo for alterado no [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] fonte seu mapeamento ainda funciona.  
  
 Nesse exemplo específico, o [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] os dados vêm de um serviço web, mas o <xref:System.Windows.Data.XmlNamespaceMapping> elemento também funciona com embutido [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] ou [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] dados em um arquivo incorporado.  
  
## <a name="see-also"></a>Consulte também  
 [Associar dados XML usando um XMLDataProvider e consultas XPath](../../../../docs/framework/wpf/data/how-to-bind-to-xml-data-using-an-xmldataprovider-and-xpath-queries.md)  
 [Visão geral da vinculação de dados](../../../../docs/framework/wpf/data/data-binding-overview.md)  
 [Tópicos de instruções](../../../../docs/framework/wpf/data/data-binding-how-to-topics.md)
