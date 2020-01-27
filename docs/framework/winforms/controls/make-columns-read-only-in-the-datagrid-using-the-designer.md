---
title: Tornar as colunas somente leitura no controle DataGridView usando o designer
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Forms, columns
- DataGridView control [Windows Forms], read-only columns
- data [Windows Forms], displaying
- columns [Windows Forms], read-only
ms.assetid: b4ef7a75-ab33-4ee3-b2cf-201530e454e9
ms.openlocfilehash: 51d9488ef83f7d2c1c01c9ffd756edf8944d738d
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76744969"
---
# <a name="how-to-make-columns-read-only-in-the-windows-forms-datagridview-control-using-the-designer"></a><span data-ttu-id="92137-102">Como deixar as colunas somente leitura no controle DataGridView dos Windows Forms usando o designer</span><span class="sxs-lookup"><span data-stu-id="92137-102">How to: Make Columns Read-Only in the Windows Forms DataGridView Control Using the Designer</span></span>
<span data-ttu-id="92137-103">Por padrão, os usuários podem modificar texto e dados numéricos exibidos no controle de <xref:System.Windows.Forms.DataGridView> de Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="92137-103">By default, users can modify text and numerical data displayed in the Windows Forms <xref:System.Windows.Forms.DataGridView> control.</span></span> <span data-ttu-id="92137-104">Se quiser exibir os dados que não são destinados para modificação, você deverá tornar somente leitura as colunas que contêm os dados.</span><span class="sxs-lookup"><span data-stu-id="92137-104">If you want to display data that is not meant for modification, you must make the columns that contain the data read-only.</span></span> <span data-ttu-id="92137-105">Para obter informações sobre como tornar o controle totalmente somente leitura, veja [Como evitar a adição e a exclusão de linha no controle no DataGridView dos Windows Forms usando o Designer](prevent-row-addition-and-deletion-in-the-datagrid-using-the-designer.md).</span><span class="sxs-lookup"><span data-stu-id="92137-105">For information about how to make the control entirely read-only, see [How to: Prevent Row Addition and Deletion in the Windows Forms DataGridView Control Using the Designer](prevent-row-addition-and-deletion-in-the-datagrid-using-the-designer.md).</span></span>

 <span data-ttu-id="92137-106">O procedimento a seguir requer um projeto de **aplicativo do Windows** com um formulário que contém um controle <xref:System.Windows.Forms.DataGridView>.</span><span class="sxs-lookup"><span data-stu-id="92137-106">The following procedure requires a **Windows Application** project with a form containing a <xref:System.Windows.Forms.DataGridView> control.</span></span> <span data-ttu-id="92137-107">Para obter informações sobre como configurar esse projeto, consulte [como: criar um projeto de aplicativo Windows Forms](/visualstudio/ide/step-1-create-a-windows-forms-application-project) e [como adicionar controles ao Windows Forms](how-to-add-controls-to-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="92137-107">For information about setting up such a project, see [How to: Create a Windows Forms application project](/visualstudio/ide/step-1-create-a-windows-forms-application-project) and [How to: Add Controls to Windows Forms](how-to-add-controls-to-windows-forms.md).</span></span>

## <a name="to-make-a-column-read-only-by-using-the-designer"></a><span data-ttu-id="92137-108">Para tornar a coluna somente leitura usando o designer</span><span class="sxs-lookup"><span data-stu-id="92137-108">To make a column read-only by using the designer</span></span>

1. <span data-ttu-id="92137-109">Clique no glifo de marca inteligente (![glifo de marca inteligente](./media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph")) no canto superior direito do controle de <xref:System.Windows.Forms.DataGridView> e selecione **Editar colunas**.</span><span class="sxs-lookup"><span data-stu-id="92137-109">Click the smart tag glyph (![Smart Tag Glyph](./media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph")) on the upper-right corner of the <xref:System.Windows.Forms.DataGridView> control, and then select **Edit Columns**.</span></span>

2. <span data-ttu-id="92137-110">Selecione uma coluna na lista **Colunas Selecionadas**.</span><span class="sxs-lookup"><span data-stu-id="92137-110">Select a column from the **Selected Columns** list.</span></span>

3. <span data-ttu-id="92137-111">Na grade **Propriedades da coluna** , defina a propriedade <xref:System.Windows.Forms.DataGridViewColumn.ReadOnly%2A> como `true`.</span><span class="sxs-lookup"><span data-stu-id="92137-111">In the **Column Properties** grid, set the <xref:System.Windows.Forms.DataGridViewColumn.ReadOnly%2A> property to `true`.</span></span>

    > [!NOTE]
    > <span data-ttu-id="92137-112">Você também pode tornar uma coluna somente leitura ao adicioná-la marcando a caixa de seleção **Somente Leitura** na caixa de diálogo **Adicionar Coluna**.</span><span class="sxs-lookup"><span data-stu-id="92137-112">You can also make a column read-only when you add it by selecting the **Read Only** check box in the **Add Column** dialog box.</span></span>

## <a name="see-also"></a><span data-ttu-id="92137-113">Veja também</span><span class="sxs-lookup"><span data-stu-id="92137-113">See also</span></span>

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridViewColumn.ReadOnly%2A?displayProperty=nameWithType>
- [<span data-ttu-id="92137-114">Como adicionar e remover colunas no controle DataGridView dos Windows Forms usando o designer</span><span class="sxs-lookup"><span data-stu-id="92137-114">How to: Add and Remove Columns in the Windows Forms DataGridView Control Using the Designer</span></span>](add-and-remove-columns-in-the-datagrid-using-the-designer.md)
- [<span data-ttu-id="92137-115">Como evitar a adição e a exclusão de linha no controle DataGridView dos Windows Forms usando o designer</span><span class="sxs-lookup"><span data-stu-id="92137-115">How to: Prevent Row Addition and Deletion in the Windows Forms DataGridView Control Using the Designer</span></span>](prevent-row-addition-and-deletion-in-the-datagrid-using-the-designer.md)
- [<span data-ttu-id="92137-116">Como criar um projeto de aplicativo Windows Forms</span><span class="sxs-lookup"><span data-stu-id="92137-116">How to: Create a Windows Forms application project</span></span>](/visualstudio/ide/step-1-create-a-windows-forms-application-project)
- [<span data-ttu-id="92137-117">Como Adicionar Controles ao Windows Forms</span><span class="sxs-lookup"><span data-stu-id="92137-117">How to: Add Controls to Windows Forms</span></span>](how-to-add-controls-to-windows-forms.md)
