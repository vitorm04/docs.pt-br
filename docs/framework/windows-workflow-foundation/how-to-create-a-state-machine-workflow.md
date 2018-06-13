---
title: Como criar um fluxo de trabalho de máquina de estado
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 3ec60e8f-fad4-493e-a426-e7962d7aee8c
ms.openlocfilehash: 00f764421d3caf44d853d26d76c6b6d872ab1e3d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33520023"
---
# <a name="how-to-create-a-state-machine-workflow"></a>Como criar um fluxo de trabalho de máquina de estado
Os fluxos de trabalho podem ser construídos a partir de atividades internas assim como as atividades personalizadas. Este tópico percorre criando um fluxo de trabalho que usa as duas atividades internas, como o <xref:System.Activities.Statements.StateMachine> atividade e as atividades personalizadas do anterior [como: criar uma atividade](../../../docs/framework/windows-workflow-foundation/how-to-create-an-activity.md) tópico. O fluxo de trabalho modela um jogo de palpite de número.  
  
> [!NOTE]
>  Cada tópico do tutorial de Introdução depende dos tópicos anteriores. Para concluir este tópico, você deve completar [como: criar uma atividade](../../../docs/framework/windows-workflow-foundation/how-to-create-an-activity.md).  
  
> [!NOTE]
>  Para baixar uma versão completa do tutorial, consulte [Windows Workflow Foundation (WF45) - Tutorial de Introdução](http://go.microsoft.com/fwlink/?LinkID=248976).  
  
### <a name="to-create-the-workflow"></a>Para criar o fluxo de trabalho  
  
1.  Clique com botão direito **NumberGuessWorkflowActivities** na **Solution Explorer** e selecione **adicionar**, **Novo Item**.  
  
2.  No **instalado**, **itens comuns** nó, selecione **fluxo de trabalho**. Selecione **atividade** do **fluxo de trabalho** lista.  
  
3.  Tipo `StateMachineNumberGuessWorkflow` para o **nome** caixa e clique em **adicionar**.  
  
4.  Arraste um **StateMachine** atividade do **máquina de estado** seção o **caixa de ferramentas** e solte-a para o **descartar atividade aqui** rótulo em a superfície de design de fluxo de trabalho.  
  
### <a name="to-create-the-workflow-variables-and-arguments"></a>Para criar as variáveis e os argumentos do fluxo de trabalho  
  
1.  Clique duas vezes em **StateMachineNumberGuessWorkflow.xaml** na **Solution Explorer** para exibir o fluxo de trabalho no designer, se ainda não estiver sendo exibida.  
  
2.  Clique em **argumentos** no lado inferior esquerdo do designer de fluxo de trabalho para exibir o **argumentos** painel.  
  
3.  Clique em **criar argumento**.  
  
4.  Tipo `MaxNumber` no **nome** caixa, selecione **na** do **direção** lista suspensa, selecione **Int32** da **Tipo de argumento** lista suspensa e, em seguida, pressione ENTER para salvar o argumento.  
  
5.  Clique em **criar argumento**.  
  
6.  Tipo `Turns` para o **nome** caixa abaixo recém-adicionado `MaxNumber` argumento, selecione **Out** do **direção** lista suspensa, selecione  **Int32** do **tipo de argumento** lista suspensa e, em seguida, pressione ENTER.  
  
7.  Clique em **argumentos** no lado inferior esquerdo do designer de atividade para fechar o **argumentos** painel.  
  
8.  Clique em **variáveis** no lado inferior esquerdo do designer de fluxo de trabalho para exibir o **variáveis** painel.  
  
9. Clique em **criar variável**.  
  
    > [!TIP]
    >  Se nenhum **criar variável** caixa é exibida, clique no <xref:System.Activities.Statements.StateMachine> atividade na superfície do designer de fluxo de trabalho para selecioná-la.  
  
10. Tipo `Guess` para o **nome** caixa, selecione **Int32** do **tipo de variável** lista suspensa e, em seguida, pressione ENTER para salvar a variável.  
  
11. Clique em **criar variável**.  
  
12. Tipo `Target` para o **nome** caixa, selecione **Int32** do **tipo de variável** lista suspensa e, em seguida, pressione ENTER para salvar a variável.  
  
13. Clique em **variáveis** no lado inferior esquerdo do designer de atividade para fechar o **variáveis** painel.  
  
### <a name="to-add-the-workflow-activities"></a>Para adicionar as atividades de fluxo de trabalho  
  
1.  Clique em **State1** para selecioná-la. No **janela propriedades**, altere o **DisplayName** para `Initialize Target`.  
  
    > [!TIP]
    >  Se o **janela propriedades** não é exibida, selecione **janela propriedades** do **exibição** menu.  
  
2.  Clique duas vezes em renomeada recentemente **destino inicializar** estado no designer de fluxo de trabalho para expandi-lo.  
  
3.  Arraste um **atribuir** atividade do **primitivos** seção o **caixa de ferramentas** e solte-a para o **entrada** seção do estado. Tipo `Target` no **para** caixa e a expressão a seguir para o **insira uma expressão de c#** ou **insira uma expressão VB** caixa.  
  
    ```vb  
    New System.Random().Next(1, MaxNumber + 1)  
    ```  
  
    ```csharp  
    new System.Random().Next(1, MaxNumber + 1)  
    ```  
  
    > [!TIP]
    >  Se o **caixa de ferramentas** janela não for exibida, selecione **caixa de ferramentas** do **exibição** menu.  
  
4.  Retornar ao geral exibição no designer de fluxo de trabalho de máquina de estado clicando **StateMachine** na navegação estrutural exibidas na parte superior do designer de fluxo de trabalho.  
  
5.  Arraste um **estado** atividade do **máquina de estado** seção o **caixa de ferramentas** para o designer de fluxo de trabalho e passe o mouse sobre o **destino inicializar** estado. Observe que os quatro triângulos aparecerá ao redor de **destino inicializar** estado quando o novo estado é sobre ele. Descarte o estado novo no triângulo que está imediatamente abaixo do **destino inicializar** estado. Isso coloca o novo estado para o fluxo de trabalho e cria uma transição do **destino inicializar** estado para o novo estado.  
  
6.  Clique em **State1** para selecioná-lo, altere o **DisplayName** para `Enter Guess`e, em seguida, clique duas vezes o estado no designer de fluxo de trabalho para expandi-lo.  
  
7.  Arraste um **WriteLine** atividade do **primitivos** seção o **caixa de ferramentas** e solte-a para o **entrada** seção do estado.  
  
8.  Digite a seguinte expressão para o **texto** caixa de propriedade do **WriteLine**.  
  
    ```vb  
    "Please enter a number between 1 and " & MaxNumber  
    ```  
  
    ```csharp  
    "Please enter a number between 1 and " + MaxNumber  
    ```  
  
9. Arraste um **atribuir** atividade do **primitivos** seção o **caixa de ferramentas** e solte o **saída** seção do estado.  
  
10. Tipo `Turns` para o **para** caixa e `Turns + 1` no **insira uma expressão de c#** ou **insira uma expressão VB** caixa.  
  
11. Retornar ao geral exibição no designer de fluxo de trabalho de máquina de estado clicando **StateMachine** na navegação estrutural exibidas na parte superior do designer de fluxo de trabalho.  
  
12. Arrastar um **FinalState** atividade do **máquina de estado** seção o **caixa de ferramentas**, passe o mouse sobre o **insira adivinhar** estado e solte-o para o triângulo que aparece à direita do **insira adivinhar** de estado para que seja criada uma transição entre **insira adivinhar** e **FinalState**.  
  
13. O nome padrão da transição é **T2**. Clique na transição no designer de fluxo de trabalho para selecioná-lo e definir seu **DisplayName** para **adivinhar correto**. Em seguida, clique em e selecione o **FinalState**e arraste-o para que haja espaço para o nome de transição completa a ser exibido sem sobreposição de qualquer um dos dois estados. Isso facilitará a conclusão das etapas restantes no tutorial.  
  
14. Clique duas vezes em renomeada recentemente **adivinhar correto** transição no designer de fluxo de trabalho para expandi-lo.  
  
15. Arraste um **ReadInt** atividade do **NumberGuessWorkflowActivities** seção o **caixa de ferramentas** e solte-o no **gatilho** seção da transição.  
  
16. No **janela propriedades** para o **ReadInt** atividade, digite `"EnterGuess"` incluindo as aspas para o **BookmarkName** caixa de valor de propriedade e digite `Guess`para o **resultados** caixa de valor de propriedade  
  
17. Digite a seguinte expressão para o **adivinhar correto** da transição **condição** caixa de valor de propriedade.  
  
    ```vb  
    Guess = Target  
    ```  
  
    ```csharp  
    Guess == Target  
    ```  
  
18. Retornar ao geral exibição no designer de fluxo de trabalho de máquina de estado clicando **StateMachine** na navegação estrutural exibidas na parte superior do designer de fluxo de trabalho.  
  
    > [!NOTE]
    >  Uma transição ocorre quando o evento de gatilho é recebido e o <xref:System.Activities.Statements.Transition.Condition%2A>, se houver, é avaliado como `True`. Para essa transição, se o usuário `Guess` corresponde gerado aleatoriamente `Target`, em seguida, o controle passará para o **FinalState** e conclui o fluxo de trabalho.  
  
19. Dependendo se a previsão está correta, o fluxo de trabalho deve fazer a transição para o **FinalState** ou de volta para o **insira estimativa** estado para tentar. Ambas as transições de compartilham o mesmo gatilho de espera para a estimativa do usuário ser recebida por meio de **ReadInt** atividade. Isso é chamado de uma transição compartilhada. Para criar uma transição compartilhada, clique no círculo que indica o início do **adivinhar correto** transição e arraste-o para o estado desejado. Nesse caso, a transição é uma transição interna, portanto, arraste o ponto inicial do **adivinhar correto** transição e solte-a novamente na parte inferior da **insira adivinhar** estado. Depois de criar a transição, selecione-a no designer de fluxo de trabalho e defina seu **DisplayName** propriedade **adivinhar incorreto**.  
  
    > [!NOTE]
    >  Transições compartilhadas também podem ser criadas de dentro do designer de transição clicando **adicionar compartilhado transição de gatilho** na parte inferior do designer de transição e, em seguida, selecionar o estado de destino desejado do  **Estados disponíveis para conexão** lista suspensa.  
  
    > [!NOTE]
    >  Observe que se <xref:System.Activities.Statements.Transition.Condition%2A> de uma transição for avaliada como `false` (ou todas as condições de uma transição do gatilho compartilhada for avaliada como `false`), a transição não ocorrerá e todos os gatilhos para todas as transições de estado serão reprogramados. Neste tutorial, essa situação não pode ocorrer devido à maneira como as condições são configuradas (temos ações específicas para se o palpite está correto ou incorreto).  
  
20. Clique duas vezes o **adivinhar incorreto** transição no designer de fluxo de trabalho para expandi-lo. Observe que o **gatilho** já está definido para o mesmo **ReadInt** atividade que foi usada o **adivinhar correto** transição.  
  
21. Digite a seguinte expressão para o **condição** caixa de valor de propriedade.  
  
    ```vb  
    Guess <> Target  
    ```  
  
    ```csharp  
    Guess != Target  
    ```  
  
22. Arraste um **se** atividade do **fluxo de controle** seção o **caixa de ferramentas** e solte-o no **ação** seção da transição.  
  
23. Digite a seguinte expressão para o **se** da atividade **condição** caixa de valor de propriedade.  
  
    ```
    Guess < Target  
    ```  
  
24. Arraste dois **WriteLine** atividades do **primitivos** seção o **caixa de ferramentas** e soltá-los para que um está no **, em seguida,** seção o **se** atividade e é no **Else** seção.  
  
25. Clique o **WriteLine** atividade no **, em seguida,** seção para selecioná-lo e, em seguida, digite a expressão a seguir para o **texto** caixa de valor de propriedade.  
  
    ```
    "Your guess is too low."  
    ```  
  
26. Clique o **WriteLine** atividade no **Else** seção para selecioná-lo e, em seguida, digite a expressão a seguir para o **texto** caixa de valor de propriedade.  
  
    ```
    "Your guess is too high."  
    ```  
  
27. Retornar ao geral exibição no designer de fluxo de trabalho de máquina de estado clicando **StateMachine** na navegação estrutural exibidas na parte superior do designer de fluxo de trabalho.  
  
     O exemplo a seguir ilustra o fluxo de trabalho concluído.  
  
     ![Fluxo de trabalho de máquina de estado concluído](../../../docs/framework/windows-workflow-foundation/media/wfstatemachinegettingstartedtutorialcomplete.JPG "WFStateMachineGettingStartedTutorialComplete")  
  
### <a name="to-build-the-workflow"></a>Para compilar o fluxo de trabalho  
  
1.  Pressione CTRL+SHIFT+B para criar a solução.  
  
     Para obter instruções sobre como executar o fluxo de trabalho, consulte o próximo tópico, [como: executar um fluxo de trabalho](../../../docs/framework/windows-workflow-foundation/how-to-run-a-workflow.md). Se você já tiver concluído a [como: executar um fluxo de trabalho](../../../docs/framework/windows-workflow-foundation/how-to-run-a-workflow.md) etapa com um estilo diferente de fluxo de trabalho e quiser executá-lo usando o fluxo de trabalho de máquina de estado desta etapa, vá para o [para compilar e executar o aplicativo](../../../docs/framework/windows-workflow-foundation/how-to-run-a-workflow.md#BKMK_ToRunTheApplication) seção [como: executar um fluxo de trabalho](../../../docs/framework/windows-workflow-foundation/how-to-run-a-workflow.md).  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Activities.Statements.Flowchart>  
 <xref:System.Activities.Statements.FlowDecision>  
 [Programação do Windows Workflow Foundation](../../../docs/framework/windows-workflow-foundation/programming.md)  
 [Criando fluxos de trabalho](../../../docs/framework/windows-workflow-foundation/designing-workflows.md)  
 [Tutorial de Introdução](../../../docs/framework/windows-workflow-foundation/getting-started-tutorial.md)  
 [Como criar uma atividade](../../../docs/framework/windows-workflow-foundation/how-to-create-an-activity.md)  
 [Como executar um fluxo de trabalho](../../../docs/framework/windows-workflow-foundation/how-to-run-a-workflow.md)
