---
title: "Instru&#231;&#245;es passo a passo: declarando e acionando eventos (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "declarações, eventos"
  - "declarando eventos, explicações passo a passo"
  - "eventos [Visual Basic], declarando"
  - "eventos [Visual Basic], acionando"
  - "eventos [Visual Basic], explicações passo a passo"
  - "disparando eventos, explicações passo a passo"
ms.assetid: 8ffb3be8-097d-4d3c-b71e-04555ebda2a2
caps.latest.revision: 16
caps.handback.revision: 16
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Instru&#231;&#245;es passo a passo: declarando e acionando eventos (Visual Basic)
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

Essa explicação passo a passo demonstra como declarar e gerar eventos para uma classe denominada `Widget`.  Depois de completar os passos, você pode querer ler o tópico,[Instruções passo a passo: tratando eventos](../Topic/Walkthrough:%20Handling%20Events%20\(Visual%20Basic\).md), que mostra como utilizar eventos a partir de objetos `Widget` para fornecer informações de status em um aplicativo.  
  
## A classe Widget  
 Suponha, por enquanto, que você tenha uma classe `Widget`.  Sua classe `Widget`tem um método que pode levar bastante tempo para executar, e você deseja que o aplicativo seja capaz de colocar em backup algum tipo de indicador de conclusão.  
  
 É claro que você pode fazer o objeto `Widget` exibir uma caixa de diálogo percentualmente completa, mas depois você estaria preso a essa caixa de diálogo em cada projeto no qual você usasse a classe `Widget` .  Um bom princípio de construção de objeto é deixar que o aplicativo que usa um objeto manipule a interface com o usuário \- a não ser que o único propósito do objeto seja gerenciar um formulário ou uma caixa de diálogo.  
  
 O objetivo de `Widget` é realizar outras tarefas, de forma que seja melhor adicionar um evento `PercentDone` e deixar que o procedimento que chama os métodos  `Widget` manipule esse evento e exiba atualizações de status.  O evento  `PercentDone` também pode fornecer um mecanismo para cancelar a tarefa.  
  
#### Para criar o exemplo de código para este tópico  
  
1.  Abra um novo projeto de Aplicativo Windows [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] e crie um formulário com o nome `Form1`.  
  
2.  Adicione dois botões e um título para `Form1`.  
  
3.  Nomeie os objetos como mostrado na tabela a seguir.  
  
    |Object|Propriedade|Configuração|  
    |------------|-----------------|------------------|  
    |`Button1`|`Text`|Iniciar tarefa|  
    |`Button2`|`Text`|Cancel|  
    |`Label`|`(Name)`, `Text`|lblPercentDone, 0|  
  
4.  No menu **Project**, escolha **Add Class** para adicionar uma classe denominada `Widget.vb` ao projeto.  
  
#### Para declarar um evento para a classe Widget  
  
-   Use a palavra\-chave `Event` para declarar um evento na classe `Widget`.  Observe que um evento pode ter argumentos `ByVal` e `ByRef`, como o evento `PercentDone` de `Widget` demonstra.  
  
     [!code-vb[VbVbcnWalkthroughDeclaringAndRaisingEvents#1](../../../../visual-basic/programming-guide/language-features/events/codesnippet/VisualBasic/walkthrough-declaring-and-raising-events_1.vb)]  
  
 Quando o objeto chamado recebe um evento `PercentDone` o argumento `Percent` contém a porcentagem da tarefa que já foi concluída.  O argumento `Cancel` pode ser configurado para `True` para cancelar o método que gerou o evento.  
  
> [!NOTE]
>  Você pode declarar argumentos de evento da mesma forma que você faz argumentos de procedimentos, com as seguintes exceções: Eventos não podem ter argumentos `Optional` ou `ParamArray`, e eventos não têm valor de retorno.  
  
 O `PercentDone` evento é gerado pela `LongTask` método da `Widget` classe.  `LongTask`leva dois argumentos: o período de tempo o método finge estar fazendo o trabalho e o intervalo mínimo de tempo antes de `LongTask` faz uma pausa para elevar a `PercentDone` evento.  
  
#### Para elevar o evento PercentDone  
  
1.  Para simplificar o acesso à propriedade `Timer` usada por essa classe, inclua uma declaração `Imports` no topo da seção de declarações do seu módulo de classe, acima da declaração `Class Widget`.  
  
     [!code-vb[VbVbcnWalkthroughDeclaringAndRaisingEvents#2](../../../../visual-basic/programming-guide/language-features/events/codesnippet/VisualBasic/walkthrough-declaring-and-raising-events_2.vb)]  
  
2.  Adicione o seguinte código à classe `Widget`:  
  
     [!code-vb[VbVbcnWalkthroughDeclaringAndRaisingEvents#3](../../../../visual-basic/programming-guide/language-features/events/codesnippet/VisualBasic/walkthrough-declaring-and-raising-events_3.vb)]  
  
 Quando seu aplicativo chama o método `LongTask`, a classe `Widget` gera o evento `PercentDone` a cada `MinimumInterval` segundos.  Quando um evento retorna, `LongTask` verifica se o argumento `Cancel` foi modificado para `True`.  
  
 Algumas isenções são necessárias aqui.  Para facilitar, o  procedimento `LongTask` considera que você sabe, de antemão, quanto tempo a tarefa vai levar para ser completada.  Isso é quase nunca o caso.  Dividir tarefas em partes do mesmo tamanho pode ser difícil, e frequentemente o que mais importa aos usuários é simplesmente a quantidade de tempo que passa antes de obter uma indicação de que algo está acontecendo.  
  
 Você pode ter observado outra falha neste exemplo.  A propriedade `Timer` retorna o número de segundos que passaram desde a meia\-noite, portanto, o aplicativo trava se foi iniciado logo antes da meia\-noite.  Uma abordagem mais cuidadosa para medição de tempo, faria com que condições de contorno fossem levadas em consideração, ou evitadas simultaneamente, utilizando propriedades tais como `Now`.  
  
 Agora que a `Widget` classe pode elevar eventos, você pode mover para a próxima junto.  [Instruções passo a passo: tratando eventos](../Topic/Walkthrough:%20Handling%20Events%20\(Visual%20Basic\).md)Demonstra como usar `WithEvents` para associar um manipulador de eventos com o `PercentDone` evento.  
  
## Consulte também  
 <xref:Microsoft.VisualBasic.DateAndTime.Timer%2A>   
 <xref:Microsoft.VisualBasic.DateAndTime.Now%2A>   
 [Instruções passo a passo: tratando eventos](../Topic/Walkthrough:%20Handling%20Events%20\(Visual%20Basic\).md)   
 [Eventos](../../../../visual-basic/programming-guide/language-features/events/events.md)