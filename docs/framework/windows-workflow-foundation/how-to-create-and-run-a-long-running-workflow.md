---
title: 'Como: Criar e executar uma longa em execução de fluxo de trabalho'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: c0043c89-2192-43c9-986d-3ecec4dd8c9c
ms.openlocfilehash: cbb00797944f63ab695c7af87ac02b49e0ad15fa
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/09/2019
ms.locfileid: "57721158"
---
# <a name="how-to-create-and-run-a-long-running-workflow"></a>Como: Criar e executar uma longa em execução de fluxo de trabalho
Um dos recursos centrais do Windows Workflow Foundation (WF) é a capacidade de persistir e descarregar fluxos de trabalho ociosos para um banco de dados do tempo de execução. As etapas em [como: Executar um fluxo de trabalho](how-to-run-a-workflow.md) demonstraram os fundamentos de hospedagem de fluxo de trabalho usando um aplicativo de console. Foram mostrados exemplos de iniciação de fluxos de trabalho, manipuladores do ciclo de vida de fluxo de trabalho e retomada de indicadores. Para demonstrar efetivamente a persistência do fluxo de trabalho, um host de fluxo de trabalho mais complexo é necessário que dá suporte a início e retomada de várias instâncias de fluxo de trabalho. Esta etapa no tutorial demonstra como criar um aplicativo de host do Windows Form que dê suporte ao início e à retomada de várias instâncias de fluxo de trabalho, persistência de fluxo de trabalho e fornece uma base para os recursos avançados como o rastreamento e o controle de versão que são demonstrados em etapas tutoriais subsequentes.  
  
