---
title: Como copiar e colar um controle ElementHost em tempo de design
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Windows Forms, content copying and pasting
- interoperability [WPF]
- ElementHost control [Windows Forms], copying and pasting at design time
- WPF user control [Windows Forms], hosting in Windows Forms
ms.assetid: e570375d-2a68-44ba-b4f7-c781af2d20e8
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: ffe7d050de84eba8c7962a62a8604a72f78bc2bc
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-copy-and-paste-an-elementhost-control-at-design-time"></a><span data-ttu-id="21463-102">Como copiar e colar um controle ElementHost em tempo de design</span><span class="sxs-lookup"><span data-stu-id="21463-102">How to: Copy and Paste an ElementHost Control at Design Time</span></span>
<span data-ttu-id="21463-103">Este procedimento mostra como copiar um controle Windows Presentation Foundation (WPF) em um Windows Form.</span><span class="sxs-lookup"><span data-stu-id="21463-103">This procedure shows you how to copy a Windows Presentation Foundation (WPF) control on a Windows Form.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="21463-104">As caixas de diálogo e os comandos de menu que você vê podem ser diferentes dos descritos na Ajuda, dependendo da sua edição ou das configurações ativas.</span><span class="sxs-lookup"><span data-stu-id="21463-104">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="21463-105">Para alterar as configurações, escolha **Importar e Exportar Configurações** no menu **Ferramentas**.</span><span class="sxs-lookup"><span data-stu-id="21463-105">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="21463-106">Para obter mais informações, consulte [Personalizando configurações de desenvolvimento no Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span><span class="sxs-lookup"><span data-stu-id="21463-106">For more information, see [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span></span>  
  
### <a name="to-copy-and-paste-an-elementhost-control-at-design-time"></a><span data-ttu-id="21463-107">Para copiar e colar um controle ElementHost em tempo de design</span><span class="sxs-lookup"><span data-stu-id="21463-107">To copy and paste an ElementHost control at design time</span></span>  
  
1.  <span data-ttu-id="21463-108">Adicione um novo WPF <xref:System.Windows.Controls.UserControl> ao seu projeto de formulários do Windows.</span><span class="sxs-lookup"><span data-stu-id="21463-108">Add a new WPF <xref:System.Windows.Controls.UserControl> to your Windows Forms project.</span></span> <span data-ttu-id="21463-109">Use o nome padrão do tipo de controle, `UserControl1.xaml`.</span><span class="sxs-lookup"><span data-stu-id="21463-109">Use the default name for the control type, `UserControl1.xaml`.</span></span> <span data-ttu-id="21463-110">Para obter mais informações, consulte [Instruções passo a passo: como criar novo conteúdo WPF nos Windows Forms em tempo de design](../../../../docs/framework/winforms/advanced/walkthrough-creating-new-wpf-content-on-windows-forms-at-design-time.md).</span><span class="sxs-lookup"><span data-stu-id="21463-110">For more information, see [Walkthrough: Creating New WPF Content on Windows Forms at Design Time](../../../../docs/framework/winforms/advanced/walkthrough-creating-new-wpf-content-on-windows-forms-at-design-time.md).</span></span>  
  
2.  <span data-ttu-id="21463-111">No **propriedades** janela, defina o valor da <xref:System.Windows.FrameworkElement.Width%2A> e <xref:System.Windows.FrameworkElement.Height%2A> propriedades de `UserControl1` para `200`.</span><span class="sxs-lookup"><span data-stu-id="21463-111">In the **Properties** window, set the value of the <xref:System.Windows.FrameworkElement.Width%2A> and <xref:System.Windows.FrameworkElement.Height%2A> properties of `UserControl1` to `200`.</span></span>  
  
3.  <span data-ttu-id="21463-112">Definir o valor de <xref:System.Windows.Controls.Control.Background%2A> propriedade `Blue`.</span><span class="sxs-lookup"><span data-stu-id="21463-112">Set the value of the <xref:System.Windows.Controls.Control.Background%2A> property to `Blue`.</span></span>  
  
4.  <span data-ttu-id="21463-113">Compile o projeto.</span><span class="sxs-lookup"><span data-stu-id="21463-113">Build the project.</span></span>  
  
5.  <span data-ttu-id="21463-114">Abra `Form1` no Designer de Formulários do Windows.</span><span class="sxs-lookup"><span data-stu-id="21463-114">Open `Form1` in the Windows Forms Designer.</span></span>  
  
6.  <span data-ttu-id="21463-115">Da **Caixa de Ferramentas**, arraste uma instância de `UserControl1` para o formulário.</span><span class="sxs-lookup"><span data-stu-id="21463-115">From the **Toolbox**, drag an instance of `UserControl1` onto the form.</span></span>  
  
     <span data-ttu-id="21463-116">Uma instância de `UserControl1` está hospedada em um novo <xref:System.Windows.Forms.Integration.ElementHost> controle chamado `elementHost1`.</span><span class="sxs-lookup"><span data-stu-id="21463-116">An instance of `UserControl1` is hosted in a new <xref:System.Windows.Forms.Integration.ElementHost> control named `elementHost1`.</span></span>  
  
7.  <span data-ttu-id="21463-117">Com `elementHost1` selecionado, pressione CTRL+C para copiá-lo para a área de transferência.</span><span class="sxs-lookup"><span data-stu-id="21463-117">With `elementHost1` selected, press CTRL+C to copy it to the clipboard.</span></span>  
  
8.  <span data-ttu-id="21463-118">Pressione CTRL + V para colar o controle copiado para o formulário.</span><span class="sxs-lookup"><span data-stu-id="21463-118">Press CTRL+V to paste the copied control onto the form.</span></span>  
  
     <span data-ttu-id="21463-119">Um novo <xref:System.Windows.Forms.Integration.ElementHost> controle chamado `elementHost2` é criado no formulário.</span><span class="sxs-lookup"><span data-stu-id="21463-119">A new <xref:System.Windows.Forms.Integration.ElementHost> control named `elementHost2` is created on the form.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="21463-120">Consulte também</span><span class="sxs-lookup"><span data-stu-id="21463-120">See Also</span></span>  
 <xref:System.Windows.Forms.Integration.ElementHost>  
 <xref:System.Windows.Forms.Integration.WindowsFormsHost>  
 [<span data-ttu-id="21463-121">Instruções passo a passo: copiando e colando um controle ElementHost em Windows Forms separados</span><span class="sxs-lookup"><span data-stu-id="21463-121">Walkthrough: Copying and Pasting an ElementHost Control into Separate Windows Forms</span></span>](../../../../docs/framework/winforms/advanced/copy--paste-an-elementhost-control-into-forms.md)  
 [<span data-ttu-id="21463-122">Migração e interoperabilidade</span><span class="sxs-lookup"><span data-stu-id="21463-122">Migration and Interoperability</span></span>](../../../../docs/framework/wpf/advanced/migration-and-interoperability.md)  
 [<span data-ttu-id="21463-123">Usando Controles do WPF</span><span class="sxs-lookup"><span data-stu-id="21463-123">Using WPF Controls</span></span>](../../../../docs/framework/winforms/advanced/using-wpf-controls.md)  
 [<span data-ttu-id="21463-124">Designer do WPF</span><span class="sxs-lookup"><span data-stu-id="21463-124">WPF Designer</span></span>](http://msdn.microsoft.com/en-us/c6c65214-8411-4e16-b254-163ed4099c26)
