---
title: "Como criar um modo de exibição personalizado para um ListView"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ListView controls [WPF], creating custom View mode
ms.assetid: 71077349-eeb9-4344-ab29-b5df96df3314
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: e67777b5568214dff889088708db166efc6ae4dd
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-create-a-custom-view-mode-for-a-listview"></a>Como criar um modo de exibição personalizado para um ListView
Este exemplo mostra como criar um personalizado <xref:System.Windows.Controls.ListView.View%2A> modo para um <xref:System.Windows.Controls.ListView> controle.  
  
## <a name="example"></a>Exemplo  
 Você deve usar o <xref:System.Windows.Controls.ViewBase> classe quando você criar uma exibição personalizada para o <xref:System.Windows.Controls.ListView> controle. O exemplo a seguir mostra um modo de exibição que é chamado `PlainView`, que é derivado de <xref:System.Windows.Controls.ViewBase> classe.  
  
 [!code-csharp[ListViewCustomView#PlainView](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewCustomView/CSharp/PlainView.cs#plainview)]
 [!code-vb[ListViewCustomView#PlainView](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ListViewCustomView/visualbasic/plainview.vb#plainview)]  
  
 Para aplicar um estilo para o modo de exibição personalizado, use o <xref:System.Windows.Style> classe. O exemplo a seguir define uma <xref:System.Windows.Style> para o `PlainView` modo de exibição. No exemplo anterior, esse estilo é definido como o valor de <xref:System.Windows.Controls.ViewBase.DefaultStyleKey%2A> propriedade que é definida para `PlainView`.  
  
 [!code-xaml[ListViewCustomView#PlainViewStyle](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewCustomView/CSharp/Themes/Generic.xaml#plainviewstyle)]  
  
 Para definir o layout dos dados em um modo de exibição personalizado, defina um <xref:System.Windows.DataTemplate> objeto. O exemplo a seguir define uma <xref:System.Windows.DataTemplate> que pode ser usado para exibir dados de `PlainView` o modo de exibição.  
  
 [!code-xaml[ListViewCustomView#PlainViewDataTemplate](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewCustomView/CSharp/Window1.xaml#plainviewdatatemplate)]  
  
 O exemplo a seguir mostra como definir um <xref:System.Windows.ResourceKey> para o `PlainView` modo de exibição que usa o <xref:System.Windows.DataTemplate> que é definida no exemplo anterior.  
  
 [!code-xaml[ListViewCustomView#PlainViewtileView](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewCustomView/CSharp/Window1.xaml#plainviewtileview)]  
  
 Um <xref:System.Windows.Controls.ListView> controle pode usar um modo de exibição personalizado se você definir o <xref:System.Windows.Controls.ListView.View%2A> propriedade para a chave de recurso. O exemplo a seguir mostra como especificar `PlainView` como o modo de exibição para um <xref:System.Windows.Controls.ListView>.  
  
 [!code-csharp[ListViewCustomView#ListViewtileViewmode](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewCustomView/CSharp/Window1.xaml.cs#listviewtileviewmode)]
 [!code-vb[ListViewCustomView#ListViewtileViewmode](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ListViewCustomView/visualbasic/window1.xaml.vb#listviewtileviewmode)]  
  
 Para obter um exemplo completo, consulte [ListView com várias exibições de exemplo](http://go.microsoft.com/fwlink/?LinkID=160013).  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Windows.Controls.ListView>  
 <xref:System.Windows.Controls.GridView>  
 [Tópicos de instruções](../../../../docs/framework/wpf/controls/listview-how-to-topics.md)  
 [Visão geral de ListView](../../../../docs/framework/wpf/controls/listview-overview.md)  
 [Visão geral de GridView](../../../../docs/framework/wpf/controls/gridview-overview.md)
