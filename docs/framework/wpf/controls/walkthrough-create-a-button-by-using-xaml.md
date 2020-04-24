---
title: 'Instruções passo a passo: criar um botão usando XAML'
ms.date: 03/30/2017
helpviewer_keywords:
- buttons [WPF]
ms.assetid: 138c41c4-1759-4bbf-8d77-77031a06a8a0
ms.openlocfilehash: a8cc227703e81e5de9dea7e44e10dfecca2cd05c
ms.sourcegitcommit: 62285ec11fa8e8424bab00511a90760c60e63c95
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/20/2020
ms.locfileid: "81646477"
---
# <a name="walkthrough-create-a-button-by-using-xaml"></a><span data-ttu-id="f0f85-102">Instruções passo a passo: criar um botão usando XAML</span><span class="sxs-lookup"><span data-stu-id="f0f85-102">Walkthrough: Create a Button by Using XAML</span></span>

<span data-ttu-id="f0f85-103">O objetivo deste passo a passo é aprender a criar um botão animado para uso em um aplicativo da Windows Presentation Foundation (WPF).</span><span class="sxs-lookup"><span data-stu-id="f0f85-103">The objective of this walkthrough is to learn how to create an animated button for use in a Windows Presentation Foundation (WPF) application.</span></span> <span data-ttu-id="f0f85-104">Este passo a passo usa estilos e um modelo para criar um recurso de botão personalizado que permite a reutilização de código e separação da lógica do botão da declaração do botão.</span><span class="sxs-lookup"><span data-stu-id="f0f85-104">This walkthrough uses styles and a template to create a customized button resource that allows reuse of code and separation of button logic from the button declaration.</span></span> <span data-ttu-id="f0f85-105">Este passo a passo é escrito inteiramente em [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)].</span><span class="sxs-lookup"><span data-stu-id="f0f85-105">This walkthrough is written entirely in [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)].</span></span>

> [!IMPORTANT]
> <span data-ttu-id="f0f85-106">Este passo a passo orienta você através das etapas para [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] criar o aplicativo digitando ou copiando e colando no Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="f0f85-106">This walkthrough guides you through the steps for creating the application by typing or copying and pasting [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] into Visual Studio.</span></span> <span data-ttu-id="f0f85-107">Se você preferir aprender a usar um designer para criar o mesmo aplicativo, consulte [Criar um botão usando o Microsoft Expression Blend](walkthrough-create-a-button-by-using-microsoft-expression-blend.md).</span><span class="sxs-lookup"><span data-stu-id="f0f85-107">If you would prefer to learn how to use a designer to create the same application, see [Create a Button by Using Microsoft Expression Blend](walkthrough-create-a-button-by-using-microsoft-expression-blend.md).</span></span>

<span data-ttu-id="f0f85-108">A figura a seguir mostra os botões concluídos.</span><span class="sxs-lookup"><span data-stu-id="f0f85-108">The following figure shows the finished buttons.</span></span>

<span data-ttu-id="f0f85-109">![Botões personalizados que foram criados usando XAML](./media/custom-button-animatedbutton-5.gif "custom_button_AnimatedButton_5")</span><span class="sxs-lookup"><span data-stu-id="f0f85-109">![Custom buttons that were created by using XAML](./media/custom-button-animatedbutton-5.gif "custom_button_AnimatedButton_5")</span></span>

## <a name="create-basic-buttons"></a><span data-ttu-id="f0f85-110">Criar botões básicos</span><span class="sxs-lookup"><span data-stu-id="f0f85-110">Create Basic Buttons</span></span>

<span data-ttu-id="f0f85-111">Vamos começar criando um novo projeto e adicionando alguns botões à janela.</span><span class="sxs-lookup"><span data-stu-id="f0f85-111">Let's start by creating a new project and adding a few buttons to the window.</span></span>

### <a name="to-create-a-new-wpf-project-and-add-buttons-to-the-window"></a><span data-ttu-id="f0f85-112">Para criar um novo projeto WPF e adicionar botões à janela</span><span class="sxs-lookup"><span data-stu-id="f0f85-112">To create a new WPF project and add buttons to the window</span></span>

1. <span data-ttu-id="f0f85-113">Inicie o Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="f0f85-113">Start Visual Studio.</span></span>

2. <span data-ttu-id="f0f85-114">**Criar um novo projeto WPF:** no menu **Arquivo**, aponte para **Novo** e, em seguida, clique em **Projeto**.</span><span class="sxs-lookup"><span data-stu-id="f0f85-114">**Create a new WPF project:** On the **File** menu, point to **New**, and then click **Project**.</span></span> <span data-ttu-id="f0f85-115">Encontre o modelo do **Aplicativo do Windows (WPF)** e nomeie o projeto como "AnimatedButton".</span><span class="sxs-lookup"><span data-stu-id="f0f85-115">Find the **Windows Application (WPF)** template and name the project "AnimatedButton".</span></span> <span data-ttu-id="f0f85-116">Isso criará o esqueleto para o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="f0f85-116">This will create the skeleton for the application.</span></span>

3. <span data-ttu-id="f0f85-117">**Adicionar botões padrão básicos:** todos os arquivos necessários para esse passo a passo são fornecidos pelo modelo.</span><span class="sxs-lookup"><span data-stu-id="f0f85-117">**Add basic default buttons:** All the files you need for this walkthrough are provided by the template.</span></span> <span data-ttu-id="f0f85-118">Abra o arquivo Window1.xaml, clicando duas vezes nele no Gerenciador de Soluções.</span><span class="sxs-lookup"><span data-stu-id="f0f85-118">Open the Window1.xaml file by double clicking it in Solution Explorer.</span></span> <span data-ttu-id="f0f85-119">Por padrão, há <xref:System.Windows.Controls.Grid> um elemento no Window1.xaml.</span><span class="sxs-lookup"><span data-stu-id="f0f85-119">By default, there is a <xref:System.Windows.Controls.Grid> element in Window1.xaml.</span></span> <span data-ttu-id="f0f85-120">Remova <xref:System.Windows.Controls.Grid> o elemento e adicione alguns botões à [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] página digitando ou copiando e colando o seguinte código destacado para Window1.xaml:</span><span class="sxs-lookup"><span data-stu-id="f0f85-120">Remove the <xref:System.Windows.Controls.Grid> element and add a few buttons to the [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] page by typing or copy and pasting the following highlighted code to Window1.xaml:</span></span>

    ```xaml
    <Window x:Class="AnimatedButton.Window1"
      xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
      xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
      Title="AnimatedButton" Height="300" Width="300"
      Background="Black">
      <!-- Buttons arranged vertically inside a StackPanel. -->
      <StackPanel HorizontalAlignment="Left">
          <Button>Button 1</Button>
          <Button>Button 2</Button>
          <Button>Button 3</Button>
      </StackPanel>
    </Window>
    ```

     <span data-ttu-id="f0f85-121">Pressione F5 para executar o aplicativo. Você deverá ver um conjunto de botões parecido com a figura a seguir.</span><span class="sxs-lookup"><span data-stu-id="f0f85-121">Press F5 to run the application; you should see a set of buttons that looks like the following figure.</span></span>

     <span data-ttu-id="f0f85-122">![Três botões básicos](./media/custom-button-animatedbutton-1.gif "custom_button_AnimatedButton_1")</span><span class="sxs-lookup"><span data-stu-id="f0f85-122">![Three basic buttons](./media/custom-button-animatedbutton-1.gif "custom_button_AnimatedButton_1")</span></span>

     <span data-ttu-id="f0f85-123">Agora que você criou os botões básicos, o trabalho no arquivo Window1.xaml está concluído.</span><span class="sxs-lookup"><span data-stu-id="f0f85-123">Now that you have created the basic buttons, you are finished working in the Window1.xaml file.</span></span> <span data-ttu-id="f0f85-124">O restante do passo a passo se concentrará no arquivo app.xaml, definindo estilos e um modelo para os botões.</span><span class="sxs-lookup"><span data-stu-id="f0f85-124">The rest of the walkthrough focuses on the app.xaml file, defining styles and a template for the buttons.</span></span>

