---
title: 'Como: Adicionar e remover itens com o controle ListView do Windows Forms usando o Designer'
ms.date: 03/30/2017
helpviewer_keywords:
- ListView control [Windows Forms], populating
- ListView control [Windows Forms], adding list items
ms.assetid: 217611ee-fd11-4d39-9a54-a37c3e781be1
ms.openlocfilehash: 6e08a7013242b0dbb433e288c4f8d788cb4e143b
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59343838"
---
# <a name="how-to-add-and-remove-items-with-the-windows-forms-listview-control-using-the-designer"></a><span data-ttu-id="a5fa1-102">Como: Adicionar e remover itens com o controle ListView do Windows Forms usando o Designer</span><span class="sxs-lookup"><span data-stu-id="a5fa1-102">How to: Add and Remove Items with the Windows Forms ListView Control Using the Designer</span></span>
<span data-ttu-id="a5fa1-103">O processo de adicionar um item em um Windows Forms <xref:System.Windows.Forms.ListView> controle consiste principalmente de especificar o item e atribuir propriedades a ele.</span><span class="sxs-lookup"><span data-stu-id="a5fa1-103">The process of adding an item to a Windows Forms <xref:System.Windows.Forms.ListView> control consists primarily of specifying the item and assigning properties to it.</span></span> <span data-ttu-id="a5fa1-104">A adição ou remoção de itens de lista pode ser feita a qualquer momento.</span><span class="sxs-lookup"><span data-stu-id="a5fa1-104">Adding or removing list items can be done at any time.</span></span>  
  
 <span data-ttu-id="a5fa1-105">O procedimento a seguir exige um **aplicativo do Windows** projeto com um formulário que contém um <xref:System.Windows.Forms.ListView> controle.</span><span class="sxs-lookup"><span data-stu-id="a5fa1-105">The following procedure requires a **Windows Application** project with a form containing a <xref:System.Windows.Forms.ListView> control.</span></span> <span data-ttu-id="a5fa1-106">Para obter informações sobre como configurar um projeto desse tipo, consulte [como: Criar um projeto de aplicativo do Windows Forms](/visualstudio/ide/step-1-create-a-windows-forms-application-project) e [como: Adicionar controles ao Windows Forms](how-to-add-controls-to-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="a5fa1-106">For information about setting up such a project, see [How to: Create a Windows Forms application project](/visualstudio/ide/step-1-create-a-windows-forms-application-project) and [How to: Add Controls to Windows Forms](how-to-add-controls-to-windows-forms.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="a5fa1-107">As caixas de diálogo e os comandos de menu que você vê podem ser diferentes dos descritos na Ajuda, dependendo da sua edição ou das configurações ativas.</span><span class="sxs-lookup"><span data-stu-id="a5fa1-107">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="a5fa1-108">Para alterar as configurações, escolha **Importar e Exportar Configurações** no menu **Ferramentas**.</span><span class="sxs-lookup"><span data-stu-id="a5fa1-108">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="a5fa1-109">Para obter mais informações, confira [Personalizar o IDE do Visual Studio](/visualstudio/ide/personalizing-the-visual-studio-ide).</span><span class="sxs-lookup"><span data-stu-id="a5fa1-109">For more information, see [Personalize the Visual Studio IDE](/visualstudio/ide/personalizing-the-visual-studio-ide).</span></span>  
  
### <a name="to-add-or-remove-items-using-the-designer"></a><span data-ttu-id="a5fa1-110">Para adicionar ou remover itens usando o designer</span><span class="sxs-lookup"><span data-stu-id="a5fa1-110">To add or remove items using the designer</span></span>  
  
1. <span data-ttu-id="a5fa1-111">Selecione o <xref:System.Windows.Forms.ListView> controle.</span><span class="sxs-lookup"><span data-stu-id="a5fa1-111">Select the <xref:System.Windows.Forms.ListView> control.</span></span>  
  
2. <span data-ttu-id="a5fa1-112">No **propriedades** janela, clique no **reticências** (![captura de tela de VisualStudioEllipsesButton](../media/vbellipsesbutton.png "vbEllipsesButton")) lado o <xref:System.Windows.Forms.ListView.Items%2A> propriedade.</span><span class="sxs-lookup"><span data-stu-id="a5fa1-112">In the **Properties** window, click the **Ellipsis** (![VisualStudioEllipsesButton screenshot](../media/vbellipsesbutton.png "vbEllipsesButton")) button next to the <xref:System.Windows.Forms.ListView.Items%2A> property.</span></span>  
  
     <span data-ttu-id="a5fa1-113">O **Editor de coleção de ListViewItem** é exibido.</span><span class="sxs-lookup"><span data-stu-id="a5fa1-113">The **ListViewItem Collection Editor** appears.</span></span>  
  
3. <span data-ttu-id="a5fa1-114">Para adicionar um item, clique no botão **Adicionar**.</span><span class="sxs-lookup"><span data-stu-id="a5fa1-114">To add an item, click the **Add** button.</span></span> <span data-ttu-id="a5fa1-115">Você pode definir as propriedades do novo item, como o <xref:System.Windows.Forms.ListView.Text%2A> e <xref:System.Windows.Forms.ListViewItem.ImageIndex%2A> propriedades.</span><span class="sxs-lookup"><span data-stu-id="a5fa1-115">You can then set properties of the new item, such as the <xref:System.Windows.Forms.ListView.Text%2A> and <xref:System.Windows.Forms.ListViewItem.ImageIndex%2A> properties.</span></span>  
  
4. <span data-ttu-id="a5fa1-116">Para remover um item, selecione-o e clique no botão **Remover**.</span><span class="sxs-lookup"><span data-stu-id="a5fa1-116">To remove an item, select it and click the **Remove** button.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a5fa1-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a5fa1-117">See also</span></span>

- [<span data-ttu-id="a5fa1-118">Visão geral do controle ListView</span><span class="sxs-lookup"><span data-stu-id="a5fa1-118">ListView Control Overview</span></span>](listview-control-overview-windows-forms.md)
- [<span data-ttu-id="a5fa1-119">Como: Adicionar colunas para o controle ListView do Windows Forms</span><span class="sxs-lookup"><span data-stu-id="a5fa1-119">How to: Add Columns to the Windows Forms ListView Control</span></span>](how-to-add-columns-to-the-windows-forms-listview-control.md)
- [<span data-ttu-id="a5fa1-120">Como: Exibir subitens em colunas com o controle ListView do Windows Forms</span><span class="sxs-lookup"><span data-stu-id="a5fa1-120">How to: Display Subitems in Columns with the Windows Forms ListView Control</span></span>](how-to-display-subitems-in-columns-with-the-windows-forms-listview-control.md)
- [<span data-ttu-id="a5fa1-121">Como: Exibir ícones para o controle ListView do Windows Forms</span><span class="sxs-lookup"><span data-stu-id="a5fa1-121">How to: Display Icons for the Windows Forms ListView Control</span></span>](how-to-display-icons-for-the-windows-forms-listview-control.md)
- [<span data-ttu-id="a5fa1-122">Como: Adicionar informações personalizadas a um controle TreeView ou ListView (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="a5fa1-122">How to: Add Custom Information to a TreeView or ListView Control (Windows Forms)</span></span>](add-custom-information-to-a-treeview-or-listview-control-wf.md)
- [<span data-ttu-id="a5fa1-123">Como: Agrupar itens em um controle ListView dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="a5fa1-123">How to: Group Items in a Windows Forms ListView Control</span></span>](how-to-group-items-in-a-windows-forms-listview-control.md)
