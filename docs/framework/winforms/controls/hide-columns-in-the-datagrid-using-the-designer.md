---
title: Ocultar colunas no controle DataGridView usando o designer
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Forms, columns
- columns [Windows Forms], hiding
- DataGridView control [Windows Forms], column hiding
- data [Windows Forms], displaying
ms.assetid: a81c38e6-2527-426a-bcb1-be691403be04
ms.openlocfilehash: 3c9a6bdeacbeb5929488e6af0054403db73c4239
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76738661"
---
# <a name="how-to-hide-columns-in-the-windows-forms-datagridview-control-using-the-designer"></a><span data-ttu-id="a6206-102">Como ocultar colunas no controle DataGridView dos Windows Forms usando o designer</span><span class="sxs-lookup"><span data-stu-id="a6206-102">How to: Hide Columns in the Windows Forms DataGridView Control Using the Designer</span></span>
<span data-ttu-id="a6206-103">Às vezes, você desejará exibir apenas algumas das colunas que estão disponíveis em um controle de <xref:System.Windows.Forms.DataGridView> Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="a6206-103">Sometimes you will want to display only some of the columns that are available in a Windows Forms <xref:System.Windows.Forms.DataGridView> control.</span></span> <span data-ttu-id="a6206-104">Por exemplo, talvez você queira mostrar uma coluna de salário de funcionários para usuários com credenciais de gerenciamento enquanto a oculta de outros usuários.</span><span class="sxs-lookup"><span data-stu-id="a6206-104">For example, you may want to show an employee salary column to users with management credentials while hiding it from other users.</span></span> <span data-ttu-id="a6206-105">Como alternativa, talvez você queira associar o controle a uma fonte de dados que contém várias colunas, sendo que você deseja exibir apenas algumas delas.</span><span class="sxs-lookup"><span data-stu-id="a6206-105">Alternately, you may want to bind the control to a data source that contains many columns, only some of which you want to display.</span></span> <span data-ttu-id="a6206-106">Nesse caso, você normalmente removerá as colunas que não está interessado em exibir em vez de ocultá-las.</span><span class="sxs-lookup"><span data-stu-id="a6206-106">In this case, you will typically remove the columns you are not interested in displaying rather than hiding them.</span></span> <span data-ttu-id="a6206-107">Para saber mais, veja [Como adicionar e remover colunas no controle DataGridView dos Windows Forms usando o designer](add-and-remove-columns-in-the-datagrid-using-the-designer.md).</span><span class="sxs-lookup"><span data-stu-id="a6206-107">For more information, see [How to: Add and Remove Columns in the Windows Forms DataGridView Control Using the Designer](add-and-remove-columns-in-the-datagrid-using-the-designer.md).</span></span>

 <span data-ttu-id="a6206-108">O procedimento a seguir requer um projeto de **aplicativo do Windows** com um formulário que contém um controle <xref:System.Windows.Forms.DataGridView>.</span><span class="sxs-lookup"><span data-stu-id="a6206-108">The following procedure requires a **Windows Application** project with a form containing a <xref:System.Windows.Forms.DataGridView> control.</span></span> <span data-ttu-id="a6206-109">Para obter informações sobre como configurar esse projeto, consulte [como: criar um projeto de aplicativo Windows Forms](/visualstudio/ide/step-1-create-a-windows-forms-application-project) e [como adicionar controles ao Windows Forms](how-to-add-controls-to-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="a6206-109">For information about setting up such a project, see [How to: Create a Windows Forms application project](/visualstudio/ide/step-1-create-a-windows-forms-application-project) and [How to: Add Controls to Windows Forms](how-to-add-controls-to-windows-forms.md).</span></span>

## <a name="to-hide-a-column-using-the-designer"></a><span data-ttu-id="a6206-110">Para ocultar uma coluna usando o designer</span><span class="sxs-lookup"><span data-stu-id="a6206-110">To hide a column using the designer</span></span>

1. <span data-ttu-id="a6206-111">Clique no glifo de marca inteligente (![glifo de marca inteligente](./media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph")) no canto superior direito do controle de <xref:System.Windows.Forms.DataGridView> e selecione **Editar colunas**.</span><span class="sxs-lookup"><span data-stu-id="a6206-111">Click the smart tag glyph (![Smart Tag Glyph](./media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph")) on the upper-right corner of the <xref:System.Windows.Forms.DataGridView> control, and then select **Edit Columns**.</span></span>

2. <span data-ttu-id="a6206-112">Selecione uma coluna na lista **Colunas Selecionadas**.</span><span class="sxs-lookup"><span data-stu-id="a6206-112">Select a column from the **Selected Columns** list.</span></span>

3. <span data-ttu-id="a6206-113">Na grade **Propriedades da coluna** , defina a propriedade <xref:System.Windows.Forms.DataGridViewColumn.Visible%2A> como `false`.</span><span class="sxs-lookup"><span data-stu-id="a6206-113">In the **Column Properties** grid, set the <xref:System.Windows.Forms.DataGridViewColumn.Visible%2A> property to `false`.</span></span>

    > [!NOTE]
    > <span data-ttu-id="a6206-114">Você também pode ocultar uma coluna ao adicioná-la desmarcando a caixa de seleção **Visível** na caixa de diálogo **Adicionar Coluna**.</span><span class="sxs-lookup"><span data-stu-id="a6206-114">You can also hide a column when adding it by clearing the **Visible** check box in the **Add Column** dialog box.</span></span>

## <a name="see-also"></a><span data-ttu-id="a6206-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a6206-115">See also</span></span>

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridViewColumn.Visible%2A?displayProperty=nameWithType>
- [<span data-ttu-id="a6206-116">Como adicionar e remover colunas no controle DataGridView dos Windows Forms usando o designer</span><span class="sxs-lookup"><span data-stu-id="a6206-116">How to: Add and Remove Columns in the Windows Forms DataGridView Control Using the Designer</span></span>](add-and-remove-columns-in-the-datagrid-using-the-designer.md)
- [<span data-ttu-id="a6206-117">Como criar um projeto de aplicativo Windows Forms</span><span class="sxs-lookup"><span data-stu-id="a6206-117">How to: Create a Windows Forms application project</span></span>](/visualstudio/ide/step-1-create-a-windows-forms-application-project)
- [<span data-ttu-id="a6206-118">Como Adicionar Controles ao Windows Forms</span><span class="sxs-lookup"><span data-stu-id="a6206-118">How to: Add Controls to Windows Forms</span></span>](how-to-add-controls-to-windows-forms.md)
