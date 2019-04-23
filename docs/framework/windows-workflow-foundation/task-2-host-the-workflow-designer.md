---
title: 'Tarefa 2: Hospedar o Designer de Fluxo de Trabalho'
ms.date: 03/30/2017
ms.assetid: 0a29b138-270d-4846-b78e-2b875e34e501
ms.openlocfilehash: 3f7964e907fe513679e60c18292f07c84128590b
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59299261"
---
# <a name="task-2-host-the-workflow-designer"></a><span data-ttu-id="253d3-102">Tarefa 2: Hospedar o Designer de Fluxo de Trabalho</span><span class="sxs-lookup"><span data-stu-id="253d3-102">Task 2: Host the Workflow Designer</span></span>
<span data-ttu-id="253d3-103">Este tópico descreve o procedimento para hospedar uma instância das [!INCLUDE[wfd1](../../../includes/wfd1-md.md)] em um aplicativo Windows Presentation Foundation (WPF).</span><span class="sxs-lookup"><span data-stu-id="253d3-103">This topic describes the procedure for hosting an instance of the [!INCLUDE[wfd1](../../../includes/wfd1-md.md)] in a Windows Presentation Foundation (WPF) application.</span></span>  
  
 <span data-ttu-id="253d3-104">O procedimento configura a **grade** controle que contém o designer cria programaticamente uma instância das <xref:System.Activities.Presentation.WorkflowDesigner> que contém um padrão <xref:System.Activities.Statements.Sequence> atividade, registra metadados de designer para fornecer suporte de Designer para atividades internas tudo e hosts a [!INCLUDE[wfd2](../../../includes/wfd2-md.md)] no [!INCLUDE[avalon2](../../../includes/avalon2-md.md)] aplicativo.</span><span class="sxs-lookup"><span data-stu-id="253d3-104">The procedure configures the **Grid** control that contains the designer, programmatically creates an instance of the <xref:System.Activities.Presentation.WorkflowDesigner> that contains a default <xref:System.Activities.Statements.Sequence> activity, registers the designer metadata to provide designer support for all built-in activities, and hosts the [!INCLUDE[wfd2](../../../includes/wfd2-md.md)] in the [!INCLUDE[avalon2](../../../includes/avalon2-md.md)] application.</span></span>  
  
### <a name="to-host-the-workflow-designer"></a><span data-ttu-id="253d3-105">Para hospedar o designer de fluxo de trabalho</span><span class="sxs-lookup"><span data-stu-id="253d3-105">To host the workflow designer</span></span>  
  
1. <span data-ttu-id="253d3-106">Abra o projeto de HostingApplication você criou no [tarefa 1: Criar um novo aplicativo do Windows Presentation Foundation](task-1-create-a-new-wpf-app.md).</span><span class="sxs-lookup"><span data-stu-id="253d3-106">Open the HostingApplication project you created in [Task 1: Create a New Windows Presentation Foundation Application](task-1-create-a-new-wpf-app.md).</span></span>  
  
2. <span data-ttu-id="253d3-107">Ajuste o tamanho da janela para facilitar usar [!INCLUDE[wfd2](../../../includes/wfd2-md.md)].</span><span class="sxs-lookup"><span data-stu-id="253d3-107">Adjust the size of the window to make it easier to use the [!INCLUDE[wfd2](../../../includes/wfd2-md.md)].</span></span> <span data-ttu-id="253d3-108">Para fazer isso, selecione **MainWindow** no designer, pressione F4 para exibir o **propriedades** janela e, na **Layout** seção lá, defina o **largura** como um valor de 600 e o **altura** para um valor de 350.</span><span class="sxs-lookup"><span data-stu-id="253d3-108">To do this, select **MainWindow** in the designer, press F4 to display the **Properties** window, and, in the **Layout** section there, set the **Width** to a value of 600 and the **Height** to a value of 350.</span></span>  
  
3. <span data-ttu-id="253d3-109">Defina o nome da grade selecionando o **grade** painel no designer (clique na caixa dentro a **MainWindow**) e configuração o **nome** propriedade na parte superior do  **Propriedades** janela a "grid1".</span><span class="sxs-lookup"><span data-stu-id="253d3-109">Set the grid name by selecting the **Grid** panel in the designer (click the box inside the **MainWindow**) and setting the **Name** property at the top of the **Properties** window to "grid1".</span></span>  
  
4. <span data-ttu-id="253d3-110">No **propriedades** janela, clique no botão de reticências (**...** ) ao lado de `ColumnDefinitions` para abrir o **Editor de coleção** caixa de diálogo.</span><span class="sxs-lookup"><span data-stu-id="253d3-110">In the **Properties** window, click the ellipsis (**…**) next to the `ColumnDefinitions` property to open the **Collection Editor** dialog box.</span></span>  
  