## <a name="set-basic-properties"></a><span data-ttu-id="f0f85-125">Definir propriedades básicas</span><span class="sxs-lookup"><span data-stu-id="f0f85-125">Set Basic Properties</span></span>

<span data-ttu-id="f0f85-126">Em seguida, vamos definir algumas propriedades para controlar a aparência e o layout desses botões.</span><span class="sxs-lookup"><span data-stu-id="f0f85-126">Next, let's set some properties on these buttons to control the button appearance and layout.</span></span> <span data-ttu-id="f0f85-127">Em vez de definir propriedades em cada botão, você usará recursos para definir propriedades de botão para todo o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="f0f85-127">Rather than setting properties on the buttons individually, you will use resources to define button properties for the entire application.</span></span> <span data-ttu-id="f0f85-128">Os recursos de aplicação são conceitualmente semelhantes às Folhas de Estilo em cascata externas (CSS) para páginas da Web; no entanto, os recursos são muito mais poderosos do que o Cascading Style Sheets (CSS), como você verá no final deste passo a passo.</span><span class="sxs-lookup"><span data-stu-id="f0f85-128">Application resources are conceptually similar to external Cascading Style Sheets (CSS) for Web pages; however, resources are much more powerful than Cascading Style Sheets (CSS), as you will see by the end of this walkthrough.</span></span> <span data-ttu-id="f0f85-129">Para saber mais sobre recursos, consulte [Recursos XAML](../../../desktop-wpf/fundamentals/xaml-resources-define.md).</span><span class="sxs-lookup"><span data-stu-id="f0f85-129">To learn more about resources, see [XAML Resources](../../../desktop-wpf/fundamentals/xaml-resources-define.md).</span></span>

### <a name="to-use-styles-to-set-basic-properties-on-the-buttons"></a><span data-ttu-id="f0f85-130">Usar estilos para definir propriedades básicas nos botões</span><span class="sxs-lookup"><span data-stu-id="f0f85-130">To use styles to set basic properties on the buttons</span></span>

1. <span data-ttu-id="f0f85-131">**Definir um bloco Application.Resources:** abra o app.xaml e adicione a seguinte marcação realçada, se ainda não estiver lá:</span><span class="sxs-lookup"><span data-stu-id="f0f85-131">**Define an Application.Resources block:** Open app.xaml and add the following highlighted markup if it is not already there:</span></span>

    ```xaml
    <Application x:Class="AnimatedButton.App"
      xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
      xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
      StartupUri="Window1.xaml"
      >
      <Application.Resources>
        <!-- Resources for the entire application can be defined here. -->
      </Application.Resources>
    </Application>
    ```

     <span data-ttu-id="f0f85-132">O escopo do recurso é determinado pelo local em que você define o recurso.</span><span class="sxs-lookup"><span data-stu-id="f0f85-132">Resource scope is determined by where you define the resource.</span></span> <span data-ttu-id="f0f85-133">A definição de recursos em `Application.Resources` no arquivo app.xaml permite que o recurso seja usado de qualquer local no aplicativo.</span><span class="sxs-lookup"><span data-stu-id="f0f85-133">Defining resources in `Application.Resources` in the app.xaml file enables the resource to be used from anywhere in the application.</span></span> <span data-ttu-id="f0f85-134">Para saber mais sobre como definir o escopo de seus recursos, consulte [Recursos XAML](../../../desktop-wpf/fundamentals/xaml-resources-define.md).</span><span class="sxs-lookup"><span data-stu-id="f0f85-134">To learn more about defining the scope of your resources, see [XAML Resources](../../../desktop-wpf/fundamentals/xaml-resources-define.md).</span></span>

2. <span data-ttu-id="f0f85-135">**Criar um estilo e definir valores básicos da propriedade com ele:** adicione a seguinte marcação ao bloco `Application.Resources`.</span><span class="sxs-lookup"><span data-stu-id="f0f85-135">**Create a style and define basic property values with it:** Add the following markup to the `Application.Resources` block.</span></span> <span data-ttu-id="f0f85-136">Esta marcação <xref:System.Windows.Style> cria um que se aplica a todos <xref:System.Windows.FrameworkElement.Width%2A> os botões do aplicativo, <xref:System.Windows.FrameworkElement.Margin%2A> definindo os botões para 90 e para 10:</span><span class="sxs-lookup"><span data-stu-id="f0f85-136">This markup creates a <xref:System.Windows.Style> that applies to all buttons in the application, setting the <xref:System.Windows.FrameworkElement.Width%2A> of the buttons to 90 and the <xref:System.Windows.FrameworkElement.Margin%2A> to 10:</span></span>

    ```xaml
    <Application.Resources>
      <Style TargetType="Button">
        <Setter Property="Width" Value="90" />
        <Setter Property="Margin" Value="10" />
      </Style>
    </Application.Resources>
    ```

     <span data-ttu-id="f0f85-137">A <xref:System.Windows.Style.TargetType%2A> propriedade especifica que o estilo se <xref:System.Windows.Controls.Button>aplica a todos os objetos do tipo .</span><span class="sxs-lookup"><span data-stu-id="f0f85-137">The <xref:System.Windows.Style.TargetType%2A> property specifies that the style applies to all objects of type <xref:System.Windows.Controls.Button>.</span></span> <span data-ttu-id="f0f85-138">Cada <xref:System.Windows.Setter> um define um <xref:System.Windows.Style>valor de propriedade diferente para o .</span><span class="sxs-lookup"><span data-stu-id="f0f85-138">Each <xref:System.Windows.Setter> sets a different property value for the <xref:System.Windows.Style>.</span></span> <span data-ttu-id="f0f85-139">Portanto, neste ponto, cada botão no aplicativo tem uma largura de 90 e uma margem de 10.</span><span class="sxs-lookup"><span data-stu-id="f0f85-139">Therefore, at this point every button in the application has a width of 90 and a margin of 10.</span></span>  <span data-ttu-id="f0f85-140">Se você pressionar F5 para executar o aplicativo, você verá a seguinte janela.</span><span class="sxs-lookup"><span data-stu-id="f0f85-140">If you press F5 to run the application, you see the following window.</span></span>

     <span data-ttu-id="f0f85-141">![Botões com largura de 90 e uma margem de 10](./media/custom-button-animatedbutton-2.gif "custom_button_AnimatedButton_2")</span><span class="sxs-lookup"><span data-stu-id="f0f85-141">![Buttons with a width of 90 and a margin of 10](./media/custom-button-animatedbutton-2.gif "custom_button_AnimatedButton_2")</span></span>

     <span data-ttu-id="f0f85-142">Há muito mais que você pode fazer com estilos, incluindo uma variedade de maneiras de ajustar quais objetos são direcionados, especificando valores da propriedade complexos e até mesmo usar estilos como entrada para outros estilos.</span><span class="sxs-lookup"><span data-stu-id="f0f85-142">There is much more you can do with styles, including a variety of ways to fine-tune what objects are targeted, specifying complex property values, and even using styles as input for other styles.</span></span> <span data-ttu-id="f0f85-143">Para obter mais informações, consulte [Styling e Templating](../../../desktop-wpf/fundamentals/styles-templates-overview.md).</span><span class="sxs-lookup"><span data-stu-id="f0f85-143">For more information, see [Styling and Templating](../../../desktop-wpf/fundamentals/styles-templates-overview.md).</span></span>

