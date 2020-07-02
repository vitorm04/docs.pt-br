---
ms.openlocfilehash: 3eab96149be1e40d528cfd552bbe05ca766cf4e8
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85619788"
---
### <a name="systemthreadingtaskstask-no-longer-throw-objectdisposedexception-after-object-is-disposed"></a><span data-ttu-id="185cf-101">System.Threading.Tasks.Task não gera mais ObjectDisposedException depois que o objeto é descartado</span><span class="sxs-lookup"><span data-stu-id="185cf-101">System.Threading.Tasks.Task no longer throw ObjectDisposedException after object is disposed</span></span>

#### <a name="details"></a><span data-ttu-id="185cf-102">Detalhes</span><span class="sxs-lookup"><span data-stu-id="185cf-102">Details</span></span>

<span data-ttu-id="185cf-103">Exceto por <xref:System.Threading.Tasks.Task.System%23IAsyncResult%23AsyncWaitHandle>, os métodos <xref:System.Threading.Tasks.Task?displayProperty=fullName>não geram mais uma exceção <xref:System.ObjectDisposedException?displayProperty=fullName> após o objeto ser descartado. Essa alteração permite o uso de tarefas em cache.</span><span class="sxs-lookup"><span data-stu-id="185cf-103">Except for <xref:System.Threading.Tasks.Task.System%23IAsyncResult%23AsyncWaitHandle>, <xref:System.Threading.Tasks.Task?displayProperty=fullName> methods no longer throw an <xref:System.ObjectDisposedException?displayProperty=fullName> exception after the object is disposed.This change supports the use of cached tasks.</span></span> <span data-ttu-id="185cf-104">Por exemplo, um método pode retornar uma tarefa em cache para representar uma operação já concluída em vez de alocar uma nova tarefa.</span><span class="sxs-lookup"><span data-stu-id="185cf-104">For example, a method can return a cached task to represent an already completed operation instead of allocating a new task.</span></span> <span data-ttu-id="185cf-105">Isso era impossível nas versões anteriores do .NET Framework porque qualquer consumidor da tarefa poderia descartá-los, o que a tornava inutilizável.</span><span class="sxs-lookup"><span data-stu-id="185cf-105">This was impossible in previous .NET Framework versions, because any consumer of the task could dispose of it, which rendered it unusable.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="185cf-106">Sugestão</span><span class="sxs-lookup"><span data-stu-id="185cf-106">Suggestion</span></span>

<span data-ttu-id="185cf-107">Lembre-se de que os métodos Task podem não gerar mais <xref:System.ObjectDisposedException?displayProperty=fullName> nos casos em que o objeto é descartado.</span><span class="sxs-lookup"><span data-stu-id="185cf-107">Be aware that Task methods may no longer throw <xref:System.ObjectDisposedException?displayProperty=fullName> in cases when the object is disposed.</span></span> <span data-ttu-id="185cf-108">Se um aplicativo dependia dessa exceção para saber que uma tarefa foi descartada, ele deverá ser atualizado para verificar explicitamente o status da tarefa usando <xref:System.Threading.Tasks.Task.Status>.</span><span class="sxs-lookup"><span data-stu-id="185cf-108">If an app was depending on this exception to know that a task was disposed, it should be updated to explicitly check the task's status using <xref:System.Threading.Tasks.Task.Status>.</span></span>

| <span data-ttu-id="185cf-109">Name</span><span class="sxs-lookup"><span data-stu-id="185cf-109">Name</span></span>    | <span data-ttu-id="185cf-110">Valor</span><span class="sxs-lookup"><span data-stu-id="185cf-110">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="185cf-111">Escopo</span><span class="sxs-lookup"><span data-stu-id="185cf-111">Scope</span></span>   |<span data-ttu-id="185cf-112">Secundária</span><span class="sxs-lookup"><span data-stu-id="185cf-112">Minor</span></span>|
|<span data-ttu-id="185cf-113">Versão</span><span class="sxs-lookup"><span data-stu-id="185cf-113">Version</span></span>|<span data-ttu-id="185cf-114">4.5</span><span class="sxs-lookup"><span data-stu-id="185cf-114">4.5</span></span>|
|<span data-ttu-id="185cf-115">Type</span><span class="sxs-lookup"><span data-stu-id="185cf-115">Type</span></span>|<span data-ttu-id="185cf-116">Runtime</span><span class="sxs-lookup"><span data-stu-id="185cf-116">Runtime</span></span>|
