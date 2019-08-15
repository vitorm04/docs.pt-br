---
title: 'Como: Adicionar colunas ao controle ListView do Windows Forms usando o Designer'
ms.date: 03/30/2017
helpviewer_keywords:
- ListView control [Windows Forms], adding column headers
- columns [Windows Forms], adding to ListView controls
ms.assetid: 5b1a8b4d-587e-479a-95c1-f9b90884f13a
ms.openlocfilehash: e82fbcf63047873ebc6e5c40b8b9fbeb14a672e5
ms.sourcegitcommit: cf9515122fce716bcfb6618ba366e39b5a2eb81e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/15/2019
ms.locfileid: "69038175"
---
# <a name="how-to-add-columns-to-the-windows-forms-listview-control-using-the-designer"></a><span data-ttu-id="fc239-102">Como: Adicionar colunas ao controle ListView do Windows Forms usando o Designer</span><span class="sxs-lookup"><span data-stu-id="fc239-102">How to: Add Columns to the Windows Forms ListView Control Using the Designer</span></span>

<span data-ttu-id="fc239-103">O controle <xref:System.Windows.Forms.ListView> Windows Forms pode exibir várias colunas para cada item de lista quando estiver na exibição de **detalhes** .</span><span class="sxs-lookup"><span data-stu-id="fc239-103">The Windows Forms <xref:System.Windows.Forms.ListView> control can display multiple columns for each list item when in the **Details** view.</span></span> <span data-ttu-id="fc239-104">Você pode usar as colunas para exibir vários tipos de informações sobre cada item de lista.</span><span class="sxs-lookup"><span data-stu-id="fc239-104">You can use the columns to display several types of information about each list item.</span></span> <span data-ttu-id="fc239-105">Por exemplo, uma lista de arquivos pode exibir o nome do arquivo, tipo de arquivo, tamanho e data da última modificação do arquivo.</span><span class="sxs-lookup"><span data-stu-id="fc239-105">For example, a list of files could display the file name, file type, size, and date the file was last modified.</span></span> <span data-ttu-id="fc239-106">Para obter informações sobre como preencher as colunas depois que elas são [criadas, consulte Como: Exibir subitens em colunas com o controle](how-to-display-subitems-in-columns-with-the-windows-forms-listview-control.md)ListView Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="fc239-106">For information on populating the columns once they are created, see [How to: Display Subitems in Columns with the Windows Forms ListView Control](how-to-display-subitems-in-columns-with-the-windows-forms-listview-control.md).</span></span>

<span data-ttu-id="fc239-107">O procedimento a seguir requer um projeto de **aplicativo do Windows** com um <xref:System.Windows.Forms.ListView> formulário que contém um controle.</span><span class="sxs-lookup"><span data-stu-id="fc239-107">The following procedure requires a **Windows Application** project with a form containing a <xref:System.Windows.Forms.ListView> control.</span></span> <span data-ttu-id="fc239-108">Para obter informações sobre como configurar esse projeto, consulte [como: Crie um projeto](/visualstudio/ide/step-1-create-a-windows-forms-application-project) de aplicativo Windows Forms [e como: Adicione controles a Windows Forms](how-to-add-controls-to-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="fc239-108">For information about setting up such a project, see [How to: Create a Windows Forms application project](/visualstudio/ide/step-1-create-a-windows-forms-application-project) and [How to: Add Controls to Windows Forms](how-to-add-controls-to-windows-forms.md).</span></span>


### <a name="to-add-columns-in-the-designer"></a><span data-ttu-id="fc239-109">Para adicionar colunas no designer</span><span class="sxs-lookup"><span data-stu-id="fc239-109">To add columns in the designer</span></span>

1. <span data-ttu-id="fc239-110">Na janela **Propriedades** , defina a propriedade do <xref:System.Windows.Forms.ListView.View%2A> controle como. <xref:System.Windows.Forms.View.Details></span><span class="sxs-lookup"><span data-stu-id="fc239-110">In the **Properties** window, set the control's <xref:System.Windows.Forms.ListView.View%2A> property to <xref:System.Windows.Forms.View.Details>.</span></span>

2. <span data-ttu-id="fc239-111">Na janela **Propriedades** , clique no botão de reticências![(o botão de reticências (...) na janela Propriedades do Visual](./media/visual-studio-ellipsis-button.png)Studio.) ao <xref:System.Windows.Forms.ListView.Columns%2A> lado da propriedade.</span><span class="sxs-lookup"><span data-stu-id="fc239-111">In the **Properties** window, click the **Ellipsis** button (![The Ellipsis button (...) in the Properties window of Visual Studio.](./media/visual-studio-ellipsis-button.png)) next to the <xref:System.Windows.Forms.ListView.Columns%2A> property.</span></span>

     <span data-ttu-id="fc239-112">O **Editor de coleção ColumnHeader** é exibido.</span><span class="sxs-lookup"><span data-stu-id="fc239-112">The **ColumnHeader Collection Editor** appears.</span></span>

3. <span data-ttu-id="fc239-113">Use o botão **Adicionar** para adicionar novas colunas.</span><span class="sxs-lookup"><span data-stu-id="fc239-113">Use the **Add** button to add new columns.</span></span> <span data-ttu-id="fc239-114">Em seguida, você pode selecionar o cabeçalho da coluna e definir seu texto (a legenda da coluna), o alinhamento do texto e a largura.</span><span class="sxs-lookup"><span data-stu-id="fc239-114">You can then select the column header and set its text (the caption of the column), text alignment, and width.</span></span>

## <a name="see-also"></a><span data-ttu-id="fc239-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="fc239-115">See also</span></span>

- [<span data-ttu-id="fc239-116">Visão geral do controle ListView</span><span class="sxs-lookup"><span data-stu-id="fc239-116">ListView Control Overview</span></span>](listview-control-overview-windows-forms.md)
- [<span data-ttu-id="fc239-117">Como: Adicionar e remover itens com o controle Windows Forms ListView</span><span class="sxs-lookup"><span data-stu-id="fc239-117">How to: Add and Remove Items with the Windows Forms ListView Control</span></span>](how-to-add-and-remove-items-with-the-windows-forms-listview-control.md)
- [<span data-ttu-id="fc239-118">Como: Exibir subitens em colunas com o controle ListView Windows Forms</span><span class="sxs-lookup"><span data-stu-id="fc239-118">How to: Display Subitems in Columns with the Windows Forms ListView Control</span></span>](how-to-display-subitems-in-columns-with-the-windows-forms-listview-control.md)
- [<span data-ttu-id="fc239-119">Como: Exibir ícones para o controle Windows Forms ListView</span><span class="sxs-lookup"><span data-stu-id="fc239-119">How to: Display Icons for the Windows Forms ListView Control</span></span>](how-to-display-icons-for-the-windows-forms-listview-control.md)
- [<span data-ttu-id="fc239-120">Como: Adicionar informações personalizadas a um controle TreeView ou ListView (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="fc239-120">How to: Add Custom Information to a TreeView or ListView Control (Windows Forms)</span></span>](add-custom-information-to-a-treeview-or-listview-control-wf.md)
