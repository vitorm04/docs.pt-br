---
title: 'Como: Exibir conteúdo de ListView usando um GridView'
ms.date: 03/30/2017
helpviewer_keywords:
- ListView controls [WPF], displaying contents with GridView
- GridView [WPF], displaying ListView contents
ms.assetid: 5bc1e767-ab46-4f14-bd41-3d5d39e1d000
ms.openlocfilehash: 9a4bcc8b613637521ee91a11b0bdac8f77f90a03
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57354395"
---
# <a name="how-to-display-listview-contents-by-using-a-gridview"></a>Como: Exibir conteúdo de ListView usando um GridView
Este exemplo mostra como definir um <xref:System.Windows.Controls.GridView> modo de exibição para um <xref:System.Windows.Controls.ListView> controle.  
  
## <a name="example"></a>Exemplo  
 Você pode definir o modo de exibição de um <xref:System.Windows.Controls.GridView> especificando <xref:System.Windows.Controls.GridViewColumn> objetos. O exemplo a seguir mostra como definir <xref:System.Windows.Controls.GridViewColumn> objetos que ligam para o conteúdo de dados que é especificado para o <xref:System.Windows.Controls.ListView> controle. Isso <xref:System.Windows.Controls.GridView> exemplo especifica três <xref:System.Windows.Controls.GridViewColumn> objetos que são mapeados para o `FirstName`, `LastName`, e `EmployeeNumber` campos do `EmployeeInfoDataSource` que é definido como o <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> do <xref:System.Windows.Controls.ListView> controle.  
  
 [!code-xaml[ListViewCode#ListViewEmployee](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewCode/CSharp/Window1.xaml#listviewemployee)]  
  
 A ilustração a seguir mostra como esse exemplo é exibido.  
  
 ![ListView com saída de GridView](./media/listviewgridview.JPG "ListViewGridView")  
  
## <a name="see-also"></a>Consulte também
- <xref:System.Windows.Controls.ListView>
- <xref:System.Windows.Controls.GridView>
- [Visão geral de ListView](listview-overview.md)
- [Visão geral de GridView](gridview-overview.md)
- [Tópicos de instruções](listview-how-to-topics.md)
