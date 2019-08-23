---
title: Manipulando eventos (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- event handling [Visual Basic], walkthroughs
- walkthroughs [Visual Basic], event handling
- variables [Visual Basic], WithEvents
- events [Visual Basic], walkthroughs
- WithEvents keyword [Visual Basic], walkthroughs
- event handlers [Visual Basic], walkthroughs
ms.assetid: f145b3fc-5ae0-4509-a2aa-1ff6934706bd
ms.openlocfilehash: 12267e0a70419298bc581421c4f3a220088d205f
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69956308"
---
# <a name="walkthrough-handling-events-visual-basic"></a>Passo a passo: Manipulando eventos (Visual Basic)
Este é o segundo de dois tópicos que demonstram como trabalhar com eventos. O primeiro tópico, [Walkthrough: Declarando e](../../../../visual-basic/programming-guide/language-features/events/walkthrough-declaring-and-raising-events.md)gerando eventos, mostra como declarar e gerar eventos. Esta seção usa o formulário e a classe desse passo a passos para mostrar como tratar eventos quando eles ocorrem.  
  
 O `Widget` exemplo de classe usa instruções tradicionais de manipulação de eventos. Visual Basic fornece outras técnicas para trabalhar com eventos. Como um exercício, você pode modificar este exemplo para usar as `AddHandler` instruções `Handles` e.  
  
### <a name="to-handle-the-percentdone-event-of-the-widget-class"></a>Para manipular o evento PercentDone da classe Widget  
  
1. Coloque o seguinte código em `Form1`:  
  
     [!code-vb[VbVbcnWalkthroughDeclaringAndRaisingEvents#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnWalkthroughDeclaringAndRaisingEvents/VB/Form1.vb#4)]  
  
     A `WithEvents` palavra-chave especifica que `mWidget` a variável é usada para lidar com os eventos de um objeto. Você especifica o tipo de objeto fornecendo o nome da classe da qual o objeto será criado.  
  
     A variável `mWidget` é declarada `WithEvents` em `Form1` porque as variáveis devem ser de nível de classe. Isso é verdadeiro independentemente do tipo de classe em que você os coloca.  
  
     A variável `mblnCancel` é usada para cancelar o `LongTask` método.  
  
## <a name="writing-code-to-handle-an-event"></a>Escrevendo código para manipular um evento  
 Assim que você declarar uma variável usando `WithEvents`, o nome da variável aparecerá na lista suspensa à esquerda do editor de **código**da classe. Quando você seleciona `mWidget`, os `Widget` eventos da classe são exibidos na lista suspensa à direita. A seleção de um evento exibe o procedimento de evento correspondente, `mWidget` com o prefixo e um sublinhado. Todos os procedimentos de evento associados a `WithEvents` uma variável recebem o nome da variável como um prefixo.  
  
#### <a name="to-handle-an-event"></a>Para identificar um evento  
  
1. Selecione `mWidget` na lista suspensa à esquerda no **Editor de códigos**.  
  
2. Selecione o `PercentDone` evento na lista suspensa à direita. O **Editor de código** abre `mWidget_PercentDone` o procedimento de evento.  
  
    > [!NOTE]
    > O **Editor de código** é útil, mas não obrigatório, para inserir novos manipuladores de eventos. Neste tutorial, é mais direto copiar apenas os manipuladores de eventos diretamente em seu código.  
  
3. Adicione o seguinte código ao manipulador de eventos do `mWidget_PercentDone`:  
  
     [!code-vb[VbVbcnWalkthroughDeclaringAndRaisingEvents#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnWalkthroughDeclaringAndRaisingEvents/VB/Form1.vb#5)]  
  
     Sempre que `PercentDone` o evento é gerado, o procedimento de evento exibe a porcentagem concluída `Label` em um controle. O `DoEvents` método permite que o rótulo seja redesenhado e também dá ao usuário a oportunidade de clicar no botão **Cancelar** .  
  
4. Adicione o seguinte código para o `Button2_Click` manipulador de eventos:  
  
     [!code-vb[VbVbcnWalkthroughDeclaringAndRaisingEvents#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnWalkthroughDeclaringAndRaisingEvents/VB/Form1.vb#6)]  
  
 Se o usuário clicar no botão **Cancelar** enquanto `LongTask` estiver em execução, `Button2_Click` o evento será executado assim que a `DoEvents` instrução permitir que o processamento de eventos ocorra. A variável `mblnCancel` no nível de classe é definida `True`como, e `mWidget_PercentDone` o evento o testa e define o `ByRef Cancel` argumento como `True`.  
  
## <a name="connecting-a-withevents-variable-to-an-object"></a>Conectando uma variável WithEvents a um objeto  
 `Form1`Agora está configurado para manipular os eventos `Widget` de um objeto. Tudo o que resta é encontrar um `Widget` em algum lugar.  
  
 Quando você declara uma variável `WithEvents` em tempo de design, nenhum objeto é associado a ela. Uma `WithEvents` variável é assim como qualquer outra variável de objeto. Você precisa criar um objeto e atribuir uma referência a ele com a `WithEvents` variável.  
  
#### <a name="to-create-an-object-and-assign-a-reference-to-it"></a>Para criar um objeto e atribuir uma referência a ele  
  
1. Selecione **(eventos Form1)** na lista suspensa à esquerda no **Editor de código**.  
  
2. Selecione o `Load` evento na lista suspensa à direita. O **Editor de código** abre `Form1_Load` o procedimento de evento.  
  
3. Adicione o seguinte código para o `Form1_Load` procedimento de evento para `Widget`criar:  
  
     [!code-vb[VbVbcnWalkthroughDeclaringAndRaisingEvents#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnWalkthroughDeclaringAndRaisingEvents/VB/Form1.vb#7)]  
  
 Quando esse código é executado, Visual Basic cria um `Widget` objeto e conecta seus eventos aos procedimentos de evento `mWidget`associados ao. Desse ponto em diante, sempre que `Widget` o gerar `PercentDone` seu evento, `mWidget_PercentDone` o procedimento de evento será executado.  
  
#### <a name="to-call-the-longtask-method"></a>Para chamar o método LongTask  
  
- Adicione o seguinte código ao manipulador de eventos do `Button1_Click`:  
  
     [!code-vb[VbVbcnWalkthroughDeclaringAndRaisingEvents#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnWalkthroughDeclaringAndRaisingEvents/VB/Form1.vb#8)]  
  
 Antes que `LongTask` o método seja chamado, o rótulo que exibe a porcentagem concluída deve ser inicializado e o sinalizador de `Boolean` nível de classe para cancelar o método deve ser definido `False`como.  
  
 `LongTask`é chamado com uma duração de tarefa de 12,2 segundos. O `PercentDone` evento é gerado uma vez a cada um terço de um segundo. Cada vez que o evento é gerado, `mWidget_PercentDone` o procedimento de evento é executado.  
  
 Quando `LongTask` for concluído, `mblnCancel` o será testado para ver `LongTask` se terminou normalmente ou se foi interrompido porque `mblnCancel` foi definido como `True`. A porcentagem concluída é atualizada apenas no primeiro caso.  
  
#### <a name="to-run-the-program"></a>Para executar o programa  
  
1. Pressione F5 para colocar o projeto no modo de execução.  
  
2. Clique no botão **Iniciar tarefa** . Cada vez que `PercentDone` o evento é gerado, o rótulo é atualizado com a porcentagem da tarefa concluída.  
  
3. Clique no botão **Cancelar** para interromper a tarefa. Observe que a aparência do botão **Cancelar** não é alterada imediatamente quando você clica nele. O `Click` evento não pode acontecer até `My.Application.DoEvents` que a instrução permita o processamento de eventos.  
  
    > [!NOTE]
    > O `My.Application.DoEvents` método não processa eventos exatamente da mesma forma que o formulário. Por exemplo, neste tutorial, você deve clicar no botão **Cancelar** duas vezes. Para permitir que o formulário manipule os eventos diretamente, você pode usar multithreading. Para obter mais informações, consulte [Threading gerenciado](../../../../standard/threading/index.md).
  
 Talvez você ache instrutivo a executar o programa com F11 e percorrer o código uma linha por vez. Você pode ver claramente como a execução `LongTask`entra e, em seguida, reinsere `Form1` brevemente cada `PercentDone` vez que o evento é gerado.  
  
 O que aconteceria se, enquanto a execução estava de volta no `Form1`código de `LongTask` , o método fosse chamado novamente? No pior, pode ocorrer um estouro de pilha `LongTask` se fosse chamado toda vez que o evento foi gerado.  
  
 Você pode fazer com que `mWidget` a variável manipule eventos para um `Widget` objeto diferente atribuindo uma referência ao novo `Widget` para `mWidget`. Na verdade, você pode fazer com que o `Button1_Click` código faça isso sempre que clicar no botão.  
  
#### <a name="to-handle-events-for-a-different-widget"></a>Para manipular eventos para um widget diferente  
  
- Adicione a seguinte linha de código ao `Button1_Click` procedimento, imediatamente antes da linha que lê: `mWidget.LongTask(12.2, 0.33)`  
  
     [!code-vb[VbVbcnWalkthroughDeclaringAndRaisingEvents#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnWalkthroughDeclaringAndRaisingEvents/VB/Form1.vb#9)]  
  
 O código acima cria um novo `Widget` cada vez que o botão é clicado. Assim que o `LongTask` método é concluído, a referência `Widget` ao é liberada e o `Widget` é destruído.  
  
 Uma `WithEvents` variável pode conter apenas uma referência de objeto por vez, portanto, se você atribuir um `Widget` objeto diferente `mWidget`ao, os `Widget` eventos do objeto anterior não serão mais manipulados. Se `mWidget` é a única variável de objeto que contém uma referência ao `Widget`antigo, o objeto é destruído. Se você quiser manipular eventos de vários `Widget` objetos, use a `AddHandler` instrução para processar eventos de cada objeto separadamente.  
  
> [!NOTE]
> Você pode declarar `WithEvents` quantas variáveis forem necessárias, mas não há suporte `WithEvents` para matrizes de variáveis.  
  
## <a name="see-also"></a>Consulte também

- [Passo a passo: Declarando e gerando eventos](../../../../visual-basic/programming-guide/language-features/events/walkthrough-declaring-and-raising-events.md)
- [Eventos](../../../../visual-basic/programming-guide/language-features/events/index.md)