5. <span data-ttu-id="253d3-111">No **Collection Editor** caixa de diálogo, clique no **Add** botão três vezes para inserir três colunas no layout.</span><span class="sxs-lookup"><span data-stu-id="253d3-111">In the **Collection Editor** dialog box, click the **Add** button three times to insert three columns into the layout.</span></span> <span data-ttu-id="253d3-112">A primeira coluna conterá o **caixa de ferramentas**, a segunda coluna hospedará o [!INCLUDE[wfd2](../../../includes/wfd2-md.md)], e a terceira coluna será usada para a inspeção de propriedade.</span><span class="sxs-lookup"><span data-stu-id="253d3-112">The first column will contain the **Toolbox**, the second column will host the [!INCLUDE[wfd2](../../../includes/wfd2-md.md)], and the third column will be used for the property inspector.</span></span>  
  
6. <span data-ttu-id="253d3-113">Defina o `Width` propriedade da coluna do meio para o valor "4 \*".</span><span class="sxs-lookup"><span data-stu-id="253d3-113">Set the `Width` property of the middle column to the value "4\*".</span></span>  
  
7. <span data-ttu-id="253d3-114">Clique em **OK** para salvar as alterações.</span><span class="sxs-lookup"><span data-stu-id="253d3-114">Click **OK** to save the changes.</span></span> <span data-ttu-id="253d3-115">O XAML a seguir é adicionado ao seu arquivo de MainWindow.xaml:</span><span class="sxs-lookup"><span data-stu-id="253d3-115">The following XAML is added to your MainWindow.xaml file:</span></span>  
  
    ```xml  
    <Grid Name="grid1">  
        <Grid.ColumnDefinitions>  
            <ColumnDefinition />  
            <ColumnDefinition Width="4*" />  
            <ColumnDefinition />  
        </Grid.ColumnDefinitions>  
    </Grid>  
    ```  
  
8. <span data-ttu-id="253d3-116">Na **Gerenciador de soluções**, MainWindow. XAML com o botão direito e selecione **Exibir código**.</span><span class="sxs-lookup"><span data-stu-id="253d3-116">In **Solution Explorer**, right-click MainWindow.xaml and select **View Code**.</span></span> <span data-ttu-id="253d3-117">Modifique o código seguindo estas etapas:</span><span class="sxs-lookup"><span data-stu-id="253d3-117">Modify the code by following these steps:</span></span>  
  
    1.  <span data-ttu-id="253d3-118">Adicione as seguintes namespaces:</span><span class="sxs-lookup"><span data-stu-id="253d3-118">Add the following namespaces:</span></span>  
  
        ```csharp  
        using System.Activities;  
        using System.Activities.Core.Presentation;  
        using System.Activities.Presentation;  
        using System.Activities.Presentation.Metadata;  
        using System.Activities.Presentation.Toolbox;  
        using System.Activities.Statements;  
        using System.ComponentModel;  
        ```  
  
    2.  <span data-ttu-id="253d3-119">Para declarar um campo de membro particular para armazenar uma instância de <xref:System.Activities.Presentation.WorkflowDesigner>, adicione o seguinte código à classe de `MainWindow` .</span><span class="sxs-lookup"><span data-stu-id="253d3-119">To declare a private member field to hold an instance of the <xref:System.Activities.Presentation.WorkflowDesigner>, add the following code to the `MainWindow` class.</span></span>  
  
        ```csharp  
        public partial class MainWindow : Window  
        {  
            private WorkflowDesigner wd;  
  
            public MainWindow()  
            {  
                InitializeComponent();  
            }  
        }  
        ```  
  
    3.  <span data-ttu-id="253d3-120">Adicione o seguinte método de `AddDesigner` a classe de `MainWindow` .</span><span class="sxs-lookup"><span data-stu-id="253d3-120">Add the following `AddDesigner` method to the `MainWindow` class.</span></span> <span data-ttu-id="253d3-121">A implementação cria uma instância das <xref:System.Activities.Presentation.WorkflowDesigner>, adiciona um <xref:System.Activities.Statements.Sequence> atividade a ele e o coloca na coluna do meio de grid1 **grade**.</span><span class="sxs-lookup"><span data-stu-id="253d3-121">The implementation creates an instance of the <xref:System.Activities.Presentation.WorkflowDesigner>, adds a <xref:System.Activities.Statements.Sequence> activity to it, and places it in middle column of the grid1 **Grid**.</span></span>  
  
        ```csharp  
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
        ```  
  
    4.  <span data-ttu-id="253d3-122">Registrar os metadados de designer para adicionar suporte do designer para todas as atividades internos.</span><span class="sxs-lookup"><span data-stu-id="253d3-122">Register the designer metadata to add designer support for all the  built-in activities.</span></span> <span data-ttu-id="253d3-123">Isso permite que você soltar atividades da caixa de ferramentas para a atividade original de <xref:System.Activities.Statements.Sequence> em [!INCLUDE[wfd2](../../../includes/wfd2-md.md)].</span><span class="sxs-lookup"><span data-stu-id="253d3-123">This enables you to drop activities from the toolbox onto the original <xref:System.Activities.Statements.Sequence> activity in the [!INCLUDE[wfd2](../../../includes/wfd2-md.md)].</span></span> <span data-ttu-id="253d3-124">Para fazer isso, adicione o método de `RegisterMetadata` a classe de `MainWindow` .</span><span class="sxs-lookup"><span data-stu-id="253d3-124">To do this, add the `RegisterMetadata` method to the `MainWindow` class.</span></span>  
  
        ```csharp  
        private void RegisterMetadata()  
        {               
            DesignerMetadata dm = new DesignerMetadata();  
            dm.Register();  
        }  
        ```  
  
         <span data-ttu-id="253d3-125">Para obter mais informações sobre como registrar os designers de atividade, consulte [como: Criar um Designer personalizado de atividade](how-to-create-a-custom-activity-designer.md).</span><span class="sxs-lookup"><span data-stu-id="253d3-125">For more information about registering activity designers, see [How to: Create a Custom Activity Designer](how-to-create-a-custom-activity-designer.md).</span></span>  
  
    5.  <span data-ttu-id="253d3-126">No construtor da classe de `MainWindow` , adicione chamadas para métodos previamente declaradas para registrar os metadados para o suporte de designer e criar <xref:System.Activities.Presentation.WorkflowDesigner>.</span><span class="sxs-lookup"><span data-stu-id="253d3-126">In the `MainWindow` class constructor, add calls to the methods declared previously to register the metadata for designer support and to create the <xref:System.Activities.Presentation.WorkflowDesigner>.</span></span>  
  
        ```csharp  
        public MainWindow()  
        {  
            InitializeComponent();  
  
            // Register the metadata  
            RegisterMetadata();  
  
            // Add the WFF Designer  
            AddDesigner();  
        }  
        ```  
  
        > [!NOTE]
        >  <span data-ttu-id="253d3-127">O método de `RegisterMetadata` registra metadados de designer de atividades internos que incluem a atividade de <xref:System.Activities.Statements.Sequence> .</span><span class="sxs-lookup"><span data-stu-id="253d3-127">The `RegisterMetadata` method registers the designer metadata of built-in activities including the <xref:System.Activities.Statements.Sequence> activity.</span></span> <span data-ttu-id="253d3-128">Porque o método de `AddDesigner` usa a atividade de <xref:System.Activities.Statements.Sequence> , o método de `RegisterMetadata` deve ser chamado primeiro.</span><span class="sxs-lookup"><span data-stu-id="253d3-128">Because the `AddDesigner` method uses the <xref:System.Activities.Statements.Sequence> activity, the `RegisterMetadata` method must be called first.</span></span>  
  
