---
title: 'Como: copiar e colar um controle ElementHost em tempo de design'
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Forms, content copying and pasting
- interoperability [WPF]
- ElementHost control [Windows Forms], copying and pasting at design time
- WPF user control [Windows Forms], hosting in Windows Forms
ms.assetid: e570375d-2a68-44ba-b4f7-c781af2d20e8
ms.openlocfilehash: e8bc4aa4ecd2bff2981b7d4faf1e270337f346e7
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/09/2019
ms.locfileid: "59346204"
---
# <a name="how-to-copy-and-paste-an-elementhost-control-at-design-time"></a><span data-ttu-id="a8eeb-102">Como: copiar e colar um controle ElementHost em tempo de design</span><span class="sxs-lookup"><span data-stu-id="a8eeb-102">How to: Copy and Paste an ElementHost Control at Design Time</span></span>
<span data-ttu-id="a8eeb-103">Este procedimento mostra como copiar um controle Windows Presentation Foundation (WPF) em um formulário do Windows.</span><span class="sxs-lookup"><span data-stu-id="a8eeb-103">This procedure shows you how to copy a Windows Presentation Foundation (WPF) control on a Windows Form.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="a8eeb-104">As caixas de diálogo e os comandos de menu que você vê podem ser diferentes dos descritos na Ajuda, dependendo da sua edição ou das configurações ativas.</span><span class="sxs-lookup"><span data-stu-id="a8eeb-104">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="a8eeb-105">Para alterar as configurações, escolha **Importar e Exportar Configurações** no menu **Ferramentas**.</span><span class="sxs-lookup"><span data-stu-id="a8eeb-105">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="a8eeb-106">Para obter mais informações, confira [Personalizar o IDE do Visual Studio](/visualstudio/ide/personalizing-the-visual-studio-ide).</span><span class="sxs-lookup"><span data-stu-id="a8eeb-106">For more information, see [Personalize the Visual Studio IDE](/visualstudio/ide/personalizing-the-visual-studio-ide).</span></span>  
  
### <a name="to-copy-and-paste-an-elementhost-control-at-design-time"></a><span data-ttu-id="a8eeb-107">Para copiar e colar um controle ElementHost em tempo de design</span><span class="sxs-lookup"><span data-stu-id="a8eeb-107">To copy and paste an ElementHost control at design time</span></span>  
  
1. <span data-ttu-id="a8eeb-108">Adicione um novo WPF <xref:System.Windows.Controls.UserControl> ao seu projeto de formulários do Windows.</span><span class="sxs-lookup"><span data-stu-id="a8eeb-108">Add a new WPF <xref:System.Windows.Controls.UserControl> to your Windows Forms project.</span></span> <span data-ttu-id="a8eeb-109">Use o nome padrão do tipo de controle, `UserControl1.xaml`.</span><span class="sxs-lookup"><span data-stu-id="a8eeb-109">Use the default name for the control type, `UserControl1.xaml`.</span></span> <span data-ttu-id="a8eeb-110">Para obter mais informações, confira [Passo a passo: Criando novo conteúdo WPF nos Windows Forms em tempo de Design](walkthrough-creating-new-wpf-content-on-windows-forms-at-design-time.md).</span><span class="sxs-lookup"><span data-stu-id="a8eeb-110">For more information, see [Walkthrough: Creating New WPF Content on Windows Forms at Design Time](walkthrough-creating-new-wpf-content-on-windows-forms-at-design-time.md).</span></span>  
  
2. <span data-ttu-id="a8eeb-111">No **propriedades** janela, defina o valor da <xref:System.Windows.FrameworkElement.Width%2A> e <xref:System.Windows.FrameworkElement.Height%2A> propriedades do `UserControl1` para `200`.</span><span class="sxs-lookup"><span data-stu-id="a8eeb-111">In the **Properties** window, set the value of the <xref:System.Windows.FrameworkElement.Width%2A> and <xref:System.Windows.FrameworkElement.Height%2A> properties of `UserControl1` to `200`.</span></span>  
  
3. <span data-ttu-id="a8eeb-112">Definir o valor de <xref:System.Windows.Controls.Control.Background%2A> propriedade para `Blue`.</span><span class="sxs-lookup"><span data-stu-id="a8eeb-112">Set the value of the <xref:System.Windows.Controls.Control.Background%2A> property to `Blue`.</span></span>  
  
4. <span data-ttu-id="a8eeb-113">Compile o projeto.</span><span class="sxs-lookup"><span data-stu-id="a8eeb-113">Build the project.</span></span>  
  
5. <span data-ttu-id="a8eeb-114">Abra `Form1` no Designer de Formulários do Windows.</span><span class="sxs-lookup"><span data-stu-id="a8eeb-114">Open `Form1` in the Windows Forms Designer.</span></span>  
  
6. <span data-ttu-id="a8eeb-115">Da **Caixa de Ferramentas**, arraste uma instância de `UserControl1` para o formulário.</span><span class="sxs-lookup"><span data-stu-id="a8eeb-115">From the **Toolbox**, drag an instance of `UserControl1` onto the form.</span></span>  
  
     <span data-ttu-id="a8eeb-116">Uma instância do `UserControl1` é hospedado em uma nova <xref:System.Windows.Forms.Integration.ElementHost> controle chamado `elementHost1`.</span><span class="sxs-lookup"><span data-stu-id="a8eeb-116">An instance of `UserControl1` is hosted in a new <xref:System.Windows.Forms.Integration.ElementHost> control named `elementHost1`.</span></span>  
  
7. <span data-ttu-id="a8eeb-117">Com `elementHost1` selecionado, pressione CTRL+C para copiá-lo para a área de transferência.</span><span class="sxs-lookup"><span data-stu-id="a8eeb-117">With `elementHost1` selected, press CTRL+C to copy it to the clipboard.</span></span>  
  
8. <span data-ttu-id="a8eeb-118">Pressione CTRL + V para colar o controle copiado para o formulário.</span><span class="sxs-lookup"><span data-stu-id="a8eeb-118">Press CTRL+V to paste the copied control onto the form.</span></span>  
  
     <span data-ttu-id="a8eeb-119">Uma nova <xref:System.Windows.Forms.Integration.ElementHost> controle chamado `elementHost2` é criado no formulário.</span><span class="sxs-lookup"><span data-stu-id="a8eeb-119">A new <xref:System.Windows.Forms.Integration.ElementHost> control named `elementHost2` is created on the form.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a8eeb-120">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a8eeb-120">See also</span></span>

- <xref:System.Windows.Forms.Integration.ElementHost>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost>
- [<span data-ttu-id="a8eeb-121">Migração e interoperabilidade</span><span class="sxs-lookup"><span data-stu-id="a8eeb-121">Migration and Interoperability</span></span>](../../wpf/advanced/migration-and-interoperability.md)
- [<span data-ttu-id="a8eeb-122">Usando controles WPF</span><span class="sxs-lookup"><span data-stu-id="a8eeb-122">Using WPF Controls</span></span>](using-wpf-controls.md)
- [<span data-ttu-id="a8eeb-123">Criar XAML no Visual Studio</span><span class="sxs-lookup"><span data-stu-id="a8eeb-123">Design XAML in Visual Studio</span></span>](/visualstudio/designers/designing-xaml-in-visual-studio)
