---
title: Usando representantes de atividades
ms.date: 03/30/2017
ms.assetid: e33cf876-8979-440b-9b23-4a12d1139960
ms.openlocfilehash: 96a412a066342fb9c459e1388c5b58847ebac390
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33518946"
---
# <a name="using-activity-delegates"></a>Usando representantes de atividades
Os representantes de atividade permitem autores de atividade para expor retornos de chamada com assinaturas específicas, para que os usuários de atividade podem fornecer manipuladores atividades base. Dois tipos de representantes de atividade estão disponíveis: <xref:System.Activities.ActivityAction%601> é usado para definir os representantes de atividade que não têm um valor de retorno, e <xref:System.Activities.ActivityFunc%601> é usado para definir os representantes de atividade que têm um valor de retorno.  
  
 Os representantes de atividade são úteis em situações onde uma atividade filho deve ser restrita a ter uma determinada assinatura. Por exemplo, uma atividade de <xref:System.Activities.Statements.While> pode conter qualquer tipo de atividade filho sem restrições, mas o corpo de uma atividade de <xref:System.Activities.Statements.ForEach%601> é <xref:System.Activities.ActivityAction%601>, e a atividade filho que é executada por finalmente <xref:System.Activities.Statements.ForEach%601> deve ter <xref:System.Activities.InArgument%601> que é o mesmo tipo dos membros da coleção que <xref:System.Activities.Statements.ForEach%601> enumera.  
  
