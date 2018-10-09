---
title: 'Como: Criar um designer personalizado de atividades'
ms.date: 03/30/2017
ms.assetid: 2f3aade6-facc-44ef-9657-a407ef8b9b31
ms.openlocfilehash: 86cd3544e9117cca273b6c8dde8454672f14a36a
ms.sourcegitcommit: 8c28ab17c26bf08abbd004cc37651985c68841b8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/08/2018
ms.locfileid: "48873002"
---
# <a name="how-to-create-a-custom-activity-designer"></a>Como: Criar um designer personalizado de atividades

Designers personalizados de atividade são normalmente implementados de modo que as atividades passível de composição sejam associados com outras atividades cujos os designers podem ser ignorados sobre a superfície de design com eles. Essa funcionalidade requer que um designer personalizado de atividade fornecem uma "zona de soltar" onde uma atividade arbitrária pode ser colocada e também os meios para gerenciar a coleção resultante dos elementos na superfície de design. Este tópico descreve como criar um designer personalizado de atividade que contém uma área para arrastar e soltar e como criar um designer personalizado de atividade que fornece a funcionalidade de edição necessária gerenciar a coleção de elementos de designer.

 Designers personalizados de atividade normalmente herdam de <xref:System.Activities.Presentation.ActivityDesigner> que é tem como padrão o tipo base do designer de atividade para todas as atividades sem um designer específico. Este tipo fornece a experiência em tempo de design de interagir com a grade de propriedade e configurar aspectos básicos como gerenciar cores e ícones.

 <xref:System.Activities.Presentation.ActivityDesigner> usa dois controles auxiliar, <xref:System.Activities.Presentation.WorkflowItemPresenter> e <xref:System.Activities.Presentation.WorkflowItemsPresenter> para tornar mais fácil desenvolver designer personalizadas de atividade. Manipular a funcionalidade comum como arrastar e soltar de elementos filho, de exclusão, de seleção, e a adição desses elementos filho. O <xref:System.Activities.Presentation.WorkflowItemPresenter> permite um único filho de elemento de interface do usuário dentro, fornecendo o "soltar", ele enquanto o <xref:System.Activities.Presentation.WorkflowItemsPresenter> pode fornecer suporte a vários elementos de interface do usuário, incluindo a funcionalidade adicional como ordenar, mover, excluir e adicionar elementos filho.

 A outra parte fundamental de artigo que precisa de realce na implementação de um designer personalizado de atividade refere-se à maneira como que as edições visuais são associadas usando os dados de [!INCLUDE[avalon2](../../../includes/avalon2-md.md)] que se associam à instância armazenado na memória que nós estamos edição no designer. Isso é feito pela árvore modelo de item, que também é responsável para ativar a notificação de alteração e o rastreamento de eventos como alterações nos estados.

 Este tópico descreve dois procedimentos.

1.  O primeiro procedimento descreve como criar um designer personalizado de atividade com <xref:System.Activities.Presentation.WorkflowItemPresenter> que fornece a área para arrastar e soltar que recebe outras atividades. Este procedimento se baseia a [Designer de compostos personalizados - apresentador de Item de fluxo de trabalho](../../../docs/framework/windows-workflow-foundation/samples/custom-composite-designers-workflow-item-presenter.md) exemplo.

2.  O segundo procedimento descreve como criar um designer personalizado de atividade com <xref:System.Activities.Presentation.WorkflowItemsPresenter> que fornece funcionalidade necessária edição de uma coleção de elementos contidos. Este procedimento se baseia a [Designer de compostos personalizados - apresentador de itens de fluxo de trabalho](../../../docs/framework/windows-workflow-foundation/samples/custom-composite-designers-workflow-items-presenter.md) exemplo.

## <a name="to-create-a-custom-activity-designer-with-a-drop-zone-using-workflowitempresenter"></a>Para criar um designer personalizado de atividade com uma área para arrastar e soltar usando WorkflowItemPresenter

1.  Inicie o Visual Studio 2010.

2.  Sobre o **arquivo** , aponte para **New**e, em seguida, selecione **projeto...** .

     A caixa de diálogo **Novo Projeto** é aberta.

3.  No **modelos instalados** painel, selecione **Windows** da categoria do seu idioma preferencial.

4.  No **modelos** painel, selecione **aplicativo WPF**.

5.  No **nome** , digite `UsingWorkflowItemPresenter`.

6.  No **local** , digite o diretório no qual você deseja salvar seu projeto, ou clique em **procurar** para navegar até ele.

7.  No **solução** caixa, aceite o valor padrão.

8.  Clique em **OK**.

9. Clique no arquivo de Mainwindows na **Gerenciador de soluções**, selecione **excluir** e confirme se **Okey** no **Microsoft Visual Studio**caixa de diálogo.

10. Clique com botão direito no projeto de UsingWorkflowItemPresenter no **Gerenciador de soluções**, selecione **Add**, em seguida, **Novo Item...** Para abrir o **Adicionar Novo Item** de caixa de diálogo e selecione o **WPF** categoria do **modelos instalados** seção à esquerda.

11. Selecione o **janela (WPF)** modelo, nomeie- `RehostingWFDesigner`e clique em **Add**.