3. <span data-ttu-id="f0f85-144">**Definir um valor da propriedade de estilo para um recurso:** os recursos proporcionam uma maneira simples de reutilizar objetos e valores comumente definidos.</span><span class="sxs-lookup"><span data-stu-id="f0f85-144">**Set a style property value to a resource:** Resources enable a simple way to reuse commonly defined objects and values.</span></span> <span data-ttu-id="f0f85-145">É especialmente útil definir valores complexos usando recursos para tornar seu código mais modular.</span><span class="sxs-lookup"><span data-stu-id="f0f85-145">It is especially useful to define complex values using resources to make your code more modular.</span></span> <span data-ttu-id="f0f85-146">Adicione a seguinte marcação realçada ao app.xaml.</span><span class="sxs-lookup"><span data-stu-id="f0f85-146">Add the following highlighted markup to app.xaml.</span></span>

    ```xaml
    <Application.Resources>
      <LinearGradientBrush x:Key="GrayBlueGradientBrush" StartPoint="0,0" EndPoint="1,1">
        <GradientStop Color="DarkGray" Offset="0" />
        <GradientStop Color="#CCCCFF" Offset="0.5" />
        <GradientStop Color="DarkGray" Offset="1" />
      </LinearGradientBrush>
      <Style TargetType="{x:Type Button}">
        <Setter Property="Background" Value="{StaticResource GrayBlueGradientBrush}" />
        <Setter Property="Width" Value="80" />
        <Setter Property="Margin" Value="10" />
      </Style>
    </Application.Resources>
    ```

     <span data-ttu-id="f0f85-147">Logo após o bloco `Application.Resources`, você criou um recurso chamado "GrayBlueGradientBrush".</span><span class="sxs-lookup"><span data-stu-id="f0f85-147">Directly under the `Application.Resources` block, you created a resource called "GrayBlueGradientBrush".</span></span> <span data-ttu-id="f0f85-148">Este recurso define um gradiente horizontal.</span><span class="sxs-lookup"><span data-stu-id="f0f85-148">This resource defines a horizontal gradient.</span></span> <span data-ttu-id="f0f85-149">Esse recurso pode ser usado como um valor de propriedade de qualquer <xref:System.Windows.Controls.Control.Background%2A> lugar do aplicativo, incluindo dentro do setter de estilo de botão para a propriedade.</span><span class="sxs-lookup"><span data-stu-id="f0f85-149">This resource can be used as a property value from anywhere in the application, including inside the button style setter for the <xref:System.Windows.Controls.Control.Background%2A> property.</span></span> <span data-ttu-id="f0f85-150">Agora, todos os botões <xref:System.Windows.Controls.Control.Background%2A> têm um valor de propriedade deste gradiente.</span><span class="sxs-lookup"><span data-stu-id="f0f85-150">Now, all the buttons have a <xref:System.Windows.Controls.Control.Background%2A> property value of this gradient.</span></span>

     <span data-ttu-id="f0f85-151">Pressione F5 para executar o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="f0f85-151">Press F5 to run the application.</span></span> <span data-ttu-id="f0f85-152">Ele deverá ter a seguinte aparência.</span><span class="sxs-lookup"><span data-stu-id="f0f85-152">It should look like the following.</span></span>

     <span data-ttu-id="f0f85-153">![Botões com fundo gradiente](./media/custom-button-animatedbutton-3.gif "custom_button_AnimatedButton_3")</span><span class="sxs-lookup"><span data-stu-id="f0f85-153">![Buttons with a gradient background](./media/custom-button-animatedbutton-3.gif "custom_button_AnimatedButton_3")</span></span>

## <a name="create-a-template-that-defines-the-look-of-the-button"></a><span data-ttu-id="f0f85-154">Criar um modelo que define a aparência do botão</span><span class="sxs-lookup"><span data-stu-id="f0f85-154">Create a Template That Defines the Look of the Button</span></span>

<span data-ttu-id="f0f85-155">Nesta seção, você cria um modelo que personaliza a aparência (apresentação) do botão.</span><span class="sxs-lookup"><span data-stu-id="f0f85-155">In this section, you create a template that customizes the appearance (presentation) of the button.</span></span> <span data-ttu-id="f0f85-156">A apresentação do botão é composta de vários objetos, incluindo retângulos e outros componentes, para dar uma aparência exclusiva ao botão.</span><span class="sxs-lookup"><span data-stu-id="f0f85-156">The button presentation is made up of several objects including rectangles and other components to give the button a unique look.</span></span>

<span data-ttu-id="f0f85-157">Até agora, o controle de como os botões se parecem no aplicativo esteve restrito à alteração das propriedades do botão.</span><span class="sxs-lookup"><span data-stu-id="f0f85-157">So far, the control of how buttons look in the application has been confined to changing properties of the button.</span></span> <span data-ttu-id="f0f85-158">E se você quiser fazer alterações mais radicais à aparência do botão?</span><span class="sxs-lookup"><span data-stu-id="f0f85-158">What if you want to make more radical changes to the button's appearance?</span></span> <span data-ttu-id="f0f85-159">Os modelos proporcionam um controle poderoso sobre a apresentação de um objeto.</span><span class="sxs-lookup"><span data-stu-id="f0f85-159">Templates enable powerful control over the presentation of an object.</span></span> <span data-ttu-id="f0f85-160">Como os modelos podem ser usados em estilos, você pode aplicar um modelo a todos os objetos aos quais o estilo se aplica (neste passo a passo, o botão).</span><span class="sxs-lookup"><span data-stu-id="f0f85-160">Because templates can be used within styles, you can apply a template to all objects that the style applies to (in this walkthrough, the button).</span></span>

