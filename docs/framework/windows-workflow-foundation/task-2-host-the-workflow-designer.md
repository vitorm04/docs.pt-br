---
title: 'Tarefa 2: Hospedar Designer de Fluxo de Trabalho'
ms.date: 03/30/2017
ms.assetid: 0a29b138-270d-4846-b78e-2b875e34e501
ms.openlocfilehash: 8ac6b3590d146909c1cb9fd8cf9cae2352b0155b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="task-2-host-the-workflow-designer"></a>Tarefa 2: Hospedar Designer de Fluxo de Trabalho
Este tópico descreve o procedimento para hospedar uma instância do [!INCLUDE[wfd1](../../../includes/wfd1-md.md)] em um aplicativo do Windows Presentation Foundation (WPF).  
  
 O procedimento configura o **grade** controle que contém o designer cria programaticamente uma instância do <xref:System.Activities.Presentation.WorkflowDesigner> que contém um padrão <xref:System.Activities.Statements.Sequence> atividade, registra o metadados de designer para fornecer suporte de Designer para hosts e atividades internas todos os a [!INCLUDE[wfd2](../../../includes/wfd2-md.md)] na [!INCLUDE[avalon2](../../../includes/avalon2-md.md)] aplicativo.  
  
### <a name="to-host-the-workflow-designer"></a>Para hospedar o designer de fluxo de trabalho  
  
1.  Abra o HostingApplication projeto criado por você na [tarefa 1: criar um novo aplicativo do Windows Presentation Foundation](../../../docs/framework/windows-workflow-foundation/task-1-create-a-new-wpf-app.md).  
  
2.  Ajuste o tamanho da janela para facilitar usar [!INCLUDE[wfd2](../../../includes/wfd2-md.md)]. Para fazer isso, selecione **MainWindow** no designer, pressione F4 para exibir a **propriedades** janela e, no **Layout** seção existe, defina o **largura** para um valor de 600 e **altura** com um valor de 350.  
  
3.  Definir o nome de grade, selecionando o **grade** painel no designer (clique na caixa dentro a **MainWindow**) e configuração o **nome** propriedade na parte superior do  **Propriedades** janela para "grid1".  
  
4.  No **propriedades** janela, clique no botão de reticências (**...** ) ao lado de `ColumnDefinitions` propriedade para abrir o **Editor de coleção** caixa de diálogo.  
  
5.  No **Editor de coleção** caixa de diálogo, clique o **adicionar** botão três vezes para inserir três colunas no layout. A primeira coluna conterá o **caixa de ferramentas**, a segunda coluna hospedará o [!INCLUDE[wfd2](../../../includes/wfd2-md.md)], e a terceira coluna será usada para o Inspetor de propriedades.  
  
6.  Definir o `Width` propriedade da coluna do meio para o valor "4 *".  
  
7.  Clique em **OK** para salvar as alterações. O XAML a seguir é adicionado ao seu arquivo de MainWindow.xaml:  
  
    ```xml  
    <Grid Name="grid1">  
        <Grid.ColumnDefinitions>  
            <ColumnDefinition />  
            <ColumnDefinition Width="4*" />  
            <ColumnDefinition />  
        </Grid.ColumnDefinitions>  
    </Grid>  
    ```  
  
8.  Em **Solution Explorer**, MainWindow. XAML e selecione **Exibir código**. Modifique o código seguindo estas etapas:  
  
    1.  Adicione as seguintes namespaces:  
  
        ```csharp  
        using System.Activities;  
        using System.Activities.Core.Presentation;  
        using System.Activities.Presentation;  
        using System.Activities.Presentation.Metadata;  
        using System.Activities.Presentation.Toolbox;  
        using System.Activities.Statements;  
        using System.ComponentModel;  
        ```  
  
    2.  Para declarar um campo de membro particular para armazenar uma instância de <xref:System.Activities.Presentation.WorkflowDesigner>, adicione o seguinte código à classe de `MainWindow` .  
  
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
  
    3.  Adicione o seguinte método de `AddDesigner` a classe de `MainWindow` . A implementação cria uma instância do <xref:System.Activities.Presentation.WorkflowDesigner>, adiciona um <xref:System.Activities.Statements.Sequence> atividade e o coloca na coluna central do grid1 **grade**.  
  
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
  
    4.  Registrar os metadados de designer para adicionar suporte do designer para todas as atividades internos. Isso permite que você soltar atividades da caixa de ferramentas para a atividade original de <xref:System.Activities.Statements.Sequence> em [!INCLUDE[wfd2](../../../includes/wfd2-md.md)]. Para fazer isso, adicione o método de `RegisterMetadata` a classe de `MainWindow` .  
  
        ```csharp  
        private void RegisterMetadata()  
        {               
            DesignerMetadata dm = new DesignerMetadata();  
            dm.Register();  
        }  
        ```  
  
         Para obter mais informações sobre como registrar os designers de atividade, consulte [como: criar um Designer de atividade personalizada](../../../docs/framework/windows-workflow-foundation/how-to-create-a-custom-activity-designer.md).  
  
    5.  No construtor da classe de `MainWindow` , adicione chamadas para métodos previamente declaradas para registrar os metadados para o suporte de designer e criar <xref:System.Activities.Presentation.WorkflowDesigner>.  
  
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
        >  O método de `RegisterMetadata` registra metadados de designer de atividades internos que incluem a atividade de <xref:System.Activities.Statements.Sequence> . Porque o método de `AddDesigner` usa a atividade de <xref:System.Activities.Statements.Sequence> , o método de `RegisterMetadata` deve ser chamado primeiro.  
  
9. Pressione F5 para compilar e executar a solução.  
  
10. Consulte [tarefa 3: criar a caixa de ferramentas e painéis de PropertyGrid](../../../docs/framework/windows-workflow-foundation/task-3-create-the-toolbox-and-propertygrid-panes.md) para aprender a adicionar **caixa de ferramentas** e **PropertyGrid** suporte para o designer de fluxo de trabalho hospedado novamente.  
  
## <a name="see-also"></a>Consulte também  
 [Hospedando novamente o Designer de Fluxo de Trabalho](../../../docs/framework/windows-workflow-foundation/rehosting-the-workflow-designer.md)  
 [Tarefa 1: Criar um novo aplicativo do Windows Presentation Foundation](../../../docs/framework/windows-workflow-foundation/task-1-create-a-new-wpf-app.md)  
 [Tarefa 3: Criar a caixa de ferramentas e os painéis de PropertyGrid](../../../docs/framework/windows-workflow-foundation/task-3-create-the-toolbox-and-propertygrid-panes.md)
