---
title: Como usar o padrão de detalhes mestre com dados XML hierárquicos
ms.date: 03/30/2017
helpviewer_keywords:
- data binding [WPF], Master-Detail data paradigm
- Master-Detail data paradigm
ms.assetid: eb8dbdd8-5871-42bb-a16b-04e655fea677
ms.openlocfilehash: 5b3a9d83dcec169fd9607c84b0a66eab0098b238
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-use-the-master-detail-pattern-with-hierarchical-xml-data"></a>Como usar o padrão de detalhes mestre com dados XML hierárquicos
Este exemplo mostra como implementar o cenário mestre-detalhes com [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] dados.  
  
## <a name="example"></a>Exemplo  
 Este exemplo é o [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] versão de dados de exemplo discutido no [usam o padrão de detalhes mestre com dados hierárquicos](../../../../docs/framework/wpf/data/how-to-use-the-master-detail-pattern-with-hierarchical-data.md). Neste exemplo, os dados são do arquivo `League.xml`. Observe como o terceiro <xref:System.Windows.Controls.ListBox> controle rastreia as alterações de seleção no segundo <xref:System.Windows.Controls.ListBox> associando seu <xref:System.Windows.Controls.Primitives.Selector.SelectedValue%2A> propriedade.  
  
 [!code-xaml[MasterDetailXml#HowTo1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/MasterDetailXml/CS/Window1.xaml#howto1)]  
[!code-xaml[MasterDetailXml#HowTo2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/MasterDetailXml/CS/Window1.xaml#howto2)]  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Windows.HierarchicalDataTemplate>  
 [Tópicos de instruções](../../../../docs/framework/wpf/data/data-binding-how-to-topics.md)