### <a name="to-use-the-template-to-define-the-look-of-the-button"></a><span data-ttu-id="f0f85-161">Para usar o modelo para definir a aparência do botão</span><span class="sxs-lookup"><span data-stu-id="f0f85-161">To use the template to define the look of the button</span></span>

1. <span data-ttu-id="f0f85-162">**Configure o modelo:** Como os <xref:System.Windows.Controls.Button> controles <xref:System.Windows.Controls.Control.Template%2A> como ter um imóvel, você pode definir o valor da <xref:System.Windows.Style> propriedade <xref:System.Windows.Setter>do modelo, assim como os outros valores de propriedade que definimos em um uso de um .</span><span class="sxs-lookup"><span data-stu-id="f0f85-162">**Set up the template:** Because controls like <xref:System.Windows.Controls.Button> have a <xref:System.Windows.Controls.Control.Template%2A> property, you can define the template property value just like the other property values we have set in a <xref:System.Windows.Style> using a <xref:System.Windows.Setter>.</span></span> <span data-ttu-id="f0f85-163">Adicione a seguinte marcação realçada ao seu estilo de botão.</span><span class="sxs-lookup"><span data-stu-id="f0f85-163">Add the following highlighted markup to your button style.</span></span>

    ```xaml
    <Application.Resources>
      <LinearGradientBrush x:Key="GrayBlueGradientBrush"
        StartPoint="0,0" EndPoint="1,1">
        <GradientStop Color="DarkGray" Offset="0" />
        <GradientStop Color="#CCCCFF" Offset="0.5" />
        <GradientStop Color="DarkGray" Offset="1" />
      </LinearGradientBrush>
      <Style TargetType="{x:Type Button}">
        <Setter Property="Background" Value="{StaticResource GrayBlueGradientBrush}" />
        <Setter Property="Width" Value="80" />
        <Setter Property="Margin" Value="10" />
        <Setter Property="Template">
          <Setter.Value>
            <!-- The button template is defined here. -->
          </Setter.Value>
        </Setter>
      </Style>
    </Application.Resources>
    ```

2. <span data-ttu-id="f0f85-164">**Alterar apresentação do botão:** neste ponto, você precisa definir o modelo.</span><span class="sxs-lookup"><span data-stu-id="f0f85-164">**Alter button presentation:** At this point, you need to define the template.</span></span> <span data-ttu-id="f0f85-165">Adicione a seguinte marcação realçada.</span><span class="sxs-lookup"><span data-stu-id="f0f85-165">Add the following highlighted markup.</span></span> <span data-ttu-id="f0f85-166">Esta marcação especifica <xref:System.Windows.Shapes.Rectangle> dois elementos com bordas <xref:System.Windows.Controls.DockPanel>arredondadas, seguido sumido por um .</span><span class="sxs-lookup"><span data-stu-id="f0f85-166">This markup specifies two <xref:System.Windows.Shapes.Rectangle> elements with rounded edges, followed by a <xref:System.Windows.Controls.DockPanel>.</span></span> <span data-ttu-id="f0f85-167">O <xref:System.Windows.Controls.DockPanel> é usado <xref:System.Windows.Controls.ContentPresenter> para hospedar o botão.</span><span class="sxs-lookup"><span data-stu-id="f0f85-167">The <xref:System.Windows.Controls.DockPanel> is used to host the <xref:System.Windows.Controls.ContentPresenter> of the button.</span></span> <span data-ttu-id="f0f85-168">A <xref:System.Windows.Controls.ContentPresenter> exibe o conteúdo do botão.</span><span class="sxs-lookup"><span data-stu-id="f0f85-168">A <xref:System.Windows.Controls.ContentPresenter> displays the content of the button.</span></span> <span data-ttu-id="f0f85-169">Neste passo a passo, o conteúdo é texto ("Botão 1", "Botão 2" e "Botão 3").</span><span class="sxs-lookup"><span data-stu-id="f0f85-169">In this walkthrough, the content is text ("Button 1", "Button 2", "Button 3").</span></span> <span data-ttu-id="f0f85-170">Todos os componentes do modelo (os <xref:System.Windows.Controls.DockPanel>retângulos e <xref:System.Windows.Controls.Grid>os ) estão dispostos dentro de um .</span><span class="sxs-lookup"><span data-stu-id="f0f85-170">All of the template components (the rectangles and the <xref:System.Windows.Controls.DockPanel>) are laid out inside of a <xref:System.Windows.Controls.Grid>.</span></span>

    ```xaml
    <Setter.Value>
      <ControlTemplate TargetType="Button">
        <Grid Width="{TemplateBinding Width}" Height="{TemplateBinding Height}" ClipToBounds="True">
          <!-- Outer Rectangle with rounded corners. -->
          <Rectangle x:Name="outerRectangle" HorizontalAlignment="Stretch" VerticalAlignment="Stretch" Stroke="{TemplateBinding Background}" RadiusX="20" RadiusY="20" StrokeThickness="5" Fill="Transparent" />
          <!-- Inner Rectangle with rounded corners. -->
          <Rectangle x:Name="innerRectangle" HorizontalAlignment="Stretch" VerticalAlignment="Stretch" Stroke="Transparent" StrokeThickness="20" Fill="{TemplateBinding Background}" RadiusX="20" RadiusY="20" />
          <!-- Present Content (text) of the button. -->
          <DockPanel Name="myContentPresenterDockPanel">
            <ContentPresenter x:Name="myContentPresenter" Margin="20" Content="{TemplateBinding  Content}" TextBlock.Foreground="Black" />
          </DockPanel>
        </Grid>
      </ControlTemplate>
    </Setter.Value>
    ```

     <span data-ttu-id="f0f85-171">Pressione F5 para executar o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="f0f85-171">Press F5 to run the application.</span></span> <span data-ttu-id="f0f85-172">Ele deverá ter a seguinte aparência.</span><span class="sxs-lookup"><span data-stu-id="f0f85-172">It should look like the following.</span></span>

     ![Janela com 3 botões](./media/custom-button-animatedbutton-4.gif)

