---
title: Extensibilidade da grade de propriedade - exemplo WF
ms.date: 03/30/2017
ms.assetid: 3530c3a3-756d-4712-9f10-fb2897414d3a
ms.openlocfilehash: f1cb64cb10e8d88359e8f94b57602ab127314cff
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/30/2019
ms.locfileid: "55287866"
---
# <a name="property-grid-extensibility"></a><span data-ttu-id="cb560-102">Extensibilidade da grade de propriedade</span><span class="sxs-lookup"><span data-stu-id="cb560-102">Property grid extensibility</span></span>

<span data-ttu-id="cb560-103">Um desenvolvedor pode personalizar a grade de propriedade que é exibida quando uma determinada atividade é selecionada no designer.</span><span class="sxs-lookup"><span data-stu-id="cb560-103">A developer can customize the property grid that is displayed when a given activity is selected within the designer.</span></span> <span data-ttu-id="cb560-104">Isso pode ser feito para criar uma experiência rica de edição.</span><span class="sxs-lookup"><span data-stu-id="cb560-104">This can be done to create a rich editing experience.</span></span> <span data-ttu-id="cb560-105">Este exemplo mostra como isso pode ser feito.</span><span class="sxs-lookup"><span data-stu-id="cb560-105">This sample shows how this can be done.</span></span>

## <a name="demonstrates"></a><span data-ttu-id="cb560-106">Demonstra</span><span class="sxs-lookup"><span data-stu-id="cb560-106">Demonstrates</span></span>

