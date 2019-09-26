---
title: 'Como: criar um designer personalizado de atividades'
ms.date: 03/30/2017
ms.assetid: 2f3aade6-facc-44ef-9657-a407ef8b9b31
ms.openlocfilehash: 3c326508744f2aa2b34f5ee574cc9ec1e2863cf6
ms.sourcegitcommit: 1e72e2990220b3635cebc39586828af9deb72d8c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/26/2019
ms.locfileid: "71306356"
---
# <a name="how-to-create-a-custom-activity-designer"></a><span data-ttu-id="16e61-102">Como: criar um designer personalizado de atividades</span><span class="sxs-lookup"><span data-stu-id="16e61-102">How to: Create a Custom Activity Designer</span></span>

<span data-ttu-id="16e61-103">Designers personalizados de atividade são normalmente implementados de modo que as atividades passível de composição sejam associados com outras atividades cujos os designers podem ser ignorados sobre a superfície de design com eles.</span><span class="sxs-lookup"><span data-stu-id="16e61-103">Custom activity designers are typically implemented so that their associated activities are composable with other activities whose designers can be dropped on to the design surface with them.</span></span> <span data-ttu-id="16e61-104">Essa funcionalidade requer que um designer de atividade personalizado forneça uma "área de destino" onde uma atividade arbitrária pode ser colocada e também o meio de gerenciar a coleção resultante de elementos na superfície de design.</span><span class="sxs-lookup"><span data-stu-id="16e61-104">This functionality requires that a custom activity designer provide a "drop zone" where an arbitrary activity can be placed and also the means to manage the resulting collection of elements on the design surface.</span></span> <span data-ttu-id="16e61-105">Este tópico descreve como criar um designer personalizado de atividade que contém uma área para arrastar e soltar e como criar um designer personalizado de atividade que fornece a funcionalidade de edição necessária gerenciar a coleção de elementos de designer.</span><span class="sxs-lookup"><span data-stu-id="16e61-105">This topic describes how to create a custom activity designer that contains such a drop zone and how to create a custom activity designer that provides that editing functionality needed to manage the collection of designer elements.</span></span>

<span data-ttu-id="16e61-106">Designers personalizados de atividade normalmente herdam de <xref:System.Activities.Presentation.ActivityDesigner> que é tem como padrão o tipo base do designer de atividade para todas as atividades sem um designer específico.</span><span class="sxs-lookup"><span data-stu-id="16e61-106">Custom activity designers typically inherit from <xref:System.Activities.Presentation.ActivityDesigner> which is the default base activity designer type for any activities without a specific designer.</span></span> <span data-ttu-id="16e61-107">Este tipo fornece a experiência em tempo de design de interagir com a grade de propriedade e configurar aspectos básicos como gerenciar cores e ícones.</span><span class="sxs-lookup"><span data-stu-id="16e61-107">This type provides the design-time experience of interacting with the property grid and configuring basic aspects such as managing colors and icons.</span></span>

<span data-ttu-id="16e61-108"><xref:System.Activities.Presentation.ActivityDesigner> usa dois controles auxiliar, <xref:System.Activities.Presentation.WorkflowItemPresenter> e <xref:System.Activities.Presentation.WorkflowItemsPresenter> para tornar mais fácil desenvolver designer personalizadas de atividade.</span><span class="sxs-lookup"><span data-stu-id="16e61-108"><xref:System.Activities.Presentation.ActivityDesigner> uses two helper controls, <xref:System.Activities.Presentation.WorkflowItemPresenter> and <xref:System.Activities.Presentation.WorkflowItemsPresenter> to make it easier to develop custom activity designers.</span></span> <span data-ttu-id="16e61-109">Manipular a funcionalidade comum como arrastar e soltar de elementos filho, de exclusão, de seleção, e a adição desses elementos filho.</span><span class="sxs-lookup"><span data-stu-id="16e61-109">They handle common functionality like dragging and dropping of child elements, deletion, selection, and addition of those child elements.</span></span> <span data-ttu-id="16e61-110">O <xref:System.Activities.Presentation.WorkflowItemPresenter> permite um único elemento de interface do usuário filho dentro, fornecendo a "área de destino" <xref:System.Activities.Presentation.WorkflowItemsPresenter> , enquanto o pode fornecer suporte a vários elementos de interface do usuário, incluindo funcionalidades adicionais como ordenação, movimentação, exclusão e adição de elementos filho.</span><span class="sxs-lookup"><span data-stu-id="16e61-110">The <xref:System.Activities.Presentation.WorkflowItemPresenter> allows a single child UI element inside, providing the "drop zone", it while the <xref:System.Activities.Presentation.WorkflowItemsPresenter> can provide support multiple UI elements, including additional functionality like the ordering, moving, deleting, and adding of child elements.</span></span>

