---
title: 'Tarefa 3: Crie a caixa de ferramentas e os painéis de PropertyGrid'
ms.date: 03/30/2017
ms.assetid: 72c1546a-eed5-4f0f-a616-719a163414f4
ms.openlocfilehash: 9bfce22e9de1d6115cb88daddcd2dca355b6bae8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="task-3-create-the-toolbox-and-propertygrid-panes"></a>Tarefa 3: Crie a caixa de ferramentas e os painéis de PropertyGrid
Nesta tarefa, você criará o **caixa de ferramentas** e **PropertyGrid** painéis e adicioná-los para o rehosted [!INCLUDE[wfd1](../../../includes/wfd1-md.md)].  
  
 Para referência, o código que deve estar no arquivo de MainWindow.xaml.cs depois de concluir as três tarefas a [nova hospedagem o Designer de fluxo de trabalho](../../../docs/framework/windows-workflow-foundation/rehosting-the-workflow-designer.md) série de tópicos é fornecido no final deste tópico.  
  
### <a name="to-create-the-toolbox-and-add-it-to-the-grid"></a>Para criar a caixa de ferramentas e adicioná-la à grade  
  
1.  Abra o projeto HostingApplication obtido seguindo o procedimento descrito em [tarefa 2: hospedar Designer de fluxo de trabalho](../../../docs/framework/windows-workflow-foundation/task-2-host-the-workflow-designer.md).  
  
2.  No **Solution Explorer** painel, clique no arquivo MainWindow. XAML e selecione **Exibir código**.  
  
3.  Adicionar um `GetToolboxControl` método para o `MainWindow` classe cria um <xref:System.Activities.Presentation.Toolbox.ToolboxControl>, adiciona um novo **caixa de ferramentas** categoria para o **caixa de ferramentas**e atribui o <xref:System.Activities.Statements.Assign> e <xref:System.Activities.Statements.Sequence> tipos de atividade para essa categoria.  
  
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
  
4.  Adicionar uma particular `AddToolbox` método para o `MainWindow` classe coloca o **caixa de ferramentas** na coluna esquerda da grade.  
  
    ```csharp  
    private void AddToolBox()  
    {  
        ToolboxControl tc = GetToolboxControl();  
        Grid.SetColumn(tc, 0);  
        grid1.Children.Add(tc);  
    }  
    ```  
  
5.  Adicione uma chamada para o método de `AddToolBox` no construtor da classe de `MainWindow()` conforme mostrado no código a seguir.  
  
    ```csharp  
    public MainWindow()  
    {  
        InitializeComponent();  
        this.RegisterMetadata();  
        this.AddDesigner();  
  
        this.AddToolBox();  
    }  
    ```  
  
6.  Pressione F5 para compilar e executar sua solução. O **caixa de ferramentas** que contém o <xref:System.Activities.Statements.Assign> e <xref:System.Activities.Statements.Sequence> atividades devem ser exibidas.  
  
### <a name="to-create-the-propertygrid"></a>Para criar o PropertyGrid  
  
1.  No **Solution Explorer** painel, clique no arquivo MainWindow. XAML e selecione **Exibir código**.  
  
2.  Adicionar o `AddPropertyInspector` método para o `MainWindow` classe para colocar o **PropertyGrid** painel na coluna mais à direita na grade.  
  
    ```csharp  
    private void AddPropertyInspector()  
    {  
        Grid.SetColumn(wd.PropertyInspectorView, 2);  
        grid1.Children.Add(wd.PropertyInspectorView);              
    }  
    ```  
  
3.  Adicione uma chamada para o método de `AddPropertyInspector` no construtor da classe de `MainWindow()` conforme mostrado no código a seguir.  
  
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
  
4.  Pressione F5 para compilar e executar a solução. O **caixa de ferramentas**, tela de design de fluxo de trabalho, e **PropertyGrid** painéis devem todas ser exibidos, e quando você arrasta um <xref:System.Activities.Statements.Assign> atividade ou um <xref:System.Activities.Statements.Sequence> atividade para a tela de design, o grade de propriedades deve atualizar dependendo da atividade realçada.  
  
## <a name="example"></a>Exemplo  
 O arquivo de MainWindow.xaml.cs agora deve conter o código a seguir.  
  
```  
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
 [Hospedando novamente o Designer de Fluxo de Trabalho](../../../docs/framework/windows-workflow-foundation/rehosting-the-workflow-designer.md)  
 [Tarefa 1: Criar um novo aplicativo do Windows Presentation Foundation](../../../docs/framework/windows-workflow-foundation/task-1-create-a-new-wpf-app.md)  
 [Tarefa 2: Hospedar o Designer de Fluxo de Trabalho](../../../docs/framework/windows-workflow-foundation/task-2-host-the-workflow-designer.md)
