---
title: 'Como: criar um fluxo de trabalho sequencial'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 5280e816-ae17-48c4-8de0-a1e6895dd8f0
ms.openlocfilehash: d94843e696848010791b1e22d06e4852d35bc68e
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/27/2019
ms.locfileid: "70044415"
---
# <a name="how-to-create-a-sequential-workflow"></a>Como: criar um fluxo de trabalho sequencial

Os fluxos de trabalho podem ser construídos a partir de atividades internas assim como as atividades personalizadas. Este tópico percorre a criação de um fluxo de trabalho que usa atividades internas, como a <xref:System.Activities.Statements.Sequence> atividade, e as atividades personalizadas da seção [como: Criar um tópico](how-to-create-an-activity.md) de atividade. O fluxo de trabalho modela um jogo de palpite de número.

> [!NOTE]
> Cada tópico do tutorial de Introdução depende dos tópicos anteriores. Para concluir este tópico, você deve primeiro concluir [como: Crie uma atividade](how-to-create-an-activity.md).

> [!NOTE]
> Para baixar uma versão completa do tutorial, consulte [Windows Workflow Foundation (WF45) – introdução tutorial](https://go.microsoft.com/fwlink/?LinkID=248976).

## <a name="to-create-the-workflow"></a>Para criar o fluxo de trabalho

1. Clique com o botão direito do mouse em **NumberGuessWorkflowActivities** em **Gerenciador de soluções** e selecione **Adicionar**, **novo item**.

2. No nó **itens comuns** **instalados**, selecione fluxo de **trabalho**. Selecione **atividade** na lista **fluxo de trabalho** .

3. Digite `SequentialNumberGuessWorkflow` na caixa **nome** e clique em **Adicionar**.

4. Arraste uma atividade de **sequência** da seção **fluxo de controle** da **caixa de ferramentas** e solte-a no rótulo **soltar atividade aqui** na superfície de design do fluxo de trabalho.

## <a name="to-create-the-workflow-variables-and-arguments"></a>Para criar as variáveis e os argumentos do fluxo de trabalho

1. Clique duas vezes em **SequentialNumberGuessWorkflow. XAML** em **Gerenciador de soluções** para exibir o fluxo de trabalho no designer, se ele ainda não estiver sendo exibido.

2. Clique em **argumentos** no lado inferior esquerdo do designer de fluxo de trabalho para exibir o painel **argumentos** .

3. Clique em **criar argumento**.

4. Digite `MaxNumber` na caixa **nome** , selecione **em na** lista suspensa **direção** , selecione **Int32** na lista suspensa **tipo de argumento** e pressione ENTER para salvar o argumento...

5. Clique em **criar argumento**.

6. Digite `Turns` na caixa de **nome** que `MaxNumber` está abaixo do argumento recém-adicionado, selecione **fora** na lista suspensa **direção** , selecione **Int32** na lista suspensa tipo de **argumento** e, em seguida, pressione Enter.

7. Clique em **argumentos** no lado inferior esquerdo do designer de atividade para fechar o painel **argumentos** .

8. Clique em **variáveis** no lado inferior esquerdo do designer de fluxo de trabalho para exibir o painel **variáveis** .

9. Clique em **criar variável**.

    > [!TIP]
    > Se nenhuma caixa **criar variável** for exibida, clique na atividade **sequência** na superfície do designer de fluxo de trabalho para selecioná-la.

10. Digite `Guess` na caixa **nome** , selecione **Int32** na lista suspensa **tipo de variável** e pressione ENTER para salvar a variável.

11. Clique em **criar variável**.

12. Digite `Target` na caixa **nome** , selecione **Int32** na lista suspensa **tipo de variável** e pressione ENTER para salvar a variável.

13. Clique em **variáveis** no lado inferior esquerdo do designer de atividade para fechar o painel **variáveis** .

## <a name="to-add-the-workflow-activities"></a>Para adicionar as atividades de fluxo de trabalho

1. Arraste uma atividade **assign** da seção **primitivas** da caixa de **ferramentas** e solte-a na atividade **sequência** . Digite `Target` na caixa **para** e a expressão a seguir na caixa **Inserir uma C# expressão** ou **Inserir uma expressão VB** .

    ```vb
    New System.Random().Next(1, MaxNumber + 1)
    ```

    ```csharp
    new System.Random().Next(1, MaxNumber + 1)
    ```

    > [!TIP]
    > Se a janela **caixa de ferramentas** não for exibida, selecione caixa de **ferramentas** no menu **Exibir** .

2. Arraste uma atividade DoWhile da seção **fluxo de controle** da **caixa de ferramentas** e solte-a no fluxo de trabalho para que ela esteja abaixo da atividade **atribuir** .

3. Digite a expressão a seguir na caixa de valor da propriedade de **condição** DoWhile da atividade.

    ```vb
    Guess <> Target
    ```

    ```csharp
    Guess != Target
    ```

     Uma atividade <xref:System.Activities.Statements.DoWhile> executa suas atividades filho e avalia seu <xref:System.Activities.Statements.DoWhile.Condition%2A>. Se o <xref:System.Activities.Statements.DoWhile.Condition%2A> é avaliado como `True`, as atividades no <xref:System.Activities.Statements.DoWhile> são executadas novamente. Neste exemplo, o palpite do usuário será avaliado e o <xref:System.Activities.Statements.DoWhile> continuará até que a previsão esteja correta.

4. Arraste uma atividade de **prompt** da seção **NumberGuessWorkflowActivities** da **caixa de ferramentas** e solte-a na atividade DoWhile da etapa anterior.

5. Na **janela Propriedades**, digite `"EnterGuess"` incluindo as aspas na caixa valor da propriedade **BookmarkName** da atividade de **prompt** . Digite `Guess` na caixa valor da propriedade de **resultado** e digite a expressão a seguir na caixa de propriedade **texto** .

    ```vb
    "Please enter a number between 1 and " & MaxNumber
    ```

    ```csharp
    "Please enter a number between 1 and " + MaxNumber
    ```

    > [!TIP]
    > Se a **janela Propriedades** não for exibida, selecione **janela Propriedades** no menu **Exibir** .

6. Arraste uma atividade **atribuir** da seção **primitivos** da caixa de **ferramentas** e solte-a na atividade DoWhile para que ela siga a atividade de **prompt** .

    > [!NOTE]
    > Quando você remove a atividade **atribuir** , observe como o designer de fluxo de trabalho adiciona automaticamente uma atividade de **sequência** para conter a atividade de **prompt** e a atividade **assign** recém-adicionada.

7. Digite `Turns` na caixa **para** e `Turns + 1` na caixa **Inserir uma C# expressão** ou **Inserir uma expressão VB** .

8. Arraste uma atividade **If** da seção **fluxo de controle** da **caixa de ferramentas** e solte-a na atividade **sequência** para que ela siga a atividade **atribuir** recém adicionada.

9. Digite a expressão a seguir na caixa de valor da propriedade **condição** **If** da atividade.

    ```vb
    Guess <> Target
    ```

    ```csharp
    Guess != Target
    ```

10. Arraste outra atividade **If** da seção **fluxo de controle** da caixa de **ferramentas** e solte-a na seção **em seguida** da primeira atividade **If** .

11. Digite a expressão a seguir na caixa de valor da propriedade **condição** da atividade do recém-adicionado.

    ```
    Guess < Target
    ```

12. Arraste duas atividades **WriteLine** da seção **primitivas** da caixa de **ferramentas** e solte-as para que uma delas esteja na seção **em seguida** da atividade **se** adicionada recentemente, e outra esteja na seção **else** .

13. Clique na atividade **WriteLine** na seção **em seguida** para selecioná-la e digite a expressão a seguir na caixa valor da propriedade de **texto** .

    ```text
    "Your guess is too low."
    ```

14. Clique na atividade **WriteLine** na seção **else** para selecioná-la e digite a expressão a seguir na caixa valor da propriedade de **texto** .

    ```text
    "Your guess is too high."
    ```

     O exemplo a seguir ilustra o fluxo de trabalho concluído:

     ![Captura de tela que mostra o fluxo de trabalho Sequencial concluído.](./media/how-to-create-a-sequential-workflow/complete-sequential-workflow.jpg)

## <a name="to-build-the-workflow"></a>Para compilar o fluxo de trabalho

1. Pressione CTRL+SHIFT+B para criar a solução.

     Para obter instruções sobre como executar o fluxo de trabalho, consulte o próximo tópico [, como: Executar um fluxo](how-to-run-a-workflow.md)de trabalho. Se você já tiver concluído o [como: Execute uma etapa](how-to-run-a-workflow.md) de fluxo de trabalho com um estilo diferente de fluxo de trabalho e queira executá-lo usando o fluxo de trabalho Sequencial nesta etapa, pule para a seção [para compilar e executar o aplicativo](how-to-run-a-workflow.md#BKMK_ToRunTheApplication) de [como: Executar um fluxo](how-to-run-a-workflow.md)de trabalho.

## <a name="see-also"></a>Consulte também

- <xref:System.Activities.Statements.Flowchart>
- <xref:System.Activities.Statements.FlowDecision>
- [Programação do Windows Workflow Foundation](programming.md)
- [Criando fluxos de trabalho](designing-workflows.md)
- [Tutorial de Introdução](getting-started-tutorial.md)
- [Como: Criar uma atividade](how-to-create-an-activity.md)
- [Como: Executar um fluxo de trabalho](how-to-run-a-workflow.md)
