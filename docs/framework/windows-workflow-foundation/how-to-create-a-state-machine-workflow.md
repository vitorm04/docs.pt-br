---
title: 'Como: Criar um fluxo de trabalho de máquina de estado'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 3ec60e8f-fad4-493e-a426-e7962d7aee8c
ms.openlocfilehash: d3ec8c1b8c9b30a23dacabeb033d525c34709931
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/09/2019
ms.locfileid: "57708256"
---
# <a name="how-to-create-a-state-machine-workflow"></a>Como: Criar um fluxo de trabalho de máquina de estado
Os fluxos de trabalho podem ser construídos a partir de atividades internas assim como as atividades personalizadas. Este tópico orienta a criação de um fluxo de trabalho usa atividades internas, como o <xref:System.Activities.Statements.StateMachine> atividade e atividades personalizadas do anterior [como: Criar uma atividade](how-to-create-an-activity.md) tópico. O fluxo de trabalho modela um jogo de palpite de número.  
  
> [!NOTE]
>  Cada tópico do tutorial de Introdução depende dos tópicos anteriores. Para concluir este tópico, você deve primeiro concluir [como: Criar uma atividade](how-to-create-an-activity.md).  
  
> [!NOTE]
>  Para baixar uma versão completa do tutorial, consulte [Windows Workflow Foundation (WF45) - Tutorial de Introdução](https://go.microsoft.com/fwlink/?LinkID=248976).  
  
### <a name="to-create-the-workflow"></a>Para criar o fluxo de trabalho  
  
1.  Clique com botão direito **NumberGuessWorkflowActivities** na **Gerenciador de soluções** e selecione **Add**, **Novo Item**.  
  
2.  No **Installed**, **itens comuns** nó, selecione **fluxo de trabalho**. Selecione **atividade** da **fluxo de trabalho** lista.  
  
3.  Tipo de `StateMachineNumberGuessWorkflow` para o **nome** caixa e clique em **Add**.  
  
4.  Arraste uma **StateMachine** a atividade do **máquina de estado** seção o **caixa de ferramentas** e solte-o no **soltar atividade aqui** rótulos no a superfície de design de fluxo de trabalho.  
  
### <a name="to-create-the-workflow-variables-and-arguments"></a>Para criar as variáveis e os argumentos do fluxo de trabalho  
  
1.  Clique duas vezes em **Statemachinenumberguessworkflow** na **Gerenciador de soluções** para exibir o fluxo de trabalho no designer, caso ainda não esteja sendo exibido.  
  
2.  Clique em **argumentos** no lado inferior esquerdo do designer de fluxo de trabalho para exibir o **argumentos** painel.  
  
3.  Clique em **criar argumento**.  
  
4.  Tipo `MaxNumber` para o **nome** caixa, selecione **no** do **direção** lista suspensa, selecione **Int32** da **Tipo de argumento** lista suspensa e pressione ENTER para salvar o argumento.  
  
5.  Clique em **criar argumento**.  
  
6.  Tipo `Turns` para o **nome** caixa abaixo recém-adicionada `MaxNumber` argumento, selecione **Out** do **direção** lista suspensa, selecione  **Int32** do **tipo de argumento** lista suspensa e pressione ENTER.  
  
7.  Clique em **argumentos** no lado inferior esquerdo do designer de atividade para fechar o **argumentos** painel.  
  
8.  Clique em **variáveis** no lado inferior esquerdo do designer de fluxo de trabalho para exibir o **variáveis** painel.  
  
9. Clique em **criar variável**.  
  
    > [!TIP]
    >  Se nenhum **criar variável** caixa é exibida, clique no <xref:System.Activities.Statements.StateMachine> atividade na superfície do designer de fluxo de trabalho para selecioná-lo.  
  
10. Tipo `Guess` para o **nome** caixa, selecione **Int32** do **tipo de variável** lista suspensa e, em seguida, pressione ENTER para salvar a variável.  
  
11. Clique em **criar variável**.  
  
12. Tipo `Target` para o **nome** caixa, selecione **Int32** do **tipo de variável** lista suspensa e, em seguida, pressione ENTER para salvar a variável.  
  
13. Clique em **variáveis** no lado inferior esquerdo do designer de atividade para fechar o **variáveis** painel.  
  
### <a name="to-add-the-workflow-activities"></a>Para adicionar as atividades de fluxo de trabalho  
  
1.  Clique em **State1** para selecioná-lo. No **janela de propriedades**, altere o **DisplayName** para `Initialize Target`.  
  
    > [!TIP]
    >  Se o **janela de propriedades** não for exibido, selecione **janela propriedades** do **exibição** menu.  
  
2.  Clique duas vezes em recém-renomeada **inicializar destino** estado no designer de fluxo de trabalho para expandi-lo.  
  
3.  Arraste um **atribuir** a atividade do **primitivos** seção o **caixa de ferramentas** e solte-o no **entrada** seção do estado. Tipo `Target` para o **para** caixa e a seguinte expressão na **insira uma expressão c#** ou **insira uma expressão VB** caixa.  
  
    ```vb  
    New System.Random().Next(1, MaxNumber + 1)  
    ```  
  
    ```csharp  
    new System.Random().Next(1, MaxNumber + 1)  
    ```  
  
    > [!TIP]
    >  Se o **caixa de ferramentas** janela não for exibida, selecione **caixa de ferramentas** do **exibição** menu.  
  
4.  Retorne ao geral exibição no designer de fluxo de trabalho de máquina de estado clicando **StateMachine** na trilha exibir na parte superior do designer de fluxo de trabalho.  
  
5.  Arraste um **estado** atividade do **máquina de estado** seção o **caixa de ferramentas** para o designer de fluxo de trabalho e passe o mouse sobre o **inicializar destino** estado. Observe que quatro triângulos aparecerão em torno de **inicializar destino** estado quando o novo estado está sobre ele. Solte o novo estado no triângulo que está imediatamente abaixo de **inicializar destino** estado. Isso coloca o novo estado no fluxo de trabalho e cria uma transição do **inicializar destino** estado para o novo estado.  
  
6.  Clique em **State1** para selecioná-lo, alterar o **DisplayName** para `Enter Guess`e, em seguida, clique duas vezes o estado no designer de fluxo de trabalho para expandi-lo.  
  
7.  Arraste um **WriteLine** a atividade do **primitivos** seção o **caixa de ferramentas** e solte-o no **entrada** seção do estado.  
  
8.  Digite a seguinte expressão no **texto** da caixa da propriedade de **WriteLine**.  
  
    ```vb  
    "Please enter a number between 1 and " & MaxNumber  
    ```  
  
    ```csharp  
    "Please enter a number between 1 and " + MaxNumber  
    ```  
  
9. Arraste uma **atribuir** a atividade do **primitivos** seção do **caixa de ferramentas** e solte o **sair** seção do estado.  
  
10. Tipo de `Turns` no **para** caixa e `Turns + 1` no **insira uma expressão c#** ou **insira uma expressão VB** caixa.  
  
11. Retorne ao geral exibição no designer de fluxo de trabalho de máquina de estado clicando **StateMachine** na trilha exibir na parte superior do designer de fluxo de trabalho.  
  
12. Arraste um **FinalState** a atividade do **máquina de estado** seção o **caixa de ferramentas**, passe o mouse sobre o **Enter Guess** de estado e solte-o no triângulo que aparece à direita do **Enter Guess** de estado para que uma transição é criada entre **Enter Guess** e **FinalState**.  
  
13. É o nome padrão da transição **T2**. Clique na transição no designer de fluxo de trabalho para selecioná-lo e defina suas **DisplayName** à **Palpite correto**. Em seguida, clique e selecione o **FinalState**e arraste-o para a direita para que haja espaço para o nome completo da transição seja exibido sem sobrepor nenhum dos dois estados. Isso facilitará a conclusão das etapas restantes no tutorial.  
  
14. Clique duas vezes em recém-renomeada **Palpite correto** transição no designer de fluxo de trabalho para expandi-lo.  
  
15. Arraste uma **ReadInt** a atividade do **NumberGuessWorkflowActivities** seção o **caixa de ferramentas** e solte-o no **gatilho** seção da transição.  
  
16. No **janela de propriedades** para o **ReadInt** atividade, digite `"EnterGuess"` incluindo as aspas no **BookmarkName** caixa de valor de propriedade e digite `Guess`para o **resultado** caixa do valor de propriedade  
  
17. Digite a seguinte expressão para o **Palpite correto** da transição **condição** caixa do valor de propriedade.  
  
    ```vb  
    Guess = Target  
    ```  
  
    ```csharp  
    Guess == Target  
    ```  
  
18. Retorne ao geral exibição no designer de fluxo de trabalho de máquina de estado clicando **StateMachine** na trilha exibir na parte superior do designer de fluxo de trabalho.  
  
    > [!NOTE]
    >  Uma transição ocorre quando o evento de gatilho é recebido e o <xref:System.Activities.Statements.Transition.Condition%2A>, se houver, é avaliado como `True`. Para essa transição, se o usuário `Guess` corresponde gerado aleatoriamente `Target`, em seguida, o controle passa para o **FinalState** e o fluxo de trabalho é concluído.  
  
19. Dependendo se o Palpite está correto, o fluxo de trabalho deve fazer a transição para o **FinalState** ou de volta para o **Enter Guess** estado para outra tentativa. Ambas as transições compartilham o mesmo gatilho de esperar o palpite do usuário ser recebida por meio de **ReadInt** atividade. Isso é chamado de uma transição compartilhada. Para criar uma transição compartilhada, clique no círculo que indica o início do **Palpite correto** transição e arraste-o para o estado desejado. Nesse caso, a transição é automática, então, arraste o ponto inicial do **Palpite correto** fazer a transição e solte-a novamente na parte inferior da **Enter Guess** estado. Depois de criar a transição, selecione-a no designer de fluxo de trabalho e defina suas **DisplayName** propriedade **Palpite incorreto**.  
  
    > [!NOTE]
    >  As transições compartilhadas também podem ser criadas de dentro do designer de transição clicando **adicionar transição de gatilho de compartilhado** na parte inferior do designer de transição e, em seguida, selecionando o estado do destino desejado do  **Estados disponíveis para conectar-se** lista suspensa.  
  
    > [!NOTE]
    >  Observe que se <xref:System.Activities.Statements.Transition.Condition%2A> de uma transição for avaliada como `false` (ou todas as condições de uma transição do gatilho compartilhada for avaliada como `false`), a transição não ocorrerá e todos os gatilhos para todas as transições de estado serão reprogramados. Neste tutorial, essa situação não pode ocorrer devido à maneira como as condições são configuradas (temos ações específicas para se o palpite está correto ou incorreto).  
  
20. Clique duas vezes o **Palpite incorreto** transição no designer de fluxo de trabalho para expandi-lo. Observe que o **disparador** já está definido como o mesmo **ReadInt** atividade que foi usada pelo **Palpite correto** transição.  
  
21. Digite a seguinte expressão para o **condição** caixa do valor de propriedade.  
  
    ```vb  
    Guess <> Target  
    ```  
  
    ```csharp  
    Guess != Target  
    ```  
  
22. Arraste uma **se** a atividade do **fluxo de controle** seção o **caixa de ferramentas** e solte-o no **ação** seção da transição.  
  
23. Digite a seguinte expressão para o **se** da atividade **condição** caixa do valor de propriedade.  
  
    ```
    Guess < Target  
    ```  
  
24. Arraste dois **WriteLine** atividades da **primitivos** seção do **caixa de ferramentas** e soltá-los de modo que uma esteja no **, em seguida,** seção o **se** atividade e outra esteja na **Else** seção.  
  
25. Clique o **WriteLine** atividade na **, em seguida,** seção para selecioná-lo e, em seguida, digite a seguinte expressão na **texto** caixa do valor de propriedade.  
  
    ```
    "Your guess is too low."  
    ```  
  
26. Clique o **WriteLine** atividade na **Else** seção para selecioná-lo e, em seguida, digite a seguinte expressão na **texto** caixa do valor de propriedade.  
  
    ```
    "Your guess is too high."  
    ```  
  
27. Retorne ao geral exibição no designer de fluxo de trabalho de máquina de estado clicando **StateMachine** na trilha exibir na parte superior do designer de fluxo de trabalho.  
  
     O exemplo a seguir ilustra o fluxo de trabalho concluído.  
  
     ![Fluxo de trabalho de máquina de estado concluído](./media/wfstatemachinegettingstartedtutorialcomplete.JPG "WFStateMachineGettingStartedTutorialComplete")  
  
### <a name="to-build-the-workflow"></a>Para compilar o fluxo de trabalho  
  
1.  Pressione CTRL+SHIFT+B para criar a solução.  
  
     Para obter instruções sobre como executar o fluxo de trabalho, consulte o próximo tópico, [como: Executar um fluxo de trabalho](how-to-run-a-workflow.md). Se você já tiver concluído o [como: Executar um fluxo de trabalho](how-to-run-a-workflow.md) passo a passo com um estilo diferente de fluxo de trabalho e quiser executá-lo usando o fluxo de trabalho de máquina de estado dessa etapa, pule para a [para compilar e executar o aplicativo](how-to-run-a-workflow.md#BKMK_ToRunTheApplication) seção [como: Executar um fluxo de trabalho](how-to-run-a-workflow.md).  
  
## <a name="see-also"></a>Consulte também
- <xref:System.Activities.Statements.Flowchart>
- <xref:System.Activities.Statements.FlowDecision>
- [Programação do Windows Workflow Foundation](programming.md)
- [Criando fluxos de trabalho](designing-workflows.md)
- [Tutorial de Introdução](getting-started-tutorial.md)
- [Como: Criar uma atividade](how-to-create-an-activity.md)
- [Como: Executar um fluxo de trabalho](how-to-run-a-workflow.md)
