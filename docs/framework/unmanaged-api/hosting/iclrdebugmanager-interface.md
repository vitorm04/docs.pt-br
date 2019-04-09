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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 22c3a480e2b68377e300df1083b3178ee4e2d2a9
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59198836"
---
# <a name="iclrdebugmanager-interface"></a><span data-ttu-id="9f623-102">Interface ICLRDebugManager</span><span class="sxs-lookup"><span data-stu-id="9f623-102">ICLRDebugManager Interface</span></span>
<span data-ttu-id="9f623-103">Fornece métodos que permitem que um host associar um conjunto de tarefas com um identificador e um nome amigável.</span><span class="sxs-lookup"><span data-stu-id="9f623-103">Provides methods that allow a host to associate a set of tasks with an identifier and a friendly name.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="9f623-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="9f623-104">Methods</span></span>  
  
|<span data-ttu-id="9f623-105">Método</span><span class="sxs-lookup"><span data-stu-id="9f623-105">Method</span></span>|<span data-ttu-id="9f623-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="9f623-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="9f623-107">Método BeginConnection</span><span class="sxs-lookup"><span data-stu-id="9f623-107">BeginConnection Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-beginconnection-method.md)|<span data-ttu-id="9f623-108">Estabelece uma nova conexão entre o host e o depurador para associar tarefas com um identificador e um nome amigável.</span><span class="sxs-lookup"><span data-stu-id="9f623-108">Establishes a new connection between the host and the debugger to associate tasks with an identifier and a friendly name.</span></span>|  
|[<span data-ttu-id="9f623-109">Método EndConnection</span><span class="sxs-lookup"><span data-stu-id="9f623-109">EndConnection Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-endconnection-method.md)|<span data-ttu-id="9f623-110">Remove a associação entre uma lista de tarefas e um identificador e um nome amigável.</span><span class="sxs-lookup"><span data-stu-id="9f623-110">Removes the association between a list of tasks and an identifier and a friendly name.</span></span>|  
|[<span data-ttu-id="9f623-111">Método GetDacl</span><span class="sxs-lookup"><span data-stu-id="9f623-111">GetDacl Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-getdacl-method.md)|<span data-ttu-id="9f623-112">Este método não está implementado.</span><span class="sxs-lookup"><span data-stu-id="9f623-112">This method is not implemented.</span></span>|  
|[<span data-ttu-id="9f623-113">Método IsDebuggerAttached</span><span class="sxs-lookup"><span data-stu-id="9f623-113">IsDebuggerAttached Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-isdebuggerattached-method.md)|<span data-ttu-id="9f623-114">Obtém um valor que indica se um depurador está anexado ao processo.</span><span class="sxs-lookup"><span data-stu-id="9f623-114">Gets a value that indicates whether a debugger is attached to the process.</span></span>|  
|[<span data-ttu-id="9f623-115">Método SetConnectionTasks</span><span class="sxs-lookup"><span data-stu-id="9f623-115">SetConnectionTasks Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-setconnectiontasks-method.md)|<span data-ttu-id="9f623-116">Associa uma lista dos [ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) instâncias com um identificador e um nome amigável.</span><span class="sxs-lookup"><span data-stu-id="9f623-116">Associates a list of [ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) instances with an identifier and a friendly name.</span></span>|  
|[<span data-ttu-id="9f623-117">Método SetDacl</span><span class="sxs-lookup"><span data-stu-id="9f623-117">SetDacl Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-setdacl-method.md)|<span data-ttu-id="9f623-118">Este método não está implementado.</span><span class="sxs-lookup"><span data-stu-id="9f623-118">This method is not implemented.</span></span>|  
|[<span data-ttu-id="9f623-119">Método SetSymbolReadingPolicy</span><span class="sxs-lookup"><span data-stu-id="9f623-119">SetSymbolReadingPolicy Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-setsymbolreadingpolicy-method.md)|<span data-ttu-id="9f623-120">Define a política para a leitura de arquivos de banco de dados (PDB) do programa.</span><span class="sxs-lookup"><span data-stu-id="9f623-120">Sets the policy for reading program database (PDB) files.</span></span> <span data-ttu-id="9f623-121">A política determina se a opção informações sobre arquivos e números de linha estão incluídas em pilhas de chamadas.</span><span class="sxs-lookup"><span data-stu-id="9f623-121">The policy determines whether information about line numbers and files is included in call stacks.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9f623-122">Comentários</span><span class="sxs-lookup"><span data-stu-id="9f623-122">Remarks</span></span>  
 <span data-ttu-id="9f623-123">Em cenários de depuração, um host pode querer agrupar tarefas de acordo com sua própria lógica de programação.</span><span class="sxs-lookup"><span data-stu-id="9f623-123">In debugging scenarios, a host might want to group tasks according to its own programming logic.</span></span> <span data-ttu-id="9f623-124">Por exemplo, um agrupamento permitiria que um desenvolvedor ver somente as tarefas necessárias para as APIs do desenvolvedor, em vez de ver todas as tarefas em execução no processo.</span><span class="sxs-lookup"><span data-stu-id="9f623-124">For example, a grouping would allow a developer to see only the tasks required by the developer's APIs, instead of seeing every task running in the process.</span></span> `ICLRDebugManager` <span data-ttu-id="9f623-125">permite que o host implementar esse tipo de agrupamento.</span><span class="sxs-lookup"><span data-stu-id="9f623-125">allows the host to implement this kind of grouping.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="9f623-126">Três `ICLRDebugManager` métodos, `BeginConnection`, `SetConnectionTasks` e `EndConnection`, são dependentes entre si.</span><span class="sxs-lookup"><span data-stu-id="9f623-126">Three `ICLRDebugManager` methods, `BeginConnection`, `SetConnectionTasks` and `EndConnection`, are dependent upon each other.</span></span> <span data-ttu-id="9f623-127">Eles devem ser chamados na ordem fornecida para funcionar conforme o esperado.</span><span class="sxs-lookup"><span data-stu-id="9f623-127">They must be called in the given order to work as expected.</span></span>  
  
 <span data-ttu-id="9f623-128">O agrupamento e os identificadores e nomes amigáveis que o host atribui ao agrupamento, não têm significado para o common language runtime (CLR).</span><span class="sxs-lookup"><span data-stu-id="9f623-128">The grouping, and the identifiers and friendly names that the host assigns to the grouping, have no meaning for the common language runtime (CLR).</span></span> <span data-ttu-id="9f623-129">O CLR simplesmente passa as informações ao longo do depurador.</span><span class="sxs-lookup"><span data-stu-id="9f623-129">The CLR merely passes the information along to the debugger.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9f623-130">Requisitos</span><span class="sxs-lookup"><span data-stu-id="9f623-130">Requirements</span></span>  
 <span data-ttu-id="9f623-131">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9f623-131">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9f623-132">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="9f623-132">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="9f623-133">**Biblioteca:** Incluído como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="9f623-133">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 **<span data-ttu-id="9f623-134">Versões do .NET Framework:</span><span class="sxs-lookup"><span data-stu-id="9f623-134">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="9f623-135">Consulte também</span><span class="sxs-lookup"><span data-stu-id="9f623-135">See also</span></span>

- [<span data-ttu-id="9f623-136">Interfaces de hospedagem</span><span class="sxs-lookup"><span data-stu-id="9f623-136">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
