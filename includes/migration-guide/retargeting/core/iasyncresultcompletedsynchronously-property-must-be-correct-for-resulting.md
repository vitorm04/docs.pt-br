---
ms.openlocfilehash: c557f1cb65a675446bc77c57ef91972df92712bb
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85617101"
---
### <a name="iasyncresultcompletedsynchronously-property-must-be-correct-for-the-resulting-task-to-complete"></a><span data-ttu-id="2cc06-101">A propriedade IAsyncResult.CompletedSynchronously deve estar correta para a tarefa resultante a ser concluída</span><span class="sxs-lookup"><span data-stu-id="2cc06-101">IAsyncResult.CompletedSynchronously property must be correct for the resulting task to complete</span></span>

#### <a name="details"></a><span data-ttu-id="2cc06-102">Detalhes</span><span class="sxs-lookup"><span data-stu-id="2cc06-102">Details</span></span>

<span data-ttu-id="2cc06-103">Ao chamar TaskFactory.FromAsync, a implementação da propriedade <xref:System.IAsyncResult.CompletedSynchronously> deve estar correta para a tarefa resultante a ser concluída.</span><span class="sxs-lookup"><span data-stu-id="2cc06-103">When calling TaskFactory.FromAsync, the implementation of the <xref:System.IAsyncResult.CompletedSynchronously> property must be correct for the resulting task to complete.</span></span> <span data-ttu-id="2cc06-104">Isto é, a propriedade deverá retornar true se, e apenas se, a implementação for concluída de modo síncrono.</span><span class="sxs-lookup"><span data-stu-id="2cc06-104">That is, the property must return true if, and only if, the implementation completed synchronously.</span></span> <span data-ttu-id="2cc06-105">Anteriormente, a propriedade não era verificada.</span><span class="sxs-lookup"><span data-stu-id="2cc06-105">Previously, the property was not checked.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="2cc06-106">Sugestão</span><span class="sxs-lookup"><span data-stu-id="2cc06-106">Suggestion</span></span>

<span data-ttu-id="2cc06-107">Se as implementações de <xref:System.IAsyncResult?displayProperty=fullName> retornarem true corretamente para a propriedade <xref:System.IAsyncResult.CompletedSynchronously?displayProperty=fullName> somente quando uma tarefa for concluída de modo síncrono, nenhuma interrupção será observada.</span><span class="sxs-lookup"><span data-stu-id="2cc06-107">If <xref:System.IAsyncResult?displayProperty=fullName> implementations correctly return true for the <xref:System.IAsyncResult.CompletedSynchronously?displayProperty=fullName> property only when a task completed synchronously, then no break will be observed.</span></span> <span data-ttu-id="2cc06-108">Os usuários devem revisar as implementações de <xref:System.IAsyncResult?displayProperty=fullName> que têm (se houver) para garantir que eles sejam avaliados corretamente se uma tarefa for concluída de modo síncrono ou não.</span><span class="sxs-lookup"><span data-stu-id="2cc06-108">Users should review <xref:System.IAsyncResult?displayProperty=fullName> implementations they own (if any) to ensure that they correctly evaluate whether a task completed synchronously or not.</span></span>

| <span data-ttu-id="2cc06-109">Name</span><span class="sxs-lookup"><span data-stu-id="2cc06-109">Name</span></span>    | <span data-ttu-id="2cc06-110">Valor</span><span class="sxs-lookup"><span data-stu-id="2cc06-110">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="2cc06-111">Escopo</span><span class="sxs-lookup"><span data-stu-id="2cc06-111">Scope</span></span>   | <span data-ttu-id="2cc06-112">Microsoft Edge</span><span class="sxs-lookup"><span data-stu-id="2cc06-112">Edge</span></span>        |
| <span data-ttu-id="2cc06-113">Versão</span><span class="sxs-lookup"><span data-stu-id="2cc06-113">Version</span></span> | <span data-ttu-id="2cc06-114">4.5</span><span class="sxs-lookup"><span data-stu-id="2cc06-114">4.5</span></span>         |
| <span data-ttu-id="2cc06-115">Type</span><span class="sxs-lookup"><span data-stu-id="2cc06-115">Type</span></span>    | <span data-ttu-id="2cc06-116">Redirecionando</span><span class="sxs-lookup"><span data-stu-id="2cc06-116">Retargeting</span></span> |

#### <a name="affected-apis"></a><span data-ttu-id="2cc06-117">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="2cc06-117">Affected APIs</span></span>

