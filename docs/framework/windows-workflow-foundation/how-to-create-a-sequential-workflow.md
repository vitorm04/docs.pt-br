---
title: Como criar um fluxo de trabalho sequencial
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 5280e816-ae17-48c4-8de0-a1e6895dd8f0
ms.openlocfilehash: d7379e6e4d24ccc23d57486c3271c482a7f17edd
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33519396"
---
# <a name="how-to-create-a-sequential-workflow"></a>Como criar um fluxo de trabalho sequencial
Os fluxos de trabalho podem ser construídos a partir de atividades internas assim como as atividades personalizadas. Este tópico percorre criando um fluxo de trabalho que usa as duas atividades internas, como o <xref:System.Activities.Statements.Sequence> atividade e as atividades personalizadas do anterior [como: criar uma atividade](../../../docs/framework/windows-workflow-foundation/how-to-create-an-activity.md) tópico. O fluxo de trabalho modela um jogo de palpite de número.  
  
> [!NOTE]
>  Cada tópico do tutorial de Introdução depende dos tópicos anteriores. Para concluir este tópico, você deve completar [como: criar uma atividade](../../../docs/framework/windows-workflow-foundation/how-to-create-an-activity.md).  
  
> [!NOTE]
>  Para baixar uma versão completa do tutorial, consulte [Windows Workflow Foundation (WF45) - Tutorial de Introdução](http://go.microsoft.com/fwlink/?LinkID=248976).  
  
### <a name="to-create-the-workflow"></a>Para criar o fluxo de trabalho  
  
1.  Clique com botão direito **NumberGuessWorkflowActivities** na **Solution Explorer** e selecione **adicionar**, **Novo Item**.  
  
2.  No **instalado**, **itens comuns** nó, selecione **fluxo de trabalho**. Selecione **atividade** do **fluxo de trabalho** lista.  
  
3.  Tipo `SequentialNumberGuessWorkflow` para o **nome** caixa e clique em **adicionar**.  
  
4.  Arraste um **sequência** atividade do **fluxo de controle** seção o **caixa de ferramentas** e solte-a para o **descartar atividade aqui** rótulo no superfície de design de fluxo de trabalho.  
  
### <a name="to-create-the-workflow-variables-and-arguments"></a>Para criar as variáveis e os argumentos do fluxo de trabalho  
  
1.  Clique duas vezes em **SequentialNumberGuessWorkflow.xaml** na **Solution Explorer** para exibir o fluxo de trabalho no designer, se ainda não estiver sendo exibida.  
  
2.  Clique em **argumentos** no lado inferior esquerdo do designer de fluxo de trabalho para exibir o **argumentos** painel.  
  
3.  Clique em **criar argumento**.  
  
4.  Tipo `MaxNumber` no **nome** caixa, selecione **na** do **direção** lista suspensa, selecione **Int32** da **Tipo de argumento** lista suspensa e, em seguida, pressione ENTER para salvar o argumento.  
  
5.  Clique em **criar argumento**.  
  
6.  Tipo `Turns` para o **nome** caixa abaixo recém-adicionado `MaxNumber` argumento, selecione **Out** do **direção** lista suspensa, selecione  **Int32** do **tipo de argumento** lista suspensa e, em seguida, pressione ENTER.  
  
7.  Clique em **argumentos** no lado inferior esquerdo do designer de atividade para fechar o **argumentos** painel.  
  
8.  Clique em **variáveis** no lado inferior esquerdo do designer de fluxo de trabalho para exibir o **variáveis** painel.  
  
9. Clique em **criar variável**.  
  
    > [!TIP]
    >  Se nenhum **criar variável** caixa é exibida, clique no **sequência** atividade na superfície do designer de fluxo de trabalho para selecioná-la.  
  
10. Tipo `Guess` para o **nome** caixa, selecione **Int32** do **tipo de variável** lista suspensa e, em seguida, pressione ENTER para salvar a variável.  
  
11. Clique em **criar variável**.  
  
12. Tipo `Target` para o **nome** caixa, selecione **Int32** do **tipo de variável** lista suspensa e, em seguida, pressione ENTER para salvar a variável.  
  
13. Clique em **variáveis** no lado inferior esquerdo do designer de atividade para fechar o **variáveis** painel.  
  
### <a name="to-add-the-workflow-activities"></a>Para adicionar as atividades de fluxo de trabalho  
  
1.  Arraste um **atribuir** atividade do **primitivos** seção o **caixa de ferramentas** e solte-a para o **sequência** atividade. Tipo `Target` no **para** caixa e a expressão a seguir para o **insira uma expressão de c#** ou **insira uma expressão VB** caixa.  
  
    ```vb  
    New System.Random().Next(1, MaxNumber + 1)  
    ```  
  
    ```csharp  
    new System.Random().Next(1, MaxNumber + 1)  
    ```  
  
    > [!TIP]
    >  Se o **caixa de ferramentas** janela não for exibida, selecione **caixa de ferramentas** do **exibição** menu.  
  
2.  Arraste um **DoWhile** atividade do **fluxo de controle** seção o **caixa de ferramentas** e solte-o no fluxo de trabalho para que ele fique abaixo o **atribuir** atividade.  
  
3.  Digite a seguinte expressão para o **DoWhile** da atividade **condição** caixa de valor de propriedade.  
  
    ```vb  
    Guess <> Target  
    ```  
  
    ```csharp  
    Guess != Target  
    ```  
  
     Uma atividade <xref:System.Activities.Statements.DoWhile> executa suas atividades filho e avalia seu <xref:System.Activities.Statements.DoWhile.Condition%2A>. Se o <xref:System.Activities.Statements.DoWhile.Condition%2A> é avaliado como `True`, as atividades no <xref:System.Activities.Statements.DoWhile> são executadas novamente. Neste exemplo, o palpite do usuário será avaliado e o <xref:System.Activities.Statements.DoWhile> continuará até que a previsão esteja correta.  
  
4.  Arraste um **Prompt** atividade do **NumberGuessWorkflowActivities** seção o **caixa de ferramentas** e solte-o no **DoWhile** atividade na etapa anterior.  
  
5.  No **janela propriedades**, tipo `"EnterGuess"` incluindo as aspas para o **BookmarkName** caixa de valor de propriedade para o **Prompt** atividade. Tipo `Guess` no **resultados** propriedade valor caixa e digite a seguinte expressão para o **texto** caixa da propriedade.  
  
    ```vb  
    "Please enter a number between 1 and " & MaxNumber  
    ```  
  
    ```csharp  
    "Please enter a number between 1 and " + MaxNumber  
    ```  
  
    > [!TIP]
    >  Se o **janela propriedades** não é exibida, selecione **janela propriedades** do **exibição** menu.  
  
6.  Arraste um **atribuir** atividade do **primitivos** seção o **caixa de ferramentas** e solte-o no **DoWhile** atividade para que ela siga a **Prompt** atividade.  
  
    > [!NOTE]
    >  Quando você solta o **atribuir** atividade, observe como o designer de fluxo de trabalho adiciona automaticamente um **sequência** atividade para conter o **Prompt** recém-adicionado e atividade **Atribuir** atividade.  
  
7.  Tipo `Turns` para o **para** caixa e `Turns + 1` no **insira uma expressão de c#** ou **insira uma expressão VB** caixa.  
  
8.  Arraste um **se** atividade do **fluxo de controle** seção o **caixa de ferramentas** e solte-o no **sequência** atividade para que ela siga a adicionado recentemente **atribuir** atividade.  
  
9. Digite a seguinte expressão para o **se** da atividade **condição** caixa de valor de propriedade.  
  
    ```vb  
    Guess <> Target  
    ```  
  
    ```csharp  
    Guess != Target  
    ```  
  
10. Arraste outro **se** atividade do **fluxo de controle** seção o **caixa de ferramentas** e solte-o no **, em seguida,** seção do primeiro **Se** atividade.  
  
11. Digite a expressão a seguir na recém-adicionada **se** da atividade **condição** caixa de valor de propriedade.  
  
    ```
    Guess < Target  
    ```  
  
12. Arraste dois **WriteLine** atividades do **primitivos** seção o **caixa de ferramentas** e soltá-los para que um está no **, em seguida,** seção recém-adicionado **se** atividade e é no **Else** seção.  
  
13. Clique o **WriteLine** atividade no **, em seguida,** seção para selecioná-lo e, em seguida, digite a expressão a seguir para o **texto** caixa de valor de propriedade.  
  
    ```vb  
    "Your guess is too low."  
    ```  
  
14. Clique o **WriteLine** atividade no **Else** seção para selecioná-lo e, em seguida, digite a expressão a seguir para o **texto** caixa de valor de propriedade.  
  
    ```vb  
    "Your guess is too high."  
    ```  
  
     O exemplo a seguir ilustra o fluxo de trabalho concluído.  
  
     ![Fluxo de trabalho sequencial concluído](../../../docs/framework/windows-workflow-foundation/media/wfsequentialgettingstartedtutorialcomplete.JPG "WFSequentialGettingStartedTutorialComplete")  
  
### <a name="to-build-the-workflow"></a>Para compilar o fluxo de trabalho  
  
1.  Pressione CTRL+SHIFT+B para criar a solução.  
  
     Para obter instruções sobre como executar o fluxo de trabalho, consulte o próximo tópico, [como: executar um fluxo de trabalho](../../../docs/framework/windows-workflow-foundation/how-to-run-a-workflow.md). Se você já tiver concluído a [como: executar um fluxo de trabalho](../../../docs/framework/windows-workflow-foundation/how-to-run-a-workflow.md) etapa com um estilo diferente de fluxo de trabalho e quiser executá-lo usando o fluxo de trabalho sequencial desta etapa, vá para o [para compilar e executar o aplicativo](../../../docs/framework/windows-workflow-foundation/how-to-run-a-workflow.md#BKMK_ToRunTheApplication)seção [como: executar um fluxo de trabalho](../../../docs/framework/windows-workflow-foundation/how-to-run-a-workflow.md).  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Activities.Statements.Flowchart>  
 <xref:System.Activities.Statements.FlowDecision>  
 [Programação do Windows Workflow Foundation](../../../docs/framework/windows-workflow-foundation/programming.md)  
 [Criando fluxos de trabalho](../../../docs/framework/windows-workflow-foundation/designing-workflows.md)  
 [Tutorial de Introdução](../../../docs/framework/windows-workflow-foundation/getting-started-tutorial.md)  
 [Como criar uma atividade](../../../docs/framework/windows-workflow-foundation/how-to-create-an-activity.md)  
 [Como executar um fluxo de trabalho](../../../docs/framework/windows-workflow-foundation/how-to-run-a-workflow.md)