<span data-ttu-id="16e61-111">A outra parte importante da história que precisa de realce na implementação de um designer de atividade personalizado se refere à maneira como as edições visuais são ligadas usando a ligação de dados do WPF à instância armazenada na memória do que estamos editando no designer.</span><span class="sxs-lookup"><span data-stu-id="16e61-111">The other key part of the story that needs highlighting in the implementation of a custom activity designer concerns the way in which the visual edits are bound using WPF data binding to the instance stored in memory of what we are editing in the designer.</span></span> <span data-ttu-id="16e61-112">Isso é feito pela árvore modelo de item, que também é responsável para ativar a notificação de alteração e o rastreamento de eventos como alterações nos estados.</span><span class="sxs-lookup"><span data-stu-id="16e61-112">This is accomplished by the Model Item tree, which is also responsible for enabling change notification and the tracking of events like changes in states.</span></span>

<span data-ttu-id="16e61-113">Este tópico descreve dois procedimentos.</span><span class="sxs-lookup"><span data-stu-id="16e61-113">This topic outlines two procedures.</span></span>

1. <span data-ttu-id="16e61-114">O primeiro procedimento descreve como criar um designer personalizado de atividade com <xref:System.Activities.Presentation.WorkflowItemPresenter> que fornece a área para arrastar e soltar que recebe outras atividades.</span><span class="sxs-lookup"><span data-stu-id="16e61-114">The first procedure describes how to create a custom activity designer with a <xref:System.Activities.Presentation.WorkflowItemPresenter> that provides the drop zone that receives other activities.</span></span> <span data-ttu-id="16e61-115">Esse procedimento se baseia na amostra [designers de composição personalizados – apresentador de item de fluxo de trabalho](./samples/custom-composite-designers-workflow-item-presenter.md) .</span><span class="sxs-lookup"><span data-stu-id="16e61-115">This procedure is based on the [Custom Composite Designers - Workflow Item Presenter](./samples/custom-composite-designers-workflow-item-presenter.md) sample.</span></span>

2. <span data-ttu-id="16e61-116">O segundo procedimento descreve como criar um designer personalizado de atividade com <xref:System.Activities.Presentation.WorkflowItemsPresenter> que fornece funcionalidade necessária edição de uma coleção de elementos contidos.</span><span class="sxs-lookup"><span data-stu-id="16e61-116">The second procedure describes how to create a custom activity designer with a <xref:System.Activities.Presentation.WorkflowItemsPresenter> that provides the functionality needed to edit of a collection of contained elements.</span></span> <span data-ttu-id="16e61-117">Esse procedimento se baseia na amostra [designers de composição personalizados – apresentador de itens de fluxo de trabalho](./samples/custom-composite-designers-workflow-items-presenter.md) .</span><span class="sxs-lookup"><span data-stu-id="16e61-117">This procedure is based on the [Custom Composite Designers - Workflow Items Presenter](./samples/custom-composite-designers-workflow-items-presenter.md) sample.</span></span>

## <a name="to-create-a-custom-activity-designer-with-a-drop-zone-using-workflowitempresenter"></a><span data-ttu-id="16e61-118">Para criar um designer personalizado de atividade com uma área para arrastar e soltar usando WorkflowItemPresenter</span><span class="sxs-lookup"><span data-stu-id="16e61-118">To create a custom activity designer with a drop zone using WorkflowItemPresenter</span></span>

1. <span data-ttu-id="16e61-119">Inicie o Visual Studio 2010.</span><span class="sxs-lookup"><span data-stu-id="16e61-119">Start Visual Studio 2010.</span></span>

2. <span data-ttu-id="16e61-120">No menu **arquivo** , aponte para **novo**e, em seguida, selecione **projeto...** .</span><span class="sxs-lookup"><span data-stu-id="16e61-120">On the **File** menu, point to **New**, and then select **Project…**.</span></span>

     <span data-ttu-id="16e61-121">A caixa de diálogo **Novo Projeto** é aberta.</span><span class="sxs-lookup"><span data-stu-id="16e61-121">The **New Project** dialog box opens.</span></span>

