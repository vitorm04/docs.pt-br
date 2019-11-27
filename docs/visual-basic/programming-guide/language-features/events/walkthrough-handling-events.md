---
title: Tratando eventos
ms.date: 07/20/2015
helpviewer_keywords:
- event handling [Visual Basic], walkthroughs
- walkthroughs [Visual Basic], event handling
- variables [Visual Basic], WithEvents
- events [Visual Basic], walkthroughs
- WithEvents keyword [Visual Basic], walkthroughs
- event handlers [Visual Basic], walkthroughs
ms.assetid: f145b3fc-5ae0-4509-a2aa-1ff6934706bd
ms.openlocfilehash: cb42f2e41e366cf8765cb9395d1a5641434bab40
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74345077"
---
# <a name="walkthrough-handling-events-visual-basic"></a>Instruções passo a passo: tratando eventos (Visual Basic)
Este é o segundo de dois tópicos que demonstram como trabalhar com eventos. O primeiro tópico, [Walkthrough: declarando e gerando eventos](../../../../visual-basic/programming-guide/language-features/events/walkthrough-declaring-and-raising-events.md), mostra como declarar e gerar eventos. Esta seção usa o formulário e a classe desse passo a passos para mostrar como tratar eventos quando eles ocorrem.  
  
 O exemplo da classe `Widget` usa instruções tradicionais de manipulação de eventos. Visual Basic fornece outras técnicas para trabalhar com eventos. Como um exercício, você pode modificar este exemplo para usar as instruções `AddHandler` e `Handles`.  
  
### <a name="to-handle-the-percentdone-event-of-the-widget-class"></a>Para manipular o evento PercentDone da classe Widget  
  
