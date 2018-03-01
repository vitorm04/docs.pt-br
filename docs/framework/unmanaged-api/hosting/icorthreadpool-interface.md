---
title: Interface ICorThreadpool
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
- ICorThreadpool
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICorThreadpool
helpviewer_keywords:
- ICorThreadpool interface [.NET Framework hosting]
ms.assetid: 18485a27-cae3-4c6a-baa8-f7df601122d5
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: d7b6ec470fae6adb76a9b78fdab9b871edc0ca49
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="icorthreadpool-interface"></a><span data-ttu-id="d6795-102">Interface ICorThreadpool</span><span class="sxs-lookup"><span data-stu-id="d6795-102">ICorThreadpool Interface</span></span>
<span data-ttu-id="d6795-103">Fornece métodos para acessar o pool de threads.</span><span class="sxs-lookup"><span data-stu-id="d6795-103">Provides methods for accessing the thread pool.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d6795-104">Essa interface é reservada para uso interno apenas.</span><span class="sxs-lookup"><span data-stu-id="d6795-104">This interface is reserved for internal use only.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="d6795-105">Métodos</span><span class="sxs-lookup"><span data-stu-id="d6795-105">Methods</span></span>  
  
|<span data-ttu-id="d6795-106">Método</span><span class="sxs-lookup"><span data-stu-id="d6795-106">Method</span></span>|<span data-ttu-id="d6795-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="d6795-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="d6795-108">Método CorRegisterWaitForSingleObject</span><span class="sxs-lookup"><span data-stu-id="d6795-108">CorRegisterWaitForSingleObject Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorthreadpool-corregisterwaitforsingleobject-method.md)|<span data-ttu-id="d6795-109">Reservado apenas para uso interno.</span><span class="sxs-lookup"><span data-stu-id="d6795-109">Reserved for internal use only.</span></span>|  
|[<span data-ttu-id="d6795-110">Método CorUnregisterWait</span><span class="sxs-lookup"><span data-stu-id="d6795-110">CorUnregisterWait Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorthreadpool-corunregisterwait-method.md)|<span data-ttu-id="d6795-111">Reservado apenas para uso interno.</span><span class="sxs-lookup"><span data-stu-id="d6795-111">Reserved for internal use only.</span></span>|  
|[<span data-ttu-id="d6795-112">Método CorQueueUserWorkItem</span><span class="sxs-lookup"><span data-stu-id="d6795-112">CorQueueUserWorkItem Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorthreadpool-corqueueuserworkitem-method.md)|<span data-ttu-id="d6795-113">Reservado apenas para uso interno.</span><span class="sxs-lookup"><span data-stu-id="d6795-113">Reserved for internal use only.</span></span>|  
|[<span data-ttu-id="d6795-114">Método CorCreateTimer</span><span class="sxs-lookup"><span data-stu-id="d6795-114">CorCreateTimer Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorthreadpool-corcreatetimer-method.md)|<span data-ttu-id="d6795-115">Reservado apenas para uso interno.</span><span class="sxs-lookup"><span data-stu-id="d6795-115">Reserved for internal use only.</span></span>|  
|[<span data-ttu-id="d6795-116">Método CorChangeTimer</span><span class="sxs-lookup"><span data-stu-id="d6795-116">CorChangeTimer Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorthreadpool-corchangetimer-method.md)|<span data-ttu-id="d6795-117">Reservado apenas para uso interno.</span><span class="sxs-lookup"><span data-stu-id="d6795-117">Reserved for internal use only.</span></span>|  
|[<span data-ttu-id="d6795-118">Método CorDeleteTimer</span><span class="sxs-lookup"><span data-stu-id="d6795-118">CorDeleteTimer Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorthreadpool-cordeletetimer-method.md)|<span data-ttu-id="d6795-119">Reservado apenas para uso interno.</span><span class="sxs-lookup"><span data-stu-id="d6795-119">Reserved for internal use only.</span></span>|  
|[<span data-ttu-id="d6795-120">Método CorBindIoCompletionCallback</span><span class="sxs-lookup"><span data-stu-id="d6795-120">CorBindIoCompletionCallback Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorthreadpool-corbindiocompletioncallback-method.md)|<span data-ttu-id="d6795-121">Reservado apenas para uso interno.</span><span class="sxs-lookup"><span data-stu-id="d6795-121">Reserved for internal use only.</span></span>|  
|[<span data-ttu-id="d6795-122">Método CorCallOrQueueUserWorkItem</span><span class="sxs-lookup"><span data-stu-id="d6795-122">CorCallOrQueueUserWorkItem Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorthreadpool-corcallorqueueuserworkitem-method.md)|<span data-ttu-id="d6795-123">Reservado apenas para uso interno.</span><span class="sxs-lookup"><span data-stu-id="d6795-123">Reserved for internal use only.</span></span>|  
|[<span data-ttu-id="d6795-124">Método CorSetMaxThreads</span><span class="sxs-lookup"><span data-stu-id="d6795-124">CorSetMaxThreads Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorthreadpool-corsetmaxthreads-method.md)|<span data-ttu-id="d6795-125">Reservado apenas para uso interno.</span><span class="sxs-lookup"><span data-stu-id="d6795-125">Reserved for internal use only.</span></span>|  
|[<span data-ttu-id="d6795-126">Método CorGetMaxThreads</span><span class="sxs-lookup"><span data-stu-id="d6795-126">CorGetMaxThreads Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorthreadpool-corgetmaxthreads-method.md)|<span data-ttu-id="d6795-127">Reservado apenas para uso interno.</span><span class="sxs-lookup"><span data-stu-id="d6795-127">Reserved for internal use only.</span></span>|  
|[<span data-ttu-id="d6795-128">Método CorGetAvailableThreads</span><span class="sxs-lookup"><span data-stu-id="d6795-128">CorGetAvailableThreads Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorthreadpool-corgetavailablethreads-method.md)|<span data-ttu-id="d6795-129">Reservado apenas para uso interno.</span><span class="sxs-lookup"><span data-stu-id="d6795-129">Reserved for internal use only.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="d6795-130">Requisitos</span><span class="sxs-lookup"><span data-stu-id="d6795-130">Requirements</span></span>  
 <span data-ttu-id="d6795-131">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d6795-131">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d6795-132">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="d6795-132">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="d6795-133">**Biblioteca:** incluído como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="d6795-133">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="d6795-134">**Versões do .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d6795-134">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d6795-135">Consulte também</span><span class="sxs-lookup"><span data-stu-id="d6795-135">See Also</span></span>  
 [<span data-ttu-id="d6795-136">Hospedagem de Interfaces</span><span class="sxs-lookup"><span data-stu-id="d6795-136">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
