---
title: Interface IHostThreadPoolManager
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- IHostThreadPoolManager
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostThreadPoolManager
helpviewer_keywords:
- IHostThreadPoolManager interface [.NET Framework hosting]
ms.assetid: c3a2cd90-7c4e-4374-bb87-b41befb8344f
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 1cd58c53deec0a895ae6f67cccf26d2c8c2530be
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="ihostthreadpoolmanager-interface"></a><span data-ttu-id="a105d-102">Interface IHostThreadPoolManager</span><span class="sxs-lookup"><span data-stu-id="a105d-102">IHostThreadPoolManager Interface</span></span>
<span data-ttu-id="a105d-103">Fornece métodos que permitem que o common language runtime (CLR) para configurar o pool de threads e para a fila de itens de trabalho para o pool de threads.</span><span class="sxs-lookup"><span data-stu-id="a105d-103">Provides methods that enable the common language runtime (CLR) to configure the thread pool and to queue work items to the thread pool.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="a105d-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="a105d-104">Methods</span></span>  
  
|<span data-ttu-id="a105d-105">Método</span><span class="sxs-lookup"><span data-stu-id="a105d-105">Method</span></span>|<span data-ttu-id="a105d-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="a105d-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="a105d-107">Método GetAvailableThreads</span><span class="sxs-lookup"><span data-stu-id="a105d-107">GetAvailableThreads Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-getavailablethreads-method.md)|<span data-ttu-id="a105d-108">Obtém o número de threads no pool de threads que não estão em processamento itens de trabalho.</span><span class="sxs-lookup"><span data-stu-id="a105d-108">Gets the number of threads in the thread pool that are not currently processing work items.</span></span>|  
|[<span data-ttu-id="a105d-109">Método GetMaxThreads</span><span class="sxs-lookup"><span data-stu-id="a105d-109">GetMaxThreads Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-getmaxthreads-method.md)|<span data-ttu-id="a105d-110">Obtém o número máximo de threads que o host mantém simultaneamente no pool de threads.</span><span class="sxs-lookup"><span data-stu-id="a105d-110">Gets the maximum number of threads that the host maintains concurrently in the thread pool.</span></span>|  
|[<span data-ttu-id="a105d-111">Método GetMinThreads</span><span class="sxs-lookup"><span data-stu-id="a105d-111">GetMinThreads Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-getminthreads-method.md)|<span data-ttu-id="a105d-112">Obtém o número mínimo de threads ociosos que mantém o host antes de solicitações.</span><span class="sxs-lookup"><span data-stu-id="a105d-112">Gets the minimum number of idle threads that the host maintains in anticipation of requests.</span></span>|  
|[<span data-ttu-id="a105d-113">Método QueueUserWorkItem</span><span class="sxs-lookup"><span data-stu-id="a105d-113">QueueUserWorkItem Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-queueuserworkitem-method.md)|<span data-ttu-id="a105d-114">Uma função para a execução de filas e fornece um objeto que contém dados a serem usados pela função.</span><span class="sxs-lookup"><span data-stu-id="a105d-114">Queues a function for execution, and provides an object containing data to be used by the function.</span></span>|  
|[<span data-ttu-id="a105d-115">Método SetMaxThreads</span><span class="sxs-lookup"><span data-stu-id="a105d-115">SetMaxThreads Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-setmaxthreads-method.md)|<span data-ttu-id="a105d-116">Define o número máximo de threads que o host pode manter no pool de threads.</span><span class="sxs-lookup"><span data-stu-id="a105d-116">Sets the maximum number of threads that the host can maintain in the thread pool.</span></span>|  
|[<span data-ttu-id="a105d-117">Método SetMinThreads</span><span class="sxs-lookup"><span data-stu-id="a105d-117">SetMinThreads Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-setminthreads-method.md)|<span data-ttu-id="a105d-118">Define o número mínimo de threads ociosos que o host deve manter em antecipação de solicitações.</span><span class="sxs-lookup"><span data-stu-id="a105d-118">Sets the minimum number of idle threads that the host must maintain in anticipation of requests.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a105d-119">Comentários</span><span class="sxs-lookup"><span data-stu-id="a105d-119">Remarks</span></span>  
 <span data-ttu-id="a105d-120">O host não é necessário para configurar o pool de threads, usando os valores especificados em chamadas para o `SetMaxThreads` e `SetMinThreads` métodos.</span><span class="sxs-lookup"><span data-stu-id="a105d-120">The host is not required to configure the thread pool by using the values specified in calls to the `SetMaxThreads` and `SetMinThreads` methods.</span></span> <span data-ttu-id="a105d-121">Nesse caso, o host deve retornar um valor HRESULT de E_NOTIMPL entre esses métodos.</span><span class="sxs-lookup"><span data-stu-id="a105d-121">In this case, the host should return an HRESULT value of E_NOTIMPL from these methods.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a105d-122">Requisitos</span><span class="sxs-lookup"><span data-stu-id="a105d-122">Requirements</span></span>  
 <span data-ttu-id="a105d-123">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a105d-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a105d-124">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="a105d-124">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="a105d-125">**Biblioteca:** incluído como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="a105d-125">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="a105d-126">**Versões do .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a105d-126">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a105d-127">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a105d-127">See Also</span></span>  
 <xref:System.Threading>  
 <xref:System.Threading.ThreadPool>  
 [<span data-ttu-id="a105d-128">Hospedagem de Interfaces</span><span class="sxs-lookup"><span data-stu-id="a105d-128">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
