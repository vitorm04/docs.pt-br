---
title: 'Como: Evitar a adição e a exclusão de linha no controle DataGridView do Windows Forms usando o designer'
ms.date: 03/30/2017
helpviewer_keywords:
- DataGridView control [Windows Forms], preventing row addition or deletion
ms.assetid: a17722bd-9400-41e6-8dcc-c9c151f0a749
ms.openlocfilehash: f47eb29bf9ae077555f352d10c667bac4ade9373
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69968329"
---
# <a name="how-to-prevent-row-addition-and-deletion-in-the-windows-forms-datagridview-control-using-the-designer"></a><span data-ttu-id="9a7c9-102">Como: Evitar a adição e a exclusão de linha no controle DataGridView do Windows Forms usando o designer</span><span class="sxs-lookup"><span data-stu-id="9a7c9-102">How to: Prevent Row Addition and Deletion in the Windows Forms DataGridView Control Using the Designer</span></span>
<span data-ttu-id="9a7c9-103">Às vezes, você desejará impedir que os usuários insiram novas linhas de dados ou exclua linhas existentes no seu <xref:System.Windows.Forms.DataGridView> controle.</span><span class="sxs-lookup"><span data-stu-id="9a7c9-103">Sometimes you will want to prevent users from entering new rows of data or deleting existing rows in your <xref:System.Windows.Forms.DataGridView> control.</span></span> <span data-ttu-id="9a7c9-104">Novas linhas são inseridas na linha especial para novos registros na parte inferior do controle.</span><span class="sxs-lookup"><span data-stu-id="9a7c9-104">New rows are entered in the special row for new records at the bottom of the control.</span></span> <span data-ttu-id="9a7c9-105">Quando você desabilitar a adição de linha, a linha para novos registros não será exibida.</span><span class="sxs-lookup"><span data-stu-id="9a7c9-105">When you disable row addition, the row for new records is not displayed.</span></span> <span data-ttu-id="9a7c9-106">Em seguida, você pode deixar o controle totalmente somente leitura desabilitando a exclusão de linha e a edição de célula.</span><span class="sxs-lookup"><span data-stu-id="9a7c9-106">You can then make the control entirely read-only by disabling row deletion and cell editing.</span></span>

 <span data-ttu-id="9a7c9-107">O procedimento a seguir requer um projeto de **aplicativo do Windows** com um <xref:System.Windows.Forms.DataGridView> formulário que contém um controle.</span><span class="sxs-lookup"><span data-stu-id="9a7c9-107">The following procedure requires a **Windows Application** project with a form containing a <xref:System.Windows.Forms.DataGridView> control.</span></span> <span data-ttu-id="9a7c9-108">Para obter informações sobre como configurar esse projeto, consulte [como: Crie um projeto](/visualstudio/ide/step-1-create-a-windows-forms-application-project) de aplicativo Windows Forms [e como: Adicione controles a Windows Forms](how-to-add-controls-to-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="9a7c9-108">For information about setting up such a project, see [How to: Create a Windows Forms application project](/visualstudio/ide/step-1-create-a-windows-forms-application-project) and [How to: Add Controls to Windows Forms](how-to-add-controls-to-windows-forms.md).</span></span>

## <a name="to-prevent-row-addition-and-deletion"></a><span data-ttu-id="9a7c9-109">Para evitar a exclusão e adição de linha</span><span class="sxs-lookup"><span data-stu-id="9a7c9-109">To prevent row addition and deletion</span></span>

- <span data-ttu-id="9a7c9-110">Clique no glifo de marca inteligente (![glifo de marca inteligente](./media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph")) no <xref:System.Windows.Forms.DataGridView> canto superior direito do controle e desmarque as caixas de seleção **habilitar adição** e **Habilitar exclusão** .</span><span class="sxs-lookup"><span data-stu-id="9a7c9-110">Click the smart tag glyph (![Smart Tag Glyph](./media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph")) on the upper-right corner of the <xref:System.Windows.Forms.DataGridView> control, and then clear the **Enable Adding** and **Enable Deleting** check boxes.</span></span>

    > [!NOTE]
    > <span data-ttu-id="9a7c9-111">Para tornar o controle somente leitura inteiramente, desmarque também a caixa de seleção **Habilitar Edição**.</span><span class="sxs-lookup"><span data-stu-id="9a7c9-111">To make the control entirely read-only, clear the **Enable Editing** check box as well.</span></span>

## <a name="see-also"></a><span data-ttu-id="9a7c9-112">Consulte também</span><span class="sxs-lookup"><span data-stu-id="9a7c9-112">See also</span></span>

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridView.AllowUserToAddRows%2A?displayProperty=nameWithType>
- [<span data-ttu-id="9a7c9-113">Como: Criar um projeto de aplicativo do Windows Forms</span><span class="sxs-lookup"><span data-stu-id="9a7c9-113">How to: Create a Windows Forms application project</span></span>](/visualstudio/ide/step-1-create-a-windows-forms-application-project)
- [<span data-ttu-id="9a7c9-114">Como: Adicionar controles a Windows Forms</span><span class="sxs-lookup"><span data-stu-id="9a7c9-114">How to: Add Controls to Windows Forms</span></span>](how-to-add-controls-to-windows-forms.md)
