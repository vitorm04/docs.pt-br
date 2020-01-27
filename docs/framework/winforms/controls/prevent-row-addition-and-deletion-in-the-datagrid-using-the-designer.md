---
title: Impedir adição e exclusão de linha no controle DataGridView usando o designer
ms.date: 03/30/2017
helpviewer_keywords:
- DataGridView control [Windows Forms], preventing row addition or deletion
ms.assetid: a17722bd-9400-41e6-8dcc-c9c151f0a749
ms.openlocfilehash: cc9aff0f15d1bd6de5c469ee7069a99f3360837a
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76728715"
---
# <a name="how-to-prevent-row-addition-and-deletion-in-the-windows-forms-datagridview-control-using-the-designer"></a><span data-ttu-id="47311-102">Como evitar a adição e a exclusão de linha no controle DataGridView dos Windows Forms usando o designer</span><span class="sxs-lookup"><span data-stu-id="47311-102">How to: Prevent Row Addition and Deletion in the Windows Forms DataGridView Control Using the Designer</span></span>
<span data-ttu-id="47311-103">Às vezes, você desejará impedir que os usuários insiram novas linhas de dados ou exclua linhas existentes no controle de <xref:System.Windows.Forms.DataGridView>.</span><span class="sxs-lookup"><span data-stu-id="47311-103">Sometimes you will want to prevent users from entering new rows of data or deleting existing rows in your <xref:System.Windows.Forms.DataGridView> control.</span></span> <span data-ttu-id="47311-104">Novas linhas são inseridas na linha especial para novos registros na parte inferior do controle.</span><span class="sxs-lookup"><span data-stu-id="47311-104">New rows are entered in the special row for new records at the bottom of the control.</span></span> <span data-ttu-id="47311-105">Quando você desabilitar a adição de linha, a linha para novos registros não será exibida.</span><span class="sxs-lookup"><span data-stu-id="47311-105">When you disable row addition, the row for new records is not displayed.</span></span> <span data-ttu-id="47311-106">Em seguida, você pode deixar o controle totalmente somente leitura desabilitando a exclusão de linha e a edição de célula.</span><span class="sxs-lookup"><span data-stu-id="47311-106">You can then make the control entirely read-only by disabling row deletion and cell editing.</span></span>

 <span data-ttu-id="47311-107">O procedimento a seguir requer um projeto de **aplicativo do Windows** com um formulário que contém um controle <xref:System.Windows.Forms.DataGridView>.</span><span class="sxs-lookup"><span data-stu-id="47311-107">The following procedure requires a **Windows Application** project with a form containing a <xref:System.Windows.Forms.DataGridView> control.</span></span> <span data-ttu-id="47311-108">Para obter informações sobre como configurar esse projeto, consulte [como: criar um projeto de aplicativo Windows Forms](/visualstudio/ide/step-1-create-a-windows-forms-application-project) e [como adicionar controles ao Windows Forms](how-to-add-controls-to-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="47311-108">For information about setting up such a project, see [How to: Create a Windows Forms application project](/visualstudio/ide/step-1-create-a-windows-forms-application-project) and [How to: Add Controls to Windows Forms](how-to-add-controls-to-windows-forms.md).</span></span>

## <a name="to-prevent-row-addition-and-deletion"></a><span data-ttu-id="47311-109">Para evitar a exclusão e adição de linha</span><span class="sxs-lookup"><span data-stu-id="47311-109">To prevent row addition and deletion</span></span>

- <span data-ttu-id="47311-110">Clique no glifo de marca inteligente (![glifo de marca inteligente](./media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph")) no canto superior direito do controle de <xref:System.Windows.Forms.DataGridView> e desmarque as caixas de seleção **habilitar adição** e **Habilitar exclusão** .</span><span class="sxs-lookup"><span data-stu-id="47311-110">Click the smart tag glyph (![Smart Tag Glyph](./media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph")) on the upper-right corner of the <xref:System.Windows.Forms.DataGridView> control, and then clear the **Enable Adding** and **Enable Deleting** check boxes.</span></span>

    > [!NOTE]
    > <span data-ttu-id="47311-111">Para tornar o controle somente leitura inteiramente, desmarque também a caixa de seleção **Habilitar Edição**.</span><span class="sxs-lookup"><span data-stu-id="47311-111">To make the control entirely read-only, clear the **Enable Editing** check box as well.</span></span>

## <a name="see-also"></a><span data-ttu-id="47311-112">Veja também</span><span class="sxs-lookup"><span data-stu-id="47311-112">See also</span></span>

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridView.AllowUserToAddRows%2A?displayProperty=nameWithType>
- [<span data-ttu-id="47311-113">Como criar um projeto de aplicativo Windows Forms</span><span class="sxs-lookup"><span data-stu-id="47311-113">How to: Create a Windows Forms application project</span></span>](/visualstudio/ide/step-1-create-a-windows-forms-application-project)
- [<span data-ttu-id="47311-114">Como Adicionar Controles ao Windows Forms</span><span class="sxs-lookup"><span data-stu-id="47311-114">How to: Add Controls to Windows Forms</span></span>](how-to-add-controls-to-windows-forms.md)
