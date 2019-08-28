---
title: 'Tarefa 2: Hospedar o Designer de Fluxo de Trabalho'
ms.date: 03/30/2017
ms.assetid: 0a29b138-270d-4846-b78e-2b875e34e501
ms.openlocfilehash: 92c5fa347cc7a2c0088ab8f4fbdfddf25ffb83c1
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/27/2019
ms.locfileid: "70037866"
---
# <a name="task-2-host-the-workflow-designer"></a>Tarefa 2: Hospedar o Designer de Fluxo de Trabalho

Este tópico descreve o procedimento para hospedar uma instância do [!INCLUDE[wfd1](../../../includes/wfd1-md.md)] em um aplicativo Windows Presentation Foundation (WPF).

O procedimento configura o controle de **grade** que contém o designer, cria programaticamente uma instância do <xref:System.Activities.Presentation.WorkflowDesigner> que contém uma atividade <xref:System.Activities.Statements.Sequence> padrão, registra os metadados do designer para fornecer suporte de designer para todos as atividades internas e hospeda o [!INCLUDE[wfd2](../../../includes/wfd2-md.md)] no aplicativo do WPF.

### <a name="to-host-the-workflow-designer"></a>Para hospedar o designer de fluxo de trabalho

1. Abra o projeto HostingApplication que você criou [na tarefa 1: Crie um novo aplicativo](task-1-create-a-new-wpf-app.md)Windows Presentation Foundation.

2. Ajuste o tamanho da janela para facilitar usar [!INCLUDE[wfd2](../../../includes/wfd2-md.md)]. Para fazer isso, selecione **MainWindow** no designer, pressione F4 para exibir a janela **Propriedades** e, na seção **layout** , defina a **largura** como um valor de 600 e a **altura** como um valor de 350.

3. Defina o nome da grade selecionando o painel de **grade** no designer (clique na caixa dentro de **MainWindow**) e definindo a propriedade **Name** na parte superior da janela **Properties** como "grid1".

4. Na janela **Propriedades** , clique nas reticências ( **...** ) ao lado da `ColumnDefinitions` propriedade para abrir a caixa de diálogo **Editor de coleção** .

5. Na caixa de diálogo **Editor de coleção** , clique no botão **Adicionar** três vezes para inserir três colunas no layout. A primeira coluna conterá a **caixa de ferramentas**, a segunda coluna hospedará o [!INCLUDE[wfd2](../../../includes/wfd2-md.md)]e a terceira coluna será usada para o Inspetor de propriedades.

6. Defina a `Width` propriedade da coluna intermediária com o valor "4 *".

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

8. Em **Gerenciador de soluções**, clique com o botão direito do mouse em MainWindow. XAML e selecione **Exibir código**. Modifique o código seguindo estas etapas:

    1. Adicione as seguintes namespaces:

        ```csharp
        using System.Activities;
        using System.Activities.Core.Presentation;
        using System.Activities.Presentation;
        using System.Activities.Presentation.Metadata;
        using System.Activities.Presentation.Toolbox;
        using System.Activities.Statements;
        using System.ComponentModel;
        ```

    2. Para declarar um campo de membro particular para armazenar uma instância de <xref:System.Activities.Presentation.WorkflowDesigner>, adicione o seguinte código à classe de `MainWindow` .

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

    3. Adicione o seguinte método de `AddDesigner` a classe de `MainWindow` . A implementação cria uma instância do <xref:System.Activities.Presentation.WorkflowDesigner>, adiciona uma <xref:System.Activities.Statements.Sequence> atividade a ela e a coloca na coluna intermediária da **grade**grid1.

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

    4. Registrar os metadados de designer para adicionar suporte do designer para todas as atividades internos. Isso permite que você soltar atividades da caixa de ferramentas para a atividade original de <xref:System.Activities.Statements.Sequence> em [!INCLUDE[wfd2](../../../includes/wfd2-md.md)]. Para fazer isso, adicione o método de `RegisterMetadata` a classe de `MainWindow` .

        ```csharp
        private void RegisterMetadata()
        {
            DesignerMetadata dm = new DesignerMetadata();
            dm.Register();
        }
        ```

        Para obter mais informações sobre como registrar os designers de [atividade, consulte Como: Crie um designer](how-to-create-a-custom-activity-designer.md)de atividade personalizado.

    5. No construtor da classe de `MainWindow` , adicione chamadas para métodos previamente declaradas para registrar os metadados para o suporte de designer e criar <xref:System.Activities.Presentation.WorkflowDesigner>.

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
        > O método de `RegisterMetadata` registra metadados de designer de atividades internos que incluem a atividade de <xref:System.Activities.Statements.Sequence> . Porque o método de `AddDesigner` usa a atividade de <xref:System.Activities.Statements.Sequence> , o método de `RegisterMetadata` deve ser chamado primeiro.

9. Pressione F5 para compilar e executar a solução.

10. Consulte [a tarefa 3: Crie os painéis](task-3-create-the-toolbox-and-propertygrid-panes.md) caixa de ferramentas e PropertyGrid para saber como adicionar suporte a **caixa de ferramentas** e **PropertyGrid** ao designer de fluxo de trabalho rehospedado.

## <a name="see-also"></a>Consulte também

- [Hospedando novamente o Designer de Fluxo de Trabalho](rehosting-the-workflow-designer.md)
- [Tarefa 1: Criar um novo aplicativo Windows Presentation Foundation](task-1-create-a-new-wpf-app.md)
- [Tarefa 3: Criar os painéis caixa de ferramentas e PropertyGrid](task-3-create-the-toolbox-and-propertygrid-panes.md)
