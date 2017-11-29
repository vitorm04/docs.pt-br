---
title: "Método ICLRGCManager::Collect"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRGCManager.Collect
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRGCManager::Collect
helpviewer_keywords:
- ICLRGCManager::Collect method [.NET Framework hosting]
- Collect method, ICLRGCManager interface [.NET Framework hosting]
ms.assetid: 0c6cbbea-c27c-4695-bda3-17c1910d8ddb
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 96f99855654a3a86873ca4623d8617f74030938b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="iclrgcmanagercollect-method"></a><span data-ttu-id="c6fa8-102">Método ICLRGCManager::Collect</span><span class="sxs-lookup"><span data-stu-id="c6fa8-102">ICLRGCManager::Collect Method</span></span>
<span data-ttu-id="c6fa8-103">Força uma coleta de lixo para a geração especificada.</span><span class="sxs-lookup"><span data-stu-id="c6fa8-103">Forces a garbage collection for the specified generation.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c6fa8-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="c6fa8-104">Syntax</span></span>  
  
```  
HRESULT Collect (  
    [in] LONG Generation  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="c6fa8-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="c6fa8-105">Parameters</span></span>  
 `Generation`  
 <span data-ttu-id="c6fa8-106">[in] A geração para coletar.</span><span class="sxs-lookup"><span data-stu-id="c6fa8-106">[in] The generation to collect.</span></span> <span data-ttu-id="c6fa8-107">Um valor de -1 força uma coleção de todas as gerações.</span><span class="sxs-lookup"><span data-stu-id="c6fa8-107">A value of -1 forces a collection of all generations.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="c6fa8-108">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="c6fa8-108">Return Value</span></span>  
  
|<span data-ttu-id="c6fa8-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="c6fa8-109">HRESULT</span></span>|<span data-ttu-id="c6fa8-110">Descrição</span><span class="sxs-lookup"><span data-stu-id="c6fa8-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="c6fa8-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="c6fa8-111">S_OK</span></span>|<span data-ttu-id="c6fa8-112">`Collect`retornou com êxito.</span><span class="sxs-lookup"><span data-stu-id="c6fa8-112">`Collect` returned successfully.</span></span>|  
|<span data-ttu-id="c6fa8-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="c6fa8-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="c6fa8-114">O common language runtime (CLR) não foi carregado em um processo ou o CLR está em um estado em que ele não pode executar código gerenciado ou processar a chamada com êxito.</span><span class="sxs-lookup"><span data-stu-id="c6fa8-114">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="c6fa8-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="c6fa8-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="c6fa8-116">A chamada foi atingido.</span><span class="sxs-lookup"><span data-stu-id="c6fa8-116">The call timed out.</span></span>|  
|<span data-ttu-id="c6fa8-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="c6fa8-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="c6fa8-118">O chamador não possui o bloqueio.</span><span class="sxs-lookup"><span data-stu-id="c6fa8-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="c6fa8-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="c6fa8-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="c6fa8-120">Um evento foi cancelado durante um thread bloqueado ou fibra estava aguardando nele.</span><span class="sxs-lookup"><span data-stu-id="c6fa8-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="c6fa8-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="c6fa8-121">E_FAIL</span></span>|<span data-ttu-id="c6fa8-122">Ocorreu uma falha catastrófica desconhecida.</span><span class="sxs-lookup"><span data-stu-id="c6fa8-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="c6fa8-123">Depois que um método retornará E_FAIL, o CLR não será mais utilizável dentro do processo.</span><span class="sxs-lookup"><span data-stu-id="c6fa8-123">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="c6fa8-124">As chamadas subsequentes para hospedagem métodos retornam HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="c6fa8-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c6fa8-125">Comentários</span><span class="sxs-lookup"><span data-stu-id="c6fa8-125">Remarks</span></span>  
 <span data-ttu-id="c6fa8-126">O `Collect` método força o coletor de lixo do CLR para executar uma coleção, independentemente de seu estado atual.</span><span class="sxs-lookup"><span data-stu-id="c6fa8-126">The `Collect` method forces the CLR's garbage collector to perform a collection regardless of its current state.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c6fa8-127">Requisitos</span><span class="sxs-lookup"><span data-stu-id="c6fa8-127">Requirements</span></span>  
 <span data-ttu-id="c6fa8-128">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c6fa8-128">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c6fa8-129">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="c6fa8-129">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="c6fa8-130">**Biblioteca:** incluído como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="c6fa8-130">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="c6fa8-131">**Versões do .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c6fa8-131">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c6fa8-132">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c6fa8-132">See Also</span></span>  
 [<span data-ttu-id="c6fa8-133">Gerenciamento Automático de Memória</span><span class="sxs-lookup"><span data-stu-id="c6fa8-133">Automatic Memory Management</span></span>](../../../../docs/standard/automatic-memory-management.md)  
 [<span data-ttu-id="c6fa8-134">Coleta de lixo</span><span class="sxs-lookup"><span data-stu-id="c6fa8-134">Garbage Collection</span></span>](../../../../docs/standard/garbage-collection/index.md)  
 [<span data-ttu-id="c6fa8-135">Interface ICLRControl</span><span class="sxs-lookup"><span data-stu-id="c6fa8-135">ICLRControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)  
 [<span data-ttu-id="c6fa8-136">Interface ICLRGCManager</span><span class="sxs-lookup"><span data-stu-id="c6fa8-136">ICLRGCManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager-interface.md)  
 [<span data-ttu-id="c6fa8-137">Interfaces de hospedagem CLR</span><span class="sxs-lookup"><span data-stu-id="c6fa8-137">CLR Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/clr-hosting-interfaces.md)  
 [<span data-ttu-id="c6fa8-138">Interfaces de hospedagem</span><span class="sxs-lookup"><span data-stu-id="c6fa8-138">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)  
 [<span data-ttu-id="c6fa8-139">Hospedagem</span><span class="sxs-lookup"><span data-stu-id="c6fa8-139">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)
