---
title: "Instruções passo a passo: criando o conteúdo WPF"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- WPF Designer [Windows Forms], styling WPF content
- interoperability [WDF]
- styles [Windows Forms], WPF content
ms.assetid: e574aac7-7ea4-4cdb-8034-bab541f000df
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: ae150e93958b622a772258ab41fa4281014dd567
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/19/2018
---
# <a name="walkthrough-styling-wpf-content"></a><span data-ttu-id="7a9fc-102">Instruções passo a passo: criando o conteúdo WPF</span><span class="sxs-lookup"><span data-stu-id="7a9fc-102">Walkthrough: Styling WPF Content</span></span>
<span data-ttu-id="7a9fc-103">Essa instrução passo a passo mostra como aplicar estilos a um controle WPF (Windows Presentation Foundation) hospedado em um Windows Form.</span><span class="sxs-lookup"><span data-stu-id="7a9fc-103">This walkthrough show you how to apply styling to a Windows Presentation Foundation (WPF) control hosted on a Windows Form.</span></span>  
  
 <span data-ttu-id="7a9fc-104">Nesta instrução passo a passo, as seguintes tarefas serão executadas:</span><span class="sxs-lookup"><span data-stu-id="7a9fc-104">In this walkthrough, you perform the following tasks:</span></span>  
  
-   <span data-ttu-id="7a9fc-105">Crie o projeto.</span><span class="sxs-lookup"><span data-stu-id="7a9fc-105">Create the project.</span></span>  
  
-   <span data-ttu-id="7a9fc-106">Crie o tipo de controle WPF.</span><span class="sxs-lookup"><span data-stu-id="7a9fc-106">Create the WPF control type.</span></span>  
  
