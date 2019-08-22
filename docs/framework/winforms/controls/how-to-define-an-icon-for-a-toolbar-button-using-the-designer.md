---
title: 'Como: Definir um ícone para um botão de barra de ferramentas usando o Designer'
ms.date: 03/30/2017
helpviewer_keywords:
- toolbars [Windows Forms], adding icons to buttons
- examples [Windows Forms], toolbars
- images [Windows Forms], toolbar buttons
- buttons [Windows Forms], images
- icons [Windows Forms], toolbar buttons
- ToolBar control [Windows Forms], adding icons to buttons
ms.assetid: d848f38e-67f2-49d4-8e88-01c845c06c02
ms.openlocfilehash: 49e93f12bebbf409e6b3a06634556b9103c85f44
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/21/2019
ms.locfileid: "69666198"
---
# <a name="how-to-define-an-icon-for-a-toolbar-button-using-the-designer"></a><span data-ttu-id="a25e8-102">Como: Definir um ícone para um botão de barra de ferramentas usando o Designer</span><span class="sxs-lookup"><span data-stu-id="a25e8-102">How to: Define an Icon for a ToolBar Button Using the Designer</span></span>

> [!NOTE]
> <span data-ttu-id="a25e8-103">O controle <xref:System.Windows.Forms.ToolStrip> substitui e adiciona funcionalidade ao controle <xref:System.Windows.Forms.ToolBar>, no entanto, o controle <xref:System.Windows.Forms.ToolBar> é mantido para compatibilidade com versões anteriores e para uso futuro, se desejado.</span><span class="sxs-lookup"><span data-stu-id="a25e8-103">The <xref:System.Windows.Forms.ToolStrip> control replaces and adds functionality to the <xref:System.Windows.Forms.ToolBar> control; however, the <xref:System.Windows.Forms.ToolBar> control is retained for both backward compatibility and future use, if you choose.</span></span>

<span data-ttu-id="a25e8-104"><xref:System.Windows.Forms.ToolBar>os botões podem exibir ícones dentro deles para facilitar a identificação pelos usuários.</span><span class="sxs-lookup"><span data-stu-id="a25e8-104"><xref:System.Windows.Forms.ToolBar> buttons are able to display icons within them for easy identification by users.</span></span> <span data-ttu-id="a25e8-105">Isso é obtido por meio da <xref:System.Windows.Forms.ImageList> <xref:System.Windows.Forms.ToolBar> adição de imagens ao componente e sua associação ao controle.</span><span class="sxs-lookup"><span data-stu-id="a25e8-105">This is achieved through adding images to the <xref:System.Windows.Forms.ImageList> component and associating it with the <xref:System.Windows.Forms.ToolBar> control.</span></span>

