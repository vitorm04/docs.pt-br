---
title: 'Como: Tornar colunas somente leitura no controle DataGridView do Windows Forms'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data grids [Windows Forms], read-only columns
- DataGridView control [Windows Forms], read-only columns
ms.assetid: 2bb73ebb-1a55-4362-9fda-e50574c087d5
ms.openlocfilehash: 2a4ca0a718373c56f77e8f3c45a9d6ee6d76a081
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59171919"
---
# <a name="how-to-make-columns-read-only-in-the-windows-forms-datagridview-control"></a><span data-ttu-id="a049c-102">Como: Tornar colunas somente leitura no controle DataGridView do Windows Forms</span><span class="sxs-lookup"><span data-stu-id="a049c-102">How to: Make Columns Read-Only in the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="a049c-103">Nem todos os dados destina-se para edição.</span><span class="sxs-lookup"><span data-stu-id="a049c-103">Not all data is meant for editing.</span></span> <span data-ttu-id="a049c-104">No <xref:System.Windows.Forms.DataGridView> controlar, a coluna <xref:System.Windows.Forms.DataGridViewColumn.ReadOnly%2A> valor da propriedade determina se os usuários podem editar as células na coluna.</span><span class="sxs-lookup"><span data-stu-id="a049c-104">In the <xref:System.Windows.Forms.DataGridView> control, the column <xref:System.Windows.Forms.DataGridViewColumn.ReadOnly%2A> property value determines whether users can edit cells in that column.</span></span> <span data-ttu-id="a049c-105">Para obter informações sobre como fazer o controle totalmente somente leitura, consulte [como: Evitar a adição de linha e exclusão no Windows Forms DataGridView Control](prevent-row-addition-and-deletion-datagridview.md).</span><span class="sxs-lookup"><span data-stu-id="a049c-105">For information about how to make the control entirely read-only, see [How to: Prevent Row Addition and Deletion in the Windows Forms DataGridView Control](prevent-row-addition-and-deletion-datagridview.md).</span></span>  
  
 <span data-ttu-id="a049c-106">Há suporte para esta tarefa no Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="a049c-106">There is support for this task in Visual Studio.</span></span>  <span data-ttu-id="a049c-107">Consulte também [como: Tornar as colunas somente leitura no Windows Forms usando o Designer de controle de DataGridView](make-columns-read-only-in-the-datagrid-using-the-designer.md).</span><span class="sxs-lookup"><span data-stu-id="a049c-107">Also see [How to: Make Columns Read-Only in the Windows Forms DataGridView Control Using the Designer](make-columns-read-only-in-the-datagrid-using-the-designer.md).</span></span>  
  
### <a name="to-make-a-column-read-only-programmatically"></a><span data-ttu-id="a049c-108">Para tornar a coluna somente leitura por meio de programação</span><span class="sxs-lookup"><span data-stu-id="a049c-108">To make a column read-only programmatically</span></span>  
  
-   <span data-ttu-id="a049c-109">Defina a propriedade <xref:System.Windows.Forms.DataGridViewColumn.ReadOnly%2A?displayProperty=nameWithType> como `true`.</span><span class="sxs-lookup"><span data-stu-id="a049c-109">Set the <xref:System.Windows.Forms.DataGridViewColumn.ReadOnly%2A?displayProperty=nameWithType> property to `true`.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#064](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#064)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#064](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#064)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="a049c-110">Compilando o código</span><span class="sxs-lookup"><span data-stu-id="a049c-110">Compiling the Code</span></span>  
 <span data-ttu-id="a049c-111">Este exemplo requer:</span><span class="sxs-lookup"><span data-stu-id="a049c-111">This example requires:</span></span>  
  
-   <span data-ttu-id="a049c-112">Um <xref:System.Windows.Forms.DataGridView> controle chamado `dataGridView1` com uma coluna chamada `CompanyName`.</span><span class="sxs-lookup"><span data-stu-id="a049c-112">A <xref:System.Windows.Forms.DataGridView> control named `dataGridView1` with a column named `CompanyName`.</span></span>  
  
-   <span data-ttu-id="a049c-113">Referências aos assemblies <xref:System?displayProperty=nameWithType> e <xref:System.Windows.Forms?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="a049c-113">References to the <xref:System?displayProperty=nameWithType> and <xref:System.Windows.Forms?displayProperty=nameWithType> assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a049c-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a049c-114">See also</span></span>

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridView.Columns%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridViewColumn.ReadOnly%2A?displayProperty=nameWithType>
- [<span data-ttu-id="a049c-115">Funcionalidades de coluna, linha e célula básicas no controle DataGridView dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="a049c-115">Basic Column, Row, and Cell Features in the Windows Forms DataGridView Control</span></span>](basic-column-row-and-cell-features-wf-datagridview-control.md)
- [<span data-ttu-id="a049c-116">Como: Evitar a adição e a exclusão de linha no controle DataGridView do Windows Forms</span><span class="sxs-lookup"><span data-stu-id="a049c-116">How to: Prevent Row Addition and Deletion in the Windows Forms DataGridView Control</span></span>](prevent-row-addition-and-deletion-datagridview.md)