-   <span data-ttu-id="7a9fc-107">Aplique um estilo ao controle do WPF.</span><span class="sxs-lookup"><span data-stu-id="7a9fc-107">Apply a style to the WPF control.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="7a9fc-108">As caixas de diálogo e os comandos de menu que você vê podem ser diferentes dos descritos na Ajuda, dependendo da sua edição ou das configurações ativas.</span><span class="sxs-lookup"><span data-stu-id="7a9fc-108">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="7a9fc-109">Para alterar as configurações, escolha **Importar e Exportar Configurações** no menu **Ferramentas**.</span><span class="sxs-lookup"><span data-stu-id="7a9fc-109">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="7a9fc-110">Para obter mais informações, consulte [Personalizando configurações de desenvolvimento no Visual Studio](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span><span class="sxs-lookup"><span data-stu-id="7a9fc-110">For more information, see [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="7a9fc-111">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="7a9fc-111">Prerequisites</span></span>  
 <span data-ttu-id="7a9fc-112">Você precisa dos seguintes componentes para concluir esta instrução passo a passo:</span><span class="sxs-lookup"><span data-stu-id="7a9fc-112">You need the following components to complete this walkthrough:</span></span>  
  
-   [!INCLUDE[vs_dev11_long](../../../../includes/vs-dev11-long-md.md)]<span data-ttu-id="7a9fc-113">.</span><span class="sxs-lookup"><span data-stu-id="7a9fc-113">.</span></span>  
  
## <a name="creating-the-project"></a><span data-ttu-id="7a9fc-114">Criando o Projeto</span><span class="sxs-lookup"><span data-stu-id="7a9fc-114">Creating the Project</span></span>  
 <span data-ttu-id="7a9fc-115">A primeira etapa é criar o projeto dos Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="7a9fc-115">The first step is to create the Windows Forms project.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="7a9fc-116">Ao hospedar conteúdo do WPF, haverá suporte apenas para projetos em C# e Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="7a9fc-116">When hosting WPF content, only C# and Visual Basic projects are supported.</span></span>  
  
#### <a name="to-create-the-project"></a><span data-ttu-id="7a9fc-117">Para criar o projeto</span><span class="sxs-lookup"><span data-stu-id="7a9fc-117">To create the project</span></span>  
  
-   <span data-ttu-id="7a9fc-118">Crie um novo projeto de Aplicativo dos Windows Forms no Visual Basic ou Visual C# chamado `StylingWpfContent`.</span><span class="sxs-lookup"><span data-stu-id="7a9fc-118">Create a new Windows Forms Application project in Visual Basic or Visual C# named `StylingWpfContent`.</span></span>  
  
## <a name="creating-the-wpf-control-types"></a><span data-ttu-id="7a9fc-119">Criando tipos de controle WPF</span><span class="sxs-lookup"><span data-stu-id="7a9fc-119">Creating the WPF Control Types</span></span>  
 <span data-ttu-id="7a9fc-120">Depois de adicionar um tipo de controle WPF ao projeto, você pode hospedá-lo em um <xref:System.Windows.Forms.Integration.ElementHost> controle.</span><span class="sxs-lookup"><span data-stu-id="7a9fc-120">After you add a WPF control type to the project, you can host it in an <xref:System.Windows.Forms.Integration.ElementHost> control.</span></span>  
  
#### <a name="to-create-wpf-control-types"></a><span data-ttu-id="7a9fc-121">Criar tipos de controle WPF</span><span class="sxs-lookup"><span data-stu-id="7a9fc-121">To create WPF control types</span></span>  
  
1.  <span data-ttu-id="7a9fc-122">Adicione um novo WPF <xref:System.Windows.Controls.UserControl> projeto à solução.</span><span class="sxs-lookup"><span data-stu-id="7a9fc-122">Add a new WPF <xref:System.Windows.Controls.UserControl> project to the solution.</span></span> <span data-ttu-id="7a9fc-123">Use o nome padrão do tipo de controle, `UserControl1.xaml`.</span><span class="sxs-lookup"><span data-stu-id="7a9fc-123">Use the default name for the control type, `UserControl1.xaml`.</span></span> <span data-ttu-id="7a9fc-124">Para obter mais informações, consulte [Instruções passo a passo: como criar novo conteúdo WPF nos Windows Forms em tempo de design](../../../../docs/framework/winforms/advanced/walkthrough-creating-new-wpf-content-on-windows-forms-at-design-time.md).</span><span class="sxs-lookup"><span data-stu-id="7a9fc-124">For more information, see [Walkthrough: Creating New WPF Content on Windows Forms at Design Time](../../../../docs/framework/winforms/advanced/walkthrough-creating-new-wpf-content-on-windows-forms-at-design-time.md).</span></span>  
  
2.  <span data-ttu-id="7a9fc-125">No modo de exibição de Design, verifique se `UserControl1` está selecionado.</span><span class="sxs-lookup"><span data-stu-id="7a9fc-125">In Design view, make sure that `UserControl1` is selected.</span></span> <span data-ttu-id="7a9fc-126">Para obter mais informações, consulte [Como Selecionar e Mover Elementos na Superfície de Design](http://msdn.microsoft.com/library/54cb70b6-b35b-46e4-a0cc-65189399c474).</span><span class="sxs-lookup"><span data-stu-id="7a9fc-126">For more information, see [How to: Select and Move Elements on the Design Surface](http://msdn.microsoft.com/library/54cb70b6-b35b-46e4-a0cc-65189399c474).</span></span>  
  
3.  <span data-ttu-id="7a9fc-127">No **propriedades** janela, defina o valor da <xref:System.Windows.FrameworkElement.Width%2A> e <xref:System.Windows.FrameworkElement.Height%2A> propriedades `200`.</span><span class="sxs-lookup"><span data-stu-id="7a9fc-127">In the **Properties** window, set the value of the <xref:System.Windows.FrameworkElement.Width%2A> and <xref:System.Windows.FrameworkElement.Height%2A> properties to `200`.</span></span>  
  
4.  <span data-ttu-id="7a9fc-128">Adicionar um <xref:System.Windows.Controls.Button?displayProperty=nameWithType> o controle para o <xref:System.Windows.Controls.UserControl> e defina o valor da <xref:System.Windows.Controls.ContentControl.Content%2A> propriedade **Cancelar**.</span><span class="sxs-lookup"><span data-stu-id="7a9fc-128">Add a <xref:System.Windows.Controls.Button?displayProperty=nameWithType> control to the <xref:System.Windows.Controls.UserControl> and set the value of the <xref:System.Windows.Controls.ContentControl.Content%2A> property to **Cancel**.</span></span>  
  
5.  <span data-ttu-id="7a9fc-129">Adicionar um segundo <xref:System.Windows.Controls.Button?displayProperty=nameWithType> o controle para o <xref:System.Windows.Controls.UserControl> e defina o valor da <xref:System.Windows.Controls.ContentControl.Content%2A> propriedade **Okey**.</span><span class="sxs-lookup"><span data-stu-id="7a9fc-129">Add a second <xref:System.Windows.Controls.Button?displayProperty=nameWithType> control to the <xref:System.Windows.Controls.UserControl> and set the value of the <xref:System.Windows.Controls.ContentControl.Content%2A> property to **OK**.</span></span>  
  
6.  <span data-ttu-id="7a9fc-130">Compile o projeto.</span><span class="sxs-lookup"><span data-stu-id="7a9fc-130">Build the project.</span></span>  
  
## <a name="applying-a-style-to-a-wpf-control"></a><span data-ttu-id="7a9fc-131">Aplicando um estilo a um controle do WPF</span><span class="sxs-lookup"><span data-stu-id="7a9fc-131">Applying a Style to a WPF Control</span></span>  
 <span data-ttu-id="7a9fc-132">Você pode aplicar um estilo diferente a um controle WPF para alterar sua aparência e comportamento.</span><span class="sxs-lookup"><span data-stu-id="7a9fc-132">You can apply different styling to a WPF control to change its appearance and behavior.</span></span>  
  
#### <a name="to-apply-a-style-to-a-wpf-control"></a><span data-ttu-id="7a9fc-133">Aplicar um estilo a um controle do WPF</span><span class="sxs-lookup"><span data-stu-id="7a9fc-133">To apply a style to a WPF control</span></span>  
  
1.  <span data-ttu-id="7a9fc-134">Abra `Form1` no Designer de Formulários do Windows.</span><span class="sxs-lookup"><span data-stu-id="7a9fc-134">Open `Form1` in the Windows Forms Designer.</span></span>  
  
2.  <span data-ttu-id="7a9fc-135">Na **Caixa de ferramentas**, clique duas vezes em `UserControl1` para criar uma instância de `UserControl1` no formulário.</span><span class="sxs-lookup"><span data-stu-id="7a9fc-135">In the **Toolbox**, double-click `UserControl1` to create an instance of `UserControl1` on the form.</span></span>  
  
     <span data-ttu-id="7a9fc-136">Uma instância de `UserControl1` está hospedada em um novo <xref:System.Windows.Forms.Integration.ElementHost> controle chamado `elementHost1`.</span><span class="sxs-lookup"><span data-stu-id="7a9fc-136">An instance of `UserControl1` is hosted in a new <xref:System.Windows.Forms.Integration.ElementHost> control named `elementHost1`.</span></span>  
  
3.  <span data-ttu-id="7a9fc-137">No painel de smart tag para `elementHost1`, clique em **Editar conteúdo hospedado** na lista suspensa.</span><span class="sxs-lookup"><span data-stu-id="7a9fc-137">In the smart tag panel for `elementHost1`, click **Edit Hosted Content** from the drop-down list.</span></span>  
  
     <span data-ttu-id="7a9fc-138">`UserControl1` é aberto no [!INCLUDE[wpfdesigner_current_short](../../../../includes/wpfdesigner-current-short-md.md)].</span><span class="sxs-lookup"><span data-stu-id="7a9fc-138">`UserControl1` opens in the [!INCLUDE[wpfdesigner_current_short](../../../../includes/wpfdesigner-current-short-md.md)].</span></span>  
  
4.  <span data-ttu-id="7a9fc-139">Na exibição XAML, insira o seguinte XAML após a marca de abertura `<UserControl>`.</span><span class="sxs-lookup"><span data-stu-id="7a9fc-139">In XAML view, insert the following XAML after the `<UserControl>` opening tag.</span></span>  
  
     <span data-ttu-id="7a9fc-140">Esse XAML cria um gradiente com uma borda gradiente de contraste.</span><span class="sxs-lookup"><span data-stu-id="7a9fc-140">This XAML creates a gradient with a contrasting gradient border.</span></span> <span data-ttu-id="7a9fc-141">Ao clicar no controle, os gradientes são alterados para gerar uma aparência de botão pressionado.</span><span class="sxs-lookup"><span data-stu-id="7a9fc-141">When the control is clicked, the gradients are changed to generate a pressed button look.</span></span> <span data-ttu-id="7a9fc-142">Para obter mais informações, consulte [Estilo e modelagem](../../../../docs/framework/wpf/controls/styling-and-templating.md).</span><span class="sxs-lookup"><span data-stu-id="7a9fc-142">For more information, see [Styling and Templating](../../../../docs/framework/wpf/controls/styling-and-templating.md).</span></span>  
  
```xaml  
<UserControl.Resources>  
    <LinearGradientBrush x:Key="NormalBrush" EndPoint="0,1" StartPoint="0,0">  
        <GradientStop Color="#FFF" Offset="0.0"/>  
        <GradientStop Color="#CCC" Offset="1.0"/>  
    </LinearGradientBrush>  
    <LinearGradientBrush x:Key="PressedBrush" EndPoint="0,1" StartPoint="0,0">  
        <GradientStop Color="#BBB" Offset="0.0"/>  
        <GradientStop Color="#EEE" Offset="0.1"/>  
        <GradientStop Color="#EEE" Offset="0.9"/>  
        <GradientStop Color="#FFF" Offset="1.0"/>  
    </LinearGradientBrush>  
    <LinearGradientBrush x:Key="NormalBorderBrush" EndPoint="0,1" StartPoint="0,0">  
        <GradientStop Color="#CCC" Offset="0.0"/>  
        <GradientStop Color="#444" Offset="1.0"/>  
    </LinearGradientBrush>  
    <LinearGradientBrush x:Key="BorderBrush" EndPoint="0,1" StartPoint="0,0">  
        <GradientStop Color="#CCC" Offset="0.0"/>  
        <GradientStop Color="#444" Offset="1.0"/>  
    </LinearGradientBrush>  
    <LinearGradientBrush x:Key="PressedBorderBrush" EndPoint="0,1" StartPoint="0,0">  
        <GradientStop Color="#444" Offset="0.0"/>  
        <GradientStop Color="#888" Offset="1.0"/>  
    </LinearGradientBrush>  
  
    <Style x:Key="SimpleButton" TargetType="{x:Type Button}" BasedOn="{x:Null}">  
        <Setter Property="Background" Value="{StaticResource NormalBrush}"/>  
        <Setter Property="BorderBrush" Value="{StaticResource NormalBorderBrush}"/>  
        <Setter Property="Template">  
            <Setter.Value>  
                <ControlTemplate TargetType="{x:Type Button}">  
                    <Grid x:Name="Grid">  
                        <Border x:Name="Border" Background="{TemplateBinding Background}" BorderBrush="{TemplateBinding BorderBrush}" BorderThickness="{TemplateBinding BorderThickness}" Padding="{TemplateBinding Padding}"/>  
                        <ContentPresenter HorizontalAlignment="{TemplateBinding HorizontalContentAlignment}" Margin="{TemplateBinding Padding}" VerticalAlignment="{TemplateBinding VerticalContentAlignment}" RecognizesAccessKey="True"/>  
                    </Grid>  
                    <ControlTemplate.Triggers>  
                        <Trigger Property="IsPressed" Value="true">  
                            <Setter Property="Background" Value="{StaticResource PressedBrush}" TargetName="Border"/>  
                            <Setter Property="BorderBrush" Value="{StaticResource PressedBorderBrush}" TargetName="Border"/>  
                        </Trigger>  
                    </ControlTemplate.Triggers>  
                </ControlTemplate>  
            </Setter.Value>  
        </Setter>  
    </Style>  
</UserControl.Resources>  
```  
  
1.  <span data-ttu-id="7a9fc-143">Aplique o estilo `SimpleButton` definido na etapa anterior para o botão Cancelar inserindo o seguinte XAML na marca `<Button>` do botão Cancelar.</span><span class="sxs-lookup"><span data-stu-id="7a9fc-143">Apply the `SimpleButton` style defined in the previous step to the Cancel button by inserting the following XAML in the `<Button>` tag of the Cancel button.</span></span>  
  
    ```  
    Style="{StaticResource SimpleButton}  
    ```  
  
     <span data-ttu-id="7a9fc-144">Sua declaração de botão será parecida com o seguinte XAML.</span><span class="sxs-lookup"><span data-stu-id="7a9fc-144">Your button declaration will resemble the following XAML.</span></span>  
  
```xaml  
<Button Height="23" Margin="41,52,98,0" Name="button1" VerticalAlignment="Top"  
                Style="{StaticResource SimpleButton}">Cancel</Button>  
```  
  
1.  <span data-ttu-id="7a9fc-145">Compile o projeto.</span><span class="sxs-lookup"><span data-stu-id="7a9fc-145">Build the project.</span></span>  
  
2.  <span data-ttu-id="7a9fc-146">Abra `Form1` no Designer de Formulários do Windows.</span><span class="sxs-lookup"><span data-stu-id="7a9fc-146">Open `Form1` in the Windows Forms Designer.</span></span>  
  
3.  <span data-ttu-id="7a9fc-147">O novo estilo é aplicado ao controle de botão.</span><span class="sxs-lookup"><span data-stu-id="7a9fc-147">The new style is applied to the button control.</span></span>  
  
4.  <span data-ttu-id="7a9fc-148">No menu **Depuração**, selecione **Iniciar Depuração** para executar o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="7a9fc-148">From the **Debug** menu, select **Start Debugging** to run the application.</span></span>  
  
5.  <span data-ttu-id="7a9fc-149">Clique nos botões OK e Cancelar e exibir as diferenças.</span><span class="sxs-lookup"><span data-stu-id="7a9fc-149">Click the OK and Cancel buttons and view the differences.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7a9fc-150">Consulte também</span><span class="sxs-lookup"><span data-stu-id="7a9fc-150">See Also</span></span>  
 <xref:System.Windows.Forms.Integration.ElementHost>  
 <xref:System.Windows.Forms.Integration.WindowsFormsHost>  
 [<span data-ttu-id="7a9fc-151">Migração e interoperabilidade</span><span class="sxs-lookup"><span data-stu-id="7a9fc-151">Migration and Interoperability</span></span>](../../../../docs/framework/wpf/advanced/migration-and-interoperability.md)  
 [<span data-ttu-id="7a9fc-152">Usando Controles do WPF</span><span class="sxs-lookup"><span data-stu-id="7a9fc-152">Using WPF Controls</span></span>](../../../../docs/framework/winforms/advanced/using-wpf-controls.md)  
 [<span data-ttu-id="7a9fc-153">Designer do WPF</span><span class="sxs-lookup"><span data-stu-id="7a9fc-153">WPF Designer</span></span>](http://msdn.microsoft.com/library/c6c65214-8411-4e16-b254-163ed4099c26)  
 [<span data-ttu-id="7a9fc-154">Visão geral de XAML (WPF)</span><span class="sxs-lookup"><span data-stu-id="7a9fc-154">XAML Overview (WPF)</span></span>](../../../../docs/framework/wpf/advanced/xaml-overview-wpf.md)  
 [<span data-ttu-id="7a9fc-155">Estilo e modelagem</span><span class="sxs-lookup"><span data-stu-id="7a9fc-155">Styling and Templating</span></span>](../../../../docs/framework/wpf/controls/styling-and-templating.md)