3. <span data-ttu-id="16e61-122">No painel **modelos instalados** , selecione **Windows** na categoria idioma preferencial.</span><span class="sxs-lookup"><span data-stu-id="16e61-122">In the **Installed Templates** pane, select **Windows** from your preferred language category.</span></span>

4. <span data-ttu-id="16e61-123">No painel **modelos** , selecione **aplicativo WPF**.</span><span class="sxs-lookup"><span data-stu-id="16e61-123">In the **Templates** pane, select **WPF Application**.</span></span>

5. <span data-ttu-id="16e61-124">Na caixa **nome** , digite `UsingWorkflowItemPresenter`.</span><span class="sxs-lookup"><span data-stu-id="16e61-124">In the **Name** box, enter `UsingWorkflowItemPresenter`.</span></span>

6. <span data-ttu-id="16e61-125">Na caixa **local** , insira o diretório no qual você deseja salvar o projeto ou clique em **procurar** para navegar até ele.</span><span class="sxs-lookup"><span data-stu-id="16e61-125">In the **Location** box, enter the directory in which you want to save your project, or click **Browse** to navigate to it.</span></span>

7. <span data-ttu-id="16e61-126">Na caixa **solução** , aceite o valor padrão.</span><span class="sxs-lookup"><span data-stu-id="16e61-126">In the **Solution** box, accept the default value.</span></span>

8. <span data-ttu-id="16e61-127">Clique em **OK**.</span><span class="sxs-lookup"><span data-stu-id="16e61-127">Click **OK**.</span></span>

9. <span data-ttu-id="16e61-128">Clique com o botão direito do mouse no arquivo *mainwindows. XAML* na **Gerenciador de soluções**, selecione **excluir** e confirmar **OK** na caixa de diálogo **Microsoft Visual Studio** .</span><span class="sxs-lookup"><span data-stu-id="16e61-128">Right-click the *MainWindows.xaml* file in the **Solution Explorer**, select **Delete** and confirm **OK** in the **Microsoft Visual Studio** dialog box.</span></span>

10. <span data-ttu-id="16e61-129">Clique com o botão direito do mouse no projeto UsingWorkflowItemPresenter em **Gerenciador de soluções**, selecione **Adicionar**e **novo item...**</span><span class="sxs-lookup"><span data-stu-id="16e61-129">Right-click the UsingWorkflowItemPresenter project in **Solution Explorer**, select **Add**, then **New Item…**</span></span> <span data-ttu-id="16e61-130">para abrir a caixa de diálogo **Adicionar novo item** e selecione a categoria **WPF** na seção **modelos instalados** à esquerda.</span><span class="sxs-lookup"><span data-stu-id="16e61-130">to bring up the **Add New Item** dialog and select the **WPF** category from the **Installed Templates** section on the left.</span></span>

11. <span data-ttu-id="16e61-131">Selecione o modelo **janela (WPF)** , nomeie- `RehostingWFDesigner`o e clique em **Adicionar**.</span><span class="sxs-lookup"><span data-stu-id="16e61-131">Select the  **Window (WPF)** template, name it `RehostingWFDesigner`, and click **Add**.</span></span>

