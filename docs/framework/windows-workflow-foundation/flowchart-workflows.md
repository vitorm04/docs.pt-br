---
title: Fluxos de trabalho do fluxograma
ms.date: 03/30/2017
ms.assetid: b0a3475c-d22f-49eb-8912-973c960aebf5
ms.openlocfilehash: dd013e47da881c16d1fa469dfc3e3c4f2a86b6e2
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33514518"
---
# <a name="flowchart-workflows"></a>Fluxos de trabalho do fluxograma
Um fluxograma é um paradigma conhecido para criar programas. A atividade do fluxograma é normalmente usada para implementar fluxos de trabalho não-sequenciais, mas pode ser usada para fluxos de trabalho sequenciais se nenhum nó de `FlowDecision` é usado.  
  
## <a name="flowchart-workflow-structure"></a>Estrutura de fluxo de trabalho do fluxograma  
 Uma atividade do fluxograma é uma atividade que contém uma coleção de atividades a ser executadas.  Os fluxogramas também contêm os elementos de controle de fluxo como <xref:System.Activities.Statements.FlowDecision> e <xref:System.Activities.Statements.FlowSwitch%601> que a execução direta entre atividades contidas base nos valores das variáveis.  
  
## <a name="types-of-flow-nodes"></a>Tipos de nós de fluxo  
 Os diferentes tipos de elementos são usados dependendo do tipo de controle de fluxo necessária quando o elemento é executado. Os tipos de elementos fluxograma incluem:  
  
-   `FlowStep` - modelos uma etapa de execução no fluxograma.  
  
-   `FlowDecision` - ramificações de execução com base em uma condição boolean, semelhante a <xref:System.Activities.Statements.If>.  
  
-   `FlowSwitch` – ramificações de execução com base em uma opção exclusivo, semelhante a <xref:System.Activities.Statements.Switch%601>.  
  
 Cada link tem uma propriedade de `Action` que define <xref:System.Activities.ActivityAction> que pode ser usado para executar atividades filhos, e uma ou mais propriedades de `Next` que definem que elemento ou elementos a executar quando o elemento atual concluir a execução.  
  
### <a name="creating-a-basic-activity-sequence-with-a-flowstep-node"></a>Criando uma sequência básica de atividade com um nó de FlowStep  
 Para modelar uma sequência básica em duas atividades que executam por sua vez, o elemento de `FlowStep` é usado. No exemplo a seguir, dois elementos de `FlowStep` são usados para executar em ordem duas atividades.  
  
```xml  
<Flowchart>  
  <FlowStep>      
  <Assign DisplayName="Get Name">  
    <Assign.To>  
      <OutArgument x:TypeArguments="x:String">[result]</OutArgument>  
    </Assign.To>  
    <Assign.Value>  
      <InArgument x:TypeArguments="x:String">["User"]</InArgument>  
    </Assign.Value>  
  </Assign>  
    <FlowStep.Next>  
      <FlowStep>  
        <WriteLine Text="["Hello, " & result]"/>  
</FlowStep>  
    </FlowStep.Next>  
  </FlowStep>  
</Flowchart>  
```  
  
### <a name="creating-a-conditional-flowchart-with-a-flowdecision-node"></a>Criando um fluxograma condicional com um nó de FlowDecision  
 Para modelar um nó condicional de fluxo em um fluxo de trabalho do fluxograma (ou seja, para criar um link que funciona como o símbolo de decisão de um fluxograma tradicional), um nó de <xref:System.Activities.Statements.FlowDecision> é usado. A propriedade de <xref:System.Activities.Statements.FlowDecision.Condition%2A> do nó é definida como uma expressão que define a condição, e as propriedades de <xref:System.Activities.Statements.FlowDecision.True%2A> e de <xref:System.Activities.Statements.FlowDecision.False%2A> são definidas para as instâncias de <xref:System.Activities.Statements.FlowNode> a ser executadas se a expressão avaliada como `true` ou a `false`. O exemplo a seguir mostra como definir um fluxo de trabalho que usa um nó de <xref:System.Activities.Statements.FlowDecision> .  
  
```xml  
<Flowchart>  
  <FlowStep>  
    <Read Result="[s]"/>  
    <FlowStep.Next>  
      <FlowDecision>  
        <IsEmpty Input="[s]" />  
        <FlowDecision.True>  
    <FlowStep>  
            <Write Text="Empty"/>  
    </FlowStep>  
        </FlowDecision.True>  
        <FlowDecision.False>  
    <FlowStep>  
            <Write Text="Non-Empty"/>  
          </FlowStep>  
        </FlowDecision.False>  
      </FlowDecision>  
    </FlowStep.Next>  
  </FlowStep>  
</Flowchart>  
```  
  
### <a name="creating-an-exclusive-switch-with-a-flowswitch-node"></a>Criando uma opção exclusivo com um nó de FlowSwitch  
 Para modelar um fluxograma na qual o caminho selecionado é exclusivo com base em um valor correspondente, o nó de <xref:System.Activities.Statements.FlowSwitch%601> é usado. A propriedade de <xref:System.Activities.Statements.FlowSwitch%601.Expression%2A> é definida como <xref:System.Activities.Activity%601> com um parâmetro de tipo de <xref:System.Object> que define o valor para coincidir com opções. A propriedade de <xref:System.Activities.Statements.FlowSwitch%601.Cases%2A> define um dicionário de chaves e objetos de <xref:System.Activities.Statements.FlowNode> a correspondência com a expressão condicional, e um conjunto de objetos de <xref:System.Activities.Statements.FlowNode> que definem como a execução deve fluxo se os casos dados correspondem a expressão condicional. <xref:System.Activities.Statements.FlowSwitch%601> também define uma propriedade de <xref:System.Activities.Statements.FlowSwitch%601.Default%2A> que define como a execução deve fluxo se nenhum caso corresponde a expressão da condição. O exemplo a seguir demonstra como definir um fluxo de trabalho que usa um elemento de <xref:System.Activities.Statements.FlowSwitch%601> .  
  
```xml  
<Flowchart>  
    <FlowSwitch>  
      <FlowStep x:Key="Red">  
        <WriteRed/>  
      </FlowStep>  
      <FlowStep x:Key="Blue">  
        <WriteBlue/>  
      </FlowStep>  
      <FlowStep x:Key="Green">  
        <WriteGreen/>  
      </FlowStep>  
    </FlowSwitch>  
</Flowchart>  
```
