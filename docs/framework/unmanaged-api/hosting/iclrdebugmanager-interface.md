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
ms.openlocfilehash: 008143c608cd19bee9dd115e97620906fb5b93b9
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73129403"
---
# <a name="iclrdebugmanager-interface"></a><span data-ttu-id="af432-102">Interface ICLRDebugManager</span><span class="sxs-lookup"><span data-stu-id="af432-102">ICLRDebugManager Interface</span></span>
<span data-ttu-id="af432-103">Fornece métodos que permitem que um host associe um conjunto de tarefas a um identificador e um nome amigável.</span><span class="sxs-lookup"><span data-stu-id="af432-103">Provides methods that allow a host to associate a set of tasks with an identifier and a friendly name.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="af432-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="af432-104">Methods</span></span>  
  
|<span data-ttu-id="af432-105">Método</span><span class="sxs-lookup"><span data-stu-id="af432-105">Method</span></span>|<span data-ttu-id="af432-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="af432-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="af432-107">Método BeginConnection</span><span class="sxs-lookup"><span data-stu-id="af432-107">BeginConnection Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-beginconnection-method.md)|<span data-ttu-id="af432-108">Estabelece uma nova conexão entre o host e o depurador para associar tarefas a um identificador e um nome amigável.</span><span class="sxs-lookup"><span data-stu-id="af432-108">Establishes a new connection between the host and the debugger to associate tasks with an identifier and a friendly name.</span></span>|  
|[<span data-ttu-id="af432-109">Método EndConnection</span><span class="sxs-lookup"><span data-stu-id="af432-109">EndConnection Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-endconnection-method.md)|<span data-ttu-id="af432-110">Remove a associação entre uma lista de tarefas e um identificador e um nome amigável.</span><span class="sxs-lookup"><span data-stu-id="af432-110">Removes the association between a list of tasks and an identifier and a friendly name.</span></span>|  
|[<span data-ttu-id="af432-111">Método GetDacl</span><span class="sxs-lookup"><span data-stu-id="af432-111">GetDacl Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-getdacl-method.md)|<span data-ttu-id="af432-112">Este método não está implementado.</span><span class="sxs-lookup"><span data-stu-id="af432-112">This method is not implemented.</span></span>|  
|[<span data-ttu-id="af432-113">Método IsDebuggerAttached</span><span class="sxs-lookup"><span data-stu-id="af432-113">IsDebuggerAttached Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-isdebuggerattached-method.md)|<span data-ttu-id="af432-114">Obtém um valor que indica se um depurador está anexado ao processo.</span><span class="sxs-lookup"><span data-stu-id="af432-114">Gets a value that indicates whether a debugger is attached to the process.</span></span>|  
|[<span data-ttu-id="af432-115">Método SetConnectionTasks</span><span class="sxs-lookup"><span data-stu-id="af432-115">SetConnectionTasks Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-setconnectiontasks-method.md)|<span data-ttu-id="af432-116">Associa uma lista de instâncias [ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) com um identificador e um nome amigável.</span><span class="sxs-lookup"><span data-stu-id="af432-116">Associates a list of [ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) instances with an identifier and a friendly name.</span></span>|  
|[<span data-ttu-id="af432-117">Método SetDacl</span><span class="sxs-lookup"><span data-stu-id="af432-117">SetDacl Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-setdacl-method.md)|<span data-ttu-id="af432-118">Este método não está implementado.</span><span class="sxs-lookup"><span data-stu-id="af432-118">This method is not implemented.</span></span>|  
|[<span data-ttu-id="af432-119">Método SetSymbolReadingPolicy</span><span class="sxs-lookup"><span data-stu-id="af432-119">SetSymbolReadingPolicy Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-setsymbolreadingpolicy-method.md)|<span data-ttu-id="af432-120">Define a política para ler arquivos de banco de dados do programa (PDB).</span><span class="sxs-lookup"><span data-stu-id="af432-120">Sets the policy for reading program database (PDB) files.</span></span> <span data-ttu-id="af432-121">A política determina se as informações sobre números de linha e arquivos estão incluídas em pilhas de chamadas.</span><span class="sxs-lookup"><span data-stu-id="af432-121">The policy determines whether information about line numbers and files is included in call stacks.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="af432-122">Comentários</span><span class="sxs-lookup"><span data-stu-id="af432-122">Remarks</span></span>  
 <span data-ttu-id="af432-123">Em cenários de depuração, um host pode querer agrupar tarefas de acordo com sua própria lógica de programação.</span><span class="sxs-lookup"><span data-stu-id="af432-123">In debugging scenarios, a host might want to group tasks according to its own programming logic.</span></span> <span data-ttu-id="af432-124">Por exemplo, um agrupamento permitiria que um desenvolvedor vêsse apenas as tarefas exigidas pelas APIs do desenvolvedor, em vez de ver cada tarefa em execução no processo.</span><span class="sxs-lookup"><span data-stu-id="af432-124">For example, a grouping would allow a developer to see only the tasks required by the developer's APIs, instead of seeing every task running in the process.</span></span> <span data-ttu-id="af432-125">`ICLRDebugManager` permite que o host implemente esse tipo de agrupamento.</span><span class="sxs-lookup"><span data-stu-id="af432-125">`ICLRDebugManager` allows the host to implement this kind of grouping.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="af432-126">Três métodos `ICLRDebugManager`, `BeginConnection`, `SetConnectionTasks` e `EndConnection`, dependem uns dos outros.</span><span class="sxs-lookup"><span data-stu-id="af432-126">Three `ICLRDebugManager` methods, `BeginConnection`, `SetConnectionTasks` and `EndConnection`, are dependent upon each other.</span></span> <span data-ttu-id="af432-127">Eles devem ser chamados na ordem especificada para funcionar conforme o esperado.</span><span class="sxs-lookup"><span data-stu-id="af432-127">They must be called in the given order to work as expected.</span></span>  
  
 <span data-ttu-id="af432-128">O agrupamento e os identificadores e nomes amigáveis que o host atribui ao agrupamento não têm significado para o Common Language Runtime (CLR).</span><span class="sxs-lookup"><span data-stu-id="af432-128">The grouping, and the identifiers and friendly names that the host assigns to the grouping, have no meaning for the common language runtime (CLR).</span></span> <span data-ttu-id="af432-129">O CLR simplesmente passa as informações ao depurador.</span><span class="sxs-lookup"><span data-stu-id="af432-129">The CLR merely passes the information along to the debugger.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="af432-130">Requisitos</span><span class="sxs-lookup"><span data-stu-id="af432-130">Requirements</span></span>  
 <span data-ttu-id="af432-131">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="af432-131">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="af432-132">**Cabeçalho:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="af432-132">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="af432-133">**Biblioteca:** Incluído como um recurso em MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="af432-133">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="af432-134">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="af432-134">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="af432-135">Consulte também</span><span class="sxs-lookup"><span data-stu-id="af432-135">See also</span></span>

- [<span data-ttu-id="af432-136">Hospedagem de Interfaces</span><span class="sxs-lookup"><span data-stu-id="af432-136">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