<span data-ttu-id="a25e8-106">O procedimento a seguir requer um projeto de **aplicativo do Windows** com um <xref:System.Windows.Forms.ToolBar> formulário que contém <xref:System.Windows.Forms.ImageList> um controle e um componente.</span><span class="sxs-lookup"><span data-stu-id="a25e8-106">The following procedure requires a **Windows Application** project with a form containing a <xref:System.Windows.Forms.ToolBar> control and an <xref:System.Windows.Forms.ImageList> component.</span></span> <span data-ttu-id="a25e8-107">Para obter informações sobre como configurar esse projeto, consulte [como: Crie um projeto](/visualstudio/ide/step-1-create-a-windows-forms-application-project) de aplicativo Windows Forms [e como: Adicione controles a Windows Forms](how-to-add-controls-to-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="a25e8-107">For information about setting up such a project, see [How to: Create a Windows Forms application project](/visualstudio/ide/step-1-create-a-windows-forms-application-project) and [How to: Add Controls to Windows Forms](how-to-add-controls-to-windows-forms.md).</span></span>

### <a name="to-set-an-icon-for-a-toolbar-button-at-design-time"></a><span data-ttu-id="a25e8-108">Para definir um ícone para um botão de barra de ferramentas em tempo de design</span><span class="sxs-lookup"><span data-stu-id="a25e8-108">To set an icon for a toolbar button at design time</span></span>

1. <span data-ttu-id="a25e8-109">Adicione imagens ao <xref:System.Windows.Forms.ImageList> componente.</span><span class="sxs-lookup"><span data-stu-id="a25e8-109">Add images to the <xref:System.Windows.Forms.ImageList> component.</span></span> <span data-ttu-id="a25e8-110">Para obter mais informações, confira [Como: Adicione ou remova imagens ImageList com o designer](how-to-add-or-remove-imagelist-images-with-the-designer.md).</span><span class="sxs-lookup"><span data-stu-id="a25e8-110">For more information, see [How to: Add or Remove ImageList Images with the Designer](how-to-add-or-remove-imagelist-images-with-the-designer.md).</span></span>

2. <span data-ttu-id="a25e8-111">Selecione o <xref:System.Windows.Forms.ToolBar> controle no formulário.</span><span class="sxs-lookup"><span data-stu-id="a25e8-111">Select the <xref:System.Windows.Forms.ToolBar> control on your form.</span></span>

3. <span data-ttu-id="a25e8-112">Na janela **Propriedades** , defina a <xref:System.Windows.Forms.ToolBar> Propriedade do <xref:System.Windows.Forms.ToolBar.ImageList%2A> controle para o <xref:System.Windows.Forms.ImageList> componente.</span><span class="sxs-lookup"><span data-stu-id="a25e8-112">In the **Properties** window, set the <xref:System.Windows.Forms.ToolBar> control's <xref:System.Windows.Forms.ToolBar.ImageList%2A> property to the <xref:System.Windows.Forms.ImageList> component.</span></span>

4. <span data-ttu-id="a25e8-113">Clique na <xref:System.Windows.Forms.ToolBar> Propriedade do <xref:System.Windows.Forms.ToolBar.Buttons%2A> controle para selecioná-la e clique nas reticências![(o botão de reticências (...) no botão janela Propriedades do](./media/visual-studio-ellipsis-button.png)Visual Studio.) para abrir o **Editor de coleção ToolBarButton**.</span><span class="sxs-lookup"><span data-stu-id="a25e8-113">Click the <xref:System.Windows.Forms.ToolBar> control's <xref:System.Windows.Forms.ToolBar.Buttons%2A> property to select it, and click the ellipsis (![The Ellipsis button (...) in the Properties window of Visual Studio.](./media/visual-studio-ellipsis-button.png)) button to open the **ToolBarButton Collection Editor**.</span></span>

5. <span data-ttu-id="a25e8-114">Use o botão **Adicionar** para adicionar botões ao <xref:System.Windows.Forms.ToolBar> controle.</span><span class="sxs-lookup"><span data-stu-id="a25e8-114">Use the **Add** button to add buttons to the <xref:System.Windows.Forms.ToolBar> control.</span></span>

6. <span data-ttu-id="a25e8-115">Na janela **Propriedades** que aparece no painel no lado direito do **Editor de coleção ToolBarButton**, defina a <xref:System.Windows.Forms.ToolBarButton.ImageIndex%2A> propriedade de cada botão da barra de ferramentas como um dos valores na lista, que é desenhado a partir das imagens que você adicionou ao <xref:System.Windows.Forms.ImageList> do componente.</span><span class="sxs-lookup"><span data-stu-id="a25e8-115">In the **Properties** window that appears in the pane on the right side of the **ToolBarButton Collection Editor**, set the <xref:System.Windows.Forms.ToolBarButton.ImageIndex%2A> property of each toolbar button to one of the values in the list, which is drawn from the images you added to the <xref:System.Windows.Forms.ImageList> component.</span></span>

## <a name="see-also"></a><span data-ttu-id="a25e8-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a25e8-116">See also</span></span>

- <xref:System.Windows.Forms.ToolBar>
- [<span data-ttu-id="a25e8-117">Como: Eventos do menu disparar para botões da barra de ferramentas</span><span class="sxs-lookup"><span data-stu-id="a25e8-117">How to: Trigger Menu Events for Toolbar Buttons</span></span>](how-to-trigger-menu-events-for-toolbar-buttons.md)
- [<span data-ttu-id="a25e8-118">Controle de barra de ferramentas</span><span class="sxs-lookup"><span data-stu-id="a25e8-118">ToolBar Control</span></span>](toolbar-control-windows-forms.md)
- [<span data-ttu-id="a25e8-119">Componente ImageList</span><span class="sxs-lookup"><span data-stu-id="a25e8-119">ImageList Component</span></span>](imagelist-component-windows-forms.md)
