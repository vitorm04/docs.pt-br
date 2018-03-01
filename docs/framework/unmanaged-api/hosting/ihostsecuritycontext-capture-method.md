---
title: "Método IHostSecurityContext::Capture"
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
- IHostSecurityContext.Capture
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostSecurityContext::Capture
helpviewer_keywords:
- Capture method [.NET Framework hosting]
- IHostSecurityContext::Capture method [.NET Framework hosting]
ms.assetid: ae0836d0-1170-4494-bac5-d0e809df51a2
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: def431dd40c6dd7aa6688a638971d3676bbd1ffb
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="ihostsecuritycontextcapture-method"></a><span data-ttu-id="268c3-102">Método IHostSecurityContext::Capture</span><span class="sxs-lookup"><span data-stu-id="268c3-102">IHostSecurityContext::Capture Method</span></span>
<span data-ttu-id="268c3-103">Obtém um clone do [IHostSecurityContext](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritycontext-interface.md) instância retornada de uma chamada para [Ihostsecuritymanager](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-getsecuritycontext-method.md).</span><span class="sxs-lookup"><span data-stu-id="268c3-103">Gets a clone of the [IHostSecurityContext](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritycontext-interface.md) instance returned from a call to [IHostSecurityManager::GetSecurityContext](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-getsecuritycontext-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="268c3-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="268c3-104">Syntax</span></span>  
  
```  
HRESULT Capture (  
    [out] IHostSecurityContext** ppClonedContext  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="268c3-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="268c3-105">Parameters</span></span>  
 `ppClonedContext`  
 <span data-ttu-id="268c3-106">[out] Um ponteiro para o endereço de um clone do `IHostSecurityContext` objeto a ser capturado.</span><span class="sxs-lookup"><span data-stu-id="268c3-106">[out] A pointer to the address of a clone of the `IHostSecurityContext` object to be captured.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="268c3-107">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="268c3-107">Return Value</span></span>  
  
|<span data-ttu-id="268c3-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="268c3-108">HRESULT</span></span>|<span data-ttu-id="268c3-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="268c3-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="268c3-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="268c3-110">S_OK</span></span>|<span data-ttu-id="268c3-111">`Capture`retornou com êxito.</span><span class="sxs-lookup"><span data-stu-id="268c3-111">`Capture` returned successfully.</span></span>|  
|<span data-ttu-id="268c3-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="268c3-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="268c3-113">O common language runtime (CLR) não foi carregado em um processo ou o CLR está em um estado em que ele não pode executar código gerenciado ou processar a chamada com êxito.</span><span class="sxs-lookup"><span data-stu-id="268c3-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="268c3-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="268c3-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="268c3-115">A chamada foi atingido.</span><span class="sxs-lookup"><span data-stu-id="268c3-115">The call timed out.</span></span>|  
|<span data-ttu-id="268c3-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="268c3-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="268c3-117">O chamador não possui o bloqueio.</span><span class="sxs-lookup"><span data-stu-id="268c3-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="268c3-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="268c3-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="268c3-119">Um evento foi cancelado durante um thread bloqueado ou fibra estava aguardando nele.</span><span class="sxs-lookup"><span data-stu-id="268c3-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="268c3-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="268c3-120">E_FAIL</span></span>|<span data-ttu-id="268c3-121">Ocorreu uma falha catastrófica desconhecida.</span><span class="sxs-lookup"><span data-stu-id="268c3-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="268c3-122">Quando um método retornará E_FAIL, o CLR não será mais utilizável dentro do processo.</span><span class="sxs-lookup"><span data-stu-id="268c3-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="268c3-123">As chamadas subsequentes para hospedagem métodos retornam HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="268c3-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="268c3-124">Comentários</span><span class="sxs-lookup"><span data-stu-id="268c3-124">Remarks</span></span>  
 <span data-ttu-id="268c3-125">O ponteiro de interface retornado de `Capture` é um clone do contexto capturado.</span><span class="sxs-lookup"><span data-stu-id="268c3-125">The interface pointer returned from `Capture` is a clone of the captured context.</span></span> <span data-ttu-id="268c3-126">Quando essas informações são movidas em um ponto de código assíncrono, seu tempo de vida é separado do que o ponteiro sobre o qual a chamada foi feita.</span><span class="sxs-lookup"><span data-stu-id="268c3-126">When this information is moved across an asynchronous code point, its lifetime is separated from that of the pointer against which the call was made.</span></span> <span data-ttu-id="268c3-127">O ponteiro original, portanto, pode ser liberado.</span><span class="sxs-lookup"><span data-stu-id="268c3-127">The original pointer can therefore be released.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="268c3-128">Requisitos</span><span class="sxs-lookup"><span data-stu-id="268c3-128">Requirements</span></span>  
 <span data-ttu-id="268c3-129">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="268c3-129">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="268c3-130">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="268c3-130">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="268c3-131">**Biblioteca:** incluído como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="268c3-131">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="268c3-132">**Versões do .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="268c3-132">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="268c3-133">Consulte também</span><span class="sxs-lookup"><span data-stu-id="268c3-133">See Also</span></span>  
 [<span data-ttu-id="268c3-134">Interface IHostSecurityContext</span><span class="sxs-lookup"><span data-stu-id="268c3-134">IHostSecurityContext Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritycontext-interface.md)  
 [<span data-ttu-id="268c3-135">Interface IHostSecurityManager</span><span class="sxs-lookup"><span data-stu-id="268c3-135">IHostSecurityManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-interface.md)
