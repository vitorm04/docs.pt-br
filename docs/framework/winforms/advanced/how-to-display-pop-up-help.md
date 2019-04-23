---
title: 'Como: exibir a ajuda pop-up'
ms.date: 03/30/2017
helpviewer_keywords:
- pop-up Help
- Help [Windows Forms], pop-up Help
- Windows Forms, displaying Help
- forms [Windows Forms], displaying Help
- modal dialog boxes [Windows Forms], pop-up Help
- F1 Help [Windows Forms], in dialog boxes
- HelpProvider component [Windows Forms]
- Help [Windows Forms], adding to dialog boxes
ms.assetid: 218aa81e-e87e-4d67-af05-11627bbdce3b
ms.openlocfilehash: f805840ea3b1a8aef6a289dba064c468a4da0cb0
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59331475"
---
# <a name="how-to-display-pop-up-help"></a><span data-ttu-id="64885-102">Como: exibir a ajuda pop-up</span><span class="sxs-lookup"><span data-stu-id="64885-102">How to: Display Pop-up Help</span></span>
<span data-ttu-id="64885-103">Uma maneira de exibir a Ajuda no Windows Forms é por meio de **ajuda** botão, localizado no lado direito da barra de título, acessível por meio o <xref:System.Windows.Forms.Form.HelpButton%2A> propriedade.</span><span class="sxs-lookup"><span data-stu-id="64885-103">One way to display Help on Windows Forms is through the **Help** button, located on the right side of the title bar, accessible through the <xref:System.Windows.Forms.Form.HelpButton%2A> property.</span></span> <span data-ttu-id="64885-104">Esse tipo de exibição de Ajuda é adequado para uso com caixas de diálogo.</span><span class="sxs-lookup"><span data-stu-id="64885-104">This type of Help display is well-suited for use with dialog boxes.</span></span> <span data-ttu-id="64885-105">Caixas de diálogo mostradas modalmente (com o <xref:System.Windows.Forms.Form.ShowDialog%2A> método) enfrentam dificuldades ajuda externa sistemas, como caixas de diálogo modais precisam ser fechadas antes que o foco pode alternar para outra janela.</span><span class="sxs-lookup"><span data-stu-id="64885-105">Dialog boxes shown modally (with the <xref:System.Windows.Forms.Form.ShowDialog%2A> method) have trouble bringing up external Help systems, because modal dialog boxes need to be closed before focus can shift to another window.</span></span> <span data-ttu-id="64885-106">Além disso, usar o botão **Ajuda** requer que não nenhum botão **Minimizar** ou **Maximizar** seja mostrado na barra de título.</span><span class="sxs-lookup"><span data-stu-id="64885-106">Additionally, using the **Help** button requires that there is no **Minimize** button or **Maximize** button shown in the title bar.</span></span> <span data-ttu-id="64885-107">Isso é uma convenção padrão de caixas de diálogo, enquanto formulários geralmente têm os botões **Minimizar** e **Maximizar**.</span><span class="sxs-lookup"><span data-stu-id="64885-107">This is a standard dialog-box convention, whereas forms usually have **Minimize** and **Maximize** buttons.</span></span>  
  
 <span data-ttu-id="64885-108">Lembre-se de que você também pode usar o <xref:System.Windows.Forms.HelpProvider> componente para vincular controles a arquivos em um sistema de Ajuda, mesmo se você tiver implementado Ajuda pop-up.</span><span class="sxs-lookup"><span data-stu-id="64885-108">Be aware that you can also use the <xref:System.Windows.Forms.HelpProvider> component to link controls to files in a Help system, even if you have implemented pop-up Help.</span></span> <span data-ttu-id="64885-109">Para obter mais informações, consulte [Fornecer ajuda em um aplicativo do Windows](how-to-provide-help-in-a-windows-application.md).</span><span class="sxs-lookup"><span data-stu-id="64885-109">For more information, see [Providing Help in a Windows Application](how-to-provide-help-in-a-windows-application.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="64885-110">As caixas de diálogo e os comandos de menu que você vê podem ser diferentes dos descritos na Ajuda, dependendo da sua edição ou das configurações ativas.</span><span class="sxs-lookup"><span data-stu-id="64885-110">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="64885-111">Para alterar as configurações, escolha **Importar e Exportar Configurações** no menu **Ferramentas**.</span><span class="sxs-lookup"><span data-stu-id="64885-111">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="64885-112">Para obter mais informações, confira [Personalizar o IDE do Visual Studio](/visualstudio/ide/personalizing-the-visual-studio-ide).</span><span class="sxs-lookup"><span data-stu-id="64885-112">For more information, see [Personalize the Visual Studio IDE](/visualstudio/ide/personalizing-the-visual-studio-ide).</span></span>  
  
### <a name="to-display-pop-up-help"></a><span data-ttu-id="64885-113">Exibir a Ajuda pop-up</span><span class="sxs-lookup"><span data-stu-id="64885-113">To display pop-up Help</span></span>  
  
1. <span data-ttu-id="64885-114">Arraste um componente [HelpProvider](../controls/helpprovider-component-windows-forms.md) da Caixa de ferramentas para seu formulário.</span><span class="sxs-lookup"><span data-stu-id="64885-114">Drag a [HelpProvider](../controls/helpprovider-component-windows-forms.md) component from the Toolbox to your form.</span></span>  
  
     <span data-ttu-id="64885-115">Ele ficará na bandeja na parte inferior do Designer de Formulários do Windows.</span><span class="sxs-lookup"><span data-stu-id="64885-115">It will sit in the tray at the bottom of the Windows Forms Designer.</span></span>  
  
2. <span data-ttu-id="64885-116">Na janela Propriedades, defina as <xref:System.Windows.Forms.Form.HelpButton%2A> propriedade para `true`.</span><span class="sxs-lookup"><span data-stu-id="64885-116">In the Properties window, set the <xref:System.Windows.Forms.Form.HelpButton%2A> property to `true`.</span></span> <span data-ttu-id="64885-117">Isso exibirá um botão com um ponto de interrogação no lado direito da barra de título do formulário.</span><span class="sxs-lookup"><span data-stu-id="64885-117">This will display a button with a question mark in it on the right side of the title bar of the form.</span></span>  
  
3. <span data-ttu-id="64885-118">Para que o <xref:System.Windows.Forms.Form.HelpButton%2A> para exibir o formulário <xref:System.Windows.Forms.Form.MinimizeBox%2A> e <xref:System.Windows.Forms.Form.MaximizeBox%2A> propriedades devem ser definidas como `false`, o <xref:System.Windows.Forms.Form.ControlBox%2A> propriedade definida como `true`e o <xref:System.Windows.Forms.Form.FormBorderStyle%2A> propriedade para um dos seguintes valores: <xref:System.Windows.Forms.FormBorderStyle.FixedSingle> , <xref:System.Windows.Forms.FormBorderStyle.Fixed3D>, <xref:System.Windows.Forms.FormBorderStyle.FixedDialog> ou <xref:System.Windows.Forms.FormBorderStyle.Sizable>.</span><span class="sxs-lookup"><span data-stu-id="64885-118">In order for the <xref:System.Windows.Forms.Form.HelpButton%2A> to display, the form's <xref:System.Windows.Forms.Form.MinimizeBox%2A> and <xref:System.Windows.Forms.Form.MaximizeBox%2A> properties must be set to `false`, the <xref:System.Windows.Forms.Form.ControlBox%2A> property set to `true`, and the <xref:System.Windows.Forms.Form.FormBorderStyle%2A> property to one of the following values: <xref:System.Windows.Forms.FormBorderStyle.FixedSingle>, <xref:System.Windows.Forms.FormBorderStyle.Fixed3D>, <xref:System.Windows.Forms.FormBorderStyle.FixedDialog> or <xref:System.Windows.Forms.FormBorderStyle.Sizable>.</span></span>  
  
4. <span data-ttu-id="64885-119">Selecione o controle para o qual você deseja exibir a Ajuda no seu formulário e defina a cadeia de caracteres de Ajuda na janela Propriedades.</span><span class="sxs-lookup"><span data-stu-id="64885-119">Select the control for which you want to show help on your form and set the Help string in the Properties window.</span></span> <span data-ttu-id="64885-120">Esta é a cadeia de texto que será exibida em uma janela similar a uma [ToolTip](../controls/tooltip-component-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="64885-120">This is the string of text that will be displayed in a window similar to a [ToolTip](../controls/tooltip-component-windows-forms.md).</span></span>  
  
5. <span data-ttu-id="64885-121">Pressione **F5**.</span><span class="sxs-lookup"><span data-stu-id="64885-121">Press **F5**.</span></span>  
  
6. <span data-ttu-id="64885-122">Pressione o botão **Ajuda** na barra de título e clique no controle no qual você definiu a cadeia de caracteres de Ajuda.</span><span class="sxs-lookup"><span data-stu-id="64885-122">Press the **Help** button on the title bar and click the control on which you set the Help string.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="64885-123">Consulte também</span><span class="sxs-lookup"><span data-stu-id="64885-123">See also</span></span>

- [<span data-ttu-id="64885-124">Ajuda de Controle Usando ToolTips</span><span class="sxs-lookup"><span data-stu-id="64885-124">Control Help Using ToolTips</span></span>](control-help-using-tooltips.md)
- [<span data-ttu-id="64885-125">Integrando a Ajuda do Usuário nos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="64885-125">Integrating User Help in Windows Forms</span></span>](integrating-user-help-in-windows-forms.md)
- [<span data-ttu-id="64885-126">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="64885-126">Windows Forms</span></span>](../index.md)
