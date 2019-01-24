---
title: Manipulação de eventos (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- event handling [Visual Basic], walkthroughs
- walkthroughs [Visual Basic], event handling
- variables [Visual Basic], WithEvents
- events [Visual Basic], walkthroughs
- WithEvents keyword [Visual Basic], walkthroughs
- event handlers [Visual Basic], walkthroughs
ms.assetid: f145b3fc-5ae0-4509-a2aa-1ff6934706bd
ms.openlocfilehash: 2af8fe5557e452db1ef3a72de35582b18117cc30
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54553731"
---
# <a name="walkthrough-handling-events-visual-basic"></a>Passo a passo: Manipulação de eventos (Visual Basic)
Este é o segundo dos dois tópicos que demonstram como trabalhar com eventos. O primeiro tópico, [passo a passo: Declarando e acionando eventos](../../../../visual-basic/programming-guide/language-features/events/walkthrough-declaring-and-raising-events.md), mostra como declarar e acionar eventos. Esta seção usa o formulário e a classe esse passo a passo para mostrar como manipular eventos quando eles ocorrem.  
  
 O `Widget` usa o exemplo de classe tradicionais instruções de manipulação de eventos. Visual Basic fornece outras técnicas para trabalhar com eventos. Como um exercício, você pode modificar esse exemplo para usar o `AddHandler` e `Handles` instruções.  
  
### <a name="to-handle-the-percentdone-event-of-the-widget-class"></a>Para manipular o evento PercentDone da classe Widget  
  
1.  Coloque o seguinte código no `Form1`:  
  
     [!code-vb[VbVbcnWalkthroughDeclaringAndRaisingEvents#4](../../../../visual-basic/programming-guide/language-features/events/codesnippet/VisualBasic/walkthrough-handling-events_1.vb)]  
  
     O `WithEvents` palavra-chave especifica que a variável `mWidget` é usada para manipular eventos de um objeto. Você pode especificar o tipo de objeto, fornecendo o nome da classe da qual o objeto será criado.  
  
     A variável `mWidget` declarado em `Form1` porque `WithEvents` variáveis devem ser o nível de classe. Isso é verdadeiro independentemente do tipo de classe em que é colocá-los.  
  
     A variável `mblnCancel` é usado para cancelar o `LongTask` método.  
  
## <a name="writing-code-to-handle-an-event"></a>Escrevendo código para manipular um evento  
 Assim que você declara uma variável usando `WithEvents`, o nome da variável é exibida na lista suspensa à esquerda da classe **Editor de códigos**. Quando você seleciona `mWidget`, o `Widget` eventos da classe aparecem na lista suspensa à direita. Selecionando um evento exibe o procedimento de evento correspondente, com o prefixo `mWidget` e um caractere de sublinhado. Todos os procedimentos de evento associados com um `WithEvents` variável recebem o nome da variável como um prefixo.  
  
#### <a name="to-handle-an-event"></a>Para identificar um evento  
  
1.  Selecione `mWidget` na lista suspensa à esquerda na **Editor de códigos**.  
  
2.  Selecione o `PercentDone` evento na lista suspensa à direita. O **Editor de códigos** abre o `mWidget_PercentDone` procedimento de evento.  
  
    > [!NOTE]
    >  O **Editor de códigos** é útil, mas não obrigatórios, para a inserção de novos manipuladores de eventos. Neste passo a passo, é mais direto para copiar apenas os manipuladores de eventos diretamente no seu código.  
  
3.  Adicione o seguinte código ao manipulador de eventos do `mWidget_PercentDone`:  
  
     [!code-vb[VbVbcnWalkthroughDeclaringAndRaisingEvents#5](../../../../visual-basic/programming-guide/language-features/events/codesnippet/VisualBasic/walkthrough-handling-events_2.vb)]  
  
     Sempre que o `PercentDone` é gerado, o procedimento de evento exibe a porcentagem concluída em um `Label` controle. O `DoEvents` método permite que o rótulo a ser redesenhado e também fornece ao usuário a oportunidade de clicar o **Cancelar** botão.  
  
4.  Adicione o seguinte código para o `Button2_Click` manipulador de eventos:  
  
     [!code-vb[VbVbcnWalkthroughDeclaringAndRaisingEvents#6](../../../../visual-basic/programming-guide/language-features/events/codesnippet/VisualBasic/walkthrough-handling-events_3.vb)]  
  
 Se o usuário clica o **Cancelar** botão durante a `LongTask` estiver em execução, o `Button2_Click` eventos é executado assim que o `DoEvents` instrução permite o processamento de evento ocorra. A variável de nível de classe `mblnCancel` é definido como `True`e o `mWidget_PercentDone` eventos, em seguida, testa-lo e define o `ByRef Cancel` argumento `True`.  
  
## <a name="connecting-a-withevents-variable-to-an-object"></a>Conectar-se a uma variável WithEvents a um objeto  
 `Form1` agora está configurado para manipular um `Widget` eventos do objeto. Tudo o que resta é localizar um `Widget` em algum lugar.  
  
 Quando você declara uma variável `WithEvents` em tempo de design, nenhum objeto estiver associado a ele. Um `WithEvents` variável é exatamente como qualquer outra variável de objeto. Você precisa criar um objeto e atribuir uma referência a ele com o `WithEvents` variável.  
  
#### <a name="to-create-an-object-and-assign-a-reference-to-it"></a>Para criar um objeto e atribuir uma referência a ele  
  
1.  Selecione **(eventos de Form1)** na lista suspensa à esquerda na **Editor de códigos**.  
  
2.  Selecione o `Load` evento na lista suspensa à direita. O **Editor de códigos** abre o `Form1_Load` procedimento de evento.  
  
3.  Adicione o seguinte código para o `Form1_Load` procedimento de evento para criar o `Widget`:  
  
     [!code-vb[VbVbcnWalkthroughDeclaringAndRaisingEvents#7](../../../../visual-basic/programming-guide/language-features/events/codesnippet/VisualBasic/walkthrough-handling-events_4.vb)]  
  
 Quando esse código é executado, o Visual Basic cria um `Widget` do objeto e conecta seus eventos para os procedimentos de evento associados `mWidget`. Partir desse ponto, sempre que o `Widget` gera sua `PercentDone` evento, o `mWidget_PercentDone` procedimento de evento é executado.  
  
#### <a name="to-call-the-longtask-method"></a>Para chamar o método LongTask  
  
-   Adicione o seguinte código ao manipulador de eventos do `Button1_Click`:  
  
     [!code-vb[VbVbcnWalkthroughDeclaringAndRaisingEvents#8](../../../../visual-basic/programming-guide/language-features/events/codesnippet/VisualBasic/walkthrough-handling-events_5.vb)]  
  
 Antes do `LongTask` método é chamado, o rótulo que exibe o percentual de conclusão deve ser inicializado e o nível de classe `Boolean` sinalizador para cancelar o método deve ser definido como `False`.  
  
 `LongTask` é chamado com duração de uma tarefa de 12.2 segundos. O `PercentDone` é gerado uma vez cada um terço de um segundo. Cada vez que o evento é gerado, o `mWidget_PercentDone` procedimento de evento é executado.  
  
 Quando `LongTask` for feito, `mblnCancel` é testado para ver se `LongTask` terminou normalmente, ou se ele tiver parado porque `mblnCancel` foi definido como `True`. A porcentagem concluída é atualizada somente no caso anterior.  
  
#### <a name="to-run-the-program"></a>Para executar o programa  
  
1.  Pressione F5 para colocar o projeto no modo de execução.  
  
2.  Clique o **Iniciar tarefa** botão. Cada vez que o `PercentDone` é gerado, o rótulo será atualizado com a porcentagem da tarefa que foi concluída.  
  
3.  Clique o **Cancelar** no botão para parar a tarefa. Observe que a aparência do **Cancelar** botão não é alterado imediatamente quando você clica nele. O `Click` evento não pode ocorrer até que o `My.Application.DoEvents` instrução permite o processamento de eventos.  
  
    > [!NOTE]
    >  O `My.Application.DoEvents` método não processa os eventos exatamente da mesma maneira como faz o formulário. Por exemplo, este passo a passo, você deve clicar o **Cancelar** botão duas vezes. Para permitir que o formulário manipular os eventos diretamente, você pode usar multithreading. Para obter mais informações, consulte [Threading gerenciado](../../../../standard/threading/index.md).
  
 Talvez você ache instrutivos para executar o programa com F11 e percorrer o código uma linha por vez. Você pode ver claramente como execução insere `LongTask`e, em seguida, brevemente reinserido `Form1` cada vez que o `PercentDone` é gerado.  
  
 O que aconteceria se, durante a execução foi novamente no código de `Form1`, o `LongTask` método fosse chamada novamente? Na pior das hipóteses, um estouro de pilha pode ocorrer se `LongTask` foram chamados toda vez que o evento foi acionado.  
  
 Você pode fazer com que a variável `mWidget` para manipular eventos para outro `Widget` objeto atribuindo uma referência para a nova `Widget` para `mWidget`. Na verdade, você pode tornar o código em `Button1_Click` fazer isso sempre que você clicar no botão.  
  
#### <a name="to-handle-events-for-a-different-widget"></a>Para manipular eventos para um widget diferente  
  
-   Adicione a seguinte linha de código para o `Button1_Click` procedimento, logo após a linha que lê `mWidget.LongTask(12.2, 0.33)`:  
  
     [!code-vb[VbVbcnWalkthroughDeclaringAndRaisingEvents#9](../../../../visual-basic/programming-guide/language-features/events/codesnippet/VisualBasic/walkthrough-handling-events_6.vb)]  
  
 O código anterior cria um novo `Widget` cada vez que o botão é clicado. Assim que o `LongTask` método é concluído, a referência para o `Widget` é liberado e o `Widget` é destruído.  
  
 Um `WithEvents` variável pode conter referência de objeto apenas uma vez, portanto, se você atribuir outro `Widget` objeto `mWidget`, anterior `Widget` eventos do objeto não serão tratados. Se `mWidget` é a única variável de objeto que contém uma referência para o antigo `Widget`, o objeto é destruído. Se você quiser manipular eventos de vários `Widget` objetos, use o `AddHandler` instrução processar eventos de cada objeto separadamente.  
  
> [!NOTE]
>  Você pode declarar tantos `WithEvents` variáveis que você precisam. Porém, matrizes de `WithEvents` variáveis não são suportadas.  
  
## <a name="see-also"></a>Consulte também
- [Passo a passo: Declarando e acionando eventos](../../../../visual-basic/programming-guide/language-features/events/walkthrough-declaring-and-raising-events.md)
- [Eventos](../../../../visual-basic/programming-guide/language-features/events/index.md)
