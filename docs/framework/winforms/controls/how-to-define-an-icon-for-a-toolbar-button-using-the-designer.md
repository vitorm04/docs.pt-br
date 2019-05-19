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
ms.openlocfilehash: f8fe28a7827c0f69f80a3078d604b1818f4134ac
ms.sourcegitcommit: c4e9d05644c9cb89de5ce6002723de107ea2e2c4
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/19/2019
ms.locfileid: "65877418"
---
# <a name="how-to-define-an-icon-for-a-toolbar-button-using-the-designer"></a><span data-ttu-id="b8f07-102">Como: Definir um ícone para um botão de barra de ferramentas usando o Designer</span><span class="sxs-lookup"><span data-stu-id="b8f07-102">How to: Define an Icon for a ToolBar Button Using the Designer</span></span>
> [!NOTE]
>  <span data-ttu-id="b8f07-103">O controle <xref:System.Windows.Forms.ToolStrip> substitui e adiciona funcionalidade ao controle <xref:System.Windows.Forms.ToolBar>, no entanto, o controle <xref:System.Windows.Forms.ToolBar> é mantido para compatibilidade com versões anteriores e para uso futuro, se desejado.</span><span class="sxs-lookup"><span data-stu-id="b8f07-103">The <xref:System.Windows.Forms.ToolStrip> control replaces and adds functionality to the <xref:System.Windows.Forms.ToolBar> control; however, the <xref:System.Windows.Forms.ToolBar> control is retained for both backward compatibility and future use, if you choose.</span></span>  
  
 <span data-ttu-id="b8f07-104"><xref:System.Windows.Forms.ToolBar> botões são capazes de exibir ícones dentro deles para facilitar a identificação pelos usuários.</span><span class="sxs-lookup"><span data-stu-id="b8f07-104"><xref:System.Windows.Forms.ToolBar> buttons are able to display icons within them for easy identification by users.</span></span> <span data-ttu-id="b8f07-105">Isso é feito pela adição de imagens para o <xref:System.Windows.Forms.ImageList> componente e associá-lo com o <xref:System.Windows.Forms.ToolBar> controle.</span><span class="sxs-lookup"><span data-stu-id="b8f07-105">This is achieved through adding images to the <xref:System.Windows.Forms.ImageList> component and associating it with the <xref:System.Windows.Forms.ToolBar> control.</span></span>  
  
 <span data-ttu-id="b8f07-106">O procedimento a seguir exige um **aplicativo do Windows** projeto com um formulário que contém uma <xref:System.Windows.Forms.ToolBar> controle e um <xref:System.Windows.Forms.ImageList> componente.</span><span class="sxs-lookup"><span data-stu-id="b8f07-106">The following procedure requires a **Windows Application** project with a form containing a <xref:System.Windows.Forms.ToolBar> control and an <xref:System.Windows.Forms.ImageList> component.</span></span> <span data-ttu-id="b8f07-107">Para obter informações sobre como configurar um projeto desse tipo, consulte [como: Criar um projeto de aplicativo do Windows Forms](/visualstudio/ide/step-1-create-a-windows-forms-application-project) e [como: Adicionar controles ao Windows Forms](how-to-add-controls-to-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="b8f07-107">For information about setting up such a project, see [How to: Create a Windows Forms application project](/visualstudio/ide/step-1-create-a-windows-forms-application-project) and [How to: Add Controls to Windows Forms](how-to-add-controls-to-windows-forms.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b8f07-108">As caixas de diálogo e os comandos de menu que você vê podem ser diferentes dos descritos na Ajuda, dependendo da sua edição ou das configurações ativas.</span><span class="sxs-lookup"><span data-stu-id="b8f07-108">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="b8f07-109">Para alterar as configurações, escolha **Importar e Exportar Configurações** no menu **Ferramentas**.</span><span class="sxs-lookup"><span data-stu-id="b8f07-109">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="b8f07-110">Para obter mais informações, confira [Personalizar o IDE do Visual Studio](/visualstudio/ide/personalizing-the-visual-studio-ide).</span><span class="sxs-lookup"><span data-stu-id="b8f07-110">For more information, see [Personalize the Visual Studio IDE](/visualstudio/ide/personalizing-the-visual-studio-ide).</span></span>  
  
### <a name="to-set-an-icon-for-a-toolbar-button-at-design-time"></a><span data-ttu-id="b8f07-111">Para definir um ícone para um botão de barra de ferramentas em tempo de design</span><span class="sxs-lookup"><span data-stu-id="b8f07-111">To set an icon for a toolbar button at design time</span></span>  
  
1. <span data-ttu-id="b8f07-112">Adicionar imagens para o <xref:System.Windows.Forms.ImageList> componente.</span><span class="sxs-lookup"><span data-stu-id="b8f07-112">Add images to the <xref:System.Windows.Forms.ImageList> component.</span></span> <span data-ttu-id="b8f07-113">Para obter mais informações, confira [Como: Adicionar ou remover imagens ImageList com o Designer](how-to-add-or-remove-imagelist-images-with-the-designer.md).</span><span class="sxs-lookup"><span data-stu-id="b8f07-113">For more information, see [How to: Add or Remove ImageList Images with the Designer](how-to-add-or-remove-imagelist-images-with-the-designer.md).</span></span>  
  
2. <span data-ttu-id="b8f07-114">Selecione o <xref:System.Windows.Forms.ToolBar> controle no formulário.</span><span class="sxs-lookup"><span data-stu-id="b8f07-114">Select the <xref:System.Windows.Forms.ToolBar> control on your form.</span></span>  
  
3. <span data-ttu-id="b8f07-115">No **propriedades** janela, defina as <xref:System.Windows.Forms.ToolBar> do controle <xref:System.Windows.Forms.ToolBar.ImageList%2A> propriedade para o <xref:System.Windows.Forms.ImageList> componente.</span><span class="sxs-lookup"><span data-stu-id="b8f07-115">In the **Properties** window, set the <xref:System.Windows.Forms.ToolBar> control's <xref:System.Windows.Forms.ToolBar.ImageList%2A> property to the <xref:System.Windows.Forms.ImageList> component.</span></span>  
  
4.  <span data-ttu-id="b8f07-116">Clique o <xref:System.Windows.Forms.ToolBar> do controle <xref:System.Windows.Forms.ToolBar.Buttons%2A> propriedade para selecioná-lo e, em seguida, clique nas reticências (![o botão (...) na janela Propriedades do Visual Studio.](./media/visual-studio-ellipsis-button.png)) para abrir o **coleção ToolBarButton Editor de**.</span><span class="sxs-lookup"><span data-stu-id="b8f07-116">Click the <xref:System.Windows.Forms.ToolBar> control's <xref:System.Windows.Forms.ToolBar.Buttons%2A> property to select it, and click the ellipsis (![The Ellipsis button (...) in the Properties window of Visual Studio.](./media/visual-studio-ellipsis-button.png)) button to open the **ToolBarButton Collection Editor**.</span></span>  
  
5. <span data-ttu-id="b8f07-117">Use o **Add** botão para adicionar botões a serem o <xref:System.Windows.Forms.ToolBar> controle.</span><span class="sxs-lookup"><span data-stu-id="b8f07-117">Use the **Add** button to add buttons to the <xref:System.Windows.Forms.ToolBar> control.</span></span>  
  
6. <span data-ttu-id="b8f07-118">No **propriedades** janela que aparece no painel à direita do **Editor de coleção ToolBarButton**, defina o <xref:System.Windows.Forms.ToolBarButton.ImageIndex%2A> propriedade de cada botão de barra de ferramentas para um dos valores na lista, que é desenhada entre as imagens que você adicionou ao <xref:System.Windows.Forms.ImageList> componente.</span><span class="sxs-lookup"><span data-stu-id="b8f07-118">In the **Properties** window that appears in the pane on the right side of the **ToolBarButton Collection Editor**, set the <xref:System.Windows.Forms.ToolBarButton.ImageIndex%2A> property of each toolbar button to one of the values in the list, which is drawn from the images you added to the <xref:System.Windows.Forms.ImageList> component.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b8f07-119">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b8f07-119">See also</span></span>

- <xref:System.Windows.Forms.ToolBar>
- [<span data-ttu-id="b8f07-120">Como: Disparar eventos de Menu para botões da barra de ferramentas</span><span class="sxs-lookup"><span data-stu-id="b8f07-120">How to: Trigger Menu Events for Toolbar Buttons</span></span>](how-to-trigger-menu-events-for-toolbar-buttons.md)
- [<span data-ttu-id="b8f07-121">Controle de barra de ferramentas</span><span class="sxs-lookup"><span data-stu-id="b8f07-121">ToolBar Control</span></span>](toolbar-control-windows-forms.md)
- [<span data-ttu-id="b8f07-122">Componente ImageList</span><span class="sxs-lookup"><span data-stu-id="b8f07-122">ImageList Component</span></span>](imagelist-component-windows-forms.md)
