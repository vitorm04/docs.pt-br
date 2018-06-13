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
ms.openlocfilehash: c3abb3e80226da909a0c7eb8e4bf54959557dcbf
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33436261"
---
# <a name="iclriocompletionmanager-interface"></a><span data-ttu-id="057c5-102">Interface ICLRIoCompletionManager</span><span class="sxs-lookup"><span data-stu-id="057c5-102">ICLRIoCompletionManager Interface</span></span>
<span data-ttu-id="057c5-103">Implementa solicitações de um método de retorno de chamada que permite que o host notificar o common language runtime (CLR) do status de e/s especificado.</span><span class="sxs-lookup"><span data-stu-id="057c5-103">Implements a callback method that allows the host to notify the common language runtime (CLR) of the status of specified I/O requests.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="057c5-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="057c5-104">Methods</span></span>  
  
|<span data-ttu-id="057c5-105">Método</span><span class="sxs-lookup"><span data-stu-id="057c5-105">Method</span></span>|<span data-ttu-id="057c5-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="057c5-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="057c5-107">Método OnComplete</span><span class="sxs-lookup"><span data-stu-id="057c5-107">OnComplete Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-oncomplete-method.md)|<span data-ttu-id="057c5-108">Notifica o CLR do status de uma solicitação de e/s foi feita usando uma chamada para o [Ihostiocompletionmanager](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-bind-method.md) método.</span><span class="sxs-lookup"><span data-stu-id="057c5-108">Notifies the CLR of the status of an I/O request that was made by using a call to the [IHostIoCompletionManager::Bind](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-bind-method.md) method.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="057c5-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="057c5-109">Remarks</span></span>  
 <span data-ttu-id="057c5-110">O host implementa a abstração de conclusão de e/s usando o [IHostIoCompletionManager](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-interface.md) interface.</span><span class="sxs-lookup"><span data-stu-id="057c5-110">The host implements the I/O completion abstraction by using the [IHostIoCompletionManager](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-interface.md) interface.</span></span> <span data-ttu-id="057c5-111">O CLR faz solicitações de e/s por meio dessa interface e o host notifica o tempo de execução do resultado dessas solicitações usando o `ICLRIoCompletionManager` interface.</span><span class="sxs-lookup"><span data-stu-id="057c5-111">The CLR makes I/O requests through this interface, and the host notifies the runtime of the outcome of such requests by using the `ICLRIoCompletionManager` interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="057c5-112">Requisitos</span><span class="sxs-lookup"><span data-stu-id="057c5-112">Requirements</span></span>  
 <span data-ttu-id="057c5-113">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="057c5-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="057c5-114">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="057c5-114">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="057c5-115">**Biblioteca:** incluído como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="057c5-115">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="057c5-116">**Versões do .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="057c5-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="057c5-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="057c5-117">See Also</span></span>  
 [<span data-ttu-id="057c5-118">Interface IHostIoCompletionManager</span><span class="sxs-lookup"><span data-stu-id="057c5-118">IHostIoCompletionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-interface.md)  
 [<span data-ttu-id="057c5-119">Interface IHostThreadPoolManager</span><span class="sxs-lookup"><span data-stu-id="057c5-119">IHostThreadPoolManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-interface.md)  
 [<span data-ttu-id="057c5-120">Hospedagem de Interfaces</span><span class="sxs-lookup"><span data-stu-id="057c5-120">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
