---
ms.openlocfilehash: 58dbb54d42d89b450134758072e3133ae4e6b13d
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/05/2020
ms.locfileid: "89496241"
---
### <a name="systemthreadingtaskstask-no-longer-throw-objectdisposedexception-after-object-is-disposed"></a><span data-ttu-id="1b145-101">System.Threading.Tasks.Task não gera mais ObjectDisposedException depois que o objeto é descartado</span><span class="sxs-lookup"><span data-stu-id="1b145-101">System.Threading.Tasks.Task no longer throw ObjectDisposedException after object is disposed</span></span>

#### <a name="details"></a><span data-ttu-id="1b145-102">Detalhes</span><span class="sxs-lookup"><span data-stu-id="1b145-102">Details</span></span>

<span data-ttu-id="1b145-103">Exceto por <xref:System.Threading.Tasks.Task.System%23IAsyncResult%23AsyncWaitHandle>, os métodos <xref:System.Threading.Tasks.Task?displayProperty=fullName>não geram mais uma exceção <xref:System.ObjectDisposedException?displayProperty=fullName> após o objeto ser descartado. Essa alteração permite o uso de tarefas em cache.</span><span class="sxs-lookup"><span data-stu-id="1b145-103">Except for <xref:System.Threading.Tasks.Task.System%23IAsyncResult%23AsyncWaitHandle>, <xref:System.Threading.Tasks.Task?displayProperty=fullName> methods no longer throw an <xref:System.ObjectDisposedException?displayProperty=fullName> exception after the object is disposed.This change supports the use of cached tasks.</span></span> <span data-ttu-id="1b145-104">Por exemplo, um método pode retornar uma tarefa em cache para representar uma operação já concluída em vez de alocar uma nova tarefa.</span><span class="sxs-lookup"><span data-stu-id="1b145-104">For example, a method can return a cached task to represent an already completed operation instead of allocating a new task.</span></span> <span data-ttu-id="1b145-105">Isso era impossível nas versões anteriores do .NET Framework porque qualquer consumidor da tarefa poderia descartá-los, o que a tornava inutilizável.</span><span class="sxs-lookup"><span data-stu-id="1b145-105">This was impossible in previous .NET Framework versions, because any consumer of the task could dispose of it, which rendered it unusable.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="1b145-106">Sugestão</span><span class="sxs-lookup"><span data-stu-id="1b145-106">Suggestion</span></span>

<span data-ttu-id="1b145-107">Lembre-se de que os métodos Task podem não gerar mais <xref:System.ObjectDisposedException?displayProperty=fullName> nos casos em que o objeto é descartado.</span><span class="sxs-lookup"><span data-stu-id="1b145-107">Be aware that Task methods may no longer throw <xref:System.ObjectDisposedException?displayProperty=fullName> in cases when the object is disposed.</span></span> <span data-ttu-id="1b145-108">Se um aplicativo dependia dessa exceção para saber que uma tarefa foi descartada, ele deverá ser atualizado para verificar explicitamente o status da tarefa usando <xref:System.Threading.Tasks.Task.Status>.</span><span class="sxs-lookup"><span data-stu-id="1b145-108">If an app was depending on this exception to know that a task was disposed, it should be updated to explicitly check the task's status using <xref:System.Threading.Tasks.Task.Status>.</span></span>

| <span data-ttu-id="1b145-109">Nome</span><span class="sxs-lookup"><span data-stu-id="1b145-109">Name</span></span>    | <span data-ttu-id="1b145-110">Valor</span><span class="sxs-lookup"><span data-stu-id="1b145-110">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="1b145-111">Escopo</span><span class="sxs-lookup"><span data-stu-id="1b145-111">Scope</span></span>   |<span data-ttu-id="1b145-112">Secundária</span><span class="sxs-lookup"><span data-stu-id="1b145-112">Minor</span></span>|
|<span data-ttu-id="1b145-113">Versão</span><span class="sxs-lookup"><span data-stu-id="1b145-113">Version</span></span>|<span data-ttu-id="1b145-114">4.5</span><span class="sxs-lookup"><span data-stu-id="1b145-114">4.5</span></span>|
|<span data-ttu-id="1b145-115">Tipo</span><span class="sxs-lookup"><span data-stu-id="1b145-115">Type</span></span>|<span data-ttu-id="1b145-116">Runtime</span><span class="sxs-lookup"><span data-stu-id="1b145-116">Runtime</span></span>|

#### <a name="affected-apis"></a><span data-ttu-id="1b145-117">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="1b145-117">Affected APIs</span></span>

<span data-ttu-id="1b145-118">Não detectável via análise de API.</span><span class="sxs-lookup"><span data-stu-id="1b145-118">Not detectable via API analysis.</span></span>

<!--

#### Affected APIs

Not detectable via API analysis.

-->