> [!NOTE]
>  Nesta etapa do tutorial e as etapas subsequentes usam todos os três tipos de fluxo de trabalho de [como: Criar um fluxo de trabalho](how-to-create-a-workflow.md). Se você não tiver concluído todos os três tipos, você pode baixar uma versão completa das etapas da [Windows Workflow Foundation (WF45) - Tutorial de Introdução](https://go.microsoft.com/fwlink/?LinkID=248976).  
  
> [!NOTE]
>  Para baixar uma versão completa ou exibir uma vídeo passo a passo do tutorial, consulte [Windows Workflow Foundation (WF45) - Tutorial de Introdução](https://go.microsoft.com/fwlink/?LinkID=248976).  
  
## <a name="in-this-topic"></a>Neste tópico  
  
-   [Para criar o banco de dados de persistência](how-to-create-and-run-a-long-running-workflow.md#BKMK_CreatePersistenceDatabase)  
  
-   [Para adicionar a referência aos assemblies do DurableInstancing](how-to-create-and-run-a-long-running-workflow.md#BKMK_AddReference)  
  
-   [Para criar o formulário de host de fluxo de trabalho](how-to-create-and-run-a-long-running-workflow.md#BKMK_CreateForm)  
  
-   [Para adicionar as propriedades e métodos auxiliares do formulário](how-to-create-and-run-a-long-running-workflow.md#BKMK_AddHelperMethods)  
  
-   [Para configurar o armazenamento de instância, manipuladores de ciclo de vida de fluxo de trabalho e extensões](how-to-create-and-run-a-long-running-workflow.md#BKMK_ConfigureWorkflowApplication)  
  
-   [Para habilitar o início e retomada de vários tipos de fluxo de trabalho](how-to-create-and-run-a-long-running-workflow.md#BKMK_WorkflowVersionMap)  
  
-   [Para iniciar um novo fluxo de trabalho](how-to-create-and-run-a-long-running-workflow.md#BKMK_StartWorkflow)  
  
-   [Para retomar um fluxo de trabalho](how-to-create-and-run-a-long-running-workflow.md#BKMK_ResumeWorkflow)  
  
-   [Para encerrar um fluxo de trabalho](how-to-create-and-run-a-long-running-workflow.md#BKMK_TerminateWorkflow)  
  
-   [Para compilar e executar o aplicativo](how-to-create-and-run-a-long-running-workflow.md#BKMK_BuildAndRun)  
  
### <a name="BKMK_CreatePersistenceDatabase"></a> Para criar o banco de dados de persistência  
  
1.  Abra o SQL Server Management Studio e conecte-se ao servidor local, por exemplo **. \SQLEXPRESS**. Clique com botão direito do **bancos de dados** nó no servidor local e selecione **novo banco de dados**. Nomeie o novo banco de dados **WF45GettingStartedTutorial**, aceite todos os outros valores e selecione **Okey**.  
  
    > [!NOTE]
    >  Certifique-se de que você tenha **criar banco de dados** permissão no servidor local antes de criar o banco de dados.  
  
2.  Escolher **aberto**, **arquivo** do **arquivo** menu. Navegue até a pasta a seguir: `C:\Windows\Microsoft.NET\Framework\v4.0.30319\sql\en`  
  
     Selecione dois arquivos a seguir e clique em **aberto**.  
  
    -   SqlWorkflowInstanceStoreLogic.sql  
  
    -   SqlWorkflowInstanceStoreSchema.sql  
  
3.  Escolher **Sqlworkflowinstancestoreschema** da **janela** menu. Certifique-se de que **WF45GettingStartedTutorial** está selecionado na **bancos de dados disponíveis** lista suspensa e escolha **Execute** do **consulta**menu.  
  
4.  Escolher **Sqlworkflowinstancestorelogic** da **janela** menu. Certifique-se de que **WF45GettingStartedTutorial** está selecionado na **bancos de dados disponíveis** lista suspensa e escolha **Execute** do **consulta**menu.  
  
    > [!WARNING]
    >  É importante executar as duas etapas anteriores na ordem correta. Se as consultas forem executadas fora de ordem, ocorrerão erros e o banco de dados de persistência não estará configurado corretamente.  
  
### <a name="BKMK_AddReference"></a> Para adicionar a referência aos assemblies do DurableInstancing  
  
1.  Clique com botão direito **NumberGuessWorkflowHost** na **Gerenciador de soluções** e selecione **Add Reference**.  
  
2.  Selecione **Assemblies** da **adicionar referência** lista e digite `DurableInstancing` no **pesquisar Assemblies** caixa. Isso filtra os assemblies e facilita a seleção das referências desejadas.  
  
3.  Marque a caixa de seleção ao lado **durableinstancing** e **System.Runtime.DurableInstancing** do **resultados da pesquisa** lista e, em seguida, clique em **Okey**.  
  
### <a name="BKMK_CreateForm"></a> Para criar o formulário de host de fluxo de trabalho  
  
> [!NOTE]
>  As etapas neste procedimento descrevem como adicionar e configurar manualmente o formulário. Se for desejar, você poderá baixar os arquivos da solução para o tutorial e adicionar o formulário concluído ao projeto. Para baixar os arquivos do tutorial, consulte [Windows Workflow Foundation (WF45) - Tutorial de Introdução](https://go.microsoft.com/fwlink/?LinkID=248976). Depois que os arquivos são baixados, clique com botão direito **NumberGuessWorkflowHost** e escolha **adicionar referência**. Adicione uma referência ao **Forms** e **System. Drawing**. Essas referências são adicionadas automaticamente se você adicionar um novo formulário do **Add**, **Novo Item** menu, mas devem ser adicionadas manualmente ao importar um formulário. Depois que as referências são adicionadas, clique com botão direito **NumberGuessWorkflowHost** na **Gerenciador de soluções** e escolha **Add**, **Item existente**. Navegue até a `Form` pasta nos arquivos de projeto, selecionadas **WorkflowHostForm.cs** (ou **Workflowhostform**) e clique em **Add**. Se você optar por importar o formulário e, em seguida, você poderá pular para a próxima seção, [para adicionar as propriedades e métodos auxiliares do formulário](how-to-create-and-run-a-long-running-workflow.md#BKMK_AddHelperMethods).  
  
1.  Clique com botão direito **NumberGuessWorkflowHost** na **Gerenciador de soluções** e escolha **Add**, **Novo Item**.  
  
2.  No **instalados** modelos, escolha **formulário do Windows**, tipo `WorkflowHostForm` no **nome** caixa e, em seguida, clique em **adicionar**.  
  
3.  Configure as propriedades a seguir no formulário.  
  
    |Propriedade|Valor|  
    |--------------|-----------|  
    |FormBorderStyle|FixedSingle|  
    |MaximizeBox|False|  
    |Tamanho|400, 420|  
  
4.  Adicione os seguintes controles ao formulário na ordem especificada e configure as propriedades como direcionadas.  
  
    |Controle|Propriedade: Valor|  
    |-------------|---------------------|  
    |**Button**|Nome: NewGame<br /><br /> Local: 13, 13<br /><br /> Tamanho: 75, 23<br /><br /> Texto: New Game|  
    |**Rótulo**|Local: 94, 18<br /><br /> Texto: Dê o palpite de um número de 1 a|  
    |**ComboBox**|Nome: NumberRange<br /><br /> DropDownStyle: DropDownList<br /><br /> Itens: 10, 100, 1000<br /><br /> Local: 228, 12<br /><br /> Tamanho: 143, 21|  
    |**Rótulo**|Local: 13, 43<br /><br /> Texto: Tipo de fluxo de trabalho|  
    |**ComboBox**|Nome: WorkflowType<br /><br /> DropDownStyle: DropDownList<br /><br /> Itens: StateMachineNumberGuessWorkflow, FlowchartNumberGuessWorkflow, SequentialNumberGuessWorkflow<br /><br /> Local: 94, 40<br /><br /> Tamanho: 277, 21|  
    |**Rótulo**|Nome: WorkflowVersion<br /><br /> Local: 13, 362<br /><br /> Texto: Versão do fluxo de trabalho|  
    |**GroupBox**|Local: 13, 67<br /><br /> Tamanho: 358, 287<br /><br /> Texto: Jogo|  
  
    > [!NOTE]
    >  Ao adicionar os seguintes controles, coloque-os na caixa de grupo.  
  
    |Controle|Propriedade: Valor|  
    |-------------|---------------------|  
    |**Rótulo**|Local: 7, 20<br /><br /> Texto: ID de Instância do Fluxo de Trabalho|  
    |**ComboBox**|Nome: InstanceId<br /><br /> DropDownStyle: DropDownList<br /><br /> Local: 121, 17<br /><br /> Tamanho: 227, 21|  
    |**Rótulo**|Local: 7, 47<br /><br /> Texto: Palpite|  
    |**TextBox**|Nome: Palpite<br /><br /> Local: 50, 44<br /><br /> Tamanho: 65, 20|  
    |**Button**|Nome: EnterGuess<br /><br /> Local: 121, 42<br /><br /> Tamanho: 75, 23<br /><br /> Texto: Enter Guess|  
    |**Button**|Nome: QuitGame<br /><br /> Local: 274, 42<br /><br /> Tamanho: 75, 23<br /><br /> Texto: Encerrar|  
    |**TextBox**|Nome: WorkflowStatus<br /><br /> Local: 10, 73<br /><br /> Várias linhas: True<br /><br /> ReadOnly: True<br /><br /> ScrollBars: Vertical<br /><br /> Tamanho: 338, 208|  
  
5.  Defina as **AcceptButton** propriedades do formulário para **EnterGuess**.  
  
 O exemplo a seguir ilustra o formato concluído.  
  
 ![WF45 Introdução ao formulário de Host de fluxo de trabalho Tutorial](./media/wf45gettingstartedtutorialworkflowhostform.png "WF45GettingStartedTutorialWorkflowHostForm")  
  
### <a name="BKMK_AddHelperMethods"></a> Para adicionar as propriedades e métodos auxiliares do formulário  
 As etapas nesta seção adicionam propriedades e métodos auxiliares para a classe de formulário que configura a interface de usuário do formulário para dar suporte à execução e à retomada de fluxos de trabalho de palpite de número.  
  
1.  Clique com botão direito **WorkflowHostForm** na **Gerenciador de soluções** e escolha **Exibir código**.  
  
2.  Adicione as seguintes instruções `using` (ou `Imports`) na parte superior do arquivo com as outras instruções `using` (ou `Imports`).  
  
    ```vb  
    Imports System.Windows.Forms  
    Imports System.Activities.DurableInstancing  
    Imports System.Activities  
    Imports System.Data.SqlClient  
    Imports System.IO  
    ```  
  
    ```csharp  
    using System.Windows.Forms;  
    using System.Activities.DurableInstancing;  
    using System.Activities;  
    using System.Data.SqlClient;  
    using System.IO;  
    ```  
  
3.  Adicione as seguintes declarações de membro para o **WorkflowHostForm** classe.  
  
    ```vb  
    Const connectionString = "Server=.\SQLEXPRESS;Initial Catalog=WF45GettingStartedTutorial;Integrated Security=SSPI"  
    Dim store As SqlWorkflowInstanceStore  
    Dim WorkflowStarting As Boolean  
    ```  
  
    ```csharp  
    const string connectionString = "Server=.\\SQLEXPRESS;Initial Catalog=WF45GettingStartedTutorial;Integrated Security=SSPI";  
    SqlWorkflowInstanceStore store;  
    bool WorkflowStarting;  
    ```  
  
    > [!NOTE]
    >  Se sua cadeia de conexão for diferente, atualize `connectionString` para se referir a seu banco de dados.  
  
4.  Adicione uma propriedade `WorkflowInstanceId` à classe `WorkflowFormHost`.  
  
    ```vb  
    Public ReadOnly Property WorkflowInstanceId() As Guid  
        Get  
            If InstanceId.SelectedIndex = -1 Then  
                Return Guid.Empty  
            Else  
                Return New Guid(InstanceId.SelectedItem.ToString())  
            End If  
        End Get  
    End Property  
    ```  
  
    ```csharp  
    public Guid WorkflowInstanceId  
    {  
        get  
        {  
            return InstanceId.SelectedIndex == -1 ? Guid.Empty : (Guid)InstanceId.SelectedItem;  
        }  
    }  
    ```  
  
     O `InstanceId` caixa de combinação exibe uma lista de ids de instância de fluxo de trabalho persistida e o `WorkflowInstanceId` propriedade retorna o fluxo de trabalho selecionado no momento.  
  
5.  Adicione um manipulador para o evento `Load` do formulário. Para adicionar o manipulador, alterne para **modo de exibição de Design** para o formulário, clique no **eventos** ícone na parte superior dos **propriedades** janela e clique duas vezes em **carga**.  
  
    ```vb  
    Private Sub WorkflowHostForm_Load(sender As Object, e As EventArgs) Handles Me.Load  
  
    End Sub  
    ```  
  
    ```csharp  
    private void WorkflowHostForm_Load(object sender, EventArgs e)  
    {  
  
    }  
    ```  
  
6.  Adicione o código a seguir ao `WorkflowHostForm_Load`.  
  
    ```vb  
    'Initialize the store and configure it so that it can be used for  
    'multiple WorkflowApplication instances.  
    store = New SqlWorkflowInstanceStore(connectionString)  
    WorkflowApplication.CreateDefaultInstanceOwner(store, Nothing, WorkflowIdentityFilter.Any)  
  
    'Set default ComboBox selections.  
    NumberRange.SelectedIndex = 0  
    WorkflowType.SelectedIndex = 0  
  
    ListPersistedWorkflows()  
    ```  
  
    ```csharp  
    // Initialize the store and configure it so that it can be used for  
    // multiple WorkflowApplication instances.  
    store = new SqlWorkflowInstanceStore(connectionString);  
    WorkflowApplication.CreateDefaultInstanceOwner(store, null, WorkflowIdentityFilter.Any);  
  
    // Set default ComboBox selections.  
    NumberRange.SelectedIndex = 0;  
    WorkflowType.SelectedIndex = 0;  
  
    ListPersistedWorkflows();  
    ```  
  
     Quando o formulário carrega, o `SqlWorkflowInstanceStore` é configurado, as caixas de combinação de intervalo e tipo de fluxo de trabalho são definidas com valores padrão, as instâncias de fluxo de trabalho persistidas são adicionadas à caixa de combinação `InstanceId`.  
  
7.  Adicione um manipulador `SelectedIndexChanged` para `InstanceId`. Para adicionar o manipulador, alterne para **modo de exibição de Design** para o formulário, selecione o `InstanceId` caixa de combinação, clique no **eventos** ícone na parte superior do **propriedades** janela, e Clique duas vezes em **SelectedIndexChanged**.  
  
    ```vb  
    Private Sub InstanceId_SelectedIndexChanged(sender As Object, e As EventArgs) Handles InstanceId.SelectedIndexChanged  
  
    End Sub  
    ```  
  
    ```csharp  
    private void InstanceId_SelectedIndexChanged(object sender, EventArgs e)  
    {  
  
    }  
    ```  
  
8.  Adicione o código a seguir ao `InstanceId_SelectedIndexChanged`. Sempre que o usuário seleciona um fluxo de trabalho usando a caixa de combinação, esse manipulador atualiza a janela de status.  
  
    ```vb  
    If InstanceId.SelectedIndex = -1 Then  
        Return  
    End If  
  
    'Clear the status window.  
    WorkflowStatus.Clear()  
  
    'Get the workflow version and display it.  
    'If the workflow is just starting then this info will not  
    'be available in the persistence store so do not try and retrieve it.  
    If Not WorkflowStarting Then  
        Dim instance As WorkflowApplicationInstance = _  
            WorkflowApplication.GetInstance(WorkflowInstanceId, store)  
  
        WorkflowVersion.Text = _  
            WorkflowVersionMap.GetIdentityDescription(instance.DefinitionIdentity)  
  
        'Unload the instance.  
        instance.Abandon()  
    End If  
    ```  
  
    ```csharp  
    if (InstanceId.SelectedIndex == -1)  
    {  
        return;  
    }  
  
    // Clear the status window.  
    WorkflowStatus.Clear();  
  
    // Get the workflow version and display it.  
    // If the workflow is just starting then this info will not  
    // be available in the persistence store so do not try and retrieve it.  
    if (!WorkflowStarting)  
    {  
        WorkflowApplicationInstance instance =  
            WorkflowApplication.GetInstance(this.WorkflowInstanceId, store);  
  
        WorkflowVersion.Text =  
            WorkflowVersionMap.GetIdentityDescription(instance.DefinitionIdentity);  
  
        // Unload the instance.  
        instance.Abandon();  
    }  
    ```  
  
9. Adicione o seguinte método `ListPersistedWorkflows` à classe do formulário.  
  
    ```vb  
    Private Sub ListPersistedWorkflows()  
        Using localCon As New SqlConnection(connectionString)  
            Dim localCmd As String = _  
                "Select [InstanceId] from [System.Activities.DurableInstancing].[Instances] Order By [CreationTime]"  
  
            Dim cmd As SqlCommand = localCon.CreateCommand()  
            cmd.CommandText = localCmd  
            localCon.Open()  
            Using reader As SqlDataReader = cmd.ExecuteReader(CommandBehavior.CloseConnection)  
  
                While (reader.Read())  
                    'Get the InstanceId of the persisted Workflow.  
                    Dim id As Guid = Guid.Parse(reader(0).ToString())  
                    InstanceId.Items.Add(id)  
                End While  
            End Using  
        End Using  
    End Sub  
    ```  
  
    ```csharp  
    using (SqlConnection localCon = new SqlConnection(connectionString))  
    {  
        string localCmd =  
            "Select [InstanceId] from [System.Activities.DurableInstancing].[Instances] Order By [CreationTime]";  
  
        SqlCommand cmd = localCon.CreateCommand();  
        cmd.CommandText = localCmd;  
        localCon.Open();  
        using (SqlDataReader reader = cmd.ExecuteReader(CommandBehavior.CloseConnection))  
        {  
            while (reader.Read())  
            {  
                // Get the InstanceId of the persisted Workflow  
                Guid id = Guid.Parse(reader[0].ToString());  
                InstanceId.Items.Add(id);  
            }  
        }  
    }  
    ```  
  
     `ListPersistedWorkflows` consulta o repositório de instâncias em busca de instâncias de fluxo de trabalho persistidas, e adiciona as ids de instância à caixa de combinação `cboInstanceId`.  
  
10. Adicione o seguinte método `UpdateStatus` e o delegado correspondente à classe de formulário. Este método atualiza a janela de status no formulário com o status do fluxo de trabalho em execução no momento.  
  
    ```vb  
    Private Delegate Sub UpdateStatusDelegate(msg As String)  
    Public Sub UpdateStatus(msg As String)  
        'We may be on a different thread so we need to  
        'make this call using BeginInvoke.  
        If InvokeRequired Then  
            BeginInvoke(New UpdateStatusDelegate(AddressOf UpdateStatus), msg)  
        Else  
            If Not msg.EndsWith(vbCrLf) Then  
                msg = msg & vbCrLf  
            End If  
  
            WorkflowStatus.AppendText(msg)  
  
            'Ensure that the newly added status is visible.  
            WorkflowStatus.SelectionStart = WorkflowStatus.Text.Length  
            WorkflowStatus.ScrollToCaret()  
        End If  
    End Sub  
    ```  
  
    ```csharp  
    private delegate void UpdateStatusDelegate(string msg);  
    public void UpdateStatus(string msg)  
    {  
        // We may be on a different thread so we need to  
        // make this call using BeginInvoke.  
        if (InvokeRequired)  
        {  
            BeginInvoke(new UpdateStatusDelegate(UpdateStatus), msg);  
        }  
        else  
        {  
            if (!msg.EndsWith("\r\n"))  
            {  
                msg += "\r\n";  
            }  
            WorkflowStatus.AppendText(msg);  
  
            WorkflowStatus.SelectionStart = WorkflowStatus.Text.Length;  
            WorkflowStatus.ScrollToCaret();  
        }  
    }  
    ```  
  
11. Adicione o seguinte método `GameOver` e o delegado correspondente à classe de formulário. Quando um fluxo de trabalho for concluído, esse método atualiza o formulário da interface do usuário, removendo a id da instância de fluxo de trabalho concluído do **InstanceId** caixa de combinação.  
  
    ```vb  
    Private Delegate Sub GameOverDelegate()  
    Private Sub GameOver()  
        If InvokeRequired Then  
            BeginInvoke(New GameOverDelegate(AddressOf GameOver))  
        Else  
            'Remove this instance from the InstanceId combo box.  
            InstanceId.Items.Remove(InstanceId.SelectedItem)  
            InstanceId.SelectedIndex = -1  
        End If  
    End Sub  
    ```  
  
    ```csharp  
    private delegate void GameOverDelegate();  
    private void GameOver()  
    {  
        if (InvokeRequired)  
        {  
            BeginInvoke(new GameOverDelegate(GameOver));  
        }  
        else  
        {  
            // Remove this instance from the combo box  
            InstanceId.Items.Remove(InstanceId.SelectedItem);  
            InstanceId.SelectedIndex = -1;  
        }  
    }  
    ```  
  
### <a name="BKMK_ConfigureWorkflowApplication"></a> Para configurar o armazenamento de instância, manipuladores de ciclo de vida de fluxo de trabalho e extensões  
  
1.  Adicione o método `ConfigureWorkflowApplication` à classe do formulário.  
  
    ```vb  
    Private Sub ConfigureWorkflowApplication(wfApp As WorkflowApplication)  
  
    End Sub  
    ```  
  
    ```csharp  
    private void ConfigureWorkflowApplication(WorkflowApplication wfApp)  
    {      
    }  
    ```  
  
     Esse método configura o `WorkflowApplication`, adiciona as extensões desejadas e adicionar manipuladores aos eventos de ciclo de vida do fluxo de trabalho.  
  
2.  Em `ConfigureWorkflowApplication`, especifique o `SqlWorkflowInstanceStore` para o `WorkflowApplication`.  
  
    ```vb  
    'Configure the persistence store.  
    wfApp.InstanceStore = store  
    ```  
  
    ```csharp  
    // Configure the persistence store.  
    wfApp.InstanceStore = store;  
    ```  
  
3.  Em seguida, crie uma instância `StringWriter` e adicione-a à coleção de `Extensions` do `WorkflowApplication`. Quando um `StringWriter` é adicionado às extensões, ele captura todas as `WriteLine` saída da atividade. Quando o fluxo de trabalho fica ocioso, a saída de `WriteLine` pode ser extraída de `StringWriter` e exibida no formulário.  
  
    ```vb  
    'Add a StringWriter to the extensions. This captures the output  
    'from the WriteLine activities so we can display it in the form.  
    Dim sw As New StringWriter()  
    wfApp.Extensions.Add(sw)  
    ```  
  
    ```csharp  
    // Add a StringWriter to the extensions. This captures the output  
    // from the WriteLine activities so we can display it in the form.  
    StringWriter sw = new StringWriter();  
    wfApp.Extensions.Add(sw);  
    ```  
  
4.  Adicione o seguinte manipulador para o evento `Completed`. Quando um fluxo de trabalho for concluído com êxito, o número de sequências realizadas para dar um palpite do número é exibido na janela de status. Se o fluxo de trabalho terminar, as informações da exceção que causaram a conclusão serão exibidas. No final do manipulador, o método `GameOver` é chamado, o que remove o fluxo de trabalho concluído da lista de fluxo de trabalho.  
  
    ```vb  
    wfApp.Completed = _  
        Sub(e As WorkflowApplicationCompletedEventArgs)  
            If e.CompletionState = ActivityInstanceState.Faulted Then  
                UpdateStatus(String.Format("Workflow Terminated. Exception: {0}" & vbCrLf & "{1}", _  
                    e.TerminationException.GetType().FullName, _  
                    e.TerminationException.Message))  
            ElseIf e.CompletionState = ActivityInstanceState.Canceled Then  
                UpdateStatus("Workflow Canceled.")  
            Else  
                Dim Turns As Integer = Convert.ToInt32(e.Outputs("Turns"))  
                UpdateStatus(String.Format("Congratulations, you guessed the number in {0} turns.", Turns))  
            End If  
            GameOver()  
        End Sub  
    ```  
  
    ```csharp  
    wfApp.Completed = delegate(WorkflowApplicationCompletedEventArgs e)  
    {  
        if (e.CompletionState == ActivityInstanceState.Faulted)  
        {  
            UpdateStatus(string.Format("Workflow Terminated. Exception: {0}\r\n{1}",  
                e.TerminationException.GetType().FullName,  
                e.TerminationException.Message));  
        }  
        else if (e.CompletionState == ActivityInstanceState.Canceled)  
        {  
            UpdateStatus("Workflow Canceled.");  
        }  
        else  
        {  
            int Turns = Convert.ToInt32(e.Outputs["Turns"]);  
            UpdateStatus(string.Format("Congratulations, you guessed the number in {0} turns.", Turns));  
        }  
        GameOver();  
    };  
    ```  
  
5.  Adicione os seguintes manipuladores `Aborted` e `OnUnhandledException`. O método `GameOver` não é chamado do manipulador `Aborted` porque, quando uma instância de fluxo de trabalho é cancelada, ela não termina e é possível retomar a instância posteriormente.  
  
    ```vb  
    wfApp.Aborted = _  
        Sub(e As WorkflowApplicationAbortedEventArgs)  
            UpdateStatus(String.Format("Workflow Aborted. Exception: {0}" & vbCrLf & "{1}", _  
                e.Reason.GetType().FullName, _  
                e.Reason.Message))  
        End Sub  
  
    wfApp.OnUnhandledException = _  
        Function(e As WorkflowApplicationUnhandledExceptionEventArgs)  
            UpdateStatus(String.Format("Unhandled Exception: {0}" & vbCrLf & "{1}", _  
                e.UnhandledException.GetType().FullName, _  
                e.UnhandledException.Message))  
            GameOver()  
            Return UnhandledExceptionAction.Terminate  
        End Function  
    ```  
  
    ```csharp  
    wfApp.Aborted = delegate(WorkflowApplicationAbortedEventArgs e)  
    {  
        UpdateStatus(string.Format("Workflow Aborted. Exception: {0}\r\n{1}",  
                e.Reason.GetType().FullName,  
                e.Reason.Message));  
    };  
  
    wfApp.OnUnhandledException = delegate(WorkflowApplicationUnhandledExceptionEventArgs e)  
    {  
        UpdateStatus(string.Format("Unhandled Exception: {0}\r\n{1}",  
                e.UnhandledException.GetType().FullName,  
                e.UnhandledException.Message));  
        GameOver();  
        return UnhandledExceptionAction.Terminate;  
    };  
    ```  
  
6.  Adicione o seguinte manipulador `PersistableIdle`. Este manipulador recupera a extensão `StringWriter` que foi adicionada, extrai a saída das atividades de `WriteLine` e as exibe na janela de status.  
  
    ```vb  
    wfApp.PersistableIdle = _  
        Function(e As WorkflowApplicationIdleEventArgs)  
            'Send the current WriteLine outputs to the status window.  
            Dim writers = e.GetInstanceExtensions(Of StringWriter)()  
            For Each writer In writers  
                UpdateStatus(writer.ToString())  
            Next  
            Return PersistableIdleAction.Unload  
        End Function  
    ```  
  
    ```csharp  
    wfApp.PersistableIdle = delegate(WorkflowApplicationIdleEventArgs e)  
    {  
        // Send the current WriteLine outputs to the status window.  
        var writers = e.GetInstanceExtensions<StringWriter>();  
        foreach (var writer in writers)  
        {  
            UpdateStatus(writer.ToString());  
        }  
        return PersistableIdleAction.Unload;  
    };  
    ```  
  
     A enumeração <xref:System.Activities.PersistableIdleAction> tem três valores: <xref:System.Activities.PersistableIdleAction.None>, <xref:System.Activities.PersistableIdleAction.Persist> e <xref:System.Activities.PersistableIdleAction.Unload>. <xref:System.Activities.PersistableIdleAction.Persist> faz com o fluxo de trabalho persistir, mas não faz o fluxo de trabalho descarregar. <xref:System.Activities.PersistableIdleAction.Unload> faz o fluxo de trabalho persistir e ser descarregado.  
  
     O exemplo a seguir é o método `ConfigureWorkflowApplication` concluído.  
  
    ```vb  
    Private Sub ConfigureWorkflowApplication(wfApp As WorkflowApplication)  
        'Configure the persistence store.  
        wfApp.InstanceStore = store  
  
        'Add a StringWriter to the extensions. This captures the output  
        'from the WriteLine activities so we can display it in the form.  
        Dim sw As New StringWriter()  
        wfApp.Extensions.Add(sw)  
  
        wfApp.Completed = _  
            Sub(e As WorkflowApplicationCompletedEventArgs)  
                If e.CompletionState = ActivityInstanceState.Faulted Then  
                    UpdateStatus(String.Format("Workflow Terminated. Exception: {0}" & vbCrLf & "{1}", _  
                        e.TerminationException.GetType().FullName, _  
                        e.TerminationException.Message))  
                ElseIf e.CompletionState = ActivityInstanceState.Canceled Then  
                    UpdateStatus("Workflow Canceled.")  
                Else  
                    Dim Turns As Integer = Convert.ToInt32(e.Outputs("Turns"))  
                    UpdateStatus(String.Format("Congratulations, you guessed the number in {0} turns.", Turns))  
                End If  
                GameOver()  
            End Sub  
  
        wfApp.Aborted = _  
            Sub(e As WorkflowApplicationAbortedEventArgs)  
                UpdateStatus(String.Format("Workflow Aborted. Exception: {0}" & vbCrLf & "{1}", _  
                    e.Reason.GetType().FullName, _  
                    e.Reason.Message))  
            End Sub  
  
        wfApp.OnUnhandledException = _  
            Function(e As WorkflowApplicationUnhandledExceptionEventArgs)  
                UpdateStatus(String.Format("Unhandled Exception: {0}" & vbCrLf & "{1}", _  
                    e.UnhandledException.GetType().FullName, _  
                    e.UnhandledException.Message))  
                GameOver()  
                Return UnhandledExceptionAction.Terminate  
            End Function  
  
        wfApp.PersistableIdle = _  
            Function(e As WorkflowApplicationIdleEventArgs)  
                'Send the current WriteLine outputs to the status window.  
                Dim writers = e.GetInstanceExtensions(Of StringWriter)()  
                For Each writer In writers  
                    UpdateStatus(writer.ToString())  
                Next  
                Return PersistableIdleAction.Unload  
            End Function  
    End Sub  
    ```  
  
    ```csharp  
    private void ConfigureWorkflowApplication(WorkflowApplication wfApp)  
    {  
        // Configure the persistence store.  
        wfApp.InstanceStore = store;  
  
        // Add a StringWriter to the extensions. This captures the output  
        // from the WriteLine activities so we can display it in the form.  
        StringWriter sw = new StringWriter();  
        wfApp.Extensions.Add(sw);  
  
        wfApp.Completed = delegate(WorkflowApplicationCompletedEventArgs e)  
        {  
            if (e.CompletionState == ActivityInstanceState.Faulted)  
            {  
                UpdateStatus(string.Format("Workflow Terminated. Exception: {0}\r\n{1}",  
                    e.TerminationException.GetType().FullName,  
                    e.TerminationException.Message));  
            }  
            else if (e.CompletionState == ActivityInstanceState.Canceled)  
            {  
                UpdateStatus("Workflow Canceled.");  
            }  
            else  
            {  
                int Turns = Convert.ToInt32(e.Outputs["Turns"]);  
                UpdateStatus(string.Format("Congratulations, you guessed the number in {0} turns.", Turns));  
            }  
            GameOver();  
        };  
  
        wfApp.Aborted = delegate(WorkflowApplicationAbortedEventArgs e)  
        {  
            UpdateStatus(string.Format("Workflow Aborted. Exception: {0}\r\n{1}",  
                    e.Reason.GetType().FullName,  
                    e.Reason.Message));  
        };  
  
        wfApp.OnUnhandledException = delegate(WorkflowApplicationUnhandledExceptionEventArgs e)  
        {  
            UpdateStatus(string.Format("Unhandled Exception: {0}\r\n{1}",  
                    e.UnhandledException.GetType().FullName,  
                    e.UnhandledException.Message));  
            GameOver();  
            return UnhandledExceptionAction.Terminate;  
        };  
  
        wfApp.PersistableIdle = delegate(WorkflowApplicationIdleEventArgs e)  
        {  
            // Send the current WriteLine outputs to the status window.  
            var writers = e.GetInstanceExtensions<StringWriter>();  
            foreach (var writer in writers)  
            {  
                UpdateStatus(writer.ToString());  
            }  
            return PersistableIdleAction.Unload;  
        };  
    }  
    ```  
  
### <a name="BKMK_WorkflowVersionMap"></a> Para habilitar o início e retomada de vários tipos de fluxo de trabalho  
 Para retomar uma instância de fluxo de trabalho, o host precisa fornecer a definição de fluxo de trabalho. Neste tutorial, há três tipos de fluxo de trabalho e as etapas tutoriais subsequentes trazem várias versões desses tipos. `WorkflowIdentity` fornece uma maneira de um aplicativo de host associar informações de identificação a uma instância do fluxo de trabalho persistida. As etapas nesta seção demonstram como criar uma classe de utilitário para ajudar com o mapeamento da identidade de fluxo de trabalho de uma instância do fluxo de trabalho persistida para a definição do fluxo de trabalho correspondente. Para obter mais informações sobre `WorkflowIdentity` e o controle de versão, consulte [usando WorkflowIdentity e controle de versão](using-workflowidentity-and-versioning.md).  
  
1.  Clique com botão direito **NumberGuessWorkflowHost** na **Gerenciador de soluções** e escolha **Add**, **classe**. Tipo de `WorkflowVersionMap` para o **nome** caixa e clique em **Add**.  
  
2.  Adicione as seguintes instruções `using` ou `Imports` na parte superior do arquivo com as outras instruções `using` ou `Imports`.  
  
    ```vb  
    Imports NumberGuessWorkflowActivities  
    Imports System.Activities  
    ```  
  
    ```csharp  
    using NumberGuessWorkflowActivities;  
    using System.Activities;  
    ```  
  
3.  Substitua a declaração de classe `WorkflowVersionMap` pela seguinte declaração.  
  
    ```vb  
    Public Module WorkflowVersionMap  
        Dim map As Dictionary(Of WorkflowIdentity, Activity)  
  
        'Current version identities.  
        Public StateMachineNumberGuessIdentity As WorkflowIdentity  
        Public FlowchartNumberGuessIdentity As WorkflowIdentity  
        Public SequentialNumberGuessIdentity As WorkflowIdentity  
  
        Sub New()  
            map = New Dictionary(Of WorkflowIdentity, Activity)  
  
            'Add the current workflow version identities.  
            StateMachineNumberGuessIdentity = New WorkflowIdentity With  
            {  
                .Name = "StateMachineNumberGuessWorkflow",  
                .Version = New Version(1, 0, 0, 0)  
            }  
  
            FlowchartNumberGuessIdentity = New WorkflowIdentity With  
            {  
                .Name = "FlowchartNumberGuessWorkflow",  
                .Version = New Version(1, 0, 0, 0)  
            }  
  
            SequentialNumberGuessIdentity = New WorkflowIdentity With  
            {  
                .Name = "SequentialNumberGuessWorkflow",  
                .Version = New Version(1, 0, 0, 0)  
            }  
  
            map.Add(StateMachineNumberGuessIdentity, New StateMachineNumberGuessWorkflow())  
            map.Add(FlowchartNumberGuessIdentity, New FlowchartNumberGuessWorkflow())  
            map.Add(SequentialNumberGuessIdentity, New SequentialNumberGuessWorkflow())  
        End Sub  
  
        Public Function GetWorkflowDefinition(identity As WorkflowIdentity) As Activity  
            Return map(identity)  
        End Function  
  
        Public Function GetIdentityDescription(identity As WorkflowIdentity) As String  
            Return identity.ToString()  
        End Function  
    End Module  
    ```  
  
    ```csharp  
    public static class WorkflowVersionMap  
    {  
        static Dictionary<WorkflowIdentity, Activity> map;  
  
        // Current version identities.  
        static public WorkflowIdentity StateMachineNumberGuessIdentity;  
        static public WorkflowIdentity FlowchartNumberGuessIdentity;  
        static public WorkflowIdentity SequentialNumberGuessIdentity;  
  
        static WorkflowVersionMap()  
        {  
            map = new Dictionary<WorkflowIdentity, Activity>();  
  
            // Add the current workflow version identities.  
            StateMachineNumberGuessIdentity = new WorkflowIdentity  
            {  
                Name = "StateMachineNumberGuessWorkflow",  
                Version = new Version(1, 0, 0, 0)  
            };  
  
            FlowchartNumberGuessIdentity = new WorkflowIdentity  
            {  
                Name = "FlowchartNumberGuessWorkflow",  
                Version = new Version(1, 0, 0, 0)  
            };  
  
            SequentialNumberGuessIdentity = new WorkflowIdentity  
            {  
                Name = "SequentialNumberGuessWorkflow",  
                Version = new Version(1, 0, 0, 0)  
            };  
  
            map.Add(StateMachineNumberGuessIdentity, new StateMachineNumberGuessWorkflow());  
            map.Add(FlowchartNumberGuessIdentity, new FlowchartNumberGuessWorkflow());  
            map.Add(SequentialNumberGuessIdentity, new SequentialNumberGuessWorkflow());  
        }  
  
        public static Activity GetWorkflowDefinition(WorkflowIdentity identity)  
        {  
            return map[identity];  
        }  
  
        public static string GetIdentityDescription(WorkflowIdentity identity)  
        {          
            return identity.ToString();  
       }  
    }  
    ```  
  
     O `WorkflowVersionMap` contém três identidades de fluxo de trabalho que mapeiam para as três definições de fluxo de trabalho deste tutorial e é usado nas seções a seguir quando os fluxos de trabalho são iniciados e retomados.  
  
### <a name="BKMK_StartWorkflow"></a> Para iniciar um novo fluxo de trabalho  
  
1.  Adicione um manipulador `Click` para `NewGame`. Para adicionar o manipulador, alterne para **modo de exibição de Design** para o formulário e clique duas vezes em `NewGame`. Um manipulador `NewGame_Click` é adicionado e a exibição alterna para a exibição do código para o formulário. Sempre que o usuário clicar nesse botão, um novo fluxo de trabalho será iniciado.  
  
    ```vb  
    Private Sub NewGame_Click(sender As Object, e As EventArgs) Handles NewGame.Click  
  
    End Sub  
    ```  
  
    ```csharp  
    private void NewGame_Click(object sender, EventArgs e)  
    {  
  
    }  
    ```  
  
2.  Adicione o seguinte código ao manipulador de cliques. O código cria um dicionário de argumentos de entrada para o fluxo de trabalho, fechados pelo nome do argumento. Esse dicionário tem uma entrada que contém o intervalo de números gerados aleatoriamente recuperados da caixa de combinação do intervalo.  
  
    ```vb  
    Dim inputs As New Dictionary(Of String, Object)()  
    inputs.Add("MaxNumber", Convert.ToInt32(NumberRange.SelectedItem))  
    ```  
  
    ```csharp  
    var inputs = new Dictionary<string, object>();  
    inputs.Add("MaxNumber", Convert.ToInt32(NumberRange.SelectedItem));  
    ```  
  
3.  Em seguida, adicione o código a seguir que inicia o fluxo de trabalho. O `WorkflowIdentity` e a definição de fluxo de trabalho que corresponde ao tipo de fluxo de trabalho selecionado são recuperados usando a classe auxiliar `WorkflowVersionMap`. Em seguida, uma nova instância de `WorkflowApplication` é criada usando a definição de fluxo de trabalho, `WorkflowIdentity`, e o dicionário de argumentos de entrada.  
  
    ```vb  
    Dim identity As WorkflowIdentity = Nothing  
    Select Case WorkflowType.SelectedItem.ToString()  
        Case "SequentialNumberGuessWorkflow"  
            identity = WorkflowVersionMap.SequentialNumberGuessIdentity  
  
        Case "StateMachineNumberGuessWorkflow"  
            identity = WorkflowVersionMap.StateMachineNumberGuessIdentity  
  
        Case "FlowchartNumberGuessWorkflow"  
            identity = WorkflowVersionMap.FlowchartNumberGuessIdentity  
    End Select  
  
    Dim wf As Activity = WorkflowVersionMap.GetWorkflowDefinition(identity)  
  
    Dim wfApp = New WorkflowApplication(wf, inputs, identity)  
    ```  
  
    ```csharp  
    WorkflowIdentity identity = null;  
    switch (WorkflowType.SelectedItem.ToString())  
    {  
        case "SequentialNumberGuessWorkflow":  
            identity = WorkflowVersionMap.SequentialNumberGuessIdentity;  
            break;  
  
        case "StateMachineNumberGuessWorkflow":  
            identity = WorkflowVersionMap.StateMachineNumberGuessIdentity;  
            break;  
  
        case "FlowchartNumberGuessWorkflow":  
            identity = WorkflowVersionMap.FlowchartNumberGuessIdentity;  
            break;  
    };  
  
    Activity wf = WorkflowVersionMap.GetWorkflowDefinition(identity);  
  
    WorkflowApplication wfApp = new WorkflowApplication(wf, inputs, identity);  
    ```  
  
4.  Em seguida, adicione o código a seguir, que adiciona o fluxo de trabalho à lista de fluxo de trabalho e exibe as informações de versão do fluxo de trabalho no formulário.  
  
    ```vb  
    'Add the workflow to the list and display the version information.  
    WorkflowStarting = True  
    InstanceId.SelectedIndex = InstanceId.Items.Add(wfApp.Id)  
    WorkflowVersion.Text = identity.ToString()  
    WorkflowStarting = False  
    ```  
  
    ```csharp  
    // Add the workflow to the list and display the version information.  
    WorkflowStarting = true;  
    InstanceId.SelectedIndex = InstanceId.Items.Add(wfApp.Id);  
    WorkflowVersion.Text = identity.ToString();  
    WorkflowStarting = false;  
    ```  
  
5.  Chame `ConfigureWorkflowApplication` para configurar o repositório de instâncias, as extensões e os manipuladores do ciclo de vida de fluxo de trabalho para essa instância `WorkflowApplication`.  
  
    ```vb  
    'Configure the instance store, extensions, and   
    'workflow lifecycle handlers.  
    ConfigureWorkflowApplication(wfApp)  
    ```  
  
    ```csharp  
    // Configure the instance store, extensions, and   
    // workflow lifecycle handlers.  
    ConfigureWorkflowApplication(wfApp);  
    ```  
  
6.  Finalmente, chame `Run`.  
  
    ```vb  
    'Start the workflow.  
    wfApp.Run()  
    ```  
  
    ```  
    // Start the workflow.  
    wfApp.Run();  
    ```  
  
     O exemplo a seguir é o manipulador `NewGame_Click` concluído.  
  
    ```vb  
    Private Sub NewGame_Click(sender As Object, e As EventArgs) Handles NewGame.Click  
        'Start a new workflow.  
        Dim inputs As New Dictionary(Of String, Object)()  
        inputs.Add("MaxNumber", Convert.ToInt32(NumberRange.SelectedItem))  
  
        Dim identity As WorkflowIdentity = Nothing  
        Select Case WorkflowType.SelectedItem.ToString()  
            Case "SequentialNumberGuessWorkflow"  
                identity = WorkflowVersionMap.SequentialNumberGuessIdentity  
  
            Case "StateMachineNumberGuessWorkflow"  
                identity = WorkflowVersionMap.StateMachineNumberGuessIdentity  
  
            Case "FlowchartNumberGuessWorkflow"  
                identity = WorkflowVersionMap.FlowchartNumberGuessIdentity  
        End Select  
  
        Dim wf As Activity = WorkflowVersionMap.GetWorkflowDefinition(identity)  
  
        Dim wfApp = New WorkflowApplication(wf, inputs, identity)  
  
        'Add the workflow to the list and display the version information.  
        WorkflowStarting = True  
        InstanceId.SelectedIndex = InstanceId.Items.Add(wfApp.Id)  
        WorkflowVersion.Text = identity.ToString()  
        WorkflowStarting = False  
  
        'Configure the instance store, extensions, and   
        'workflow lifecycle handlers.  
        ConfigureWorkflowApplication(wfApp)  
  
        'Start the workflow.  
        wfApp.Run()  
    End Sub  
    ```  
  
    ```csharp  
    private void NewGame_Click(object sender, EventArgs e)  
    {  
        var inputs = new Dictionary<string, object>();  
        inputs.Add("MaxNumber", Convert.ToInt32(NumberRange.SelectedItem));  
  
        WorkflowIdentity identity = null;  
        switch (WorkflowType.SelectedItem.ToString())  
        {  
            case "SequentialNumberGuessWorkflow":  
                identity = WorkflowVersionMap.SequentialNumberGuessIdentity;  
                break;  
  
            case "StateMachineNumberGuessWorkflow":  
                identity = WorkflowVersionMap.StateMachineNumberGuessIdentity;  
                break;  
  
            case "FlowchartNumberGuessWorkflow":  
                identity = WorkflowVersionMap.FlowchartNumberGuessIdentity;  
                break;  
        };  
  
        Activity wf = WorkflowVersionMap.GetWorkflowDefinition(identity);  
  
        WorkflowApplication wfApp = new WorkflowApplication(wf, inputs, identity);  
  
        // Add the workflow to the list and display the version information.  
        WorkflowStarting = true;  
        InstanceId.SelectedIndex = InstanceId.Items.Add(wfApp.Id);  
        WorkflowVersion.Text = identity.ToString();  
        WorkflowStarting = false;  
  
        // Configure the instance store, extensions, and   
        // workflow lifecycle handlers.  
        ConfigureWorkflowApplication(wfApp);  
  
        // Start the workflow.  
        wfApp.Run();  
    }  
    ```  
  
### <a name="BKMK_ResumeWorkflow"></a> Para retomar um fluxo de trabalho  
  
1.  Adicione um manipulador `Click` para `EnterGuess`. Para adicionar o manipulador, alterne para **modo de exibição de Design** para o formulário e clique duas vezes em `EnterGuess`. Sempre que o usuário clicar nesse botão, um fluxo de trabalho é retomado.  
  
    ```vb  
    Private Sub EnterGuess_Click(sender As Object, e As EventArgs) Handles EnterGuess.Click  
  
    End Sub  
    ```  
  
    ```csharp  
    private void EnterGuess_Click(object sender, EventArgs e)  
    {  
  
    }  
    ```  
  
2.  Adicione o código a seguir para garantir que um fluxo de trabalho seja selecionado na lista de fluxo de trabalho, e que o palpite do usuário seja válido.  
  
    ```vb  
    If WorkflowInstanceId = Guid.Empty Then  
        MessageBox.Show("Please select a workflow.")  
        Return  
    End If  
  
    Dim userGuess As Integer  
    If Not Int32.TryParse(Guess.Text, userGuess) Then  
        MessageBox.Show("Please enter an integer.")  
        Guess.SelectAll()  
        Guess.Focus()  
        Return  
    End If  
    ```  
  
    ```csharp  
    if (WorkflowInstanceId == Guid.Empty)  
    {  
        MessageBox.Show("Please select a workflow.");  
        return;  
    }  
  
    int guess;  
    if (!Int32.TryParse(Guess.Text, out guess))  
    {  
        MessageBox.Show("Please enter an integer.");  
        Guess.SelectAll();  
        Guess.Focus();  
        return;  
    }  
    ```  
  
3.  Em seguida, recupere o `WorkflowApplicationInstance` da instância do fluxo de trabalho persistida. Um `WorkflowApplicationInstance` representa uma instância do fluxo de trabalho persistida que ainda não esteja associada a uma definição de fluxo de trabalho. O `DefinitionIdentity` do `WorkflowApplicationInstance` contém o `WorkflowIdentity` da instância do fluxo de trabalho persistida. Neste tutorial, a classe de utilitário `WorkflowVersionMap` é usada para mapear o `WorkflowIdentity` para a definição correta de fluxo de trabalho. Quando a definição de fluxo de trabalho é recuperada, um `WorkflowApplication` é criado, usando a definição correta de fluxo de trabalho.  
  
    ```vb  
    Dim instance As WorkflowApplicationInstance = _  
        WorkflowApplication.GetInstance(WorkflowInstanceId, store)  
  
    'Use the persisted WorkflowIdentity to retrieve the correct workflow  
    'definition from the dictionary.  
    Dim wf As Activity = _  
        WorkflowVersionMap.GetWorkflowDefinition(instance.DefinitionIdentity)  
  
    'Associate the WorkflowApplication with the correct definition  
    Dim wfApp As WorkflowApplication = _  
        New WorkflowApplication(wf, instance.DefinitionIdentity)  
    ```  
  
    ```csharp  
    WorkflowApplicationInstance instance =  
        WorkflowApplication.GetInstance(WorkflowInstanceId, store);  
  
    // Use the persisted WorkflowIdentity to retrieve the correct workflow  
    // definition from the dictionary.  
    Activity wf =  
        WorkflowVersionMap.GetWorkflowDefinition(instance.DefinitionIdentity);  
  
    // Associate the WorkflowApplication with the correct definition  
    WorkflowApplication wfApp =  
        new WorkflowApplication(wf, instance.DefinitionIdentity);  
    ```  
  
4.  Quando a `WorkflowApplication` é criada, configure o repositório de instâncias, os manipuladores do ciclo de vida de fluxo de trabalho e as extensões chamando `ConfigureWorkflowApplication`. Essas etapas devem ser executadas toda vez que um `WorkflowApplication` novo é criado, e devem ser feitas antes que a instância de fluxo de trabalho seja carregada no `WorkflowApplication`. Depois que o fluxo de trabalho é carregado, ele será retomado com o palpite do usuário.  
  
    ```vb  
    'Configure the extensions and lifecycle handlers.  
    'Do this before the instance is loaded. Once the instance is  
    'loaded it is too late to add extensions.  
    ConfigureWorkflowApplication(wfApp)  
  
    'Load the workflow.  
    wfApp.Load(instance)  
  
    'Resume the workflow.  
    wfApp.ResumeBookmark("EnterGuess", userGuess)  
    ```  
  
    ```csharp  
    // Configure the extensions and lifecycle handlers.  
    // Do this before the instance is loaded. Once the instance is  
    // loaded it is too late to add extensions.  
    ConfigureWorkflowApplication(wfApp);  
  
    // Load the workflow.  
    wfApp.Load(instance);  
  
    // Resume the workflow.  
    wfApp.ResumeBookmark("EnterGuess", guess);  
    ```  
  
5.  Finalmente, desmarque a caixa de texto de palpite e prepare o formulário para aceitar outro palpite.  
  
    ```vb  
    'Clear the Guess textbox.  
    Guess.Clear()  
    Guess.Focus()  
    ```  
  
    ```csharp  
    // Clear the Guess textbox.  
    Guess.Clear();  
    Guess.Focus();  
    ```  
  
     O exemplo a seguir é o manipulador `EnterGuess_Click` concluído.  
  
    ```vb  
    Private Sub EnterGuess_Click(sender As Object, e As EventArgs) Handles EnterGuess.Click  
        If WorkflowInstanceId = Guid.Empty Then  
            MessageBox.Show("Please select a workflow.")  
            Return  
        End If  
  
        Dim userGuess As Integer  
        If Not Int32.TryParse(Guess.Text, userGuess) Then  
            MessageBox.Show("Please enter an integer.")  
            Guess.SelectAll()  
            Guess.Focus()  
            Return  
        End If  
  
        Dim instance As WorkflowApplicationInstance = _  
            WorkflowApplication.GetInstance(WorkflowInstanceId, store)  
  
        'Use the persisted WorkflowIdentity to retrieve the correct workflow  
        'definition from the dictionary.  
        Dim wf As Activity = _  
            WorkflowVersionMap.GetWorkflowDefinition(instance.DefinitionIdentity)  
  
        'Associate the WorkflowApplication with the correct definition  
        Dim wfApp As WorkflowApplication = _  
            New WorkflowApplication(wf, instance.DefinitionIdentity)  
  
        'Configure the extensions and lifecycle handlers.  
        'Do this before the instance is loaded. Once the instance is  
        'loaded it is too late to add extensions.  
        ConfigureWorkflowApplication(wfApp)  
  
        'Load the workflow.  
        wfApp.Load(instance)  
  
        'Resume the workflow.  
        wfApp.ResumeBookmark("EnterGuess", userGuess)  
  
        'Clear the Guess textbox.  
        Guess.Clear()  
        Guess.Focus()  
    End Sub  
    ```  
  
    ```csharp  
    private void EnterGuess_Click(object sender, EventArgs e)  
    {  
        if (WorkflowInstanceId == Guid.Empty)  
        {  
            MessageBox.Show("Please select a workflow.");  
            return;  
        }  
  
        int guess;  
        if (!Int32.TryParse(Guess.Text, out guess))  
        {  
            MessageBox.Show("Please enter an integer.");  
            Guess.SelectAll();  
            Guess.Focus();  
            return;  
        }  
  
        WorkflowApplicationInstance instance =  
            WorkflowApplication.GetInstance(WorkflowInstanceId, store);  
  
        // Use the persisted WorkflowIdentity to retrieve the correct workflow  
        // definition from the dictionary.  
        Activity wf =  
            WorkflowVersionMap.GetWorkflowDefinition(instance.DefinitionIdentity);  
  
        // Associate the WorkflowApplication with the correct definition  
        WorkflowApplication wfApp =  
            new WorkflowApplication(wf, instance.DefinitionIdentity);  
  
        // Configure the extensions and lifecycle handlers.  
        // Do this before the instance is loaded. Once the instance is  
        // loaded it is too late to add extensions.  
        ConfigureWorkflowApplication(wfApp);  
  
        // Load the workflow.  
        wfApp.Load(instance);  
  
        // Resume the workflow.  
        wfApp.ResumeBookmark("EnterGuess", guess);  
  
        // Clear the Guess textbox.  
        Guess.Clear();  
        Guess.Focus();  
    }  
    ```  
  
### <a name="BKMK_TerminateWorkflow"></a> Para encerrar um fluxo de trabalho  
  
1.  Adicione um manipulador `Click` para `QuitGame`. Para adicionar o manipulador, alterne para **modo de exibição de Design** para o formulário e clique duas vezes em `QuitGame`. Sempre que o usuário clicar nesse botão, o fluxo de trabalho selecionado atual será encerrado.  
  
    ```vb  
    Private Sub QuitGame_Click(sender As Object, e As EventArgs) Handles QuitGame.Click  
  
    End Sub  
    ```  
  
    ```csharp  
    private void QuitGame_Click(object sender, EventArgs e)  
    {  
  
    }  
    ```  
  
2.  Adicione o seguinte código ao manipulador `QuitGame_Click`. Esse código primeiro verifica para garantir que um fluxo de trabalho esteja selecionado na lista de fluxo de trabalho. Em seguida, ele carrega a instância persistida em um `WorkflowApplicationInstance`, use a `DefinitionIdentity` para determinar a definição correta de fluxo de trabalho e depois inicializa o `WorkflowApplication`. Em seguida, as extensões e os manipuladores de ciclo de vida de fluxo de trabalho são configurados com uma chamada para `ConfigureWorkflowApplication`. Quando o `WorkflowApplication` é configurado, ele será carregado e, em seguida, `Terminate` será chamado.  
  
    ```vb  
    If WorkflowInstanceId = Guid.Empty Then  
        MessageBox.Show("Please select a workflow.")  
        Return  
    End If  
  
    Dim instance As WorkflowApplicationInstance = _  
        WorkflowApplication.GetInstance(WorkflowInstanceId, store)  
  
    'Use the persisted WorkflowIdentity to retrieve the correct workflow  
    'definition from the dictionary.  
    Dim wf As Activity = WorkflowVersionMap.GetWorkflowDefinition(instance.DefinitionIdentity)  
  
    'Associate the WorkflowApplication with the correct definition.  
    Dim wfApp As WorkflowApplication = _  
        New WorkflowApplication(wf, instance.DefinitionIdentity)  
  
    'Configure the extensions and lifecycle handlers.  
    ConfigureWorkflowApplication(wfApp)  
  
    'Load the workflow.  
    wfApp.Load(instance)  
  
    'Terminate the workflow.  
    wfApp.Terminate("User resigns.")  
    ```  
  
    ```csharp  
    if (WorkflowInstanceId == Guid.Empty)  
    {  
        MessageBox.Show("Please select a workflow.");  
        return;  
    }  
  
    WorkflowApplicationInstance instance =  
        WorkflowApplication.GetInstance(WorkflowInstanceId, store);  
  
    // Use the persisted WorkflowIdentity to retrieve the correct workflow  
    // definition from the dictionary.  
    Activity wf = WorkflowVersionMap.GetWorkflowDefinition(instance.DefinitionIdentity);  
  
    // Associate the WorkflowApplication with the correct definition  
    WorkflowApplication wfApp =  
        new WorkflowApplication(wf, instance.DefinitionIdentity);  
  
    // Configure the extensions and lifecycle handlers  
    ConfigureWorkflowApplication(wfApp);  
  
    // Load the workflow.  
    wfApp.Load(instance);  
  
    // Terminate the workflow.  
    wfApp.Terminate("User resigns.");  
    ```  
  
### <a name="BKMK_BuildAndRun"></a> Para compilar e executar o aplicativo  
  
1.  Clique duas vezes em **Program.cs** (ou **Module1.vb**) na **Gerenciador de soluções** para exibir o código.  
  
2.  Adicione a seguinte instrução `using` (ou `Imports`) na parte superior do arquivo com as outras instruções `using` (ou `Imports`).  
  
    ```vb  
    Imports System.Windows.Forms  
    ```  
  
    ```csharp  
    using System.Windows.Forms;  
    ```  
  
3.  Remova ou comente o fluxo de trabalho existente que hospeda o código de [como: Executar um fluxo de trabalho](how-to-run-a-workflow.md)e substitua-o pelo código a seguir.  
  
    ```vb  
    Sub Main()  
        Application.EnableVisualStyles()  
        Application.Run(New WorkflowHostForm())  
    End Sub  
    ```  
  
    ```csharp  
    static void Main(string[] args)  
    {  
        Application.EnableVisualStyles();  
        Application.Run(new WorkflowHostForm());  
    }  
    ```  
  
4.  Clique com botão direito **NumberGuessWorkflowHost** na **Gerenciador de soluções** e escolha **propriedades**. No **Application** , especifique **aplicativo do Windows** para o **tipo de saída**. Essa etapa é opcional, mas se não for seguida, a janela do console será exibida além do formulário.  
  
5.  Pressione Ctrl+Shift+B para criar o aplicativo.  
  
6.  Certifique-se de que **NumberGuessWorkflowHost** está definido como o aplicativo de inicialização e pressione Ctrl + F5 para iniciar o aplicativo.  
  
7.  Selecionar um intervalo para o jogo de estimativa e o tipo de fluxo de trabalho para iniciar e, em seguida, clique em **novo jogo**. Insira um Palpite na **Palpite** caixa e clique em **vá** para enviar seu palpite. Observe que a saída das atividades de `WriteLine` são exibidas no formulário.  
  
8.  Iniciar vários fluxos de trabalho usando intervalos de número e os tipos de fluxo de trabalho diferente, insira alguns Palpites e alterne entre os fluxos de trabalho, selecionando a partir de **Id da instância de fluxo de trabalho** lista.  
  
     Observe que, quando você alterna para um novo fluxo de trabalho, os palpites anteriores e o progresso do fluxo de trabalho não são exibidos na janela de status. A razão pela qual o status não está disponível é porque ele não é capturado e salvo em nenhum lugar. Na próxima etapa do tutorial, [como: Criar um participante de acompanhamento personalizado](how-to-create-a-custom-tracking-participant.md), criar um participante personalizado que salva essas informações.
