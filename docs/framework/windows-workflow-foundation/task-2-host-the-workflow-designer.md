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
# <a name="task-2-host-the-workflow-designer"></a>Tarefa 2: Hospedar o Designer de Fluxo de Trabalho
Este tópico descreve o procedimento para hospedar uma instância das [!INCLUDE[wfd1](../../../includes/wfd1-md.md)] em um aplicativo Windows Presentation Foundation (WPF).  
  
 O procedimento configura a **grade** controle que contém o designer cria programaticamente uma instância das <xref:System.Activities.Presentation.WorkflowDesigner> que contém um padrão <xref:System.Activities.Statements.Sequence> atividade, registra metadados de designer para fornecer suporte de Designer para atividades internas tudo e hosts a [!INCLUDE[wfd2](../../../includes/wfd2-md.md)] no [!INCLUDE[avalon2](../../../includes/avalon2-md.md)] aplicativo.  
  
### <a name="to-host-the-workflow-designer"></a>Para hospedar o designer de fluxo de trabalho  
  
1. Abra o projeto de HostingApplication você criou no [tarefa 1: Criar um novo aplicativo do Windows Presentation Foundation](task-1-create-a-new-wpf-app.md).  
  
2. Ajuste o tamanho da janela para facilitar usar [!INCLUDE[wfd2](../../../includes/wfd2-md.md)]. Para fazer isso, selecione **MainWindow** no designer, pressione F4 para exibir o **propriedades** janela e, na **Layout** seção lá, defina o **largura** como um valor de 600 e o **altura** para um valor de 350.  
  
3. Defina o nome da grade selecionando o **grade** painel no designer (clique na caixa dentro a **MainWindow**) e configuração o **nome** propriedade na parte superior do  **Propriedades** janela a "grid1".  
  
4. No **propriedades** janela, clique no botão de reticências (**...** ) ao lado de `ColumnDefinitions` para abrir o **Editor de coleção** caixa de diálogo.  
  
5. No **Collection Editor** caixa de diálogo, clique no **Add** botão três vezes para inserir três colunas no layout. A primeira coluna conterá o **caixa de ferramentas**, a segunda coluna hospedará o [!INCLUDE[wfd2](../../../includes/wfd2-md.md)], e a terceira coluna será usada para a inspeção de propriedade.  
  
6. Defina o `Width` propriedade da coluna do meio para o valor "4 *".  
  
7. Clique em **OK** para salvar as alterações. O XAML a seguir é adicionado ao seu arquivo de MainWindow.xaml:  
  
    ```xml  
    <Grid Name="grid1">  
        <Grid.ColumnDefinitions>  
            <ColumnDefinition />  
            <ColumnDefinition Width="4*" />  
            <ColumnDefinition />  
        </Grid.ColumnDefinitions>  
    </Grid>  
    ```  
  
8. Na **Gerenciador de soluções**, MainWindow. XAML com o botão direito e selecione **Exibir código**. Modifique o código seguindo estas etapas:  
  
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
  
    3.  Adicione o seguinte método de `AddDesigner` a classe de `MainWindow` . A implementação cria uma instância das <xref:System.Activities.Presentation.WorkflowDesigner>, adiciona um <xref:System.Activities.Statements.Sequence> atividade a ele e o coloca na coluna do meio de grid1 **grade**.  
  
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
  
         Para obter mais informações sobre como registrar os designers de atividade, consulte [como: Criar um Designer personalizado de atividade](how-to-create-a-custom-activity-designer.md).  
  
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
  
10. Consulte [tarefa 3: Criar caixa de ferramentas e painéis de PropertyGrid](task-3-create-the-toolbox-and-propertygrid-panes.md) para aprender a adicionar **caixa de ferramentas** e **PropertyGrid** dão suporte ao seu designer de fluxo de trabalho rehosted.  
  
## <a name="see-also"></a>Consulte também

- [Hospedando novamente o Designer de Fluxo de Trabalho](rehosting-the-workflow-designer.md)
- [Tarefa 1: Criar um novo aplicativo do Windows Presentation Foundation](task-1-create-a-new-wpf-app.md)
- [Tarefa 3: Criar caixa de ferramentas e painéis de PropertyGrid](task-3-create-the-toolbox-and-propertygrid-panes.md)
