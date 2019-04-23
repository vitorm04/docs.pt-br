---
title: 'Como: Usar o padrão de detalhes mestre com os dados XML hierárquicos'
ms.date: 03/30/2017
helpviewer_keywords:
- data binding [WPF], Master-Detail data paradigm
- Master-Detail data paradigm
ms.assetid: eb8dbdd8-5871-42bb-a16b-04e655fea677
ms.openlocfilehash: ba6c932f519ffa5c3c70ecb21eb9b5d08c40fb28
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59086254"
---
# <a name="how-to-use-the-master-detail-pattern-with-hierarchical-xml-data"></a>Como: Usar o padrão de detalhes mestre com os dados XML hierárquicos
Este exemplo mostra como implementar o cenário mestre / detalhes com [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] dados.  
  
## <a name="example"></a>Exemplo  
 Este exemplo é o [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] versão de dados de exemplo discutido no [usar o padrão de detalhes mestre com dados hierárquicos](how-to-use-the-master-detail-pattern-with-hierarchical-data.md). Neste exemplo, os dados são do arquivo `League.xml`. Observe como o terceiro <xref:System.Windows.Controls.ListBox> controle rastreia as alterações de seleção na segunda <xref:System.Windows.Controls.ListBox> fazendo a ligação com seu <xref:System.Windows.Controls.Primitives.Selector.SelectedValue%2A> propriedade.  
  
 [!code-xaml[MasterDetailXml#HowTo1](~/samples/snippets/csharp/VS_Snippets_Wpf/MasterDetailXml/CS/Window1.xaml#howto1)]  
[!code-xaml[MasterDetailXml#HowTo2](~/samples/snippets/csharp/VS_Snippets_Wpf/MasterDetailXml/CS/Window1.xaml#howto2)]  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Windows.HierarchicalDataTemplate>
- [Tópicos de instruções](data-binding-how-to-topics.md)
