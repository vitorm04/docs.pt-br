---
title: 'Como: Evitar a adição de linha e exclusão no controle DataGridView dos Windows Forms'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DataGridView control [Windows Forms], disabling data entry
- data entry [Windows Forms], disabling in grids
- data grids [Windows Forms], disabling data entry
ms.assetid: ef9539ce-539b-404e-84b6-ac282b64b88c
ms.openlocfilehash: 9f579720b4f3ff561ecd807e09db8d464abc9001
ms.sourcegitcommit: 2b986afe4ce9e13bbeec929c9737757eb61de60e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/22/2019
ms.locfileid: "56664582"
---
# <a name="how-to-prevent-row-addition-and-deletion-in-the-windows-forms-datagridview-control"></a><span data-ttu-id="8f264-102">Como: Evitar a adição de linha e exclusão no controle DataGridView dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="8f264-102">How to: Prevent Row Addition and Deletion in the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="8f264-103">Às vezes, você desejará impedir que usuários insiram novas linhas de dados ou excluam linhas existentes em seu <xref:System.Windows.Forms.DataGridView> controle.</span><span class="sxs-lookup"><span data-stu-id="8f264-103">Sometimes you will want to prevent users from entering new rows of data or deleting existing rows in your <xref:System.Windows.Forms.DataGridView> control.</span></span> <span data-ttu-id="8f264-104">O <xref:System.Windows.Forms.DataGridView.AllowUserToAddRows%2A> propriedade indica se a linha para novos registros está presente na parte inferior do controle, enquanto o <xref:System.Windows.Forms.DataGridView.AllowUserToDeleteRows%2A> propriedade indica se as linhas podem ser removidas.</span><span class="sxs-lookup"><span data-stu-id="8f264-104">The <xref:System.Windows.Forms.DataGridView.AllowUserToAddRows%2A> property indicates whether the row for new records is present at the bottom of the control, while the <xref:System.Windows.Forms.DataGridView.AllowUserToDeleteRows%2A> property indicates whether rows can be removed.</span></span> <span data-ttu-id="8f264-105">O exemplo de código a seguir usa essas propriedades e também define o <xref:System.Windows.Forms.DataGridView.ReadOnly%2A> propriedade para tornar o controle totalmente somente leitura.</span><span class="sxs-lookup"><span data-stu-id="8f264-105">The following code example uses these properties and also sets the <xref:System.Windows.Forms.DataGridView.ReadOnly%2A> property to make the control entirely read-only.</span></span>  
  
 <span data-ttu-id="8f264-106">Há suporte para esta tarefa no Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="8f264-106">There is support for this task in Visual Studio.</span></span> <span data-ttu-id="8f264-107">Consulte também [como: Evitar a adição de linha e exclusão no Windows Forms usando o Designer de controle de DataGridView](prevent-row-addition-and-deletion-in-the-datagrid-using-the-designer.md).</span><span class="sxs-lookup"><span data-stu-id="8f264-107">Also see [How to: Prevent Row Addition and Deletion in the Windows Forms DataGridView Control Using the Designer](prevent-row-addition-and-deletion-in-the-datagrid-using-the-designer.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="8f264-108">Exemplo</span><span class="sxs-lookup"><span data-stu-id="8f264-108">Example</span></span>  
 [!code-csharp[System.Windows.Forms.DataGridViewMisc#090](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#090)]
 [!code-vb[System.Windows.Forms.DataGridViewMisc#090](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#090)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="8f264-109">Compilando o código</span><span class="sxs-lookup"><span data-stu-id="8f264-109">Compiling the Code</span></span>  
 <span data-ttu-id="8f264-110">Este exemplo requer:</span><span class="sxs-lookup"><span data-stu-id="8f264-110">This example requires:</span></span>  
  
-   <span data-ttu-id="8f264-111">Um controle <xref:System.Windows.Forms.DataGridView> chamado `dataGridView1`.</span><span class="sxs-lookup"><span data-stu-id="8f264-111">A <xref:System.Windows.Forms.DataGridView> control named `dataGridView1`.</span></span>  
  
-   <span data-ttu-id="8f264-112">Referências aos assemblies <xref:System?displayProperty=nameWithType> e <xref:System.Windows.Forms?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="8f264-112">References to the <xref:System?displayProperty=nameWithType> and <xref:System.Windows.Forms?displayProperty=nameWithType> assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8f264-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="8f264-113">See also</span></span>
- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridView.AllowUserToAddRows%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridView.ReadOnly%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridView.AllowUserToAddRows%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridView.AllowUserToDeleteRows%2A?displayProperty=nameWithType>
- [<span data-ttu-id="8f264-114">Funcionalidades de coluna, linha e célula básicas no controle DataGridView do Windows Forms</span><span class="sxs-lookup"><span data-stu-id="8f264-114">Basic Column, Row, and Cell Features in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/basic-column-row-and-cell-features-wf-datagridview-control.md)