12. <span data-ttu-id="16e61-132">Abra o arquivo *RehostingWFDesigner. XAML* e cole o código a seguir nele para definir a interface do usuário para o aplicativo:</span><span class="sxs-lookup"><span data-stu-id="16e61-132">Open the *RehostingWFDesigner.xaml* file and paste the following code into it to define the UI for the application:</span></span>

    ```xaml
    <Window x:Class=" UsingWorkflowItemPresenter.RehostingWFDesigner"
            xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
            xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
            xmlns:sapt="clr-namespace:System.Activities.Presentation.Toolbox;assembly=System.Activities.Presentation"
            xmlns:sys="clr-namespace:System;assembly=mscorlib"
            Title="Window1" Height="600" Width="900">
        <Window.Resources>
            <sys:String x:Key="AssemblyName">System.Activities, Version=4.0.0.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35</sys:String>
        </Window.Resources>
        <Grid>
            <Grid.ColumnDefinitions>
                <ColumnDefinition Width="2*"/>
                <ColumnDefinition Width="7*"/>
                <ColumnDefinition Width="3*"/>
            </Grid.ColumnDefinitions>
            <Border Grid.Column="0">
                <sapt:ToolboxControl Name="Toolbox">
                    <sapt:ToolboxCategory CategoryName="Basic">
                        <sapt:ToolboxItemWrapper AssemblyName="{StaticResource AssemblyName}" >
                            <sapt:ToolboxItemWrapper.ToolName>
                                System.Activities.Statements.Sequence
                            </sapt:ToolboxItemWrapper.ToolName>
                           </sapt:ToolboxItemWrapper>
                        <sapt:ToolboxItemWrapper  AssemblyName="{StaticResource AssemblyName}">
                            <sapt:ToolboxItemWrapper.ToolName>
                                System.Activities.Statements.WriteLine
                            </sapt:ToolboxItemWrapper.ToolName>

                        </sapt:ToolboxItemWrapper>
                        <sapt:ToolboxItemWrapper  AssemblyName="{StaticResource AssemblyName}">
                            <sapt:ToolboxItemWrapper.ToolName>
                                System.Activities.Statements.If
                            </sapt:ToolboxItemWrapper.ToolName>

                        </sapt:ToolboxItemWrapper>
                        <sapt:ToolboxItemWrapper  AssemblyName="{StaticResource AssemblyName}">
                            <sapt:ToolboxItemWrapper.ToolName>
                                System.Activities.Statements.While
                            </sapt:ToolboxItemWrapper.ToolName>

                        </sapt:ToolboxItemWrapper>
                    </sapt:ToolboxCategory>
                </sapt:ToolboxControl>
            </Border>
            <Border Grid.Column="1" Name="DesignerBorder"/>
            <Border Grid.Column="2" Name="PropertyBorder"/>
        </Grid>
    </Window>
    ```

13. <span data-ttu-id="16e61-133">Para associar um designer de atividade com um tipo de atividade, você deve registrar que o designer de atividade com o armazenamento de metadados.</span><span class="sxs-lookup"><span data-stu-id="16e61-133">To associate an activity designer with an activity type, you must register that activity designer with the metadata store.</span></span> <span data-ttu-id="16e61-134">Para fazer isso, adicione o método de `RegisterMetadata` a classe de `RehostingWFDesigner` .</span><span class="sxs-lookup"><span data-stu-id="16e61-134">To do this, add the `RegisterMetadata` method to the `RehostingWFDesigner` class.</span></span> <span data-ttu-id="16e61-135">No escopo do método de `RegisterMetadata` , crie um objeto de <xref:System.Activities.Presentation.Metadata.AttributeTableBuilder> e chame o método de <xref:System.Activities.Presentation.Metadata.AttributeTableBuilder.AddCustomAttributes%2A> para adicionar os atributos.</span><span class="sxs-lookup"><span data-stu-id="16e61-135">Within the scope of the  `RegisterMetadata` method, create an <xref:System.Activities.Presentation.Metadata.AttributeTableBuilder> object and call the <xref:System.Activities.Presentation.Metadata.AttributeTableBuilder.AddCustomAttributes%2A> method to add the attributes to it.</span></span> <span data-ttu-id="16e61-136">Chame o método de <xref:System.Activities.Presentation.Metadata.MetadataStore.AddAttributeTable%2A> para adicionar <xref:System.Activities.Presentation.Metadata.AttributeTable> para o armazenamento de metadados.</span><span class="sxs-lookup"><span data-stu-id="16e61-136">Call the <xref:System.Activities.Presentation.Metadata.MetadataStore.AddAttributeTable%2A> method to add the <xref:System.Activities.Presentation.Metadata.AttributeTable> to the metadata store.</span></span> <span data-ttu-id="16e61-137">O código a seguir contém a lógica rehosting para o designer.</span><span class="sxs-lookup"><span data-stu-id="16e61-137">The following code contains the rehosting logic for the designer.</span></span> <span data-ttu-id="16e61-138">Registra os metadados, coloca `SimpleNativeActivity` na caixa de ferramentas, e cria o fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="16e61-138">It registers the metadata, puts the `SimpleNativeActivity` into the toolbox, and creates the workflow.</span></span> <span data-ttu-id="16e61-139">Coloque esse código no arquivo *RehostingWFDesigner.XAML.cs* .</span><span class="sxs-lookup"><span data-stu-id="16e61-139">Put this code into the *RehostingWFDesigner.xaml.cs* file.</span></span>

    ```csharp
    using System;
    using System.Activities.Core.Presentation;
    using System.Activities.Presentation;
    using System.Activities.Presentation.Metadata;
    using System.Activities.Presentation.Toolbox;
    using System.Activities.Statements;
    using System.ComponentModel;
    using System.Windows;

    namespace UsingWorkflowItemPresenter
    {
        // Interaction logic for RehostingWFDesigner.xaml
        public partial class RehostingWFDesigner
        {
            public RehostingWFDesigner()
            {
                InitializeComponent();
            }

            protected override void OnInitialized(EventArgs e)
            {
                base.OnInitialized(e);
                // Register metadata.
                (new DesignerMetadata()).Register();
                RegisterCustomMetadata();
                // Add custom activity to toolbox.
                Toolbox.Categories.Add(new ToolboxCategory("Custom activities"));
                Toolbox.Categories[1].Add(new ToolboxItemWrapper(typeof(SimpleNativeActivity)));

                // Create the workflow designer.
                var wd = new WorkflowDesigner();
                wd.Load(new Sequence());
                DesignerBorder.Child = wd.View;
                PropertyBorder.Child = wd.PropertyInspectorView;

            }

            void RegisterCustomMetadata()
            {
                var builder = new AttributeTableBuilder();
                builder.AddCustomAttributes(typeof(SimpleNativeActivity), new DesignerAttribute(typeof(SimpleNativeDesigner)));
                MetadataStore.AddAttributeTable(builder.CreateTable());
            }
        }
    }
    ```

