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
# <a name="how-to-display-data-by-using-gridviewrowpresenter"></a><span data-ttu-id="c4b61-102">Como exibir dados usando GridViewRowPresenter</span><span class="sxs-lookup"><span data-stu-id="c4b61-102">How to: Display Data by Using GridViewRowPresenter</span></span>
<span data-ttu-id="c4b61-103">Este exemplo mostra como usar o <xref:System.Windows.Controls.GridViewRowPresenter> e <xref:System.Windows.Controls.GridViewHeaderRowPresenter> objetos para exibir dados em colunas.</span><span class="sxs-lookup"><span data-stu-id="c4b61-103">This example shows how to use the <xref:System.Windows.Controls.GridViewRowPresenter> and <xref:System.Windows.Controls.GridViewHeaderRowPresenter> objects to display data in columns.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c4b61-104">Exemplo</span><span class="sxs-lookup"><span data-stu-id="c4b61-104">Example</span></span>  
 <span data-ttu-id="c4b61-105">O exemplo a seguir mostra como especificar um <xref:System.Windows.Controls.GridViewColumnCollection> que exibe o <xref:System.DateTime.DayOfWeek%2A> e <xref:System.DateTime.Year%2A> de um <xref:System.DateTime> objeto usando <xref:System.Windows.Controls.GridViewRowPresenter> e <xref:System.Windows.Controls.GridViewHeaderRowPresenter> objetos.</span><span class="sxs-lookup"><span data-stu-id="c4b61-105">The following example shows how to specify a <xref:System.Windows.Controls.GridViewColumnCollection> that displays the <xref:System.DateTime.DayOfWeek%2A> and <xref:System.DateTime.Year%2A> of a <xref:System.DateTime> object by using <xref:System.Windows.Controls.GridViewRowPresenter> and <xref:System.Windows.Controls.GridViewHeaderRowPresenter> objects.</span></span> <span data-ttu-id="c4b61-106">O exemplo também define um <xref:System.Windows.Style> para o <xref:System.Windows.Controls.GridViewColumn.Header%2A> de um <xref:System.Windows.Controls.GridViewColumn>.</span><span class="sxs-lookup"><span data-stu-id="c4b61-106">The example also defines a <xref:System.Windows.Style> for the <xref:System.Windows.Controls.GridViewColumn.Header%2A> of a <xref:System.Windows.Controls.GridViewColumn>.</span></span>  
  
 [!code-xaml[GridViewRowPresenterSample#GridViewRowPresenter](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GridViewRowPresenterSample/CS/Window1.xaml#gridviewrowpresenter)]  
  
## <a name="see-also"></a><span data-ttu-id="c4b61-107">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c4b61-107">See Also</span></span>  
 <xref:System.Windows.Controls.GridViewHeaderRowPresenter>  
 <xref:System.Windows.Controls.GridViewRowPresenter>  
 <xref:System.Windows.Controls.GridViewColumnCollection>  
 [<span data-ttu-id="c4b61-108">Visão geral de GridView</span><span class="sxs-lookup"><span data-stu-id="c4b61-108">GridView Overview</span></span>](../../../../docs/framework/wpf/controls/gridview-overview.md)
