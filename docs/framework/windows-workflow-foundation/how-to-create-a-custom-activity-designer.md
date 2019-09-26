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
# <a name="how-to-create-a-custom-activity-designer"></a>Como: criar um designer personalizado de atividades

Designers personalizados de atividade são normalmente implementados de modo que as atividades passível de composição sejam associados com outras atividades cujos os designers podem ser ignorados sobre a superfície de design com eles. Essa funcionalidade requer que um designer de atividade personalizado forneça uma "área de destino" onde uma atividade arbitrária pode ser colocada e também o meio de gerenciar a coleção resultante de elementos na superfície de design. Este tópico descreve como criar um designer personalizado de atividade que contém uma área para arrastar e soltar e como criar um designer personalizado de atividade que fornece a funcionalidade de edição necessária gerenciar a coleção de elementos de designer.

Designers personalizados de atividade normalmente herdam de <xref:System.Activities.Presentation.ActivityDesigner> que é tem como padrão o tipo base do designer de atividade para todas as atividades sem um designer específico. Este tipo fornece a experiência em tempo de design de interagir com a grade de propriedade e configurar aspectos básicos como gerenciar cores e ícones.

<xref:System.Activities.Presentation.ActivityDesigner> usa dois controles auxiliar, <xref:System.Activities.Presentation.WorkflowItemPresenter> e <xref:System.Activities.Presentation.WorkflowItemsPresenter> para tornar mais fácil desenvolver designer personalizadas de atividade. Manipular a funcionalidade comum como arrastar e soltar de elementos filho, de exclusão, de seleção, e a adição desses elementos filho. O <xref:System.Activities.Presentation.WorkflowItemPresenter> permite um único elemento de interface do usuário filho dentro, fornecendo a "área de destino" <xref:System.Activities.Presentation.WorkflowItemsPresenter> , enquanto o pode fornecer suporte a vários elementos de interface do usuário, incluindo funcionalidades adicionais como ordenação, movimentação, exclusão e adição de elementos filho.

A outra parte importante da história que precisa de realce na implementação de um designer de atividade personalizado se refere à maneira como as edições visuais são ligadas usando a ligação de dados do WPF à instância armazenada na memória do que estamos editando no designer. Isso é feito pela árvore modelo de item, que também é responsável para ativar a notificação de alteração e o rastreamento de eventos como alterações nos estados.

Este tópico descreve dois procedimentos.

1. O primeiro procedimento descreve como criar um designer personalizado de atividade com <xref:System.Activities.Presentation.WorkflowItemPresenter> que fornece a área para arrastar e soltar que recebe outras atividades. Esse procedimento se baseia na amostra [designers de composição personalizados – apresentador de item de fluxo de trabalho](./samples/custom-composite-designers-workflow-item-presenter.md) .

2. O segundo procedimento descreve como criar um designer personalizado de atividade com <xref:System.Activities.Presentation.WorkflowItemsPresenter> que fornece funcionalidade necessária edição de uma coleção de elementos contidos. Esse procedimento se baseia na amostra [designers de composição personalizados – apresentador de itens de fluxo de trabalho](./samples/custom-composite-designers-workflow-items-presenter.md) .

## <a name="to-create-a-custom-activity-designer-with-a-drop-zone-using-workflowitempresenter"></a>Para criar um designer personalizado de atividade com uma área para arrastar e soltar usando WorkflowItemPresenter

1. Inicie o Visual Studio 2010.

2. No menu **arquivo** , aponte para **novo**e, em seguida, selecione **projeto...** .

     A caixa de diálogo **Novo Projeto** é aberta.

3. No painel **modelos instalados** , selecione **Windows** na categoria idioma preferencial.

4. No painel **modelos** , selecione **aplicativo WPF**.

5. Na caixa **nome** , digite `UsingWorkflowItemPresenter`.

6. Na caixa **local** , insira o diretório no qual você deseja salvar o projeto ou clique em **procurar** para navegar até ele.

7. Na caixa **solução** , aceite o valor padrão.

8. Clique em **OK**.

9. Clique com o botão direito do mouse no arquivo *mainwindows. XAML* na **Gerenciador de soluções**, selecione **excluir** e confirmar **OK** na caixa de diálogo **Microsoft Visual Studio** .

10. Clique com o botão direito do mouse no projeto UsingWorkflowItemPresenter em **Gerenciador de soluções**, selecione **Adicionar**e **novo item...** para abrir a caixa de diálogo **Adicionar novo item** e selecione a categoria **WPF** na seção **modelos instalados** à esquerda.

11. Selecione o modelo **janela (WPF)** , nomeie- `RehostingWFDesigner`o e clique em **Adicionar**.

12. Abra o arquivo *RehostingWFDesigner. XAML* e cole o código a seguir nele para definir a interface do usuário para o aplicativo:

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

