---
title: Crie um modelo no WPF - .NET Desktop
description: Aprenda a criar e referenciar um modelo de controle no Windows Presentation Foundation e no .NET Core.
author: thraka
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
ms.openlocfilehash: c901864d387b8de976bbfa9a9b3c14a7d5a0b4d8
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2019
ms.locfileid: "82071244"
---
# <a name="create-a-template-for-a-control"></a><span data-ttu-id="21ee9-103">Crie um modelo para um controle</span><span class="sxs-lookup"><span data-stu-id="21ee9-103">Create a template for a control</span></span>

<span data-ttu-id="21ee9-104">Com o Windows Presentation Foundation (WPF), você pode personalizar a estrutura visual e o comportamento de um controle existente com seu próprio modelo reutilizável.</span><span class="sxs-lookup"><span data-stu-id="21ee9-104">With Windows Presentation Foundation (WPF), you can customize an existing control's visual structure and behavior with your own reusable template.</span></span> <span data-ttu-id="21ee9-105">Os modelos podem ser aplicados globalmente ao seu aplicativo, janelas e páginas ou diretamente aos controles.</span><span class="sxs-lookup"><span data-stu-id="21ee9-105">Templates can be applied globally to your application, windows and pages, or directly to controls.</span></span> <span data-ttu-id="21ee9-106">A maioria dos cenários que exigem que você crie um novo controle pode ser coberto criando um novo modelo para um controle existente.</span><span class="sxs-lookup"><span data-stu-id="21ee9-106">Most scenarios that require you to create a new control can be covered by instead creating a new template for an existing control.</span></span>

[!INCLUDE [desktop guide under construction](../../../includes/desktop-guide-preview-note.md)]

<span data-ttu-id="21ee9-107">Neste artigo, você explorará a <xref:System.Windows.Controls.ControlTemplate> criação <xref:System.Windows.Controls.Button> de um novo para o controle.</span><span class="sxs-lookup"><span data-stu-id="21ee9-107">In this article, you'll explore creating a new <xref:System.Windows.Controls.ControlTemplate> for the <xref:System.Windows.Controls.Button> control.</span></span>

## <a name="when-to-create-a-controltemplate"></a><span data-ttu-id="21ee9-108">Quando criar um ControlTemplate</span><span class="sxs-lookup"><span data-stu-id="21ee9-108">When to create a ControlTemplate</span></span>

<span data-ttu-id="21ee9-109">Os controles têm muitas <xref:System.Windows.Controls.Border.Background%2A>propriedades, tais como, <xref:System.Windows.Controls.Control.Foreground%2A>e <xref:System.Windows.Controls.Control.FontFamily%2A>.</span><span class="sxs-lookup"><span data-stu-id="21ee9-109">Controls have many properties, such as <xref:System.Windows.Controls.Border.Background%2A>, <xref:System.Windows.Controls.Control.Foreground%2A>, and <xref:System.Windows.Controls.Control.FontFamily%2A>.</span></span> <span data-ttu-id="21ee9-110">Essas propriedades controlam diferentes aspectos da aparência do controle, mas as alterações que você pode fazer definindo essas propriedades são limitadas.</span><span class="sxs-lookup"><span data-stu-id="21ee9-110">These properties control different aspects of the control's appearance, but the changes that you can make by setting these properties are limited.</span></span> <span data-ttu-id="21ee9-111">Por exemplo, você <xref:System.Windows.Controls.Control.Foreground%2A> pode definir <xref:System.Windows.Controls.Control.FontStyle%2A> a propriedade como <xref:System.Windows.Controls.CheckBox>azul e itálica em um .</span><span class="sxs-lookup"><span data-stu-id="21ee9-111">For example, you can set the <xref:System.Windows.Controls.Control.Foreground%2A> property to blue and <xref:System.Windows.Controls.Control.FontStyle%2A> to italic on a <xref:System.Windows.Controls.CheckBox>.</span></span> <span data-ttu-id="21ee9-112">Quando você deseja personalizar a aparência do controle além do que a configuração das outras propriedades no controle pode fazer, você cria um <xref:System.Windows.Controls.ControlTemplate>.</span><span class="sxs-lookup"><span data-stu-id="21ee9-112">When you want to customize the control's appearance beyond what setting the other properties on the control can do, you create a <xref:System.Windows.Controls.ControlTemplate>.</span></span>

