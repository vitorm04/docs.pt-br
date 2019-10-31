---
title: 'Instruções passo a passo: criando o conteúdo WPF'
ms.date: 03/30/2017
helpviewer_keywords:
- WPF Designer [Windows Forms], styling WPF content
- interoperability [WDF]
- styles [Windows Forms], WPF content
ms.assetid: e574aac7-7ea4-4cdb-8034-bab541f000df
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 8b9e2c5c05f1a4b263890c2d8ca8474abe07d836
ms.sourcegitcommit: 5a28f8eb071fcc09b045b0c4ae4b96898673192e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2019
ms.locfileid: "73197420"
---
# <a name="walkthrough-style-wpf-content"></a><span data-ttu-id="c482a-102">Walkthrough: estilo de conteúdo do WPF</span><span class="sxs-lookup"><span data-stu-id="c482a-102">Walkthrough: Style WPF content</span></span>

<span data-ttu-id="c482a-103">Este artigo mostra como aplicar o estilo a um controle Windows Presentation Foundation (WPF) hospedado em um formulário do Windows.</span><span class="sxs-lookup"><span data-stu-id="c482a-103">This article show you how to apply styling to a Windows Presentation Foundation (WPF) control hosted on a Windows Form.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="c482a-104">Prerequisites</span><span class="sxs-lookup"><span data-stu-id="c482a-104">Prerequisites</span></span>

<span data-ttu-id="c482a-105">É necessário o Visual Studio para concluir este passo a passo.</span><span class="sxs-lookup"><span data-stu-id="c482a-105">You need Visual Studio to complete this walkthrough.</span></span>

## <a name="create-the-project"></a><span data-ttu-id="c482a-106">Criar o projeto</span><span class="sxs-lookup"><span data-stu-id="c482a-106">Create the project</span></span>

<span data-ttu-id="c482a-107">Abra o Visual Studio e crie um novo projeto de aplicativo Windows Forms em Visual Basic C# ou Visual chamado `StylingWpfContent`.</span><span class="sxs-lookup"><span data-stu-id="c482a-107">Open Visual Studio and create a new Windows Forms Application project in Visual Basic or Visual C# named `StylingWpfContent`.</span></span>

> [!NOTE]
> <span data-ttu-id="c482a-108">Ao hospedar conteúdo do WPF, haverá suporte apenas para projetos em C# e Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="c482a-108">When hosting WPF content, only C# and Visual Basic projects are supported.</span></span>

## <a name="create-the-wpf-control-types"></a><span data-ttu-id="c482a-109">Criar os tipos de controle do WPF</span><span class="sxs-lookup"><span data-stu-id="c482a-109">Create the WPF control types</span></span>

<span data-ttu-id="c482a-110">Depois de adicionar um tipo de controle do WPF ao projeto, você pode hospedá-lo em um controle de <xref:System.Windows.Forms.Integration.ElementHost>.</span><span class="sxs-lookup"><span data-stu-id="c482a-110">After you add a WPF control type to the project, you can host it in an <xref:System.Windows.Forms.Integration.ElementHost> control.</span></span>

1. <span data-ttu-id="c482a-111">Adicione um novo projeto <xref:System.Windows.Controls.UserControl> do WPF à solução.</span><span class="sxs-lookup"><span data-stu-id="c482a-111">Add a new WPF <xref:System.Windows.Controls.UserControl> project to the solution.</span></span> <span data-ttu-id="c482a-112">Use o nome padrão do tipo de controle, `UserControl1.xaml`.</span><span class="sxs-lookup"><span data-stu-id="c482a-112">Use the default name for the control type, `UserControl1.xaml`.</span></span> <span data-ttu-id="c482a-113">Para obter mais informações, consulte [Instruções passo a passo: como criar novo conteúdo WPF nos Windows Forms em tempo de design](walkthrough-creating-new-wpf-content-on-windows-forms-at-design-time.md).</span><span class="sxs-lookup"><span data-stu-id="c482a-113">For more information, see [Walkthrough: Creating New WPF Content on Windows Forms at Design Time](walkthrough-creating-new-wpf-content-on-windows-forms-at-design-time.md).</span></span>

2. <span data-ttu-id="c482a-114">No modo de exibição de Design, verifique se `UserControl1` está selecionado.</span><span class="sxs-lookup"><span data-stu-id="c482a-114">In Design view, make sure that `UserControl1` is selected.</span></span>

