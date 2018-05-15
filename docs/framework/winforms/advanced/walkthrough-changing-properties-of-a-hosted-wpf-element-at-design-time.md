---
title: 'Instruções passo a passo: alterando propriedades de um elemento WPF hospedado no tempo de design'
ms.date: 03/30/2017
helpviewer_keywords:
- WPF content [Windows Forms], changing properties at design time
- Windows Forms, changing properties of WPF content at design time
- WPF content [Windows Forms], hosting in Windows Forms
- interoperability [WPF]
ms.assetid: a1f7a90c-0bbb-4781-8c3c-8cc8bef2488d
ms.openlocfilehash: d17273f52d0cef118b79fef03af72522f6677073
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="walkthrough-changing-properties-of-a-hosted-wpf-element-at-design-time"></a><span data-ttu-id="5a116-102">Instruções passo a passo: alterando propriedades de um elemento WPF hospedado no tempo de design</span><span class="sxs-lookup"><span data-stu-id="5a116-102">Walkthrough: Changing Properties of a Hosted WPF Element at Design Time</span></span>
<span data-ttu-id="5a116-103">Este passo a passo mostra como alterar os valores de propriedade de um controle WPF (Windows Presentation Foundation) hospedado em um formulário do Windows Form.</span><span class="sxs-lookup"><span data-stu-id="5a116-103">This walkthrough shows you how to change property values of a Windows Presentation Foundation (WPF) control hosted on a Windows Form.</span></span>  
  
 <span data-ttu-id="5a116-104">Nesta instrução passo a passo, as seguintes tarefas serão executadas:</span><span class="sxs-lookup"><span data-stu-id="5a116-104">In this walkthrough, you perform the following tasks:</span></span>  
  
-   <span data-ttu-id="5a116-105">Crie o projeto.</span><span class="sxs-lookup"><span data-stu-id="5a116-105">Create the project.</span></span>  
  
-   <span data-ttu-id="5a116-106">Crie o controle WPF.</span><span class="sxs-lookup"><span data-stu-id="5a116-106">Create the WPF control.</span></span>  
  
-   <span data-ttu-id="5a116-107">Hospede os controles WPF em um formulário do Windows Form.</span><span class="sxs-lookup"><span data-stu-id="5a116-107">Host the WPF controls on a Windows Form.</span></span>  
  
