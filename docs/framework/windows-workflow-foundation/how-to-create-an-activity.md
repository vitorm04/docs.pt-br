---
title: Como criar uma atividade
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
ms.assetid: c09b1e99-21b5-4d96-9c04-ec31db3f4436
caps.latest.revision: "39"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 26385d91b4201820a5f6ba77b512e7bcfd5372c3
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/02/2017
---
# <a name="how-to-create-an-activity"></a>Como criar uma atividade
As atividades são a unidade principal de comportamento no [!INCLUDE[wf1](../../../includes/wf1-md.md)]. A lógica de execução de uma atividade pode ser implementada em código gerenciado ou pode ser implementada usando outras atividades. Este tópico demonstra como criar duas atividades. A primeira atividade é uma atividade simples que usa o código para implementar a sua lógica de execução. A implementação da segunda atividade é definida usando outras atividades. Essas atividades são usadas nas seguintes etapas no tutorial.  
  
> [!NOTE]
>  Para baixar uma versão completa do tutorial, consulte [Windows Workflow Foundation (WF45) - Tutorial de Introdução](http://go.microsoft.com/fwlink/?LinkID=248976).  
  
### <a name="to-create-the-activity-library-project"></a>Para criar o projeto de biblioteca de atividade  
  
1.  Abra [!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)] e escolha **novo**, **projeto** do **arquivo** menu.  
  
2.  Expanda o **outros tipos de projetos** nó o **instalado**, **modelos** e selecione **soluções do Visual Studio**.  
  
3.  Selecione **solução em branco** do **soluções do Visual Studio** lista. Certifique-se de que **.NET Framework 4.5** está selecionado na lista suspensa de versão do .NET Framework. Tipo `WF45GettingStartedTutorial` no **nome** caixa e, em seguida, clique em **Okey**.  
  
4.  Clique com botão direito **WF45GettingStartedTutorial** na **Solution Explorer** e escolha **adicionar**, **novo projeto**.  
  
    > [!TIP]
    >  Se o **Solution Explorer** janela não for exibida, selecione **Solution Explorer** do **exibição** menu.  
  
5.  No **instalado** nó, selecione **Visual C#**, **fluxo de trabalho** (ou **Visual Basic**, **fluxo de trabalho**). Certifique-se de que **.NET Framework 4.5** está selecionado no [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] lista suspensa de versão. Selecione **biblioteca de atividades** do **fluxo de trabalho** lista. Tipo `NumberGuessWorkflowActivities` no **nome** caixa e, em seguida, clique em **Okey**.  
  
    > [!NOTE]
    >  Dependendo da linguagem de programação que é configurada como linguagem primária no [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)], o **Visual C#** ou **Visual Basic** nó pode estar sob o **outras linguagens**nó o **instalado** nó.  
  
6.  Clique com botão direito **activity1** na **Solution Explorer** e escolha **excluir**. Clique em **Okey** para confirmar.  
  
### <a name="to-create-the-readint-activity"></a>Para criar a atividade de ReadInt  
  
1.  Escolha **Adicionar Novo Item** do **projeto** menu.  
  
2.  No **instalado**, **itens comuns** nó, selecione **fluxo de trabalho**. Selecione **atividade de código** do **fluxo de trabalho** lista.  
  
3.  Tipo `ReadInt` para o **nome** caixa e, em seguida, clique em **adicionar**.  
  
