---
title: "Como exibir conteúdo de ListView usando um GridView"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- ListView controls [WPF], displaying contents with GridView
- GridView [WPF], displaying ListView contents
ms.assetid: 5bc1e767-ab46-4f14-bd41-3d5d39e1d000
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: ee2885868c07b00f16290b6414e7f7bdd64fd68c
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-display-listview-contents-by-using-a-gridview"></a>Como exibir conteúdo de ListView usando um GridView
Este exemplo mostra como definir um <xref:System.Windows.Controls.GridView> modo de exibição para um <xref:System.Windows.Controls.ListView> controle.  
  
## <a name="example"></a>Exemplo  
 Você pode definir o modo de exibição de um <xref:System.Windows.Controls.GridView> especificando <xref:System.Windows.Controls.GridViewColumn> objetos. O exemplo a seguir mostra como definir <xref:System.Windows.Controls.GridViewColumn> objetos que associam ao conteúdo especificado para o <xref:System.Windows.Controls.ListView> controle. Isso <xref:System.Windows.Controls.GridView> exemplo especifica três <xref:System.Windows.Controls.GridViewColumn> objetos que são mapeados para o `FirstName`, `LastName`, e `EmployeeNumber` campos do `EmployeeInfoDataSource` que é definido como o <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> do <xref:System.Windows.Controls.ListView> controle.  
  
 [!code-xaml[ListViewCode#ListViewEmployee](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewCode/CSharp/Window1.xaml#listviewemployee)]  
  
 A ilustração a seguir mostra como esse exemplo é exibido.  
  
 ![ListView com saída de GridView](../../../../docs/framework/wpf/controls/media/listviewgridview.JPG "ListViewGridView")  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Windows.Controls.ListView>  
 <xref:System.Windows.Controls.GridView>  
 [Visão geral de ListView](../../../../docs/framework/wpf/controls/listview-overview.md)  
 [Visão geral de GridView](../../../../docs/framework/wpf/controls/gridview-overview.md)  
 [Tópicos de instruções](../../../../docs/framework/wpf/controls/listview-how-to-topics.md)
