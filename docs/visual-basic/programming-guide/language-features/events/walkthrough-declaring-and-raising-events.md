---
title: Declarando e acionando eventos (Visual Basic) | Documentos do Microsoft
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- declarations, events
- events [Visual Basic], walkthroughs
- declaring events, walkthroughs
- events [Visual Basic], declaring
- events [Visual Basic], raising
- raising events, walkthroughs
ms.assetid: 8ffb3be8-097d-4d3c-b71e-04555ebda2a2
caps.latest.revision: 16
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 233673c1d42684b7caa9042d18fb341a1043a31b
ms.lasthandoff: 03/13/2017

---
# <a name="walkthrough-declaring-and-raising-events-visual-basic"></a>Instruções passo a passo: declarando e acionando eventos (Visual Basic)
Este passo a passo demonstra como declarar e gerar eventos para uma classe denominada `Widget`. Depois de concluir as etapas, você talvez queira ler o tópico [passo a passo: Manipulando eventos](../../../../visual-basic/programming-guide/language-features/events/walkthrough-handling-events.md), que mostra como usar eventos de `Widget` objetos para fornecer informações de status em um aplicativo.  
  
## <a name="the-widget-class"></a>A classe Widget  
 Suponha que você tem um `Widget` classe. O `Widget` classe tem um método que pode levar muito tempo para executar, e você deseja que o aplicativo seja capaz de colocar em backup algum tipo de indicador de conclusão.  
  
 Obviamente, você pode fazer o `Widget` objeto mostrar uma caixa de diálogo de porcentagem de conclusão, mas, em seguida, você estaria preso a caixa de diálogo em cada projeto que você usou o `Widget` classe. Um princípio de design do objeto é permitir que o aplicativo que usa um identificador de objeto da interface do usuário — a menos que seja o único propósito do objeto gerenciar uma caixa de diálogo ou formulário.  
  
 A finalidade do `Widget` é realizar outras tarefas, portanto, é melhor adicionar um `PercentDone` evento e deixar que o procedimento que chama `Widget`do métodos lidar com atualizações de status de evento e a exibição. O `PercentDone` evento também pode fornecer um mecanismo para cancelar a tarefa.  
  
#### <a name="to-build-the-code-example-for-this-topic"></a>Para compilar o exemplo de código para este tópico  
  
1.  Abra uma nova [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] aplicativo do Windows do projeto e criar um formulário chamado `Form1`.  
  
2.  Adicione dois botões e um rótulo para `Form1`.  
  
3.  Nomeie os objetos como mostrado na tabela a seguir.  
  
    |Objeto|Propriedade|Configuração|  
    |------------|--------------|-------------|  
    |`Button1`|`Text`|Iniciar tarefa|  
    |`Button2`|`Text`|Cancelar|  
    |`Label`|`(Name)`, `Text`|lblPercentDone, 0|  
  
4.  Sobre o **projeto** menu, escolha **Add Class** para adicionar uma classe denominada `Widget.vb` ao projeto.  
  
#### <a name="to-declare-an-event-for-the-widget-class"></a>Para declarar um evento para a classe Widget  
  
-   Use o `Event` palavra-chave para declarar um evento na `Widget` classe. Observe que um evento pode ter `ByVal` e `ByRef` argumentos, como `Widget`do `PercentDone` evento demonstra:  
  
     [!code-vb[VbVbcnWalkthroughDeclaringAndRaisingEvents n º&1;](../../../../visual-basic/programming-guide/language-features/events/codesnippet/VisualBasic/walkthrough-declaring-and-raising-events_1.vb)]  
  
 Quando o objeto de chamada recebe uma `PercentDone` evento, o `Percent` argumento contém a porcentagem da tarefa que foi concluída. O `Cancel` argumento pode ser definido como `True` para cancelar o método que gerou o evento.  
  
> [!NOTE]
>  Você pode declarar argumentos de evento, assim como você faz argumentos de procedimentos, com as seguintes exceções: eventos não podem ter `Optional` ou `ParamArray` argumentos e eventos não têm valores de retorno.  
  
 O `PercentDone` é gerado pelo `LongTask` método o `Widget` classe. `LongTask`leva dois argumentos: o período de tempo que o método estaria estar fazendo o trabalho e o intervalo de tempo mínimo antes de `LongTask` pare de gerar o `PercentDone` evento.  
  
#### <a name="to-raise-the-percentdone-event"></a>Para elevar o evento PercentDone  
  
1.  Para simplificar o acesso para o `Timer` propriedade usada por essa classe, adicione uma `Imports` instrução na parte superior da seção de declarações do seu módulo de classe, acima de `Class Widget` instrução.  
  
     [!code-vb[VbVbcnWalkthroughDeclaringAndRaisingEvents n º&2;](../../../../visual-basic/programming-guide/language-features/events/codesnippet/VisualBasic/walkthrough-declaring-and-raising-events_2.vb)]  
  
2.  Adicione o seguinte código à classe `Widget`:  
  
     [!code-vb[VbVbcnWalkthroughDeclaringAndRaisingEvents n º&3;](../../../../visual-basic/programming-guide/language-features/events/codesnippet/VisualBasic/walkthrough-declaring-and-raising-events_3.vb)]  
  
 Quando o aplicativo chama o `LongTask` método, o `Widget` classe gera o `PercentDone` evento cada `MinimumInterval` segundos. Quando um evento retorna, `LongTask` verifica se o `Cancel` argumento foi definido como `True`.  
  
 Algumas isenções são necessárias aqui. Para simplificar, o `LongTask` procedimento pressupõe que você saiba com antecedência quanto tempo levará a tarefa. Isso é quase nunca o caso. Dividir tarefas em partes do mesmo tamanho pode ser difícil, e geralmente o que mais importa aos usuários é simplesmente a quantidade de tempo que passa antes de obter uma indicação de que algo está acontecendo.  
  
 Você pode ter observado outra falha neste exemplo. O `Timer` propriedade retorna o número de segundos decorridos desde a meia-noite; portanto, o aplicativo fica preso se ele for iniciado antes de meia-noite. Uma abordagem mais cuidadosa para medição de tempo levariam condições de limite como isso em consideração, ou evitadas simultaneamente, utilizando propriedades tais como `Now`.  
  
 Agora que o `Widget` classe pode gerar eventos, você pode mover para a próximo passo a passo. [Passo a passo: Manipulação de eventos](../../../../visual-basic/programming-guide/language-features/events/walkthrough-handling-events.md) demonstra como usar `WithEvents` para associar um manipulador de evento com o `PercentDone` evento.  
  
## <a name="see-also"></a>Consulte também  
 <xref:Microsoft.VisualBasic.DateAndTime.Timer%2A></xref:Microsoft.VisualBasic.DateAndTime.Timer%2A>   
 <xref:Microsoft.VisualBasic.DateAndTime.Now%2A></xref:Microsoft.VisualBasic.DateAndTime.Now%2A>   
 [Passo a passo: Manipulando eventos](../../../../visual-basic/programming-guide/language-features/events/walkthrough-handling-events.md)   
 [Eventos](../../../../visual-basic/programming-guide/language-features/events/index.md)