14. <span data-ttu-id="16e61-140">Clique com o botão direito do mouse no diretório referências em Gerenciador de Soluções e selecione **Adicionar referência..** .</span><span class="sxs-lookup"><span data-stu-id="16e61-140">Right-click the References directory in Solution Explorer and select **Add Reference …**</span></span> <span data-ttu-id="16e61-141">para abrir a caixa de diálogo **Adicionar referência** .</span><span class="sxs-lookup"><span data-stu-id="16e61-141">to bring up the **Add Reference** dialog.</span></span>

15. <span data-ttu-id="16e61-142">Clique na guia **.net** , localize o assembly chamado **System. Activities. Core. Presentation**, selecione-o e clique em **OK**.</span><span class="sxs-lookup"><span data-stu-id="16e61-142">Click the **.NET** tab, locate the assembly named **System.Activities.Core.Presentation**, select it and click **OK**.</span></span>

16. <span data-ttu-id="16e61-143">Usando o mesmo procedimento, adicione referências para os seguintes conjuntos:</span><span class="sxs-lookup"><span data-stu-id="16e61-143">Using the same procedure, add references to the following assemblies:</span></span>

    1. <span data-ttu-id="16e61-144">System.Data.DataSetExtensions.dll</span><span class="sxs-lookup"><span data-stu-id="16e61-144">System.Data.DataSetExtensions.dll</span></span>

    2. <span data-ttu-id="16e61-145">System.Activities.Presentation.dll</span><span class="sxs-lookup"><span data-stu-id="16e61-145">System.Activities.Presentation.dll</span></span>

    3. <span data-ttu-id="16e61-146">System.ServiceModel.Activities.dll</span><span class="sxs-lookup"><span data-stu-id="16e61-146">System.ServiceModel.Activities.dll</span></span>

17. <span data-ttu-id="16e61-147">Abra o arquivo *app. XAML* e altere o valor de StartUpUri para "RehostingWFDesigner. xaml".</span><span class="sxs-lookup"><span data-stu-id="16e61-147">Open the *App.xaml* file and change the value of the StartUpUri to "RehostingWFDesigner.xaml".</span></span>

18. <span data-ttu-id="16e61-148">Clique com o botão direito do mouse no projeto UsingWorkflowItemPresenter em **Gerenciador de soluções**, selecione **Adicionar**e **novo item...**</span><span class="sxs-lookup"><span data-stu-id="16e61-148">Right-click the UsingWorkflowItemPresenter project in **Solution Explorer**, select **Add**, then **New Item…**</span></span> <span data-ttu-id="16e61-149">para abrir a caixa de diálogo **Adicionar novo item** e selecionar a categoria de **fluxo de trabalho** , selecione a seção **modelos instalados** à esquerda.</span><span class="sxs-lookup"><span data-stu-id="16e61-149">to bring up the **Add New Item** dialog and select the **Workflow** category form the **Installed Templates** section on the left.</span></span>

