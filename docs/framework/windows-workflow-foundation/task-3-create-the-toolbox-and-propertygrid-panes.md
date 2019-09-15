---
title: 'Tarefa 3: Criar os painéis de Caixa de ferramentas e PropertyGrid'
ms.date: 03/30/2017
ms.assetid: 72c1546a-eed5-4f0f-a616-719a163414f4
ms.openlocfilehash: 6339969c52a5c4eedfb0e89eebdc982ca3fe6686
ms.sourcegitcommit: 005980b14629dfc193ff6cdc040800bc75e0a5a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/14/2019
ms.locfileid: "70988708"
---
# <a name="task-3-create-the-toolbox-and-propertygrid-panes"></a>Tarefa 3: Criar os painéis de Caixa de ferramentas e PropertyGrid
Nesta tarefa, você criará os painéis **caixa de ferramentas** e **PropertyGrid** e os adicionará ao rehospedado [!INCLUDE[wfd1](../../../includes/wfd1-md.md)].  
  
 Para referência, o código que deve estar no arquivo MainWindow.xaml.cs depois de concluir as três tarefas na série de tópicos de [rehospedagem, a designer de fluxo de trabalho](rehosting-the-workflow-designer.md) é fornecida no final deste tópico.  
  
### <a name="to-create-the-toolbox-and-add-it-to-the-grid"></a>Para criar a caixa de ferramentas e adicioná-la à grade  
  
1. Abra o projeto HostingApplication obtido seguindo o procedimento descrito na [tarefa 2: Hospede o Designer de Fluxo de Trabalho](task-2-host-the-workflow-designer.md).  
  
2. No painel de **Gerenciador de soluções** , clique com o botão direito do mouse no arquivo MainWindow. XAML e selecione **Exibir código**.  
  
3. Adicione um `GetToolboxControl` `MainWindow` método à classe que cria um <xref:System.Activities.Presentation.Toolbox.ToolboxControl>, adiciona uma nova categoria da **caixa de ferramentas** à caixa de **ferramentas**e atribui os <xref:System.Activities.Statements.Assign> tipos <xref:System.Activities.Statements.Sequence> de atividade e a essa categoria.  
  
    ```csharp  
    private ToolboxControl GetToolboxControl()  
    {  
        // Create the ToolBoxControl.  
        ToolboxControl ctrl = new ToolboxControl();  
  
        // Create a category.  
        ToolboxCategory category = new ToolboxCategory("category1");  
  
        // Create Toolbox items.  
        ToolboxItemWrapper tool1 =   
            new ToolboxItemWrapper("System.Activities.Statements.Assign",   
            typeof(Assign).Assembly.FullName, null, "Assign");  
  
        ToolboxItemWrapper tool2 = new ToolboxItemWrapper("System.Activities.Statements.Sequence",   
            typeof(Sequence).Assembly.FullName, null, "Sequence");  
  
        // Add the Toolbox items to the category.  
        category.Add(tool1);  
        category.Add(tool2);  
  
        // Add the category to the ToolBox control.  
        ctrl.Categories.Add(category);  
        return ctrl;  
    }  
    ```  
  
4. Adicione um método `AddToolbox` particular `MainWindow` à classe que coloca a **caixa de ferramentas** na coluna esquerda da grade.  
  
    ```csharp  
    private void AddToolBox()  
    {  
        ToolboxControl tc = GetToolboxControl();  
        Grid.SetColumn(tc, 0);  
        grid1.Children.Add(tc);  
    }  
    ```  
  
5. Adicione uma chamada para o método de `AddToolBox` no construtor da classe de `MainWindow()` conforme mostrado no código a seguir.  
  
    ```csharp  
    public MainWindow()  
    {  
        InitializeComponent();  
        this.RegisterMetadata();  
        this.AddDesigner();  
  
        this.AddToolBox();  
    }  
    ```  
  
6. Pressione F5 para compilar e executar sua solução. A **caixa** de ferramentas <xref:System.Activities.Statements.Assign> que <xref:System.Activities.Statements.Sequence> contém as atividades e deve ser exibida.  
  
### <a name="to-create-the-propertygrid"></a>Para criar o PropertyGrid  
  
1. No painel de **Gerenciador de soluções** , clique com o botão direito do mouse no arquivo MainWindow. XAML e selecione **Exibir código**.  
  
2. Adicione o `AddPropertyInspector` método `MainWindow` à classe para posicionar o painel **PropertyGrid** na coluna mais à direita na grade.  
  
    ```csharp  
    private void AddPropertyInspector()  
    {  
        Grid.SetColumn(wd.PropertyInspectorView, 2);  
        grid1.Children.Add(wd.PropertyInspectorView);              
    }  
    ```  
  
