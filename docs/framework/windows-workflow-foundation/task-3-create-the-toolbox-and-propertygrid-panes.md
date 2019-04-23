---
title: 'Tarefa 3: Criar os painéis de Caixa de ferramentas e PropertyGrid'
ms.date: 03/30/2017
ms.assetid: 72c1546a-eed5-4f0f-a616-719a163414f4
ms.openlocfilehash: 15e5b4ea08b6bc243484b6963c1c06f448bb985b
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59305995"
---
# <a name="task-3-create-the-toolbox-and-propertygrid-panes"></a><span data-ttu-id="d1d62-102">Tarefa 3: Criar os painéis de Caixa de ferramentas e PropertyGrid</span><span class="sxs-lookup"><span data-stu-id="d1d62-102">Task 3: Create the Toolbox and PropertyGrid Panes</span></span>
<span data-ttu-id="d1d62-103">Nesta tarefa, você aprenderá a criar o **caixa de ferramentas** e **PropertyGrid** painéis e adicioná-los para o rehosted [!INCLUDE[wfd1](../../../includes/wfd1-md.md)].</span><span class="sxs-lookup"><span data-stu-id="d1d62-103">In this task, you will create the **Toolbox** and **PropertyGrid** panes and add them to the rehosted [!INCLUDE[wfd1](../../../includes/wfd1-md.md)].</span></span>  
  
 <span data-ttu-id="d1d62-104">Para referência, o código que deve estar no arquivo MainWindow.xaml.cs após concluir as três tarefas a [Rehosting o Designer de fluxo de trabalho](rehosting-the-workflow-designer.md) série de tópicos é fornecido no final deste tópico.</span><span class="sxs-lookup"><span data-stu-id="d1d62-104">For reference, the code that should be in the MainWindow.xaml.cs file after completing the three tasks in the [Rehosting the Workflow Designer](rehosting-the-workflow-designer.md) series of topics is provided at the end of this topic.</span></span>  
  
### <a name="to-create-the-toolbox-and-add-it-to-the-grid"></a><span data-ttu-id="d1d62-105">Para criar a caixa de ferramentas e adicioná-la à grade</span><span class="sxs-lookup"><span data-stu-id="d1d62-105">To create the Toolbox and add it to the grid</span></span>  
  
1. <span data-ttu-id="d1d62-106">Abra o projeto de HostingApplication você obteve seguindo o procedimento descrito em [tarefa 2: Hospedar o Designer de fluxo de trabalho](task-2-host-the-workflow-designer.md).</span><span class="sxs-lookup"><span data-stu-id="d1d62-106">Open the HostingApplication project you obtained by following the procedure described in [Task 2: Host the Workflow Designer](task-2-host-the-workflow-designer.md).</span></span>  
  
2. <span data-ttu-id="d1d62-107">No **Gerenciador de soluções** painel, clique no arquivo MainWindow. XAML e selecione **Exibir código**.</span><span class="sxs-lookup"><span data-stu-id="d1d62-107">In the **Solution Explorer** pane, right-click the MainWindow.xaml file and select **View Code**.</span></span>  
  
3. <span data-ttu-id="d1d62-108">Adicionar um `GetToolboxControl` método para o `MainWindow` classe que cria um <xref:System.Activities.Presentation.Toolbox.ToolboxControl>, adiciona um novo **caixa de ferramentas** categoria para o **caixa de ferramentas**e atribui o <xref:System.Activities.Statements.Assign> e <xref:System.Activities.Statements.Sequence> tipos de atividade para essa categoria.</span><span class="sxs-lookup"><span data-stu-id="d1d62-108">Add a `GetToolboxControl` method to the `MainWindow` class that creates a <xref:System.Activities.Presentation.Toolbox.ToolboxControl>, adds a new **Toolbox** category to the **Toolbox**, and assigns the <xref:System.Activities.Statements.Assign> and <xref:System.Activities.Statements.Sequence> activity types to that category.</span></span>  
  
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
  
4. <span data-ttu-id="d1d62-109">Adicionar uma privada `AddToolbox` método para o `MainWindow` classe coloca o **caixa de ferramentas** na coluna esquerda na grade.</span><span class="sxs-lookup"><span data-stu-id="d1d62-109">Add a private `AddToolbox` method to the `MainWindow` class that places the **Toolbox** in the left column on the grid.</span></span>  
  
    ```csharp  
    private void AddToolBox()  
    {  
        ToolboxControl tc = GetToolboxControl();  
        Grid.SetColumn(tc, 0);  
        grid1.Children.Add(tc);  
    }  
    ```  
  
5. <span data-ttu-id="d1d62-110">Adicione uma chamada para o método de `AddToolBox` no construtor da classe de `MainWindow()` conforme mostrado no código a seguir.</span><span class="sxs-lookup"><span data-stu-id="d1d62-110">Add a call to the `AddToolBox` method in the `MainWindow()` class constructor as shown in the following code.</span></span>  
  
    ```csharp  
    public MainWindow()  
    {  
        InitializeComponent();  
        this.RegisterMetadata();  
        this.AddDesigner();  
  
        this.AddToolBox();  
    }  
    ```  
  