3. <span data-ttu-id="f0f85-174">**Adicionar um efeito de vidro ao modelo:** em seguida, você adicionará o vidro.</span><span class="sxs-lookup"><span data-stu-id="f0f85-174">**Add a glasseffect to the template:** Next you will add the glass.</span></span> <span data-ttu-id="f0f85-175">Primeiro, você cria alguns recursos que produzem um efeito de gradiente de vidro.</span><span class="sxs-lookup"><span data-stu-id="f0f85-175">First you create some resources that create a glass gradient effect.</span></span> <span data-ttu-id="f0f85-176">Adicione esses recursos de gradiente em qualquer local no bloco `Application.Resources`:</span><span class="sxs-lookup"><span data-stu-id="f0f85-176">Add these gradient resources anywhere within the `Application.Resources` block:</span></span>

    ```xaml
    <Application.Resources>
      <GradientStopCollection x:Key="MyGlassGradientStopsResource">
        <GradientStop Color="WhiteSmoke" Offset="0.2" />
        <GradientStop Color="Transparent" Offset="0.4" />
        <GradientStop Color="WhiteSmoke" Offset="0.5" />
        <GradientStop Color="Transparent" Offset="0.75" />
        <GradientStop Color="WhiteSmoke" Offset="0.9" />
        <GradientStop Color="Transparent" Offset="1" />
      </GradientStopCollection>
      <LinearGradientBrush x:Key="MyGlassBrushResource"
        StartPoint="0,0" EndPoint="1,1" Opacity="0.75"
        GradientStops="{StaticResource MyGlassGradientStopsResource}" />
    <!-- Styles and other resources below here. -->
    ```

     <span data-ttu-id="f0f85-177">Esses recursos são <xref:System.Windows.Shapes.Shape.Fill%2A> usados como para um retângulo que inserimos no <xref:System.Windows.Controls.Grid> modelo do botão.</span><span class="sxs-lookup"><span data-stu-id="f0f85-177">These resources are used as the <xref:System.Windows.Shapes.Shape.Fill%2A> for a rectangle that we insert into the <xref:System.Windows.Controls.Grid> of the button template.</span></span> <span data-ttu-id="f0f85-178">Adicione a seguinte marcação realçada ao modelo.</span><span class="sxs-lookup"><span data-stu-id="f0f85-178">Add the following highlighted markup to the template.</span></span>

    ```xaml
    <Setter.Value>
      <ControlTemplate TargetType="{x:Type Button}">
        <Grid Width="{TemplateBinding Width}" Height="{TemplateBinding Height}"
          ClipToBounds="True">

        <!-- Outer Rectangle with rounded corners. -->
        <Rectangle x:Name="outerRectangle" HorizontalAlignment="Stretch"
          VerticalAlignment="Stretch" Stroke="{TemplateBinding Background}"
          RadiusX="20" RadiusY="20" StrokeThickness="5" Fill="Transparent" />

        <!-- Inner Rectangle with rounded corners. -->
        <Rectangle x:Name="innerRectangle" HorizontalAlignment="Stretch"
          VerticalAlignment="Stretch" Stroke="Transparent" StrokeThickness="20"
          Fill="{TemplateBinding Background}" RadiusX="20" RadiusY="20" />

        <!-- Glass Rectangle -->
        <Rectangle x:Name="glassCube" HorizontalAlignment="Stretch"
          VerticalAlignment="Stretch"
          StrokeThickness="2" RadiusX="10" RadiusY="10" Opacity="0"
          Fill="{StaticResource MyGlassBrushResource}"
          RenderTransformOrigin="0.5,0.5">
          <Rectangle.Stroke>
            <LinearGradientBrush StartPoint="0.5,0" EndPoint="0.5,1">
              <LinearGradientBrush.GradientStops>
                <GradientStop Offset="0.0" Color="LightBlue" />
                <GradientStop Offset="1.0" Color="Gray" />
              </LinearGradientBrush.GradientStops>
            </LinearGradientBrush>
          </Rectangle.Stroke>
          <!-- These transforms have no effect as they are declared here.
          The reason the transforms are included is to be targets
          for animation (see later). -->
          <Rectangle.RenderTransform>
            <TransformGroup>
              <ScaleTransform />
              <RotateTransform />
            </TransformGroup>
          </Rectangle.RenderTransform>
          <!-- A BevelBitmapEffect is applied to give the button a "Beveled" look. -->
          <Rectangle.BitmapEffect>
            <BevelBitmapEffect />
          </Rectangle.BitmapEffect>
        </Rectangle>

        <!-- Present Text of the button. -->
        <DockPanel Name="myContentPresenterDockPanel">
          <ContentPresenter x:Name="myContentPresenter" Margin="20"
            Content="{TemplateBinding  Content}" TextBlock.Foreground="Black" />
        </DockPanel>
      </Grid>
    </ControlTemplate>
    </Setter.Value>
    ```

     <span data-ttu-id="f0f85-179">Observe que <xref:System.Windows.UIElement.Opacity%2A> o retângulo `x:Name` com a propriedade de "glassCube" é 0, então quando você executa a amostra, você não vê o retângulo de vidro sobreposto por cima.</span><span class="sxs-lookup"><span data-stu-id="f0f85-179">Notice that the <xref:System.Windows.UIElement.Opacity%2A> of the rectangle with the `x:Name` property of "glassCube" is 0, so when you run the sample, you do not see the glass rectangle overlaid on top.</span></span> <span data-ttu-id="f0f85-180">Isso é assim porque depois adicionaremos gatilhos ao modelo para quando o usuário interagir com o botão.</span><span class="sxs-lookup"><span data-stu-id="f0f85-180">This is because we will later add triggers to the template for when the user interacts with the button.</span></span> <span data-ttu-id="f0f85-181">No entanto, você pode ver como <xref:System.Windows.UIElement.Opacity%2A> o botão se parece agora, alterando o valor para 1 e executando o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="f0f85-181">However, you can see what the button looks like now by changing the <xref:System.Windows.UIElement.Opacity%2A> value to 1 and running the application.</span></span> <span data-ttu-id="f0f85-182">Consulte a figura a seguir.</span><span class="sxs-lookup"><span data-stu-id="f0f85-182">See the following figure.</span></span> <span data-ttu-id="f0f85-183">Antes de seguir para o <xref:System.Windows.UIElement.Opacity%2A> próximo passo, mude a parte de volta para 0.</span><span class="sxs-lookup"><span data-stu-id="f0f85-183">Before proceeding to the next step, change the <xref:System.Windows.UIElement.Opacity%2A> back to 0.</span></span>

     <span data-ttu-id="f0f85-184">![Botões personalizados que foram criados usando XAML](./media/custom-button-animatedbutton-5.gif "custom_button_AnimatedButton_5")</span><span class="sxs-lookup"><span data-stu-id="f0f85-184">![Custom buttons that were created by using XAML](./media/custom-button-animatedbutton-5.gif "custom_button_AnimatedButton_5")</span></span>

## <a name="create-button-interactivity"></a><span data-ttu-id="f0f85-185">Criar interatividade de botão</span><span class="sxs-lookup"><span data-stu-id="f0f85-185">Create Button Interactivity</span></span>

