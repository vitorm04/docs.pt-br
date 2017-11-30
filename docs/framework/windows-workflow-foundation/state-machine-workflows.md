---
title: Fluxos de trabalho do computador de estado
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 344caacd-bf3b-4716-bd5a-eca74fc5a61d
caps.latest.revision: "16"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 23f903af1bfb63ac5d0b800656e7264d0f9d8b9b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="state-machine-workflows"></a>Fluxos de trabalho do computador de estado
Um computador de estado é um paradigma conhecido para programas desenvolvimento. A atividade de <xref:System.Activities.Statements.StateMachine> , juntamente com <xref:System.Activities.Statements.State>, <xref:System.Activities.Statements.Transition>, e outras atividades pode ser usada para criar programas de fluxo de trabalho do computador de estado. Este tópico fornece uma visão geral de criar fluxos de trabalho do computador de estado.  
  
## <a name="state-machine-workflow-overview"></a>Visão geral de fluxo de trabalho do computador de estado  
 Fluxos de trabalho do computador de estado fornecem um estilo modelagem com que você pode modelar seu fluxo de trabalho em uma maneira de baseada. Uma atividade de <xref:System.Activities.Statements.StateMachine> contém os estados e as transições que compõem a lógica do computador de estado, e pode ser usada em qualquer lugar uma atividade pode ser usada. Há várias classes no tempo de execução do computador de estado:  
  
-   <xref:System.Activities.Statements.StateMachine>  
  
-   <xref:System.Activities.Statements.State>  
  
-   <xref:System.Activities.Statements.Transition>  
  
 Para criar um fluxo de trabalho do computador de estado, os estados são adicionados a uma atividade de <xref:System.Activities.Statements.StateMachine> , e as transições são controle usado o fluxo entre estados. Captura de tela a seguir, do [Tutorial de Introdução](../../../docs/framework/windows-workflow-foundation/getting-started-tutorial.md) etapa [como: criar um fluxo de trabalho de máquina de estado](../../../docs/framework/windows-workflow-foundation/how-to-create-a-state-machine-workflow.md), mostra um fluxo de trabalho de máquina de estado com três estados e transições de três. **Inicializar destino** é o estado inicial e representa o primeiro estado no fluxo de trabalho. Isso é designado pela linha à esquerda do **iniciar** nó. O estado final do fluxo de trabalho é denominado **FinalState**e representa o ponto em que o fluxo de trabalho é concluído.  
  
 ![Fluxo de trabalho de máquina de estado concluído](../../../docs/framework/windows-workflow-foundation/media/wfstatemachinegettingstartedtutorialcomplete.JPG "WFStateMachineGettingStartedTutorialComplete")  
  
 Um fluxo de trabalho do computador de estado deve ter um e somente um estados iniciais, e pelo menos um estados finais. Cada estado que não é um estado final deve ter pelo menos uma transição. As seções a seguir abordam como criar e configurar de estados e das transições.  
  
## <a name="creating-and-configuring-states"></a>Criando e configurando estados  
 <xref:System.Activities.Statements.State> representa um estado em que um computador de estado pode estar. Para adicionar um <xref:System.Activities.Statements.State> para um fluxo de trabalho, arraste o **estado** designer de atividade do **máquina de estado** seção o **caixa de ferramentas** e solte-a para um <xref:System.Activities.Statements.StateMachine> atividade no [!INCLUDE[wfd1](../../../includes/wfd1-md.md)] superfície.  
  
 ![WF4 Atividades da máquina de estado](../../../docs/framework/windows-workflow-foundation/media/netframework4platformupdate1statemachineactivities.jpg "NETFramework4PlatformUpdate1StateMachineActivities")  
  
 Para configurar um estado como o **estado inicial do**, o estado e selecione **definir como estado inicial do**. Além disso, se não houver nenhum estado inicial atual, o estado inicial pode ser designado, arrastando uma linha do **iniciar** nó na parte superior do fluxo de trabalho para o estado desejado. Quando um <xref:System.Activities.Statements.StateMachine> atividade é descartada no designer de fluxo de trabalho, ele é pré-configurado com um estado inicial denominado **State1**. Um fluxo de trabalho do computador de estado deve ter um e somente um estados iniciais.  
  
 Um estado que representa um estado de terminação em um computador de estado é chamado um estado final. Um estado final é um estado que tem sua propriedade de <xref:System.Activities.Statements.State.IsFinal%2A> definida como `true`, não tem nenhuma atividade de <xref:System.Activities.Statements.State.Exit%2A> , e nenhuma transição que se origina delas. Para adicionar um estado final para um fluxo de trabalho, arraste um **FinalState** designer de atividade do **máquina de estado** seção o **caixa de ferramentas** e solte-a para um <xref:System.Activities.Statements.StateMachine> atividade em o [!INCLUDE[wfd1](../../../includes/wfd1-md.md)] superfície. Um fluxo de trabalho do computador de estado deve ter pelo menos um estado final.  
  