19. <span data-ttu-id="16e61-150">Selecione o modelo do **Designer de atividade** , `SimpleNativeDesigner`nomeie-o e clique em **Adicionar**.</span><span class="sxs-lookup"><span data-stu-id="16e61-150">Select the **Activity Designer** template, name it `SimpleNativeDesigner`, and click **Add**.</span></span>

20. <span data-ttu-id="16e61-151">Abra o arquivo *SimpleNativeDesigner. XAML* e cole o código a seguir nele.</span><span class="sxs-lookup"><span data-stu-id="16e61-151">Open the *SimpleNativeDesigner.xaml* file and paste the following code into it.</span></span> <span data-ttu-id="16e61-152">Observe <xref:System.Activities.Presentation.ActivityDesigner> usa esse código como seu elemento raiz e mostra como associar é usado para integrar <xref:System.Activities.Presentation.WorkflowItemPresenter> no designer para que um tipo filho pode ser exibido no designer composto de atividade.</span><span class="sxs-lookup"><span data-stu-id="16e61-152">Note this code uses <xref:System.Activities.Presentation.ActivityDesigner> as your root element and shows how binding is used to integrate <xref:System.Activities.Presentation.WorkflowItemPresenter> into your designer so a child type can be displayed in your composite activity designer.</span></span>

    > [!NOTE]
    > <span data-ttu-id="16e61-153">O esquema para <xref:System.Activities.Presentation.ActivityDesigner> permite a adição de apenas um elemento filho a sua definição personalizado de designer de atividade; no entanto, esse elemento pode ser `StackPanel`, `Grid`, ou outro elemento composto de interface do usuário.</span><span class="sxs-lookup"><span data-stu-id="16e61-153">The schema for <xref:System.Activities.Presentation.ActivityDesigner> allows the addition of only one child element to your custom activity designer definition; however, this element could be a `StackPanel`, `Grid`, or some other composite UI element.</span></span>

    ```xaml
    <sap:ActivityDesigner x:Class=" UsingWorkflowItemPresenter.SimpleNativeDesigner"
        xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
        xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
        xmlns:sap="clr-namespace:System.Activities.Presentation;assembly=System.Activities.Presentation"
        xmlns:sapv="clr-namespace:System.Activities.Presentation.View;assembly=System.Activities.Presentation">
        <sap:ActivityDesigner.Resources>
            <DataTemplate x:Key="Collapsed">
                <StackPanel>
                    <TextBlock>This is the collapsed view</TextBlock>
                </StackPanel>
            </DataTemplate>
            <DataTemplate x:Key="Expanded">
                <StackPanel>
                    <TextBlock>Custom Text</TextBlock>
                    <sap:WorkflowItemPresenter Item="{Binding Path=ModelItem.Body, Mode=TwoWay}"
                                            HintText="Please drop an activity here" />
                </StackPanel>
            </DataTemplate>
            <Style x:Key="ExpandOrCollapsedStyle" TargetType="{x:Type ContentPresenter}">
                <Setter Property="ContentTemplate" Value="{DynamicResource Collapsed}"/>
                <Style.Triggers>
                    <DataTrigger Binding="{Binding Path=ShowExpanded}" Value="true">
                        <Setter Property="ContentTemplate" Value="{DynamicResource Expanded}"/>
                    </DataTrigger>
                </Style.Triggers>
            </Style>
        </sap:ActivityDesigner.Resources>
        <Grid>
            <ContentPresenter Style="{DynamicResource ExpandOrCollapsedStyle}" Content="{Binding}" />
        </Grid>
    </sap:ActivityDesigner>
    ```

