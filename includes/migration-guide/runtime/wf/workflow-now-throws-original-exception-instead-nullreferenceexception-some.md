---
ms.openlocfilehash: 6e5e90a4cfb862b3bfd74ac5a3715e97a736f598
ms.sourcegitcommit: 0aca6c5d166d7961a1e354c248495645b97a1dc5
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/01/2019
ms.locfileid: "58760403"
---
### <a name="workflow-now-throws-original-exception-instead-of-nullreferenceexception-in-some-cases"></a><span data-ttu-id="39761-101">Agora, o fluxo de trabalho gera a exceção original em vez de NullReferenceException em alguns casos</span><span class="sxs-lookup"><span data-stu-id="39761-101">Workflow now throws original exception instead of NullReferenceException in some cases</span></span>

|   |   |
|---|---|
|<span data-ttu-id="39761-102">Detalhes</span><span class="sxs-lookup"><span data-stu-id="39761-102">Details</span></span>|<span data-ttu-id="39761-103">No .NET Framework 4.6.2 e versões anteriores, quando o método Executar de uma atividade de fluxo de trabalho gera uma exceção com um valor <code>null</code> para a propriedade <xref:System.Exception.Message>, o tempo de execução do fluxo de trabalho System.Activities gera <xref:System.NullReferenceException?displayProperty=name>, mascarando a exceção original. No .NET Framework 4.7, a exceção mascarada anteriormente é gerada.</span><span class="sxs-lookup"><span data-stu-id="39761-103">In the .NET Framework 4.6.2 and earlier versions, when the Execute method of a workflow activity throws an exception with a <code>null</code> value for the <xref:System.Exception.Message> property, the System.Activities Workflow runtime throws a <xref:System.NullReferenceException?displayProperty=name>, masking the original exception.In the .NET Framework 4.7, the previously masked exception is thrown.</span></span>|
|<span data-ttu-id="39761-104">Sugestão</span><span class="sxs-lookup"><span data-stu-id="39761-104">Suggestion</span></span>|<span data-ttu-id="39761-105">Se o código depender do tratamento de <xref:System.NullReferenceException?displayProperty=name>, altere-o para capturar as exceções que possam ser geradas por meio das atividades personalizadas.</span><span class="sxs-lookup"><span data-stu-id="39761-105">If your code relies on handling the <xref:System.NullReferenceException?displayProperty=name>, change it to catch the exceptions that could be thrown from your custom activities.</span></span>|
|<span data-ttu-id="39761-106">Escopo</span><span class="sxs-lookup"><span data-stu-id="39761-106">Scope</span></span>|<span data-ttu-id="39761-107">Secundário</span><span class="sxs-lookup"><span data-stu-id="39761-107">Minor</span></span>|
|<span data-ttu-id="39761-108">Versão</span><span class="sxs-lookup"><span data-stu-id="39761-108">Version</span></span>|<span data-ttu-id="39761-109">4.7</span><span class="sxs-lookup"><span data-stu-id="39761-109">4.7</span></span>|
|<span data-ttu-id="39761-110">Tipo</span><span class="sxs-lookup"><span data-stu-id="39761-110">Type</span></span>|<span data-ttu-id="39761-111">Tempo de execução</span><span class="sxs-lookup"><span data-stu-id="39761-111">Runtime</span></span>|
|<span data-ttu-id="39761-112">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="39761-112">Affected APIs</span></span>|<ul><li><xref:System.Activities.CodeActivity.Execute(System.Activities.CodeActivityContext)?displayProperty=nameWithType></li><li><xref:System.Activities.AsyncCodeActivity.BeginExecute(System.Activities.AsyncCodeActivityContext,System.AsyncCallback,System.Object)?displayProperty=nameWithType></li><li><xref:System.Activities.AsyncCodeActivity%601.BeginExecute(System.Activities.AsyncCodeActivityContext,System.AsyncCallback,System.Object)?displayProperty=nameWithType></li><li><xref:System.Activities.WorkflowInvoker.Invoke?displayProperty=nameWithType></li></ul>|

