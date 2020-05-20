---
title: Interface ICLRDebugManager
ms.date: 03/30/2017
api_name:
- ICLRDebugManager
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRDebugManager
helpviewer_keywords:
- ICLRDebugManager interface [.NET Framework hosting]
ms.assetid: e835062c-c7d6-4945-8a44-2de7ebf3928e
topic_type:
- apiref
ms.openlocfilehash: 717a3d12528a34eafbd918c29d8e13bb87097d82
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83615768"
---
# <a name="iclrdebugmanager-interface"></a><span data-ttu-id="0c654-102">Interface ICLRDebugManager</span><span class="sxs-lookup"><span data-stu-id="0c654-102">ICLRDebugManager Interface</span></span>
<span data-ttu-id="0c654-103">Fornece métodos que permitem que um host associe um conjunto de tarefas a um identificador e um nome amigável.</span><span class="sxs-lookup"><span data-stu-id="0c654-103">Provides methods that allow a host to associate a set of tasks with an identifier and a friendly name.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="0c654-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="0c654-104">Methods</span></span>  
  
|<span data-ttu-id="0c654-105">Método</span><span class="sxs-lookup"><span data-stu-id="0c654-105">Method</span></span>|<span data-ttu-id="0c654-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="0c654-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="0c654-107">Método BeginConnection</span><span class="sxs-lookup"><span data-stu-id="0c654-107">BeginConnection Method</span></span>](iclrdebugmanager-beginconnection-method.md)|<span data-ttu-id="0c654-108">Estabelece uma nova conexão entre o host e o depurador para associar tarefas a um identificador e um nome amigável.</span><span class="sxs-lookup"><span data-stu-id="0c654-108">Establishes a new connection between the host and the debugger to associate tasks with an identifier and a friendly name.</span></span>|  
|[<span data-ttu-id="0c654-109">Método EndConnection</span><span class="sxs-lookup"><span data-stu-id="0c654-109">EndConnection Method</span></span>](iclrdebugmanager-endconnection-method.md)|<span data-ttu-id="0c654-110">Remove a associação entre uma lista de tarefas e um identificador e um nome amigável.</span><span class="sxs-lookup"><span data-stu-id="0c654-110">Removes the association between a list of tasks and an identifier and a friendly name.</span></span>|  
|[<span data-ttu-id="0c654-111">Método GetDacl</span><span class="sxs-lookup"><span data-stu-id="0c654-111">GetDacl Method</span></span>](iclrdebugmanager-getdacl-method.md)|<span data-ttu-id="0c654-112">Este método não está implementado.</span><span class="sxs-lookup"><span data-stu-id="0c654-112">This method is not implemented.</span></span>|  
|[<span data-ttu-id="0c654-113">Método IsDebuggerAttached</span><span class="sxs-lookup"><span data-stu-id="0c654-113">IsDebuggerAttached Method</span></span>](iclrdebugmanager-isdebuggerattached-method.md)|<span data-ttu-id="0c654-114">Obtém um valor que indica se um depurador está anexado ao processo.</span><span class="sxs-lookup"><span data-stu-id="0c654-114">Gets a value that indicates whether a debugger is attached to the process.</span></span>|  
|[<span data-ttu-id="0c654-115">Método SetConnectionTasks</span><span class="sxs-lookup"><span data-stu-id="0c654-115">SetConnectionTasks Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-setconnectiontasks-method.md)|<span data-ttu-id="0c654-116">Associa uma lista de instâncias [ICLRTask](iclrtask-interface.md) com um identificador e um nome amigável.</span><span class="sxs-lookup"><span data-stu-id="0c654-116">Associates a list of [ICLRTask](iclrtask-interface.md) instances with an identifier and a friendly name.</span></span>|  
|[<span data-ttu-id="0c654-117">Método SetDacl</span><span class="sxs-lookup"><span data-stu-id="0c654-117">SetDacl Method</span></span>](iclrdebugmanager-setdacl-method.md)|<span data-ttu-id="0c654-118">Este método não está implementado.</span><span class="sxs-lookup"><span data-stu-id="0c654-118">This method is not implemented.</span></span>|  
|[<span data-ttu-id="0c654-119">Método SetSymbolReadingPolicy</span><span class="sxs-lookup"><span data-stu-id="0c654-119">SetSymbolReadingPolicy Method</span></span>](iclrdebugmanager-setsymbolreadingpolicy-method.md)|<span data-ttu-id="0c654-120">Define a política para ler arquivos de banco de dados do programa (PDB).</span><span class="sxs-lookup"><span data-stu-id="0c654-120">Sets the policy for reading program database (PDB) files.</span></span> <span data-ttu-id="0c654-121">A política determina se as informações sobre números de linha e arquivos estão incluídas em pilhas de chamadas.</span><span class="sxs-lookup"><span data-stu-id="0c654-121">The policy determines whether information about line numbers and files is included in call stacks.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0c654-122">Comentários</span><span class="sxs-lookup"><span data-stu-id="0c654-122">Remarks</span></span>  
 <span data-ttu-id="0c654-123">Em cenários de depuração, um host pode querer agrupar tarefas de acordo com sua própria lógica de programação.</span><span class="sxs-lookup"><span data-stu-id="0c654-123">In debugging scenarios, a host might want to group tasks according to its own programming logic.</span></span> <span data-ttu-id="0c654-124">Por exemplo, um agrupamento permitiria que um desenvolvedor vêsse apenas as tarefas exigidas pelas APIs do desenvolvedor, em vez de ver cada tarefa em execução no processo.</span><span class="sxs-lookup"><span data-stu-id="0c654-124">For example, a grouping would allow a developer to see only the tasks required by the developer's APIs, instead of seeing every task running in the process.</span></span> <span data-ttu-id="0c654-125">`ICLRDebugManager`permite que o host implemente esse tipo de agrupamento.</span><span class="sxs-lookup"><span data-stu-id="0c654-125">`ICLRDebugManager` allows the host to implement this kind of grouping.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="0c654-126">Três `ICLRDebugManager` métodos, `BeginConnection` `SetConnectionTasks` e `EndConnection` , dependem uns dos outros.</span><span class="sxs-lookup"><span data-stu-id="0c654-126">Three `ICLRDebugManager` methods, `BeginConnection`, `SetConnectionTasks` and `EndConnection`, are dependent upon each other.</span></span> <span data-ttu-id="0c654-127">Eles devem ser chamados na ordem especificada para funcionar conforme o esperado.</span><span class="sxs-lookup"><span data-stu-id="0c654-127">They must be called in the given order to work as expected.</span></span>  
  
 <span data-ttu-id="0c654-128">O agrupamento e os identificadores e nomes amigáveis que o host atribui ao agrupamento não têm significado para o Common Language Runtime (CLR).</span><span class="sxs-lookup"><span data-stu-id="0c654-128">The grouping, and the identifiers and friendly names that the host assigns to the grouping, have no meaning for the common language runtime (CLR).</span></span> <span data-ttu-id="0c654-129">O CLR simplesmente passa as informações ao depurador.</span><span class="sxs-lookup"><span data-stu-id="0c654-129">The CLR merely passes the information along to the debugger.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0c654-130">Requisitos</span><span class="sxs-lookup"><span data-stu-id="0c654-130">Requirements</span></span>  
 <span data-ttu-id="0c654-131">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0c654-131">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0c654-132">**Cabeçalho:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="0c654-132">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="0c654-133">**Biblioteca:** Incluído como um recurso em MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="0c654-133">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="0c654-134">**.NET Framework versões:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0c654-134">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0c654-135">Confira também</span><span class="sxs-lookup"><span data-stu-id="0c654-135">See also</span></span>

- [<span data-ttu-id="0c654-136">Interfaces de hospedagem</span><span class="sxs-lookup"><span data-stu-id="0c654-136">Hosting Interfaces</span></span>](hosting-interfaces.md)
