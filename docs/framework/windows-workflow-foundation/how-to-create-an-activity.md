---
title: Como criar uma atividade
ms.date: 09/14/2018
dev_langs:
- csharp
- vb
ms.assetid: c09b1e99-21b5-4d96-9c04-ec31db3f4436
ms.openlocfilehash: 8aa6900b26bbe9f77fe0802a7929febe5af61269
ms.sourcegitcommit: 213292dfbb0c37d83f62709959ff55c50af5560d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/25/2018
ms.locfileid: "47112673"
---
# <a name="how-to-create-an-activity"></a>Como criar uma atividade

As atividades são a unidade principal de comportamento no [!INCLUDE[wf1](../../../includes/wf1-md.md)]. A lógica de execução de uma atividade pode ser implementada em código gerenciado ou pode ser implementada usando outras atividades. Este tópico demonstra como criar duas atividades. A primeira atividade é uma atividade simples que usa o código para implementar a sua lógica de execução. A implementação da segunda atividade é definida usando outras atividades. Essas atividades são usadas nas seguintes etapas no tutorial.

> [!NOTE]
> Para baixar uma versão completa do tutorial, consulte [Windows Workflow Foundation (WF45) - Tutorial de Introdução](https://go.microsoft.com/fwlink/?LinkID=248976).

## <a name="create-the-activity-library-project"></a>Criar o projeto de biblioteca de atividade

1.  Abra o Visual Studio e escolha **New** > **projeto** do **arquivo** menu.

2.  No **novo projeto** caixa de diálogo, sob o **instalado** categoria, selecione **Visual c#** > **fluxo de trabalho** (ou **Visual Basic** > **fluxo de trabalho**).

    > [!NOTE]
    > Se você não vir as **fluxo de trabalho** categoria do modelo, você talvez precise instalar o **Windows Workflow Foundation** componente do Visual Studio. Escolha o **abrir instalador do Visual Studio** link no lado esquerdo das **novo projeto** caixa de diálogo. No instalador do Visual Studio, selecione o **componentes individuais** guia. Em seguida, na **atividades de desenvolvimento** categoria, selecione o **Windows Workflow Foundation** componente. Escolher **modificar** para instalar o componente.

3. Selecione o **biblioteca de atividades** modelo de projeto. Tipo de `NumberGuessWorkflowActivities` no **nome** caixa e, em seguida, clique em **Okey**.

4.  Clique com botão direito **Activity1.xaml** na **Gerenciador de soluções** e escolha **excluir**. Clique em **Okey** para confirmar.

## <a name="create-the-readint-activity"></a>Criar a atividade de ReadInt

1.  Escolher **Adicionar Novo Item** da **projeto** menu.

2.  No **Installed** > **itens comuns** nó, selecione **fluxo de trabalho**. Selecione **atividade de código** da **fluxo de trabalho** lista.

3.  Tipo de `ReadInt` para o **nome** caixa e, em seguida, clique em **Add**.

4.  Substitua a definição existente de `ReadInt` pela seguinte definição.

     [!code-csharp[CFX_WF_GettingStarted#1](../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_wf_gettingstarted/cs/readint.cs#1)]
     [!code-vb[CFX_WF_GettingStarted#1](../../../samples/snippets/visualbasic/VS_Snippets_CFX/cfx_wf_gettingstarted/vb/readint.vb#1)]

    > [!NOTE]
    > A atividade `ReadInt` é derivada de <xref:System.Activities.NativeActivity%601> em vez de <xref:System.Activities.CodeActivity>, que é o padrão para o modelo de atividade de código. <xref:System.Activities.CodeActivity%601> poderá ser usado se a atividade fornecer um único resultado, que é exposto através do argumento <xref:System.Activities.Activity%601.Result%2A>, mas <xref:System.Activities.CodeActivity%601> não oferece suporte ao uso de indicadores, portanto <xref:System.Activities.NativeActivity%601> será usado.

## <a name="create-the-prompt-activity"></a>Criar a atividade de Prompt

1.  Pressione **Ctrl**+**Shift**+**B** para compilar o projeto. Compilar o projeto permite que a atividade `ReadInt` neste projeto seja usada para criar a atividade personalizada dessa etapa.

2.  Escolher **Adicionar Novo Item** da **projeto** menu.

3.  No **Installed** > **itens comuns** nó, selecione **fluxo de trabalho**. Selecione **atividade** da **fluxo de trabalho** lista.

4.  Tipo de `Prompt` para o **nome** caixa e, em seguida, clique em **Add**.

5.  Clique duas vezes em **prompt** na **Gerenciador de soluções** para exibi-lo no designer caso ainda não esteja sendo exibido.

6.  Clique em **argumentos** no lado inferior esquerdo do designer de atividade para exibir o **argumentos** painel.

7.  Clique em **criar argumento**.

8.  Tipo `BookmarkName` para o **nome** caixa, selecione **no** do **direção** lista suspensa, selecione **cadeia de caracteres** da **Tipo de argumento** lista suspensa e pressione **Enter** para salvar o argumento.

9. Clique em **criar argumento**.

10. Tipo `Result` para o **nome** caixa que está embaixo recém-adicionada `BookmarkName` argumento, selecione **Out** do **direção** lista suspensa, selecione **Int32** da **tipo de argumento** lista suspensa e pressione **Enter**.

11. Clique em **criar argumento**.

12. Tipo `Text` para o **nome** caixa, selecione **no** do **direção** lista suspensa, selecione **cadeia de caracteres** da **Tipo de argumento** lista suspensa e pressione **Enter** para salvar o argumento.

     Esses três argumentos são associados aos argumentos correspondentes das atividades <xref:System.Activities.Statements.WriteLine> e `ReadInt` que são adicionadas à atividade `Prompt` nas seguintes etapas.

13. Clique em **argumentos** no lado inferior esquerdo do designer de atividade para fechar o **argumentos** painel.

14. Arraste um **sequência** a atividade do **fluxo de controle** seção o **caixa de ferramentas** e solte-o no **soltar atividade aqui** rótulo da **Prompt** designer de atividade.

    > [!TIP]
    > Se o **caixa de ferramentas** janela não for exibida, selecione **caixa de ferramentas** do **exibição** menu.

15. Arraste um **WriteLine** a atividade do **primitivos** seção o **caixa de ferramentas** e solte-o no **soltar atividade aqui** rótulo da **Sequência** atividade.

16. Associar o **texto** argumento do **WriteLine** atividade para o **texto** argumento do **Prompt** atividade digitando `Text` para o **insira uma expressão c#** ou **insira uma expressão VB** caixa **propriedades** janela e, em seguida, pressione o **guia** chave de duas vezes. Isso fecha a janela dos membros da lista do IntelliSense e salva o valor da propriedade removendo a seleção da propriedade. Essa propriedade também pode ser definida digitando `Text` para o **inserir uma expressão c#** ou **insira uma expressão VB** caixa na própria atividade.

    > [!TIP]
    > Se o **janela de propriedades** não for exibido, selecione **janela propriedades** do **exibição** menu.

17. Arraste uma **ReadInt** a atividade do **NumberGuessWorkflowActivities** seção o **caixa de ferramentas** e solte-o no **sequência** atividade para que ela siga a **WriteLine** atividade.

18. Associar o **BookmarkName** argumento do **ReadInt** atividade para o **BookmarkName** argumento do **Prompt** atividade digitando `BookmarkName` no **inserir uma expressão de VB** caixa à direita do **BookmarkName** argumento no **janela propriedades**e, em seguida, pressione a **Guia** duas vezes para fechar a janela de membros da lista do IntelliSense e salvar a propriedade de chave.

19. Associar o **resultado** argumento do **ReadInt** atividade para o **resultados** argumento do **Prompt** atividade digitando `Result` na **insira uma expressão VB** caixa à direita do **resultado** argumento no **janela propriedades**e, em seguida, pressione o **guia** duas vezes de chave.

20. Pressione **Ctrl**+**Shift**+**B** para compilar a solução.

## <a name="next-steps"></a>Próximas etapas

Para obter instruções sobre como criar um fluxo de trabalho por meio dessas atividades, consulte a próxima etapa no tutorial, [como: criar um fluxo de trabalho](../../../docs/framework/windows-workflow-foundation/how-to-create-a-workflow.md).

## <a name="see-also"></a>Consulte também

- <xref:System.Activities.CodeActivity>
- <xref:System.Activities.NativeActivity%601>
- [Criando e implementando atividades personalizadas](../../../docs/framework/windows-workflow-foundation/designing-and-implementing-custom-activities.md)
- [Tutorial de Introdução](../../../docs/framework/windows-workflow-foundation/getting-started-tutorial.md)
- [Como criar um fluxo de trabalho](../../../docs/framework/windows-workflow-foundation/how-to-create-a-workflow.md)
- [Usando o ExpressionTextBox em um designer personalizado de atividades](../../../docs/framework/windows-workflow-foundation/samples/using-the-expressiontextbox-in-a-custom-activity-designer.md)