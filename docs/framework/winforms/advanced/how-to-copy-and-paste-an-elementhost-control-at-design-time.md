---
title: Como copiar e colar um controle ElementHost em tempo de design
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Forms, content copying and pasting
- interoperability [WPF]
- ElementHost control [Windows Forms], copying and pasting at design time
- WPF user control [Windows Forms], hosting in Windows Forms
ms.assetid: e570375d-2a68-44ba-b4f7-c781af2d20e8
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 3d1887eb1161f714962c2c26d6fe618749b26c0f
ms.sourcegitcommit: 5a28f8eb071fcc09b045b0c4ae4b96898673192e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2019
ms.locfileid: "73197484"
---
# <a name="how-to-copy-and-paste-an-elementhost-control"></a><span data-ttu-id="d8575-102">Como copiar e colar um controle ElementHost</span><span class="sxs-lookup"><span data-stu-id="d8575-102">How to: Copy and paste an ElementHost control</span></span>

<span data-ttu-id="d8575-103">Este procedimento mostra como copiar um controle Windows Presentation Foundation (WPF) em um formulário do Windows no Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="d8575-103">This procedure shows you how to copy a Windows Presentation Foundation (WPF) control on a Windows Form in Visual Studio.</span></span>

1. <span data-ttu-id="d8575-104">No Visual Studio, adicione um novo <xref:System.Windows.Controls.UserControl> do WPF a um projeto Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="d8575-104">In Visual Studio, add a new WPF <xref:System.Windows.Controls.UserControl> to a Windows Forms project.</span></span> <span data-ttu-id="d8575-105">Use o nome padrão do tipo de controle, `UserControl1.xaml`.</span><span class="sxs-lookup"><span data-stu-id="d8575-105">Use the default name for the control type, `UserControl1.xaml`.</span></span> <span data-ttu-id="d8575-106">Para obter mais informações, consulte [Instruções passo a passo: como criar novo conteúdo WPF nos Windows Forms em tempo de design](walkthrough-creating-new-wpf-content-on-windows-forms-at-design-time.md).</span><span class="sxs-lookup"><span data-stu-id="d8575-106">For more information, see [Walkthrough: Creating New WPF Content on Windows Forms at Design Time](walkthrough-creating-new-wpf-content-on-windows-forms-at-design-time.md).</span></span>

2. <span data-ttu-id="d8575-107">Na janela **Propriedades** , defina o valor do <xref:System.Windows.FrameworkElement.Width%2A> e <xref:System.Windows.FrameworkElement.Height%2A> propriedades de `UserControl1` como **200**.</span><span class="sxs-lookup"><span data-stu-id="d8575-107">In the **Properties** window, set the value of the <xref:System.Windows.FrameworkElement.Width%2A> and <xref:System.Windows.FrameworkElement.Height%2A> properties of `UserControl1` to **200**.</span></span>

3. <span data-ttu-id="d8575-108">Defina o valor da propriedade <xref:System.Windows.Controls.Control.Background%2A> como **azul**.</span><span class="sxs-lookup"><span data-stu-id="d8575-108">Set the value of the <xref:System.Windows.Controls.Control.Background%2A> property to **Blue**.</span></span>

4. <span data-ttu-id="d8575-109">Compile o projeto.</span><span class="sxs-lookup"><span data-stu-id="d8575-109">Build the project.</span></span>

5. <span data-ttu-id="d8575-110">Abra `Form1` no Designer de Formulários do Windows.</span><span class="sxs-lookup"><span data-stu-id="d8575-110">Open `Form1` in the Windows Forms Designer.</span></span>

6. <span data-ttu-id="d8575-111">Da **Caixa de Ferramentas**, arraste uma instância de `UserControl1` para o formulário.</span><span class="sxs-lookup"><span data-stu-id="d8575-111">From the **Toolbox**, drag an instance of `UserControl1` onto the form.</span></span>

   <span data-ttu-id="d8575-112">Uma instância de `UserControl1` é hospedada em um novo controle de <xref:System.Windows.Forms.Integration.ElementHost> chamado `elementHost1`.</span><span class="sxs-lookup"><span data-stu-id="d8575-112">An instance of `UserControl1` is hosted in a new <xref:System.Windows.Forms.Integration.ElementHost> control named `elementHost1`.</span></span>

7. <span data-ttu-id="d8575-113">Com `elementHost1` selecionado, pressione **Ctrl**+**C** para copiá-lo para a área de transferência.</span><span class="sxs-lookup"><span data-stu-id="d8575-113">With `elementHost1` selected, press **Ctrl**+**C** to copy it to the clipboard.</span></span>

8. <span data-ttu-id="d8575-114">Pressione **Ctrl**+**V** para colar o controle copiado no formulário.</span><span class="sxs-lookup"><span data-stu-id="d8575-114">Press **Ctrl**+**V** to paste the copied control onto the form.</span></span>

   <span data-ttu-id="d8575-115">Um novo controle de <xref:System.Windows.Forms.Integration.ElementHost> chamado `elementHost2` é criado no formulário.</span><span class="sxs-lookup"><span data-stu-id="d8575-115">A new <xref:System.Windows.Forms.Integration.ElementHost> control named `elementHost2` is created on the form.</span></span>

## <a name="see-also"></a><span data-ttu-id="d8575-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="d8575-116">See also</span></span>

- <xref:System.Windows.Forms.Integration.ElementHost>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost>
- [<span data-ttu-id="d8575-117">Migração e Interoperabilidade</span><span class="sxs-lookup"><span data-stu-id="d8575-117">Migration and Interoperability</span></span>](../../wpf/advanced/migration-and-interoperability.md)
- [<span data-ttu-id="d8575-118">Usando Controles do WPF</span><span class="sxs-lookup"><span data-stu-id="d8575-118">Using WPF Controls</span></span>](using-wpf-controls.md)
- [<span data-ttu-id="d8575-119">Criar o XAML no Visual Studio</span><span class="sxs-lookup"><span data-stu-id="d8575-119">Design XAML in Visual Studio</span></span>](/visualstudio/xaml-tools/designing-xaml-in-visual-studio)