21. <span data-ttu-id="16e61-154">Clique com o botão direito do mouse no projeto UsingWorkflowItemPresenter em **Gerenciador de soluções**, selecione **Adicionar**e **novo item...**</span><span class="sxs-lookup"><span data-stu-id="16e61-154">Right-click the UsingWorkflowItemPresenter project in **Solution Explorer**, select **Add**, then **New Item…**</span></span> <span data-ttu-id="16e61-155">para abrir a caixa de diálogo **Adicionar novo item** e selecionar a categoria de **fluxo de trabalho** , selecione a seção **modelos instalados** à esquerda.</span><span class="sxs-lookup"><span data-stu-id="16e61-155">to bring up the **Add New Item** dialog and select the **Workflow** category form the **Installed Templates** section on the left.</span></span>

22. <span data-ttu-id="16e61-156">Selecione o modelo de **atividade de código** , `SimpleNativeActivity`nomeie-o e clique em **Adicionar**.</span><span class="sxs-lookup"><span data-stu-id="16e61-156">Select the  **Code Activity** template, name it `SimpleNativeActivity`, and click **Add**.</span></span>

23. <span data-ttu-id="16e61-157">Implemente `SimpleNativeActivity` a classe inserindo o seguinte código no arquivo *SimpleNativeActivity.cs* :</span><span class="sxs-lookup"><span data-stu-id="16e61-157">Implement the `SimpleNativeActivity` class by entering the following code into the *SimpleNativeActivity.cs* file:</span></span>

    ```csharp
    using System.Activities;

    namespace UsingWorkflowItemPresenter
    {
        public sealed class SimpleNativeActivity : NativeActivity
        {
            // this property contains an activity that will be scheduled in the execute method
            // the WorkflowItemPresenter in the designer is bound to this to enable editing
            // of the value
            public Activity Body { get; set; }

            protected override void CacheMetadata(NativeActivityMetadata metadata)
            {
               metadata.AddChild(Body);
               base.CacheMetadata(metadata);

            }

            protected override void Execute(NativeActivityContext context)
            {
                context.ScheduleActivity(Body);
            }
        }
    }
    ```

24. <span data-ttu-id="16e61-158">Selecione **Compilar solução** no menu **Compilar** .</span><span class="sxs-lookup"><span data-stu-id="16e61-158">Select **Build Solution** from the **Build** menu.</span></span>

25. <span data-ttu-id="16e61-159">Selecione **Iniciar sem depuração** no menu **depurar** para abrir a janela de design personalizado rehospedada.</span><span class="sxs-lookup"><span data-stu-id="16e61-159">Select **Start Without Debugging** from the **Debug** menu to open the rehosted custom design window.</span></span>

### <a name="to-create-a-custom-activity-designer-using-workflowitemspresenter"></a><span data-ttu-id="16e61-160">Para criar um designer personalizado de atividade que usa WorkflowItemsPresenter</span><span class="sxs-lookup"><span data-stu-id="16e61-160">To create a custom activity designer using WorkflowItemsPresenter</span></span>

1. <span data-ttu-id="16e61-161">O procedimento para o segundo designer de atividade personalizado é o paralelo do primeiro com algumas modificações, o primeiro deles é nomear o segundo aplicativo `UsingWorkflowItemsPresenter`.</span><span class="sxs-lookup"><span data-stu-id="16e61-161">The procedure for the second custom activity designer is the parallels the first with a few modifications, the first of which is to name the second application `UsingWorkflowItemsPresenter`.</span></span> <span data-ttu-id="16e61-162">Também este aplicativo não define uma nova atividade personalizado.</span><span class="sxs-lookup"><span data-stu-id="16e61-162">Also this application does not define a new custom activity.</span></span>

