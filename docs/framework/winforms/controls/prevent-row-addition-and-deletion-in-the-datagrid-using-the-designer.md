---
title: 'Como: Evitar a adição e a exclusão de linha no controle DataGridView do Windows Forms usando o designer'
ms.date: 03/30/2017
helpviewer_keywords:
- DataGridView control [Windows Forms], preventing row addition or deletion
ms.assetid: a17722bd-9400-41e6-8dcc-c9c151f0a749
ms.openlocfilehash: 20f9b85dc48ccd634468d0fed000120723f8ee5c
ms.sourcegitcommit: cf9515122fce716bcfb6618ba366e39b5a2eb81e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/15/2019
ms.locfileid: "69038198"
---
# <a name="how-to-prevent-row-addition-and-deletion-in-the-windows-forms-datagridview-control-using-the-designer"></a><span data-ttu-id="b733e-102">Como: Evitar a adição e a exclusão de linha no controle DataGridView do Windows Forms usando o designer</span><span class="sxs-lookup"><span data-stu-id="b733e-102">How to: Prevent Row Addition and Deletion in the Windows Forms DataGridView Control Using the Designer</span></span>
<span data-ttu-id="b733e-103">Às vezes, você desejará impedir que os usuários insiram novas linhas de dados ou exclua linhas existentes no seu <xref:System.Windows.Forms.DataGridView> controle.</span><span class="sxs-lookup"><span data-stu-id="b733e-103">Sometimes you will want to prevent users from entering new rows of data or deleting existing rows in your <xref:System.Windows.Forms.DataGridView> control.</span></span> <span data-ttu-id="b733e-104">Novas linhas são inseridas na linha especial para novos registros na parte inferior do controle.</span><span class="sxs-lookup"><span data-stu-id="b733e-104">New rows are entered in the special row for new records at the bottom of the control.</span></span> <span data-ttu-id="b733e-105">Quando você desabilitar a adição de linha, a linha para novos registros não será exibida.</span><span class="sxs-lookup"><span data-stu-id="b733e-105">When you disable row addition, the row for new records is not displayed.</span></span> <span data-ttu-id="b733e-106">Em seguida, você pode deixar o controle totalmente somente leitura desabilitando a exclusão de linha e a edição de célula.</span><span class="sxs-lookup"><span data-stu-id="b733e-106">You can then make the control entirely read-only by disabling row deletion and cell editing.</span></span>

 <span data-ttu-id="b733e-107">O procedimento a seguir requer um projeto de **aplicativo do Windows** com um <xref:System.Windows.Forms.DataGridView> formulário que contém um controle.</span><span class="sxs-lookup"><span data-stu-id="b733e-107">The following procedure requires a **Windows Application** project with a form containing a <xref:System.Windows.Forms.DataGridView> control.</span></span> <span data-ttu-id="b733e-108">Para obter informações sobre como configurar esse projeto, consulte [como: Crie um projeto](/visualstudio/ide/step-1-create-a-windows-forms-application-project) de aplicativo Windows Forms [e como: Adicione controles a Windows Forms](how-to-add-controls-to-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="b733e-108">For information about setting up such a project, see [How to: Create a Windows Forms application project](/visualstudio/ide/step-1-create-a-windows-forms-application-project) and [How to: Add Controls to Windows Forms](how-to-add-controls-to-windows-forms.md).</span></span>

## <a name="to-prevent-row-addition-and-deletion"></a><span data-ttu-id="b733e-109">Para evitar a exclusão e adição de linha</span><span class="sxs-lookup"><span data-stu-id="b733e-109">To prevent row addition and deletion</span></span>

- <span data-ttu-id="b733e-110">Clique no glifo de marca inteligente (![glifo de marca inteligente](./media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph")) no <xref:System.Windows.Forms.DataGridView> canto superior direito do controle e desmarque as caixas de seleção **habilitar adição** e **Habilitar exclusão** .</span><span class="sxs-lookup"><span data-stu-id="b733e-110">Click the smart tag glyph (![Smart Tag Glyph](./media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph")) on the upper-right corner of the <xref:System.Windows.Forms.DataGridView> control, and then clear the **Enable Adding** and **Enable Deleting** check boxes.</span></span>

    > [!NOTE]
    >  <span data-ttu-id="b733e-111">Para tornar o controle somente leitura inteiramente, desmarque também a caixa de seleção **Habilitar Edição**.</span><span class="sxs-lookup"><span data-stu-id="b733e-111">To make the control entirely read-only, clear the **Enable Editing** check box as well.</span></span>

## <a name="see-also"></a><span data-ttu-id="b733e-112">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b733e-112">See also</span></span>

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridView.AllowUserToAddRows%2A?displayProperty=nameWithType>
- [<span data-ttu-id="b733e-113">Como: Criar um projeto de aplicativo do Windows Forms</span><span class="sxs-lookup"><span data-stu-id="b733e-113">How to: Create a Windows Forms application project</span></span>](/visualstudio/ide/step-1-create-a-windows-forms-application-project)
- [<span data-ttu-id="b733e-114">Como: Adicionar controles a Windows Forms</span><span class="sxs-lookup"><span data-stu-id="b733e-114">How to: Add Controls to Windows Forms</span></span>](how-to-add-controls-to-windows-forms.md)
