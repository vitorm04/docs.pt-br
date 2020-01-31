---
title: Especificar o modo de edição para o controle DataGridView
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DataGridView control [Windows Forms], edit mode
- data grids [Windows Forms], edit mode
ms.assetid: 93e117e8-94c4-411b-ba31-645e475ed85c
ms.openlocfilehash: c0318202a80f9a43f1b656201732ef032f430b5b
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76743771"
---
# <a name="how-to-specify-the-edit-mode-for-the-windows-forms-datagridview-control"></a><span data-ttu-id="b82b5-102">Como especificar o modo de edição do controle DataGridView dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="b82b5-102">How to: Specify the Edit Mode for the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="b82b5-103">Por padrão, os usuários podem editar o conteúdo da célula da caixa de texto <xref:System.Windows.Forms.DataGridView> atual digitando-o ou pressionando F2.</span><span class="sxs-lookup"><span data-stu-id="b82b5-103">By default, users can edit the contents of the current <xref:System.Windows.Forms.DataGridView> text box cell by typing in it or pressing F2.</span></span> <span data-ttu-id="b82b5-104">Isso colocará a célula no modo de edição se todas as condições a seguir forem atendidas:</span><span class="sxs-lookup"><span data-stu-id="b82b5-104">This puts the cell in edit mode if all of the following conditions are met:</span></span>  
  
- <span data-ttu-id="b82b5-105">A fonte de dados subjacente der suporte à edição.</span><span class="sxs-lookup"><span data-stu-id="b82b5-105">The underlying data source supports editing.</span></span>  
  
- <span data-ttu-id="b82b5-106">O controle <xref:System.Windows.Forms.DataGridView> está habilitado.</span><span class="sxs-lookup"><span data-stu-id="b82b5-106">The <xref:System.Windows.Forms.DataGridView> control is enabled.</span></span>  
  
- <span data-ttu-id="b82b5-107">O valor da propriedade <xref:System.Windows.Forms.DataGridView.EditMode%2A> não é <xref:System.Windows.Forms.DataGridViewEditMode.EditProgrammatically>.</span><span class="sxs-lookup"><span data-stu-id="b82b5-107">The <xref:System.Windows.Forms.DataGridView.EditMode%2A> property value is not <xref:System.Windows.Forms.DataGridViewEditMode.EditProgrammatically>.</span></span>  
  
- <span data-ttu-id="b82b5-108">As propriedade `ReadOnly` de célula, linha, coluna e controle estiverem definidas como `false`.</span><span class="sxs-lookup"><span data-stu-id="b82b5-108">The `ReadOnly` properties of the cell, row, column, and control are all set to `false`.</span></span>  
  
 <span data-ttu-id="b82b5-109">No modo de edição, o usuário pode alterar o valor da célula e pressionar ENTER para confirmar a alteração ou ESC para reverter a célula para seu valor original.</span><span class="sxs-lookup"><span data-stu-id="b82b5-109">In edit mode, the user can change the cell value and press ENTER to commit the change or ESC to revert the cell to its original value.</span></span>  
  
 <span data-ttu-id="b82b5-110">Você pode configurar um controle de <xref:System.Windows.Forms.DataGridView> para que uma célula entre no modo de edição assim que se tornar a célula atual.</span><span class="sxs-lookup"><span data-stu-id="b82b5-110">You can configure a <xref:System.Windows.Forms.DataGridView> control so that a cell enters edit mode as soon as it becomes the current cell.</span></span> <span data-ttu-id="b82b5-111">O comportamento das teclas ENTER e ESC fica inalterado nesse caso, mas a célula permanece no modo de edição depois que o valor é confirmado ou revertido.</span><span class="sxs-lookup"><span data-stu-id="b82b5-111">The behavior of the ENTER and ESC keys is unchanged in this case, but the cell remains in edit mode after the value is committed or reverted.</span></span> <span data-ttu-id="b82b5-112">Você também pode configurar o controle para que as células entrem no modo de edição somente quando os usuários digitam na célula ou quando pressionam F2.</span><span class="sxs-lookup"><span data-stu-id="b82b5-112">You can also configure the control so that cells enter edit mode only when users type in the cell or only when users press F2.</span></span> <span data-ttu-id="b82b5-113">Por fim, você pode impedir que as células entrem no modo de edição, exceto quando chamar o método <xref:System.Windows.Forms.DataGridView.BeginEdit%2A>.</span><span class="sxs-lookup"><span data-stu-id="b82b5-113">Finally, you can prevent cells from entering edit mode except when you call the <xref:System.Windows.Forms.DataGridView.BeginEdit%2A> method.</span></span>  
  
### <a name="to-change-the-edit-mode-of-a-datagridview-control"></a><span data-ttu-id="b82b5-114">Para alterar o modo de edição de um controle DataGridView</span><span class="sxs-lookup"><span data-stu-id="b82b5-114">To change the edit mode of a DataGridView control</span></span>  
  
- <span data-ttu-id="b82b5-115">Defina a propriedade <xref:System.Windows.Forms.DataGridView.EditMode%2A?displayProperty=nameWithType> como a enumeração de <xref:System.Windows.Forms.DataGridViewEditMode> apropriada.</span><span class="sxs-lookup"><span data-stu-id="b82b5-115">Set the <xref:System.Windows.Forms.DataGridView.EditMode%2A?displayProperty=nameWithType> property to the appropriate <xref:System.Windows.Forms.DataGridViewEditMode> enumeration.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#067](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#067)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#067](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#067)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="b82b5-116">Compilando o Código</span><span class="sxs-lookup"><span data-stu-id="b82b5-116">Compiling the Code</span></span>  
 <span data-ttu-id="b82b5-117">Este exemplo requer:</span><span class="sxs-lookup"><span data-stu-id="b82b5-117">This example requires:</span></span>  
  
- <span data-ttu-id="b82b5-118">Um controle <xref:System.Windows.Forms.DataGridView> chamado `dataGridView1`.</span><span class="sxs-lookup"><span data-stu-id="b82b5-118">A <xref:System.Windows.Forms.DataGridView> control named `dataGridView1`.</span></span>  
  
- <span data-ttu-id="b82b5-119">Referências aos assemblies <xref:System> e <xref:System.Windows.Forms>.</span><span class="sxs-lookup"><span data-stu-id="b82b5-119">References to the <xref:System> and <xref:System.Windows.Forms> assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b82b5-120">Veja também</span><span class="sxs-lookup"><span data-stu-id="b82b5-120">See also</span></span>

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridView.EditMode%2A?displayProperty=nameWithType>
- [<span data-ttu-id="b82b5-121">Entrada de Dados no controle DataGridView dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="b82b5-121">Data Entry in the Windows Forms DataGridView Control</span></span>](data-entry-in-the-windows-forms-datagridview-control.md)