## <a name="using-activityaction"></a>Usando ActivityAction  
 Várias atividades de [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] usam ações de atividade, como a atividade de <xref:System.Activities.Statements.Catch> e a atividade de <xref:System.Activities.Statements.ForEach%601> . Em cada caso, a ação de atividade representa um local onde o autor de fluxo de trabalho especifica uma atividade para fornecer um comportamento desejado quando estiver compondo um fluxo de trabalho usando uma dessas atividades. No exemplo a seguir, uma atividade de <xref:System.Activities.Statements.ForEach%601> é usada para exibir texto na janela do console. O corpo de <xref:System.Activities.Statements.ForEach%601> é especificado usando <xref:System.Activities.ActivityAction%601> que corresponde ao tipo de <xref:System.Activities.Statements.ForEach%601> que é cadeia de caracteres. A atividade de <xref:System.Activities.Statements.WriteLine> especificada em <xref:System.Activities.ActivityDelegate.Handler%2A> tem seu argumento de <xref:System.Activities.Statements.WriteLine.Text%2A> associado a valores de cadeia de caracteres na coleção que a atividade de <xref:System.Activities.Statements.ForEach%601> itera.  
  
 [!code-csharp[CFX_ActivityExample#6](../../../samples/snippets/csharp/VS_Snippets_CFX/CFX_ActivityExample/cs/Program.cs#6)]  
  
 O actionArgument é usado para fluir itens individuais na coleção para WriteLine. Quando o fluxo de trabalho é chamado, a saída a seguir são exibidas no console.  
 ``` 
 HelloWorld.
 ```  
Os exemplos deste tópico usam sintaxe de inicialização de objeto. A sintaxe de inicialização de objeto pode ser uma maneira útil de criar definições de fluxo de trabalho no código porque fornece uma exibição hierárquica das atividades no fluxo de trabalho e mostra a relação entre as atividades. Não há nenhum requisito para usar a sintaxe de inicialização de objeto quando você cria fluxos de trabalho programaticamente. O exemplo a seguir é funcionalmente equivalente ao exemplo anterior.  
  
 [!code-csharp[CFX_ActivityExample#7](../../../samples/snippets/csharp/VS_Snippets_CFX/CFX_ActivityExample/cs/Program.cs#7)]  
  
 Para obter mais informações sobre os inicializadores de objeto, consulte [como: inicializar objetos sem chamar um construtor (c# Programming Guide)](http://go.microsoft.com/fwlink/?LinkId=161015) e [como: declarar um objeto usando um inicializador de objeto](http://go.microsoft.com/fwlink/?LinkId=161016).  
  
 No exemplo a seguir, uma atividade de <xref:System.Activities.Statements.TryCatch> é usada em um fluxo de trabalho. <xref:System.ApplicationException> é gerada pelo fluxo de trabalho, e tratado por uma atividade de <xref:System.Activities.Statements.Catch%601> . O manipulador para o <xref:System.Activities.Statements.Catch%601> ação de atividade da atividade é uma <xref:System.Activities.Statements.WriteLine> atividade e os detalhes da exceção flui através de usando o `ex` <xref:System.Activities.DelegateInArgument%601>.  
  
 [!code-csharp[CFX_WorkflowApplicationExample#33](../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowapplicationexample/cs/program.cs#33)]  
  
 Ao criar uma atividade personalizado que define <xref:System.Activities.ActivityAction%601>, use <xref:System.Activities.Statements.InvokeAction%601> para modelar invocação do <xref:System.Activities.ActivityAction%601>. Nesse exemplo, uma atividade de `WriteLineWithNotification` personalizado é definida. Esta atividade é composta de <xref:System.Activities.Statements.Sequence> que contém uma atividade de <xref:System.Activities.Statements.WriteLine> seguida por <xref:System.Activities.Statements.InvokeAction%601> que invoca <xref:System.Activities.ActivityAction%601> que recebe um argumento de cadeia de caracteres.  
  
 [!code-csharp[CFX_ActivityExample#1](../../../samples/snippets/csharp/VS_Snippets_CFX/CFX_ActivityExample/cs/Program.cs#1)]  
  
 Quando um fluxo de trabalho é criado usando a atividade de `WriteLineWithNotification` , o autor de fluxo de trabalho especifica a lógica personalizada desejada em <xref:System.Activities.ActivityDelegate.Handler%2A>de ação de atividade. Nesse exemplo, um fluxo de trabalho é criado usando a atividade de `WriteLineWithNotification` , e uma atividade de <xref:System.Activities.Statements.WriteLine> é usada como <xref:System.Activities.ActivityDelegate.Handler%2A>.  
  
 [!code-csharp[CFX_ActivityExample#2](../../../samples/snippets/csharp/VS_Snippets_CFX/CFX_ActivityExample/cs/Program.cs#2)]  
  
 Há várias versões genéricas de <xref:System.Activities.Statements.InvokeAction%601> e de <xref:System.Activities.ActivityAction%601> fornecidos passando um ou mais argumentos.  
  
## <a name="using-activityfunc"></a>Usando ActivityFunc  
 <xref:System.Activities.ActivityAction%601> é útil quando não há nenhum valor do resultado da atividade, e <xref:System.Activities.ActivityFunc%601> é usado quando um valor de resultado é retornado. Ao criar uma atividade personalizado que define <xref:System.Activities.ActivityFunc%601>, use <xref:System.Activities.Expressions.InvokeFunc%601> para modelar invocação do <xref:System.Activities.ActivityFunc%601>. No exemplo a seguir, uma atividade de `WriteFillerText` é definida. Para fornecer o texto de preencher, <xref:System.Activities.Expressions.InvokeFunc%601> é especificado que recebe um argumento integer e tem um resultado de cadeia de caracteres. Uma vez que o texto do enchimento é recuperado, é exibido no console usando uma atividade de <xref:System.Activities.Statements.WriteLine> .  
  
 [!code-csharp[CFX_ActivityExample#3](../../../samples/snippets/csharp/VS_Snippets_CFX/CFX_ActivityExample/cs/Program.cs#3)]  
  
 Para fornecer texto, uma atividade deve ser usada que recebe um argumento de `int` e tem um resultado de cadeia de caracteres. Este exemplo mostra uma atividade de `TextGenerator` que atenda a esses requisitos.  
  
 [!code-csharp[CFX_ActivityExample#4](../../../samples/snippets/csharp/VS_Snippets_CFX/CFX_ActivityExample/cs/Program.cs#4)]  
  
 Para usar a atividade de `TextGenerator` com a atividade de `WriteFillerText` , especifique-o como <xref:System.Activities.ActivityDelegate.Handler%2A>.  
  
 [!code-csharp[CFX_ActivityExample#5](../../../samples/snippets/csharp/VS_Snippets_CFX/CFX_ActivityExample/cs/Program.cs#5)]  
  
## <a name="see-also"></a>Consulte também  
 [Expõe e invocar ActivityActions](../../../docs/framework/windows-workflow-foundation/samples/exposing-and-invoking-activityactions.md)
