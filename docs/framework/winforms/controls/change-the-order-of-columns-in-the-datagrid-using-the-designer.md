---
title: Alterar a ordem das colunas no controle DataGridView usando o designer
ms.date: 03/30/2017
helpviewer_keywords:
- columns [Windows Forms], order of
- DataGridView control [Windows Forms], column order
- Windows Forms, columns
- data [Windows Forms], displaying
ms.assetid: 7fe52a98-75d6-448c-97a5-65ca2c568c1a
ms.openlocfilehash: be4f67ca6530b74fc90cb50a10463b2378edb933
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76743148"
---
# <a name="how-to-change-the-order-of-columns-in-the-windows-forms-datagridview-control-using-the-designer"></a><span data-ttu-id="6344c-102">Como alterar a ordem de colunas no controle DataGridView dos Windows Forms usando o designer</span><span class="sxs-lookup"><span data-stu-id="6344c-102">How to: Change the Order of Columns in the Windows Forms DataGridView Control Using the Designer</span></span>

<span data-ttu-id="6344c-103">Quando você associa um Windows Forms <xref:System.Windows.Forms.DataGridView> controle a uma fonte de dados, a ordem de exibição das colunas geradas automaticamente é determinada pela fonte de dados.</span><span class="sxs-lookup"><span data-stu-id="6344c-103">When you bind a Windows Forms <xref:System.Windows.Forms.DataGridView> control to a data source, the display order of the automatically generated columns is dictated by the data source.</span></span> <span data-ttu-id="6344c-104">Se essa ordem não for a que preferir, você poderá alterar a ordem das colunas usando o designer.</span><span class="sxs-lookup"><span data-stu-id="6344c-104">If this order is not what you prefer, you can change the order of the columns using the designer.</span></span> <span data-ttu-id="6344c-105">Talvez deseje adicionar colunas não associadas ao controle e alterar a ordem de exibição.</span><span class="sxs-lookup"><span data-stu-id="6344c-105">You may also want to add unbound columns to the control and change their display order.</span></span> <span data-ttu-id="6344c-106">Para obter informações sobre como alterar a ordem das colunas programaticamente, consulte [Como alterar a ordem de colunas no controle DataGridView dos Windows Forms](how-to-change-the-order-of-columns-in-the-windows-forms-datagridview-control.md).</span><span class="sxs-lookup"><span data-stu-id="6344c-106">For information about how to change the column order programmatically, see [How to: Change the Order of Columns in the Windows Forms DataGridView Control](how-to-change-the-order-of-columns-in-the-windows-forms-datagridview-control.md).</span></span>

<span data-ttu-id="6344c-107">O procedimento a seguir requer um projeto de **aplicativo do Windows** com um formulário que contém um controle <xref:System.Windows.Forms.DataGridView>.</span><span class="sxs-lookup"><span data-stu-id="6344c-107">The following procedure requires a **Windows Application** project with a form containing a <xref:System.Windows.Forms.DataGridView> control.</span></span> <span data-ttu-id="6344c-108">Para obter informações sobre como configurar esse projeto, consulte [como: criar um projeto de aplicativo Windows Forms](/visualstudio/ide/step-1-create-a-windows-forms-application-project) e [como adicionar controles ao Windows Forms](how-to-add-controls-to-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="6344c-108">For information about setting up such a project, see [How to: Create a Windows Forms application project](/visualstudio/ide/step-1-create-a-windows-forms-application-project) and [How to: Add Controls to Windows Forms](how-to-add-controls-to-windows-forms.md).</span></span>

## <a name="to-change-the-column-order-using-the-designer"></a><span data-ttu-id="6344c-109">Para alterar a ordem das colunas usando o designer</span><span class="sxs-lookup"><span data-stu-id="6344c-109">To change the column order using the designer</span></span>

1. <span data-ttu-id="6344c-110">Clique no glifo de marca inteligente (![glifo de marca inteligente](./media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph")) no canto superior direito do controle de <xref:System.Windows.Forms.DataGridView> e selecione **Editar colunas**.</span><span class="sxs-lookup"><span data-stu-id="6344c-110">Click the smart tag glyph (![Smart Tag Glyph](./media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph")) on the upper-right corner of the <xref:System.Windows.Forms.DataGridView> control, and then select **Edit Columns**.</span></span>

2. <span data-ttu-id="6344c-111">Selecione uma coluna na lista **Colunas Selecionadas**.</span><span class="sxs-lookup"><span data-stu-id="6344c-111">Select a column from the **Selected Columns** list.</span></span>

3. <span data-ttu-id="6344c-112">Clique na seta para cima ou para baixo à direita da lista **Colunas selecionadas** até que a coluna selecionada esteja na posição desejada.</span><span class="sxs-lookup"><span data-stu-id="6344c-112">Click the up or down arrow to the right of the **Selected Columns** list until the selected column is in the position you want.</span></span>

## <a name="see-also"></a><span data-ttu-id="6344c-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="6344c-113">See also</span></span>

- <xref:System.Windows.Forms.DataGridView>
- [<span data-ttu-id="6344c-114">Como adicionar e remover colunas no controle DataGridView dos Windows Forms usando o designer</span><span class="sxs-lookup"><span data-stu-id="6344c-114">How to: Add and Remove Columns in the Windows Forms DataGridView Control Using the Designer</span></span>](add-and-remove-columns-in-the-datagrid-using-the-designer.md)
- [<span data-ttu-id="6344c-115">Como criar um projeto de aplicativo Windows Forms</span><span class="sxs-lookup"><span data-stu-id="6344c-115">How to: Create a Windows Forms application project</span></span>](/visualstudio/ide/step-1-create-a-windows-forms-application-project)
- [<span data-ttu-id="6344c-116">Como Adicionar Controles ao Windows Forms</span><span class="sxs-lookup"><span data-stu-id="6344c-116">How to: Add Controls to Windows Forms</span></span>](how-to-add-controls-to-windows-forms.md)
