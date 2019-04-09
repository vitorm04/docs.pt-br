---
title: Interface ICLRIoCompletionManager
ms.date: 03/30/2017
api_name:
- ICLRIoCompletionManager
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRIoCompletionManager
helpviewer_keywords:
- ICLRIoCompletionManager interface [.NET Framework hosting]
ms.assetid: c6c3ace6-e5e7-4450-8cc5-a9a48208c493
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7864bb81c3b457bf8ec07cd194d24b29a42bd441
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59156059"
---
# <a name="iclriocompletionmanager-interface"></a><span data-ttu-id="82358-102">Interface ICLRIoCompletionManager</span><span class="sxs-lookup"><span data-stu-id="82358-102">ICLRIoCompletionManager Interface</span></span>
<span data-ttu-id="82358-103">Implementa solicitações de um método de retorno de chamada que permite que o host notificar o common language runtime (CLR) do status de e/s especificado.</span><span class="sxs-lookup"><span data-stu-id="82358-103">Implements a callback method that allows the host to notify the common language runtime (CLR) of the status of specified I/O requests.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="82358-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="82358-104">Methods</span></span>  
  
|<span data-ttu-id="82358-105">Método</span><span class="sxs-lookup"><span data-stu-id="82358-105">Method</span></span>|<span data-ttu-id="82358-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="82358-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="82358-107">Método OnComplete</span><span class="sxs-lookup"><span data-stu-id="82358-107">OnComplete Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-oncomplete-method.md)|<span data-ttu-id="82358-108">Notifica o CLR do status de uma solicitação de e/s foi feita usando uma chamada para o [ihostiocompletionmanager:: Bind](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-bind-method.md) método.</span><span class="sxs-lookup"><span data-stu-id="82358-108">Notifies the CLR of the status of an I/O request that was made by using a call to the [IHostIoCompletionManager::Bind](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-bind-method.md) method.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="82358-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="82358-109">Remarks</span></span>  
 <span data-ttu-id="82358-110">O host implementa a abstração de conclusão de e/s usando o [IHostIoCompletionManager](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-interface.md) interface.</span><span class="sxs-lookup"><span data-stu-id="82358-110">The host implements the I/O completion abstraction by using the [IHostIoCompletionManager](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-interface.md) interface.</span></span> <span data-ttu-id="82358-111">O CLR faz solicitações de e/s por meio dessa interface e o host notifica o tempo de execução do resultado de tais solicitações usando o `ICLRIoCompletionManager` interface.</span><span class="sxs-lookup"><span data-stu-id="82358-111">The CLR makes I/O requests through this interface, and the host notifies the runtime of the outcome of such requests by using the `ICLRIoCompletionManager` interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="82358-112">Requisitos</span><span class="sxs-lookup"><span data-stu-id="82358-112">Requirements</span></span>  
 <span data-ttu-id="82358-113">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="82358-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="82358-114">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="82358-114">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="82358-115">**Biblioteca:** Incluído como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="82358-115">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 **<span data-ttu-id="82358-116">Versões do .NET Framework:</span><span class="sxs-lookup"><span data-stu-id="82358-116">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="82358-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="82358-117">See also</span></span>

- [<span data-ttu-id="82358-118">Interface IHostIoCompletionManager</span><span class="sxs-lookup"><span data-stu-id="82358-118">IHostIoCompletionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-interface.md)
- [<span data-ttu-id="82358-119">Interface IHostThreadPoolManager</span><span class="sxs-lookup"><span data-stu-id="82358-119">IHostThreadPoolManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-interface.md)
- [<span data-ttu-id="82358-120">Interfaces de hospedagem</span><span class="sxs-lookup"><span data-stu-id="82358-120">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
