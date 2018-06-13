---
title: Como exibir dados usando GridViewRowPresenter
ms.date: 03/30/2017
helpviewer_keywords:
- displaying data with GridViewRowPresenter [WPF]
- GridViewRowPresenter [WPF]
ms.assetid: bdb785a5-a262-44d5-a517-ea14383e5f70
ms.openlocfilehash: f68bc3a4ffff268138721a6750a0eb50c825377e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33550784"
---
# <a name="how-to-display-data-by-using-gridviewrowpresenter"></a>Como exibir dados usando GridViewRowPresenter
Este exemplo mostra como usar o <xref:System.Windows.Controls.GridViewRowPresenter> e <xref:System.Windows.Controls.GridViewHeaderRowPresenter> objetos para exibir dados em colunas.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra como especificar um <xref:System.Windows.Controls.GridViewColumnCollection> que exibe o <xref:System.DateTime.DayOfWeek%2A> e <xref:System.DateTime.Year%2A> de um <xref:System.DateTime> objeto usando <xref:System.Windows.Controls.GridViewRowPresenter> e <xref:System.Windows.Controls.GridViewHeaderRowPresenter> objetos. O exemplo também define um <xref:System.Windows.Style> para o <xref:System.Windows.Controls.GridViewColumn.Header%2A> de um <xref:System.Windows.Controls.GridViewColumn>.  
  
 [!code-xaml[GridViewRowPresenterSample#GridViewRowPresenter](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GridViewRowPresenterSample/CS/Window1.xaml#gridviewrowpresenter)]  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Windows.Controls.GridViewHeaderRowPresenter>  
 <xref:System.Windows.Controls.GridViewRowPresenter>  
 <xref:System.Windows.Controls.GridViewColumnCollection>  
 [Visão geral de GridView](../../../../docs/framework/wpf/controls/gridview-overview.md)
