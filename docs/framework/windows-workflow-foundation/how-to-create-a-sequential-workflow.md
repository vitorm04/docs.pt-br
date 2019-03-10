---
title: 'Como: Criar um fluxo de trabalho sequencial'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 5280e816-ae17-48c4-8de0-a1e6895dd8f0
ms.openlocfilehash: 2213d766435aaafbf37b8646a66ea3007bfcb734
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/09/2019
ms.locfileid: "57719631"
---
# <a name="how-to-create-a-sequential-workflow"></a>Como: Criar um fluxo de trabalho sequencial
Os fluxos de trabalho podem ser construídos a partir de atividades internas assim como as atividades personalizadas. Este tópico orienta a criação de um fluxo de trabalho usa atividades internas, como o <xref:System.Activities.Statements.Sequence> atividade e atividades personalizadas do anterior [como: Criar uma atividade](how-to-create-an-activity.md) tópico. O fluxo de trabalho modela um jogo de palpite de número.  
  
> [!NOTE]
>  Cada tópico do tutorial de Introdução depende dos tópicos anteriores. Para concluir este tópico, você deve primeiro concluir [como: Criar uma atividade](how-to-create-an-activity.md).  
  
> [!NOTE]
>  Para baixar uma versão completa do tutorial, consulte [Windows Workflow Foundation (WF45) - Tutorial de Introdução](https://go.microsoft.com/fwlink/?LinkID=248976).  
  
### <a name="to-create-the-workflow"></a>Para criar o fluxo de trabalho  
  
1.  Clique com botão direito **NumberGuessWorkflowActivities** na **Gerenciador de soluções** e selecione **Add**, **Novo Item**.  
  
2.  No **Installed**, **itens comuns** nó, selecione **fluxo de trabalho**. Selecione **atividade** da **fluxo de trabalho** lista.  
  
3.  Tipo de `SequentialNumberGuessWorkflow` para o **nome** caixa e clique em **Add**.  
  
4.  Arraste uma **sequência** a atividade do **fluxo de controle** seção o **caixa de ferramentas** e solte-o no **soltar atividade aqui** rótulos no superfície de design de fluxo de trabalho.  
  
### <a name="to-create-the-workflow-variables-and-arguments"></a>Para criar as variáveis e os argumentos do fluxo de trabalho  
  
1.  Clique duas vezes em **Sequentialnumberguessworkflow** na **Gerenciador de soluções** para exibir o fluxo de trabalho no designer, caso ainda não esteja sendo exibido.  
  
2.  Clique em **argumentos** no lado inferior esquerdo do designer de fluxo de trabalho para exibir o **argumentos** painel.  
  
3.  Clique em **criar argumento**.  
  
4.  Tipo `MaxNumber` para o **nome** caixa, selecione **no** do **direção** lista suspensa, selecione **Int32** da **Tipo de argumento** lista suspensa e pressione ENTER para salvar o argumento.  
  
5.  Clique em **criar argumento**.  
  
6.  Tipo `Turns` para o **nome** caixa abaixo recém-adicionada `MaxNumber` argumento, selecione **Out** do **direção** lista suspensa, selecione  **Int32** do **tipo de argumento** lista suspensa e pressione ENTER.  
  
7.  Clique em **argumentos** no lado inferior esquerdo do designer de atividade para fechar o **argumentos** painel.  
  
8.  Clique em **variáveis** no lado inferior esquerdo do designer de fluxo de trabalho para exibir o **variáveis** painel.  
  
9. Clique em **criar variável**.  
  
    > [!TIP]
    >  Se nenhum **criar variável** caixa é exibida, clique no **sequência** atividade na superfície do designer de fluxo de trabalho para selecioná-lo.  
  
10. Tipo `Guess` para o **nome** caixa, selecione **Int32** do **tipo de variável** lista suspensa e, em seguida, pressione ENTER para salvar a variável.  
  
11. Clique em **criar variável**.  
  
12. Tipo `Target` para o **nome** caixa, selecione **Int32** do **tipo de variável** lista suspensa e, em seguida, pressione ENTER para salvar a variável.  
  
13. Clique em **variáveis** no lado inferior esquerdo do designer de atividade para fechar o **variáveis** painel.  
  
### <a name="to-add-the-workflow-activities"></a>Para adicionar as atividades de fluxo de trabalho  
  
1.  Arraste uma **atribuir** a atividade do **primitivos** seção o **caixa de ferramentas** e solte-o no **sequência** atividade. Tipo `Target` para o **para** caixa e a seguinte expressão na **insira uma expressão c#** ou **insira uma expressão VB** caixa.  
  
    ```vb  
    New System.Random().Next(1, MaxNumber + 1)  
    ```  
  
    ```csharp  
    new System.Random().Next(1, MaxNumber + 1)  
    ```  
  
    > [!TIP]
    >  Se o **caixa de ferramentas** janela não for exibida, selecione **caixa de ferramentas** do **exibição** menu.  
  
2.  Arraste uma **DoWhile** a atividade do **fluxo de controle** seção o **caixa de ferramentas** e solte-o no fluxo de trabalho para que fique abaixo o **atribuir** atividade.  
  
3.  Digite a seguinte expressão para o **DoWhile** da atividade **condição** caixa do valor de propriedade.  
  
    ```vb  
    Guess <> Target  
    ```  
  
    ```csharp  
    Guess != Target  
    ```  
  
     Uma atividade <xref:System.Activities.Statements.DoWhile> executa suas atividades filho e avalia seu <xref:System.Activities.Statements.DoWhile.Condition%2A>. Se o <xref:System.Activities.Statements.DoWhile.Condition%2A> é avaliado como `True`, as atividades no <xref:System.Activities.Statements.DoWhile> são executadas novamente. Neste exemplo, o palpite do usuário será avaliado e o <xref:System.Activities.Statements.DoWhile> continuará até que a previsão esteja correta.  
  
4.  Arraste uma **Prompt** a atividade do **NumberGuessWorkflowActivities** seção o **caixa de ferramentas** e solte-o no **DoWhile** atividade na etapa anterior.  
  
5.  No **janela de propriedades**, tipo `"EnterGuess"` incluindo as aspas na **BookmarkName** caixa de valor de propriedade para o **Prompt** atividade. Tipo de `Guess` para o **resultado** caixa do valor de propriedade e digite a seguinte expressão na **texto** caixa da propriedade.  
  
    ```vb  
    "Please enter a number between 1 and " & MaxNumber  
    ```  
  
    ```csharp  
    "Please enter a number between 1 and " + MaxNumber  
    ```  
  
    > [!TIP]
    >  Se o **janela de propriedades** não for exibido, selecione **janela propriedades** do **exibição** menu.  
  
6.  Arraste um **atribuir** a atividade do **primitivos** seção o **caixa de ferramentas** e solte-o no **DoWhile** atividade para que ela siga a **Prompt** atividade.  
  
    > [!NOTE]
    >  Quando você solta o **atribuir** atividade, observe como o designer de fluxo de trabalho adiciona automaticamente uma **sequência** atividade para conter o **Prompt** recém-adicionada e atividade **Atribuir** atividade.  
  
7.  Tipo de `Turns` no **para** caixa e `Turns + 1` no **insira uma expressão c#** ou **insira uma expressão VB** caixa.  
  
8.  Arraste uma **se** a atividade do **fluxo de controle** seção o **caixa de ferramentas** e solte-o no **sequência** atividade para que ela siga a adicionados recentemente **atribuir** atividade.  
  
9. Digite a seguinte expressão para o **se** da atividade **condição** caixa do valor de propriedade.  
  
    ```vb  
    Guess <> Target  
    ```  
  
    ```csharp  
    Guess != Target  
    ```  
  
10. Arraste outro **se** atividade da **fluxo de controle** seção o **caixa de ferramentas** e solte-o no **, em seguida,** seção dos primeiros **Se** atividade.  
  
11. Digite a seguinte expressão na recém-adicionada **se** da atividade **condição** caixa do valor de propriedade.  
  
    ```
    Guess < Target  
    ```  
  
12. Arraste dois **WriteLine** atividades da **primitivos** seção do **caixa de ferramentas** e soltá-los de modo que uma esteja no **, em seguida,** seção recém-adicionada **se** atividade e outra esteja na **Else** seção.  
  
13. Clique o **WriteLine** atividade na **, em seguida,** seção para selecioná-lo e, em seguida, digite a seguinte expressão na **texto** caixa do valor de propriedade.  
  
    ```vb  
    "Your guess is too low."  
    ```  
  
14. Clique o **WriteLine** atividade na **Else** seção para selecioná-lo e, em seguida, digite a seguinte expressão na **texto** caixa do valor de propriedade.  
  
    ```vb  
    "Your guess is too high."  
    ```  
  
     O exemplo a seguir ilustra o fluxo de trabalho concluído.  
  
     ![Fluxo de trabalho sequencial concluído](./media/wfsequentialgettingstartedtutorialcomplete.JPG "WFSequentialGettingStartedTutorialComplete")  
  
### <a name="to-build-the-workflow"></a>Para compilar o fluxo de trabalho  
  
1.  Pressione CTRL+SHIFT+B para criar a solução.  
  
     Para obter instruções sobre como executar o fluxo de trabalho, consulte o próximo tópico, [como: Executar um fluxo de trabalho](how-to-run-a-workflow.md). Se você já tiver concluído o [como: Executar um fluxo de trabalho](how-to-run-a-workflow.md) passo a passo com um estilo diferente de fluxo de trabalho e quiser executá-lo usando o fluxo de trabalho sequencial dessa etapa, pule para a [para compilar e executar o aplicativo](how-to-run-a-workflow.md#BKMK_ToRunTheApplication) seção [como: Executar um fluxo de trabalho](how-to-run-a-workflow.md).  
  
## <a name="see-also"></a>Consulte também
- <xref:System.Activities.Statements.Flowchart>
- <xref:System.Activities.Statements.FlowDecision>
- [Programação do Windows Workflow Foundation](programming.md)
- [Criando fluxos de trabalho](designing-workflows.md)
- [Tutorial de Introdução](getting-started-tutorial.md)
- [Como: Criar uma atividade](how-to-create-an-activity.md)
- [Como: Executar um fluxo de trabalho](how-to-run-a-workflow.md)
