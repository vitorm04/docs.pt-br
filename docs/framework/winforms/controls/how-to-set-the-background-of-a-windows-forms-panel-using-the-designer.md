---
title: Definir o plano de fundo de um painel usando o designer
ms.date: 03/30/2017
helpviewer_keywords:
- background colors [Windows Forms], Windows Forms Panel controls
- background images [Windows Forms], Windows Forms Panel controls
- Panel control [Windows Forms], background
- colors [Windows Forms], Windows Forms Panel controls
ms.assetid: db83cf54-3c69-4b08-ac6c-25b9b5abb1b0
ms.openlocfilehash: 8bdefba433632f7ba02f549a549c52c7aa56c2d7
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76731924"
---
# <a name="how-to-set-the-background-of-a-windows-forms-panel-using-the-designer"></a><span data-ttu-id="91fa2-102">Como: definir o plano de fundo de um painel de Windows Forms usando o designer</span><span class="sxs-lookup"><span data-stu-id="91fa2-102">How to: Set the background of a Windows Forms panel using the Designer</span></span>

<span data-ttu-id="91fa2-103">Um controle de <xref:System.Windows.Forms.Panel> de Windows Forms pode exibir uma cor de plano de fundo e uma imagem de plano de fundo.</span><span class="sxs-lookup"><span data-stu-id="91fa2-103">A Windows Forms <xref:System.Windows.Forms.Panel> control can display both a background color and a background image.</span></span> <span data-ttu-id="91fa2-104">A propriedade <xref:System.Windows.Forms.Control.BackColor%2A> define a cor do plano de fundo dos controles contidos no painel, como rótulos e botões de opção.</span><span class="sxs-lookup"><span data-stu-id="91fa2-104">The <xref:System.Windows.Forms.Control.BackColor%2A> property sets the background color for controls that are contained in the panel, such as labels and radio buttons.</span></span> <span data-ttu-id="91fa2-105">Se a propriedade <xref:System.Windows.Forms.Control.BackgroundImage%2A> não estiver definida, a seleção de <xref:System.Windows.Forms.Control.BackColor%2A> preencherá todo o painel.</span><span class="sxs-lookup"><span data-stu-id="91fa2-105">If the <xref:System.Windows.Forms.Control.BackgroundImage%2A> property is not set, the <xref:System.Windows.Forms.Control.BackColor%2A> selection will fill all of the panel.</span></span> <span data-ttu-id="91fa2-106">Se a propriedade <xref:System.Windows.Forms.Control.BackgroundImage%2A> for definida, a imagem será exibida atrás dos controles contidos no painel.</span><span class="sxs-lookup"><span data-stu-id="91fa2-106">If the <xref:System.Windows.Forms.Control.BackgroundImage%2A> property is set, the image will be displayed behind the controls that are contained in the panel.</span></span>

<span data-ttu-id="91fa2-107">O procedimento a seguir requer um projeto de **aplicativo do Windows** com um formulário que contenha um controle de <xref:System.Windows.Forms.Panel>.</span><span class="sxs-lookup"><span data-stu-id="91fa2-107">The following procedure requires a **Windows Application** project with a form that contains a <xref:System.Windows.Forms.Panel> control.</span></span> <span data-ttu-id="91fa2-108">Para obter informações sobre como configurar esse projeto no Visual Studio, consulte [como criar um projeto de aplicativo Windows Forms](/visualstudio/ide/step-1-create-a-windows-forms-application-project) e [como: adicionar controles a Windows Forms](how-to-add-controls-to-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="91fa2-108">For information about how to set up such a project in Visual Studio, see [How to: Create a Windows Forms application project](/visualstudio/ide/step-1-create-a-windows-forms-application-project) and [How to: Add Controls to Windows Forms](how-to-add-controls-to-windows-forms.md).</span></span>

## <a name="set-the-background-in-the-windows-forms-designer"></a><span data-ttu-id="91fa2-109">Definir o plano de fundo no Designer de Formulários do Windows</span><span class="sxs-lookup"><span data-stu-id="91fa2-109">Set the background in the Windows Forms Designer</span></span>

1. <span data-ttu-id="91fa2-110">Abra o projeto no Visual Studio e selecione o controle de <xref:System.Windows.Forms.Panel>.</span><span class="sxs-lookup"><span data-stu-id="91fa2-110">Open the project in Visual Studio and select the <xref:System.Windows.Forms.Panel> control.</span></span>

2. <span data-ttu-id="91fa2-111">Na janela **Propriedades** , clique no botão de seta ao lado da propriedade <xref:System.Windows.Forms.Control.BackColor%2A> para exibir uma janela com três guias.</span><span class="sxs-lookup"><span data-stu-id="91fa2-111">In the **Properties** window, click the arrow button next to the <xref:System.Windows.Forms.Control.BackColor%2A> property to display a window with three tabs.</span></span>

3. <span data-ttu-id="91fa2-112">Selecione a guia **Personalizado** para exibir uma paleta de cores.</span><span class="sxs-lookup"><span data-stu-id="91fa2-112">Select the **Custom** tab to display a palette of colors.</span></span>

4. <span data-ttu-id="91fa2-113">Selecione a guia **Web** ou **Sistema** para exibir uma lista de nomes predefinidos para cores e, em seguida, selecione uma cor.</span><span class="sxs-lookup"><span data-stu-id="91fa2-113">Select the **Web** or **System** tab to display a list of predefined names for colors, and then select a color.</span></span>

5. <span data-ttu-id="91fa2-114">Na janela **Propriedades** , clique no botão de seta ao lado da propriedade <xref:System.Windows.Forms.Control.BackgroundImage%2A>.</span><span class="sxs-lookup"><span data-stu-id="91fa2-114">In the **Properties** window, click the arrow button next to the <xref:System.Windows.Forms.Control.BackgroundImage%2A> property.</span></span>

6. <span data-ttu-id="91fa2-115">Na caixa de diálogo **Abrir**, selecione o arquivo que deseja exibir.</span><span class="sxs-lookup"><span data-stu-id="91fa2-115">In the **Open** dialog box, select the file that you want to display.</span></span>

## <a name="see-also"></a><span data-ttu-id="91fa2-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="91fa2-116">See also</span></span>

- <xref:System.Windows.Forms.Control.BackColor%2A>
- <xref:System.Windows.Forms.Control.BackgroundImage%2A>
- [<span data-ttu-id="91fa2-117">Controle de painel</span><span class="sxs-lookup"><span data-stu-id="91fa2-117">Panel Control</span></span>](panel-control-windows-forms.md)
- [<span data-ttu-id="91fa2-118">Visão geral do controle Panel</span><span class="sxs-lookup"><span data-stu-id="91fa2-118">Panel Control Overview</span></span>](panel-control-overview-windows-forms.md)
- [<span data-ttu-id="91fa2-119">Como agrupar controles com o controle de painel dos Windows Forms usando o Designer</span><span class="sxs-lookup"><span data-stu-id="91fa2-119">How to: Group Controls with the Windows Forms Panel Control Using the Designer</span></span>](group-controls-with-wf-panel-control-using-the-designer.md)
