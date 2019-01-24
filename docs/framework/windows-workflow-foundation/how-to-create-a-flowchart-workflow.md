---
title: 'Como: Criar um fluxo de trabalho de fluxograma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 185d7aea-68a6-4bd8-adde-45050f33170a
ms.openlocfilehash: b8de9852a29c9cc20e2c607506ae3d804e6d406e
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54569973"
---
# <a name="how-to-create-a-flowchart-workflow"></a>Como: Criar um fluxo de trabalho de fluxograma
Os fluxos de trabalho podem ser construídos a partir de atividades internas assim como as atividades personalizadas. Este tópico orienta a criação de um fluxo de trabalho usa atividades internas, como o <xref:System.Activities.Statements.Flowchart> atividade e atividades personalizadas do anterior [como: Criar uma atividade](../../../docs/framework/windows-workflow-foundation/how-to-create-an-activity.md) tópico. O fluxo de trabalho modela um jogo de palpite de número.  
  
> [!NOTE]
>  Cada tópico do tutorial de Introdução depende dos tópicos anteriores. Para concluir este tópico, você deve primeiro concluir [como: Criar uma atividade](../../../docs/framework/windows-workflow-foundation/how-to-create-an-activity.md).  
  
> [!NOTE]
>  Para baixar uma versão completa do tutorial, consulte [Windows Workflow Foundation (WF45) - Tutorial de Introdução](https://go.microsoft.com/fwlink/?LinkID=248976).  
  
### <a name="to-create-the-workflow"></a>Para criar o fluxo de trabalho  
  
1.  Clique com botão direito **NumberGuessWorkflowActivities** na **Gerenciador de soluções** e selecione **Add**, **Novo Item**.  
  
2.  No **Installed**, **itens comuns** nó, selecione **fluxo de trabalho**. Selecione **atividade** da **fluxo de trabalho** lista.  
  
3.  Tipo de `FlowchartNumberGuessWorkflow` para o **nome** caixa e clique em **Add**.  
  
4.  Arraste uma **fluxograma** a atividade do **fluxograma** seção o **caixa de ferramentas** e solte-o no **soltar atividade aqui** rótulos no superfície de design de fluxo de trabalho.  
  
### <a name="to-create-the-workflow-variables-and-arguments"></a>Para criar as variáveis e os argumentos do fluxo de trabalho  
  
1.  Clique duas vezes em **Flowchartnumberguessworkflow** na **Gerenciador de soluções** para exibir o fluxo de trabalho no designer, caso ainda não esteja sendo exibido.  
  
2.  Clique em **argumentos** no lado inferior esquerdo do designer de fluxo de trabalho para exibir o **argumentos** painel.  
  
3.  Clique em **criar argumento**.  
  
4.  Tipo `MaxNumber` para o **nome** caixa, selecione **no** do **direção** lista suspensa, selecione **Int32** da **Tipo de argumento** lista suspensa e pressione ENTER para salvar o argumento.  
  
5.  Clique em **criar argumento**.  
  
6.  Tipo `Turns` para o **nome** caixa abaixo recém-adicionada `MaxNumber` argumento, selecione **Out** do **direção** lista suspensa, selecione  **Int32** do **tipo de argumento** lista suspensa e pressione ENTER.  
  
7.  Clique em **argumentos** no lado inferior esquerdo do designer de atividade para fechar o **argumentos** painel.  
  
8.  Clique em **variáveis** no lado inferior esquerdo do designer de fluxo de trabalho para exibir o **variáveis** painel.  
  
9. Clique em **criar variável**.  
  
    > [!TIP]
    >  Se nenhum **criar variável** caixa é exibida, clique no <xref:System.Activities.Statements.Flowchart> atividade na superfície do designer de fluxo de trabalho para selecioná-lo.  
  
10. Tipo `Guess` para o **nome** caixa, selecione **Int32** do **tipo de variável** lista suspensa e, em seguida, pressione ENTER para salvar a variável.  
  
11. Clique em **criar variável**.  
  
12. Tipo `Target` para o **nome** caixa, selecione **Int32** do **tipo de variável** lista suspensa e, em seguida, pressione ENTER para salvar a variável.  
  
13. Clique em **variáveis** no lado inferior esquerdo do designer de atividade para fechar o **variáveis** painel.  
  
### <a name="to-add-the-workflow-activities"></a>Para adicionar as atividades de fluxo de trabalho  
  
1.  Arraste um **atribuir** a atividade do **primitivos** seção o **caixa de ferramentas** e passe o mouse sobre o **iniciar** nó, que é na parte superior do fluxograma. Quando o **atribuir** atividade está sobre o **iniciar** nó, três triângulos aparecerão em torno do **iniciar** nó. Descartar os **atribuir** atividade no triângulo que está diretamente abaixo de **iniciar** nó. Isso vinculará os dois itens juntos e designa a **atribuir** atividade como a primeira atividade no fluxograma.  
  
    > [!NOTE]
    >  As atividades também podem ser indicadas como a atividade de início no fluxo de trabalho manualmente vinculando-as ao nó de origem. Para fazer isso, passe o mouse sobre o **inicie** nó, clique em um dos retângulos que aparecem quando o mouse está sobre o **iniciar** nó e arraste a conectar-se da linha até a atividade desejada e solte-o em um dos os retângulos que aparecem. Você também pode designar uma atividade como a atividade de início clicando duas vezes o it e escolhendo **definido como nó de início**.  
  
2.  Tipo `Target` para o **para** caixa e a seguinte expressão na **insira uma expressão c#** ou **insira uma expressão VB** caixa.  
  
    ```vb  
    New System.Random().Next(1, MaxNumber + 1)  
    ```  
  
    ```csharp  
    new System.Random().Next(1, MaxNumber + 1)  
    ```  
  
    > [!TIP]
    >  Se o **caixa de ferramentas** janela não for exibida, selecione **caixa de ferramentas** do **exibição** menu.  
  
3.  Arrastar um **Prompt** a atividade do **NumberGuessWorkflowActivities** seção do **caixa de ferramentas**, solte-o abaixo de **atribuir** atividade do anterior etapa e conecte-se a **Prompt** atividade para o **atribuir** atividade. Há três modos de conectar as duas atividades. A primeira maneira é para conectá-los conforme você descartar a **Prompt** atividade do fluxo de trabalho. Como você está arrastando o **Prompt** atividade ao fluxo de trabalho, focalize-lo a **atribuir** atividade e solte-o em um dos quatro triângulos que aparecem quando o **Prompt** atividade está sobre o **atribuir** atividade. A segunda maneira é descartar o **Prompt** atividade no fluxo de trabalho no local desejado. Em seguida, passe o mouse sobre o **atribua** atividade e arraste um dos retângulos que aparece para o **Prompt** atividade. Arraste o mouse para que a linha de conexão das **atribuir** atividade se conecta a um dos retângulos das **Prompt** atividade e, em seguida, solte o botão do mouse. A terceira maneira é muito semelhante ao primeiro, exceto que em vez de arrastar o **Prompt** atividade da **caixa de ferramentas**, arraste-o de seu local na superfície de design de fluxo de trabalho, passe o mouse sobre o  **Atribuir** atividade e solte-o em um dos triângulos que aparece.  
  
4.  No **janela de propriedades** para o **Prompt** atividade, digite `"EnterGuess"` incluindo as aspas no **BookmarkName** caixa do valor de propriedade. Tipo de `Guess` para o **resultado** caixa do valor de propriedade e digite a seguinte expressão na **texto** caixa da propriedade.  
  
    ```vb  
    "Please enter a number between 1 and " & MaxNumber  
    ```  
  
    ```csharp  
    "Please enter a number between 1 and " + MaxNumber  
    ```  
  
    > [!TIP]
    >  Se o **janela de propriedades** não for exibido, selecione **janela propriedades** do **exibição** menu.  
  
5.  Arraste um **atribuir** atividade da **primitivos** seção o **caixa de ferramentas** e conectá-lo usando um dos métodos descritos na etapa anterior para que fique abaixo de  **Prompt** atividade.  
  
6.  Tipo de `Turns` no **para** caixa e `Turns + 1` no **insira uma expressão c#** ou **insira uma expressão VB** caixa.  
  
7.  Arraste um **FlowDecision** da **fluxograma** seção o **caixa de ferramentas** e conectá-la abaixo o **atribuir** atividade. No **janela de propriedades**, digite a seguinte expressão na **condição** caixa do valor de propriedade.  
  
    ```vb  
    Guess = Target  
    ```  
  
    ```csharp  
    Guess == Target  
    ```  
  
8.  Arraste outro **FlowDecision** atividades desde o **caixa de ferramentas** e solte-o abaixo da primeira. Conecte as duas atividades arrastando do retângulo que é rotulado **falsos** na parte superior **FlowDecision** atividade para o retângulo na parte superior da segunda **FlowDecision**atividade.  
  
    > [!TIP]
    >  Se você não vir o **verdadeira** e **falso** rótulos no **FlowDecision**, passe o mouse sobre o **FlowDecision**.  
  
9. Clique na segunda **FlowDecision** atividade para selecioná-lo. No **janela de propriedades**, digite a seguinte expressão na **condição** caixa do valor de propriedade.  
  
    ```
    Guess < Target  
    ```  
  
10. Arraste duas **WriteLine** atividades da **primitivos** seção o **caixa de ferramentas** e soltá-los para que fiquem lado a lado abaixo das duas **FlowDecision**  atividades. Conectar-se a **verdadeira** ação da parte inferior **FlowDecision** atividade mais à esquerda **WriteLine** atividade e o **False** ação para o mais à direita **WriteLine** atividade.  
  
11. Clique em mais à esquerda **WriteLine** atividade para selecioná-la e digite a seguinte expressão na **texto** caixa do valor de propriedade **janela propriedades**.  
  
    ```
    "Your guess is too low."  
    ```  
  
12. Conectar-se a **WriteLine** para o lado esquerdo das **Prompt** atividade que está acima dela.  
  
13. Clique em mais à direita **WriteLine** atividade para selecioná-la e digite a seguinte expressão na **texto** caixa do valor de propriedade **janela propriedades**.  
  
    ```
    "Your guess is too high."  
    ```  
  
14. Conectar-se a **WriteLine** atividade para o lado direito das **Prompt** atividade acima dele.  
  
     O exemplo a seguir ilustra o fluxo de trabalho concluído.  
  
     ![Concluído o Windows Workflow Foundation](../../../docs/framework/windows-workflow-foundation/media/gettingstartedtutorialcompletedflowchart.PNG "GettingStartedTutorialCompletedFlowchart")  
  
### <a name="to-build-the-workflow"></a>Para compilar o fluxo de trabalho  
  
1.  Pressione CTRL+SHIFT+B para criar a solução.  
  
     Para obter instruções sobre como executar o fluxo de trabalho, consulte o próximo tópico, [como: Executar um fluxo de trabalho](../../../docs/framework/windows-workflow-foundation/how-to-run-a-workflow.md). Se você já tiver concluído o [como: Executar um fluxo de trabalho](../../../docs/framework/windows-workflow-foundation/how-to-run-a-workflow.md) passo a passo com um estilo diferente de fluxo de trabalho e quiser executá-lo usando o fluxo de trabalho de fluxograma dessa etapa, pule para a [para compilar e executar o aplicativo](../../../docs/framework/windows-workflow-foundation/how-to-run-a-workflow.md#BKMK_ToRunTheApplication) seção [como: Executar um fluxo de trabalho](../../../docs/framework/windows-workflow-foundation/how-to-run-a-workflow.md).  
  
## <a name="see-also"></a>Consulte também
- <xref:System.Activities.Statements.Flowchart>
- <xref:System.Activities.Statements.FlowDecision>
- [Programação do Windows Workflow Foundation](../../../docs/framework/windows-workflow-foundation/programming.md)
- [Criando fluxos de trabalho](../../../docs/framework/windows-workflow-foundation/designing-workflows.md)
- [Tutorial de Introdução](../../../docs/framework/windows-workflow-foundation/getting-started-tutorial.md)
- [Como: Criar uma atividade](../../../docs/framework/windows-workflow-foundation/how-to-create-an-activity.md)
- [Como: Executar um fluxo de trabalho](../../../docs/framework/windows-workflow-foundation/how-to-run-a-workflow.md)
