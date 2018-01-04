---
title: 'Tarefa 2: Hospedar Designer de Fluxo de Trabalho'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0a29b138-270d-4846-b78e-2b875e34e501
caps.latest.revision: "19"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 991f3d25a81e90ab779936c993ec7dd09a71b794
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="task-2-host-the-workflow-designer"></a><span data-ttu-id="9b3ee-102">Tarefa 2: Hospedar Designer de Fluxo de Trabalho</span><span class="sxs-lookup"><span data-stu-id="9b3ee-102">Task 2: Host the Workflow Designer</span></span>
<span data-ttu-id="9b3ee-103">Este tópico descreve o procedimento para hospedar uma instância de [!INCLUDE[wfd1](../../../includes/wfd1-md.md)] em um aplicativo de [!INCLUDE[avalon1](../../../includes/avalon1-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="9b3ee-103">This topic describes the procedure for hosting an instance of the [!INCLUDE[wfd1](../../../includes/wfd1-md.md)] in a [!INCLUDE[avalon1](../../../includes/avalon1-md.md)] application.</span></span>  
  
 <span data-ttu-id="9b3ee-104">O procedimento configura o **grade** controle que contém o designer cria programaticamente uma instância do <xref:System.Activities.Presentation.WorkflowDesigner> que contém um padrão <xref:System.Activities.Statements.Sequence> atividade, registra o metadados de designer para fornecer suporte de Designer para hosts e atividades internas todos os a [!INCLUDE[wfd2](../../../includes/wfd2-md.md)] na [!INCLUDE[avalon2](../../../includes/avalon2-md.md)] aplicativo.</span><span class="sxs-lookup"><span data-stu-id="9b3ee-104">The procedure configures the **Grid** control that contains the designer, programmatically creates an instance of the <xref:System.Activities.Presentation.WorkflowDesigner> that contains a default <xref:System.Activities.Statements.Sequence> activity, registers the designer metadata to provide designer support for all built-in activities, and hosts the [!INCLUDE[wfd2](../../../includes/wfd2-md.md)] in the [!INCLUDE[avalon2](../../../includes/avalon2-md.md)] application.</span></span>  
  
### <a name="to-host-the-workflow-designer"></a><span data-ttu-id="9b3ee-105">Para hospedar o designer de fluxo de trabalho</span><span class="sxs-lookup"><span data-stu-id="9b3ee-105">To host the workflow designer</span></span>  
  
1.  <span data-ttu-id="9b3ee-106">Abra o HostingApplication projeto criado por você na [tarefa 1: criar um novo aplicativo do Windows Presentation Foundation](../../../docs/framework/windows-workflow-foundation/task-1-create-a-new-wpf-app.md).</span><span class="sxs-lookup"><span data-stu-id="9b3ee-106">Open the HostingApplication project you created in [Task 1: Create a New Windows Presentation Foundation Application](../../../docs/framework/windows-workflow-foundation/task-1-create-a-new-wpf-app.md).</span></span>  
  
2.  <span data-ttu-id="9b3ee-107">Ajuste o tamanho da janela para facilitar usar [!INCLUDE[wfd2](../../../includes/wfd2-md.md)].</span><span class="sxs-lookup"><span data-stu-id="9b3ee-107">Adjust the size of the window to make it easier to use the [!INCLUDE[wfd2](../../../includes/wfd2-md.md)].</span></span> <span data-ttu-id="9b3ee-108">Para fazer isso, selecione **MainWindow** no designer, pressione F4 para exibir a **propriedades** janela e, no **Layout** seção existe, defina o **largura** para um valor de 600 e **altura** com um valor de 350.</span><span class="sxs-lookup"><span data-stu-id="9b3ee-108">To do this, select **MainWindow** in the designer, press F4 to display the **Properties** window, and, in the **Layout** section there, set the **Width** to a value of 600 and the **Height** to a value of 350.</span></span>  
  
3.  <span data-ttu-id="9b3ee-109">Definir o nome de grade, selecionando o **grade** painel no designer (clique na caixa dentro a **MainWindow**) e configuração o **nome** propriedade na parte superior do  **Propriedades** janela para "grid1".</span><span class="sxs-lookup"><span data-stu-id="9b3ee-109">Set the grid name by selecting the **Grid** panel in the designer (click the box inside the **MainWindow**) and setting the **Name** property at the top of the **Properties** window to "grid1".</span></span>  
  
4.  <span data-ttu-id="9b3ee-110">No **propriedades** janela, clique no botão de reticências (**...** ) ao lado de `ColumnDefinitions` propriedade para abrir o **Editor de coleção** caixa de diálogo.</span><span class="sxs-lookup"><span data-stu-id="9b3ee-110">In the **Properties** window, click the ellipsis (**…**) next to the `ColumnDefinitions` property to open the **Collection Editor** dialog box.</span></span>  
  
5.  <span data-ttu-id="9b3ee-111">No **Editor de coleção** caixa de diálogo, clique o **adicionar** botão três vezes para inserir três colunas no layout.</span><span class="sxs-lookup"><span data-stu-id="9b3ee-111">In the **Collection Editor** dialog box, click the **Add** button three times to insert three columns into the layout.</span></span> <span data-ttu-id="9b3ee-112">A primeira coluna conterá o **caixa de ferramentas**, a segunda coluna hospedará o [!INCLUDE[wfd2](../../../includes/wfd2-md.md)], e a terceira coluna será usada para o Inspetor de propriedades.</span><span class="sxs-lookup"><span data-stu-id="9b3ee-112">The first column will contain the **Toolbox**, the second column will host the [!INCLUDE[wfd2](../../../includes/wfd2-md.md)], and the third column will be used for the property inspector.</span></span>  
  
6.  <span data-ttu-id="9b3ee-113">Definir o `Width` propriedade da coluna do meio para o valor "4 *".</span><span class="sxs-lookup"><span data-stu-id="9b3ee-113">Set the `Width` property of the middle column to the value "4*".</span></span>  
  
7.  <span data-ttu-id="9b3ee-114">Clique em **OK** para salvar as alterações.</span><span class="sxs-lookup"><span data-stu-id="9b3ee-114">Click **OK** to save the changes.</span></span> <span data-ttu-id="9b3ee-115">O XAML a seguir é adicionado ao seu arquivo de MainWindow.xaml:</span><span class="sxs-lookup"><span data-stu-id="9b3ee-115">The following XAML is added to your MainWindow.xaml file:</span></span>  
  
    ```xml  
    <Grid Name="grid1">  
        <Grid.ColumnDefinitions>  
            <ColumnDefinition />  
            <ColumnDefinition Width="4*" />  
            <ColumnDefinition />  
        </Grid.ColumnDefinitions>  
    </Grid>  
    ```  
  
8.  <span data-ttu-id="9b3ee-116">Em **Solution Explorer**, MainWindow. XAML e selecione **Exibir código**.</span><span class="sxs-lookup"><span data-stu-id="9b3ee-116">In **Solution Explorer**, right-click MainWindow.xaml and select **View Code**.</span></span> <span data-ttu-id="9b3ee-117">Modifique o código seguindo estas etapas:</span><span class="sxs-lookup"><span data-stu-id="9b3ee-117">Modify the code by following these steps:</span></span>  
  
    1.  <span data-ttu-id="9b3ee-118">Adicione as seguintes namespaces:</span><span class="sxs-lookup"><span data-stu-id="9b3ee-118">Add the following namespaces:</span></span>  
  
        ```csharp  
        using System.Activities;  
        using System.Activities.Core.Presentation;  
        using System.Activities.Presentation;  
        using System.Activities.Presentation.Metadata;  
        using System.Activities.Presentation.Toolbox;  
        using System.Activities.Statements;  
        using System.ComponentModel;  
        ```  
  
    2.  <span data-ttu-id="9b3ee-119">Para declarar um campo de membro particular para armazenar uma instância de <xref:System.Activities.Presentation.WorkflowDesigner>, adicione o seguinte código à classe de `MainWindow` .</span><span class="sxs-lookup"><span data-stu-id="9b3ee-119">To declare a private member field to hold an instance of the <xref:System.Activities.Presentation.WorkflowDesigner>, add the following code to the `MainWindow` class.</span></span>  
  
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
  
    3.  <span data-ttu-id="9b3ee-120">Adicione o seguinte método de `AddDesigner` a classe de `MainWindow` .</span><span class="sxs-lookup"><span data-stu-id="9b3ee-120">Add the following `AddDesigner` method to the `MainWindow` class.</span></span> <span data-ttu-id="9b3ee-121">A implementação cria uma instância do <xref:System.Activities.Presentation.WorkflowDesigner>, adiciona um <xref:System.Activities.Statements.Sequence> atividade e o coloca na coluna central do grid1 **grade**.</span><span class="sxs-lookup"><span data-stu-id="9b3ee-121">The implementation creates an instance of the <xref:System.Activities.Presentation.WorkflowDesigner>, adds a <xref:System.Activities.Statements.Sequence> activity to it, and places it in middle column of the grid1 **Grid**.</span></span>  
  
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
  
    4.  <span data-ttu-id="9b3ee-122">Registrar os metadados de designer para adicionar suporte do designer para todas as atividades internos.</span><span class="sxs-lookup"><span data-stu-id="9b3ee-122">Register the designer metadata to add designer support for all the  built-in activities.</span></span> <span data-ttu-id="9b3ee-123">Isso permite que você soltar atividades da caixa de ferramentas para a atividade original de <xref:System.Activities.Statements.Sequence> em [!INCLUDE[wfd2](../../../includes/wfd2-md.md)].</span><span class="sxs-lookup"><span data-stu-id="9b3ee-123">This enables you to drop activities from the toolbox onto the original <xref:System.Activities.Statements.Sequence> activity in the [!INCLUDE[wfd2](../../../includes/wfd2-md.md)].</span></span> <span data-ttu-id="9b3ee-124">Para fazer isso, adicione o método de `RegisterMetadata` a classe de `MainWindow` .</span><span class="sxs-lookup"><span data-stu-id="9b3ee-124">To do this, add the `RegisterMetadata` method to the `MainWindow` class.</span></span>  
  
        ```csharp  
        private void RegisterMetadata()  
        {               
            DesignerMetadata dm = new DesignerMetadata();  
            dm.Register();  
        }  
        ```  
  
         [!INCLUDE[crabout](../../../includes/crabout-md.md)]<span data-ttu-id="9b3ee-125">registrar os designers de atividade, consulte [como: criar um Designer de atividade personalizada](../../../docs/framework/windows-workflow-foundation/how-to-create-a-custom-activity-designer.md).</span><span class="sxs-lookup"><span data-stu-id="9b3ee-125"> registering activity designers, see [How to: Create a Custom Activity Designer](../../../docs/framework/windows-workflow-foundation/how-to-create-a-custom-activity-designer.md).</span></span>  
  
    5.  <span data-ttu-id="9b3ee-126">No construtor da classe de `MainWindow` , adicione chamadas para métodos previamente declaradas para registrar os metadados para o suporte de designer e criar <xref:System.Activities.Presentation.WorkflowDesigner>.</span><span class="sxs-lookup"><span data-stu-id="9b3ee-126">In the `MainWindow` class constructor, add calls to the methods declared previously to register the metadata for designer support and to create the <xref:System.Activities.Presentation.WorkflowDesigner>.</span></span>  
  
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
        >  <span data-ttu-id="9b3ee-127">O método de `RegisterMetadata` registra metadados de designer de atividades internos que incluem a atividade de <xref:System.Activities.Statements.Sequence> .</span><span class="sxs-lookup"><span data-stu-id="9b3ee-127">The `RegisterMetadata` method registers the designer metadata of built-in activities including the <xref:System.Activities.Statements.Sequence> activity.</span></span> <span data-ttu-id="9b3ee-128">Porque o método de `AddDesigner` usa a atividade de <xref:System.Activities.Statements.Sequence> , o método de `RegisterMetadata` deve ser chamado primeiro.</span><span class="sxs-lookup"><span data-stu-id="9b3ee-128">Because the `AddDesigner` method uses the <xref:System.Activities.Statements.Sequence> activity, the `RegisterMetadata` method must be called first.</span></span>  
  
9. <span data-ttu-id="9b3ee-129">Pressione F5 para compilar e executar a solução.</span><span class="sxs-lookup"><span data-stu-id="9b3ee-129">Press F5 to build and run the solution.</span></span>  
  
10. <span data-ttu-id="9b3ee-130">Consulte [tarefa 3: criar a caixa de ferramentas e painéis de PropertyGrid](../../../docs/framework/windows-workflow-foundation/task-3-create-the-toolbox-and-propertygrid-panes.md) para aprender a adicionar **caixa de ferramentas** e **PropertyGrid** suporte para o designer de fluxo de trabalho hospedado novamente.</span><span class="sxs-lookup"><span data-stu-id="9b3ee-130">See [Task 3: Create the Toolbox and PropertyGrid Panes](../../../docs/framework/windows-workflow-foundation/task-3-create-the-toolbox-and-propertygrid-panes.md) to learn how to add **Toolbox** and **PropertyGrid** support to your rehosted workflow designer.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9b3ee-131">Consulte também</span><span class="sxs-lookup"><span data-stu-id="9b3ee-131">See Also</span></span>  
 [<span data-ttu-id="9b3ee-132">Hospedando novamente o Designer de Fluxo de Trabalho</span><span class="sxs-lookup"><span data-stu-id="9b3ee-132">Rehosting the Workflow Designer</span></span>](../../../docs/framework/windows-workflow-foundation/rehosting-the-workflow-designer.md)  
 [<span data-ttu-id="9b3ee-133">Tarefa 1: Criar um novo aplicativo do Windows Presentation Foundation</span><span class="sxs-lookup"><span data-stu-id="9b3ee-133">Task 1: Create a New Windows Presentation Foundation Application</span></span>](../../../docs/framework/windows-workflow-foundation/task-1-create-a-new-wpf-app.md)  
 [<span data-ttu-id="9b3ee-134">Tarefa 3: Criar a caixa de ferramentas e os painéis de PropertyGrid</span><span class="sxs-lookup"><span data-stu-id="9b3ee-134">Task 3: Create the Toolbox and PropertyGrid Panes</span></span>](../../../docs/framework/windows-workflow-foundation/task-3-create-the-toolbox-and-propertygrid-panes.md)
