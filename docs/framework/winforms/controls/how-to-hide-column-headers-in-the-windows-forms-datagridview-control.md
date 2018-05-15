---
title: Como ocultar cabeçalhos no controle DataGridView dos Windows Forms
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- columns [Windows Forms], hiding column headers
- column headers [Windows Forms], hiding
- DataGridView control [Windows Forms], column headers
ms.assetid: e4ad5f68-50d2-4b9e-93ee-9d622423a8ab
ms.openlocfilehash: ff9c32725384219e4ffc98f3a76fcff9f6cfc221
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-hide-column-headers-in-the-windows-forms-datagridview-control"></a><span data-ttu-id="afbef-102">Como ocultar cabeçalhos no controle DataGridView dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="afbef-102">How to: Hide Column Headers in the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="afbef-103">Às vezes você deseja exibir um <xref:System.Windows.Forms.DataGridView> sem cabeçalhos de coluna.</span><span class="sxs-lookup"><span data-stu-id="afbef-103">Sometimes you will want to display a <xref:System.Windows.Forms.DataGridView> without column headers.</span></span> <span data-ttu-id="afbef-104">No <xref:System.Windows.Forms.DataGridView> controle, o <xref:System.Windows.Forms.DataGridView.ColumnHeadersVisible%2A> o valor da propriedade determina se os cabeçalhos de coluna são exibidos.</span><span class="sxs-lookup"><span data-stu-id="afbef-104">In the <xref:System.Windows.Forms.DataGridView> control, the <xref:System.Windows.Forms.DataGridView.ColumnHeadersVisible%2A> property value determines whether the column headers are displayed.</span></span>  
  
### <a name="to-hide-the-column-headers"></a><span data-ttu-id="afbef-105">Para ocultar os cabeçalhos de coluna</span><span class="sxs-lookup"><span data-stu-id="afbef-105">To hide the column headers</span></span>  
  
-   <span data-ttu-id="afbef-106">Defina a propriedade <xref:System.Windows.Forms.DataGridView.ColumnHeadersVisible%2A?displayProperty=nameWithType> como `false`.</span><span class="sxs-lookup"><span data-stu-id="afbef-106">Set the <xref:System.Windows.Forms.DataGridView.ColumnHeadersVisible%2A?displayProperty=nameWithType> property to `false`.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#062](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#062)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#062](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#062)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="afbef-107">Compilando o código</span><span class="sxs-lookup"><span data-stu-id="afbef-107">Compiling the Code</span></span>  
 <span data-ttu-id="afbef-108">Este exemplo requer:</span><span class="sxs-lookup"><span data-stu-id="afbef-108">This example requires:</span></span>  
  
-   <span data-ttu-id="afbef-109">Um controle <xref:System.Windows.Forms.DataGridView> chamado `dataGridView1`.</span><span class="sxs-lookup"><span data-stu-id="afbef-109">A <xref:System.Windows.Forms.DataGridView> control named `dataGridView1`.</span></span>  
  
-   <span data-ttu-id="afbef-110">Referências aos assemblies <xref:System?displayProperty=nameWithType> e <xref:System.Windows.Forms?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="afbef-110">References to the <xref:System?displayProperty=nameWithType> and <xref:System.Windows.Forms?displayProperty=nameWithType> assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="afbef-111">Consulte também</span><span class="sxs-lookup"><span data-stu-id="afbef-111">See Also</span></span>  
 <xref:System.Windows.Forms.DataGridView>  
 <xref:System.Windows.Forms.DataGridView.ColumnHeadersVisible%2A?displayProperty=nameWithType>  
 [<span data-ttu-id="afbef-112">Funcionalidades de coluna, linha e célula básicas no controle DataGridView do Windows Forms</span><span class="sxs-lookup"><span data-stu-id="afbef-112">Basic Column, Row, and Cell Features in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/basic-column-row-and-cell-features-wf-datagridview-control.md)
