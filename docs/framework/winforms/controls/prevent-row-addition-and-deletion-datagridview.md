---
title: Impedir adição e exclusão de linha no controle DataGridView
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DataGridView control [Windows Forms], disabling data entry
- data entry [Windows Forms], disabling in grids
- data grids [Windows Forms], disabling data entry
ms.assetid: ef9539ce-539b-404e-84b6-ac282b64b88c
ms.openlocfilehash: de8e0412faf8c3731f9356771b35a4a5d31b6ec7
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76728728"
---
# <a name="how-to-prevent-row-addition-and-deletion-in-the-windows-forms-datagridview-control"></a><span data-ttu-id="6bb3a-102">Como evitar a adição e a exclusão de linha no controle DataGridView dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="6bb3a-102">How to: Prevent Row Addition and Deletion in the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="6bb3a-103">Às vezes, você desejará impedir que os usuários insiram novas linhas de dados ou exclua linhas existentes no controle de <xref:System.Windows.Forms.DataGridView>.</span><span class="sxs-lookup"><span data-stu-id="6bb3a-103">Sometimes you will want to prevent users from entering new rows of data or deleting existing rows in your <xref:System.Windows.Forms.DataGridView> control.</span></span> <span data-ttu-id="6bb3a-104">A propriedade <xref:System.Windows.Forms.DataGridView.AllowUserToAddRows%2A> indica se a linha de novos registros está presente na parte inferior do controle, enquanto a propriedade <xref:System.Windows.Forms.DataGridView.AllowUserToDeleteRows%2A> indica se as linhas podem ser removidas.</span><span class="sxs-lookup"><span data-stu-id="6bb3a-104">The <xref:System.Windows.Forms.DataGridView.AllowUserToAddRows%2A> property indicates whether the row for new records is present at the bottom of the control, while the <xref:System.Windows.Forms.DataGridView.AllowUserToDeleteRows%2A> property indicates whether rows can be removed.</span></span> <span data-ttu-id="6bb3a-105">O exemplo de código a seguir usa essas propriedades e também define a propriedade <xref:System.Windows.Forms.DataGridView.ReadOnly%2A> para tornar o controle inteiramente somente leitura.</span><span class="sxs-lookup"><span data-stu-id="6bb3a-105">The following code example uses these properties and also sets the <xref:System.Windows.Forms.DataGridView.ReadOnly%2A> property to make the control entirely read-only.</span></span>  
  
 <span data-ttu-id="6bb3a-106">Há suporte para esta tarefa no Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="6bb3a-106">There is support for this task in Visual Studio.</span></span> <span data-ttu-id="6bb3a-107">Consulte também [como impedir a adição e exclusão de linhas no controle Windows Forms DataGridView usando o designer](prevent-row-addition-and-deletion-in-the-datagrid-using-the-designer.md).</span><span class="sxs-lookup"><span data-stu-id="6bb3a-107">Also see [How to: Prevent Row Addition and Deletion in the Windows Forms DataGridView Control Using the Designer](prevent-row-addition-and-deletion-in-the-datagrid-using-the-designer.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="6bb3a-108">{1&gt;Exemplo&lt;1}</span><span class="sxs-lookup"><span data-stu-id="6bb3a-108">Example</span></span>  
 [!code-csharp[System.Windows.Forms.DataGridViewMisc#090](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#090)]
 [!code-vb[System.Windows.Forms.DataGridViewMisc#090](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#090)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="6bb3a-109">Compilando o Código</span><span class="sxs-lookup"><span data-stu-id="6bb3a-109">Compiling the Code</span></span>  
 <span data-ttu-id="6bb3a-110">Este exemplo requer:</span><span class="sxs-lookup"><span data-stu-id="6bb3a-110">This example requires:</span></span>  
  
- <span data-ttu-id="6bb3a-111">Um controle <xref:System.Windows.Forms.DataGridView> chamado `dataGridView1`.</span><span class="sxs-lookup"><span data-stu-id="6bb3a-111">A <xref:System.Windows.Forms.DataGridView> control named `dataGridView1`.</span></span>  
  
- <span data-ttu-id="6bb3a-112">Referências aos assemblies <xref:System?displayProperty=nameWithType> e <xref:System.Windows.Forms?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="6bb3a-112">References to the <xref:System?displayProperty=nameWithType> and <xref:System.Windows.Forms?displayProperty=nameWithType> assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6bb3a-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="6bb3a-113">See also</span></span>

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridView.AllowUserToAddRows%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridView.ReadOnly%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridView.AllowUserToAddRows%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridView.AllowUserToDeleteRows%2A?displayProperty=nameWithType>
- [<span data-ttu-id="6bb3a-114">Funcionalidades de coluna, linha e célula básicas no controle DataGridView do Windows Forms</span><span class="sxs-lookup"><span data-stu-id="6bb3a-114">Basic Column, Row, and Cell Features in the Windows Forms DataGridView Control</span></span>](basic-column-row-and-cell-features-wf-datagridview-control.md)
