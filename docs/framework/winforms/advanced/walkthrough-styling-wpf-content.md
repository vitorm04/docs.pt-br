---
title: 'Passo a passo: definir o estilo do conteúdo do WPF'
ms.date: 03/30/2017
helpviewer_keywords:
- WPF Designer [Windows Forms], styling WPF content
- interoperability [WDF]
- styles [Windows Forms], WPF content
ms.assetid: e574aac7-7ea4-4cdb-8034-bab541f000df
ms.openlocfilehash: 32ca9658ddf4ab6e8690f29797b7ac7b09df2ca7
ms.sourcegitcommit: d98fdb087d9c8aba7d2cb93fe4b4ee35a2308cee
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/14/2019
ms.locfileid: "69012952"
---
# <a name="walkthrough-style-wpf-content"></a><span data-ttu-id="6f253-102">Passo a passo: Conteúdo do WPF de estilo</span><span class="sxs-lookup"><span data-stu-id="6f253-102">Walkthrough: Style WPF content</span></span>

<span data-ttu-id="6f253-103">Essa instrução passo a passo mostra como aplicar estilos a um controle WPF (Windows Presentation Foundation) hospedado em um Windows Form.</span><span class="sxs-lookup"><span data-stu-id="6f253-103">This walkthrough show you how to apply styling to a Windows Presentation Foundation (WPF) control hosted on a Windows Form.</span></span>

 <span data-ttu-id="6f253-104">Nesta instrução passo a passo, as seguintes tarefas serão executadas:</span><span class="sxs-lookup"><span data-stu-id="6f253-104">In this walkthrough, you perform the following tasks:</span></span>

- <span data-ttu-id="6f253-105">Crie o projeto.</span><span class="sxs-lookup"><span data-stu-id="6f253-105">Create the project.</span></span>

- <span data-ttu-id="6f253-106">Crie o tipo de controle WPF.</span><span class="sxs-lookup"><span data-stu-id="6f253-106">Create the WPF control type.</span></span>

- <span data-ttu-id="6f253-107">Aplique um estilo ao controle do WPF.</span><span class="sxs-lookup"><span data-stu-id="6f253-107">Apply a style to the WPF control.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="6f253-108">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="6f253-108">Prerequisites</span></span>

<span data-ttu-id="6f253-109">É necessário o Visual Studio para concluir este passo a passo.</span><span class="sxs-lookup"><span data-stu-id="6f253-109">You need Visual Studio to complete this walkthrough.</span></span>

## <a name="create-the-project"></a><span data-ttu-id="6f253-110">Criar o projeto</span><span class="sxs-lookup"><span data-stu-id="6f253-110">Create the project</span></span>

<span data-ttu-id="6f253-111">Abra o Visual Studio e crie um novo projeto de aplicativo Windows Forms em Visual Basic C# ou `StylingWpfContent`Visual chamado.</span><span class="sxs-lookup"><span data-stu-id="6f253-111">Open Visual Studio and create a new Windows Forms Application project in Visual Basic or Visual C# named `StylingWpfContent`.</span></span>

> [!NOTE]
> <span data-ttu-id="6f253-112">Ao hospedar conteúdo do WPF, haverá suporte apenas para projetos em C# e Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="6f253-112">When hosting WPF content, only C# and Visual Basic projects are supported.</span></span>

## <a name="create-the-wpf-control-types"></a><span data-ttu-id="6f253-113">Criar os tipos de controle do WPF</span><span class="sxs-lookup"><span data-stu-id="6f253-113">Create the WPF control types</span></span>

<span data-ttu-id="6f253-114">Depois de adicionar um tipo de controle do WPF ao projeto, você pode hospedá-lo <xref:System.Windows.Forms.Integration.ElementHost> em um controle.</span><span class="sxs-lookup"><span data-stu-id="6f253-114">After you add a WPF control type to the project, you can host it in an <xref:System.Windows.Forms.Integration.ElementHost> control.</span></span>

1. <span data-ttu-id="6f253-115">Adicione um novo projeto <xref:System.Windows.Controls.UserControl> do WPF à solução.</span><span class="sxs-lookup"><span data-stu-id="6f253-115">Add a new WPF <xref:System.Windows.Controls.UserControl> project to the solution.</span></span> <span data-ttu-id="6f253-116">Use o nome padrão do tipo de controle, `UserControl1.xaml`.</span><span class="sxs-lookup"><span data-stu-id="6f253-116">Use the default name for the control type, `UserControl1.xaml`.</span></span> <span data-ttu-id="6f253-117">Para obter mais informações, confira [Passo a passo: Criando novo conteúdo do WPF em Windows Forms em tempo](walkthrough-creating-new-wpf-content-on-windows-forms-at-design-time.md)de design.</span><span class="sxs-lookup"><span data-stu-id="6f253-117">For more information, see [Walkthrough: Creating New WPF Content on Windows Forms at Design Time](walkthrough-creating-new-wpf-content-on-windows-forms-at-design-time.md).</span></span>

