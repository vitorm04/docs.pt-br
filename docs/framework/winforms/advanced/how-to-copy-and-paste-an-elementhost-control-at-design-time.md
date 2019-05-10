---
title: 'Como: copiar e colar um controle ElementHost em tempo de design'
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Forms, content copying and pasting
- interoperability [WPF]
- ElementHost control [Windows Forms], copying and pasting at design time
- WPF user control [Windows Forms], hosting in Windows Forms
ms.assetid: e570375d-2a68-44ba-b4f7-c781af2d20e8
ms.openlocfilehash: 0f3367deaaec04744a3f812d7f2d08047d7eb588
ms.sourcegitcommit: 0d0a6e96737dfe24d3257b7c94f25d9500f383ea
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/07/2019
ms.locfileid: "65211377"
---
# <a name="how-to-copy-and-paste-an-elementhost-control-at-design-time"></a><span data-ttu-id="6b86f-102">Como: copiar e colar um controle ElementHost em tempo de design</span><span class="sxs-lookup"><span data-stu-id="6b86f-102">How to: Copy and Paste an ElementHost Control at Design Time</span></span>

<span data-ttu-id="6b86f-103">Este procedimento mostra como copiar um controle Windows Presentation Foundation (WPF) em um formulário do Windows no Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="6b86f-103">This procedure shows you how to copy a Windows Presentation Foundation (WPF) control on a Windows Form in Visual Studio.</span></span>

## <a name="copy-and-paste-an-elementhost-control-at-design-time"></a><span data-ttu-id="6b86f-104">Copiar e colar um controle ElementHost em tempo de design</span><span class="sxs-lookup"><span data-stu-id="6b86f-104">Copy and paste an ElementHost control at design time</span></span>

1. <span data-ttu-id="6b86f-105">Adicione um novo WPF <xref:System.Windows.Controls.UserControl> ao seu projeto de formulários do Windows.</span><span class="sxs-lookup"><span data-stu-id="6b86f-105">Add a new WPF <xref:System.Windows.Controls.UserControl> to your Windows Forms project.</span></span> <span data-ttu-id="6b86f-106">Use o nome padrão do tipo de controle, `UserControl1.xaml`.</span><span class="sxs-lookup"><span data-stu-id="6b86f-106">Use the default name for the control type, `UserControl1.xaml`.</span></span> <span data-ttu-id="6b86f-107">Para obter mais informações, confira [Passo a passo: Criando novo conteúdo WPF nos Windows Forms em tempo de Design](walkthrough-creating-new-wpf-content-on-windows-forms-at-design-time.md).</span><span class="sxs-lookup"><span data-stu-id="6b86f-107">For more information, see [Walkthrough: Creating New WPF Content on Windows Forms at Design Time](walkthrough-creating-new-wpf-content-on-windows-forms-at-design-time.md).</span></span>

2. <span data-ttu-id="6b86f-108">No **propriedades** janela, defina o valor da <xref:System.Windows.FrameworkElement.Width%2A> e <xref:System.Windows.FrameworkElement.Height%2A> propriedades do `UserControl1` para `200`.</span><span class="sxs-lookup"><span data-stu-id="6b86f-108">In the **Properties** window, set the value of the <xref:System.Windows.FrameworkElement.Width%2A> and <xref:System.Windows.FrameworkElement.Height%2A> properties of `UserControl1` to `200`.</span></span>

3. <span data-ttu-id="6b86f-109">Definir o valor de <xref:System.Windows.Controls.Control.Background%2A> propriedade para `Blue`.</span><span class="sxs-lookup"><span data-stu-id="6b86f-109">Set the value of the <xref:System.Windows.Controls.Control.Background%2A> property to `Blue`.</span></span>

4. <span data-ttu-id="6b86f-110">Compile o projeto.</span><span class="sxs-lookup"><span data-stu-id="6b86f-110">Build the project.</span></span>

5. <span data-ttu-id="6b86f-111">Abra `Form1` no Designer de Formulários do Windows.</span><span class="sxs-lookup"><span data-stu-id="6b86f-111">Open `Form1` in the Windows Forms Designer.</span></span>

6. <span data-ttu-id="6b86f-112">Da **Caixa de Ferramentas**, arraste uma instância de `UserControl1` para o formulário.</span><span class="sxs-lookup"><span data-stu-id="6b86f-112">From the **Toolbox**, drag an instance of `UserControl1` onto the form.</span></span>

   <span data-ttu-id="6b86f-113">Uma instância do `UserControl1` é hospedado em uma nova <xref:System.Windows.Forms.Integration.ElementHost> controle chamado `elementHost1`.</span><span class="sxs-lookup"><span data-stu-id="6b86f-113">An instance of `UserControl1` is hosted in a new <xref:System.Windows.Forms.Integration.ElementHost> control named `elementHost1`.</span></span>

7. <span data-ttu-id="6b86f-114">Com `elementHost1` selecionado, pressione CTRL+C para copiá-lo para a área de transferência.</span><span class="sxs-lookup"><span data-stu-id="6b86f-114">With `elementHost1` selected, press CTRL+C to copy it to the clipboard.</span></span>

8. <span data-ttu-id="6b86f-115">Pressione CTRL + V para colar o controle copiado para o formulário.</span><span class="sxs-lookup"><span data-stu-id="6b86f-115">Press CTRL+V to paste the copied control onto the form.</span></span>

   <span data-ttu-id="6b86f-116">Uma nova <xref:System.Windows.Forms.Integration.ElementHost> controle chamado `elementHost2` é criado no formulário.</span><span class="sxs-lookup"><span data-stu-id="6b86f-116">A new <xref:System.Windows.Forms.Integration.ElementHost> control named `elementHost2` is created on the form.</span></span>

## <a name="see-also"></a><span data-ttu-id="6b86f-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="6b86f-117">See also</span></span>

- <xref:System.Windows.Forms.Integration.ElementHost>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost>
- [<span data-ttu-id="6b86f-118">Migração e interoperabilidade</span><span class="sxs-lookup"><span data-stu-id="6b86f-118">Migration and Interoperability</span></span>](../../wpf/advanced/migration-and-interoperability.md)
- [<span data-ttu-id="6b86f-119">Usando Controles do WPF</span><span class="sxs-lookup"><span data-stu-id="6b86f-119">Using WPF Controls</span></span>](using-wpf-controls.md)
- [<span data-ttu-id="6b86f-120">Criar o XAML no Visual Studio</span><span class="sxs-lookup"><span data-stu-id="6b86f-120">Design XAML in Visual Studio</span></span>](/visualstudio/designers/designing-xaml-in-visual-studio)