3. <span data-ttu-id="c482a-115">Na janela **Propriedades** , defina o valor das propriedades <xref:System.Windows.FrameworkElement.Width%2A> e <xref:System.Windows.FrameworkElement.Height%2A> como **200**.</span><span class="sxs-lookup"><span data-stu-id="c482a-115">In the **Properties** window, set the value of the <xref:System.Windows.FrameworkElement.Width%2A> and <xref:System.Windows.FrameworkElement.Height%2A> properties to **200**.</span></span>

4. <span data-ttu-id="c482a-116">Adicione um controle de <xref:System.Windows.Controls.Button?displayProperty=nameWithType> à <xref:System.Windows.Controls.UserControl> e defina o valor da propriedade <xref:System.Windows.Controls.ContentControl.Content%2A> como **Cancelar**.</span><span class="sxs-lookup"><span data-stu-id="c482a-116">Add a <xref:System.Windows.Controls.Button?displayProperty=nameWithType> control to the <xref:System.Windows.Controls.UserControl> and set the value of the <xref:System.Windows.Controls.ContentControl.Content%2A> property to **Cancel**.</span></span>

5. <span data-ttu-id="c482a-117">Adicione um segundo controle de <xref:System.Windows.Controls.Button?displayProperty=nameWithType> à <xref:System.Windows.Controls.UserControl> e defina o valor da propriedade <xref:System.Windows.Controls.ContentControl.Content%2A> como **OK**.</span><span class="sxs-lookup"><span data-stu-id="c482a-117">Add a second <xref:System.Windows.Controls.Button?displayProperty=nameWithType> control to the <xref:System.Windows.Controls.UserControl> and set the value of the <xref:System.Windows.Controls.ContentControl.Content%2A> property to **OK**.</span></span>

6. <span data-ttu-id="c482a-118">Compile o projeto.</span><span class="sxs-lookup"><span data-stu-id="c482a-118">Build the project.</span></span>

## <a name="apply-a-style-to-a-wpf-control"></a><span data-ttu-id="c482a-119">Aplicar um estilo a um controle WPF</span><span class="sxs-lookup"><span data-stu-id="c482a-119">Apply a Style to a WPF Control</span></span>

<span data-ttu-id="c482a-120">Você pode aplicar um estilo diferente a um controle WPF para alterar sua aparência e comportamento.</span><span class="sxs-lookup"><span data-stu-id="c482a-120">You can apply different styling to a WPF control to change its appearance and behavior.</span></span>

1. <span data-ttu-id="c482a-121">Abra `Form1` no Designer de Formulários do Windows.</span><span class="sxs-lookup"><span data-stu-id="c482a-121">Open `Form1` in the Windows Forms Designer.</span></span>

1. <span data-ttu-id="c482a-122">Na **Caixa de ferramentas**, clique duas vezes em `UserControl1` para criar uma instância de `UserControl1` no formulário.</span><span class="sxs-lookup"><span data-stu-id="c482a-122">In the **Toolbox**, double-click `UserControl1` to create an instance of `UserControl1` on the form.</span></span>

   <span data-ttu-id="c482a-123">Uma instância de `UserControl1` é hospedada em um novo controle de <xref:System.Windows.Forms.Integration.ElementHost> chamado `elementHost1`.</span><span class="sxs-lookup"><span data-stu-id="c482a-123">An instance of `UserControl1` is hosted in a new <xref:System.Windows.Forms.Integration.ElementHost> control named `elementHost1`.</span></span>

1. <span data-ttu-id="c482a-124">No painel de smart tag para `elementHost1`, clique em **Editar conteúdo hospedado** na lista suspensa.</span><span class="sxs-lookup"><span data-stu-id="c482a-124">In the smart tag panel for `elementHost1`, click **Edit Hosted Content** from the drop-down list.</span></span>

   <span data-ttu-id="c482a-125">o `UserControl1` é aberto no designer do WPF.</span><span class="sxs-lookup"><span data-stu-id="c482a-125">`UserControl1` opens in the WPF Designer.</span></span>