<span data-ttu-id="21ee9-113">Na maioria das interfaces de usuário, um botão tem a mesma aparência geral: um retângulo com algum texto.</span><span class="sxs-lookup"><span data-stu-id="21ee9-113">In most user interfaces, a button has the same general appearance: a rectangle with some text.</span></span> <span data-ttu-id="21ee9-114">Se você quiser criar um botão arredondado, você pode criar um novo controle que herda do botão ou recria a funcionalidade do botão.</span><span class="sxs-lookup"><span data-stu-id="21ee9-114">If you wanted to create a rounded button, you could create a new control that inherits from the button or recreates the functionality of the button.</span></span> <span data-ttu-id="21ee9-115">Além disso, o novo controle do usuário forneceria o visual circular.</span><span class="sxs-lookup"><span data-stu-id="21ee9-115">In addition, the new user control would provide the circular visual.</span></span>

<span data-ttu-id="21ee9-116">Você pode evitar criar novos controles personalizando o layout visual de um controle existente.</span><span class="sxs-lookup"><span data-stu-id="21ee9-116">You can avoid creating new controls by customizing the visual layout of an existing control.</span></span> <span data-ttu-id="21ee9-117">Com um botão arredondado, você cria um <xref:System.Windows.Controls.ControlTemplate> com o layout visual desejado.</span><span class="sxs-lookup"><span data-stu-id="21ee9-117">With a rounded button, you create a <xref:System.Windows.Controls.ControlTemplate> with the desired visual layout.</span></span>

<span data-ttu-id="21ee9-118">Por outro lado, se você precisar de um controle com novas funcionalidades, diferentes propriedades e novas configurações, você criará um novo <xref:System.Windows.Controls.UserControl>.</span><span class="sxs-lookup"><span data-stu-id="21ee9-118">On the other hand, if you need a control with new functionality, different properties, and new settings, you would create a new <xref:System.Windows.Controls.UserControl>.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="21ee9-119">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="21ee9-119">Prerequisites</span></span>

<span data-ttu-id="21ee9-120">Crie um novo aplicativo WPF e no *MainWindow.xaml* (ou outra janela \*\* \<\*\* de sua escolha) defina as seguintes propriedades no elemento Janela>:</span><span class="sxs-lookup"><span data-stu-id="21ee9-120">Create a new WPF application and in *MainWindow.xaml* (or another window of your choice) set the following properties on the **\<Window>** element:</span></span>

|     |     |
| --- | --- |
| **[!OP.NO-LOC(Title)]**         | `Template Intro Sample` |
| **[!OP.NO-LOC(SizeToContent)]** | `WidthAndHeight` |
| **[!OP.NO-LOC(MinWidth)]**      | `250` |

<span data-ttu-id="21ee9-121">Defina o conteúdo do elemento \*\* \<Janela>\*\* para o seguinte XAML:</span><span class="sxs-lookup"><span data-stu-id="21ee9-121">Set the content of the **\<Window>** element to the following XAML:</span></span>