### <a name="configuring-entry-and-exit-actions"></a>Configurando ações de entrada e de saída  
 Um estado pode ter <xref:System.Activities.Statements.State.Entry%2A> e uma ação de <xref:System.Activities.Statements.State.Exit%2A> . (O estado de configurado como um estado final pode ter apenas uma ação de entrada). Quando uma instância de fluxo de trabalho entra em um estado, todas as atividades em ação de entrada são executadas. Quando a ação de entrada estiver concluída, disparadores para as transições de estado estão agendados. Quando uma transição para outro estado é confirmada, as atividades em ação de saída são executadas, mesmo se o estado faz a transição de volta ao mesmo estado. Depois que a ação de saída for concluída, as atividades em ação de transição, e executam o novo estado é feito à transição, e suas ações de entrada são agendadas.  
  
> [!NOTE]
>  Para depurar um fluxo de trabalho do computador de estado, pontos de interrupção podem ser colocados na atividade e os estados do computador de estado da raiz no fluxo de trabalho do computador de estado. Os pontos de interrupção não podem ser colocados diretamente nas transições, mas podem ser colocados em todas as atividades contidas nos estados e as transições.  
  
## <a name="creating-and-configuring-transitions"></a>Criando e configurando as transições  
 Todos os estados devem ter pelo menos uma transição, exceto para um estado final que não tenha nenhuma transições. Transições podem ser adicionadas após um estado é adicionado a um fluxo de trabalho do computador de estado, ou podem ser criadas como o estado são soltas.  
  
 Para adicionar um <xref:System.Activities.Statements.State> e criar uma transição em uma única etapa, arraste um **estado** atividade do **máquina de estado** seção o **caixa de ferramentas** e passe o mouse sobre o estado de outro em o designer de fluxo de trabalho. Quando <xref:System.Activities.Statements.State> arrastado está sobre um outro <xref:System.Activities.Statements.State>, quatro triângulos aparecerão em torno do outro <xref:System.Activities.Statements.State>. Se <xref:System.Activities.Statements.State> é solto em um dos quatro triângulos, é adicionado ao computador de estado e uma transição é criada de origem <xref:System.Activities.Statements.State> ao destino solto <xref:System.Activities.Statements.State>. Para obter mais informações, consulte [Designer de atividade de transição](/visualstudio/workflow-designer/transition-activity-designer).  
  
 Para criar uma transição após um estado é adicionado, existem duas opções. A primeira opção é arraste o estado da superfície do designer de fluxo de trabalho e focalizar-lo sobre um estado existente e solte-o em um dos pontos da operação. Isso é muito semelhante ao método descrito na seção anterior. Você pode também passa o mouse sobre o estado desejado de origem, e arraste uma linha para o estado desejado de destino.  
  
