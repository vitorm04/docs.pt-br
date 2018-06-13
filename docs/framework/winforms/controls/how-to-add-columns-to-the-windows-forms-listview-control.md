---
title: Como adicionar colunas ao controle ListView dos Windows Forms
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ListView control [Windows Forms], adding column headers
- columns [Windows Forms], adding to ListView controls
- list views [Windows Forms], adding columns
ms.assetid: 79174274-12ee-4a5d-80db-6ec02976d010
ms.openlocfilehash: 4c284e9d2798a1992e3152a85eca47c8d33bfde8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33528265"
---
# <a name="how-to-add-columns-to-the-windows-forms-listview-control"></a><span data-ttu-id="9dca9-102">Como adicionar colunas ao controle ListView dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="9dca9-102">How to: Add Columns to the Windows Forms ListView Control</span></span>
<span data-ttu-id="9dca9-103">Na exibição de detalhes, o <xref:System.Windows.Forms.ListView> controle pode exibir várias colunas para cada item de lista.</span><span class="sxs-lookup"><span data-stu-id="9dca9-103">In the Details view, the <xref:System.Windows.Forms.ListView> control can display multiple columns for each list item.</span></span> <span data-ttu-id="9dca9-104">Você pode usar as colunas para exibição ao usuário vários tipos de informações sobre cada item da lista.</span><span class="sxs-lookup"><span data-stu-id="9dca9-104">You can use the columns to display to the user several types of information about each list item.</span></span> <span data-ttu-id="9dca9-105">Por exemplo, uma lista de arquivos pode exibir o nome do arquivo, tipo de arquivo, tamanho e data da última modificação do arquivo.</span><span class="sxs-lookup"><span data-stu-id="9dca9-105">For example, a list of files could display the file name, file type, size, and date the file was last modified.</span></span> <span data-ttu-id="9dca9-106">Para obter informações sobre como preencher as colunas depois que elas são criadas, consulte [como: Exibir subitens em colunas com o controle ListView dos Windows Forms](../../../../docs/framework/winforms/controls/how-to-display-subitems-in-columns-with-the-windows-forms-listview-control.md).</span><span class="sxs-lookup"><span data-stu-id="9dca9-106">For information about populating the columns after they are created, see [How to: Display Subitems in Columns with the Windows Forms ListView Control](../../../../docs/framework/winforms/controls/how-to-display-subitems-in-columns-with-the-windows-forms-listview-control.md).</span></span>  
  
### <a name="to-add-columns-programmatically"></a><span data-ttu-id="9dca9-107">Para adicionar colunas programaticamente</span><span class="sxs-lookup"><span data-stu-id="9dca9-107">To add columns programmatically</span></span>  
  
1.  <span data-ttu-id="9dca9-108">Definir o controle <xref:System.Windows.Forms.ListView.View%2A> propriedade <xref:System.Windows.Forms.View.Details>.</span><span class="sxs-lookup"><span data-stu-id="9dca9-108">Set the control's <xref:System.Windows.Forms.ListView.View%2A> property to <xref:System.Windows.Forms.View.Details>.</span></span>  
  
2.  <span data-ttu-id="9dca9-109">Use o <xref:System.Windows.Forms.ListView.ColumnHeaderCollection.Add%2A> método de exibição de lista <xref:System.Windows.Forms.ListView.Columns%2A> propriedade.</span><span class="sxs-lookup"><span data-stu-id="9dca9-109">Use the <xref:System.Windows.Forms.ListView.ColumnHeaderCollection.Add%2A> method of the list view's <xref:System.Windows.Forms.ListView.Columns%2A> property.</span></span>  
  
     [!code-csharp[System.Windows.Forms.ListViewLegacyTopics#31](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/CS/Class1.cs#31)]
     [!code-vb[System.Windows.Forms.ListViewLegacyTopics#31](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/VB/Class1.vb#31)]  
  
## <a name="see-also"></a><span data-ttu-id="9dca9-110">Consulte também</span><span class="sxs-lookup"><span data-stu-id="9dca9-110">See Also</span></span>  
 <xref:System.Windows.Forms.ListView>  
 [<span data-ttu-id="9dca9-111">Controle ListView</span><span class="sxs-lookup"><span data-stu-id="9dca9-111">ListView Control</span></span>](../../../../docs/framework/winforms/controls/listview-control-windows-forms.md)  
 [<span data-ttu-id="9dca9-112">Visão geral do controle ListView</span><span class="sxs-lookup"><span data-stu-id="9dca9-112">ListView Control Overview</span></span>](../../../../docs/framework/winforms/controls/listview-control-overview-windows-forms.md)
