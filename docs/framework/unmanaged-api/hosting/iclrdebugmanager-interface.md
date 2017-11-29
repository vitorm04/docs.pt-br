---
title: Interface ICLRDebugManager
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRDebugManager
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRDebugManager
helpviewer_keywords: ICLRDebugManager interface [.NET Framework hosting]
ms.assetid: e835062c-c7d6-4945-8a44-2de7ebf3928e
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 0e537b955524f2721868ddf5da9fccf68f9d4efd
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="iclrdebugmanager-interface"></a><span data-ttu-id="217a3-102">Interface ICLRDebugManager</span><span class="sxs-lookup"><span data-stu-id="217a3-102">ICLRDebugManager Interface</span></span>
<span data-ttu-id="217a3-103">Fornece métodos que permitem que um host associar um conjunto de tarefas com um identificador e um nome amigável.</span><span class="sxs-lookup"><span data-stu-id="217a3-103">Provides methods that allow a host to associate a set of tasks with an identifier and a friendly name.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="217a3-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="217a3-104">Methods</span></span>  
  
|<span data-ttu-id="217a3-105">Método</span><span class="sxs-lookup"><span data-stu-id="217a3-105">Method</span></span>|<span data-ttu-id="217a3-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="217a3-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="217a3-107">Método BeginConnection</span><span class="sxs-lookup"><span data-stu-id="217a3-107">BeginConnection Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-beginconnection-method.md)|<span data-ttu-id="217a3-108">Estabelece uma nova conexão entre o host e o depurador para associar tarefas com um identificador e um nome amigável.</span><span class="sxs-lookup"><span data-stu-id="217a3-108">Establishes a new connection between the host and the debugger to associate tasks with an identifier and a friendly name.</span></span>|  
|[<span data-ttu-id="217a3-109">Método EndConnection</span><span class="sxs-lookup"><span data-stu-id="217a3-109">EndConnection Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-endconnection-method.md)|<span data-ttu-id="217a3-110">Remove a associação entre uma lista de tarefas e um identificador e um nome amigável.</span><span class="sxs-lookup"><span data-stu-id="217a3-110">Removes the association between a list of tasks and an identifier and a friendly name.</span></span>|  
|[<span data-ttu-id="217a3-111">Método GetDacl</span><span class="sxs-lookup"><span data-stu-id="217a3-111">GetDacl Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-getdacl-method.md)|<span data-ttu-id="217a3-112">Este método não está implementado.</span><span class="sxs-lookup"><span data-stu-id="217a3-112">This method is not implemented.</span></span>|  
|[<span data-ttu-id="217a3-113">Método IsDebuggerAttached</span><span class="sxs-lookup"><span data-stu-id="217a3-113">IsDebuggerAttached Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-isdebuggerattached-method.md)|<span data-ttu-id="217a3-114">Obtém um valor que indica se um depurador está anexado ao processo.</span><span class="sxs-lookup"><span data-stu-id="217a3-114">Gets a value that indicates whether a debugger is attached to the process.</span></span>|  
|[<span data-ttu-id="217a3-115">Método SetConnectionTasks</span><span class="sxs-lookup"><span data-stu-id="217a3-115">SetConnectionTasks Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-setconnectiontasks-method.md)|<span data-ttu-id="217a3-116">Associa uma lista de [ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) instâncias com um identificador e um nome amigável.</span><span class="sxs-lookup"><span data-stu-id="217a3-116">Associates a list of [ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) instances with an identifier and a friendly name.</span></span>|  
|[<span data-ttu-id="217a3-117">Método SetDacl</span><span class="sxs-lookup"><span data-stu-id="217a3-117">SetDacl Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-setdacl-method.md)|<span data-ttu-id="217a3-118">Este método não está implementado.</span><span class="sxs-lookup"><span data-stu-id="217a3-118">This method is not implemented.</span></span>|  
|[<span data-ttu-id="217a3-119">Método SetSymbolReadingPolicy</span><span class="sxs-lookup"><span data-stu-id="217a3-119">SetSymbolReadingPolicy Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-setsymbolreadingpolicy-method.md)|<span data-ttu-id="217a3-120">Define a política para a leitura de arquivos do programa (PDB) de banco de dados.</span><span class="sxs-lookup"><span data-stu-id="217a3-120">Sets the policy for reading program database (PDB) files.</span></span> <span data-ttu-id="217a3-121">A política determina se as informações sobre números de linha e de arquivos estão incluídas em pilhas de chamadas.</span><span class="sxs-lookup"><span data-stu-id="217a3-121">The policy determines whether information about line numbers and files is included in call stacks.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="217a3-122">Comentários</span><span class="sxs-lookup"><span data-stu-id="217a3-122">Remarks</span></span>  
 <span data-ttu-id="217a3-123">Em cenários de depuração, um host pode querer agrupar tarefas de acordo com sua própria lógica de programação.</span><span class="sxs-lookup"><span data-stu-id="217a3-123">In debugging scenarios, a host might want to group tasks according to its own programming logic.</span></span> <span data-ttu-id="217a3-124">Por exemplo, um agrupamento permitiria que um desenvolvedor ver somente as tarefas necessárias por APIs do desenvolvedor, ao invés de fazer todas as tarefas em execução no processo.</span><span class="sxs-lookup"><span data-stu-id="217a3-124">For example, a grouping would allow a developer to see only the tasks required by the developer's APIs, instead of seeing every task running in the process.</span></span> <span data-ttu-id="217a3-125">`ICLRDebugManager`permite que o host implementar esse tipo de agrupamento.</span><span class="sxs-lookup"><span data-stu-id="217a3-125">`ICLRDebugManager` allows the host to implement this kind of grouping.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="217a3-126">Três `ICLRDebugManager` métodos, `BeginConnection`, `SetConnectionTasks` e `EndConnection`, são dependentes entre si.</span><span class="sxs-lookup"><span data-stu-id="217a3-126">Three `ICLRDebugManager` methods, `BeginConnection`, `SetConnectionTasks` and `EndConnection`, are dependent upon each other.</span></span> <span data-ttu-id="217a3-127">Ele devem ser chamados na ordem fornecida para funcionar como esperado.</span><span class="sxs-lookup"><span data-stu-id="217a3-127">They must be called in the given order to work as expected.</span></span>  
  
 <span data-ttu-id="217a3-128">O agrupamento e os identificadores e nomes amigáveis que atribui o host para o agrupamento não têm significado para o common language runtime (CLR).</span><span class="sxs-lookup"><span data-stu-id="217a3-128">The grouping, and the identifiers and friendly names that the host assigns to the grouping, have no meaning for the common language runtime (CLR).</span></span> <span data-ttu-id="217a3-129">O CLR simplesmente passa as informações ao longo do depurador.</span><span class="sxs-lookup"><span data-stu-id="217a3-129">The CLR merely passes the information along to the debugger.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="217a3-130">Requisitos</span><span class="sxs-lookup"><span data-stu-id="217a3-130">Requirements</span></span>  
 <span data-ttu-id="217a3-131">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="217a3-131">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="217a3-132">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="217a3-132">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="217a3-133">**Biblioteca:** incluído como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="217a3-133">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="217a3-134">**Versões do .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="217a3-134">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="217a3-135">Consulte também</span><span class="sxs-lookup"><span data-stu-id="217a3-135">See Also</span></span>  
 [<span data-ttu-id="217a3-136">Interfaces de hospedagem</span><span class="sxs-lookup"><span data-stu-id="217a3-136">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