<span data-ttu-id="f0f85-186">Nesta seção, você criará gatilhos de propriedade e gatilhos de evento para alterar os valores da propriedade e executar animações em resposta às ações do usuário, como mover o ponteiro do mouse sobre o botão e clicar.</span><span class="sxs-lookup"><span data-stu-id="f0f85-186">In this section, you will create property triggers and event triggers to change property values and run animations in response to user actions such as moving the mouse pointer over the button and clicking.</span></span>

<span data-ttu-id="f0f85-187">Uma maneira fácil de adicionar interatividade (passar o mouse, soltar o mouse, clicar e assim por diante) é definir gatilhos dentro de seu modelo ou estilo.</span><span class="sxs-lookup"><span data-stu-id="f0f85-187">An easy way to add interactivity (mouse-over, mouse-leave, click, and so on) is to define triggers within your template or style.</span></span> <span data-ttu-id="f0f85-188">Para criar <xref:System.Windows.Trigger>um , você define uma "condição" de propriedade, tais como: O valor da propriedade do botão <xref:System.Windows.UIElement.IsMouseOver%2A> é igual a `true`.</span><span class="sxs-lookup"><span data-stu-id="f0f85-188">To create a <xref:System.Windows.Trigger>, you define a property "condition" such as: The button <xref:System.Windows.UIElement.IsMouseOver%2A> property value is equal to `true`.</span></span> <span data-ttu-id="f0f85-189">Em seguida, você define setters (ações) que ocorrem quando a condição do gatilho for verdadeira.</span><span class="sxs-lookup"><span data-stu-id="f0f85-189">You then define setters (actions) that take place when the trigger condition is true.</span></span>

### <a name="to-create-button-interactivity"></a><span data-ttu-id="f0f85-190">Para criar interatividade de botão</span><span class="sxs-lookup"><span data-stu-id="f0f85-190">To create button interactivity</span></span>

1. <span data-ttu-id="f0f85-191">**Adicionar modelos de gatilho:** adicione a marcação realçada ao seu modelo.</span><span class="sxs-lookup"><span data-stu-id="f0f85-191">**Add template triggers:** Add the highlighted markup to your template.</span></span>

    ```xaml
    <Setter.Value>
      <ControlTemplate TargetType="{x:Type Button}">
        <Grid Width="{TemplateBinding Width}"
          Height="{TemplateBinding Height}" ClipToBounds="True">

          <!-- Outer Rectangle with rounded corners. -->
          <Rectangle x:Name="outerRectangle" HorizontalAlignment="Stretch"
          VerticalAlignment="Stretch" Stroke="{TemplateBinding Background}"
          RadiusX="20" RadiusY="20" StrokeThickness="5" Fill="Transparent" />

          <!-- Inner Rectangle with rounded corners. -->
          <Rectangle x:Name="innerRectangle" HorizontalAlignment="Stretch"
            VerticalAlignment="Stretch" Stroke="Transparent"
            StrokeThickness="20"
            Fill="{TemplateBinding Background}" RadiusX="20" RadiusY="20"
          />

          <!-- Glass Rectangle -->
          <Rectangle x:Name="glassCube" HorizontalAlignment="Stretch"
            VerticalAlignment="Stretch"
            StrokeThickness="2" RadiusX="10" RadiusY="10" Opacity="0"
            Fill="{StaticResource MyGlassBrushResource}"
            RenderTransformOrigin="0.5,0.5">
            <Rectangle.Stroke>
              <LinearGradientBrush StartPoint="0.5,0" EndPoint="0.5,1">
                <LinearGradientBrush.GradientStops>
                  <GradientStop Offset="0.0" Color="LightBlue" />
                  <GradientStop Offset="1.0" Color="Gray" />
                </LinearGradientBrush.GradientStops>
              </LinearGradientBrush>
            </Rectangle.Stroke>

            <!-- These transforms have no effect as they
                 are declared here.
                 The reason the transforms are included is to be targets
                 for animation (see later). -->
            <Rectangle.RenderTransform>
              <TransformGroup>
                <ScaleTransform />
                <RotateTransform />
              </TransformGroup>
            </Rectangle.RenderTransform>

              <!-- A BevelBitmapEffect is applied to give the button a
                   "Beveled" look. -->
            <Rectangle.BitmapEffect>
              <BevelBitmapEffect />
            </Rectangle.BitmapEffect>
          </Rectangle>

          <!-- Present Text of the button. -->
          <DockPanel Name="myContentPresenterDockPanel">
            <ContentPresenter x:Name="myContentPresenter" Margin="20"
              Content="{TemplateBinding  Content}" TextBlock.Foreground="Black" />
          </DockPanel>
        </Grid>

        <ControlTemplate.Triggers>       <!-- Set action triggers for the buttons and define            what the button does in response to those triggers. -->     </ControlTemplate.Triggers>
      </ControlTemplate>
    </Setter.Value>
    ```

2. <span data-ttu-id="f0f85-192">**Adicionar gatilhos de propriedade:** adicionar a marcação realçada ao bloco `ControlTemplate.Triggers`:</span><span class="sxs-lookup"><span data-stu-id="f0f85-192">**Add property triggers:** Add the highlighted markup to the `ControlTemplate.Triggers` block:</span></span>

    ```xaml
    <ControlTemplate.Triggers>

      <!-- Set properties when mouse pointer is over the button. -->   <Trigger Property="IsMouseOver" Value="True">     <!-- Below are three property settings that occur when the           condition is met (user mouses over button).  -->     <!-- Change the color of the outer rectangle when user           mouses over it. -->     <Setter Property ="Rectangle.Stroke" TargetName="outerRectangle"       Value="{DynamicResource {x:Static SystemColors.HighlightBrushKey}}" />     <!-- Sets the glass opacity to 1, therefore, the           glass "appears" when user mouses over it. -->     <Setter Property="Rectangle.Opacity" Value="1" TargetName="glassCube" />     <!-- Makes the text slightly blurry as though you           were looking at it through blurry glass. -->     <Setter Property="ContentPresenter.BitmapEffect"        TargetName="myContentPresenter">       <Setter.Value>         <BlurBitmapEffect Radius="1" />       </Setter.Value>     </Setter>   </Trigger>

    <ControlTemplate.Triggers/>
    ```

     <span data-ttu-id="f0f85-193">Pressione F5 para executar o aplicativo e veja o efeito ao passar o ponteiro do mouse sobre os botões.</span><span class="sxs-lookup"><span data-stu-id="f0f85-193">Press F5 to run the application and see the effect as you run the mouse pointer over the buttons.</span></span>

