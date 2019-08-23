---
title: Declarando e gerando eventos (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- declarations [Visual Basic], events
- events [Visual Basic], walkthroughs
- declaring events [Visual Basic], walkthroughs
- events [Visual Basic], declaring
- events [Visual Basic], raising
- raising events [Visual Basic], walkthroughs
ms.assetid: 8ffb3be8-097d-4d3c-b71e-04555ebda2a2
ms.openlocfilehash: 20e2b0efbf40597049c515134f408927f18d5603
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69956330"
---
# <a name="walkthrough-declaring-and-raising-events-visual-basic"></a>Passo a passo: Declarando e gerando eventos (Visual Basic)
Este tutorial demonstra como declarar e gerar eventos para uma classe chamada `Widget`. Depois de concluir as etapas, talvez você queira ler o tópico [complementar: Manipulação de](../../../../visual-basic/programming-guide/language-features/events/walkthrough-handling-events.md)eventos, que mostra como usar eventos de `Widget` objetos para fornecer informações de status em um aplicativo.  
  
## <a name="the-widget-class"></a>A classe Widget  
 Suponha que, por enquanto, você tenha `Widget` uma classe. Sua `Widget` classe tem um método que pode levar muito tempo para ser executada e você deseja que seu aplicativo seja capaz de colocar algum tipo de indicador de conclusão.  
  
 É claro que você pode fazer com `Widget` que o objeto mostre uma caixa de diálogo de porcentagem concluída, mas, em seguida, você estaria preso a essa caixa de diálogo em todos `Widget` os projetos nos quais usou a classe. Um bom princípio do design de objeto é permitir que o aplicativo que usa um objeto manipule a interface do usuário — a menos que a finalidade do objeto seja gerenciar um formulário ou caixa de diálogo.  
  
 A finalidade do `Widget` é executar outras tarefas, portanto, é melhor adicionar um `PercentDone` evento e permitir que o procedimento que chama `Widget`os métodos manipule esse evento e exiba as atualizações de status. O `PercentDone` evento também pode fornecer um mecanismo para cancelar a tarefa.  
  
#### <a name="to-build-the-code-example-for-this-topic"></a>Para criar o exemplo de código para este tópico  
  
1. Abra um novo projeto de aplicativo do Windows Visual Basic e crie um `Form1`formulário chamado.  
  
2. Adicione dois botões e um rótulo a `Form1`.  
  
3. Nomeie os objetos como mostrado na tabela a seguir.  
  
    |Objeto|Propriedade|Configuração|  
    |------------|--------------|-------------|  
    |`Button1`|`Text`|Iniciar tarefa|  
    |`Button2`|`Text`|Cancelar|  
    |`Label`|`(Name)`, `Text`|lblPercentDone, 0|  
  
4. No menu **projeto** , escolha **Adicionar classe** para adicionar uma classe chamada `Widget.vb` ao projeto.  
  
#### <a name="to-declare-an-event-for-the-widget-class"></a>Para declarar um evento para a classe Widget  
  
- Use a `Event` palavra-chave para declarar um evento `Widget` na classe. Observe que um evento pode ter `ByVal` argumentos `ByRef` e, como `Widget`é `PercentDone` demonstrado pelo evento:  
  
     [!code-vb[VbVbcnWalkthroughDeclaringAndRaisingEvents#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnWalkthroughDeclaringAndRaisingEvents/VB/Widget.vb#1)]  
  
 Quando o objeto de chamada recebe `PercentDone` um evento, `Percent` o argumento contém a porcentagem da tarefa concluída. O `Cancel` argumento pode ser definido como `True` para cancelar o método que gerou o evento.  
  
> [!NOTE]
> Você pode declarar argumentos de evento da mesma forma como faz argumentos de procedimentos, com as seguintes exceções: Os eventos não `Optional` podem `ParamArray` ter argumentos ou, e os eventos não têm valores de retorno.  
  
 O `PercentDone` evento é gerado `LongTask` pelo método da `Widget` classe. `LongTask`usa dois argumentos: o período de tempo que o método pretende a fazer funcionar e o intervalo de tempo mínimo antes `LongTask` de pausar para gerar o `PercentDone` evento.  
  
#### <a name="to-raise-the-percentdone-event"></a>Para gerar o evento PercentDone  
  
1. Para simplificar o `Timer` acesso à propriedade usada por essa classe, adicione `Imports` uma instrução à parte superior da seção de declarações do seu módulo de classe, `Class Widget` acima da instrução.  
  
     [!code-vb[VbVbcnWalkthroughDeclaringAndRaisingEvents#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnWalkthroughDeclaringAndRaisingEvents/VB/Widget.vb#2)]  
  
2. Adicione o seguinte código à classe `Widget`:  
  
     [!code-vb[VbVbcnWalkthroughDeclaringAndRaisingEvents#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnWalkthroughDeclaringAndRaisingEvents/VB/Widget.vb#3)]  
  
 Quando o aplicativo chama o `LongTask` método, a `Widget` classe gera o `PercentDone` evento a `MinimumInterval` cada segundos. Quando o evento retorna, `LongTask` o verifica se o `Cancel` argumento foi definido como `True`.  
  
 Alguns isenções de responsabilidade são necessários aqui. Para simplificar, `LongTask` o procedimento pressupõe que você saiba com antecedência quanto tempo a tarefa levará. Esse é quase nunca o caso. Dividir tarefas em partes de tamanho par pode ser difícil e, muitas vezes, o que mais importa para os usuários é simplesmente a quantidade de tempo que o passa antes de receber uma indicação de que algo está acontecendo.  
  
 Você pode ter extratado outra falha neste exemplo. A `Timer` propriedade retorna o número de segundos que passaram desde a meia-noite; portanto, o aplicativo ficará preso se for iniciado logo antes da meia-noite. Uma abordagem mais cuidadosa para medir o tempo teria condições de limite como essa em consideração, ou evitá-las completamente, usando propriedades como `Now`.  
  
 Agora que a `Widget` classe pode gerar eventos, você pode ir para o próximo passo a passos. [Passo a passo: Manipulação de](../../../../visual-basic/programming-guide/language-features/events/walkthrough-handling-events.md) eventos demonstra como usar `WithEvents` o `PercentDone` para associar um manipulador de eventos ao evento.  
  
## <a name="see-also"></a>Consulte também

- <xref:Microsoft.VisualBasic.DateAndTime.Timer%2A>
- <xref:Microsoft.VisualBasic.DateAndTime.Now%2A>
- [Passo a passo: Manipulando eventos](../../../../visual-basic/programming-guide/language-features/events/walkthrough-handling-events.md)
- [Eventos](../../../../visual-basic/programming-guide/language-features/events/index.md)
