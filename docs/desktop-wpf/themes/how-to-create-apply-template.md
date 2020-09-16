---
title: Criar um modelo no WPF-.NET desktop
description: Saiba como criar e referenciar um modelo de controle no Windows Presentation Foundation e no .NET Core.
author: adegeo
ms.author: adegeo
ms.date: 11/15/2019
no-loc:
- <Window>
- <ControlTemplate>
- <Ellipse>
- <ContentPresenter>
- <Trigger>
- <Setter>
- <PropertyTrigger>
- <Grid>
- <VisualStateManager.VisualStateGroups>
- <VisualStateGroup>
- <VisualState>
- <Storyboard>
- SizeToContent
- MinWidth
- TargetType
- Title
helpviewer_keywords:
- control contract [WPF]
- controls [WPF], visual structure changes
- ControlTemplate [WPF], customizing for existing controls
- skinning controls [WPF]
- controls [WPF], appearance specified by state
- templates [WPF], custom for existing controls
ms.openlocfilehash: 8be38a2b4f046a43ab187ea3517335437ec49b08
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90551888"
---
# <a name="create-a-template-for-a-control"></a><span data-ttu-id="a6b64-103">Criar um modelo para um controle</span><span class="sxs-lookup"><span data-stu-id="a6b64-103">Create a template for a control</span></span>

<span data-ttu-id="a6b64-104">Com o Windows Presentation Foundation (WPF), você pode personalizar uma estrutura visual do controle existente e um comportamento com seu próprio modelo reutilizável.</span><span class="sxs-lookup"><span data-stu-id="a6b64-104">With Windows Presentation Foundation (WPF), you can customize an existing control's visual structure and behavior with your own reusable template.</span></span> <span data-ttu-id="a6b64-105">Os modelos podem ser aplicados globalmente ao seu aplicativo, janelas e páginas ou diretamente aos controles.</span><span class="sxs-lookup"><span data-stu-id="a6b64-105">Templates can be applied globally to your application, windows and pages, or directly to controls.</span></span> <span data-ttu-id="a6b64-106">A maioria dos cenários que exigem a criação de um novo controle pode ser abordada em vez de criar um novo modelo para um controle existente.</span><span class="sxs-lookup"><span data-stu-id="a6b64-106">Most scenarios that require you to create a new control can be covered by instead creating a new template for an existing control.</span></span>

[!INCLUDE [desktop guide under construction](../../../includes/desktop-guide-preview-note.md)]

<span data-ttu-id="a6b64-107">Neste artigo, você vai explorar a criação de uma nova <xref:System.Windows.Controls.ControlTemplate> para o <xref:System.Windows.Controls.Button> controle.</span><span class="sxs-lookup"><span data-stu-id="a6b64-107">In this article, you'll explore creating a new <xref:System.Windows.Controls.ControlTemplate> for the <xref:System.Windows.Controls.Button> control.</span></span>

## <a name="when-to-create-a-controltemplate"></a><span data-ttu-id="a6b64-108">Quando criar um ControlTemplate</span><span class="sxs-lookup"><span data-stu-id="a6b64-108">When to create a ControlTemplate</span></span>

<span data-ttu-id="a6b64-109">Os controles têm muitas propriedades, como <xref:System.Windows.Controls.Border.Background%2A> , <xref:System.Windows.Controls.Control.Foreground%2A> e <xref:System.Windows.Controls.Control.FontFamily%2A> .</span><span class="sxs-lookup"><span data-stu-id="a6b64-109">Controls have many properties, such as <xref:System.Windows.Controls.Border.Background%2A>, <xref:System.Windows.Controls.Control.Foreground%2A>, and <xref:System.Windows.Controls.Control.FontFamily%2A>.</span></span> <span data-ttu-id="a6b64-110">Essas propriedades controlam diferentes aspectos da aparência do controle, mas as alterações que você pode fazer definindo essas propriedades são limitadas.</span><span class="sxs-lookup"><span data-stu-id="a6b64-110">These properties control different aspects of the control's appearance, but the changes that you can make by setting these properties are limited.</span></span> <span data-ttu-id="a6b64-111">Por exemplo, você pode definir a <xref:System.Windows.Controls.Control.Foreground%2A> propriedade como azul e <xref:System.Windows.Controls.Control.FontStyle%2A> itálico em um <xref:System.Windows.Controls.CheckBox> .</span><span class="sxs-lookup"><span data-stu-id="a6b64-111">For example, you can set the <xref:System.Windows.Controls.Control.Foreground%2A> property to blue and <xref:System.Windows.Controls.Control.FontStyle%2A> to italic on a <xref:System.Windows.Controls.CheckBox>.</span></span> <span data-ttu-id="a6b64-112">Quando você quiser personalizar a aparência do controle além do que definir as outras propriedades no controle pode fazer, crie um <xref:System.Windows.Controls.ControlTemplate> .</span><span class="sxs-lookup"><span data-stu-id="a6b64-112">When you want to customize the control's appearance beyond what setting the other properties on the control can do, you create a <xref:System.Windows.Controls.ControlTemplate>.</span></span>

