---
title: Como criar um fluxo de trabalho de fluxograma
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 185d7aea-68a6-4bd8-adde-45050f33170a
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 3df93a876522ccdc001bc3f6bc8c780bc80dc21b
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/02/2017
---
# <a name="how-to-create-a-flowchart-workflow"></a>Como criar um fluxo de trabalho de fluxograma
Os fluxos de trabalho podem ser construídos a partir de atividades internas assim como as atividades personalizadas. Este tópico percorre criando um fluxo de trabalho que usa as duas atividades internas, como o <xref:System.Activities.Statements.Flowchart> atividade e as atividades personalizadas do anterior [como: criar uma atividade](../../../docs/framework/windows-workflow-foundation/how-to-create-an-activity.md) tópico. O fluxo de trabalho modela um jogo de palpite de número.  
  
> [!NOTE]
>  Cada tópico do tutorial de Introdução depende dos tópicos anteriores. Para concluir este tópico, você deve completar [como: criar uma atividade](../../../docs/framework/windows-workflow-foundation/how-to-create-an-activity.md).  
  
> [!NOTE]
>  Para baixar uma versão completa do tutorial, consulte [Windows Workflow Foundation (WF45) - Tutorial de Introdução](http://go.microsoft.com/fwlink/?LinkID=248976).  
  
### <a name="to-create-the-workflow"></a>Para criar o fluxo de trabalho  
  
1.  Clique com botão direito **NumberGuessWorkflowActivities** na **Solution Explorer** e selecione **adicionar**, **Novo Item**.  
  
2.  No **instalado**, **itens comuns** nó, selecione **fluxo de trabalho**. Selecione **atividade** do **fluxo de trabalho** lista.  
  
3.  Tipo `FlowchartNumberGuessWorkflow` para o **nome** caixa e clique em **adicionar**.  
  
4.  Arraste um **fluxograma** atividade do **fluxograma** seção o **caixa de ferramentas** e solte-a para o **descartar atividade aqui** rótulo no superfície de design de fluxo de trabalho.  
  
### <a name="to-create-the-workflow-variables-and-arguments"></a>Para criar as variáveis e os argumentos do fluxo de trabalho  
  
1.  Clique duas vezes em **FlowchartNumberGuessWorkflow.xaml** na **Solution Explorer** para exibir o fluxo de trabalho no designer, se ainda não estiver sendo exibida.  
  
2.  Clique em **argumentos** no lado inferior esquerdo do designer de fluxo de trabalho para exibir o **argumentos** painel.  
  
3.  Clique em **criar argumento**.  
  
4.  Tipo `MaxNumber` no **nome** caixa, selecione **na** do **direção** lista suspensa, selecione **Int32** da **Tipo de argumento** lista suspensa e, em seguida, pressione ENTER para salvar o argumento.  
  
5.  Clique em **criar argumento**.  
  
6.  Tipo `Turns` para o **nome** caixa abaixo recém-adicionado `MaxNumber` argumento, selecione **Out** do **direção** lista suspensa, selecione  **Int32** do **tipo de argumento** lista suspensa e, em seguida, pressione ENTER.  
  
7.  Clique em **argumentos** no lado inferior esquerdo do designer de atividade para fechar o **argumentos** painel.  
  
8.  Clique em **variáveis** no lado inferior esquerdo do designer de fluxo de trabalho para exibir o **variáveis** painel.  
  
9. Clique em **criar variável**.  
  
    > [!TIP]
    >  Se nenhum **criar variável** caixa é exibida, clique no <xref:System.Activities.Statements.Flowchart> atividade na superfície do designer de fluxo de trabalho para selecioná-la.  
  
10. Tipo `Guess` para o **nome** caixa, selecione **Int32** do **tipo de variável** lista suspensa e, em seguida, pressione ENTER para salvar a variável.  
  
11. Clique em **criar variável**.  
  
12. Tipo `Target` para o **nome** caixa, selecione **Int32** do **tipo de variável** lista suspensa e, em seguida, pressione ENTER para salvar a variável.  
  
13. Clique em **variáveis** no lado inferior esquerdo do designer de atividade para fechar o **variáveis** painel.  
  
### <a name="to-add-the-workflow-activities"></a>Para adicionar as atividades de fluxo de trabalho  
  
1.  Arraste um **atribuir** atividade do **primitivos** seção o **caixa de ferramentas** e passe o mouse sobre o **iniciar** nó, que está no topo do fluxograma. Quando o **atribuir** atividade está sobre o **iniciar** nó, três triângulos aparecerá ao redor o **iniciar** nó. Descartar o **atribuir** atividade no triângulo que está diretamente abaixo do **iniciar** nó. Isso vinculará os dois itens juntos e designa o **atribuir** atividade como a primeira atividade do fluxograma.  
  
    > [!NOTE]
    >  As atividades também podem ser indicadas como a atividade de início no fluxo de trabalho manualmente vinculando-as ao nó de origem. Para fazer isso, passe o mouse sobre o **iniciar** nó, clique em um dos retângulos que aparecem quando o mouse estiver sobre o **iniciar** nó e arraste a conexão de linha para baixo até a atividade desejada e solte-o em um dos os retângulos que aparecem. Você também pode designar e atividade como a atividade inicial clicando duas vezes o it e escolhendo **definido como nó iniciar**.  
  
2.  Tipo `Target` no **para** caixa e a expressão a seguir para o **insira uma expressão de c#** ou **insira uma expressão VB** caixa.  
  
    ```vb  
    New System.Random().Next(1, MaxNumber + 1)  
    ```  
  
    ```csharp  
    new System.Random().Next(1, MaxNumber + 1)  
    ```  
  
    > [!TIP]
    >  Se o **caixa de ferramentas** janela não for exibida, selecione **caixa de ferramentas** do **exibição** menu.  
  
3.  Arrastar um **Prompt** atividade do **NumberGuessWorkflowActivities** seção o **caixa de ferramentas**, solte-o abaixo de **atribuir** atividade do anterior etapa e conecte-se a **Prompt** atividade para o **atribuir** atividade. Há três modos de conectar as duas atividades. O primeiro modo é para conectá-los como você descartar o **Prompt** atividade no fluxo de trabalho. Como você está arrastando o **Prompt** atividade ao fluxo de trabalho, o focalize o **atribuir** atividade e solte-a para um dos quatro triângulos que aparecem quando o **Prompt** atividade está sobre o **atribuir** atividade. A segunda maneira é remover o **Prompt** atividade no fluxo de trabalho no local desejado. Em seguida, passe o mouse sobre o **atribuir** atividade e arraste um dos retângulos que aparece para o **Prompt** atividade. Arraste o mouse para que a conexão de linha do **atribuir** atividade se conecta a um dos retângulos do **Prompt** atividade e, em seguida, solte o botão do mouse. A terceira maneira é muito semelhante à forma como primeiro, exceto que, em vez de arrastar o **Prompt** atividade a partir de **caixa de ferramentas**, arraste-o de seu local na superfície de design de fluxo de trabalho, passe o mouse sobre o  **Atribuir** atividade e soltá-lo em uma de triângulos que aparece.  
  
4.  No **janela propriedades** para o **Prompt** atividade, digite `"EnterGuess"` incluindo as aspas no **BookmarkName** caixa de valor de propriedade. Tipo `Guess` no **resultados** propriedade valor caixa e digite a seguinte expressão para o **texto** caixa da propriedade.  
  
    ```vb  
    "Please enter a number between 1 and " & MaxNumber  
    ```  
  
    ```csharp  
    "Please enter a number between 1 and " + MaxNumber  
    ```  
  
    > [!TIP]
    >  Se o **janela propriedades** não é exibida, selecione **janela propriedades** do **exibição** menu.  
  
5.  Arraste um **atribuir** atividade do **primitivos** seção o **caixa de ferramentas** e conectá-lo usando um dos métodos descritos na etapa anterior para que ele fique abaixo do  **Prompt** atividade.  
  
6.  Tipo `Turns` para o **para** caixa e `Turns + 1` no **insira uma expressão de c#** ou **insira uma expressão VB** caixa.  
  
7.  Arraste um **FlowDecision** do **fluxograma** seção do **caixa de ferramentas** e conecte-o abaixo de **atribuir** atividade. No **janela propriedades**, digite a seguinte expressão para o **condição** caixa de valor de propriedade.  
  
    ```vb  
    Guess = Target  
    ```  
  
    ```csharp  
    Guess == Target  
    ```  
  
8.  Arraste outro **FlowDecision** atividade a partir de **caixa de ferramentas** e solte-o abaixo do primeiro. Conecte as duas atividades, arrastando do retângulo que é rotulado **False** na parte superior **FlowDecision** atividade para o retângulo na parte superior da segunda **FlowDecision**atividade.  
  
    > [!TIP]
    >  Se você não vir o **True** e **False** rótulos no **FlowDecision**, passe o mouse sobre o **FlowDecision**.  
  
9. Clique no segundo **FlowDecision** atividade para selecioná-la. No **janela propriedades**, digite a seguinte expressão para o **condição** caixa de valor de propriedade.  
  
    ```
    Guess < Target  
    ```  
  
10. Arraste dois **WriteLine** atividades do **primitivos** seção o **caixa de ferramentas** e soltá-los para que fiquem lado a lado abaixo os dois **FlowDecision**  atividades. Conecte-se a **True** ação da parte inferior **FlowDecision** atividade para a esquerda **WriteLine** atividade e o **False** ação para o mais à direita **WriteLine** atividade.  
  
11. Clique em mais à esquerda **WriteLine** atividade para selecioná-lo e digite a expressão a seguir para o **texto** caixa valor da propriedade o **janela propriedades**.  
  
    ```
    "Your guess is too low."  
    ```  
  
12. Conecte-se a **WriteLine** para o lado esquerdo do **Prompt** atividade acima dele.  
  
13. Clique em mais à direita **WriteLine** atividade para selecioná-lo e digite a seguinte expressão no **texto** caixa valor da propriedade de **janela propriedades**.  
  
    ```
    "Your guess is too high."  
    ```  
  
14. Conecte-se a **WriteLine** à direita da atividade a **Prompt** atividade acima dele.  
  
     O exemplo a seguir ilustra o fluxo de trabalho concluído.  
  
     ![Concluído o Windows Workflow Foundation](../../../docs/framework/windows-workflow-foundation/media/gettingstartedtutorialcompletedflowchart.PNG "GettingStartedTutorialCompletedFlowchart")  
  
### <a name="to-build-the-workflow"></a>Para compilar o fluxo de trabalho  
  
1.  Pressione CTRL+SHIFT+B para criar a solução.  
  
     Para obter instruções sobre como executar o fluxo de trabalho, consulte o próximo tópico, [como: executar um fluxo de trabalho](../../../docs/framework/windows-workflow-foundation/how-to-run-a-workflow.md). Se você já tiver concluído a [como: executar um fluxo de trabalho](../../../docs/framework/windows-workflow-foundation/how-to-run-a-workflow.md) etapa com um estilo diferente de fluxo de trabalho e quiser executá-lo usando o fluxo de trabalho do fluxograma desta etapa, vá para o [para compilar e executar o aplicativo](../../../docs/framework/windows-workflow-foundation/how-to-run-a-workflow.md#BKMK_ToRunTheApplication)seção [como: executar um fluxo de trabalho](../../../docs/framework/windows-workflow-foundation/how-to-run-a-workflow.md).  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Activities.Statements.Flowchart>  
 <xref:System.Activities.Statements.FlowDecision>  
 [Programação do Windows Workflow Foundation](../../../docs/framework/windows-workflow-foundation/programming.md)  
 [Criando fluxos de trabalho](../../../docs/framework/windows-workflow-foundation/designing-workflows.md)  
 [Tutorial de Introdução](../../../docs/framework/windows-workflow-foundation/getting-started-tutorial.md)  
 [Como criar uma atividade](../../../docs/framework/windows-workflow-foundation/how-to-create-an-activity.md)  
 [Como executar um fluxo de trabalho](../../../docs/framework/windows-workflow-foundation/how-to-run-a-workflow.md)