13. Para associar um designer de atividade com um tipo de atividade, você deve registrar que o designer de atividade com o armazenamento de metadados. Para fazer isso, adicione o método de `RegisterMetadata` a classe de `RehostingWFDesigner` . No escopo do método de `RegisterMetadata` , crie um objeto de <xref:System.Activities.Presentation.Metadata.AttributeTableBuilder> e chame o método de <xref:System.Activities.Presentation.Metadata.AttributeTableBuilder.AddCustomAttributes%2A> para adicionar os atributos. Chame o método de <xref:System.Activities.Presentation.Metadata.MetadataStore.AddAttributeTable%2A> para adicionar <xref:System.Activities.Presentation.Metadata.AttributeTable> para o armazenamento de metadados. O código a seguir contém a lógica rehosting para o designer. Registra os metadados, coloca `SimpleNativeActivity` na caixa de ferramentas, e cria o fluxo de trabalho. Coloque esse código no arquivo *RehostingWFDesigner.XAML.cs* .

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

14. Clique com o botão direito do mouse no diretório referências em Gerenciador de Soluções e selecione **Adicionar referência..** . para abrir a caixa de diálogo **Adicionar referência** .

15. Clique na guia **.net** , localize o assembly chamado **System. Activities. Core. Presentation**, selecione-o e clique em **OK**.

16. Usando o mesmo procedimento, adicione referências para os seguintes conjuntos:

    1. System.Data.DataSetExtensions.dll

    2. System.Activities.Presentation.dll

    3. System.ServiceModel.Activities.dll

17. Abra o arquivo *app. XAML* e altere o valor de StartUpUri para "RehostingWFDesigner. xaml".

18. Clique com o botão direito do mouse no projeto UsingWorkflowItemPresenter em **Gerenciador de soluções**, selecione **Adicionar**e **novo item...** para abrir a caixa de diálogo **Adicionar novo item** e selecionar a categoria de **fluxo de trabalho** , selecione a seção **modelos instalados** à esquerda.

19. Selecione o modelo do **Designer de atividade** , `SimpleNativeDesigner`nomeie-o e clique em **Adicionar**.

20. Abra o arquivo *SimpleNativeDesigner. XAML* e cole o código a seguir nele. Observe <xref:System.Activities.Presentation.ActivityDesigner> usa esse código como seu elemento raiz e mostra como associar é usado para integrar <xref:System.Activities.Presentation.WorkflowItemPresenter> no designer para que um tipo filho pode ser exibido no designer composto de atividade.

    > [!NOTE]
    > O esquema para <xref:System.Activities.Presentation.ActivityDesigner> permite a adição de apenas um elemento filho a sua definição personalizado de designer de atividade; no entanto, esse elemento pode ser `StackPanel`, `Grid`, ou outro elemento composto de interface do usuário.

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

21. Clique com o botão direito do mouse no projeto UsingWorkflowItemPresenter em **Gerenciador de soluções**, selecione **Adicionar**e **novo item...** para abrir a caixa de diálogo **Adicionar novo item** e selecionar a categoria de **fluxo de trabalho** , selecione a seção **modelos instalados** à esquerda.

22. Selecione o modelo de **atividade de código** , `SimpleNativeActivity`nomeie-o e clique em **Adicionar**.

23. Implemente `SimpleNativeActivity` a classe inserindo o seguinte código no arquivo *SimpleNativeActivity.cs* :

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

24. Selecione **Compilar solução** no menu **Compilar** .

25. Selecione **Iniciar sem depuração** no menu **depurar** para abrir a janela de design personalizado rehospedada.

### <a name="to-create-a-custom-activity-designer-using-workflowitemspresenter"></a>Para criar um designer personalizado de atividade que usa WorkflowItemsPresenter

1. O procedimento para o segundo designer de atividade personalizado é o paralelo do primeiro com algumas modificações, o primeiro deles é nomear o segundo aplicativo `UsingWorkflowItemsPresenter`. Também este aplicativo não define uma nova atividade personalizado.

2. As principais diferenças estão contidas nos arquivos *CustomParallelDesigner. XAML* e *RehostingWFDesigner.XAML.cs* . Este é o código do arquivo *CustomParallelDesigner. XAML* que define a interface do usuário:

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

3. Este é o código do arquivo *RehostingWFDesigner.XAML.cs* que fornece a lógica de rehospedagem:

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

## <a name="see-also"></a>Consulte também

- <xref:System.Activities.Presentation.ActivityDesigner>
- <xref:System.Activities.Presentation.WorkflowItemPresenter>
- <xref:System.Activities.Presentation.WorkflowItemsPresenter>
- <xref:System.Activities.Presentation.WorkflowViewElement>
- <xref:System.Activities.Presentation.Model.ModelItem>
- [Personalizando a experiência de design de fluxo de trabalho](customizing-the-workflow-design-experience.md)
