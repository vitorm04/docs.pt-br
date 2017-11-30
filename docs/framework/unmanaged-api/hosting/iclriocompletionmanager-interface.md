---
title: Interface ICLRIoCompletionManager
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRIoCompletionManager
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRIoCompletionManager
helpviewer_keywords: ICLRIoCompletionManager interface [.NET Framework hosting]
ms.assetid: c6c3ace6-e5e7-4450-8cc5-a9a48208c493
topic_type: apiref
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: dbff3c39da2a18ab45f0ea03d1e1588aa61c7c3c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="iclriocompletionmanager-interface"></a><span data-ttu-id="6d676-102">Interface ICLRIoCompletionManager</span><span class="sxs-lookup"><span data-stu-id="6d676-102">ICLRIoCompletionManager Interface</span></span>
<span data-ttu-id="6d676-103">Implementa solicitações de um método de retorno de chamada que permite que o host notificar o common language runtime (CLR) do status de e/s especificado.</span><span class="sxs-lookup"><span data-stu-id="6d676-103">Implements a callback method that allows the host to notify the common language runtime (CLR) of the status of specified I/O requests.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="6d676-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="6d676-104">Methods</span></span>  
  
|<span data-ttu-id="6d676-105">Método</span><span class="sxs-lookup"><span data-stu-id="6d676-105">Method</span></span>|<span data-ttu-id="6d676-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="6d676-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="6d676-107">Método OnComplete</span><span class="sxs-lookup"><span data-stu-id="6d676-107">OnComplete Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-oncomplete-method.md)|<span data-ttu-id="6d676-108">Notifica o CLR do status de uma solicitação de e/s foi feita usando uma chamada para o [Ihostiocompletionmanager](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-bind-method.md) método.</span><span class="sxs-lookup"><span data-stu-id="6d676-108">Notifies the CLR of the status of an I/O request that was made by using a call to the [IHostIoCompletionManager::Bind](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-bind-method.md) method.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6d676-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="6d676-109">Remarks</span></span>  
 <span data-ttu-id="6d676-110">O host implementa a abstração de conclusão de e/s usando o [IHostIoCompletionManager](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-interface.md) interface.</span><span class="sxs-lookup"><span data-stu-id="6d676-110">The host implements the I/O completion abstraction by using the [IHostIoCompletionManager](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-interface.md) interface.</span></span> <span data-ttu-id="6d676-111">O CLR faz solicitações de e/s por meio dessa interface e o host notifica o tempo de execução do resultado dessas solicitações usando o `ICLRIoCompletionManager` interface.</span><span class="sxs-lookup"><span data-stu-id="6d676-111">The CLR makes I/O requests through this interface, and the host notifies the runtime of the outcome of such requests by using the `ICLRIoCompletionManager` interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6d676-112">Requisitos</span><span class="sxs-lookup"><span data-stu-id="6d676-112">Requirements</span></span>  
 <span data-ttu-id="6d676-113">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6d676-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6d676-114">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="6d676-114">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="6d676-115">**Biblioteca:** incluído como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="6d676-115">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="6d676-116">**Versões do .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6d676-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6d676-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="6d676-117">See Also</span></span>  
 [<span data-ttu-id="6d676-118">Interface IHostIoCompletionManager</span><span class="sxs-lookup"><span data-stu-id="6d676-118">IHostIoCompletionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-interface.md)  
 [<span data-ttu-id="6d676-119">Interface IHostThreadPoolManager</span><span class="sxs-lookup"><span data-stu-id="6d676-119">IHostThreadPoolManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-interface.md)  
 [<span data-ttu-id="6d676-120">Interfaces de hospedagem</span><span class="sxs-lookup"><span data-stu-id="6d676-120">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