3. Adicione uma chamada para o método de `AddPropertyInspector` no construtor da classe de `MainWindow()` conforme mostrado no código a seguir.  
  
    ```csharp  
    public MainWindow()  
    {  
        InitializeComponent();  
        this.RegisterMetadata();  
        this.AddDesigner();  
        this.AddToolBox();  
  
        this.AddPropertyInspector();   
    }  
    ```  
  
4. Pressione F5 para compilar e executar a solução. A **caixa de ferramentas**, a tela de design do fluxo de trabalho e os painéis de **PropertyGrid** devem ser exibidos <xref:System.Activities.Statements.Assign> e, quando <xref:System.Activities.Statements.Sequence> você arrasta uma atividade ou uma atividade para a tela de design, a grade de propriedades deve ser atualizada dependendo do atividade realçada.  
  
## <a name="example"></a>Exemplo  
 O arquivo de MainWindow.xaml.cs agora deve conter o código a seguir.  
  
```csharp  
using System;  
using System.Collections.Generic;  
using System.Linq;  
using System.Text;  
using System.Windows;  
using System.Windows.Controls;  
using System.Windows.Data;  
using System.Windows.Documents;  
using System.Windows.Input;  
using System.Windows.Media;  
using System.Windows.Media.Imaging;  
using System.Windows.Navigation;  
using System.Windows.Shapes;  
//dlls added  
using System.Activities;  
using System.Activities.Core.Presentation;  
using System.Activities.Presentation;  
using System.Activities.Presentation.Metadata;  
using System.Activities.Presentation.Toolbox;  
using System.Activities.Statements;  
using System.ComponentModel;  
  
namespace HostingApplication  
{  
    /// <summary>  
    /// Interaction logic for MainWindow.xaml  
    /// </summary>  
    public partial class MainWindow : Window  
    {  
        private WorkflowDesigner wd;  
  
        public MainWindow()  
        {  
            InitializeComponent();  
            RegisterMetadata();  
            AddDesigner();  
            this.AddToolBox();  
            this.AddPropertyInspector();  
        }  
  
        private void AddDesigner()  
        {  
            //Create an instance of WorkflowDesigner class.  
            this.wd = new WorkflowDesigner();  
  
            //Place the designer canvas in the middle column of the grid.  
            Grid.SetColumn(this.wd.View, 1);  
  
            //Load a new Sequence as default.  
            this.wd.Load(new Sequence());  
  
            //Add the designer canvas to the grid.  
            grid1.Children.Add(this.wd.View);  
        }  
  
        private void RegisterMetadata()  
        {  
            DesignerMetadata dm = new DesignerMetadata();  
            dm.Register();  
        }  
  
        private ToolboxControl GetToolboxControl()  
        {  
            // Create the ToolBoxControl.  
            ToolboxControl ctrl = new ToolboxControl();  
  
            // Create a category.  
            ToolboxCategory category = new ToolboxCategory("category1");  
  
            // Create Toolbox items.  
            ToolboxItemWrapper tool1 =  
                new ToolboxItemWrapper("System.Activities.Statements.Assign",  
                typeof(Assign).Assembly.FullName, null, "Assign");  
  
            ToolboxItemWrapper tool2 = new ToolboxItemWrapper("System.Activities.Statements.Sequence",  
                typeof(Sequence).Assembly.FullName, null, "Sequence");  
  
            // Add the Toolbox items to the category.  
            category.Add(tool1);  
            category.Add(tool2);  
  
            // Add the category to the ToolBox control.  
            ctrl.Categories.Add(category);  
            return ctrl;  
        }  
  
        private void AddToolBox()  
        {  
            ToolboxControl tc = GetToolboxControl();  
            Grid.SetColumn(tc, 0);  
            grid1.Children.Add(tc);  
        }  
  
        private void AddPropertyInspector()  
        {  
            Grid.SetColumn(wd.PropertyInspectorView, 2);  
            grid1.Children.Add(wd.PropertyInspectorView);  
        }  
  
    }  
}  
```  
  
## <a name="see-also"></a>Consulte também

- [Hospedando novamente o Designer de Fluxo de Trabalho](rehosting-the-workflow-designer.md)
- [Tarefa 1: Criar um novo aplicativo Windows Presentation Foundation](task-1-create-a-new-wpf-app.md)
- [Tarefa 2: Hospedar o Designer de Fluxo de Trabalho](task-2-host-the-workflow-designer.md)