<span data-ttu-id="a6b64-113">Na maioria das interfaces de usuário, um botão tem a mesma aparência geral: um retângulo com algum texto.</span><span class="sxs-lookup"><span data-stu-id="a6b64-113">In most user interfaces, a button has the same general appearance: a rectangle with some text.</span></span> <span data-ttu-id="a6b64-114">Se você quisesse criar um botão arredondado, poderia criar um novo controle herdado do botão ou recriar a funcionalidade do botão.</span><span class="sxs-lookup"><span data-stu-id="a6b64-114">If you wanted to create a rounded button, you could create a new control that inherits from the button or recreates the functionality of the button.</span></span> <span data-ttu-id="a6b64-115">Além disso, o novo controle de usuário forneceria o Visual circular.</span><span class="sxs-lookup"><span data-stu-id="a6b64-115">In addition, the new user control would provide the circular visual.</span></span>

<span data-ttu-id="a6b64-116">Você pode evitar a criação de novos controles Personalizando o layout visual de um controle existente.</span><span class="sxs-lookup"><span data-stu-id="a6b64-116">You can avoid creating new controls by customizing the visual layout of an existing control.</span></span> <span data-ttu-id="a6b64-117">Com um botão arredondado, você cria um <xref:System.Windows.Controls.ControlTemplate> com o layout visual desejado.</span><span class="sxs-lookup"><span data-stu-id="a6b64-117">With a rounded button, you create a <xref:System.Windows.Controls.ControlTemplate> with the desired visual layout.</span></span>

<span data-ttu-id="a6b64-118">Por outro lado, se você precisar de um controle com novas funcionalidades, propriedades diferentes e novas configurações, você criará um novo <xref:System.Windows.Controls.UserControl> .</span><span class="sxs-lookup"><span data-stu-id="a6b64-118">On the other hand, if you need a control with new functionality, different properties, and new settings, you would create a new <xref:System.Windows.Controls.UserControl>.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="a6b64-119">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="a6b64-119">Prerequisites</span></span>

<span data-ttu-id="a6b64-120">Crie um novo aplicativo WPF e, em *MainWindow. XAML* (ou outra janela de sua escolha) defina as seguintes propriedades no elemento \*\* \: :: no-Loc ( <Window> ):::\*\* element:</span><span class="sxs-lookup"><span data-stu-id="a6b64-120">Create a new WPF application and in *MainWindow.xaml* (or another window of your choice) set the following properties on the **\<Window>** element:</span></span>

|     |     |
| --- | --- |
| **Title**         | `Template Intro Sample` |
| **SizeToContent** | `WidthAndHeight` |
| **MinWidth**      | `250` |

<span data-ttu-id="a6b64-121">Defina o conteúdo do elemento \*\* \: :: no-Loc ( <Window> ):::\*\* para o seguinte XAML:</span><span class="sxs-lookup"><span data-stu-id="a6b64-121">Set the content of the **\<Window>** element to the following XAML:</span></span>

