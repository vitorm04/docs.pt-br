---
title: "Como personalizar a aparência de células no controle DataGridView dos Windows Forms"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data grids [Windows Forms], customizing cells
- DataGridView control [Windows Forms], customizing cells
- cells [Windows Forms], customizing in DataGridView control
ms.assetid: 478b20c9-625c-4116-9c5c-5a16e6f4ec67
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 61b2a39943dfca412afa4b66265aabbf65b9ccf0
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-customize-the-appearance-of-cells-in-the-windows-forms-datagridview-control"></a><span data-ttu-id="94078-102">Como personalizar a aparência de células no controle DataGridView dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="94078-102">How to: Customize the Appearance of Cells in the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="94078-103">Você pode personalizar a aparência de qualquer célula manipulando o <xref:System.Windows.Forms.DataGridView> do controle <xref:System.Windows.Forms.DataGridView.CellPainting> eventos.</span><span class="sxs-lookup"><span data-stu-id="94078-103">You can customize the appearance of any cell by handling the <xref:System.Windows.Forms.DataGridView> control's <xref:System.Windows.Forms.DataGridView.CellPainting> event.</span></span> <span data-ttu-id="94078-104">Você pode extrair o <xref:System.Windows.Forms.DataGridView> do controle <xref:System.Drawing.Graphics> do <xref:System.Windows.Forms.DataGridViewCellPaintingEventArgs.Graphics%2A> propriedade o <xref:System.Windows.Forms.DataGridViewCellPaintingEventArgs>.</span><span class="sxs-lookup"><span data-stu-id="94078-104">You can extract the <xref:System.Windows.Forms.DataGridView> control's <xref:System.Drawing.Graphics> from the <xref:System.Windows.Forms.DataGridViewCellPaintingEventArgs.Graphics%2A> property of the <xref:System.Windows.Forms.DataGridViewCellPaintingEventArgs>.</span></span> <span data-ttu-id="94078-105">Com isso <xref:System.Drawing.Graphics>, você pode afetar a aparência de todo o <xref:System.Windows.Forms.DataGridView> controle, mas você geralmente desejará afetam apenas a aparência da célula que está atualmente sendo pintada.</span><span class="sxs-lookup"><span data-stu-id="94078-105">With this <xref:System.Drawing.Graphics>, you can affect the appearance of the entire <xref:System.Windows.Forms.DataGridView> control, but you will usually want to affect only the appearance of the cell that is currently being painted.</span></span> <span data-ttu-id="94078-106">O <xref:System.Windows.Forms.DataGridViewCellPaintingEventArgs.ClipBounds%2A> propriedade o <xref:System.Windows.Forms.DataGridViewCellPaintingEventArgs> permite restringir as operações de pintura para a célula que está atualmente sendo pintado.</span><span class="sxs-lookup"><span data-stu-id="94078-106">The <xref:System.Windows.Forms.DataGridViewCellPaintingEventArgs.ClipBounds%2A> property of the <xref:System.Windows.Forms.DataGridViewCellPaintingEventArgs> enables you to restrict your painting operations to the cell that is currently being painted.</span></span>  
  
 <span data-ttu-id="94078-107">No exemplo de código a seguir, você pintará todas as células de uma `ContactName` coluna usando o <xref:System.Windows.Forms.DataGridView> esquema de cores do controle.</span><span class="sxs-lookup"><span data-stu-id="94078-107">In the following code example, you will paint all the cells in a `ContactName` column using the <xref:System.Windows.Forms.DataGridView> control's color scheme.</span></span> <span data-ttu-id="94078-108">Conteúdo de texto de cada célula é pintado em <xref:System.Drawing.Color.Crimson%2A>, e um retângulo de inserção é desenhado na mesma cor como o <xref:System.Windows.Forms.DataGridView> do controle <xref:System.Windows.Forms.DataGridView.GridColor%2A> propriedade.</span><span class="sxs-lookup"><span data-stu-id="94078-108">Each cell's text content is painted in <xref:System.Drawing.Color.Crimson%2A>, and an inset rectangle is drawn in the same color as the <xref:System.Windows.Forms.DataGridView> control's <xref:System.Windows.Forms.DataGridView.GridColor%2A> property.</span></span>  
  
## <a name="example"></a><span data-ttu-id="94078-109">Exemplo</span><span class="sxs-lookup"><span data-stu-id="94078-109">Example</span></span>  
 [!code-csharp[System.Windows.Forms.DataGridViewCellPainting#10](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewCellPainting/CS/form1.cs#10)]
 [!code-vb[System.Windows.Forms.DataGridViewCellPainting#10](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewCellPainting/VB/form1.vb#10)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="94078-110">Compilando o código</span><span class="sxs-lookup"><span data-stu-id="94078-110">Compiling the Code</span></span>  
 <span data-ttu-id="94078-111">Este exemplo requer:</span><span class="sxs-lookup"><span data-stu-id="94078-111">This example requires:</span></span>  
  
-   <span data-ttu-id="94078-112">Um <xref:System.Windows.Forms.DataGridView> controle chamado `dataGridView1` com um `ContactName` coluna, como mostrado na tabela Customers no banco de dados de exemplo Northwind.</span><span class="sxs-lookup"><span data-stu-id="94078-112">A <xref:System.Windows.Forms.DataGridView> control named `dataGridView1` with a `ContactName` column such as the one in the Customers table in the Northwind sample database.</span></span>  
  
-   <span data-ttu-id="94078-113">Referências aos assemblies System, System.Windows.Forms e System.Drawing.</span><span class="sxs-lookup"><span data-stu-id="94078-113">References to the System, System.Windows.Forms, and System.Drawing assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="94078-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="94078-114">See Also</span></span>  
 <xref:System.Windows.Forms.DataGridView>  
 <xref:System.Windows.Forms.DataGridView.CellPainting>  
 [<span data-ttu-id="94078-115">Personalizando o controle DataGridView dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="94078-115">Customizing the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/customizing-the-windows-forms-datagridview-control.md)
