---
title: Como criar TreeViews simples ou complexos
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- TreeView control [WPF], creating
- Control class [WPF], TreeView [WPF], creating
ms.assetid: 1defbb78-b8e7-4c0e-b650-576453ac828d
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 3a7e87295a50f901be0c7028bb2d6025b51c248c
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-create-simple-or-complex-treeviews"></a>Como criar TreeViews simples ou complexos
Este exemplo mostra como criar simples ou complexa <xref:System.Windows.Controls.TreeView> controles.  
  
 Um <xref:System.Windows.Controls.TreeView> consiste em uma hierarquia de <xref:System.Windows.Controls.TreeViewItem> controles, que podem conter cadeias de caracteres de texto simples e também conteúdo mais complexo, como <xref:System.Windows.Controls.Button> controles ou <xref:System.Windows.Controls.StackPanel> com conteúdo incorporado. Você pode definir explicitamente o <xref:System.Windows.Controls.TreeView> conteúdo ou uma fonte de dados pode fornecer o conteúdo. Este tópico fornece exemplos desses conceitos.  
  
## <a name="example"></a>Exemplo  
 O <xref:System.Windows.Controls.HeaderedItemsControl.Header%2A> propriedade o <xref:System.Windows.Controls.TreeViewItem> contém o conteúdo que o <xref:System.Windows.Controls.TreeView> exibe para aquele item. Um <xref:System.Windows.Controls.TreeViewItem> também pode ter <xref:System.Windows.Controls.TreeViewItem> controles como seus elementos filho e você podem definir esses elementos filho usando o <xref:System.Windows.Controls.ItemsControl.Items%2A> propriedade.  
  
 O exemplo a seguir mostra como definir explicitamente <xref:System.Windows.Controls.TreeViewItem> conteúdo definindo o <xref:System.Windows.Controls.HeaderedItemsControl.Header%2A> propriedade como uma cadeia de caracteres de texto.  
  
 [!code-xaml[TreeViewSimple#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TreeViewSimple/CS/Window1.xaml#1)]  
  
 O exemplo a seguir mostram como definir os elementos filho de um <xref:System.Windows.Controls.TreeViewItem> definindo <xref:System.Windows.Controls.ItemsControl.Items%2A> que são <xref:System.Windows.Controls.Button> controles.  
  
 [!code-xaml[TreeViewSimple#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TreeViewSimple/CS/Window1.xaml#3)]  
  
 O exemplo a seguir mostra como criar um <xref:System.Windows.Controls.TreeView> onde um <xref:System.Windows.Data.XmlDataProvider> fornece <xref:System.Windows.Controls.TreeViewItem> conteúdo e um <xref:System.Windows.HierarchicalDataTemplate> define a aparência do conteúdo.  
  
 [!code-xaml[TreeViewSimple#6](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TreeViewSimple/CS/Window1.xaml#6)]  
  
 [!code-xaml[TreeViewSimple#7](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TreeViewSimple/CS/Window1.xaml#7)]  
  
 [!code-xaml[TreeViewSimple#5](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TreeViewSimple/CS/Window1.xaml#5)]  
  
 O exemplo a seguir mostra como criar um <xref:System.Windows.Controls.TreeView> onde o <xref:System.Windows.Controls.TreeViewItem> contém conteúdo <xref:System.Windows.Controls.DockPanel> controles que têm conteúdo embutido.  
  
 [!code-xaml[TreeViewSimple#9](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TreeViewSimple/CS/Window1.xaml#9)]  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Windows.Controls.TreeView>  
 <xref:System.Windows.Controls.TreeViewItem>  
 [Visão geral de TreeView](../../../../docs/framework/wpf/controls/treeview-overview.md)  
 [Tópicos de instruções](../../../../docs/framework/wpf/controls/treeview-how-to-topics.md)
