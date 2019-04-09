---
title: 'Como: Ancorar controles nos Windows Forms'
ms.date: 03/30/2017
helpviewer_keywords:
- Anchor property [Windows Forms], enabling resizable forms
- Windows Forms controls, screen resolutions
- resizing forms [Windows Forms]
- Windows Forms controls, size
- screen resolution and control display
- controls [Windows Forms], anchoring
- forms [Windows Forms], resizing
- Windows Forms, resizing
- controls [Windows Forms], positioning
ms.assetid: 59ea914f-fbd3-427a-80fe-decd02f7ae6d
ms.openlocfilehash: 28cee4e1aa989ef4df902907c09645a1a0400475
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59072982"
---
# <a name="how-to-anchor-controls-on-windows-forms"></a><span data-ttu-id="f3d17-102">Como: Ancorar controles nos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="f3d17-102">How to: Anchor Controls on Windows Forms</span></span>
<span data-ttu-id="f3d17-103">Se você estiver criando um formulário que o usuário pode redimensionar em tempo de execução, os controles no formulário deverão redimensionados e reposicionados corretamente.</span><span class="sxs-lookup"><span data-stu-id="f3d17-103">If you are designing a form that the user can resize at run time, the controls on your form should resize and reposition properly.</span></span> <span data-ttu-id="f3d17-104">Para redimensionar controles dinamicamente com o formulário, você pode usar o <xref:System.Windows.Forms.Control.Anchor%2A> propriedade dos controles dos Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="f3d17-104">To resize controls dynamically with the form, you can use the <xref:System.Windows.Forms.Control.Anchor%2A> property of Windows Forms controls.</span></span> <span data-ttu-id="f3d17-105">O <xref:System.Windows.Forms.Control.Anchor%2A> propriedade define uma posição de âncora para o controle.</span><span class="sxs-lookup"><span data-stu-id="f3d17-105">The <xref:System.Windows.Forms.Control.Anchor%2A> property defines an anchor position for the control.</span></span> <span data-ttu-id="f3d17-106">Quando um controle é ancorado a um formulário e esse formulário é redimensionado, o controle mantém a distância entre o controle e as posições de âncora.</span><span class="sxs-lookup"><span data-stu-id="f3d17-106">When a control is anchored to a form and the form is resized, the control maintains the distance between the control and the anchor positions.</span></span> <span data-ttu-id="f3d17-107">Por exemplo, se você tiver um <xref:System.Windows.Forms.TextBox> controle é ancorado a esquerda, direita e bordas na parte inferior do formulário, como o formulário é redimensionado, o <xref:System.Windows.Forms.TextBox> controle é redimensionado horizontalmente, de modo que ele mantém a mesma distância dos lados direito e esquerdos do formulário.</span><span class="sxs-lookup"><span data-stu-id="f3d17-107">For example, if you have a <xref:System.Windows.Forms.TextBox> control that is anchored to the left, right, and bottom edges of the form, as the form is resized, the <xref:System.Windows.Forms.TextBox> control resizes horizontally so that it maintains the same distance from the right and left sides of the form.</span></span> <span data-ttu-id="f3d17-108">Além disso, o controle se posiciona verticalmente para que sua localização seja sempre a mesma distância da borda inferior do formulário.</span><span class="sxs-lookup"><span data-stu-id="f3d17-108">In addition, the control positions itself vertically so that its location is always the same distance from the bottom edge of the form.</span></span> <span data-ttu-id="f3d17-109">Se um controle não estiver ancorado e o formulário for redimensionado, a posição do controle em relação às bordas do formulário será alterada.</span><span class="sxs-lookup"><span data-stu-id="f3d17-109">If a control is not anchored and the form is resized, the position of the control relative to the edges of the form is changed.</span></span>  
  
 <span data-ttu-id="f3d17-110">O <xref:System.Windows.Forms.Control.Anchor%2A> propriedade interage com o <xref:System.Windows.Forms.Control.AutoSize%2A> propriedade.</span><span class="sxs-lookup"><span data-stu-id="f3d17-110">The <xref:System.Windows.Forms.Control.Anchor%2A> property interacts with the <xref:System.Windows.Forms.Control.AutoSize%2A> property.</span></span> <span data-ttu-id="f3d17-111">Para obter mais informações, consulte [Visão Geral da Propriedade AutoSize](autosize-property-overview.md).</span><span class="sxs-lookup"><span data-stu-id="f3d17-111">For more information, see [AutoSize Property Overview](autosize-property-overview.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="f3d17-112">As caixas de diálogo e os comandos de menu que você vê podem ser diferentes dos descritos na Ajuda, dependendo da sua edição ou das configurações ativas.</span><span class="sxs-lookup"><span data-stu-id="f3d17-112">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="f3d17-113">Para alterar as configurações, escolha **Importar e Exportar Configurações** no menu **Ferramentas**.</span><span class="sxs-lookup"><span data-stu-id="f3d17-113">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="f3d17-114">Para obter mais informações, confira [Personalizar o IDE do Visual Studio](/visualstudio/ide/personalizing-the-visual-studio-ide).</span><span class="sxs-lookup"><span data-stu-id="f3d17-114">For more information, see [Personalize the Visual Studio IDE](/visualstudio/ide/personalizing-the-visual-studio-ide).</span></span>  
  
### <a name="to-anchor-a-control-on-a-form"></a><span data-ttu-id="f3d17-115">Ancorar um controle em um formulário</span><span class="sxs-lookup"><span data-stu-id="f3d17-115">To anchor a control on a form</span></span>  
  
1.  <span data-ttu-id="f3d17-116">Selecione o controle que deseja ancorar.</span><span class="sxs-lookup"><span data-stu-id="f3d17-116">Select the control you want to anchor.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="f3d17-117">É possível ancorar vários controles simultaneamente pressionando a tecla CTRL, clicando em cada controle para selecioná-lo e, em seguida, seguindo o resto desse procedimento.</span><span class="sxs-lookup"><span data-stu-id="f3d17-117">You can anchor multiple controls simultaneously by pressing the CTRL key, clicking each control to select it, and then following the rest of this procedure.</span></span>  
  
2.  <span data-ttu-id="f3d17-118">No **propriedades** janela, clique na seta à direita do <xref:System.Windows.Forms.Control.Anchor%2A> propriedade.</span><span class="sxs-lookup"><span data-stu-id="f3d17-118">In the **Properties** window, click the arrow to the right of the <xref:System.Windows.Forms.Control.Anchor%2A> property.</span></span>  
  
     <span data-ttu-id="f3d17-119">Um editor será exibido e mostra uma cruz.</span><span class="sxs-lookup"><span data-stu-id="f3d17-119">An editor is displayed that shows a cross.</span></span>  
  
3.  <span data-ttu-id="f3d17-120">Para definir uma âncora, clique na seção superior, esquerda, direita ou inferior da cruz.</span><span class="sxs-lookup"><span data-stu-id="f3d17-120">To set an anchor, click the top, left, right, or bottom section of the cross.</span></span>  
  
     <span data-ttu-id="f3d17-121">Os controles estão ancorados na parte superior e esquerda por padrão.</span><span class="sxs-lookup"><span data-stu-id="f3d17-121">Controls are anchored to the top and left by default.</span></span>  
  
4.  <span data-ttu-id="f3d17-122">Para limpar um lado do controle que foi ancorado, clique nessa parte da cruz.</span><span class="sxs-lookup"><span data-stu-id="f3d17-122">To clear a side of the control that has been anchored, click that arm of the cross.</span></span>  
  
5.  <span data-ttu-id="f3d17-123">Para fechar o <xref:System.Windows.Forms.Control.Anchor%2A> editor de propriedades, clique no <xref:System.Windows.Forms.Control.Anchor%2A> novamente o nome da propriedade.</span><span class="sxs-lookup"><span data-stu-id="f3d17-123">To close the <xref:System.Windows.Forms.Control.Anchor%2A> property editor, click the <xref:System.Windows.Forms.Control.Anchor%2A> property name again.</span></span>  
  
 <span data-ttu-id="f3d17-124">Quando o formulário é exibido em tempo de execução, o controle é redimensionado para permanecer posicionado na mesma distância da borda do formulário.</span><span class="sxs-lookup"><span data-stu-id="f3d17-124">When your form is displayed at run time, the control resizes to remain positioned at the same distance from the edge of the form.</span></span> <span data-ttu-id="f3d17-125">A distância da borda ancorada sempre é a mesma distância definida quando o controle é posicionado no Designer de Formulários do Windows.</span><span class="sxs-lookup"><span data-stu-id="f3d17-125">The distance from the anchored edge always remains the same as the distance defined when the control is positioned in the Windows Forms Designer.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="f3d17-126">Alguns controles, como o <xref:System.Windows.Forms.ComboBox> , têm um limite de altura.</span><span class="sxs-lookup"><span data-stu-id="f3d17-126">Certain controls, such as the <xref:System.Windows.Forms.ComboBox> control, have a limit to their height.</span></span> <span data-ttu-id="f3d17-127">Ancorar o controle na parte inferior do formulário ou contêiner não pode forçar o controle a exceder o limite de altura.</span><span class="sxs-lookup"><span data-stu-id="f3d17-127">Anchoring the control to the bottom of its form or container cannot force the control to exceed its height limit.</span></span>  
  
 <span data-ttu-id="f3d17-128">Controles herdados devem ser `Protected` para serem ancorados.</span><span class="sxs-lookup"><span data-stu-id="f3d17-128">Inherited controls must be `Protected` to be able to be anchored.</span></span> <span data-ttu-id="f3d17-129">Para alterar o nível de acesso de um controle, defina sua propriedade `Modifiers` na janela **Propriedades**.</span><span class="sxs-lookup"><span data-stu-id="f3d17-129">To change the access level of a control, set its `Modifiers` property in the **Properties** window.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f3d17-130">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f3d17-130">See also</span></span>

- [<span data-ttu-id="f3d17-131">Controles de Windows Forms</span><span class="sxs-lookup"><span data-stu-id="f3d17-131">Windows Forms Controls</span></span>](index.md)
- [<span data-ttu-id="f3d17-132">Organizando controles nos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="f3d17-132">Arranging Controls on Windows Forms</span></span>](arranging-controls-on-windows-forms.md)
- [<span data-ttu-id="f3d17-133">Visão geral da propriedade AutoSize</span><span class="sxs-lookup"><span data-stu-id="f3d17-133">AutoSize Property Overview</span></span>](autosize-property-overview.md)
- [<span data-ttu-id="f3d17-134">Como: Encaixar controles nos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="f3d17-134">How to: Dock Controls on Windows Forms</span></span>](how-to-dock-controls-on-windows-forms.md)
- [<span data-ttu-id="f3d17-135">Passo a passo: Organizando controles nos Windows Forms utilizando um FlowLayoutPanel</span><span class="sxs-lookup"><span data-stu-id="f3d17-135">Walkthrough: Arranging Controls on Windows Forms Using a FlowLayoutPanel</span></span>](walkthrough-arranging-controls-on-windows-forms-using-a-flowlayoutpanel.md)
- [<span data-ttu-id="f3d17-136">Passo a passo: Organizar controles nos Windows Forms usando um TableLayoutPanel</span><span class="sxs-lookup"><span data-stu-id="f3d17-136">Walkthrough: Arranging Controls on Windows Forms Using a TableLayoutPanel</span></span>](walkthrough-arranging-controls-on-windows-forms-using-a-tablelayoutpanel.md)
- [<span data-ttu-id="f3d17-137">Passo a passo: Definir o layout de controles do Windows Forms com preenchimento, margens e a propriedade AutoSize</span><span class="sxs-lookup"><span data-stu-id="f3d17-137">Walkthrough: Laying Out Windows Forms Controls with Padding, Margins, and the AutoSize Property</span></span>](windows-forms-controls-padding-autosize.md)