6. <span data-ttu-id="d1d62-111">Pressione F5 para compilar e executar sua solução.</span><span class="sxs-lookup"><span data-stu-id="d1d62-111">Press F5 to build and run your solution.</span></span> <span data-ttu-id="d1d62-112">O **caixa de ferramentas** que contém o <xref:System.Activities.Statements.Assign> e <xref:System.Activities.Statements.Sequence> atividades devem ser exibidas.</span><span class="sxs-lookup"><span data-stu-id="d1d62-112">The **Toolbox** containing the <xref:System.Activities.Statements.Assign> and <xref:System.Activities.Statements.Sequence> activities should be displayed.</span></span>  
  
### <a name="to-create-the-propertygrid"></a><span data-ttu-id="d1d62-113">Para criar o PropertyGrid</span><span class="sxs-lookup"><span data-stu-id="d1d62-113">To create the PropertyGrid</span></span>  
  
1. <span data-ttu-id="d1d62-114">No **Gerenciador de soluções** painel, clique no arquivo MainWindow. XAML e selecione **Exibir código**.</span><span class="sxs-lookup"><span data-stu-id="d1d62-114">In the **Solution Explorer** pane, right-click the MainWindow.xaml file and select **View Code**.</span></span>  
  
2. <span data-ttu-id="d1d62-115">Adicione a `AddPropertyInspector` método para o `MainWindow` classe para colocar o **PropertyGrid** painel na coluna mais à direita na grade.</span><span class="sxs-lookup"><span data-stu-id="d1d62-115">Add the `AddPropertyInspector` method to the `MainWindow` class to place the **PropertyGrid** pane in the rightmost column on the grid.</span></span>  
  
    ```csharp  
    private void AddPropertyInspector()  
    {  
        Grid.SetColumn(wd.PropertyInspectorView, 2);  
        grid1.Children.Add(wd.PropertyInspectorView);              
    }  
    ```  
  
3. <span data-ttu-id="d1d62-116">Adicione uma chamada para o método de `AddPropertyInspector` no construtor da classe de `MainWindow()` conforme mostrado no código a seguir.</span><span class="sxs-lookup"><span data-stu-id="d1d62-116">Add a call to the `AddPropertyInspector` method in the `MainWindow()` class constructor as shown in the following code.</span></span>  
  
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
  
4. <span data-ttu-id="d1d62-117">Pressione F5 para compilar e executar a solução.</span><span class="sxs-lookup"><span data-stu-id="d1d62-117">Press F5 to build and run the solution.</span></span> <span data-ttu-id="d1d62-118">O **caixa de ferramentas**, tela de design de fluxo de trabalho, e **PropertyGrid** painéis devem todos ser exibidos, e quando você arrasta um <xref:System.Activities.Statements.Assign> atividade ou um <xref:System.Activities.Statements.Sequence> atividade na tela de design, o grade de propriedades deve atualizar dependendo da atividade realçado.</span><span class="sxs-lookup"><span data-stu-id="d1d62-118">The **Toolbox**, workflow design canvas, and **PropertyGrid** panes should all be displayed, and when you drag an <xref:System.Activities.Statements.Assign> activity or a <xref:System.Activities.Statements.Sequence> activity onto the design canvas, the property grid should update depending on the highlighted activity.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d1d62-119">Exemplo</span><span class="sxs-lookup"><span data-stu-id="d1d62-119">Example</span></span>  
 <span data-ttu-id="d1d62-120">O arquivo de MainWindow.xaml.cs agora deve conter o código a seguir.</span><span class="sxs-lookup"><span data-stu-id="d1d62-120">The MainWindow.xaml.cs file should now contain the following code.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="d1d62-121">Consulte também</span><span class="sxs-lookup"><span data-stu-id="d1d62-121">See also</span></span>

- [<span data-ttu-id="d1d62-122">Hospedando novamente o Designer de Fluxo de Trabalho</span><span class="sxs-lookup"><span data-stu-id="d1d62-122">Rehosting the Workflow Designer</span></span>](rehosting-the-workflow-designer.md)
- [<span data-ttu-id="d1d62-123">Tarefa 1: Criar um novo aplicativo do Windows Presentation Foundation</span><span class="sxs-lookup"><span data-stu-id="d1d62-123">Task 1: Create a New Windows Presentation Foundation Application</span></span>](task-1-create-a-new-wpf-app.md)
- [<span data-ttu-id="d1d62-124">Tarefa 2: Hospedar o Designer de fluxo de trabalho</span><span class="sxs-lookup"><span data-stu-id="d1d62-124">Task 2: Host the Workflow Designer</span></span>](task-2-host-the-workflow-designer.md)