3. <span data-ttu-id="f0f85-194">**Adicionar um gatilho de foco:** em seguida, adicionaremos alguns setters semelhantes para manipular o caso em que o botão tiver o foco (por exemplo, depois que o usuário clica nele).</span><span class="sxs-lookup"><span data-stu-id="f0f85-194">**Add a focus trigger:** Next, we'll add some similar setters to handle the case when the button has focus (for example, after the user clicks it).</span></span>

    ```xaml
    <ControlTemplate.Triggers>

      <!-- Set properties when mouse pointer is over the button. -->
      <Trigger Property="IsMouseOver" Value="True">

        <!-- Below are three property settings that occur when the
             condition is met (user mouses over button).  -->
        <!-- Change the color of the outer rectangle when user          mouses over it. -->
        <Setter Property ="Rectangle.Stroke" TargetName="outerRectangle"
          Value="{DynamicResource {x:Static SystemColors.HighlightBrushKey}}" />

        <!-- Sets the glass opacity to 1, therefore, the          glass "appears" when user mouses over it. -->
        <Setter Property="Rectangle.Opacity" Value="1"       TargetName="glassCube" />

        <!-- Makes the text slightly blurry as though you were          looking at it through blurry glass. -->
        <Setter Property="ContentPresenter.BitmapEffect"       TargetName="myContentPresenter">
          <Setter.Value>
            <BlurBitmapEffect Radius="1" />
          </Setter.Value>
        </Setter>
      </Trigger>
      <!-- Set properties when button has focus. -->   <Trigger Property="IsFocused" Value="true">     <Setter Property="Rectangle.Opacity" Value="1"       TargetName="glassCube" />     <Setter Property="Rectangle.Stroke" TargetName="outerRectangle"       Value="{DynamicResource {x:Static SystemColors.HighlightBrushKey}}" />     <Setter Property="Rectangle.Opacity" Value="1" TargetName="glassCube" />   </Trigger>

    </ControlTemplate.Triggers>
    ```

     <span data-ttu-id="f0f85-195">Pressione F5 para executar o aplicativo e clique em um dos botões.</span><span class="sxs-lookup"><span data-stu-id="f0f85-195">Press F5 to run the application and click on one of the buttons.</span></span> <span data-ttu-id="f0f85-196">Observe que o botão permanece realçado depois que você clica nele, porque ele ainda tem foco.</span><span class="sxs-lookup"><span data-stu-id="f0f85-196">Notice that the button stays highlighted after you click it because it still has focus.</span></span> <span data-ttu-id="f0f85-197">Se você clicar em outro botão, o novo botão obtém o foco e o outro perde o foco.</span><span class="sxs-lookup"><span data-stu-id="f0f85-197">If you click another button, the new button gains focus while the last one loses it.</span></span>

4. <span data-ttu-id="f0f85-198">**Adicione animações para** <xref:System.Windows.UIElement.MouseEnter> **e** <xref:System.Windows.UIElement.MouseLeave> **:** Em seguida adicionamos algumas animações aos gatilhos.  </span><span class="sxs-lookup"><span data-stu-id="f0f85-198">**Add animations for**  <xref:System.Windows.UIElement.MouseEnter> **and** <xref:System.Windows.UIElement.MouseLeave> **:** Next we add some animations to the triggers.</span></span> <span data-ttu-id="f0f85-199">Adicione a seguinte marcação em qualquer local dentro do bloco `ControlTemplate.Triggers`.</span><span class="sxs-lookup"><span data-stu-id="f0f85-199">Add the following markup anywhere inside of the `ControlTemplate.Triggers` block.</span></span>

    ```xaml
    <!-- Animations that start when mouse enters and leaves button. -->
    <EventTrigger RoutedEvent="Mouse.MouseEnter">
      <EventTrigger.Actions>
        <BeginStoryboard Name="mouseEnterBeginStoryboard">
          <Storyboard>
          <!-- This animation makes the glass rectangle shrink in the X direction. -->
            <DoubleAnimation Storyboard.TargetName="glassCube"
              Storyboard.TargetProperty=
              "(Rectangle.RenderTransform).(TransformGroup.Children)[0].(ScaleTransform.ScaleX)"
              By="-0.1" Duration="0:0:0.5" />
            <!-- This animation makes the glass rectangle shrink in the Y direction. -->
            <DoubleAnimation
            Storyboard.TargetName="glassCube"
              Storyboard.TargetProperty=
              "(Rectangle.RenderTransform).(TransformGroup.Children)[0].(ScaleTransform.ScaleY)"
              By="-0.1" Duration="0:0:0.5" />
          </Storyboard>
        </BeginStoryboard>
      </EventTrigger.Actions>
    </EventTrigger>
    <EventTrigger RoutedEvent="Mouse.MouseLeave">
      <EventTrigger.Actions>
        <!-- Stopping the storyboard sets all animated properties back to default. -->
        <StopStoryboard BeginStoryboardName="mouseEnterBeginStoryboard" />
      </EventTrigger.Actions>
    </EventTrigger>
    ```

     <span data-ttu-id="f0f85-200">O retângulo de vidro é reduzido quando o ponteiro do mouse passa sobre o botão e retorna ao tamanho normal quando o ponteiro sai.</span><span class="sxs-lookup"><span data-stu-id="f0f85-200">The glass rectangle shrinks when the mouse pointer moves over the button and returns back to normal size when the pointer leaves.</span></span>

     <span data-ttu-id="f0f85-201">Existem duas animações que são acionadas quando<xref:System.Windows.UIElement.MouseEnter> o ponteiro passa por cima do botão (o evento é levantado).</span><span class="sxs-lookup"><span data-stu-id="f0f85-201">There are two animations that are triggered when the pointer goes over the button (<xref:System.Windows.UIElement.MouseEnter> event is raised).</span></span> <span data-ttu-id="f0f85-202">Essas animações reduzem o retângulo de vidro ao longo dos eixos X e Y.</span><span class="sxs-lookup"><span data-stu-id="f0f85-202">These animations shrink the glass rectangle along the X and Y axis.</span></span> <span data-ttu-id="f0f85-203">Observe as propriedades <xref:System.Windows.Media.Animation.DoubleAnimation> nos <xref:System.Windows.Media.Animation.Timeline.Duration%2A> <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A>elementos — e .</span><span class="sxs-lookup"><span data-stu-id="f0f85-203">Notice the properties on the <xref:System.Windows.Media.Animation.DoubleAnimation> elements — <xref:System.Windows.Media.Animation.Timeline.Duration%2A> and <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A>.</span></span> <span data-ttu-id="f0f85-204">O <xref:System.Windows.Media.Animation.Timeline.Duration%2A> especifica que a animação ocorre mais <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A> de meio segundo, e especifica que o vidro encolhe 10%.</span><span class="sxs-lookup"><span data-stu-id="f0f85-204">The <xref:System.Windows.Media.Animation.Timeline.Duration%2A> specifies that the animation occurs over half a second, and <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A> specifies that the glass shrinks by 10%.</span></span>

     <span data-ttu-id="f0f85-205">O segundo gatilho<xref:System.Windows.UIElement.MouseLeave>de evento ( ) simplesmente pára o primeiro.</span><span class="sxs-lookup"><span data-stu-id="f0f85-205">The second event trigger (<xref:System.Windows.UIElement.MouseLeave>) simply stops the first one.</span></span> <span data-ttu-id="f0f85-206">Quando você <xref:System.Windows.Media.Animation.Storyboard>para um , todas as propriedades animadas retornam aos seus valores padrão.</span><span class="sxs-lookup"><span data-stu-id="f0f85-206">When you stop a <xref:System.Windows.Media.Animation.Storyboard>, all the animated properties return to their default values.</span></span> <span data-ttu-id="f0f85-207">Portanto, quando o usuário move o ponteiro para fora do botão, o botão volta à forma que estava antes de o ponteiro do mouse ser passado sobre o botão.</span><span class="sxs-lookup"><span data-stu-id="f0f85-207">Therefore, when the user moves the pointer off the button, the button goes back to the way it was before the mouse pointer moved over the button.</span></span> <span data-ttu-id="f0f85-208">Para obter mais informações sobre animações, consulte [Visão geral de animação](../graphics-multimedia/animation-overview.md).</span><span class="sxs-lookup"><span data-stu-id="f0f85-208">For more information about animations, see [Animation Overview](../graphics-multimedia/animation-overview.md).</span></span>