[!code-xaml[Initial](~/samples/snippets/desktop-guide/wpf/styles-templates-create-apply-template/csharp/Window1.xaml#Initial)]

<span data-ttu-id="21ee9-122">No final, o arquivo *MainWindow.xaml* deve ser semelhante ao seguinte:</span><span class="sxs-lookup"><span data-stu-id="21ee9-122">In the end, the *MainWindow.xaml* file should look similar to the following:</span></span>

[!code-xaml[InitialWhole](~/samples/snippets/desktop-guide/wpf/styles-templates-create-apply-template/csharp/Window1.xaml#InitialWhole)]

<span data-ttu-id="21ee9-123">Se você executar o aplicativo, ele se parece com o seguinte:</span><span class="sxs-lookup"><span data-stu-id="21ee9-123">If you run the application, it looks like the following:</span></span>

![Janela WPF com dois botões sem estilo](media/create-apply-template/unstyled-button.png)

## <a name="create-a-controltemplate"></a><span data-ttu-id="21ee9-125">Criar um ControlTemplate</span><span class="sxs-lookup"><span data-stu-id="21ee9-125">Create a ControlTemplate</span></span>

<span data-ttu-id="21ee9-126">A maneira mais comum de declarar <xref:System.Windows.Controls.ControlTemplate> `Resources` a é como um recurso na seção em um arquivo XAML.</span><span class="sxs-lookup"><span data-stu-id="21ee9-126">The most common way to declare a <xref:System.Windows.Controls.ControlTemplate> is as a resource in the `Resources` section in a XAML file.</span></span> <span data-ttu-id="21ee9-127">Como os modelos são recursos, eles obedecem às mesmas regras de escopo que se aplicam a todos os recursos.</span><span class="sxs-lookup"><span data-stu-id="21ee9-127">Because templates are resources, they obey the same scoping rules that apply to all resources.</span></span> <span data-ttu-id="21ee9-128">Simplificando, onde você declara que um modelo afeta onde o modelo pode ser aplicado.</span><span class="sxs-lookup"><span data-stu-id="21ee9-128">Put simply, where you declare a template affects where the template can be applied.</span></span> <span data-ttu-id="21ee9-129">Por exemplo, se você declarar o modelo no elemento raiz do arquivo XAML da definição do aplicativo, o modelo poderá ser usado em qualquer lugar do seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="21ee9-129">For example, if you declare the template in the root element of your application definition XAML file, the template can be used anywhere in your application.</span></span> <span data-ttu-id="21ee9-130">Se você definir o modelo em uma janela, apenas os controles dessa janela podem usar o modelo.</span><span class="sxs-lookup"><span data-stu-id="21ee9-130">If you define the template in a window, only the controls in that window can use the template.</span></span>

<span data-ttu-id="21ee9-131">Para começar, adicione `Window.Resources` um elemento ao seu arquivo *MainWindow.xaml:*</span><span class="sxs-lookup"><span data-stu-id="21ee9-131">To start with, add a `Window.Resources` element to your *MainWindow.xaml* file:</span></span>

[!code-xaml[WindowResStart](~/samples/snippets/desktop-guide/wpf/styles-templates-create-apply-template/csharp/Window2.xaml#WindowResStart)]

<span data-ttu-id="21ee9-132">Crie um novo \*\* \<>ControlTemplate\*\* com o seguinte conjunto de propriedades:</span><span class="sxs-lookup"><span data-stu-id="21ee9-132">Create a new **\<ControlTemplate>** with the following properties set:</span></span>

|     |     |
| --- | --- |
| <span data-ttu-id="21ee9-133">**x:Key**</span><span class="sxs-lookup"><span data-stu-id="21ee9-133">**x:Key**</span></span>         | `roundbutton` |
| **TargetType**    | `Button` |

<span data-ttu-id="21ee9-134">Este modelo de controle será simples:</span><span class="sxs-lookup"><span data-stu-id="21ee9-134">This control template will be simple:</span></span>

- <span data-ttu-id="21ee9-135">um elemento raiz para o controle, um<xref:System.Windows.Controls.Grid></span><span class="sxs-lookup"><span data-stu-id="21ee9-135">a root element for the control, a <xref:System.Windows.Controls.Grid></span></span>
- <span data-ttu-id="21ee9-136">um <xref:System.Windows.Shapes.Ellipse> para desenhar a aparência arredondada do botão</span><span class="sxs-lookup"><span data-stu-id="21ee9-136">an <xref:System.Windows.Shapes.Ellipse> to draw the rounded appearance of the button</span></span>
- <span data-ttu-id="21ee9-137">a <xref:System.Windows.Controls.ContentPresenter> para exibir o conteúdo do botão especificado pelo usuário</span><span class="sxs-lookup"><span data-stu-id="21ee9-137">a <xref:System.Windows.Controls.ContentPresenter> to display the user-specified button content</span></span>

[!code-xaml[ControlTemplate](~/samples/snippets/desktop-guide/wpf/styles-templates-create-apply-template/csharp/Window3.xaml#ControlTemplate)]

### <a name="templatebinding"></a><span data-ttu-id="21ee9-138">TemplateBinding</span><span class="sxs-lookup"><span data-stu-id="21ee9-138">TemplateBinding</span></span>

<span data-ttu-id="21ee9-139">Quando você cria <xref:System.Windows.Controls.ControlTemplate>um novo , você ainda pode querer usar as propriedades públicas para alterar a aparência do controle.</span><span class="sxs-lookup"><span data-stu-id="21ee9-139">When you create a new <xref:System.Windows.Controls.ControlTemplate>, you still might want to use the public properties to change the control's appearance.</span></span> <span data-ttu-id="21ee9-140">A extensão [de marcação De vinculação de modelos](../../framework/wpf/advanced/templatebinding-markup-extension.md) vincula uma propriedade de um elemento que está no <xref:System.Windows.Controls.ControlTemplate> a um imóvel público definido pelo controle.</span><span class="sxs-lookup"><span data-stu-id="21ee9-140">The [TemplateBinding](../../framework/wpf/advanced/templatebinding-markup-extension.md) markup extension binds a property of an element that is in the <xref:System.Windows.Controls.ControlTemplate> to a public property that is defined by the control.</span></span> <span data-ttu-id="21ee9-141">Quando você usa um [TemplateBinding,](../../framework/wpf/advanced/templatebinding-markup-extension.md)você habilita propriedades no controle para agir como parâmetros para o modelo.</span><span class="sxs-lookup"><span data-stu-id="21ee9-141">When you use a [TemplateBinding](../../framework/wpf/advanced/templatebinding-markup-extension.md), you enable properties on the control to act as parameters to the template.</span></span> <span data-ttu-id="21ee9-142">Ou seja, quando uma propriedade em um controle é definida, esse valor é passado para o elemento que contém a [TemplateBinding](../../framework/wpf/advanced/templatebinding-markup-extension.md).</span><span class="sxs-lookup"><span data-stu-id="21ee9-142">That is, when a property on a control is set, that value is passed on to the element that has the [TemplateBinding](../../framework/wpf/advanced/templatebinding-markup-extension.md) on it.</span></span>

### <a name="ellipse"></a><span data-ttu-id="21ee9-143">Ellipse</span><span class="sxs-lookup"><span data-stu-id="21ee9-143">Ellipse</span></span>

<span data-ttu-id="21ee9-144">Observe que **:::no-loc text="Fill":::** **:::no-loc text="Stroke":::** as propriedades do elemento \*\* \<Ellipse>\*\* estão <xref:System.Windows.Controls.Control.Foreground> <xref:System.Windows.Controls.Control.Background> ligadas ao controle e propriedades.</span><span class="sxs-lookup"><span data-stu-id="21ee9-144">Notice that the **:::no-loc text="Fill":::** and **:::no-loc text="Stroke":::** properties of the **\<Ellipse>** element are bound to the control's <xref:System.Windows.Controls.Control.Foreground> and <xref:System.Windows.Controls.Control.Background> properties.</span></span>

### <a name="contentpresenter"></a><span data-ttu-id="21ee9-145">ContentPresenter</span><span class="sxs-lookup"><span data-stu-id="21ee9-145">ContentPresenter</span></span>

<span data-ttu-id="21ee9-146">Um elemento [ \<de>de ContentPresenter](xref:System.Windows.Controls.ContentPresenter) também é adicionado ao modelo.</span><span class="sxs-lookup"><span data-stu-id="21ee9-146">A [\<ContentPresenter>](xref:System.Windows.Controls.ContentPresenter) element is also added to the template.</span></span> <span data-ttu-id="21ee9-147">Como este modelo foi projetado para um botão, leve <xref:System.Windows.Controls.ContentControl>em consideração que o botão herda de .</span><span class="sxs-lookup"><span data-stu-id="21ee9-147">Because this template is designed for a button, take into consideration that the button inherits from <xref:System.Windows.Controls.ContentControl>.</span></span> <span data-ttu-id="21ee9-148">O botão apresenta o conteúdo do elemento.</span><span class="sxs-lookup"><span data-stu-id="21ee9-148">The button presents the content of the element.</span></span> <span data-ttu-id="21ee9-149">Você pode definir qualquer coisa dentro do botão, como texto simples ou até mesmo outro controle.</span><span class="sxs-lookup"><span data-stu-id="21ee9-149">You can set anything inside of the button, such as plain text or even another control.</span></span> <span data-ttu-id="21ee9-150">Ambos os botões a seguir são válidos:</span><span class="sxs-lookup"><span data-stu-id="21ee9-150">Both of the following are valid buttons:</span></span>

```xaml
<Button>My Text</Button>

<!-- and -->

<Button>
    <CheckBox>Checkbox in a button</CheckBox>
</Button>
```

<span data-ttu-id="21ee9-151">Em ambos os exemplos anteriores, o texto e a caixa de seleção são definidos como a propriedade [Button.Content.](xref:System.Windows.Controls.ContentControl.Content)</span><span class="sxs-lookup"><span data-stu-id="21ee9-151">In both of the previous examples, the text and the checkbox are set as the [Button.Content](xref:System.Windows.Controls.ContentControl.Content) property.</span></span> <span data-ttu-id="21ee9-152">O que for definido como o conteúdo pode ser apresentado através de um \*\* \<contentPresenter>\*\*, que é o que o modelo faz.</span><span class="sxs-lookup"><span data-stu-id="21ee9-152">Whatever is set as the content can be presented through a **\<ContentPresenter>**, which is what the template does.</span></span>

<span data-ttu-id="21ee9-153">Se <xref:System.Windows.Controls.ControlTemplate> o é aplicado <xref:System.Windows.Controls.ContentControl> a um `Button`tipo, <xref:System.Windows.Controls.ContentPresenter> como a , a é pesquisado na árvore de elementos.</span><span class="sxs-lookup"><span data-stu-id="21ee9-153">If the <xref:System.Windows.Controls.ControlTemplate> is applied to a <xref:System.Windows.Controls.ContentControl> type, such as a `Button`, a <xref:System.Windows.Controls.ContentPresenter> is searched for in the element tree.</span></span> <span data-ttu-id="21ee9-154">Se `ContentPresenter` for encontrado, o modelo vincula automaticamente <xref:System.Windows.Controls.ContentControl.Content> a `ContentPresenter`propriedade do controle ao .</span><span class="sxs-lookup"><span data-stu-id="21ee9-154">If the `ContentPresenter` is found, the template automatically binds the control's <xref:System.Windows.Controls.ContentControl.Content> property to the `ContentPresenter`.</span></span>

## <a name="use-the-template"></a><span data-ttu-id="21ee9-155">Usar o modelo</span><span class="sxs-lookup"><span data-stu-id="21ee9-155">Use the template</span></span>

<span data-ttu-id="21ee9-156">Encontre os botões que foram declarados no início deste artigo.</span><span class="sxs-lookup"><span data-stu-id="21ee9-156">Find the buttons that were declared at the start of this article.</span></span>

[!code-xaml[Initial](~/samples/snippets/desktop-guide/wpf/styles-templates-create-apply-template/csharp/Window1.xaml#Initial)]

<span data-ttu-id="21ee9-157">Defina a propriedade <xref:System.Windows.Controls.Control.Template> do `roundbutton` segundo botão para o recurso:</span><span class="sxs-lookup"><span data-stu-id="21ee9-157">Set the second button's <xref:System.Windows.Controls.Control.Template> property to the `roundbutton` resource:</span></span>

[!code-xaml[StyledButton](~/samples/snippets/desktop-guide/wpf/styles-templates-create-apply-template/csharp/Window3.xaml#StyledButton)]

<span data-ttu-id="21ee9-158">Se você executar o projeto e olhar para o resultado, você verá que o botão tem um fundo arredondado.</span><span class="sxs-lookup"><span data-stu-id="21ee9-158">If you run the project and look at the result, you'll see that the button has a rounded background.</span></span>

![Janela WPF com um botão oval de modelo](media/create-apply-template/styled-button.png)

<span data-ttu-id="21ee9-160">Você deve ter notado que o botão não é um círculo, mas está distorcido.</span><span class="sxs-lookup"><span data-stu-id="21ee9-160">You may have noticed that the button isn't a circle but is skewed.</span></span> <span data-ttu-id="21ee9-161">Devido à forma \*\* \<\*\* como o elemento Elipse>funciona, ele sempre se expande para preencher o espaço disponível.</span><span class="sxs-lookup"><span data-stu-id="21ee9-161">Because of the way the **\<Ellipse>** element works, it always expands to fill the available space.</span></span> <span data-ttu-id="21ee9-162">Faça o uniforme do círculo **:::no-loc text="width":::** alterando o botão e **:::no-loc text="height":::** as propriedades para o mesmo valor:</span><span class="sxs-lookup"><span data-stu-id="21ee9-162">Make the circle uniform by changing the button's  **:::no-loc text="width":::** and **:::no-loc text="height":::** properties to the same value:</span></span>

[!code-xaml[StyledButtonSize](~/samples/snippets/desktop-guide/wpf/styles-templates-create-apply-template/csharp/Window3.xaml#StyledButtonSize)]

![Janela WPF com um botão circular de modelo](media/create-apply-template/styled-uniform-button.png)

## <a name="add-a-trigger"></a><span data-ttu-id="21ee9-164">Adicionar um gatilho</span><span class="sxs-lookup"><span data-stu-id="21ee9-164">Add a Trigger</span></span>

<span data-ttu-id="21ee9-165">Mesmo que um botão com um modelo aplicado pareça diferente, ele se comporta da mesma forma que qualquer outro botão.</span><span class="sxs-lookup"><span data-stu-id="21ee9-165">Even though a button with a template applied looks different, it behaves the same as any other button.</span></span> <span data-ttu-id="21ee9-166">Se você apertar o <xref:System.Windows.Controls.Primitives.ButtonBase.Click> botão, o evento é acionado.</span><span class="sxs-lookup"><span data-stu-id="21ee9-166">If you press the button, the <xref:System.Windows.Controls.Primitives.ButtonBase.Click> event fires.</span></span> <span data-ttu-id="21ee9-167">No entanto, você deve ter notado que quando você move o mouse sobre o botão, o visual do botão não muda.</span><span class="sxs-lookup"><span data-stu-id="21ee9-167">However, you may have noticed that when you move your mouse over the button, the button's visuals don't change.</span></span> <span data-ttu-id="21ee9-168">Essas interações visuais são todas definidas pelo modelo.</span><span class="sxs-lookup"><span data-stu-id="21ee9-168">These visual interactions are all defined by the template.</span></span>

<span data-ttu-id="21ee9-169">Com os sistemas dinâmicos de eventos e propriedades que o WPF fornece, você pode observar uma propriedade específica por um valor e, em seguida, reestilizar o modelo quando apropriado.</span><span class="sxs-lookup"><span data-stu-id="21ee9-169">With the dynamic event and property systems that WPF provides, you can watch a specific property for a value and then restyle the template when appropriate.</span></span> <span data-ttu-id="21ee9-170">Neste exemplo, você observará a <xref:System.Windows.UIElement.IsMouseOver> propriedade do botão.</span><span class="sxs-lookup"><span data-stu-id="21ee9-170">In this example, you'll watch the button's <xref:System.Windows.UIElement.IsMouseOver> property.</span></span> <span data-ttu-id="21ee9-171">Quando o mouse estiver sobre o controle, estilize o \*\* \<>de Elipse\*\* com uma nova cor.</span><span class="sxs-lookup"><span data-stu-id="21ee9-171">When the mouse is over the control, style the **\<Ellipse>** with a new color.</span></span> <span data-ttu-id="21ee9-172">Este tipo de gatilho é conhecido como *PropertyTrigger*.</span><span class="sxs-lookup"><span data-stu-id="21ee9-172">This type of trigger is known as a *PropertyTrigger*.</span></span>

<span data-ttu-id="21ee9-173">Para que isso funcione, você precisará adicionar um nome ao \*\* \<>de Elipse\*\* que você pode referenciar.</span><span class="sxs-lookup"><span data-stu-id="21ee9-173">For this to work, you'll need to add a name to the **\<Ellipse>** that you can reference.</span></span> <span data-ttu-id="21ee9-174">Dê-lhe o nome de **backgroundElement**.</span><span class="sxs-lookup"><span data-stu-id="21ee9-174">Give it the name of **backgroundElement**.</span></span>

[!code-xaml[EllipseName](~/samples/snippets/desktop-guide/wpf/styles-templates-create-apply-template/csharp/Window4.xaml#EllipseName)]

<span data-ttu-id="21ee9-175">Em seguida, <xref:System.Windows.Trigger> adicione um novo à coleção [ControlTemplate.Triggers.](xref:System.Windows.Controls.ControlTemplate.Triggers)</span><span class="sxs-lookup"><span data-stu-id="21ee9-175">Next, add a new <xref:System.Windows.Trigger> to the [ControlTemplate.Triggers](xref:System.Windows.Controls.ControlTemplate.Triggers) collection.</span></span> <span data-ttu-id="21ee9-176">O gatilho observará o `IsMouseOver` `true`evento pelo valor.</span><span class="sxs-lookup"><span data-stu-id="21ee9-176">The trigger will watch the `IsMouseOver` event for the value `true`.</span></span>

[!code-xaml[ControlTemplate](~/samples/snippets/desktop-guide/wpf/styles-templates-create-apply-template/csharp/Window4.xaml?name=ControlTemplate&highlight=6-10)]

<span data-ttu-id="21ee9-177">Em seguida, adicione um \*\* \<setter>\*\* ao \*\* \<trigger>\*\* que altera a propriedade **Preenchimento** do \*\* \<>de Elipse\*\* para uma nova cor.</span><span class="sxs-lookup"><span data-stu-id="21ee9-177">Next, add a **\<Setter>** to the **\<Trigger>** that changes the **Fill** property of the **\<Ellipse>** to a new color.</span></span>

[!code-xaml[MouseOver](~/samples/snippets/desktop-guide/wpf/styles-templates-create-apply-template/csharp/Window5.xaml#MouseOver)]

<span data-ttu-id="21ee9-178">Execute o projeto.</span><span class="sxs-lookup"><span data-stu-id="21ee9-178">Run the project.</span></span> <span data-ttu-id="21ee9-179">Observe que quando você move o mouse sobre o botão, a cor da \*\* \<elipse>\*\* muda.</span><span class="sxs-lookup"><span data-stu-id="21ee9-179">Notice that when you move the mouse over the button, the color of the **\<Ellipse>** changes.</span></span>

![mouse move sobre o botão WPF para alterar a cor de preenchimento](media/create-apply-template/mouse-move-over-button.gif)

## <a name="use-a-visualstate"></a><span data-ttu-id="21ee9-181">Use um VisualState</span><span class="sxs-lookup"><span data-stu-id="21ee9-181">Use a VisualState</span></span>

<span data-ttu-id="21ee9-182">Os estados visuais são definidos e acionados por um controle.</span><span class="sxs-lookup"><span data-stu-id="21ee9-182">Visual states are defined and triggered by a control.</span></span> <span data-ttu-id="21ee9-183">Por exemplo, quando o mouse é movido `CommonStates.MouseOver` em cima do controle, o estado é acionado.</span><span class="sxs-lookup"><span data-stu-id="21ee9-183">For example, when the mouse is moved on top of the control, the `CommonStates.MouseOver` state is triggered.</span></span> <span data-ttu-id="21ee9-184">Você pode animar as mudanças de propriedade com base no estado atual do controle.</span><span class="sxs-lookup"><span data-stu-id="21ee9-184">You can animate property changes based on the current state of the control.</span></span> <span data-ttu-id="21ee9-185">Na seção anterior, `IsMouseOver` um `true` \*\* \<>PropertyTrigger\*\* foi usado para `AliceBlue` alterar o primeiro plano do botão para quando a propriedade era .</span><span class="sxs-lookup"><span data-stu-id="21ee9-185">In the previous section, a **\<PropertyTrigger>** was used to change the foreground of the button to `AliceBlue` when the `IsMouseOver` property was `true`.</span></span> <span data-ttu-id="21ee9-186">Em vez disso, crie um estado visual que anima a mudança dessa cor, proporcionando uma transição suave.</span><span class="sxs-lookup"><span data-stu-id="21ee9-186">Instead, create a visual state that animates the change of this color, providing a smooth transition.</span></span> <span data-ttu-id="21ee9-187">Para obter mais informações sobre *o VisualStates,* consulte [Estilos e modelos no WPF](../fundamentals/styles-templates-overview.md#visual-states).</span><span class="sxs-lookup"><span data-stu-id="21ee9-187">For more information about *VisualStates*, see [Styles and templates in WPF](../fundamentals/styles-templates-overview.md#visual-states).</span></span>

<span data-ttu-id="21ee9-188">Para converter \*\* \<oTrigger>em\*\* um estado visual animado, primeiro, remova o \*\* \<elemento ControlTemplate.Triggers>\*\* do seu modelo.</span><span class="sxs-lookup"><span data-stu-id="21ee9-188">To convert the **\<PropertyTrigger>** to an animated visual state, First, remove the **\<ControlTemplate.Triggers>** element from your template.</span></span>

[!code-xaml[CleanTemplate](~/samples/snippets/desktop-guide/wpf/styles-templates-create-apply-template/csharp/Window5.xaml#CleanTemplate)]

<span data-ttu-id="21ee9-189">Em seguida, \*\* \<\*\* na grade>raiz do modelo de controle, adicione o `CommonStates` \*\* \<elemento visualStateManager.VisualStateGroups>\*\* com um \*\* \<visualStateGroup>\*\* para .</span><span class="sxs-lookup"><span data-stu-id="21ee9-189">Next, in the **\<Grid>** root of the control template, add the **\<VisualStateManager.VisualStateGroups>** element with a **\<VisualStateGroup>** for `CommonStates`.</span></span> <span data-ttu-id="21ee9-190">Defina dois `Normal` `MouseOver`estados, e .</span><span class="sxs-lookup"><span data-stu-id="21ee9-190">Define two states, `Normal` and `MouseOver`.</span></span>

[!code-xaml[VisualState](~/samples/snippets/desktop-guide/wpf/styles-templates-create-apply-template/csharp/Window6.xaml#VisualState)]

<span data-ttu-id="21ee9-191">Todas as animações definidas em um \*\* \<visualState>\*\* são aplicadas quando esse estado é acionado.</span><span class="sxs-lookup"><span data-stu-id="21ee9-191">Any animations defined in a **\<VisualState>** are applied when that state is triggered.</span></span> <span data-ttu-id="21ee9-192">Crie animações para cada estado.</span><span class="sxs-lookup"><span data-stu-id="21ee9-192">Create animations for each state.</span></span> <span data-ttu-id="21ee9-193">As animações são \*\* \<\*\* colocadas dentro de um elemento de>storyboard.</span><span class="sxs-lookup"><span data-stu-id="21ee9-193">Animations are put inside of a **\<Storyboard>** element.</span></span> <span data-ttu-id="21ee9-194">Para obter mais informações sobre storyboards, consulte [Storyboards Overview](../../framework/wpf/graphics-multimedia/storyboards-overview.md).</span><span class="sxs-lookup"><span data-stu-id="21ee9-194">For more information about storyboards, see [Storyboards Overview](../../framework/wpf/graphics-multimedia/storyboards-overview.md).</span></span>

- <span data-ttu-id="21ee9-195">Normal</span><span class="sxs-lookup"><span data-stu-id="21ee9-195">Normal</span></span>

  <span data-ttu-id="21ee9-196">Este estado anima o preenchimento de elipse, restaurando-o à cor do `Background` controle.</span><span class="sxs-lookup"><span data-stu-id="21ee9-196">This state animates the ellipse fill, restoring it to the control's `Background` color.</span></span>

  [!code-xaml[NormalState](~/samples/snippets/desktop-guide/wpf/styles-templates-create-apply-template/csharp/Window6.xaml#NormalState)]

- <span data-ttu-id="21ee9-197">MouseOver</span><span class="sxs-lookup"><span data-stu-id="21ee9-197">MouseOver</span></span>

  <span data-ttu-id="21ee9-198">Este estado anima a `Background` cor da elipse `Yellow`a uma nova cor: .</span><span class="sxs-lookup"><span data-stu-id="21ee9-198">This state animates the ellipse `Background` color to a new color: `Yellow`.</span></span>

  [!code-xaml[MouseOverState](~/samples/snippets/desktop-guide/wpf/styles-templates-create-apply-template/csharp/Window6.xaml#MouseOverState)]

<span data-ttu-id="21ee9-199">O \*\* \<>ControlTemplate\*\* deve agora parecer o seguinte.</span><span class="sxs-lookup"><span data-stu-id="21ee9-199">The **\<ControlTemplate>** should now look like the following.</span></span>

[!code-xaml[FinalTemplate](~/samples/snippets/desktop-guide/wpf/styles-templates-create-apply-template/csharp/Window7.xaml#FinalTemplate)]

<span data-ttu-id="21ee9-200">Execute o projeto.</span><span class="sxs-lookup"><span data-stu-id="21ee9-200">Run the project.</span></span> <span data-ttu-id="21ee9-201">Observe que quando você move o mouse sobre o botão, a cor da \*\* \<elipse>\*\* anima.</span><span class="sxs-lookup"><span data-stu-id="21ee9-201">Notice that when you move the mouse over the button, the color of the **\<Ellipse>** animates.</span></span>

![mouse move sobre o botão WPF para alterar a cor de preenchimento](media/create-apply-template/mouse-move-over-button-visualstate.gif)

## <a name="next-steps"></a><span data-ttu-id="21ee9-203">Próximas etapas</span><span class="sxs-lookup"><span data-stu-id="21ee9-203">Next steps</span></span>

- [<span data-ttu-id="21ee9-204">Crie um estilo para um controle no WPF</span><span class="sxs-lookup"><span data-stu-id="21ee9-204">Create a style for a control in WPF</span></span>](../fundamentals/styles-templates-create-apply-style.md)
- [<span data-ttu-id="21ee9-205">Estilos e modelos em WPF</span><span class="sxs-lookup"><span data-stu-id="21ee9-205">Styles and templates in WPF</span></span>](../fundamentals/styles-templates-overview.md)
- [<span data-ttu-id="21ee9-206">Visão geral dos recursos XAML</span><span class="sxs-lookup"><span data-stu-id="21ee9-206">Overview of XAML Resources</span></span>](../fundamentals/xaml-resources-define.md)
