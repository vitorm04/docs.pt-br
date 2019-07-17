---
title: 'Como: executar um fluxo de trabalho'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: f814ff82-fe2b-4614-aebb-b768c3e61179
ms.openlocfilehash: a7784f37c9e8009adc3735974a6fb0423f24ea37
ms.sourcegitcommit: 4d8efe00f2e5ab42e598aff298d13b8c052d9593
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/16/2019
ms.locfileid: "68238510"
---
# <a name="how-to-run-a-workflow"></a>Como: executar um fluxo de trabalho
Este tópico é uma continuação do tutorial do guia de Introdução do Windows Workflow Foundation e discute como criar um host de fluxo de trabalho e executar o fluxo de trabalho definido anteriormente na [como: Criar um fluxo de trabalho](how-to-create-a-workflow.md) tópico.

> [!NOTE]
>  Cada tópico do tutorial de Introdução depende dos tópicos anteriores. Para concluir este tópico, você deve primeiro concluir [como: Criar uma atividade](how-to-create-an-activity.md) e [como: Criar um fluxo de trabalho](how-to-create-a-workflow.md).

> [!NOTE]
>  Para baixar uma versão completa do tutorial, consulte [Windows Workflow Foundation (WF45) - Tutorial de Introdução](https://go.microsoft.com/fwlink/?LinkID=248976).  
  
### <a name="to-create-the-workflow-host-project"></a>Para criar o projeto de host de fluxo de trabalho  
  
1. Abra a solução do anterior [como: Criar uma atividade](how-to-create-an-activity.md) tópico usando o Visual Studio 2012.  
  
2. Com o botão direito do **WF45GettingStartedTutorial** solução em **Gerenciador de soluções** e selecione **Add**, **novo projeto**.  
  
    > [!TIP]
    >  Se o **Gerenciador de soluções** janela não for exibida, selecione **Gerenciador de soluções** do **exibição** menu.

3. No **Installed** nó, selecione **Visual c#** , **fluxo de trabalho** (ou **Visual Basic**, **fluxo de trabalho**).

    > [!NOTE]
    >  Dependendo da linguagem de programação configurada como linguagem primária no Visual Studio, o **Visual c#** ou **Visual Basic** nó pode estar abaixo de **outros idiomas** nó de **instalado** nó.

     Certifique-se de que **.NET Framework 4.5** está selecionado na lista suspensa de versão do .NET Framework. Selecione **aplicativo de Console do fluxo de trabalho** da **fluxo de trabalho** lista. Tipo de `NumberGuessWorkflowHost` para o **nome** caixa e clique em **Okey**. Isso cria um aplicativo de fluxo de trabalho inicial com suporte básico de hospedagem de fluxo de trabalho. Esse código básico de hospedagem é modificado e usado para executar o aplicativo de fluxo de trabalho.

4. Clique com botão direito recém-adicionada **NumberGuessWorkflowHost** project no **Gerenciador de soluções** e selecione **Add Reference**. Selecione **solução** da **adicionar referência** lista, marque a caixa de seleção ao lado de **NumberGuessWorkflowActivities**e, em seguida, clique em **Okey** .

5. Clique com botão direito **Workflow1.xaml** na **Gerenciador de soluções** e escolha **excluir**. Clique em **Okey** para confirmar.

### <a name="to-modify-the-workflow-hosting-code"></a>Para modificar o código de hospedagem do fluxo de trabalho

1. Clique duas vezes em **Program.cs** ou **Module1.vb** na **Gerenciador de soluções** para exibir o código.

    > [!TIP]
    >  Se o **Gerenciador de soluções** janela não for exibida, selecione **Gerenciador de soluções** do **exibição** menu.

     Porque este projeto foi criado usando o **aplicativo de Console do fluxo de trabalho** modelo, **Program.cs** ou **Module1.vb** contém a seguinte hospedagem de fluxo de trabalho básico código.

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

     Esse código de hospedagem gerado usa <xref:System.Activities.WorkflowInvoker>. <xref:System.Activities.WorkflowInvoker> fornece uma maneira simples para chamar um fluxo de trabalho como se fosse uma chamada de método e pode ser usado somente para os fluxos de trabalho que não usam persistência. <xref:System.Activities.WorkflowApplication> fornece um modelo mais avançado para executar fluxos de trabalho que incluem a notificação de eventos de ciclo de vida, o controle de execução, o reinício do indicador e a persistência. Este exemplo usa indicadores e o <xref:System.Activities.WorkflowApplication> é usado para hospedar o fluxo de trabalho. Adicione o seguinte `using` ou **Imports** instrução na parte superior da **Program.cs** ou **Module1.vb** abaixo das **usando** ou **importações** instruções.

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
    >  Substitua `Workflow1` nesses exemplos com `FlowchartNumberGuessWorkflow`, `SequentialNumberGuessWorkflow`, ou `StateMachineNumberGuessWorkflow`, dependendo de qual fluxo de trabalho concluída anteriormente na [como: Criar um fluxo de trabalho](how-to-create-a-workflow.md) etapa. Se você não substituir `Workflow1`, receberá erros de compilação quando tentar criar ou executar o fluxo de trabalho.

     [!code-csharp[CFX_WF_GettingStarted#4](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_wf_gettingstarted/cs/extrasnippets.cs#4)]
     [!code-vb[CFX_WF_GettingStarted#4](~/samples/snippets/visualbasic/VS_Snippets_CFX/cfx_wf_gettingstarted/vb/extrasnippets.vb#4)]

     Esse código cria um <xref:System.Activities.WorkflowApplication>, assina três eventos do ciclo de vida de fluxo de trabalho, inicia o fluxo de trabalho com uma chamada para <xref:System.Activities.WorkflowApplication.Run%2A> e aguarda que o fluxo de trabalho seja concluído. Quando o fluxo de trabalho estiver concluído, o <xref:System.Threading.AutoResetEvent> é definido e o aplicativo host é concluído.

### <a name="to-set-input-arguments-of-a-workflow"></a>Para definir argumentos de entrada de um fluxo de trabalho

1. Adicione a seguinte instrução na parte superior da **Program.cs** ou **Module1.vb** abaixo das `using` ou `Imports` instruções.

     [!code-csharp[CFX_WF_GettingStarted#5](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_wf_gettingstarted/cs/program.cs#5)]
     [!code-vb[CFX_WF_GettingStarted#5](~/samples/snippets/visualbasic/VS_Snippets_CFX/cfx_wf_gettingstarted/vb/module1.vb#5)]

2. Substitua a linha de código que cria uma nova <xref:System.Activities.WorkflowApplication> pelo código a seguir que cria e passa um dicionário dos parâmetros para o fluxo de trabalho quando ele é criado.

    > [!NOTE]
    >  Substitua `Workflow1` nesses exemplos com `FlowchartNumberGuessWorkflow`, `SequentialNumberGuessWorkflow`, ou `StateMachineNumberGuessWorkflow`, dependendo de qual fluxo de trabalho concluída anteriormente na [como: Criar um fluxo de trabalho](how-to-create-a-workflow.md) etapa. Se você não substituir `Workflow1`, receberá erros de compilação quando tentar criar ou executar o fluxo de trabalho.

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

     Cada vez que o fluxo de trabalho fica ocioso aguardando o próximo Palpite, esse manipulador é chamado e o `idleAction` <xref:System.Threading.AutoResetEvent> está definido. O código na etapa a seguir usa `idleEvent` e `syncEvent` para determinar se o fluxo de trabalho está esperando o próximo palpite ou está concluído.

    > [!NOTE]
    >  Neste exemplo, o aplicativo host usa eventos de redefinição automática nos manipuladores <xref:System.Activities.WorkflowApplication.Completed%2A> e de <xref:System.Activities.WorkflowApplication.Idle%2A> para sincronizar o aplicativo host com o progresso do fluxo de trabalho. Não é necessário bloquear e esperar que o fluxo de trabalho fique inativo antes de retomar um indicador, mas, nesse exemplo, os eventos de sincronização são necessários para que o host saiba se o fluxo de trabalho está concluído ou se está aguardando mais entrada do usuário usando o <xref:System.Activities.Bookmark>. Para obter mais informações, consulte [indicadores](bookmarks.md).

3. Remova a chamada para `WaitOne` e substitua-a pelo código para coletar entrada do usuário e retomar o <xref:System.Activities.Bookmark>.

     Remova a seguinte linha de código.

     [!code-csharp[CFX_WF_GettingStarted#10](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_wf_gettingstarted/cs/extrasnippets.cs#10)]
     [!code-vb[CFX_WF_GettingStarted#10](~/samples/snippets/visualbasic/VS_Snippets_CFX/cfx_wf_gettingstarted/vb/extrasnippets.vb#10)]

     Substitua-a pelo exemplo a seguir.

     [!code-csharp[CFX_WF_GettingStarted#11](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_wf_gettingstarted/cs/program.cs#11)]
     [!code-vb[CFX_WF_GettingStarted#11](~/samples/snippets/visualbasic/VS_Snippets_CFX/cfx_wf_gettingstarted/vb/module1.vb#11)]

## <a name="BKMK_ToRunTheApplication"></a> Para compilar e executar o aplicativo

1. Clique com botão direito **NumberGuessWorkflowHost** na **Gerenciador de soluções** e selecione **Set as StartUp Project**.

2. Pressione CTRL+F5 para compilar e executar o aplicativo. Tente determinar o número no menor número de sequências possível.

     Para testar o aplicativo com um dos outros estilos de fluxo de trabalho, substitua `Workflow1` no código que cria o <xref:System.Activities.WorkflowApplication> por `FlowchartNumberGuessWorkflow`, `SequentialNumberGuessWorkflow` ou `StateMachineNumberGuessWorkflow`, dependendo de qual estilo de fluxo de trabalho você deseja.

     [!code-csharp[CFX_WF_GettingStarted#6](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_wf_gettingstarted/cs/program.cs#6)]
     [!code-vb[CFX_WF_GettingStarted#6](~/samples/snippets/visualbasic/VS_Snippets_CFX/cfx_wf_gettingstarted/vb/module1.vb#6)]

     Para obter instruções sobre como adicionar persistência a um aplicativo de fluxo de trabalho, consulte o próximo tópico, [como: Criar e executar uma longa em execução de fluxo de trabalho](how-to-create-and-run-a-long-running-workflow.md).

## <a name="example"></a>Exemplo
 O exemplo a seguir é a listagem de código completa para o método `Main`.

> [!NOTE]
>  Substitua `Workflow1` nesses exemplos com `FlowchartNumberGuessWorkflow`, `SequentialNumberGuessWorkflow`, ou `StateMachineNumberGuessWorkflow`, dependendo de qual fluxo de trabalho concluída anteriormente na [como: Criar um fluxo de trabalho](how-to-create-a-workflow.md) etapa. Se você não substituir `Workflow1`, receberá erros de compilação quando tentar criar ou executar o fluxo de trabalho.

 [!code-csharp[CFX_WF_GettingStarted#12](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_wf_gettingstarted/cs/program.cs#12)]
 [!code-vb[CFX_WF_GettingStarted#12](~/samples/snippets/visualbasic/VS_Snippets_CFX/cfx_wf_gettingstarted/vb/module1.vb#12)]

## <a name="see-also"></a>Consulte também

- <xref:System.Activities.WorkflowApplication>
- <xref:System.Activities.Bookmark>
- [Programação do Windows Workflow Foundation](programming.md)
- [Tutorial de Introdução](getting-started-tutorial.md)
- [Como: Criar um fluxo de trabalho](how-to-create-a-workflow.md)
- [Como: Criar e executar uma longa em execução de fluxo de trabalho](how-to-create-and-run-a-long-running-workflow.md)
- [Esperando entrada em um fluxo de trabalho](waiting-for-input-in-a-workflow.md)
- [Hospedando fluxos de trabalho](hosting-workflows.md)