<span data-ttu-id="cb560-107">Extensibilidade da grade de propriedade do designer de fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="cb560-107">Workflow designer property grid extensibility.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="cb560-108">Os exemplos podem já estar instalados no seu computador.</span><span class="sxs-lookup"><span data-stu-id="cb560-108">The samples may already be installed on your machine.</span></span> <span data-ttu-id="cb560-109">Verifique o seguinte diretório (padrão) antes de continuar.</span><span class="sxs-lookup"><span data-stu-id="cb560-109">Check for the following (default) directory before continuing.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> <span data-ttu-id="cb560-110">Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e o Windows Workflow Foundation (WF) exemplos do .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os Windows Communication Foundation (WCF) e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos.</span><span class="sxs-lookup"><span data-stu-id="cb560-110">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="cb560-111">Este exemplo está localizado no seguinte diretório.</span><span class="sxs-lookup"><span data-stu-id="cb560-111">This sample is located in the following directory.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Designer\PropertyGridExtensibility`

## <a name="discussion"></a><span data-ttu-id="cb560-112">Discussão</span><span class="sxs-lookup"><span data-stu-id="cb560-112">Discussion</span></span>

<span data-ttu-id="cb560-113">Para estender a grade de propriedade, um desenvolvedor tem opções personalizar a aparência de um editor embutido da grade de propriedade ou fornecer uma caixa de diálogo que aparece para uma superfície mais avançado de edição.</span><span class="sxs-lookup"><span data-stu-id="cb560-113">To extend the property grid, a developer has options to customize the inline appearance of a property grid editor or provide a dialog that appears for a more advanced editing surface.</span></span> <span data-ttu-id="cb560-114">Há dois editores diferentes demonstrados nesse exemplo; um editor embutido e um editor caixa de diálogo.</span><span class="sxs-lookup"><span data-stu-id="cb560-114">There are two different editors demonstrated in this sample; an inline editor and a dialog editor.</span></span>

## <a name="inline-editor"></a><span data-ttu-id="cb560-115">Editor embutido</span><span class="sxs-lookup"><span data-stu-id="cb560-115">Inline editor</span></span>

<span data-ttu-id="cb560-116">O exemplo editor embutido demonstra o seguinte:</span><span class="sxs-lookup"><span data-stu-id="cb560-116">The inline editor sample demonstrates the following:</span></span>

- <span data-ttu-id="cb560-117">Cria um tipo deriva de <xref:System.Activities.Presentation.PropertyEditing.PropertyValueEditor>.</span><span class="sxs-lookup"><span data-stu-id="cb560-117">Creates a type that derives from <xref:System.Activities.Presentation.PropertyEditing.PropertyValueEditor>.</span></span>

- <span data-ttu-id="cb560-118">No construtor, o <xref:System.Activities.Presentation.PropertyEditing.PropertyValueEditor.InlineEditorTemplate%2A> valor é definido com um modelo de dados do Windows Presentation Foundation (WPF).</span><span class="sxs-lookup"><span data-stu-id="cb560-118">In the constructor, the <xref:System.Activities.Presentation.PropertyEditing.PropertyValueEditor.InlineEditorTemplate%2A> value is set with a Windows Presentation Foundation (WPF) data template.</span></span> <span data-ttu-id="cb560-119">Isso pode ser associado a um modelo XAML, mas nesse exemplo, o código é usado para inicializar a associação de dados.</span><span class="sxs-lookup"><span data-stu-id="cb560-119">This can be bound to a XAML template, but in this sample, code is used to initialize data binding.</span></span>

- <span data-ttu-id="cb560-120">O modelo de dados tem um contexto de dados de <xref:System.Activities.Presentation.PropertyEditing.PropertyValue> de item processado na grade de propriedade.</span><span class="sxs-lookup"><span data-stu-id="cb560-120">The data template has a data context of the <xref:System.Activities.Presentation.PropertyEditing.PropertyValue> of the item rendered in the property grid.</span></span> <span data-ttu-id="cb560-121">Observe o seguinte código (de CustomInlineEditor.cs) que este contexto associando a propriedade de `Value` .</span><span class="sxs-lookup"><span data-stu-id="cb560-121">Note in the following code (from CustomInlineEditor.cs) that this context then binds to the `Value` property.</span></span>

    ```csharp
    FrameworkElementFactory stack = new FrameworkElementFactory(typeof(StackPanel));
    FrameworkElementFactory slider = new FrameworkElementFactory(typeof(Slider));
    Binding sliderBinding = new Binding("Value");
    sliderBinding.Mode = BindingMode.TwoWay;
    slider.SetValue(Slider.MinimumProperty, 0.0);
    slider.SetValue(Slider.MaximumProperty, 100.0);
    slider.SetValue(Slider.ValueProperty, sliderBinding);
    stack.AppendChild(slider);
    ```

- <span data-ttu-id="cb560-122">Porque a atividade e o designer estão no mesmo assembly, o registro dos atributos do designer de atividade é feito no construtor estático de atividade próprio, conforme mostrado no exemplo de SimpleCodeActivity.cs.</span><span class="sxs-lookup"><span data-stu-id="cb560-122">Because the activity and the designer are in the same assembly, registration of the activity designer attributes are accomplished in the static constructor of the activity itself, as shown in the following example from SimpleCodeActivity.cs.</span></span>

    ```csharp
    static SimpleCodeActivity()
    {
        AttributeTableBuilder builder = new AttributeTableBuilder();
        builder.AddCustomAttributes(typeof(SimpleCodeActivity), "RepeatCount", new EditorAttribute(typeof(CustomInlineEditor), typeof(PropertyValueEditor)));
        builder.AddCustomAttributes(typeof(SimpleCodeActivity), "FileName", new EditorAttribute(typeof(FilePickerEditor), typeof(DialogPropertyValueEditor)));
        MetadataStore.AddAttributeTable(builder.CreateTable());
    }
    ```

## <a name="dialog-editor"></a><span data-ttu-id="cb560-123">Editor de caixa de diálogo</span><span class="sxs-lookup"><span data-stu-id="cb560-123">Dialog editor</span></span>

<span data-ttu-id="cb560-124">O exemplo do editor de diálogo demonstra o seguinte:</span><span class="sxs-lookup"><span data-stu-id="cb560-124">The dialog editor sample demonstrates the following:</span></span>

1. <span data-ttu-id="cb560-125">Cria um tipo deriva de <xref:System.Activities.Presentation.PropertyEditing.DialogPropertyValueEditor>.</span><span class="sxs-lookup"><span data-stu-id="cb560-125">Creates a type that derives from <xref:System.Activities.Presentation.PropertyEditing.DialogPropertyValueEditor>.</span></span>

2. <span data-ttu-id="cb560-126">Defina o valor de <xref:System.Activities.Presentation.PropertyEditing.PropertyValueEditor.InlineEditorTemplate%2A> no construtor com um modelo de dados de [!INCLUDE[avalon2](../../../../includes/avalon2-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="cb560-126">Sets the <xref:System.Activities.Presentation.PropertyEditing.PropertyValueEditor.InlineEditorTemplate%2A> value in the constructor with a [!INCLUDE[avalon2](../../../../includes/avalon2-md.md)] data template.</span></span> <span data-ttu-id="cb560-127">Isso pode ser criado em XAML, mas nesse exemplo, este é criado em código.</span><span class="sxs-lookup"><span data-stu-id="cb560-127">This can be created in XAML, but in this sample, this is created in code.</span></span>

3. <span data-ttu-id="cb560-128">O modelo de dados tem um contexto de dados de <xref:System.Activities.Presentation.PropertyEditing.PropertyValue> de item processado na grade de propriedade.</span><span class="sxs-lookup"><span data-stu-id="cb560-128">The data template has a data context of the <xref:System.Activities.Presentation.PropertyEditing.PropertyValue> of the item rendered in the property grid.</span></span> <span data-ttu-id="cb560-129">No código a seguir, ou associação à propriedade de `Value` .</span><span class="sxs-lookup"><span data-stu-id="cb560-129">In the following code, this then binds to the `Value` property.</span></span> <span data-ttu-id="cb560-130">É importante incluir também <xref:System.Activities.Presentation.PropertyEditing.EditModeSwitchButton> para fornecer o botão que aumenta a caixa de diálogo em FilePickerEditor.cs.</span><span class="sxs-lookup"><span data-stu-id="cb560-130">It is critical to also include an <xref:System.Activities.Presentation.PropertyEditing.EditModeSwitchButton> to provide the button that raises the dialog in FilePickerEditor.cs.</span></span>

    ```csharp
    this.InlineEditorTemplate = new DataTemplate();

    FrameworkElementFactory stack = new FrameworkElementFactory(typeof(StackPanel));
    stack.SetValue(StackPanel.OrientationProperty, Orientation.Horizontal);
    FrameworkElementFactory label = new FrameworkElementFactory(typeof(Label));
    Binding labelBinding = new Binding("Value");
    label.SetValue(Label.ContentProperty, labelBinding);
    label.SetValue(Label.MaxWidthProperty, 90.0);

    stack.AppendChild(label);

    FrameworkElementFactory editModeSwitch = new FrameworkElementFactory(typeof(EditModeSwitchButton));

    editModeSwitch.SetValue(EditModeSwitchButton.TargetEditModeProperty, PropertyContainerEditMode.Dialog);

    stack.AppendChild(editModeSwitch);

    this.InlineEditorTemplate.VisualTree = stack;
    ```

4. <span data-ttu-id="cb560-131">Substitui o método de <xref:System.Activities.Presentation.PropertyEditing.DialogPropertyValueEditor.ShowDialog%2A> no tipo de designer para manipular a exibição da caixa de diálogo.</span><span class="sxs-lookup"><span data-stu-id="cb560-131">Overrides the <xref:System.Activities.Presentation.PropertyEditing.DialogPropertyValueEditor.ShowDialog%2A> method in the designer type to handle the display of the dialog.</span></span> <span data-ttu-id="cb560-132">Nesse exemplo, <xref:System.Windows.Forms.FileDialog> básico é mostrado.</span><span class="sxs-lookup"><span data-stu-id="cb560-132">In this sample, a basic <xref:System.Windows.Forms.FileDialog> is shown.</span></span>

    ```csharp
    public override void ShowDialog(PropertyValue propertyValue, IInputElement commandSource)
    {
        Microsoft.Win32.OpenFileDialog ofd = new Microsoft.Win32.OpenFileDialog();
        if (ofd.ShowDialog() == true)
        {
            propertyValue.Value = ofd.FileName;
        }
    }
    ```

5. <span data-ttu-id="cb560-133">Porque a atividade e o designer estão no mesmo assembly, o registro dos atributos do designer de atividade é feito no construtor estático de atividade próprio, conforme mostrado no exemplo de SimpleCodeActivity.cs.</span><span class="sxs-lookup"><span data-stu-id="cb560-133">Because the activity and the designer are in the same assembly, registration of the activity designer attributes are accomplished in the static constructor of the activity itself, as shown in the following example from SimpleCodeActivity.cs.</span></span>

    ```csharp
    static SimpleCodeActivity()
    {
        AttributeTableBuilder builder = new AttributeTableBuilder();
        builder.AddCustomAttributes(typeof(SimpleCodeActivity), "RepeatCount", new EditorAttribute(typeof(CustomInlineEditor), typeof(PropertyValueEditor)));
        builder.AddCustomAttributes(typeof(SimpleCodeActivity), "FileName", new EditorAttribute(typeof(FilePickerEditor), typeof(DialogPropertyValueEditor)));
        MetadataStore.AddAttributeTable(builder.CreateTable());
    }
    ```

## <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="cb560-134">Para configurar, compilar, e executar o exemplo</span><span class="sxs-lookup"><span data-stu-id="cb560-134">To set up, build, and run the sample</span></span>

1. <span data-ttu-id="cb560-135">Crie a solução, e abra Workflow1.xaml.</span><span class="sxs-lookup"><span data-stu-id="cb560-135">Build the solution, and then open Workflow1.xaml.</span></span>

2. <span data-ttu-id="cb560-136">Arraste uma **SimpleCodeActivity** Toolbox para a tela do designer.</span><span class="sxs-lookup"><span data-stu-id="cb560-136">Drag a **SimpleCodeActivity** from the toolbox onto the designer canvas.</span></span>

3. <span data-ttu-id="cb560-137">Clique o **SimpleCodeActivity** e, em seguida, abra a grade propriedade onde há um controle deslizante e um arquivo de controle de separação.</span><span class="sxs-lookup"><span data-stu-id="cb560-137">Click the **SimpleCodeActivity** and then open the property grid where there is a slider control and a file picking control.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="cb560-138">Os exemplos podem já estar instalados no seu computador.</span><span class="sxs-lookup"><span data-stu-id="cb560-138">The samples may already be installed on your machine.</span></span> <span data-ttu-id="cb560-139">Verifique o seguinte diretório (padrão) antes de continuar.</span><span class="sxs-lookup"><span data-stu-id="cb560-139">Check for the following (default) directory before continuing.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> <span data-ttu-id="cb560-140">Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e o Windows Workflow Foundation (WF) exemplos do .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os Windows Communication Foundation (WCF) e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos.</span><span class="sxs-lookup"><span data-stu-id="cb560-140">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="cb560-141">Este exemplo está localizado no seguinte diretório.</span><span class="sxs-lookup"><span data-stu-id="cb560-141">This sample is located in the following directory.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Designer\PropertyGridExtensibility`