12. Abra o arquivo de RehostingWFDesigner.xaml e cole o seguinte código nele para definir uma interface de usuário para o aplicativo.

    ```xml
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

13. Para associar um designer de atividade com um tipo de atividade, você deve registrar que o designer de atividade com o armazenamento de metadados. Para fazer isso, adicione o método de `RegisterMetadata` a classe de `RehostingWFDesigner` . No escopo do método de `RegisterMetadata` , crie um objeto de <xref:System.Activities.Presentation.Metadata.AttributeTableBuilder> e chame o método de <xref:System.Activities.Presentation.Metadata.AttributeTableBuilder.AddCustomAttributes%2A> para adicionar os atributos. Chame o método de <xref:System.Activities.Presentation.Metadata.MetadataStore.AddAttributeTable%2A> para adicionar <xref:System.Activities.Presentation.Metadata.AttributeTable> para o armazenamento de metadados. O código a seguir contém a lógica rehosting para o designer. Registra os metadados, coloca `SimpleNativeActivity` na caixa de ferramentas, e cria o fluxo de trabalho. Coloque esse código no arquivo de RehostingWFDesigner.xaml.cs.

    ```
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
                // register metadata
                (new DesignerMetadata()).Register();
                RegisterCustomMetadata();
                // add custom activity to toolbox
                Toolbox.Categories.Add(new ToolboxCategory("Custom activities"));
                Toolbox.Categories[1].Add(new ToolboxItemWrapper(typeof(SimpleNativeActivity)));

                // create the workflow designer
                WorkflowDesigner wd = new WorkflowDesigner();
                wd.Load(new Sequence());
                DesignerBorder.Child = wd.View;
                PropertyBorder.Child = wd.PropertyInspectorView;

            }

            void RegisterCustomMetadata()
            {
                AttributeTableBuilder builder = new AttributeTableBuilder();
                builder.AddCustomAttributes(typeof(SimpleNativeActivity), new DesignerAttribute(typeof(SimpleNativeDesigner)));
                MetadataStore.AddAttributeTable(builder.CreateTable());
            }
        }
    }
    ```

14. Clique com botão direito no diretório de referências no Gerenciador de soluções e selecione **adicionar referência...** Para abrir o **adicionar referência** caixa de diálogo.

15. Clique o **.NET** guia, localize o assembly chamado **Activities**, selecione-o e clique em **Okey**.

16. Usando o mesmo procedimento, adicione referências para os seguintes conjuntos:

    1.  System.Data.DataSetExtensions.dll

    2.  System.Activities.Presentation.dll

    3.  System.ServiceModel.Activities.dll

17. Abra o arquivo App. XAML e altere o valor de StartUpUri para "Rehostingwfdesigner".

18. Clique com botão direito no projeto de UsingWorkflowItemPresenter no **Gerenciador de soluções**, selecione **Add**, em seguida, **Novo Item...** Para abrir o **Adicionar Novo Item** de caixa de diálogo e selecione o **fluxo de trabalho** formulário de categoria a **modelos instalados** seção à esquerda.

19. Selecione o **Designer de atividade** modelo, nomeie- `SimpleNativeDesigner`e clique em **Add**.

20. Abra o arquivo de SimpleNativeDesigner.xaml e cole o seguinte código nele. Observe <xref:System.Activities.Presentation.ActivityDesigner> usa esse código como seu elemento raiz e mostra como associar é usado para integrar <xref:System.Activities.Presentation.WorkflowItemPresenter> no designer para que um tipo filho pode ser exibido no designer composto de atividade.

    > [!NOTE]
    >  O esquema para <xref:System.Activities.Presentation.ActivityDesigner> permite a adição de apenas um elemento filho a sua definição personalizado de designer de atividade; no entanto, esse elemento pode ser `StackPanel`, `Grid`, ou outro elemento composto de interface do usuário.

    ```xml
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

21. Clique com botão direito no projeto de UsingWorkflowItemPresenter no **Gerenciador de soluções**, selecione **Add**, em seguida, **Novo Item...** Para abrir o **Adicionar Novo Item** de caixa de diálogo e selecione o **fluxo de trabalho** formulário de categoria a **modelos instalados** seção à esquerda.

22. Selecione o **atividade de código** modelo, nomeie- `SimpleNativeActivity`e clique em **Add**.

23. Implementar a classe de `SimpleNativeActivity` digitando o seguinte código no arquivo de SimpleNativeActivity.cs.

    ```
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

24. Selecione **compilar solução** da **Build** menu.

25. Selecione **Start Without Debugging** da **depurar** menu para abrir a janela de design personalizado hospedado novamente.

### <a name="to-create-a-custom-activity-designer-using-workflowitemspresenter"></a>Para criar um designer personalizado de atividade que usa WorkflowItemsPresenter

1.  O procedimento para o segundo designer de atividade personalizada é a paralelas o primeiro com algumas modificações, o primeiro deles é nomear o segundo aplicativo `UsingWorkflowItemsPresenter`. Também este aplicativo não define uma nova atividade personalizado.

2.  As principais diferenças são contidas nos arquivos de CustomParallelDesigner.xaml e de RehostingWFDesigner.xaml.cs. Aqui está o código do arquivo de CustomParallelDesigne.xaml que define interface do usuário.

    ```xml
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

3.  Aqui está o código do arquivo de RehostingWFDesigner.xaml.cs que fornece lógica rehosting.

    ```
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
                // register metadata
                (new DesignerMetadata()).Register();
                RegisterCustomMetadata();

                // create the workflow designer
                WorkflowDesigner wd = new WorkflowDesigner();
                wd.Load(new Sequence());
                DesignerBorder.Child = wd.View;
                PropertyBorder.Child = wd.PropertyInspectorView;

            }

            void RegisterCustomMetadata()
            {
                AttributeTableBuilder builder = new AttributeTableBuilder();
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
- [Personalizando a experiência de design de fluxo de trabalho](../../../docs/framework/windows-workflow-foundation/customizing-the-workflow-design-experience.md)