2. <span data-ttu-id="6f253-118">No modo de exibição de Design, verifique se `UserControl1` está selecionado.</span><span class="sxs-lookup"><span data-stu-id="6f253-118">In Design view, make sure that `UserControl1` is selected.</span></span> <span data-ttu-id="6f253-119">Para obter mais informações, confira [Como: Selecione e mova elementos no Design Surface](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/bb514527(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="6f253-119">For more information, see [How to: Select and Move Elements on the Design Surface](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/bb514527(v=vs.100)).</span></span>

3. <span data-ttu-id="6f253-120">Na janela **Propriedades** , defina o valor das <xref:System.Windows.FrameworkElement.Width%2A> Propriedades e <xref:System.Windows.FrameworkElement.Height%2A> como `200`.</span><span class="sxs-lookup"><span data-stu-id="6f253-120">In the **Properties** window, set the value of the <xref:System.Windows.FrameworkElement.Width%2A> and <xref:System.Windows.FrameworkElement.Height%2A> properties to `200`.</span></span>

4. <span data-ttu-id="6f253-121">Adicione um <xref:System.Windows.Controls.Button?displayProperty=nameWithType> <xref:System.Windows.Controls.UserControl> controle ao e <xref:System.Windows.Controls.ContentControl.Content%2A> defina o valor da propriedade como **Cancelar**.</span><span class="sxs-lookup"><span data-stu-id="6f253-121">Add a <xref:System.Windows.Controls.Button?displayProperty=nameWithType> control to the <xref:System.Windows.Controls.UserControl> and set the value of the <xref:System.Windows.Controls.ContentControl.Content%2A> property to **Cancel**.</span></span>

5. <span data-ttu-id="6f253-122">Adicione um segundo <xref:System.Windows.Controls.Button?displayProperty=nameWithType> controle <xref:System.Windows.Controls.UserControl> ao e <xref:System.Windows.Controls.ContentControl.Content%2A> defina o valor da propriedade como **OK**.</span><span class="sxs-lookup"><span data-stu-id="6f253-122">Add a second <xref:System.Windows.Controls.Button?displayProperty=nameWithType> control to the <xref:System.Windows.Controls.UserControl> and set the value of the <xref:System.Windows.Controls.ContentControl.Content%2A> property to **OK**.</span></span>

6. <span data-ttu-id="6f253-123">Compile o projeto.</span><span class="sxs-lookup"><span data-stu-id="6f253-123">Build the project.</span></span>

## <a name="apply-a-style-to-a-wpf-control"></a><span data-ttu-id="6f253-124">Aplicar um estilo a um controle WPF</span><span class="sxs-lookup"><span data-stu-id="6f253-124">Apply a Style to a WPF Control</span></span>

<span data-ttu-id="6f253-125">Você pode aplicar um estilo diferente a um controle WPF para alterar sua aparência e comportamento.</span><span class="sxs-lookup"><span data-stu-id="6f253-125">You can apply different styling to a WPF control to change its appearance and behavior.</span></span>

1. <span data-ttu-id="6f253-126">Abra `Form1` no Designer de Formulários do Windows.</span><span class="sxs-lookup"><span data-stu-id="6f253-126">Open `Form1` in the Windows Forms Designer.</span></span>

1. <span data-ttu-id="6f253-127">Na **Caixa de ferramentas**, clique duas vezes em `UserControl1` para criar uma instância de `UserControl1` no formulário.</span><span class="sxs-lookup"><span data-stu-id="6f253-127">In the **Toolbox**, double-click `UserControl1` to create an instance of `UserControl1` on the form.</span></span>

     <span data-ttu-id="6f253-128">Uma instância do `UserControl1` é hospedada em um <xref:System.Windows.Forms.Integration.ElementHost> novo controle `elementHost1`chamado.</span><span class="sxs-lookup"><span data-stu-id="6f253-128">An instance of `UserControl1` is hosted in a new <xref:System.Windows.Forms.Integration.ElementHost> control named `elementHost1`.</span></span>

1. <span data-ttu-id="6f253-129">No painel de smart tag para `elementHost1`, clique em **Editar conteúdo hospedado** na lista suspensa.</span><span class="sxs-lookup"><span data-stu-id="6f253-129">In the smart tag panel for `elementHost1`, click **Edit Hosted Content** from the drop-down list.</span></span>

     <span data-ttu-id="6f253-130">`UserControl1` é aberto no [!INCLUDE[wpfdesigner_current_short](../../../../includes/wpfdesigner-current-short-md.md)].</span><span class="sxs-lookup"><span data-stu-id="6f253-130">`UserControl1` opens in the [!INCLUDE[wpfdesigner_current_short](../../../../includes/wpfdesigner-current-short-md.md)].</span></span>

1. <span data-ttu-id="6f253-131">Na exibição XAML, insira o seguinte XAML após a marca de abertura `<UserControl>`.</span><span class="sxs-lookup"><span data-stu-id="6f253-131">In XAML view, insert the following XAML after the `<UserControl>` opening tag.</span></span>

     <span data-ttu-id="6f253-132">Esse XAML cria um gradiente com uma borda gradiente de contraste.</span><span class="sxs-lookup"><span data-stu-id="6f253-132">This XAML creates a gradient with a contrasting gradient border.</span></span> <span data-ttu-id="6f253-133">Ao clicar no controle, os gradientes são alterados para gerar uma aparência de botão pressionado.</span><span class="sxs-lookup"><span data-stu-id="6f253-133">When the control is clicked, the gradients are changed to generate a pressed button look.</span></span> <span data-ttu-id="6f253-134">Para obter mais informações, consulte [Estilo e modelagem](../../wpf/controls/styling-and-templating.md).</span><span class="sxs-lookup"><span data-stu-id="6f253-134">For more information, see [Styling and Templating](../../wpf/controls/styling-and-templating.md).</span></span>

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

1. <span data-ttu-id="6f253-135">Aplique o estilo `SimpleButton` definido na etapa anterior para o botão Cancelar inserindo o seguinte XAML na marca `<Button>` do botão Cancelar.</span><span class="sxs-lookup"><span data-stu-id="6f253-135">Apply the `SimpleButton` style defined in the previous step to the Cancel button by inserting the following XAML in the `<Button>` tag of the Cancel button.</span></span>

   ```xaml
   Style="{StaticResource SimpleButton}
   ```

   <span data-ttu-id="6f253-136">A declaração do botão será semelhante ao seguinte XAML:</span><span class="sxs-lookup"><span data-stu-id="6f253-136">Your button declaration will resemble the following XAML:</span></span>

   ```xaml
   <Button Height="23" Margin="41,52,98,0" Name="button1" VerticalAlignment="Top"
                Style="{StaticResource SimpleButton}">Cancel</Button>
   ```

1. <span data-ttu-id="6f253-137">Compile o projeto.</span><span class="sxs-lookup"><span data-stu-id="6f253-137">Build the project.</span></span>

1. <span data-ttu-id="6f253-138">Abra `Form1` no Designer de Formulários do Windows.</span><span class="sxs-lookup"><span data-stu-id="6f253-138">Open `Form1` in the Windows Forms Designer.</span></span>

1. <span data-ttu-id="6f253-139">O novo estilo é aplicado ao controle de botão.</span><span class="sxs-lookup"><span data-stu-id="6f253-139">The new style is applied to the button control.</span></span>

1. <span data-ttu-id="6f253-140">No menu **Depuração**, selecione **Iniciar Depuração** para executar o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="6f253-140">From the **Debug** menu, select **Start Debugging** to run the application.</span></span>

1. <span data-ttu-id="6f253-141">Clique nos botões OK e Cancelar e exibir as diferenças.</span><span class="sxs-lookup"><span data-stu-id="6f253-141">Click the OK and Cancel buttons and view the differences.</span></span>

## <a name="see-also"></a><span data-ttu-id="6f253-142">Consulte também</span><span class="sxs-lookup"><span data-stu-id="6f253-142">See also</span></span>

- <xref:System.Windows.Forms.Integration.ElementHost>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost>
- [<span data-ttu-id="6f253-143">Migração e interoperabilidade</span><span class="sxs-lookup"><span data-stu-id="6f253-143">Migration and Interoperability</span></span>](../../wpf/advanced/migration-and-interoperability.md)
- [<span data-ttu-id="6f253-144">Usando Controles do WPF</span><span class="sxs-lookup"><span data-stu-id="6f253-144">Using WPF Controls</span></span>](using-wpf-controls.md)
- [<span data-ttu-id="6f253-145">Criar o XAML no Visual Studio</span><span class="sxs-lookup"><span data-stu-id="6f253-145">Design XAML in Visual Studio</span></span>](/visualstudio/designers/designing-xaml-in-visual-studio)
- [<span data-ttu-id="6f253-146">Visão geral de XAML (WPF)</span><span class="sxs-lookup"><span data-stu-id="6f253-146">XAML Overview (WPF)</span></span>](../../wpf/advanced/xaml-overview-wpf.md)
- [<span data-ttu-id="6f253-147">Estilo e modelagem</span><span class="sxs-lookup"><span data-stu-id="6f253-147">Styling and Templating</span></span>](../../wpf/controls/styling-and-templating.md)
