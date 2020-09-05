---
ms.openlocfilehash: 9d0791f00db7d830fc5d327af30218a0bbfcb25f
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/05/2020
ms.locfileid: "89497725"
---
### <a name="change-in-behavior-for-taskwaitall-methods-with-time-out-arguments"></a><span data-ttu-id="098ed-101">Mudança no comportamento de métodos Task.WaitAll com argumentos de tempo limite</span><span class="sxs-lookup"><span data-stu-id="098ed-101">Change in behavior for Task.WaitAll methods with time-out arguments</span></span>

#### <a name="details"></a><span data-ttu-id="098ed-102">Detalhes</span><span class="sxs-lookup"><span data-stu-id="098ed-102">Details</span></span>

<span data-ttu-id="098ed-103">O comportamento de <xref:System.Threading.Tasks.Task.WaitAll%2A?displayProperty=nameWithType> ficou mais consistente no .NET Framework 4.5. No .NET Framework 4, esses métodos se comportavam de forma inconsistente.</span><span class="sxs-lookup"><span data-stu-id="098ed-103"><xref:System.Threading.Tasks.Task.WaitAll%2A?displayProperty=nameWithType> behavior was made more consistent in .NET Framework 4.5.In the .NET Framework 4, these methods behaved inconsistently.</span></span> <span data-ttu-id="098ed-104">Quando o tempo limite expirou, se uma ou mais tarefas foram concluídas ou canceladas antes da chamada de método, o método lançou uma exceção <xref:System.AggregateException?displayProperty=fullName>.</span><span class="sxs-lookup"><span data-stu-id="098ed-104">When the time-out expired, if one or more tasks were completed or canceled before the method call, the method threw an <xref:System.AggregateException?displayProperty=fullName> exception.</span></span> <span data-ttu-id="098ed-105">Quando o tempo limite expirava, se nenhuma tarefa tivesse sido concluída ou cancelada antes da chamada de método, mas uma ou mais tarefas tivessem entrado nesses estados após a chamada de método, o método retornava false.</span><span class="sxs-lookup"><span data-stu-id="098ed-105">When the time-out expired, if no tasks were completed or canceled before the method call, but one or more tasks entered these states after the method call, the method returned false.</span></span><br/><br/><span data-ttu-id="098ed-106">No .NET Framework 4.5, essas sobrecargas de método agora retornam false se alguma tarefa ainda está em execução quando o intervalo de tempo limite expira e geram uma exceção <xref:System.AggregateException?displayProperty=fullName> somente se uma tarefa de entrada é cancelada (não importa se antes ou depois da chamada de método) e nenhuma outra tarefa ainda está em execução.</span><span class="sxs-lookup"><span data-stu-id="098ed-106">In the .NET Framework 4.5, these method overloads now return false if any tasks are still running when the time-out interval expired, and they throw an <xref:System.AggregateException?displayProperty=fullName> exception only if an input task was cancelled (regardless of whether it was before or after the method call) and no other tasks are still running.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="098ed-107">Sugestão</span><span class="sxs-lookup"><span data-stu-id="098ed-107">Suggestion</span></span>

<span data-ttu-id="098ed-108">Se um <xref:System.AggregateException?displayProperty=fullName> era capturado como um meio de detectar uma tarefa cancelada antes da invocação da chamada de <xref:System.Threading.Tasks.Task.WaitAll%2A>, esse código deverá fazer a mesma detecção por meio da propriedade <xref:System.Threading.Tasks.Task.IsCanceled%2A> [por exemplo: .Any(t =&gt; t.IsCanceled)], porque o .NET Framework 4.6 acionará esse caso apenas se todas as tarefas esperadas forem concluídas antes do tempo limite.</span><span class="sxs-lookup"><span data-stu-id="098ed-108">If an <xref:System.AggregateException?displayProperty=fullName> was being caught as a means of detecting a task that was cancelled prior to the <xref:System.Threading.Tasks.Task.WaitAll%2A> call being invoked, that code should instead do the same detection via the  <xref:System.Threading.Tasks.Task.IsCanceled%2A> property (for example: .Any(t =&gt; t.IsCanceled)) since .NET Framework 4.6 will only throw in that case if all awaited tasks are completed prior to the timeout.</span></span>

| <span data-ttu-id="098ed-109">Nome</span><span class="sxs-lookup"><span data-stu-id="098ed-109">Name</span></span>    | <span data-ttu-id="098ed-110">Valor</span><span class="sxs-lookup"><span data-stu-id="098ed-110">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="098ed-111">Escopo</span><span class="sxs-lookup"><span data-stu-id="098ed-111">Scope</span></span>   |<span data-ttu-id="098ed-112">Secundária</span><span class="sxs-lookup"><span data-stu-id="098ed-112">Minor</span></span>|
|<span data-ttu-id="098ed-113">Versão</span><span class="sxs-lookup"><span data-stu-id="098ed-113">Version</span></span>|<span data-ttu-id="098ed-114">4.5</span><span class="sxs-lookup"><span data-stu-id="098ed-114">4.5</span></span>|
|<span data-ttu-id="098ed-115">Tipo</span><span class="sxs-lookup"><span data-stu-id="098ed-115">Type</span></span>|<span data-ttu-id="098ed-116">Runtime</span><span class="sxs-lookup"><span data-stu-id="098ed-116">Runtime</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="098ed-117">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="098ed-117">Affected APIs</span></span>

- <xref:System.Threading.Tasks.Task.WaitAll(System.Threading.Tasks.Task[],System.Int32)?displayProperty=nameWithType>
- <xref:System.Threading.Tasks.Task.WaitAll(System.Threading.Tasks.Task[],System.Int32,System.Threading.CancellationToken)?displayProperty=nameWithType>
- <xref:System.Threading.Tasks.Task.WaitAll(System.Threading.Tasks.Task[],System.TimeSpan)?displayProperty=nameWithType>

<!--

#### Affected APIs

- `M:System.Threading.Tasks.Task.WaitAll(System.Threading.Tasks.Task[],System.Int32)`
- `M:System.Threading.Tasks.Task.WaitAll(System.Threading.Tasks.Task[],System.Int32,System.Threading.CancellationToken)`
- `M:System.Threading.Tasks.Task.WaitAll(System.Threading.Tasks.Task[],System.TimeSpan)`

-->
