---
title: Inspeção da árvore de atividade
ms.date: 03/30/2017
ms.assetid: 100d00e4-8c1d-4233-8fbb-dd443a01155d
ms.openlocfilehash: 4f2ca6bff27cfe0e3362e2a3b95cd08a0f8d5297
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33516835"
---
# <a name="activity-tree-inspection"></a>Inspeção da árvore de atividade
A inspeção da árvore de atividade é usada por autores de aplicativo de fluxo de trabalho para inspecionar os fluxos de trabalho hospedados pelo aplicativo. Usando <xref:System.Activities.WorkflowInspectionServices>, os fluxos de trabalho podem ser pesquisados para atividades filhos específicas, as atividades individuais e suas propriedades podem ser enumeradas, e os metadados de tempo de execução das atividades podem ser armazenados em cachê em um horário específico. Este tópico fornece uma visão geral de <xref:System.Activities.WorkflowInspectionServices> e como usá-la para inspecionar uma árvore de atividade.  
  
## <a name="using-workflowinspectionservices"></a>Usando WorkflowInspectionServices  
 O método de <xref:System.Activities.WorkflowInspectionServices.GetActivities%2A> é usado para enumerar todas as atividades na árvore de atividade especificada. retorna um<xref:System.Activities.WorkflowInspectionServices.GetActivities%2A> enumerável que toque em todas as atividades dentro da árvore que inclui filhos, manipuladores de representante opções, variáveis, e expressões de argumento. No exemplo a seguir, uma definição de fluxo de trabalho é criada usando <xref:System.Activities.Statements.Sequence>, <xref:System.Activities.Statements.While>, <xref:System.Activities.Statements.ForEach%601>, <xref:System.Activities.Statements.WriteLine>, e expressões. Depois que a definição de fluxo de trabalho é criada, invoca-se e o método de `InspectActivity` é então chamado.  
  
 [!code-csharp[CFX_WorkflowApplicationExample#45](../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowapplicationexample/cs/program.cs#45)]  
  
 Para enumerar as atividades, <xref:System.Activities.WorkflowInspectionServices.GetActivities%2A> é chamado a atividade de raiz, e novamente recursivamente em cada atividade retornado. No exemplo a seguir, <xref:System.Activities.Activity.DisplayName%2A> de cada atividade e expressão na árvore de atividade é escrito no console.  
  
 [!code-csharp[CFX_WorkflowApplicationExample#46](../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowapplicationexample/cs/program.cs#46)]  
  
 Esse código de exemplo fornece a seguinte saída.  
  
 **Item de lista 1**  
**Item de lista 2**   
**Item de lista 3**   
**Item de lista 4**   
**Item de lista 5**   
**Itens adicionados à coleção.**   
**sequência**   
 **Literal < lista\<cadeia de caracteres >>**  
 **While**  
 **AddToCollection\<cadeia de caracteres >**  
 **VariableValue < ICollection\<cadeia de caracteres >>**  
 **LambdaValue\<cadeia de caracteres >**  
 **LocationReferenceValue < lista\<cadeia de caracteres >>**  
 **LambdaValue\<booliana >**  
 **LocationReferenceValue < lista\<cadeia de caracteres >>**  
 **ForEach\<cadeia de caracteres >**  
 **VariableValue < IEnumerable\<cadeia de caracteres >>**  
 **WriteLine**  
 **DelegateArgumentValue\<cadeia de caracteres >**  
 **sequência**  
 **WriteLine**  
 **Literal\<cadeia de caracteres >** para recuperar uma atividade específica, em vez de enumerar todas as atividades, <xref:System.Activities.WorkflowInspectionServices.Resolve%2A> é usado. <xref:System.Activities.WorkflowInspectionServices.Resolve%2A> e <xref:System.Activities.WorkflowInspectionServices.GetActivities%2A> executam o cachê de metadados `WorkflowInspectionServices.CacheMetadata` se não tiver sido chamado anteriormente. Se <xref:System.Activities.WorkflowInspectionServices.CacheMetadata%2A> tiver sido chamado em <xref:System.Activities.WorkflowInspectionServices.GetActivities%2A> é baseado nos metadados existentes. Portanto, se as alterações de árvore foram feitas desde a última chamada a <xref:System.Activities.WorkflowInspectionServices.CacheMetadata%2A>, <xref:System.Activities.WorkflowInspectionServices.GetActivities%2A> pode dar resultados inesperados. Se as alterações foram feitas ao fluxo de trabalho depois de chamar <xref:System.Activities.WorkflowInspectionServices.GetActivities%2A>, metadados podem ser novamente armazenada em cache chamando o <xref:System.Activities.Validation.ActivityValidationServices> <xref:System.Activities.Validation.ActivityValidationServices.Validate%2A> método. Armazenando em cachê metadados é abordado na seção a seguir.  
  
### <a name="caching-metadata"></a>Metadados de Caching  
 Armazenando em cachê os metadados para uma atividade compila e valida uma descrição dos argumentos de atividade, variáveis, as atividades filhos, e os representantes de atividade. Os metadados, são armazenados em cachê por padrão no tempo de execução em que uma atividade é preparada para a execução. Se um autor de host de fluxo de trabalho deseja armazenar em cachê os metadados para uma atividade ou a árvore de atividade antes disso, por exemplo tomar com antecedência todos os custos, então <xref:System.Activities.WorkflowInspectionServices.CacheMetadata%2A> pode ser usada para armazenar em cachê os metadados em tempo desejado.