2. <span data-ttu-id="16e61-163">As principais diferenças estão contidas nos arquivos *CustomParallelDesigner. XAML* e *RehostingWFDesigner.XAML.cs* .</span><span class="sxs-lookup"><span data-stu-id="16e61-163">Key differences are contained in the *CustomParallelDesigner.xaml* and *RehostingWFDesigner.xaml.cs* files.</span></span> <span data-ttu-id="16e61-164">Este é o código do arquivo *CustomParallelDesigner. XAML* que define a interface do usuário:</span><span class="sxs-lookup"><span data-stu-id="16e61-164">Here is the code from the *CustomParallelDesigner.xaml* file that defines the UI:</span></span>

    ```xaml
    <sap:ActivityDesigner x:Class=" UsingWorkflowItemsPresenter.CustomParallelDesigner"
        xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
        xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
        xmlns:sap="clr-namespace:System.Activities.Presentation;assembly=System.Activities.Presentation"
        xmlns:sapv="clr-namespace:System.Activities.Presentation.View;assembly=System.Activities.Presentation">
        <sap:ActivityDesigner.Resources>
            <DataTemplate x:Key="Collapsed">
                <TextBlock>This is the Collapsed View</TextBlock>
            </DataTemplate>
            <DataTemplate x:Key="Expanded">
                <StackPanel>
                    <TextBlock HorizontalAlignment="Center">This is the</TextBlock>
                    <TextBlock HorizontalAlignment="Center">extended view</TextBlock>
                    <sap:WorkflowItemsPresenter HintText="Drop Activities Here"
                                        Items="{Binding Path=ModelItem.Branches}">
                        <sap:WorkflowItemsPresenter.SpacerTemplate>
                            <DataTemplate>
                                <Ellipse Width="10" Height="10" Fill="Black"/>
                            </DataTemplate>
                        </sap:WorkflowItemsPresenter.SpacerTemplate>
                        <sap:WorkflowItemsPresenter.ItemsPanel>
                            <ItemsPanelTemplate>
                                <StackPanel Orientation="Horizontal"/>
                            </ItemsPanelTemplate>
                        </sap:WorkflowItemsPresenter.ItemsPanel>
                    </sap:WorkflowItemsPresenter>
                </StackPanel>
            </DataTemplate>
            <Style x:Key="ExpandOrCollapsedStyle" TargetType="{x:Type ContentPresenter}">
                <Setter Property="ContentTemplate" Value="{DynamicResource Collapsed}"/>
                <Style.Triggers>
                    <DataTrigger Binding="{Binding Path=ShowExpanded}" Value="true">
                        <Setter Property="ContentTemplate" Value="{DynamicResource Expanded}"/>
                    </DataTrigger>
                </Style.Triggers>
            </Style>
        </sap:ActivityDesigner.Resources>
        <Grid>
            <ContentPresenter Style="{DynamicResource ExpandOrCollapsedStyle}" Content="{Binding}"/>
        </Grid>
    </sap:ActivityDesigner>
    ```

3. <span data-ttu-id="16e61-165">Este é o código do arquivo *RehostingWFDesigner.XAML.cs* que fornece a lógica de rehospedagem:</span><span class="sxs-lookup"><span data-stu-id="16e61-165">Here is the code from the *RehostingWFDesigner.xaml.cs* file that provides the rehosting logic:</span></span>

    ```csharp
    using System;
    using System.Activities.Core.Presentation;
    using System.Activities.Presentation;
    using System.Activities.Presentation.Metadata;
    using System.Activities.Statements;
    using System.ComponentModel;
    using System.Windows;

    namespaceUsingWorkflowItemsPresenter
    {
        public partial class RehostingWfDesigner : Window
        {
            public RehostingWfDesigner()
            {
                InitializeComponent();
            }

            protected override void OnInitialized(EventArgs e)
            {
                base.OnInitialized(e);
                // Register metadata.
                (new DesignerMetadata()).Register();
                RegisterCustomMetadata();

                // Create the workflow designer.
                var wd = new WorkflowDesigner();
                wd.Load(new Sequence());
                DesignerBorder.Child = wd.View;
                PropertyBorder.Child = wd.PropertyInspectorView;

            }

            void RegisterCustomMetadata()
            {
                var builder = new AttributeTableBuilder();
                builder.AddCustomAttributes(typeof(Parallel), new DesignerAttribute(typeof(CustomParallelDesigner)));
                MetadataStore.AddAttributeTable(builder.CreateTable());
            }
        }
    }
    ```

## <a name="see-also"></a><span data-ttu-id="16e61-166">Consulte também</span><span class="sxs-lookup"><span data-stu-id="16e61-166">See also</span></span>

- <xref:System.Activities.Presentation.ActivityDesigner>
- <xref:System.Activities.Presentation.WorkflowItemPresenter>
- <xref:System.Activities.Presentation.WorkflowItemsPresenter>
- <xref:System.Activities.Presentation.WorkflowViewElement>
- <xref:System.Activities.Presentation.Model.ModelItem>
- [<span data-ttu-id="16e61-167">Personalizando a experiência de design de fluxo de trabalho</span><span class="sxs-lookup"><span data-stu-id="16e61-167">Customizing the Workflow Design Experience</span></span>](customizing-the-workflow-design-experience.md)