5. <span data-ttu-id="f0f85-209">**Adicionar uma animação para quando o botão é clicado:** a etapa final é adicionar um gatilho para quando o usuário clica no botão.</span><span class="sxs-lookup"><span data-stu-id="f0f85-209">**Add an animation for when the button is clicked:** The final step is to add a trigger for when the user clicks the button.</span></span> <span data-ttu-id="f0f85-210">Adicione a seguinte marcação em qualquer local dentro do bloco `ControlTemplate.Triggers`:</span><span class="sxs-lookup"><span data-stu-id="f0f85-210">Add the following markup anywhere inside of the `ControlTemplate.Triggers` block:</span></span>

    ```xaml
    <!-- Animation fires when button is clicked, causing glass to spin.  -->
    <EventTrigger RoutedEvent="Button.Click">
      <EventTrigger.Actions>
        <BeginStoryboard>
          <Storyboard>
            <DoubleAnimation Storyboard.TargetName="glassCube"
              Storyboard.TargetProperty=
              "(Rectangle.RenderTransform).(TransformGroup.Children)[1].(RotateTransform.Angle)"
              By="360" Duration="0:0:0.5" />
          </Storyboard>
        </BeginStoryboard>
      </EventTrigger.Actions>
    </EventTrigger>
    ```

     <span data-ttu-id="f0f85-211">Pressione F5 para executar o aplicativo e clique em um dos botões.</span><span class="sxs-lookup"><span data-stu-id="f0f85-211">Press F5 to run the application, and click one of the buttons.</span></span> <span data-ttu-id="f0f85-212">Quando você clica em um botão, o retângulo de vidro faz um giro.</span><span class="sxs-lookup"><span data-stu-id="f0f85-212">When you click a button, the glass rectangle spins around.</span></span>

## <a name="summary"></a><span data-ttu-id="f0f85-213">Resumo</span><span class="sxs-lookup"><span data-stu-id="f0f85-213">Summary</span></span>
 <span data-ttu-id="f0f85-214">Neste passo a passo, você realizou os seguintes exercícios:</span><span class="sxs-lookup"><span data-stu-id="f0f85-214">In this walkthrough, you performed the following exercises:</span></span>

- <span data-ttu-id="f0f85-215">Direcionado a <xref:System.Windows.Style> um tipo<xref:System.Windows.Controls.Button>de objeto ().</span><span class="sxs-lookup"><span data-stu-id="f0f85-215">Targeted a <xref:System.Windows.Style> to an object type (<xref:System.Windows.Controls.Button>).</span></span>

- <span data-ttu-id="f0f85-216">Propriedades básicas controladas dos botões em <xref:System.Windows.Style>toda a aplicação usando o .</span><span class="sxs-lookup"><span data-stu-id="f0f85-216">Controlled basic properties of the buttons in the entire application using the <xref:System.Windows.Style>.</span></span>

- <span data-ttu-id="f0f85-217">Criou recursos como gradientes para usar para <xref:System.Windows.Style> valores de propriedade dos setters.</span><span class="sxs-lookup"><span data-stu-id="f0f85-217">Created resources like gradients to use for property values of the <xref:System.Windows.Style> setters.</span></span>

- <span data-ttu-id="f0f85-218">Personalizou a aparência dos botões em todo o aplicativo, aplicando um modelo aos botões.</span><span class="sxs-lookup"><span data-stu-id="f0f85-218">Customized the look of buttons in the entire application by applying a template to the buttons.</span></span>

- <span data-ttu-id="f0f85-219">Comportamento personalizado para os botões em resposta às <xref:System.Windows.UIElement.MouseEnter> <xref:System.Windows.UIElement.MouseLeave>ações <xref:System.Windows.Controls.Primitives.ButtonBase.Click>do usuário (como , e ) que incluíam efeitos de animação.</span><span class="sxs-lookup"><span data-stu-id="f0f85-219">Customized behavior for the buttons in response to user actions (such as <xref:System.Windows.UIElement.MouseEnter>, <xref:System.Windows.UIElement.MouseLeave>, and <xref:System.Windows.Controls.Primitives.ButtonBase.Click>) that included animation effects.</span></span>

## <a name="see-also"></a><span data-ttu-id="f0f85-220">Confira também</span><span class="sxs-lookup"><span data-stu-id="f0f85-220">See also</span></span>

- [<span data-ttu-id="f0f85-221">Criar um botão usando o Microsoft Expression Blend</span><span class="sxs-lookup"><span data-stu-id="f0f85-221">Create a Button by Using Microsoft Expression Blend</span></span>](walkthrough-create-a-button-by-using-microsoft-expression-blend.md)
- [<span data-ttu-id="f0f85-222">Estilo e modelagem</span><span class="sxs-lookup"><span data-stu-id="f0f85-222">Styling and Templating</span></span>](../../../desktop-wpf/fundamentals/styles-templates-overview.md)
- [<span data-ttu-id="f0f85-223">Visão geral da animação</span><span class="sxs-lookup"><span data-stu-id="f0f85-223">Animation Overview</span></span>](../graphics-multimedia/animation-overview.md)
- [<span data-ttu-id="f0f85-224">Visão geral da pintura com cores sólidas e gradientes</span><span class="sxs-lookup"><span data-stu-id="f0f85-224">Painting with Solid Colors and Gradients Overview</span></span>](../graphics-multimedia/painting-with-solid-colors-and-gradients-overview.md)
- [<span data-ttu-id="f0f85-225">Visão geral dos efeitos de bitmap</span><span class="sxs-lookup"><span data-stu-id="f0f85-225">Bitmap Effects Overview</span></span>](../graphics-multimedia/bitmap-effects-overview.md)
