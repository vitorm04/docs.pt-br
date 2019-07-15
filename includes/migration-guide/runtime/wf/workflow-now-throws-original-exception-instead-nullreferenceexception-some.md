---
ms.openlocfilehash: 6e5e90a4cfb862b3bfd74ac5a3715e97a736f598
ms.sourcegitcommit: d55e14eb63588830c0ba1ea95a24ce6c57ef8c8c
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/11/2019
ms.locfileid: "67802491"
---
### <a name="workflow-now-throws-original-exception-instead-of-nullreferenceexception-in-some-cases"></a>Agora, o fluxo de trabalho gera a exceção original em vez de NullReferenceException em alguns casos

|   |   |
|---|---|
|Detalhes|No .NET Framework 4.6.2 e versões anteriores, quando o método Executar de uma atividade de fluxo de trabalho gera uma exceção com um valor <code>null</code> para a propriedade <xref:System.Exception.Message>, o tempo de execução do fluxo de trabalho System.Activities gera <xref:System.NullReferenceException?displayProperty=name>, mascarando a exceção original. No .NET Framework 4.7, a exceção mascarada anteriormente é gerada.|
|Sugestão|Se o código depender do tratamento de <xref:System.NullReferenceException?displayProperty=name>, altere-o para capturar as exceções que possam ser geradas por meio das atividades personalizadas.|
|Escopo|Secundário|
|Versão|4.7|
|Tipo|Tempo de execução|
|APIs afetadas|<ul><li><xref:System.Activities.CodeActivity.Execute(System.Activities.CodeActivityContext)?displayProperty=nameWithType></li><li><xref:System.Activities.AsyncCodeActivity.BeginExecute(System.Activities.AsyncCodeActivityContext,System.AsyncCallback,System.Object)?displayProperty=nameWithType></li><li><xref:System.Activities.AsyncCodeActivity%601.BeginExecute(System.Activities.AsyncCodeActivityContext,System.AsyncCallback,System.Object)?displayProperty=nameWithType></li><li><xref:System.Activities.WorkflowInvoker.Invoke?displayProperty=nameWithType></li></ul>|

