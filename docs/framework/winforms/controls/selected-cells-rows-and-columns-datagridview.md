---
title: Como obter as células, as linhas e as colunas selecionadas no controle DataGridView dos Windows Forms
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- selection [Windows Forms], DataGridView control [Windows Forms]
- DataGridView control [Windows Forms], getting selection
- getting selection [Windows Forms], DataGridView control [Windows Forms]
ms.assetid: d93c4b5b-498e-49bc-982a-2229d61778e4
ms.openlocfilehash: a1d2338250abbced89ef7821d02edc654d26d7fa
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33539100"
---
# <a name="how-to-get-the-selected-cells-rows-and-columns-in-the-windows-forms-datagridview-control"></a><span data-ttu-id="9cab1-102">Como obter as células, as linhas e as colunas selecionadas no controle DataGridView dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="9cab1-102">How to: Get the Selected Cells, Rows, and Columns in the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="9cab1-103">Você pode obter as células selecionadas, linhas ou colunas de uma <xref:System.Windows.Forms.DataGridView> controle usando as propriedades correspondentes: <xref:System.Windows.Forms.DataGridView.SelectedCells%2A>, <xref:System.Windows.Forms.DataGridView.SelectedRows%2A>, e <xref:System.Windows.Forms.DataGridView.SelectedColumns%2A>.</span><span class="sxs-lookup"><span data-stu-id="9cab1-103">You can get the selected cells, rows, or columns from a <xref:System.Windows.Forms.DataGridView> control by using the corresponding properties: <xref:System.Windows.Forms.DataGridView.SelectedCells%2A>, <xref:System.Windows.Forms.DataGridView.SelectedRows%2A>, and <xref:System.Windows.Forms.DataGridView.SelectedColumns%2A>.</span></span> <span data-ttu-id="9cab1-104">Nos procedimentos a seguir, você obterá as células selecionadas e exibir seus índices de linha e coluna em uma <xref:System.Windows.Forms.MessageBox>.</span><span class="sxs-lookup"><span data-stu-id="9cab1-104">In the following procedures, you will get the selected cells and display their row and column indexes in a <xref:System.Windows.Forms.MessageBox>.</span></span>  
  
### <a name="to-get-the-selected-cells-in-a-datagridview-control"></a><span data-ttu-id="9cab1-105">Para obter as células selecionadas em um controle DataGridView</span><span class="sxs-lookup"><span data-stu-id="9cab1-105">To get the selected cells in a DataGridView control</span></span>  
  