1. Coloque o seguinte código no `Form1`:  
  
     [!code-vb[VbVbcnWalkthroughDeclaringAndRaisingEvents#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnWalkthroughDeclaringAndRaisingEvents/VB/Form1.vb#4)]  
  
     A palavra-chave `WithEvents` especifica que a variável `mWidget` é usada para lidar com os eventos de um objeto. Você especifica o tipo de objeto fornecendo o nome da classe da qual o objeto será criado.  
  
     A variável `mWidget` é declarada em `Form1` porque `WithEvents` variáveis devem ser de nível de classe. Isso é verdadeiro independentemente do tipo de classe em que você os coloca.  
  
     A variável `mblnCancel` é usada para cancelar o método `LongTask`.  
  
## <a name="writing-code-to-handle-an-event"></a>Escrevendo código para manipular um evento  
 Assim que você declarar uma variável usando `WithEvents`, o nome da variável aparecerá na lista suspensa à esquerda do **Editor de código**da classe. Quando você seleciona `mWidget`, os eventos da classe `Widget` aparecem na lista suspensa à direita. A seleção de um evento exibe o procedimento de evento correspondente, com o prefixo `mWidget` e um sublinhado. Todos os procedimentos de evento associados a uma variável `WithEvents` recebem o nome da variável como um prefixo.  
  
#### <a name="to-handle-an-event"></a>Para identificar um evento  
  
1. Selecione `mWidget` na lista suspensa à esquerda no **Editor de código**.  
  
2. Selecione o evento `PercentDone` na lista suspensa à direita. O **Editor de código** abre o procedimento de evento `mWidget_PercentDone`.  
  
    > [!NOTE]
    > O **Editor de código** é útil, mas não obrigatório, para inserir novos manipuladores de eventos. Neste tutorial, é mais direto copiar apenas os manipuladores de eventos diretamente em seu código.  
  
3. Adicione o seguinte código ao manipulador de eventos do `mWidget_PercentDone`:  
  
     [!code-vb[VbVbcnWalkthroughDeclaringAndRaisingEvents#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnWalkthroughDeclaringAndRaisingEvents/VB/Form1.vb#5)]  
  
     Sempre que o evento de `PercentDone` é gerado, o procedimento de evento exibe a porcentagem concluída em um controle de `Label`. O método `DoEvents` permite que o rótulo seja redesenhado e também dá ao usuário a oportunidade de clicar no botão **Cancelar** .  
  
4. Adicione o seguinte código para o manipulador de eventos `Button2_Click`:  
  
     [!code-vb[VbVbcnWalkthroughDeclaringAndRaisingEvents#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnWalkthroughDeclaringAndRaisingEvents/VB/Form1.vb#6)]  
  
 Se o usuário clicar no botão **Cancelar** enquanto `LongTask` estiver em execução, o evento `Button2_Click` será executado assim que a instrução `DoEvents` permitir que o processamento de eventos ocorra. A variável no nível de classe `mblnCancel` é definida como `True`, e o evento `mWidget_PercentDone` então o testa e define o argumento `ByRef Cancel` como `True`.  
  
## <a name="connecting-a-withevents-variable-to-an-object"></a>Conectando uma variável WithEvents a um objeto  
 `Form1` agora está configurado para manipular os eventos de um objeto de `Widget`. Tudo o que resta é encontrar um `Widget` em algum lugar.  
  
 Quando você declara uma variável `WithEvents` em tempo de design, nenhum objeto é associado a ela. Uma variável `WithEvents` é assim como qualquer outra variável de objeto. Você precisa criar um objeto e atribuir uma referência a ele com a variável `WithEvents`.  
  
#### <a name="to-create-an-object-and-assign-a-reference-to-it"></a>Para criar um objeto e atribuir uma referência a ele  
  
1. Selecione **(eventos Form1)** na lista suspensa à esquerda no **Editor de código**.  
  
2. Selecione o evento `Load` na lista suspensa à direita. O **Editor de código** abre o procedimento de evento `Form1_Load`.  
  
3. Adicione o seguinte código para o procedimento de evento `Form1_Load` para criar o `Widget`:  
  
     [!code-vb[VbVbcnWalkthroughDeclaringAndRaisingEvents#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnWalkthroughDeclaringAndRaisingEvents/VB/Form1.vb#7)]  
  
 Quando esse código é executado, Visual Basic cria um objeto `Widget` e conecta seus eventos aos procedimentos de evento associados ao `mWidget`. Desse ponto em diante, sempre que o `Widget` gera seu evento `PercentDone`, o procedimento de evento `mWidget_PercentDone` é executado.  
  
#### <a name="to-call-the-longtask-method"></a>Para chamar o método LongTask  
  
- Adicione o seguinte código ao manipulador de eventos do `Button1_Click`:  
  
     [!code-vb[VbVbcnWalkthroughDeclaringAndRaisingEvents#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnWalkthroughDeclaringAndRaisingEvents/VB/Form1.vb#8)]  
  
 Antes que o método `LongTask` seja chamado, o rótulo que exibe a porcentagem concluída deve ser inicializado e o sinalizador de `Boolean` de nível de classe para cancelar o método deve ser definido como `False`.  
  
 `LongTask` é chamado com uma duração de tarefa de 12,2 segundos. O evento `PercentDone` é gerado uma vez a cada um terço de um segundo. Cada vez que o evento é gerado, o procedimento de evento `mWidget_PercentDone` é executado.  
  
 Quando `LongTask` é feito, `mblnCancel` é testado para ver se `LongTask` foi encerrado normalmente ou se foi interrompido porque `mblnCancel` foi definido como `True`. A porcentagem concluída é atualizada apenas no primeiro caso.  
  
#### <a name="to-run-the-program"></a>Para executar o programa  
  
1. Pressione F5 para colocar o projeto no modo de execução.  
  
2. Clique no botão **Iniciar tarefa** . Cada vez que o evento de `PercentDone` é gerado, o rótulo é atualizado com a porcentagem da tarefa concluída.  
  
3. Clique no botão **Cancelar** para interromper a tarefa. Observe que a aparência do botão **Cancelar** não é alterada imediatamente quando você clica nele. O evento `Click` não pode acontecer até que a instrução `My.Application.DoEvents` permita o processamento de eventos.  
  
    > [!NOTE]
    > O método `My.Application.DoEvents` não processa eventos exatamente da mesma forma que o formulário. Por exemplo, neste tutorial, você deve clicar no botão **Cancelar** duas vezes. Para permitir que o formulário manipule os eventos diretamente, você pode usar multithreading. Para obter mais informações, consulte [Threading gerenciado](../../../../standard/threading/index.md).
  
 Talvez você ache instrutivo a executar o programa com F11 e percorrer o código uma linha por vez. Você pode ver claramente como a execução entra `LongTask`e, em seguida, reinserir brevemente `Form1` cada vez que o evento `PercentDone` for gerado.  
  
 O que aconteceria se, enquanto a execução estava de volta no código de `Form1`, o método `LongTask` foi chamado novamente? No pior, pode ocorrer um estouro de pilha se `LongTask` fosse chamado toda vez que o evento foi gerado.  
  
 Você pode fazer com que a variável `mWidget` manipule eventos para um objeto `Widget` diferente atribuindo uma referência à nova `Widget` para `mWidget`. Na verdade, você pode tornar o código em `Button1_Click` fazer isso sempre que clicar no botão.  
  
#### <a name="to-handle-events-for-a-different-widget"></a>Para manipular eventos para um widget diferente  
  
- Adicione a seguinte linha de código ao procedimento `Button1_Click`, imediatamente antes da linha que lê `mWidget.LongTask(12.2, 0.33)`:  
  
     [!code-vb[VbVbcnWalkthroughDeclaringAndRaisingEvents#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnWalkthroughDeclaringAndRaisingEvents/VB/Form1.vb#9)]  
  
 O código acima cria um novo `Widget` cada vez que o botão é clicado. Assim que o método de `LongTask` é concluído, a referência ao `Widget` é liberada e o `Widget` é destruído.  
  
 Uma variável `WithEvents` pode conter apenas uma referência de objeto por vez, portanto, se você atribuir um objeto de `Widget` diferente para `mWidget`, os eventos do objeto `Widget` anterior não serão mais manipulados. Se `mWidget` for a única variável de objeto que contém uma referência ao `Widget`antigo, o objeto será destruído. Se você quiser manipular eventos de vários objetos `Widget`, use a instrução `AddHandler` para processar eventos de cada objeto separadamente.  
  
> [!NOTE]
> Você pode declarar quantas variáveis `WithEvents` forem necessárias, mas não há suporte para matrizes de `WithEvents` variáveis.  
  
## <a name="see-also"></a>Consulte também

- [Instruções passo a passo: declarando e acionando eventos](../../../../visual-basic/programming-guide/language-features/events/walkthrough-declaring-and-raising-events.md)
- [Eventos](../../../../visual-basic/programming-guide/language-features/events/index.md)
