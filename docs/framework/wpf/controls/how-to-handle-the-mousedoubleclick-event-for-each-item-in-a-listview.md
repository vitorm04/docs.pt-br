---
title: Como identificar o evento MouseDoubleClick para cada item em um ListView
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords: ListView controls [WPF], MouseDoubleClick event
ms.assetid: 81b39369-655a-4585-ac58-4640e5bb8fed
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 53c40e9e3b02bdf33a073a93d28b619e399e375f
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-handle-the-mousedoubleclick-event-for-each-item-in-a-listview"></a>Como identificar o evento MouseDoubleClick para cada item em um ListView
Para manipular um evento de um item em uma <xref:System.Windows.Controls.ListView>, você precisa adicionar um manipulador de eventos para cada <xref:System.Windows.Controls.ListViewItem>. Quando um <xref:System.Windows.Controls.ListView> está associado a uma fonte de dados, você não criar explicitamente uma <xref:System.Windows.Controls.ListViewItem>, mas você pode manipular o evento para cada item, adicionando um <xref:System.Windows.EventSetter> de um estilo de um <xref:System.Windows.Controls.ListViewItem>.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir cria uma associação de dados <xref:System.Windows.Controls.ListView> e cria um <xref:System.Windows.Style> para adicionar um manipulador de eventos a cada <xref:System.Windows.Controls.ListViewItem>.  
  
 [!code-xaml[ListViewHowTos#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewHowTos/CSharp/Window1.xaml#1)]  
[!code-xaml[ListViewHowTos#5](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewHowTos/CSharp/Window1.xaml#5)]  
[!code-xaml[ListViewHowTos#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewHowTos/CSharp/Window1.xaml#2)]  
  
 A exemplo a seguir trata o <xref:System.Windows.Controls.Control.MouseDoubleClick> evento.  
  
 [!code-csharp[ListViewHowTos#6](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewHowTos/CSharp/Window1.xaml.cs#6)]
 [!code-vb[ListViewHowTos#6](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ListViewHowTos/VisualBasic/Window1.xaml.vb#6)]  
  
> [!NOTE]
>  Embora seja mais comum para associar um <xref:System.Windows.Controls.ListView> para uma fonte de dados, você pode usar um estilo para adicionar um manipulador de eventos a cada <xref:System.Windows.Controls.ListViewItem> em uma não-associados a dados <xref:System.Windows.Controls.ListView> independentemente se você criar explicitamente uma <xref:System.Windows.Controls.ListViewItem>.  Para obter mais informações sobre explícita e implicitamente criado <xref:System.Windows.Controls.ListViewItem> controles, consulte <xref:System.Windows.Controls.ItemsControl>.  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Xml.XmlElement>  
 [Visão geral da vinculação de dados](../../../../docs/framework/wpf/data/data-binding-overview.md)  
 [Estilo e modelagem](../../../../docs/framework/wpf/controls/styling-and-templating.md)  
 [Associar dados XML usando um XMLDataProvider e consultas XPath](../../../../docs/framework/wpf/data/how-to-bind-to-xml-data-using-an-xmldataprovider-and-xpath-queries.md)  
 [Visão geral de ListView](../../../../docs/framework/wpf/controls/listview-overview.md)