9. <span data-ttu-id="253d3-129">Pressione F5 para compilar e executar a solução.</span><span class="sxs-lookup"><span data-stu-id="253d3-129">Press F5 to build and run the solution.</span></span>  
  
10. <span data-ttu-id="253d3-130">Consulte [tarefa 3: Criar caixa de ferramentas e painéis de PropertyGrid](task-3-create-the-toolbox-and-propertygrid-panes.md) para aprender a adicionar **caixa de ferramentas** e **PropertyGrid** dão suporte ao seu designer de fluxo de trabalho rehosted.</span><span class="sxs-lookup"><span data-stu-id="253d3-130">See [Task 3: Create the Toolbox and PropertyGrid Panes](task-3-create-the-toolbox-and-propertygrid-panes.md) to learn how to add **Toolbox** and **PropertyGrid** support to your rehosted workflow designer.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="253d3-131">Consulte também</span><span class="sxs-lookup"><span data-stu-id="253d3-131">See also</span></span>

- [<span data-ttu-id="253d3-132">Hospedando novamente o Designer de Fluxo de Trabalho</span><span class="sxs-lookup"><span data-stu-id="253d3-132">Rehosting the Workflow Designer</span></span>](rehosting-the-workflow-designer.md)
- [<span data-ttu-id="253d3-133">Tarefa 1: Criar um novo aplicativo do Windows Presentation Foundation</span><span class="sxs-lookup"><span data-stu-id="253d3-133">Task 1: Create a New Windows Presentation Foundation Application</span></span>](task-1-create-a-new-wpf-app.md)
- [<span data-ttu-id="253d3-134">Tarefa 3: Criar caixa de ferramentas e painéis de PropertyGrid</span><span class="sxs-lookup"><span data-stu-id="253d3-134">Task 3: Create the Toolbox and PropertyGrid Panes</span></span>](task-3-create-the-toolbox-and-propertygrid-panes.md)
