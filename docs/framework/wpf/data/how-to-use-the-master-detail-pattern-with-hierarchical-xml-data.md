---
title: "Como usar o padrão de detalhes mestre com dados XML hierárquicos"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- data binding [WPF], Master-Detail data paradigm
- Master-Detail data paradigm
ms.assetid: eb8dbdd8-5871-42bb-a16b-04e655fea677
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: f0ef460664b3701f4942b8c28b8e39f891d7c871
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
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
