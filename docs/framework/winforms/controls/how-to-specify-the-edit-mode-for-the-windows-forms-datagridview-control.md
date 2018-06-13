---
title: Como especificar o modo de edição do controle DataGridView dos Windows Forms
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DataGridView control [Windows Forms], edit mode
- data grids [Windows Forms], edit mode
ms.assetid: 93e117e8-94c4-411b-ba31-645e475ed85c
ms.openlocfilehash: 5117dfe2e017cf4af1d352fdbf23c6599c0e56a9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33536267"
---
# <a name="how-to-specify-the-edit-mode-for-the-windows-forms-datagridview-control"></a><span data-ttu-id="4ec1f-102">Como especificar o modo de edição do controle DataGridView dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="4ec1f-102">How to: Specify the Edit Mode for the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="4ec1f-103">Por padrão, os usuários podem editar o conteúdo do atual <xref:System.Windows.Forms.DataGridView> célula da caixa de texto digitando nele ou pressionando F2.</span><span class="sxs-lookup"><span data-stu-id="4ec1f-103">By default, users can edit the contents of the current <xref:System.Windows.Forms.DataGridView> text box cell by typing in it or pressing F2.</span></span> <span data-ttu-id="4ec1f-104">Isso colocará a célula no modo de edição se todas as condições a seguir forem atendidas:</span><span class="sxs-lookup"><span data-stu-id="4ec1f-104">This puts the cell in edit mode if all of the following conditions are met:</span></span>  
  
-   <span data-ttu-id="4ec1f-105">A fonte de dados subjacente der suporte à edição.</span><span class="sxs-lookup"><span data-stu-id="4ec1f-105">The underlying data source supports editing.</span></span>  
  
-   <span data-ttu-id="4ec1f-106">O <xref:System.Windows.Forms.DataGridView> controle está habilitado.</span><span class="sxs-lookup"><span data-stu-id="4ec1f-106">The <xref:System.Windows.Forms.DataGridView> control is enabled.</span></span>  
  
-   <span data-ttu-id="4ec1f-107">O valor da propriedade <xref:System.Windows.Forms.DataGridView.EditMode%2A> não é <xref:System.Windows.Forms.DataGridViewEditMode.EditProgrammatically>.</span><span class="sxs-lookup"><span data-stu-id="4ec1f-107">The <xref:System.Windows.Forms.DataGridView.EditMode%2A> property value is not <xref:System.Windows.Forms.DataGridViewEditMode.EditProgrammatically>.</span></span>  
  
-   <span data-ttu-id="4ec1f-108">As propriedade `ReadOnly` de célula, linha, coluna e controle estiverem definidas como `false`.</span><span class="sxs-lookup"><span data-stu-id="4ec1f-108">The `ReadOnly` properties of the cell, row, column, and control are all set to `false`.</span></span>  
  
 <span data-ttu-id="4ec1f-109">No modo de edição, o usuário pode alterar o valor da célula e pressionar ENTER para confirmar a alteração ou ESC para reverter a célula para seu valor original.</span><span class="sxs-lookup"><span data-stu-id="4ec1f-109">In edit mode, the user can change the cell value and press ENTER to commit the change or ESC to revert the cell to its original value.</span></span>  
  
 <span data-ttu-id="4ec1f-110">Você pode configurar um <xref:System.Windows.Forms.DataGridView> controlar de forma que uma célula entra em modo de edição assim que ele se torna a célula atual.</span><span class="sxs-lookup"><span data-stu-id="4ec1f-110">You can configure a <xref:System.Windows.Forms.DataGridView> control so that a cell enters edit mode as soon as it becomes the current cell.</span></span> <span data-ttu-id="4ec1f-111">O comportamento das teclas ENTER e ESC fica inalterado nesse caso, mas a célula permanece no modo de edição depois que o valor é confirmado ou revertido.</span><span class="sxs-lookup"><span data-stu-id="4ec1f-111">The behavior of the ENTER and ESC keys is unchanged in this case, but the cell remains in edit mode after the value is committed or reverted.</span></span> <span data-ttu-id="4ec1f-112">Você também pode configurar o controle para que as células entrem no modo de edição somente quando os usuários digitam na célula ou quando pressionam F2.</span><span class="sxs-lookup"><span data-stu-id="4ec1f-112">You can also configure the control so that cells enter edit mode only when users type in the cell or only when users press F2.</span></span> <span data-ttu-id="4ec1f-113">Por fim, você pode impedir que as células no modo de edição, exceto quando você chama o <xref:System.Windows.Forms.DataGridView.BeginEdit%2A> método.</span><span class="sxs-lookup"><span data-stu-id="4ec1f-113">Finally, you can prevent cells from entering edit mode except when you call the <xref:System.Windows.Forms.DataGridView.BeginEdit%2A> method.</span></span>  
  
### <a name="to-change-the-edit-mode-of-a-datagridview-control"></a><span data-ttu-id="4ec1f-114">Para alterar o modo de edição de um controle DataGridView</span><span class="sxs-lookup"><span data-stu-id="4ec1f-114">To change the edit mode of a DataGridView control</span></span>  
  
-   <span data-ttu-id="4ec1f-115">Definir o <xref:System.Windows.Forms.DataGridView.EditMode%2A?displayProperty=nameWithType> propriedade apropriada <xref:System.Windows.Forms.DataGridViewEditMode> enumeração.</span><span class="sxs-lookup"><span data-stu-id="4ec1f-115">Set the <xref:System.Windows.Forms.DataGridView.EditMode%2A?displayProperty=nameWithType> property to the appropriate <xref:System.Windows.Forms.DataGridViewEditMode> enumeration.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#067](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#067)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#067](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#067)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="4ec1f-116">Compilando o código</span><span class="sxs-lookup"><span data-stu-id="4ec1f-116">Compiling the Code</span></span>  
 <span data-ttu-id="4ec1f-117">Este exemplo requer:</span><span class="sxs-lookup"><span data-stu-id="4ec1f-117">This example requires:</span></span>  
  
-   <span data-ttu-id="4ec1f-118">Um controle <xref:System.Windows.Forms.DataGridView> chamado `dataGridView1`.</span><span class="sxs-lookup"><span data-stu-id="4ec1f-118">A <xref:System.Windows.Forms.DataGridView> control named `dataGridView1`.</span></span>  
  
-   <span data-ttu-id="4ec1f-119">Referências aos assemblies <xref:System> e <xref:System.Windows.Forms>.</span><span class="sxs-lookup"><span data-stu-id="4ec1f-119">References to the <xref:System> and <xref:System.Windows.Forms> assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4ec1f-120">Consulte também</span><span class="sxs-lookup"><span data-stu-id="4ec1f-120">See Also</span></span>  
 <xref:System.Windows.Forms.DataGridView>  
 <xref:System.Windows.Forms.DataGridView.EditMode%2A?displayProperty=nameWithType>  
 [<span data-ttu-id="4ec1f-121">Entrada de Dados no controle DataGridView dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="4ec1f-121">Data Entry in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/data-entry-in-the-windows-forms-datagridview-control.md)
