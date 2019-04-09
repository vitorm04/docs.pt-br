---
title: 'Como: Definir a tela de fundo de um painel do Windows Forms usando o Designer'
ms.date: 03/30/2017
helpviewer_keywords:
- background colors [Windows Forms], Windows Forms Panel controls
- background images [Windows Forms], Windows Forms Panel controls
- Panel control [Windows Forms], background
- colors [Windows Forms], Windows Forms Panel controls
ms.assetid: db83cf54-3c69-4b08-ac6c-25b9b5abb1b0
ms.openlocfilehash: e66d8c81114a4550f0473f75a8101e79e8db2c76
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59103708"
---
# <a name="how-to-set-the-background-of-a-windows-forms-panel-using-the-designer"></a><span data-ttu-id="2c6ac-102">Como: Definir a tela de fundo de um painel do Windows Forms usando o Designer</span><span class="sxs-lookup"><span data-stu-id="2c6ac-102">How to: Set the Background of a Windows Forms Panel Using the Designer</span></span>
<span data-ttu-id="2c6ac-103">Um Windows Forms <xref:System.Windows.Forms.Panel> controle pode exibir uma cor de fundo e uma imagem de plano de fundo.</span><span class="sxs-lookup"><span data-stu-id="2c6ac-103">A Windows Forms <xref:System.Windows.Forms.Panel> control can display both a background color and a background image.</span></span> <span data-ttu-id="2c6ac-104">O <xref:System.Windows.Forms.Control.BackColor%2A> propriedade define a cor de plano de fundo de controles que estão contidos no painel, como rótulos e botões de opção.</span><span class="sxs-lookup"><span data-stu-id="2c6ac-104">The <xref:System.Windows.Forms.Control.BackColor%2A> property sets the background color for controls that are contained in the panel, such as labels and radio buttons.</span></span> <span data-ttu-id="2c6ac-105">Se o <xref:System.Windows.Forms.Control.BackgroundImage%2A> não está definida, o <xref:System.Windows.Forms.Control.BackColor%2A> seleção preencherá todos o painel.</span><span class="sxs-lookup"><span data-stu-id="2c6ac-105">If the <xref:System.Windows.Forms.Control.BackgroundImage%2A> property is not set, the <xref:System.Windows.Forms.Control.BackColor%2A> selection will fill all of the panel.</span></span> <span data-ttu-id="2c6ac-106">Se o <xref:System.Windows.Forms.Control.BackgroundImage%2A> estiver definida, a imagem será exibida por trás dos controles que estão contidos no painel.</span><span class="sxs-lookup"><span data-stu-id="2c6ac-106">If the <xref:System.Windows.Forms.Control.BackgroundImage%2A> property is set, the image will be displayed behind the controls that are contained in the panel.</span></span>  
  
 <span data-ttu-id="2c6ac-107">O procedimento a seguir exige um **aplicativo do Windows** projeto com um formulário que contenha um <xref:System.Windows.Forms.Panel> controle.</span><span class="sxs-lookup"><span data-stu-id="2c6ac-107">The following procedure requires a **Windows Application** project with a form that contains a <xref:System.Windows.Forms.Panel> control.</span></span> <span data-ttu-id="2c6ac-108">Para obter informações sobre como configurar um projeto desse tipo, consulte [como: Criar um projeto de aplicativo do Windows Forms](/visualstudio/ide/step-1-create-a-windows-forms-application-project) e [como: Adicionar controles ao Windows Forms](how-to-add-controls-to-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="2c6ac-108">For information about how to set up such a project, see [How to: Create a Windows Forms application project](/visualstudio/ide/step-1-create-a-windows-forms-application-project) and [How to: Add Controls to Windows Forms](how-to-add-controls-to-windows-forms.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="2c6ac-109">As caixas de diálogo e os comandos de menu que você vê podem ser diferentes dos descritos na Ajuda, dependendo da sua edição ou das configurações ativas.</span><span class="sxs-lookup"><span data-stu-id="2c6ac-109">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="2c6ac-110">Para alterar as configurações, escolha **Importar e Exportar Configurações** no menu **Ferramentas**.</span><span class="sxs-lookup"><span data-stu-id="2c6ac-110">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="2c6ac-111">Para obter mais informações, confira [Personalizar o IDE do Visual Studio](/visualstudio/ide/personalizing-the-visual-studio-ide).</span><span class="sxs-lookup"><span data-stu-id="2c6ac-111">For more information, see [Personalize the Visual Studio IDE](/visualstudio/ide/personalizing-the-visual-studio-ide).</span></span>  
  
### <a name="to-set-the-background-in-the-windows-forms-designer"></a><span data-ttu-id="2c6ac-112">Para definir a tela de fundo no Designer de Formulários do Windows</span><span class="sxs-lookup"><span data-stu-id="2c6ac-112">To set the background in the Windows Forms Designer</span></span>  
  
1.  <span data-ttu-id="2c6ac-113">Selecione o <xref:System.Windows.Forms.Panel> controle.</span><span class="sxs-lookup"><span data-stu-id="2c6ac-113">Select the <xref:System.Windows.Forms.Panel> control.</span></span>  
  
2.  <span data-ttu-id="2c6ac-114">No **propriedades** , clique na seta ao lado de <xref:System.Windows.Forms.Control.BackColor%2A> propriedade para exibir uma janela com três guias.</span><span class="sxs-lookup"><span data-stu-id="2c6ac-114">In the **Properties** window, click the arrow button next to the <xref:System.Windows.Forms.Control.BackColor%2A> property to display a window with three tabs.</span></span>  
  
3.  <span data-ttu-id="2c6ac-115">Selecione a guia **Personalizado** para exibir uma paleta de cores.</span><span class="sxs-lookup"><span data-stu-id="2c6ac-115">Select the **Custom** tab to display a palette of colors.</span></span>  
  
4.  <span data-ttu-id="2c6ac-116">Selecione a guia **Web** ou **Sistema** para exibir uma lista de nomes predefinidos para cores e, em seguida, selecione uma cor.</span><span class="sxs-lookup"><span data-stu-id="2c6ac-116">Select the **Web** or **System** tab to display a list of predefined names for colors, and then select a color.</span></span>  
  
5.  <span data-ttu-id="2c6ac-117">No **propriedades** , clique na seta ao lado de <xref:System.Windows.Forms.Control.BackgroundImage%2A> propriedade.</span><span class="sxs-lookup"><span data-stu-id="2c6ac-117">In the **Properties** window, click the arrow button next to the <xref:System.Windows.Forms.Control.BackgroundImage%2A> property.</span></span>  
  
6.  <span data-ttu-id="2c6ac-118">Na caixa de diálogo **Abrir**, selecione o arquivo que deseja exibir.</span><span class="sxs-lookup"><span data-stu-id="2c6ac-118">In the **Open** dialog box, select the file that you want to display.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2c6ac-119">Consulte também</span><span class="sxs-lookup"><span data-stu-id="2c6ac-119">See also</span></span>

- <xref:System.Windows.Forms.Control.BackColor%2A>
- <xref:System.Windows.Forms.Control.BackgroundImage%2A>
- [<span data-ttu-id="2c6ac-120">Controle de painel</span><span class="sxs-lookup"><span data-stu-id="2c6ac-120">Panel Control</span></span>](panel-control-windows-forms.md)
- [<span data-ttu-id="2c6ac-121">Visão geral do controle de painel</span><span class="sxs-lookup"><span data-stu-id="2c6ac-121">Panel Control Overview</span></span>](panel-control-overview-windows-forms.md)
- [<span data-ttu-id="2c6ac-122">Como: Agrupar controles com o controle de painel do Windows Forms usando o Designer</span><span class="sxs-lookup"><span data-stu-id="2c6ac-122">How to: Group Controls with the Windows Forms Panel Control Using the Designer</span></span>](group-controls-with-wf-panel-control-using-the-designer.md)