-   <span data-ttu-id="5a116-108">Use o WPF Designer do Visual Studio para alterar valores de propriedade.</span><span class="sxs-lookup"><span data-stu-id="5a116-108">Use the WPF Designer for Visual Studio to change property values.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="5a116-109">As caixas de diálogo e os comandos de menu que você vê podem ser diferentes dos descritos na Ajuda, dependendo da sua edição ou das configurações ativas.</span><span class="sxs-lookup"><span data-stu-id="5a116-109">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="5a116-110">Para alterar as configurações, escolha **Importar e Exportar Configurações** no menu **Ferramentas**.</span><span class="sxs-lookup"><span data-stu-id="5a116-110">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="5a116-111">Para obter mais informações, consulte [Personalizando configurações de desenvolvimento no Visual Studio](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span><span class="sxs-lookup"><span data-stu-id="5a116-111">For more information, see [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="5a116-112">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="5a116-112">Prerequisites</span></span>  
 <span data-ttu-id="5a116-113">Você precisa dos seguintes componentes para concluir esta instrução passo a passo:</span><span class="sxs-lookup"><span data-stu-id="5a116-113">You need the following components to complete this walkthrough:</span></span>  
  
-   [!INCLUDE[vs_dev11_long](../../../../includes/vs-dev11-long-md.md)]<span data-ttu-id="5a116-114">.</span><span class="sxs-lookup"><span data-stu-id="5a116-114">.</span></span>  
  
## <a name="creating-the-project"></a><span data-ttu-id="5a116-115">Criando o Projeto</span><span class="sxs-lookup"><span data-stu-id="5a116-115">Creating the Project</span></span>  
 <span data-ttu-id="5a116-116">A primeira etapa é criar o projeto dos Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="5a116-116">The first step is to create the Windows Forms project.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="5a116-117">Ao hospedar conteúdo do WPF, haverá suporte apenas para projetos em C# e Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="5a116-117">When hosting WPF content, only C# and Visual Basic projects are supported.</span></span>  
  
#### <a name="to-create-the-project"></a><span data-ttu-id="5a116-118">Para criar o projeto</span><span class="sxs-lookup"><span data-stu-id="5a116-118">To create the project</span></span>  
  
-   <span data-ttu-id="5a116-119">Crie um novo projeto de Aplicativo dos Windows Forms no Visual Basic ou Visual C# chamado `WpfHost`.</span><span class="sxs-lookup"><span data-stu-id="5a116-119">Create a new Windows Forms Application project in Visual Basic or Visual C# named `WpfHost`.</span></span>  
  
## <a name="creating-the-wpf-control"></a><span data-ttu-id="5a116-120">Criando o controle WPF</span><span class="sxs-lookup"><span data-stu-id="5a116-120">Creating the WPF Control</span></span>  
 <span data-ttu-id="5a116-121">Depois de adicionar um controle WPF ao projeto, você pode organizá-lo no formulário.</span><span class="sxs-lookup"><span data-stu-id="5a116-121">After you add a WPF control to the project, you can arrange it on the form.</span></span>  
  
#### <a name="to-create-wpf-controls"></a><span data-ttu-id="5a116-122">Para criar controles WPF</span><span class="sxs-lookup"><span data-stu-id="5a116-122">To create WPF controls</span></span>  
  
1.  <span data-ttu-id="5a116-123">Adicione um novo WPF <xref:System.Windows.Controls.UserControl> ao projeto.</span><span class="sxs-lookup"><span data-stu-id="5a116-123">Add a new WPF <xref:System.Windows.Controls.UserControl> to the project.</span></span> <span data-ttu-id="5a116-124">Use o nome padrão do tipo de controle, `UserControl1.xaml`.</span><span class="sxs-lookup"><span data-stu-id="5a116-124">Use the default name for the control type, `UserControl1.xaml`.</span></span> <span data-ttu-id="5a116-125">Para obter mais informações, consulte [Instruções passo a passo: como criar novo conteúdo WPF nos Windows Forms em tempo de design](../../../../docs/framework/winforms/advanced/walkthrough-creating-new-wpf-content-on-windows-forms-at-design-time.md).</span><span class="sxs-lookup"><span data-stu-id="5a116-125">For more information, see [Walkthrough: Creating New WPF Content on Windows Forms at Design Time](../../../../docs/framework/winforms/advanced/walkthrough-creating-new-wpf-content-on-windows-forms-at-design-time.md).</span></span>  
  
2.  <span data-ttu-id="5a116-126">No **propriedades** janela, defina o valor da <xref:System.Windows.Controls.Control.Background%2A> propriedade `Blue`.</span><span class="sxs-lookup"><span data-stu-id="5a116-126">In the **Properties** window, set the value of the <xref:System.Windows.Controls.Control.Background%2A> property to `Blue`.</span></span>  
  
3.  <span data-ttu-id="5a116-127">Compile o projeto.</span><span class="sxs-lookup"><span data-stu-id="5a116-127">Build the project.</span></span>  
  
## <a name="changing-property-values-on-the-wpf-control"></a><span data-ttu-id="5a116-128">Alterando os valores de propriedade no controle do WPF</span><span class="sxs-lookup"><span data-stu-id="5a116-128">Changing Property Values on the WPF Control</span></span>  
 <span data-ttu-id="5a116-129">O <xref:System.Windows.Forms.Integration.ElementHost> marca inteligente torna mais fácil alterar as propriedades de WPF hospedado conteúdo usando o Designer do WPF.</span><span class="sxs-lookup"><span data-stu-id="5a116-129">The <xref:System.Windows.Forms.Integration.ElementHost> smart tag makes it easy to change properties of hosted WPF content by using the WPF Designer.</span></span>  
  
#### <a name="to-host-a-wpf-control"></a><span data-ttu-id="5a116-130">Para hospedar um controle WPF</span><span class="sxs-lookup"><span data-stu-id="5a116-130">To host a WPF control</span></span>  
  
1.  <span data-ttu-id="5a116-131">Abra `Form1` no Designer de Formulários do Windows.</span><span class="sxs-lookup"><span data-stu-id="5a116-131">Open `Form1` in the Windows Forms Designer.</span></span>  
  
2.  <span data-ttu-id="5a116-132">Na **Caixa de ferramentas**, na guia **Controles de usuário do WPF**, clique duas vezes em `UserControl1` para criar uma instância de `UserControl1` no formulário.</span><span class="sxs-lookup"><span data-stu-id="5a116-132">In the **Toolbox**, in the **WPF User Controls** tab, double-click `UserControl1` to create an instance of `UserControl1` on the form.</span></span>  
  
     <span data-ttu-id="5a116-133">A instância do `UserControl1` está hospedada em um novo <xref:System.Windows.Forms.Integration.ElementHost> controle chamado `elementHost1`.</span><span class="sxs-lookup"><span data-stu-id="5a116-133">The instance of `UserControl1` is hosted in a new <xref:System.Windows.Forms.Integration.ElementHost> control named `elementHost1`.</span></span>  
  
3.  <span data-ttu-id="5a116-134">No painel de smart tag **ElementHost Tasks**, selecione **Editar conteúdo hospedado**.</span><span class="sxs-lookup"><span data-stu-id="5a116-134">In the **ElementHost Tasks** smart tag panel, select **Edit Hosted Content**.</span></span>  
  
     <span data-ttu-id="5a116-135">O UserControl1.xaml se abre no Designer do WPF.</span><span class="sxs-lookup"><span data-stu-id="5a116-135">UserControl1.xaml opens in the WPF Designer.</span></span>  
  
4.  <span data-ttu-id="5a116-136">No **propriedades** janela, defina o valor da <xref:System.Windows.Controls.Control.Background%2A> propriedade `Red`.</span><span class="sxs-lookup"><span data-stu-id="5a116-136">In the **Properties** window, set the value of the <xref:System.Windows.Controls.Control.Background%2A> property to `Red`.</span></span>  
  
5.  <span data-ttu-id="5a116-137">Recompile o projeto.</span><span class="sxs-lookup"><span data-stu-id="5a116-137">Rebuild the project.</span></span>  
  
6.  <span data-ttu-id="5a116-138">Abra `Form1` no Designer de Formulários do Windows.</span><span class="sxs-lookup"><span data-stu-id="5a116-138">Open `Form1` in the Windows Forms Designer.</span></span>  
  
     <span data-ttu-id="5a116-139">A instância do `UserControl1` tem uma tela de fundo vermelha.</span><span class="sxs-lookup"><span data-stu-id="5a116-139">The instance of `UserControl1` has a red background.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5a116-140">Consulte também</span><span class="sxs-lookup"><span data-stu-id="5a116-140">See Also</span></span>  
 <xref:System.Windows.Forms.Integration.ElementHost>  
 <xref:System.Windows.Forms.Integration.WindowsFormsHost>  
 [<span data-ttu-id="5a116-141">Como ancorar e encaixar controles filho em um controle TableLayoutPanel</span><span class="sxs-lookup"><span data-stu-id="5a116-141">How to: Anchor and Dock Child Controls in a TableLayoutPanel Control</span></span>](../../../../docs/framework/winforms/controls/how-to-anchor-and-dock-child-controls-in-a-tablelayoutpanel-control.md)  
 [<span data-ttu-id="5a116-142">Como alinhar um controle às bordas de formulários no tempo de design</span><span class="sxs-lookup"><span data-stu-id="5a116-142">How to: Align a Control to the Edges of Forms at Design Time</span></span>](../../../../docs/framework/winforms/controls/how-to-align-a-control-to-the-edges-of-forms-at-design-time.md)  
 [<span data-ttu-id="5a116-143">Instruções passo a passo: organizando controles no Windows Forms usando guias de alinhamento</span><span class="sxs-lookup"><span data-stu-id="5a116-143">Walkthrough: Arranging Controls on Windows Forms Using Snaplines</span></span>](../../../../docs/framework/winforms/controls/walkthrough-arranging-controls-on-windows-forms-using-snaplines.md)  
 [<span data-ttu-id="5a116-144">Migração e interoperabilidade</span><span class="sxs-lookup"><span data-stu-id="5a116-144">Migration and Interoperability</span></span>](../../../../docs/framework/wpf/advanced/migration-and-interoperability.md)  
 [<span data-ttu-id="5a116-145">Usando Controles do WPF</span><span class="sxs-lookup"><span data-stu-id="5a116-145">Using WPF Controls</span></span>](../../../../docs/framework/winforms/advanced/using-wpf-controls.md)  
 [<span data-ttu-id="5a116-146">Designer do WPF</span><span class="sxs-lookup"><span data-stu-id="5a116-146">WPF Designer</span></span>](http://msdn.microsoft.com/library/c6c65214-8411-4e16-b254-163ed4099c26)