1. <span data-ttu-id="c482a-126">Na exibição XAML, insira o seguinte XAML após a marca de abertura `<UserControl>`.</span><span class="sxs-lookup"><span data-stu-id="c482a-126">In XAML view, insert the following XAML after the `<UserControl>` opening tag.</span></span> <span data-ttu-id="c482a-127">Esse XAML cria um gradiente com uma borda gradiente de contraste.</span><span class="sxs-lookup"><span data-stu-id="c482a-127">This XAML creates a gradient with a contrasting gradient border.</span></span> <span data-ttu-id="c482a-128">Ao clicar no controle, os gradientes são alterados para gerar uma aparência de botão pressionado.</span><span class="sxs-lookup"><span data-stu-id="c482a-128">When the control is clicked, the gradients are changed to generate a pressed button look.</span></span> <span data-ttu-id="c482a-129">Para obter mais informações, consulte [Estilo e modelagem](../../wpf/controls/styling-and-templating.md).</span><span class="sxs-lookup"><span data-stu-id="c482a-129">For more information, see [Styling and Templating](../../wpf/controls/styling-and-templating.md).</span></span>

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

1. <span data-ttu-id="c482a-130">Aplique o estilo de `SimpleButton` definido na etapa anterior ao botão Cancelar inserindo o XAML a seguir na marca de `<Button>` do botão **Cancelar** .</span><span class="sxs-lookup"><span data-stu-id="c482a-130">Apply the `SimpleButton` style defined in the previous step to the Cancel button by inserting the following XAML in the `<Button>` tag of the **Cancel** button.</span></span>

   ```xaml
   Style="{StaticResource SimpleButton}
   ```

   <span data-ttu-id="c482a-131">A declaração do botão será semelhante ao seguinte XAML:</span><span class="sxs-lookup"><span data-stu-id="c482a-131">Your button declaration will resemble the following XAML:</span></span>

   ```xaml
   <Button Height="23" Margin="41,52,98,0" Name="button1" VerticalAlignment="Top"
                Style="{StaticResource SimpleButton}">Cancel</Button>
   ```

1. <span data-ttu-id="c482a-132">Compile o projeto.</span><span class="sxs-lookup"><span data-stu-id="c482a-132">Build the project.</span></span>

1. <span data-ttu-id="c482a-133">Abra `Form1` no Designer de Formulários do Windows.</span><span class="sxs-lookup"><span data-stu-id="c482a-133">Open `Form1` in the Windows Forms Designer.</span></span>

1. <span data-ttu-id="c482a-134">O novo estilo é aplicado ao controle de botão.</span><span class="sxs-lookup"><span data-stu-id="c482a-134">The new style is applied to the button control.</span></span>

1. <span data-ttu-id="c482a-135">No menu **Depuração**, selecione **Iniciar Depuração** para executar o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="c482a-135">From the **Debug** menu, select **Start Debugging** to run the application.</span></span>

1. <span data-ttu-id="c482a-136">Clique nos botões **OK** e **Cancelar** e exiba as diferenças.</span><span class="sxs-lookup"><span data-stu-id="c482a-136">Click the **OK** and **Cancel** buttons and view the differences.</span></span>

## <a name="see-also"></a><span data-ttu-id="c482a-137">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c482a-137">See also</span></span>

- <xref:System.Windows.Forms.Integration.ElementHost>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost>
- [<span data-ttu-id="c482a-138">Migração e Interoperabilidade</span><span class="sxs-lookup"><span data-stu-id="c482a-138">Migration and Interoperability</span></span>](../../wpf/advanced/migration-and-interoperability.md)
- [<span data-ttu-id="c482a-139">Usando Controles do WPF</span><span class="sxs-lookup"><span data-stu-id="c482a-139">Using WPF Controls</span></span>](using-wpf-controls.md)
- [<span data-ttu-id="c482a-140">Criar o XAML no Visual Studio</span><span class="sxs-lookup"><span data-stu-id="c482a-140">Design XAML in Visual Studio</span></span>](/visualstudio/xaml-tools/designing-xaml-in-visual-studio)
- [<span data-ttu-id="c482a-141">Visão geral de XAML (WPF)</span><span class="sxs-lookup"><span data-stu-id="c482a-141">XAML Overview (WPF)</span></span>](../../wpf/advanced/xaml-overview-wpf.md)
- [<span data-ttu-id="c482a-142">Estilo e modelagem</span><span class="sxs-lookup"><span data-stu-id="c482a-142">Styling and Templating</span></span>](../../wpf/controls/styling-and-templating.md)