-   <span data-ttu-id="9cab1-106">Use a propriedade <xref:System.Windows.Forms.DataGridView.SelectedCells%2A>.</span><span class="sxs-lookup"><span data-stu-id="9cab1-106">Use the <xref:System.Windows.Forms.DataGridView.SelectedCells%2A> property.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="9cab1-107">Use o <xref:System.Windows.Forms.DataGridView.AreAllCellsSelected%2A> método para evitar mostrando um número potencialmente grande de células.</span><span class="sxs-lookup"><span data-stu-id="9cab1-107">Use the <xref:System.Windows.Forms.DataGridView.AreAllCellsSelected%2A> method to avoid showing a potentially large number of cells.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridViewSelectedCollections#10](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSelectedCollections/CS/DataGridViewSelectedCollections.cs#10)]
     [!code-vb[System.Windows.Forms.DataGridViewSelectedCollections#10](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSelectedCollections/VB/DataGridViewSelectedCollections.vb#10)]  
  
### <a name="to-get-the-selected-rows-in-a-datagridview-control"></a><span data-ttu-id="9cab1-108">Para obter as linhas selecionadas em um controle DataGridView</span><span class="sxs-lookup"><span data-stu-id="9cab1-108">To get the selected rows in a DataGridView control</span></span>  
  
-   <span data-ttu-id="9cab1-109">Use a propriedade <xref:System.Windows.Forms.DataGridView.SelectedRows%2A>.</span><span class="sxs-lookup"><span data-stu-id="9cab1-109">Use the <xref:System.Windows.Forms.DataGridView.SelectedRows%2A> property.</span></span> <span data-ttu-id="9cab1-110">Para habilitar usuários selecionar linhas, você deve definir o <xref:System.Windows.Forms.DataGridView.SelectionMode%2A> propriedade <xref:System.Windows.Forms.DataGridViewSelectionMode.FullRowSelect> ou <xref:System.Windows.Forms.DataGridViewSelectionMode.RowHeaderSelect>.</span><span class="sxs-lookup"><span data-stu-id="9cab1-110">To enable users to select rows, you must set the <xref:System.Windows.Forms.DataGridView.SelectionMode%2A> property to <xref:System.Windows.Forms.DataGridViewSelectionMode.FullRowSelect> or <xref:System.Windows.Forms.DataGridViewSelectionMode.RowHeaderSelect>.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridViewSelectedCollections#20](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSelectedCollections/CS/DataGridViewSelectedCollections.cs#20)]
     [!code-vb[System.Windows.Forms.DataGridViewSelectedCollections#20](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSelectedCollections/VB/DataGridViewSelectedCollections.vb#20)]  
  
### <a name="to-get-the-selected-columns-in-a-datagridview-control"></a><span data-ttu-id="9cab1-111">Para obter as colunas selecionadas em um controle DataGridView</span><span class="sxs-lookup"><span data-stu-id="9cab1-111">To get the selected columns in a DataGridView control</span></span>  
  
-   <span data-ttu-id="9cab1-112">Use a propriedade <xref:System.Windows.Forms.DataGridView.SelectedColumns%2A>.</span><span class="sxs-lookup"><span data-stu-id="9cab1-112">Use the <xref:System.Windows.Forms.DataGridView.SelectedColumns%2A> property.</span></span> <span data-ttu-id="9cab1-113">Para permitir aos usuários selecionar colunas, você deve definir o <xref:System.Windows.Forms.DataGridView.SelectionMode%2A> propriedade <xref:System.Windows.Forms.DataGridViewSelectionMode.FullColumnSelect> ou <xref:System.Windows.Forms.DataGridViewSelectionMode.ColumnHeaderSelect>.</span><span class="sxs-lookup"><span data-stu-id="9cab1-113">To enable users to select columns, you must set the <xref:System.Windows.Forms.DataGridView.SelectionMode%2A> property to <xref:System.Windows.Forms.DataGridViewSelectionMode.FullColumnSelect> or <xref:System.Windows.Forms.DataGridViewSelectionMode.ColumnHeaderSelect>.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridViewSelectedCollections#30](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSelectedCollections/CS/DataGridViewSelectedCollections.cs#30)]
     [!code-vb[System.Windows.Forms.DataGridViewSelectedCollections#30](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSelectedCollections/VB/DataGridViewSelectedCollections.vb#30)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="9cab1-114">Compilando o código</span><span class="sxs-lookup"><span data-stu-id="9cab1-114">Compiling the Code</span></span>  
 <span data-ttu-id="9cab1-115">Este exemplo requer:</span><span class="sxs-lookup"><span data-stu-id="9cab1-115">This example requires:</span></span>  
  
-   <span data-ttu-id="9cab1-116"><xref:System.Windows.Forms.Button> controles denominados `selectedCellsButton`, `selectedRowsButton`, e `selectedColumnsButton`, cada um com manipuladores para o <xref:System.Windows.Forms.Control.Click> evento anexado.</span><span class="sxs-lookup"><span data-stu-id="9cab1-116"><xref:System.Windows.Forms.Button> controls named `selectedCellsButton`, `selectedRowsButton`, and `selectedColumnsButton`, each with handlers for the <xref:System.Windows.Forms.Control.Click> event attached.</span></span>  
  
-   <span data-ttu-id="9cab1-117">Um controle <xref:System.Windows.Forms.DataGridView> chamado `dataGridView1`.</span><span class="sxs-lookup"><span data-stu-id="9cab1-117">A <xref:System.Windows.Forms.DataGridView> control named `dataGridView1`.</span></span>  
  
-   <span data-ttu-id="9cab1-118">Referências a <xref:System?displayProperty=nameWithType>, <xref:System.Windows.Forms?displayProperty=nameWithType>, e <xref:System.Text?displayProperty=nameWithType> assemblies.</span><span class="sxs-lookup"><span data-stu-id="9cab1-118">References to the <xref:System?displayProperty=nameWithType>, <xref:System.Windows.Forms?displayProperty=nameWithType>, and <xref:System.Text?displayProperty=nameWithType> assemblies.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="9cab1-119">Programação robusta</span><span class="sxs-lookup"><span data-stu-id="9cab1-119">Robust Programming</span></span>  
 <span data-ttu-id="9cab1-120">As coleções descritas neste tópico não são executadas com eficiência quando uma grande quantidade de células, linhas ou colunas for selecionada.</span><span class="sxs-lookup"><span data-stu-id="9cab1-120">The collections described in this topic do not perform efficiently when large numbers of cells, rows, or columns are selected.</span></span> <span data-ttu-id="9cab1-121">Para obter mais informações sobre como usar essas coleções com grandes quantidades de dados, consulte [Práticas recomendadas para dimensionamento do controle DataGridView dos Windows Forms](../../../../docs/framework/winforms/controls/best-practices-for-scaling-the-windows-forms-datagridview-control.md).</span><span class="sxs-lookup"><span data-stu-id="9cab1-121">For more information about using these collections with large amounts of data, see [Best Practices for Scaling the Windows Forms DataGridView Control](../../../../docs/framework/winforms/controls/best-practices-for-scaling-the-windows-forms-datagridview-control.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9cab1-122">Consulte também</span><span class="sxs-lookup"><span data-stu-id="9cab1-122">See Also</span></span>  
 <xref:System.Windows.Forms.DataGridView>  
 <xref:System.Windows.Forms.DataGridView.SelectionMode%2A>  
 <xref:System.Windows.Forms.DataGridView.AreAllCellsSelected%2A>  
 <xref:System.Windows.Forms.DataGridView.SelectedCells%2A>  
 <xref:System.Windows.Forms.DataGridView.SelectedRows%2A>  
 <xref:System.Windows.Forms.DataGridView.SelectedColumns%2A>  
 [<span data-ttu-id="9cab1-123">Seleção e uso da Área de Transferência com o controle DataGridView do Windows Forms</span><span class="sxs-lookup"><span data-stu-id="9cab1-123">Selection and Clipboard Use with the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/selection-and-clipboard-use-with-the-windows-forms-datagridview-control.md)