4.  Substitua a definição existente de `ReadInt` pela seguinte definição.  
  
     [!code-csharp[CFX_WF_GettingStarted#1](../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_wf_gettingstarted/cs/readint.cs#1)]
     [!code-vb[CFX_WF_GettingStarted#1](../../../samples/snippets/visualbasic/VS_Snippets_CFX/cfx_wf_gettingstarted/vb/readint.vb#1)]  
  
    > [!NOTE]
    >  A atividade `ReadInt` é derivada de <xref:System.Activities.NativeActivity%601> em vez de <xref:System.Activities.CodeActivity>, que é o padrão para o modelo de atividade de código. <xref:System.Activities.CodeActivity%601> poderá ser usado se a atividade fornecer um único resultado, que é exposto através do argumento <xref:System.Activities.Activity%601.Result%2A>, mas <xref:System.Activities.CodeActivity%601> não oferece suporte ao uso de indicadores, portanto <xref:System.Activities.NativeActivity%601> será usado.  
  
### <a name="to-create-the-prompt-activity"></a>Para criar a atividade de Prompt  
  
1.  Pressione CTRL+SHIFT+B para criar o projeto. Compilar o projeto permite que a atividade `ReadInt` neste projeto seja usada para criar a atividade personalizada dessa etapa.  
  
2.  Escolha **Adicionar Novo Item** do **projeto** menu.  
  
3.  No **instalado**, **itens comuns** nó, selecione **fluxo de trabalho**. Selecione **atividade** do **fluxo de trabalho** lista.  
  
4.  Tipo `Prompt` para o **nome** caixa e, em seguida, clique em **adicionar**.  
  
5.  Clique duas vezes em **Prompt.xaml** na **Solution Explorer** para exibi-lo no designer caso ainda não esteja sendo exibido.  
  
6.  Clique em **argumentos** no lado inferior esquerdo do designer de atividade para exibir o **argumentos** painel.  
  
7.  Clique em **criar argumento**.  
  
8.  Tipo `BookmarkName` no **nome** caixa, selecione **na** do **direção** lista suspensa, selecione **cadeia de caracteres** da **Tipo de argumento** lista suspensa e, em seguida, pressione ENTER para salvar o argumento.  
  
9. Clique em **criar argumento**.  
  
10. Tipo `Result` para o **nome** caixa sob recém-adicionado `BookmarkName` argumento, selecione **Out** do **direção** lista suspensa, selecione **Int32** do **tipo de argumento** lista suspensa e, em seguida, pressione ENTER.  
  
11. Clique em **criar argumento**.  
  
12. Tipo `Text` no **nome** caixa, selecione **na** do **direção** lista suspensa, selecione **cadeia de caracteres** da **Tipo de argumento** lista suspensa e, em seguida, pressione ENTER para salvar o argumento.  
  
     Esses três argumentos são associados aos argumentos correspondentes das atividades <xref:System.Activities.Statements.WriteLine> e `ReadInt` que são adicionadas à atividade `Prompt` nas seguintes etapas.  
  
13. Clique em **argumentos** no lado inferior esquerdo do designer de atividade para fechar o **argumentos** painel.  
  
14. Arraste um **sequência** atividade do **fluxo de controle** seção o **caixa de ferramentas** e solte-a para o **descartar atividade aqui** rótulo da **Prompt** designer de atividade.  
  
    > [!TIP]
    >  Se o **caixa de ferramentas** janela não for exibida, selecione **caixa de ferramentas** do **exibição** menu.  
  
15. Arraste um **WriteLine** atividade do **primitivos** seção o **caixa de ferramentas** e solte-a para o **descartar atividade aqui** rótulo da **Sequência** atividade.  
  
16. Associar o **texto** argumento do **WriteLine** atividade para o **texto** argumento do **Prompt** atividade digitando `Text` para o **insira uma expressão de c#** ou **insira uma expressão VB** caixa o **propriedades** janela e, em seguida, pressione a guia chave duas vezes. Isso fecha a janela dos membros da lista do IntelliSense e salva o valor da propriedade removendo a seleção da propriedade. Essa propriedade também pode ser definida digitando `Text` para o **insira uma expressão de c#** ou **insira uma expressão VB** caixa sobre a atividade em si.  
  
    > [!TIP]
    >  Se o **janela propriedades** não é exibida, selecione **janela propriedades** do **exibição** menu.  
  
17. Arraste um **ReadInt** atividade do **NumberGuessWorkflowActivities** seção o **caixa de ferramentas** e solte-o no **sequência** atividade para que ela siga a **WriteLine** atividade.  
  
18. Associar o **BookmarkName** argumento do **ReadInt** atividade para o **BookmarkName** argumento do **Prompt** atividade digitando `BookmarkName` no **insira uma expressão VB** caixa à direita do **BookmarkName** argumento o **janela propriedades**e, em seguida, pressione a tecla TAB duas vezes para fechar a janela de membros de lista do IntelliSense e salvar a propriedade.  
  
19. Associar o **resultados** argumento do **ReadInt** atividade para o **resultados** argumento do **Prompt** atividade digitando `Result` no **insira uma expressão VB** caixa à direita do **resultados** argumento no **janela propriedades**e, em seguida, pressione a tecla TAB duas vezes.  
  
20. Pressione CTRL+SHIFT+B para criar a solução.  
  
     Para obter instruções sobre como criar um fluxo de trabalho com essas atividades, consulte a próxima etapa no tutorial, [como: criar um fluxo de trabalho](../../../docs/framework/windows-workflow-foundation/how-to-create-a-workflow.md).  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Activities.CodeActivity>  
 <xref:System.Activities.NativeActivity%601>  
 [Criando e implementando atividades personalizadas](../../../docs/framework/windows-workflow-foundation/designing-and-implementing-custom-activities.md)  
 [Tutorial de Introdução](../../../docs/framework/windows-workflow-foundation/getting-started-tutorial.md)  
 [Como criar um fluxo de trabalho](../../../docs/framework/windows-workflow-foundation/how-to-create-a-workflow.md)  
 [Usando o ExpressionTextBox em um Designer de atividade personalizada](../../../docs/framework/windows-workflow-foundation/samples/using-the-expressiontextbox-in-a-custom-activity-designer.md)
