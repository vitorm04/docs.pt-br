---
ms.openlocfilehash: 61d5885c19e39b138090c1a98fa26348724893c5
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/05/2020
ms.locfileid: "89497261"
---
### <a name="workflow-now-throws-original-exception-instead-of-nullreferenceexception-in-some-cases"></a><span data-ttu-id="1cc7e-101">Agora, o fluxo de trabalho gera a exceção original em vez de NullReferenceException em alguns casos</span><span class="sxs-lookup"><span data-stu-id="1cc7e-101">Workflow now throws original exception instead of NullReferenceException in some cases</span></span>

#### <a name="details"></a><span data-ttu-id="1cc7e-102">Detalhes</span><span class="sxs-lookup"><span data-stu-id="1cc7e-102">Details</span></span>

<span data-ttu-id="1cc7e-103">No .NET Framework 4.6.2 e versões anteriores, quando o método Executar de uma atividade de fluxo de trabalho gera uma exceção com um valor <code>null</code> para a propriedade <xref:System.Exception.Message>, o runtime do fluxo de trabalho System.Activities gera <xref:System.NullReferenceException?displayProperty=fullName>, mascarando a exceção original. No .NET Framework 4.7, a exceção mascarada anteriormente é gerada.</span><span class="sxs-lookup"><span data-stu-id="1cc7e-103">In the .NET Framework 4.6.2 and earlier versions, when the Execute method of a workflow activity throws an exception with a <code>null</code> value for the <xref:System.Exception.Message> property, the System.Activities Workflow runtime throws a <xref:System.NullReferenceException?displayProperty=fullName>, masking the original exception.In the .NET Framework 4.7, the previously masked exception is thrown.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="1cc7e-104">Sugestão</span><span class="sxs-lookup"><span data-stu-id="1cc7e-104">Suggestion</span></span>

<span data-ttu-id="1cc7e-105">Se o código depender do tratamento de <xref:System.NullReferenceException?displayProperty=fullName>, altere-o para capturar as exceções que possam ser geradas por meio das atividades personalizadas.</span><span class="sxs-lookup"><span data-stu-id="1cc7e-105">If your code relies on handling the <xref:System.NullReferenceException?displayProperty=fullName>, change it to catch the exceptions that could be thrown from your custom activities.</span></span>

| <span data-ttu-id="1cc7e-106">Nome</span><span class="sxs-lookup"><span data-stu-id="1cc7e-106">Name</span></span>    | <span data-ttu-id="1cc7e-107">Valor</span><span class="sxs-lookup"><span data-stu-id="1cc7e-107">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="1cc7e-108">Escopo</span><span class="sxs-lookup"><span data-stu-id="1cc7e-108">Scope</span></span>   |<span data-ttu-id="1cc7e-109">Secundária</span><span class="sxs-lookup"><span data-stu-id="1cc7e-109">Minor</span></span>|
|<span data-ttu-id="1cc7e-110">Versão</span><span class="sxs-lookup"><span data-stu-id="1cc7e-110">Version</span></span>|<span data-ttu-id="1cc7e-111">4.7</span><span class="sxs-lookup"><span data-stu-id="1cc7e-111">4.7</span></span>|
|<span data-ttu-id="1cc7e-112">Tipo</span><span class="sxs-lookup"><span data-stu-id="1cc7e-112">Type</span></span>|<span data-ttu-id="1cc7e-113">Runtime</span><span class="sxs-lookup"><span data-stu-id="1cc7e-113">Runtime</span></span>|

#### <a name="affected-apis"></a><span data-ttu-id="1cc7e-114">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="1cc7e-114">Affected APIs</span></span>

- <xref:System.Activities.CodeActivity.Execute(System.Activities.CodeActivityContext)?displayProperty=nameWithType>
- <xref:System.Activities.AsyncCodeActivity.BeginExecute(System.Activities.AsyncCodeActivityContext,System.AsyncCallback,System.Object)?displayProperty=nameWithType>
- <xref:System.Activities.AsyncCodeActivity%601.BeginExecute(System.Activities.AsyncCodeActivityContext,System.AsyncCallback,System.Object)?displayProperty=nameWithType>
- <xref:System.Activities.WorkflowInvoker.Invoke?displayProperty=nameWithType>

<!--

#### Affected APIs

- `M:System.Activities.CodeActivity.Execute(System.Activities.CodeActivityContext)`
- `M:System.Activities.AsyncCodeActivity.BeginExecute(System.Activities.AsyncCodeActivityContext,System.AsyncCallback,System.Object)`
- ``M:System.Activities.AsyncCodeActivity`1.BeginExecute(System.Activities.AsyncCodeActivityContext,System.AsyncCallback,System.Object)``
- `M:System.Activities.WorkflowInvoker.Invoke`

-->
