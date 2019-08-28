---
title: 'Como: executar um fluxo de trabalho'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: f814ff82-fe2b-4614-aebb-b768c3e61179
ms.openlocfilehash: 07f0e5dc232411633626add460ffc29cc7a79d81
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/27/2019
ms.locfileid: "70044346"
---
# <a name="how-to-run-a-workflow"></a>Como: executar um fluxo de trabalho
Este tópico é uma continuação do Windows Workflow Foundation introdução tutorial e discute como criar um host de fluxo de trabalho e executar o fluxo de trabalho definido no [seguinte como: Criar um tópico](how-to-create-a-workflow.md) de fluxo de trabalho.

> [!NOTE]
> Cada tópico do tutorial de Introdução depende dos tópicos anteriores. Para concluir este tópico, você deve primeiro [concluir como: Crie uma atividade](how-to-create-an-activity.md) e [como: Crie um fluxo](how-to-create-a-workflow.md)de trabalho.

> [!NOTE]
> Para baixar uma versão completa do tutorial, consulte [Windows Workflow Foundation (WF45) – introdução tutorial](https://go.microsoft.com/fwlink/?LinkID=248976).  
  
### <a name="to-create-the-workflow-host-project"></a>Para criar o projeto de host de fluxo de trabalho  
  
1. Abra a solução na seção [como: Crie um tópico](how-to-create-an-activity.md) de atividade usando o Visual Studio 2012.  
  
2. Clique com o botão direito do mouse na solução **WF45GettingStartedTutorial** em **Gerenciador de soluções** e selecione **Adicionar**, **novo projeto**.  
  
    > [!TIP]
    > Se a janela de **Gerenciador de soluções** não for exibida, selecione **Gerenciador de soluções** no menu **Exibir** .

3. No nó **instalado** , selecione **Visual C#** , **fluxo de trabalho** (ou **Visual Basic**, fluxo de **trabalho**).

    > [!NOTE]
    > Dependendo da linguagem de programação configurada como o idioma principal no Visual Studio, o **nó C# Visual** ou **Visual Basic** pode estar no nó **outros idiomas** do nó **instalado** .

     Verifique se **.NET Framework 4,5** está selecionado na lista suspensa .NET Framework versão. Selecione **aplicativo de console de fluxo de trabalho** na lista **fluxo de trabalho** . Digite `NumberGuessWorkflowHost` na caixa **nome** e clique em **OK**. Isso cria um aplicativo de fluxo de trabalho inicial com suporte básico de hospedagem de fluxo de trabalho. Esse código básico de hospedagem é modificado e usado para executar o aplicativo de fluxo de trabalho.

4. Clique com o botão direito do mouse no projeto **NumberGuessWorkflowHost** recém-adicionado no **Gerenciador de soluções** e selecione **Adicionar referência**. Selecione **solução** na lista **Adicionar referência** , marque a caixa de seleção ao lado de **NumberGuessWorkflowActivities**e clique em **OK**.

5. Clique com o botão direito do mouse em **Workflow1. XAML** em **Gerenciador de soluções** e escolha **excluir**. Clique em **OK** para confirmar.

### <a name="to-modify-the-workflow-hosting-code"></a>Para modificar o código de hospedagem do fluxo de trabalho

1. Clique duas vezes em **Program.cs** ou **Module1. vb** em **Gerenciador de soluções** para exibir o código.

    > [!TIP]
    > Se a janela de **Gerenciador de soluções** não for exibida, selecione **Gerenciador de soluções** no menu **Exibir** .

     Como esse projeto foi criado usando o modelo de **aplicativo do console de fluxo de trabalho** , **Program.cs** ou **Module1. vb** contém o código de hospedagem do fluxo de trabalho básico a seguir.

    ```vb
    ' Create and cache the workflow definition.
    Dim workflow1 As Activity = New Workflow1()
    WorkflowInvoker.Invoke(workflow1)
    ```

    ```csharp
    // Create and cache the workflow definition.
    Activity workflow1 = new Workflow1();
    WorkflowInvoker.Invoke(workflow1);
    ```

     Esse código de hospedagem gerado usa <xref:System.Activities.WorkflowInvoker>. <xref:System.Activities.WorkflowInvoker> fornece uma maneira simples para chamar um fluxo de trabalho como se fosse uma chamada de método e pode ser usado somente para os fluxos de trabalho que não usam persistência. <xref:System.Activities.WorkflowApplication> fornece um modelo mais avançado para executar fluxos de trabalho que incluem a notificação de eventos de ciclo de vida, o controle de execução, o reinício do indicador e a persistência. Este exemplo usa indicadores e o <xref:System.Activities.WorkflowApplication> é usado para hospedar o fluxo de trabalho. Adicione a seguinte `using` instrução ou Imports na parte superior do **Program.cs** ou **Module1. vb** abaixo das instruções **using** ou Imports existentes.

    ```vb
    Imports NumberGuessWorkflowActivities
    Imports System.Threading
    ```

    ```csharp
    using NumberGuessWorkflowActivities;
    using System.Threading;
    ```

     Substituir as linhas de código que usam <xref:System.Activities.WorkflowInvoker> com o código de hospedagem básica <xref:System.Activities.WorkflowApplication> a seguir. Este código de hospedagem de exemplo demonstra as etapas básicas para hospedar e chamar um fluxo de trabalho, mas ainda não contém a funcionalidade para executar com êxito o fluxo de trabalho a partir deste tópico. Nas etapas a seguir, esse código básico é modificado e os recursos adicionais são adicionados até que o aplicativo esteja concluído.

    > [!NOTE]
    > `Workflow1` Substitua esses exemplos pelo `FlowchartNumberGuessWorkflow`, `SequentialNumberGuessWorkflow`ou `StateMachineNumberGuessWorkflow`, dependendo de qual fluxo de trabalho você concluiu na seção [como: Crie uma etapa](how-to-create-a-workflow.md) de fluxo de trabalho. Se você não substituir `Workflow1`, receberá erros de compilação quando tentar criar ou executar o fluxo de trabalho.

     [!code-csharp[CFX_WF_GettingStarted#4](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_wf_gettingstarted/cs/extrasnippets.cs#4)]
     [!code-vb[CFX_WF_GettingStarted#4](~/samples/snippets/visualbasic/VS_Snippets_CFX/cfx_wf_gettingstarted/vb/extrasnippets.vb#4)]

     Esse código cria um <xref:System.Activities.WorkflowApplication>, assina três eventos do ciclo de vida de fluxo de trabalho, inicia o fluxo de trabalho com uma chamada para <xref:System.Activities.WorkflowApplication.Run%2A> e aguarda que o fluxo de trabalho seja concluído. Quando o fluxo de trabalho estiver concluído, o <xref:System.Threading.AutoResetEvent> é definido e o aplicativo host é concluído.

### <a name="to-set-input-arguments-of-a-workflow"></a>Para definir argumentos de entrada de um fluxo de trabalho

1. Adicione a seguinte instrução na parte superior de **Program.cs** ou **Module1. vb** abaixo das instruções `using` ou `Imports` existentes.

     [!code-csharp[CFX_WF_GettingStarted#5](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_wf_gettingstarted/cs/program.cs#5)]
     [!code-vb[CFX_WF_GettingStarted#5](~/samples/snippets/visualbasic/VS_Snippets_CFX/cfx_wf_gettingstarted/vb/module1.vb#5)]

2. Substitua a linha de código que cria uma nova <xref:System.Activities.WorkflowApplication> pelo código a seguir que cria e passa um dicionário dos parâmetros para o fluxo de trabalho quando ele é criado.

    > [!NOTE]
    > `Workflow1` Substitua esses exemplos pelo `FlowchartNumberGuessWorkflow`, `SequentialNumberGuessWorkflow`ou `StateMachineNumberGuessWorkflow`, dependendo de qual fluxo de trabalho você concluiu na seção [como: Crie uma etapa](how-to-create-a-workflow.md) de fluxo de trabalho. Se você não substituir `Workflow1`, receberá erros de compilação quando tentar criar ou executar o fluxo de trabalho.

     [!code-csharp[CFX_WF_GettingStarted#6](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_wf_gettingstarted/cs/program.cs#6)]
     [!code-vb[CFX_WF_GettingStarted#6](~/samples/snippets/visualbasic/VS_Snippets_CFX/cfx_wf_gettingstarted/vb/module1.vb#6)]

     Este dicionário contém um elemento com uma chave `MaxNumber`. As chaves do dicionário de entrada correspondem a argumentos de entrada na atividade raiz do fluxo de trabalho. `MaxNumber` é usado pelo fluxo de trabalho para determinar o limite superior para o número gerado aleatoriamente.

### <a name="to-retrieve-output-arguments-of-a-workflow"></a>Para recuperar argumentos de saída de um fluxo de trabalho

1. Modifique o manipulador <xref:System.Activities.WorkflowApplication.Completed%2A> para recuperar e exibir o número de sequências usadas pelo fluxo de trabalho.

     [!code-csharp[CFX_WF_GettingStarted#7](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_wf_gettingstarted/cs/program.cs#7)]
     [!code-vb[CFX_WF_GettingStarted#7](~/samples/snippets/visualbasic/VS_Snippets_CFX/cfx_wf_gettingstarted/vb/module1.vb#7)]

### <a name="to-resume-a-bookmark"></a>Para retomar um indicador

1. Adicione o código a seguir na parte superior do método `Main` imediatamente após a instrução <xref:System.Threading.AutoResetEvent> existente.

     [!code-csharp[CFX_WF_GettingStarted#8](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_wf_gettingstarted/cs/program.cs#8)]
     [!code-vb[CFX_WF_GettingStarted#8](~/samples/snippets/visualbasic/VS_Snippets_CFX/cfx_wf_gettingstarted/vb/module1.vb#8)]

2. Adicione o manipulador <xref:System.Activities.WorkflowApplication.Idle%2A> a seguir abaixo dos manipuladores existentes do ciclo de vida de fluxo de trabalho em `Main`.

     [!code-csharp[CFX_WF_GettingStarted#9](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_wf_gettingstarted/cs/program.cs#9)]
     [!code-vb[CFX_WF_GettingStarted#9](~/samples/snippets/visualbasic/VS_Snippets_CFX/cfx_wf_gettingstarted/vb/module1.vb#9)]

     Cada vez que o fluxo de trabalho se torna ocioso aguardando a próxima estimativa, esse manipulador `idleAction` é chamado e o <xref:System.Threading.AutoResetEvent> é definido. O código na etapa a seguir usa `idleEvent` e `syncEvent` para determinar se o fluxo de trabalho está esperando o próximo palpite ou está concluído.

    > [!NOTE]
    > Neste exemplo, o aplicativo host usa eventos de redefinição automática nos manipuladores <xref:System.Activities.WorkflowApplication.Completed%2A> e de <xref:System.Activities.WorkflowApplication.Idle%2A> para sincronizar o aplicativo host com o progresso do fluxo de trabalho. Não é necessário bloquear e esperar que o fluxo de trabalho fique inativo antes de retomar um indicador, mas, nesse exemplo, os eventos de sincronização são necessários para que o host saiba se o fluxo de trabalho está concluído ou se está aguardando mais entrada do usuário usando o <xref:System.Activities.Bookmark>. Para obter mais informações, consulte [indicadores](bookmarks.md).

3. Remova a chamada para `WaitOne` e substitua-a pelo código para coletar entrada do usuário e retomar o <xref:System.Activities.Bookmark>.

     Remova a seguinte linha de código.

     [!code-csharp[CFX_WF_GettingStarted#10](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_wf_gettingstarted/cs/extrasnippets.cs#10)]
     [!code-vb[CFX_WF_GettingStarted#10](~/samples/snippets/visualbasic/VS_Snippets_CFX/cfx_wf_gettingstarted/vb/extrasnippets.vb#10)]

     Substitua-a pelo exemplo a seguir.

     [!code-csharp[CFX_WF_GettingStarted#11](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_wf_gettingstarted/cs/program.cs#11)]
     [!code-vb[CFX_WF_GettingStarted#11](~/samples/snippets/visualbasic/VS_Snippets_CFX/cfx_wf_gettingstarted/vb/module1.vb#11)]

## <a name="BKMK_ToRunTheApplication"></a>Para compilar e executar o aplicativo

1. Clique com o botão direito do mouse em **NumberGuessWorkflowHost** em **Gerenciador de soluções** e selecione **definir como projeto de inicialização**.

2. Pressione CTRL+F5 para compilar e executar o aplicativo. Tente determinar o número no menor número de sequências possível.

     Para testar o aplicativo com um dos outros estilos de fluxo de trabalho, substitua `Workflow1` no código que cria o <xref:System.Activities.WorkflowApplication> por `FlowchartNumberGuessWorkflow`, `SequentialNumberGuessWorkflow` ou `StateMachineNumberGuessWorkflow`, dependendo de qual estilo de fluxo de trabalho você deseja.

     [!code-csharp[CFX_WF_GettingStarted#6](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_wf_gettingstarted/cs/program.cs#6)]
     [!code-vb[CFX_WF_GettingStarted#6](~/samples/snippets/visualbasic/VS_Snippets_CFX/cfx_wf_gettingstarted/vb/module1.vb#6)]

     Para obter instruções sobre como adicionar persistência a um aplicativo de fluxo de trabalho, consulte o [próximo tópico, como: Crie e execute um fluxo de trabalho](how-to-create-and-run-a-long-running-workflow.md)de longa execução.

## <a name="example"></a>Exemplo
 O exemplo a seguir é a listagem de código completa para o método `Main`.

> [!NOTE]
> `Workflow1` Substitua esses exemplos pelo `FlowchartNumberGuessWorkflow`, `SequentialNumberGuessWorkflow`ou `StateMachineNumberGuessWorkflow`, dependendo de qual fluxo de trabalho você concluiu na seção [como: Crie uma etapa](how-to-create-a-workflow.md) de fluxo de trabalho. Se você não substituir `Workflow1`, receberá erros de compilação quando tentar criar ou executar o fluxo de trabalho.

 [!code-csharp[CFX_WF_GettingStarted#12](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_wf_gettingstarted/cs/program.cs#12)]
 [!code-vb[CFX_WF_GettingStarted#12](~/samples/snippets/visualbasic/VS_Snippets_CFX/cfx_wf_gettingstarted/vb/module1.vb#12)]

## <a name="see-also"></a>Consulte também

- <xref:System.Activities.WorkflowApplication>
- <xref:System.Activities.Bookmark>
- [Programação do Windows Workflow Foundation](programming.md)
- [Tutorial de Introdução](getting-started-tutorial.md)
- [Como: Criar um fluxo de trabalho](how-to-create-a-workflow.md)
- [Como: Criar e executar um fluxo de trabalho de longa execução](how-to-create-and-run-a-long-running-workflow.md)
- [Esperando entrada em um fluxo de trabalho](waiting-for-input-in-a-workflow.md)
- [Hospedando fluxos de trabalho](hosting-workflows.md)