[!code-xaml[Initial](~/samples/snippets/desktop-guide/wpf/styles-templates-create-apply-template/csharp/Window1.xaml#Initial)]

<span data-ttu-id="a6b64-122">No final, o arquivo *MainWindow. XAML* deve ser semelhante ao seguinte:</span><span class="sxs-lookup"><span data-stu-id="a6b64-122">In the end, the *MainWindow.xaml* file should look similar to the following:</span></span>

[!code-xaml[InitialWhole](~/samples/snippets/desktop-guide/wpf/styles-templates-create-apply-template/csharp/Window1.xaml#InitialWhole)]

<span data-ttu-id="a6b64-123">Se você executar o aplicativo, ele será semelhante ao seguinte:</span><span class="sxs-lookup"><span data-stu-id="a6b64-123">If you run the application, it looks like the following:</span></span>

![Janela do WPF com dois botões sem estilo](media/create-apply-template/unstyled-button.png)

## <a name="create-a-controltemplate"></a><span data-ttu-id="a6b64-125">Criar um ControlTemplate</span><span class="sxs-lookup"><span data-stu-id="a6b64-125">Create a ControlTemplate</span></span>

<span data-ttu-id="a6b64-126">A maneira mais comum de declarar um <xref:System.Windows.Controls.ControlTemplate> é como um recurso na `Resources` seção em um arquivo XAML.</span><span class="sxs-lookup"><span data-stu-id="a6b64-126">The most common way to declare a <xref:System.Windows.Controls.ControlTemplate> is as a resource in the `Resources` section in a XAML file.</span></span> <span data-ttu-id="a6b64-127">Como os modelos são recursos, eles obedecem às mesmas regras de escopo que se aplicam a todos os recursos.</span><span class="sxs-lookup"><span data-stu-id="a6b64-127">Because templates are resources, they obey the same scoping rules that apply to all resources.</span></span> <span data-ttu-id="a6b64-128">Em suma, o local em que você declara um modelo afeta o local em que o modelo pode ser aplicado.</span><span class="sxs-lookup"><span data-stu-id="a6b64-128">Put simply, where you declare a template affects where the template can be applied.</span></span> <span data-ttu-id="a6b64-129">Por exemplo, se você declarar o modelo no elemento raiz do arquivo XAML de definição de aplicativo, o modelo poderá ser usado em qualquer lugar em seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="a6b64-129">For example, if you declare the template in the root element of your application definition XAML file, the template can be used anywhere in your application.</span></span> <span data-ttu-id="a6b64-130">Se você definir o modelo em uma janela, somente os controles nessa janela poderão usar o modelo.</span><span class="sxs-lookup"><span data-stu-id="a6b64-130">If you define the template in a window, only the controls in that window can use the template.</span></span>

<span data-ttu-id="a6b64-131">Para começar, adicione um `Window.Resources` elemento ao seu arquivo *MainWindow. XAML* :</span><span class="sxs-lookup"><span data-stu-id="a6b64-131">To start with, add a `Window.Resources` element to your *MainWindow.xaml* file:</span></span>

[!code-xaml[WindowResStart](~/samples/snippets/desktop-guide/wpf/styles-templates-create-apply-template/csharp/Window2.xaml#WindowResStart)]

<span data-ttu-id="a6b64-132">Crie um novo \*\* \: :: no-Loc ( <ControlTemplate> ):::\*\* com as seguintes propriedades definidas:</span><span class="sxs-lookup"><span data-stu-id="a6b64-132">Create a new **\<ControlTemplate>** with the following properties set:</span></span>

|     |     |
| --- | --- |
| <span data-ttu-id="a6b64-133">**x:Key**</span><span class="sxs-lookup"><span data-stu-id="a6b64-133">**x:Key**</span></span>         | `roundbutton` |
| **TargetType**    | `Button` |

<span data-ttu-id="a6b64-134">Este modelo de controle será simples:</span><span class="sxs-lookup"><span data-stu-id="a6b64-134">This control template will be simple:</span></span>

- <span data-ttu-id="a6b64-135">um elemento raiz para o controle, um <xref:System.Windows.Controls.Grid></span><span class="sxs-lookup"><span data-stu-id="a6b64-135">a root element for the control, a <xref:System.Windows.Controls.Grid></span></span>
- <span data-ttu-id="a6b64-136">um <xref:System.Windows.Shapes.Ellipse> para desenhar a aparência arredondada do botão</span><span class="sxs-lookup"><span data-stu-id="a6b64-136">an <xref:System.Windows.Shapes.Ellipse> to draw the rounded appearance of the button</span></span>
- <span data-ttu-id="a6b64-137">um <xref:System.Windows.Controls.ContentPresenter> para exibir o conteúdo do botão especificado pelo usuário</span><span class="sxs-lookup"><span data-stu-id="a6b64-137">a <xref:System.Windows.Controls.ContentPresenter> to display the user-specified button content</span></span>

[!code-xaml[ControlTemplate](~/samples/snippets/desktop-guide/wpf/styles-templates-create-apply-template/csharp/Window3.xaml#ControlTemplate)]

### <a name="templatebinding"></a><span data-ttu-id="a6b64-138">TemplateBinding</span><span class="sxs-lookup"><span data-stu-id="a6b64-138">TemplateBinding</span></span>

<span data-ttu-id="a6b64-139">Quando você cria um novo <xref:System.Windows.Controls.ControlTemplate> , ainda convém usar as propriedades públicas para alterar a aparência do controle.</span><span class="sxs-lookup"><span data-stu-id="a6b64-139">When you create a new <xref:System.Windows.Controls.ControlTemplate>, you still might want to use the public properties to change the control's appearance.</span></span> <span data-ttu-id="a6b64-140">A extensão de marcação [TemplateBinding](/dotnet/desktop/wpf/advanced/templatebinding-markup-extension) associa uma propriedade de um elemento que está no <xref:System.Windows.Controls.ControlTemplate> a uma propriedade pública que é definida pelo controle.</span><span class="sxs-lookup"><span data-stu-id="a6b64-140">The [TemplateBinding](/dotnet/desktop/wpf/advanced/templatebinding-markup-extension) markup extension binds a property of an element that is in the <xref:System.Windows.Controls.ControlTemplate> to a public property that is defined by the control.</span></span> <span data-ttu-id="a6b64-141">Quando você usa um [TemplateBinding](/dotnet/desktop/wpf/advanced/templatebinding-markup-extension), você habilita as propriedades no controle para atuar como parâmetros para o modelo.</span><span class="sxs-lookup"><span data-stu-id="a6b64-141">When you use a [TemplateBinding](/dotnet/desktop/wpf/advanced/templatebinding-markup-extension), you enable properties on the control to act as parameters to the template.</span></span> <span data-ttu-id="a6b64-142">Ou seja, quando uma propriedade em um controle é definida, esse valor é passado para o elemento que contém a [TemplateBinding](/dotnet/desktop/wpf/advanced/templatebinding-markup-extension).</span><span class="sxs-lookup"><span data-stu-id="a6b64-142">That is, when a property on a control is set, that value is passed on to the element that has the [TemplateBinding](/dotnet/desktop/wpf/advanced/templatebinding-markup-extension) on it.</span></span>

### <a name="ellipse"></a><span data-ttu-id="a6b64-143">Elipse</span><span class="sxs-lookup"><span data-stu-id="a6b64-143">Ellipse</span></span>

<span data-ttu-id="a6b64-144">Observe que as **:::no-loc text="Fill":::** **:::no-loc text="Stroke":::** Propriedades e do elemento \*\* \: :: no-Loc ( <Ellipse> ):::\*\* estão associadas às propriedades e do controle <xref:System.Windows.Controls.Control.Foreground> <xref:System.Windows.Controls.Control.Background> .</span><span class="sxs-lookup"><span data-stu-id="a6b64-144">Notice that the **:::no-loc text="Fill":::** and **:::no-loc text="Stroke":::** properties of the **\<Ellipse>** element are bound to the control's <xref:System.Windows.Controls.Control.Foreground> and <xref:System.Windows.Controls.Control.Background> properties.</span></span>

### <a name="contentpresenter"></a><span data-ttu-id="a6b64-145">ContentPresenter</span><span class="sxs-lookup"><span data-stu-id="a6b64-145">ContentPresenter</span></span>

<span data-ttu-id="a6b64-146">Um elemento [ \: :: no-Loc ( <ContentPresenter> ):::](xref:System.Windows.Controls.ContentPresenter) também é adicionado ao modelo.</span><span class="sxs-lookup"><span data-stu-id="a6b64-146">A [\<ContentPresenter>](xref:System.Windows.Controls.ContentPresenter) element is also added to the template.</span></span> <span data-ttu-id="a6b64-147">Como esse modelo foi projetado para um botão, leve em consideração que o botão é herdado de <xref:System.Windows.Controls.ContentControl> .</span><span class="sxs-lookup"><span data-stu-id="a6b64-147">Because this template is designed for a button, take into consideration that the button inherits from <xref:System.Windows.Controls.ContentControl>.</span></span> <span data-ttu-id="a6b64-148">O botão apresenta o conteúdo do elemento.</span><span class="sxs-lookup"><span data-stu-id="a6b64-148">The button presents the content of the element.</span></span> <span data-ttu-id="a6b64-149">Você pode definir qualquer coisa dentro do botão, como texto sem formatação ou até mesmo outro controle.</span><span class="sxs-lookup"><span data-stu-id="a6b64-149">You can set anything inside of the button, such as plain text or even another control.</span></span> <span data-ttu-id="a6b64-150">Os dois itens a seguir são botões válidos:</span><span class="sxs-lookup"><span data-stu-id="a6b64-150">Both of the following are valid buttons:</span></span>

```xaml
<Button>My Text</Button>

<!-- and -->

<Button>
    <CheckBox>Checkbox in a button</CheckBox>
</Button>
```

<span data-ttu-id="a6b64-151">Nos dois exemplos anteriores, o texto e a caixa de seleção são definidos como a propriedade [Button. Content](xref:System.Windows.Controls.ContentControl.Content) .</span><span class="sxs-lookup"><span data-stu-id="a6b64-151">In both of the previous examples, the text and the checkbox are set as the [Button.Content](xref:System.Windows.Controls.ContentControl.Content) property.</span></span> <span data-ttu-id="a6b64-152">O que for definido como o conteúdo pode ser apresentado por meio de um \*\* \: :: no-Loc ( <ContentPresenter> )::\*\*:, que é o que o modelo faz.</span><span class="sxs-lookup"><span data-stu-id="a6b64-152">Whatever is set as the content can be presented through a **\<ContentPresenter>**, which is what the template does.</span></span>

<span data-ttu-id="a6b64-153">Se o <xref:System.Windows.Controls.ControlTemplate> for aplicado a um <xref:System.Windows.Controls.ContentControl> tipo, como um `Button` , um <xref:System.Windows.Controls.ContentPresenter> será procurado na árvore de elementos.</span><span class="sxs-lookup"><span data-stu-id="a6b64-153">If the <xref:System.Windows.Controls.ControlTemplate> is applied to a <xref:System.Windows.Controls.ContentControl> type, such as a `Button`, a <xref:System.Windows.Controls.ContentPresenter> is searched for in the element tree.</span></span> <span data-ttu-id="a6b64-154">Se `ContentPresenter` for encontrado, o modelo associará automaticamente a propriedade do controle <xref:System.Windows.Controls.ContentControl.Content> ao `ContentPresenter` .</span><span class="sxs-lookup"><span data-stu-id="a6b64-154">If the `ContentPresenter` is found, the template automatically binds the control's <xref:System.Windows.Controls.ContentControl.Content> property to the `ContentPresenter`.</span></span>

## <a name="use-the-template"></a><span data-ttu-id="a6b64-155">Usar o modelo</span><span class="sxs-lookup"><span data-stu-id="a6b64-155">Use the template</span></span>

<span data-ttu-id="a6b64-156">Localize os botões que foram declarados no início deste artigo.</span><span class="sxs-lookup"><span data-stu-id="a6b64-156">Find the buttons that were declared at the start of this article.</span></span>

[!code-xaml[Initial](~/samples/snippets/desktop-guide/wpf/styles-templates-create-apply-template/csharp/Window1.xaml#Initial)]

<span data-ttu-id="a6b64-157">Defina a propriedade do segundo botão <xref:System.Windows.Controls.Control.Template> para o `roundbutton` recurso:</span><span class="sxs-lookup"><span data-stu-id="a6b64-157">Set the second button's <xref:System.Windows.Controls.Control.Template> property to the `roundbutton` resource:</span></span>

[!code-xaml[StyledButton](~/samples/snippets/desktop-guide/wpf/styles-templates-create-apply-template/csharp/Window3.xaml#StyledButton)]

<span data-ttu-id="a6b64-158">Se você executar o projeto e examinar o resultado, verá que o botão tem um plano de fundo arredondado.</span><span class="sxs-lookup"><span data-stu-id="a6b64-158">If you run the project and look at the result, you'll see that the button has a rounded background.</span></span>

![Janela do WPF com um botão de modelo oval](media/create-apply-template/styled-button.png)

<span data-ttu-id="a6b64-160">Você deve ter notado que o botão não é um círculo, mas está distorcido.</span><span class="sxs-lookup"><span data-stu-id="a6b64-160">You may have noticed that the button isn't a circle but is skewed.</span></span> <span data-ttu-id="a6b64-161">Devido à maneira como o elemento \*\* \: :: no-Loc ( <Ellipse> ):::\*\* funciona, ele sempre se expande para preencher o espaço disponível.</span><span class="sxs-lookup"><span data-stu-id="a6b64-161">Because of the way the **\<Ellipse>** element works, it always expands to fill the available space.</span></span> <span data-ttu-id="a6b64-162">Torne o círculo uniforme alterando as  **:::no-loc text="width":::** Propriedades e do botão **:::no-loc text="height":::** para o mesmo valor:</span><span class="sxs-lookup"><span data-stu-id="a6b64-162">Make the circle uniform by changing the button's  **:::no-loc text="width":::** and **:::no-loc text="height":::** properties to the same value:</span></span>

[!code-xaml[StyledButtonSize](~/samples/snippets/desktop-guide/wpf/styles-templates-create-apply-template/csharp/Window3.xaml#StyledButtonSize)]

![Janela do WPF com um botão circular de modelo](media/create-apply-template/styled-uniform-button.png)

## <a name="add-a-trigger"></a><span data-ttu-id="a6b64-164">Adicionar um gatilho</span><span class="sxs-lookup"><span data-stu-id="a6b64-164">Add a Trigger</span></span>

<span data-ttu-id="a6b64-165">Embora um botão com um modelo aplicado pareça diferente, ele comporta-se como qualquer outro botão.</span><span class="sxs-lookup"><span data-stu-id="a6b64-165">Even though a button with a template applied looks different, it behaves the same as any other button.</span></span> <span data-ttu-id="a6b64-166">Se você pressionar o botão, o <xref:System.Windows.Controls.Primitives.ButtonBase.Click> evento será acionado.</span><span class="sxs-lookup"><span data-stu-id="a6b64-166">If you press the button, the <xref:System.Windows.Controls.Primitives.ButtonBase.Click> event fires.</span></span> <span data-ttu-id="a6b64-167">No entanto, você pode ter notado que quando você move o mouse sobre o botão, os visuais do botão não são alterados.</span><span class="sxs-lookup"><span data-stu-id="a6b64-167">However, you may have noticed that when you move your mouse over the button, the button's visuals don't change.</span></span> <span data-ttu-id="a6b64-168">Essas interações visuais são todas definidas pelo modelo.</span><span class="sxs-lookup"><span data-stu-id="a6b64-168">These visual interactions are all defined by the template.</span></span>

<span data-ttu-id="a6b64-169">Com o evento dinâmico e os sistemas de propriedades fornecidos pelo WPF, você pode observar uma propriedade específica para um valor e reestilizar o modelo quando apropriado.</span><span class="sxs-lookup"><span data-stu-id="a6b64-169">With the dynamic event and property systems that WPF provides, you can watch a specific property for a value and then restyle the template when appropriate.</span></span> <span data-ttu-id="a6b64-170">Neste exemplo, você observará a propriedade do botão <xref:System.Windows.UIElement.IsMouseOver> .</span><span class="sxs-lookup"><span data-stu-id="a6b64-170">In this example, you'll watch the button's <xref:System.Windows.UIElement.IsMouseOver> property.</span></span> <span data-ttu-id="a6b64-171">Quando o mouse estiver sobre o controle, estilizar \*\* \: :: no-Loc ( <Ellipse> ):::\*\* com uma nova cor.</span><span class="sxs-lookup"><span data-stu-id="a6b64-171">When the mouse is over the control, style the **\<Ellipse>** with a new color.</span></span> <span data-ttu-id="a6b64-172">Esse tipo de gatilho é conhecido como um *PropertyTrigger*.</span><span class="sxs-lookup"><span data-stu-id="a6b64-172">This type of trigger is known as a *PropertyTrigger*.</span></span>

<span data-ttu-id="a6b64-173">Para que isso funcione, você precisará adicionar um nome ao \*\* \: :: no-Loc ( <Ellipse> ):::\*\* que você pode referenciar.</span><span class="sxs-lookup"><span data-stu-id="a6b64-173">For this to work, you'll need to add a name to the **\<Ellipse>** that you can reference.</span></span> <span data-ttu-id="a6b64-174">Dê a ele o nome de **backgroundelement**.</span><span class="sxs-lookup"><span data-stu-id="a6b64-174">Give it the name of **backgroundElement**.</span></span>

[!code-xaml[EllipseName](~/samples/snippets/desktop-guide/wpf/styles-templates-create-apply-template/csharp/Window4.xaml#EllipseName)]

<span data-ttu-id="a6b64-175">Em seguida, adicione um novo <xref:System.Windows.Trigger> à coleção [ControlTemplate. Triggers](xref:System.Windows.Controls.ControlTemplate.Triggers) .</span><span class="sxs-lookup"><span data-stu-id="a6b64-175">Next, add a new <xref:System.Windows.Trigger> to the [ControlTemplate.Triggers](xref:System.Windows.Controls.ControlTemplate.Triggers) collection.</span></span> <span data-ttu-id="a6b64-176">O gatilho observará o `IsMouseOver` evento para o valor `true` .</span><span class="sxs-lookup"><span data-stu-id="a6b64-176">The trigger will watch the `IsMouseOver` event for the value `true`.</span></span>

[!code-xaml[ControlTemplate](~/samples/snippets/desktop-guide/wpf/styles-templates-create-apply-template/csharp/Window4.xaml?name=ControlTemplate&highlight=6-10)]

<span data-ttu-id="a6b64-177">Em seguida, adicione um \*\* \: :: no-Loc ( <Setter> ):::\*\* a \*\* \: :: no-Loc ( <Trigger> ):::\*\* que altera a propriedade **Fill** de \*\* \: :: no-Loc ( <Ellipse> )::\*\* : para uma nova cor.</span><span class="sxs-lookup"><span data-stu-id="a6b64-177">Next, add a **\<Setter>** to the **\<Trigger>** that changes the **Fill** property of the **\<Ellipse>** to a new color.</span></span>

[!code-xaml[MouseOver](~/samples/snippets/desktop-guide/wpf/styles-templates-create-apply-template/csharp/Window5.xaml#MouseOver)]

<span data-ttu-id="a6b64-178">Execute o projeto.</span><span class="sxs-lookup"><span data-stu-id="a6b64-178">Run the project.</span></span> <span data-ttu-id="a6b64-179">Observe que quando você move o mouse sobre o botão, a cor das alterações \*\* \: :: não-Loc ( <Ellipse> )::\*\* : é alterada.</span><span class="sxs-lookup"><span data-stu-id="a6b64-179">Notice that when you move the mouse over the button, the color of the **\<Ellipse>** changes.</span></span>

![o mouse se move sobre o botão do WPF para alterar a cor do preenchimento](media/create-apply-template/mouse-move-over-button.gif)

## <a name="use-a-visualstate"></a><span data-ttu-id="a6b64-181">Usar um VisualState</span><span class="sxs-lookup"><span data-stu-id="a6b64-181">Use a VisualState</span></span>

<span data-ttu-id="a6b64-182">Os Estados visuais são definidos e disparados por um controle.</span><span class="sxs-lookup"><span data-stu-id="a6b64-182">Visual states are defined and triggered by a control.</span></span> <span data-ttu-id="a6b64-183">Por exemplo, quando o mouse é movido sobre o controle, o `CommonStates.MouseOver` estado é disparado.</span><span class="sxs-lookup"><span data-stu-id="a6b64-183">For example, when the mouse is moved on top of the control, the `CommonStates.MouseOver` state is triggered.</span></span> <span data-ttu-id="a6b64-184">Você pode animar as alterações de propriedade com base no estado atual do controle.</span><span class="sxs-lookup"><span data-stu-id="a6b64-184">You can animate property changes based on the current state of the control.</span></span> <span data-ttu-id="a6b64-185">Na seção anterior, um \*\* \: :: no-Loc ( <PropertyTrigger> ):::\*\* foi usado para alterar o primeiro plano do botão para `AliceBlue` quando a `IsMouseOver` propriedade foi `true` .</span><span class="sxs-lookup"><span data-stu-id="a6b64-185">In the previous section, a **\<PropertyTrigger>** was used to change the foreground of the button to `AliceBlue` when the `IsMouseOver` property was `true`.</span></span> <span data-ttu-id="a6b64-186">Em vez disso, crie um estado visual que anime a alteração dessa cor, fornecendo uma transição suave.</span><span class="sxs-lookup"><span data-stu-id="a6b64-186">Instead, create a visual state that animates the change of this color, providing a smooth transition.</span></span> <span data-ttu-id="a6b64-187">Para obter mais informações sobre *VisualStates*, consulte [estilos e modelos no WPF](../fundamentals/styles-templates-overview.md#visual-states).</span><span class="sxs-lookup"><span data-stu-id="a6b64-187">For more information about *VisualStates*, see [Styles and templates in WPF](../fundamentals/styles-templates-overview.md#visual-states).</span></span>

<span data-ttu-id="a6b64-188">Para converter \*\* \: :: no-Loc ( <PropertyTrigger> ):::\*\* para um estado visual animado, primeiro remova o **\<ControlTemplate.Triggers>** elemento do modelo.</span><span class="sxs-lookup"><span data-stu-id="a6b64-188">To convert the **\<PropertyTrigger>** to an animated visual state, First, remove the **\<ControlTemplate.Triggers>** element from your template.</span></span>

[!code-xaml[CleanTemplate](~/samples/snippets/desktop-guide/wpf/styles-templates-create-apply-template/csharp/Window5.xaml#CleanTemplate)]

<span data-ttu-id="a6b64-189">Em seguida, na raiz \*\* \: :: no-Loc ( <Grid> ):::\*\* do modelo de controle, adicione o elemento \*\* \: :: no-Loc (<VisualStateManager. VisualStateGroups>):::\*\* Element com um \*\* \: :: no-Loc ( <VisualStateGroup> ):::\*\* para `CommonStates` .</span><span class="sxs-lookup"><span data-stu-id="a6b64-189">Next, in the **\<Grid>** root of the control template, add the **\<VisualStateManager.VisualStateGroups>** element with a **\<VisualStateGroup>** for `CommonStates`.</span></span> <span data-ttu-id="a6b64-190">Defina dois Estados `Normal` e `MouseOver` .</span><span class="sxs-lookup"><span data-stu-id="a6b64-190">Define two states, `Normal` and `MouseOver`.</span></span>

[!code-xaml[VisualState](~/samples/snippets/desktop-guide/wpf/styles-templates-create-apply-template/csharp/Window6.xaml#VisualState)]

<span data-ttu-id="a6b64-191">Todas as animações definidas em \*\* \: :: no-Loc ( <VisualState> ):::\*\* são aplicadas quando esse estado é disparado.</span><span class="sxs-lookup"><span data-stu-id="a6b64-191">Any animations defined in a **\<VisualState>** are applied when that state is triggered.</span></span> <span data-ttu-id="a6b64-192">Crie animações para cada Estado.</span><span class="sxs-lookup"><span data-stu-id="a6b64-192">Create animations for each state.</span></span> <span data-ttu-id="a6b64-193">As animações são colocadas dentro de um elemento \*\* \: :: no-Loc ( <Storyboard> ):::\*\* Element.</span><span class="sxs-lookup"><span data-stu-id="a6b64-193">Animations are put inside of a **\<Storyboard>** element.</span></span> <span data-ttu-id="a6b64-194">Para obter mais informações sobre storyboards, consulte [visão geral de storyboards](/dotnet/desktop/wpf/graphics-multimedia/storyboards-overview).</span><span class="sxs-lookup"><span data-stu-id="a6b64-194">For more information about storyboards, see [Storyboards Overview](/dotnet/desktop/wpf/graphics-multimedia/storyboards-overview).</span></span>

- <span data-ttu-id="a6b64-195">Normal</span><span class="sxs-lookup"><span data-stu-id="a6b64-195">Normal</span></span>

  <span data-ttu-id="a6b64-196">Esse estado anima o preenchimento da elipse, restaurando-o para a `Background` cor do controle.</span><span class="sxs-lookup"><span data-stu-id="a6b64-196">This state animates the ellipse fill, restoring it to the control's `Background` color.</span></span>

  [!code-xaml[NormalState](~/samples/snippets/desktop-guide/wpf/styles-templates-create-apply-template/csharp/Window6.xaml#NormalState)]

- <span data-ttu-id="a6b64-197">MouseOver</span><span class="sxs-lookup"><span data-stu-id="a6b64-197">MouseOver</span></span>

  <span data-ttu-id="a6b64-198">Esse estado anima a cor da elipse `Background` com uma nova cor: `Yellow` .</span><span class="sxs-lookup"><span data-stu-id="a6b64-198">This state animates the ellipse `Background` color to a new color: `Yellow`.</span></span>

  [!code-xaml[MouseOverState](~/samples/snippets/desktop-guide/wpf/styles-templates-create-apply-template/csharp/Window6.xaml#MouseOverState)]

<span data-ttu-id="a6b64-199">O \*\* \: :: no-Loc ( <ControlTemplate> )::\*\* : deve agora ser semelhante ao seguinte.</span><span class="sxs-lookup"><span data-stu-id="a6b64-199">The **\<ControlTemplate>** should now look like the following.</span></span>

[!code-xaml[FinalTemplate](~/samples/snippets/desktop-guide/wpf/styles-templates-create-apply-template/csharp/Window7.xaml#FinalTemplate)]

<span data-ttu-id="a6b64-200">Execute o projeto.</span><span class="sxs-lookup"><span data-stu-id="a6b64-200">Run the project.</span></span> <span data-ttu-id="a6b64-201">Observe que quando você move o mouse sobre o botão, a cor de \*\* \: :: no-Loc ( <Ellipse> ):::\*\* anima.</span><span class="sxs-lookup"><span data-stu-id="a6b64-201">Notice that when you move the mouse over the button, the color of the **\<Ellipse>** animates.</span></span>

![o mouse se move sobre o botão do WPF para alterar a cor do preenchimento](media/create-apply-template/mouse-move-over-button-visualstate.gif)

## <a name="next-steps"></a><span data-ttu-id="a6b64-203">Próximas etapas</span><span class="sxs-lookup"><span data-stu-id="a6b64-203">Next steps</span></span>

- [<span data-ttu-id="a6b64-204">Criar um estilo para um controle no WPF</span><span class="sxs-lookup"><span data-stu-id="a6b64-204">Create a style for a control in WPF</span></span>](../fundamentals/styles-templates-create-apply-style.md)
- [<span data-ttu-id="a6b64-205">Estilos e modelos no WPF</span><span class="sxs-lookup"><span data-stu-id="a6b64-205">Styles and templates in WPF</span></span>](../fundamentals/styles-templates-overview.md)
- [<span data-ttu-id="a6b64-206">Visão geral dos recursos XAML</span><span class="sxs-lookup"><span data-stu-id="a6b64-206">Overview of XAML Resources</span></span>](../fundamentals/xaml-resources-define.md)