- <xref:System.Threading.Tasks.TaskFactory.FromAsync(System.IAsyncResult,System.Action{System.IAsyncResult})?displayProperty=nameWithType>
- <xref:System.Threading.Tasks.TaskFactory.FromAsync(System.IAsyncResult,System.Action{System.IAsyncResult},System.Threading.Tasks.TaskCreationOptions)?displayProperty=nameWithType>
- <xref:System.Threading.Tasks.TaskFactory.FromAsync(System.IAsyncResult,System.Action{System.IAsyncResult},System.Threading.Tasks.TaskCreationOptions,System.Threading.Tasks.TaskScheduler)?displayProperty=nameWithType>
- <xref:System.Threading.Tasks.TaskFactory.FromAsync%60%601(System.IAsyncResult,System.Func{System.IAsyncResult,%60%600})?displayProperty=nameWithType>
- <xref:System.Threading.Tasks.TaskFactory.FromAsync(System.Func{System.AsyncCallback,System.Object,System.IAsyncResult},System.Action{System.IAsyncResult},System.Object)?displayProperty=nameWithType>
- <xref:System.Threading.Tasks.TaskFactory.FromAsync(System.Func{System.AsyncCallback,System.Object,System.IAsyncResult},System.Action{System.IAsyncResult},System.Object,System.Threading.Tasks.TaskCreationOptions)?displayProperty=nameWithType>
- <xref:System.Threading.Tasks.TaskFactory.FromAsync%60%601(System.Func{%60%600,System.AsyncCallback,System.Object,System.IAsyncResult},System.Action{System.IAsyncResult},%60%600,System.Object)?displayProperty=nameWithType>
- <xref:System.Threading.Tasks.TaskFactory.FromAsync%60%601(System.Func{%60%600,System.AsyncCallback,System.Object,System.IAsyncResult},System.Action{System.IAsyncResult},%60%600,System.Object,System.Threading.Tasks.TaskCreationOptions)?displayProperty=nameWithType>
- <xref:System.Threading.Tasks.TaskFactory.FromAsync%60%601(System.Func{System.AsyncCallback,System.Object,System.IAsyncResult},System.Func{System.IAsyncResult,%60%600},System.Object)?displayProperty=nameWithType>
- <xref:System.Threading.Tasks.TaskFactory.FromAsync%60%601(System.Func{System.AsyncCallback,System.Object,System.IAsyncResult},System.Func{System.IAsyncResult,%60%600},System.Object,System.Threading.Tasks.TaskCreationOptions)?displayProperty=nameWithType>
- <xref:System.Threading.Tasks.TaskFactory.FromAsync%60%601(System.IAsyncResult,System.Func{System.IAsyncResult,%60%600},System.Threading.Tasks.TaskCreationOptions)?displayProperty=nameWithType>
- <xref:System.Threading.Tasks.TaskFactory.FromAsync%60%601(System.IAsyncResult,System.Func{System.IAsyncResult,%60%600},System.Threading.Tasks.TaskCreationOptions,System.Threading.Tasks.TaskScheduler)?displayProperty=nameWithType>
- <xref:System.Threading.Tasks.TaskFactory.FromAsync%60%602(System.Func{%60%600,%60%601,System.AsyncCallback,System.Object,System.IAsyncResult},System.Action{System.IAsyncResult},%60%600,%60%601,System.Object)?displayProperty=nameWithType>
- <xref:System.Threading.Tasks.TaskFactory.FromAsync%60%602(System.Func{%60%600,%60%601,System.AsyncCallback,System.Object,System.IAsyncResult},System.Action{System.IAsyncResult},%60%600,%60%601,System.Object,System.Threading.Tasks.TaskCreationOptions)?displayProperty=nameWithType>
- <xref:System.Threading.Tasks.TaskFactory.FromAsync%60%602(System.Func{%60%600,System.AsyncCallback,System.Object,System.IAsyncResult},System.Func{System.IAsyncResult,%60%601},%60%600,System.Object)?displayProperty=nameWithType>
- <xref:System.Threading.Tasks.TaskFactory.FromAsync%60%602(System.Func{%60%600,System.AsyncCallback,System.Object,System.IAsyncResult},System.Func{System.IAsyncResult,%60%601},%60%600,System.Object,System.Threading.Tasks.TaskCreationOptions)?displayProperty=nameWithType>
- <xref:System.Threading.Tasks.TaskFactory.FromAsync%60%603(System.Func{%60%600,%60%601,System.AsyncCallback,System.Object,System.IAsyncResult},System.Func{System.IAsyncResult,%60%602},%60%600,%60%601,System.Object)?displayProperty=nameWithType>
- <xref:System.Threading.Tasks.TaskFactory.FromAsync%60%603(System.Func{%60%600,%60%601,%60%602,System.AsyncCallback,System.Object,System.IAsyncResult},System.Action{System.IAsyncResult},%60%600,%60%601,%60%602,System.Object)?displayProperty=nameWithType>
- <xref:System.Threading.Tasks.TaskFactory.FromAsync%60%603(System.Func{%60%600,%60%601,%60%602,System.AsyncCallback,System.Object,System.IAsyncResult},System.Action{System.IAsyncResult},%60%600,%60%601,%60%602,System.Object,System.Threading.Tasks.TaskCreationOptions)?displayProperty=nameWithType>
- <xref:System.Threading.Tasks.TaskFactory.FromAsync%60%603(System.Func{%60%600,%60%601,System.AsyncCallback,System.Object,System.IAsyncResult},System.Func{System.IAsyncResult,%60%602},%60%600,%60%601,System.Object,System.Threading.Tasks.TaskCreationOptions)?displayProperty=nameWithType>
- <xref:System.Threading.Tasks.TaskFactory.FromAsync%60%604(System.Func{%60%600,%60%601,%60%602,System.AsyncCallback,System.Object,System.IAsyncResult},System.Func{System.IAsyncResult,%60%603},%60%600,%60%601,%60%602,System.Object)?displayProperty=nameWithType>
- <xref:System.Threading.Tasks.TaskFactory.FromAsync%60%604(System.Func{%60%600,%60%601,%60%602,System.AsyncCallback,System.Object,System.IAsyncResult},System.Func{System.IAsyncResult,%60%603},%60%600,%60%601,%60%602,System.Object,System.Threading.Tasks.TaskCreationOptions)?displayProperty=nameWithType>
