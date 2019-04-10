---
title: Declarando e acionando eventos (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- declarations [Visual Basic], events
- events [Visual Basic], walkthroughs
- declaring events [Visual Basic], walkthroughs
- events [Visual Basic], declaring
- events [Visual Basic], raising
- raising events [Visual Basic], walkthroughs
ms.assetid: 8ffb3be8-097d-4d3c-b71e-04555ebda2a2
ms.openlocfilehash: cab6c90947eae8abeb9387535eadb2f89e71454a
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/09/2019
ms.locfileid: "59320685"
---
# <a name="walkthrough-declaring-and-raising-events-visual-basic"></a>Passo a passo: Declarando e acionando eventos (Visual Basic)
Este passo a passo demonstra como declarar e acionar eventos para uma classe chamada `Widget`. Depois de concluir as etapas, você talvez queira ler o tópico [passo a passo: Manipulação de eventos](../../../../visual-basic/programming-guide/language-features/events/walkthrough-handling-events.md), que mostra como usar eventos de `Widget` objetos para fornecer informações de status em um aplicativo.  
  
## <a name="the-widget-class"></a>A classe de Widget  
 Suponha para o momento em que você tem um `Widget` classe. Seu `Widget` classe tem um método que pode levar muito tempo para executar, e você deseja que o aplicativo seja capaz de juntar-se de algum tipo de indicador de conclusão.  
  
 É claro, você poderia fazer o `Widget` objeto mostrar uma caixa de diálogo de porcentagem de conclusão, mas, em seguida, você estaria preso com essa caixa de diálogo em cada projeto que você usou o `Widget` classe. Um princípio de design do objeto é permitir que o aplicativo que usa um identificador de objeto da interface do usuário — a menos que a finalidade do objeto é gerenciar uma caixa de diálogo ou formulário.  
  
 A finalidade `Widget` é executar outras tarefas, portanto, é melhor adicionar uma `PercentDone` evento e deixar que o procedimento que chama `Widget`do métodos lidam com atualizações de status de evento e a exibição. O `PercentDone` evento também pode fornecer um mecanismo para cancelar a tarefa.  
  
#### <a name="to-build-the-code-example-for-this-topic"></a>Para compilar o exemplo de código para este tópico  
  
1. Abra um novo projeto de aplicativo do Windows Visual Basic e crie um formulário chamado `Form1`.  
  
2. Adicione dois botões e um rótulo para `Form1`.  
  
3. Nomeie os objetos como mostrado na tabela a seguir.  
  
    |Objeto|Propriedade|Configuração|  
    |------------|--------------|-------------|  
    |`Button1`|`Text`|Iniciar tarefa|  
    |`Button2`|`Text`|Cancelar|  
    |`Label`|`(Name)`, `Text`|lblPercentDone, 0|  
  
4. Sobre o **projeto** menu, escolha **Adicionar classe** para adicionar uma classe chamada `Widget.vb` ao projeto.  
  
#### <a name="to-declare-an-event-for-the-widget-class"></a>Para declarar um evento para a classe de Widget  
  
-   Use o `Event` palavra-chave para declarar um evento no `Widget` classe. Observe que um evento pode ter `ByVal` e `ByRef` argumentos, como `Widget`do `PercentDone` evento demonstra:  
  
     [!code-vb[VbVbcnWalkthroughDeclaringAndRaisingEvents#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnWalkthroughDeclaringAndRaisingEvents/VB/Widget.vb#1)]  
  
 Quando o objeto de chamada recebe um `PercentDone` evento, o `Percent` argumento contém a porcentagem da tarefa que foi concluída. O `Cancel` argumento pode ser definido como `True` para cancelar o método que gerou o evento.  
  
> [!NOTE]
>  Você pode declarar argumentos de evento, assim como faria argumentos dos procedimentos, com as seguintes exceções: Eventos não podem ter `Optional` ou `ParamArray` argumentos e eventos não têm valores de retorno.  
  
 O `PercentDone` é gerado pela `LongTask` método o `Widget` classe. `LongTask` leva dois argumentos: o período de tempo, o método aparenta estar fazendo o trabalho e o intervalo de tempo mínimo antes `LongTask` pausas para gerar o `PercentDone` eventos.  
  
#### <a name="to-raise-the-percentdone-event"></a>Para gerar o evento PercentDone  
  
1. Para simplificar o acesso para o `Timer` propriedade usada por essa classe, adicione uma `Imports` instrução na parte superior da seção de declarações do seu módulo de classe, acima o `Class Widget` instrução.  
  
     [!code-vb[VbVbcnWalkthroughDeclaringAndRaisingEvents#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnWalkthroughDeclaringAndRaisingEvents/VB/Widget.vb#2)]  
  
2. Adicione o seguinte código à classe `Widget`:  
  
     [!code-vb[VbVbcnWalkthroughDeclaringAndRaisingEvents#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnWalkthroughDeclaringAndRaisingEvents/VB/Widget.vb#3)]  
  
 Quando seu aplicativo chama o `LongTask` método, o `Widget` classe gera o `PercentDone` evento cada `MinimumInterval` segundos. Quando o evento é retornado, `LongTask` verifica se o `Cancel` argumento foi definido como `True`.  
  
 Alguns avisos de isenção de responsabilidade aqui são necessários. Para simplificar, o `LongTask` procedimento pressupõe que você sabe de antemão quanto tempo levará a tarefa. Isso quase nunca é o caso. Dividir tarefas em partes do mesmo tamanho pode ser difícil, e muitas vezes o que é mais importante para os usuários é simplesmente a quantidade de tempo decorrido antes que eles recebem uma indicação de que algo está acontecendo.  
  
 Você pode ter observado outra falha neste exemplo. O `Timer` propriedade retorna o número de segundos decorridos desde a meia-noite; portanto, o aplicativo travar se ele for iniciado antes de meia-noite. Uma abordagem mais cuidadosa para medição de tempo levariam condições de limite como isso em consideração, ou evitá-los completamente, usando propriedades como `Now`.  
  
 Agora que o `Widget` classe pode gerar eventos, você pode mover para a próximo passo a passo. [Passo a passo: Manipulação de eventos](../../../../visual-basic/programming-guide/language-features/events/walkthrough-handling-events.md) demonstra como usar `WithEvents` para associar um manipulador de eventos com o `PercentDone` eventos.  
  
## <a name="see-also"></a>Consulte também

- <xref:Microsoft.VisualBasic.DateAndTime.Timer%2A>
- <xref:Microsoft.VisualBasic.DateAndTime.Now%2A>
- [Passo a passo: Tratando eventos](../../../../visual-basic/programming-guide/language-features/events/walkthrough-handling-events.md)
- [Eventos](../../../../visual-basic/programming-guide/language-features/events/index.md)