> [!NOTE]
>  Um único estado em um computador de estado pode ter até 76 transições criadas utilizando o designer de fluxo de trabalho. O limite nas transições para um estado para fluxos de trabalho criados fora de designer é delimitado somente por recursos do sistema.  
  
 Uma transição pode ter <xref:System.Activities.Statements.Transition.Trigger%2A>, <xref:System.Activities.Statements.Transition.Condition%2A>, e <xref:System.Activities.Statements.Transition.Action%2A>. <xref:System.Activities.Statements.Transition.Trigger%2A> de uma transição é agendada quando a ação de <xref:System.Activities.Statements.State.Entry%2A> de estado da fonte de transição é concluída. Normalmente <xref:System.Activities.Statements.Transition.Trigger%2A> é uma atividade que espera qualquer tipo de evento ocorra, mas pode ser qualquer atividade, ou nenhuma atividade de todo. Uma vez que a atividade de <xref:System.Activities.Statements.Transition.Trigger%2A> estiver concluída, <xref:System.Activities.Statements.Transition.Condition%2A>, se presentes, é avaliada. Se não houver nenhuma atividade de <xref:System.Activities.Statements.Transition.Trigger%2A> em <xref:System.Activities.Statements.Transition.Condition%2A> é avaliado imediatamente. Se a condição for avaliada como `false`, a transição é cancelada, e quaisquer atividades de <xref:System.Activities.Statements.Transition.Trigger%2A> para faz a transição de estado é reprogramada. Se existem outras transições que compartilham o mesmo estado de origem que a transição atual, essas ações de <xref:System.Activities.Statements.Transition.Trigger%2A> são canceladas e reprogramadas também. Se <xref:System.Activities.Statements.Transition.Condition%2A> avalia a `true`, ou não há nenhuma condição, então a ação de <xref:System.Activities.Statements.State.Exit%2A> de estado de origem é executada, e <xref:System.Activities.Statements.Transition.Action%2A> de transição é executado em seguida. Quando o <xref:System.Activities.Statements.Transition.Action%2A> for concluída, o controle passará para o **destino** estado  
  
 Faz a transição que compartilham um disparador comum é conhecido como o disparador compartilhado transições. Cada transição em um grupo de transições compartilhadas do disparador tem o mesmo disparador, mas <xref:System.Activities.Statements.Transition.Condition%2A> e uma ação exclusivos. Para adicionar ações adicionais para uma transição e criar uma transição compartilhada, clique no círculo que indica o início de transição desejada e arraste-o para estado desejado. A nova transição compartilhar um disparador mesmo que a transição inicial, mas terá uma condição e uma ação exclusivos. Transições compartilhadas também podem ser criadas de dentro do designer de transição clicando **adicionar compartilhado transição de gatilho** na parte inferior do designer de transição e, em seguida, selecionar o estado de destino desejado do  **Estados disponíveis para conexão** lista suspensa.  
  
> [!NOTE]
>  Observe que se <xref:System.Activities.Statements.Transition.Condition%2A> de uma transição for avaliada como `False` (ou todas as condições de uma transição do gatilho compartilhada for avaliada como `False`), a transição não ocorrerá e todos os gatilhos para todas as transições de estado serão reprogramados.  
  
 Para obter mais informações sobre a criação de fluxos de trabalho de máquina de estado, consulte [como: criar um fluxo de trabalho de máquina de estado](../../../docs/framework/windows-workflow-foundation/how-to-create-a-state-machine-workflow.md), [Designer de atividade de StateMachine](/visualstudio/workflow-designer/statemachine-activity-designer), [Designer de atividade de estado](/visualstudio/workflow-designer/state-activity-designer), [Designer de atividade de FinalState](/visualstudio/workflow-designer/finalstate-activity-designer), e [transição o Designer de atividade](/visualstudio/workflow-designer/transition-activity-designer).  
  
## <a name="state-machine-terminology"></a>Terminologia do computador de estado  
 Esta seção define o vocabulário do computador de estado usado em todo este tópico.  
  
 Estado  
 A unidade básica que compõem um computador de estado. Um computador de estado pode estar em um estado em todas as hora.  
  
 Ação de entrada  
 Uma atividade executada ao inserir no estado  
  
 Ação de saída  
 Uma atividade executada quando deixar o estado  
  
 Transição  
 Direcionada uma relação entre dois estados que representa a resposta completo de um computador de estado para uma ocorrência de um evento de um tipo específico.  
  
 Transição compartilhada  
 Uma transição que compartilhar um estado de origem e o disparador com um ou mais faz a transição, mas tem uma condição e uma ação exclusivos.  
  
 Disparador  
 Uma atividade disparando que faz com que uma transição ocorre.  
  
 Condição  
 Uma restrição que deve ser avaliada como `true` após o disparador ocorre a transição para que ela seja concluída.  
  
 Ação de transição  
 Uma atividade que é executada ao executar alguma transição.  
  
 Transição condicional  
 Uma transição com uma condição explícita.  
  
 Dica transição  
 Uma transição que transite por de um estado para se.  
  
 Estado inicial  
 Um estado que representa o ponto de partida do computador de estado.  
  
 Estado final  
 Um estado que representa a conclusão do computador de estado.  
  
## <a name="see-also"></a>Consulte também  
 [Como criar um fluxo de trabalho de máquina de estado](../../../docs/framework/windows-workflow-foundation/how-to-create-a-state-machine-workflow.md)  
 [Designer de atividade StateMachine](/visualstudio/workflow-designer/statemachine-activity-designer)  
 [Designer de atividade de estado](/visualstudio/workflow-designer/state-activity-designer)  
 [Designer de atividade FinalState](/visualstudio/workflow-designer/finalstate-activity-designer)  
 [Designer de atividade Transition](/visualstudio/workflow-designer/transition-activity-designer)
