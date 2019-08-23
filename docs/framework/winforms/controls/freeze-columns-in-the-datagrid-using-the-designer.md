---
title: 'Como: Congelar colunas no controle DataGridView do Windows Forms usando o designer'
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Forms, columns
- columns [Windows Forms], freezing
- DataGridView control [Windows Forms], column freezing
- data [Windows Forms], displaying
ms.assetid: 87412dd2-478f-4751-af87-dafc591fc215
ms.openlocfilehash: 7ebdf7a1598ac3cd61005ae607e5bfbe7cb49059
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69933710"
---
# <a name="how-to-freeze-columns-in-the-windows-forms-datagridview-control-using-the-designer"></a><span data-ttu-id="f773f-102">Como: Congelar colunas no controle DataGridView do Windows Forms usando o designer</span><span class="sxs-lookup"><span data-stu-id="f773f-102">How to: Freeze Columns in the Windows Forms DataGridView Control Using the Designer</span></span>
<span data-ttu-id="f773f-103">Quando os usuários exibem dados exibidos em <xref:System.Windows.Forms.DataGridView> um controle de Windows Forms, às vezes eles precisam se referir a uma única coluna ou conjunto de colunas com frequência.</span><span class="sxs-lookup"><span data-stu-id="f773f-103">When users view data displayed in a Windows Forms <xref:System.Windows.Forms.DataGridView> control, they sometimes need to refer to a single column or set of columns frequently.</span></span> <span data-ttu-id="f773f-104">Por exemplo, quando você exibe uma tabela de informações do cliente que contém várias colunas, é útil exibir o nome do cliente em todos os momentos, enquanto permite que outras colunas rolem para fora da região visível.</span><span class="sxs-lookup"><span data-stu-id="f773f-104">For example, when you display a table of customer information that contains many columns, it is useful for you to display the customer name at all times while enabling other columns to scroll outside the visible region.</span></span>

 <span data-ttu-id="f773f-105">Para obter esse comportamento, você pode congelar colunas no controle.</span><span class="sxs-lookup"><span data-stu-id="f773f-105">To achieve this behavior, you can freeze columns in the control.</span></span> <span data-ttu-id="f773f-106">Quando você congela uma coluna, todas as colunas à esquerda (ou à direita em scripts de idioma da direita para esquerda) são congeladas também.</span><span class="sxs-lookup"><span data-stu-id="f773f-106">When you freeze a column, all the columns to its left (or to its right in right-to-left language scripts) are frozen as well.</span></span> <span data-ttu-id="f773f-107">Colunas congeladas permanecerão no local enquanto todas as outras colunas podem rolar.</span><span class="sxs-lookup"><span data-stu-id="f773f-107">Frozen columns remain in place while all other columns can scroll.</span></span> <span data-ttu-id="f773f-108">Se a reordenação de coluna estiver habilitada, as colunas congeladas serão tratadas como um grupo diferente das colunas não congeladas.</span><span class="sxs-lookup"><span data-stu-id="f773f-108">If column reordering is enabled, the frozen columns are treated as a group distinct from the unfrozen columns.</span></span> <span data-ttu-id="f773f-109">Os usuários podem reposicionar colunas em um dos grupos, mas não poderão mover uma coluna de um grupo para outro.</span><span class="sxs-lookup"><span data-stu-id="f773f-109">Users can reposition columns in either group, but they cannot move a column from one group to the other.</span></span>

 <span data-ttu-id="f773f-110">O procedimento a seguir requer um projeto de **aplicativo do Windows** com um <xref:System.Windows.Forms.DataGridView> formulário que contém um controle.</span><span class="sxs-lookup"><span data-stu-id="f773f-110">The following procedure requires a **Windows Application** project with a form containing a <xref:System.Windows.Forms.DataGridView> control.</span></span> <span data-ttu-id="f773f-111">Para obter informações sobre como configurar esse projeto, consulte [como: Crie um projeto](/visualstudio/ide/step-1-create-a-windows-forms-application-project) de aplicativo Windows Forms [e como: Adicione controles a Windows Forms](how-to-add-controls-to-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="f773f-111">For information about setting up such a project, see [How to: Create a Windows Forms application project](/visualstudio/ide/step-1-create-a-windows-forms-application-project) and [How to: Add Controls to Windows Forms](how-to-add-controls-to-windows-forms.md).</span></span>

## <a name="to-freeze-a-column-using-the-designer"></a><span data-ttu-id="f773f-112">Para congelar uma coluna usando o designer</span><span class="sxs-lookup"><span data-stu-id="f773f-112">To freeze a column using the designer</span></span>

1. <span data-ttu-id="f773f-113">Clique no glifo de marca inteligente (![glifo de marca inteligente](./media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph")) no <xref:System.Windows.Forms.DataGridView> canto superior direito do controle e selecione **Editar colunas**.</span><span class="sxs-lookup"><span data-stu-id="f773f-113">Click the smart tag glyph (![Smart Tag Glyph](./media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph")) on the upper-right corner of the <xref:System.Windows.Forms.DataGridView> control, and then select **Edit Columns**.</span></span>

2. <span data-ttu-id="f773f-114">Selecione uma coluna na lista **Colunas Selecionadas**.</span><span class="sxs-lookup"><span data-stu-id="f773f-114">Select a column from the **Selected Columns** list.</span></span>

3. <span data-ttu-id="f773f-115">Na grade **Propriedades da coluna** , defina a <xref:System.Windows.Forms.DataGridViewColumn.Frozen%2A> Propriedade como `true`.</span><span class="sxs-lookup"><span data-stu-id="f773f-115">In the **Column Properties** grid, set the <xref:System.Windows.Forms.DataGridViewColumn.Frozen%2A> property to `true`.</span></span>

    > [!NOTE]
    > <span data-ttu-id="f773f-116">Você também pode congelar uma coluna ao adicioná-la selecionando a caixa de seleção **Congelada** na caixa de diálogo **Adicionar Coluna**.</span><span class="sxs-lookup"><span data-stu-id="f773f-116">You can also freeze a column when adding it by selecting the **Frozen** box in the **Add Column** dialog box.</span></span>

## <a name="see-also"></a><span data-ttu-id="f773f-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f773f-117">See also</span></span>

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridViewColumn.Frozen%2A?displayProperty=nameWithType>
- [<span data-ttu-id="f773f-118">Como: Adicionar e remover colunas no controle Windows Forms DataGridView usando o designer</span><span class="sxs-lookup"><span data-stu-id="f773f-118">How to: Add and Remove Columns in the Windows Forms DataGridView Control Using the Designer</span></span>](add-and-remove-columns-in-the-datagrid-using-the-designer.md)
- [<span data-ttu-id="f773f-119">Como: Habilitar reordenação de coluna no controle Windows Forms DataGridView usando o designer</span><span class="sxs-lookup"><span data-stu-id="f773f-119">How to: Enable Column Reordering in the Windows Forms DataGridView Control Using the Designer</span></span>](enable-column-reordering-in-the-datagrid-using-the-designer.md)
- <span data-ttu-id="f773f-120">[Como: Exibir texto da direita para a esquerda em Windows Forms para globalização](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/7d3337xw(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="f773f-120">[How to: Display Right-to-Left Text in Windows Forms for Globalization](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/7d3337xw(v=vs.100))</span></span>
- [<span data-ttu-id="f773f-121">Como: Criar um projeto de aplicativo do Windows Forms</span><span class="sxs-lookup"><span data-stu-id="f773f-121">How to: Create a Windows Forms application project</span></span>](/visualstudio/ide/step-1-create-a-windows-forms-application-project)
- [<span data-ttu-id="f773f-122">Como: Adicionar controles a Windows Forms</span><span class="sxs-lookup"><span data-stu-id="f773f-122">How to: Add Controls to Windows Forms</span></span>](how-to-add-controls-to-windows-forms.md)
