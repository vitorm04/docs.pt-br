---
title: Método ICLRRuntimeHost::SetHostControl
ms.date: 03/30/2017
api_name:
- ICLRRuntimeHost.SetHostControl
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRRuntimeHost::SetHostControl
helpviewer_keywords:
- SetHostControl method [.NET Framework hosting]
- ICLRRuntimeHost::SetHostControl method [.NET Framework hosting]
ms.assetid: 6136be87-e631-4756-81ed-74b66581bad4
topic_type:
- apiref
ms.openlocfilehash: 68b06a2840de277bdaed1dc9ce0b51e6b363c897
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73120458"
---
# <a name="iclrruntimehostsethostcontrol-method"></a><span data-ttu-id="0ea91-102">Método ICLRRuntimeHost::SetHostControl</span><span class="sxs-lookup"><span data-stu-id="0ea91-102">ICLRRuntimeHost::SetHostControl Method</span></span>
<span data-ttu-id="0ea91-103">Define o ponteiro de interface que o Common Language Runtime (CLR) pode usar para obter a implementação do host da [interface IHostControl](../../../../docs/framework/unmanaged-api/hosting/ihostcontrol-interface.md).</span><span class="sxs-lookup"><span data-stu-id="0ea91-103">Sets the interface pointer that the common language runtime (CLR) can use to get the host's implementation of [IHostControl Interface](../../../../docs/framework/unmanaged-api/hosting/ihostcontrol-interface.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0ea91-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="0ea91-104">Syntax</span></span>  
  
```cpp  
HRESULT SetHostControl(  
    [in] IHostControl* pHostControl  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0ea91-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="0ea91-105">Parameters</span></span>  
 `pHostControl`  
 <span data-ttu-id="0ea91-106">no Um ponteiro de interface para a implementação do host da [interface IHostControl](../../../../docs/framework/unmanaged-api/hosting/ihostcontrol-interface.md).</span><span class="sxs-lookup"><span data-stu-id="0ea91-106">[in] An interface pointer to the host's implementation of [IHostControl Interface](../../../../docs/framework/unmanaged-api/hosting/ihostcontrol-interface.md).</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="0ea91-107">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="0ea91-107">Return Value</span></span>  
  
|<span data-ttu-id="0ea91-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="0ea91-108">HRESULT</span></span>|<span data-ttu-id="0ea91-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="0ea91-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="0ea91-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="0ea91-110">S_OK</span></span>|<span data-ttu-id="0ea91-111">`SetHostControl` retornado com êxito.</span><span class="sxs-lookup"><span data-stu-id="0ea91-111">`SetHostControl` returned successfully.</span></span>|  
|<span data-ttu-id="0ea91-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="0ea91-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="0ea91-113">O CLR não foi carregado em um processo ou o CLR está em um estado no qual não pode executar código gerenciado ou processar a chamada com êxito.</span><span class="sxs-lookup"><span data-stu-id="0ea91-113">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="0ea91-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="0ea91-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="0ea91-115">A chamada atingiu o tempo limite.</span><span class="sxs-lookup"><span data-stu-id="0ea91-115">The call timed out.</span></span>|  
|<span data-ttu-id="0ea91-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="0ea91-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="0ea91-117">O chamador não possui o bloqueio.</span><span class="sxs-lookup"><span data-stu-id="0ea91-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="0ea91-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="0ea91-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="0ea91-119">Um evento foi cancelado enquanto um thread ou uma fibra bloqueada estava esperando.</span><span class="sxs-lookup"><span data-stu-id="0ea91-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="0ea91-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="0ea91-120">E_FAIL</span></span>|<span data-ttu-id="0ea91-121">Ocorreu uma falha catastrófica desconhecida.</span><span class="sxs-lookup"><span data-stu-id="0ea91-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="0ea91-122">Se um método retornar E_FAIL, o CLR não poderá mais ser usado no processo.</span><span class="sxs-lookup"><span data-stu-id="0ea91-122">If a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="0ea91-123">As chamadas subsequentes para métodos de hospedagem retornam HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="0ea91-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="0ea91-124">E_CLR_ALREADY_STARTED</span><span class="sxs-lookup"><span data-stu-id="0ea91-124">E_CLR_ALREADY_STARTED</span></span>|<span data-ttu-id="0ea91-125">O CLR já foi inicializado.</span><span class="sxs-lookup"><span data-stu-id="0ea91-125">The CLR has already been initialized.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0ea91-126">Comentários</span><span class="sxs-lookup"><span data-stu-id="0ea91-126">Remarks</span></span>  
 <span data-ttu-id="0ea91-127">Você deve chamar `SetHostControl` antes que o CLR seja inicializado, ou seja, antes de chamar o [método Start](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-start-method.md) ou usar qualquer uma das [interfaces de metadados](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md).</span><span class="sxs-lookup"><span data-stu-id="0ea91-127">You must call `SetHostControl` before the CLR is initialized, that is, before you call [Start Method](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-start-method.md) or use any of the [Metadata Interfaces](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md).</span></span> <span data-ttu-id="0ea91-128">É recomendável chamar `SetHostControl` imediatamente após chamar a [função CorBindToCurrentRuntime](../../../../docs/framework/unmanaged-api/hosting/corbindtocurrentruntime-function.md) ou a [função CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md).</span><span class="sxs-lookup"><span data-stu-id="0ea91-128">It is recommended that you call `SetHostControl` immediately after calling [CorBindToCurrentRuntime Function](../../../../docs/framework/unmanaged-api/hosting/corbindtocurrentruntime-function.md) or [CorBindToRuntimeEx Function](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0ea91-129">Requisitos</span><span class="sxs-lookup"><span data-stu-id="0ea91-129">Requirements</span></span>  
 <span data-ttu-id="0ea91-130">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0ea91-130">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0ea91-131">**Cabeçalho:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="0ea91-131">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="0ea91-132">**Biblioteca:** Incluído como um recurso em MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="0ea91-132">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="0ea91-133">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0ea91-133">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0ea91-134">Consulte também</span><span class="sxs-lookup"><span data-stu-id="0ea91-134">See also</span></span>

- [<span data-ttu-id="0ea91-135">Interface ICLRRuntimeHost</span><span class="sxs-lookup"><span data-stu-id="0ea91-135">ICLRRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md)
- [<span data-ttu-id="0ea91-136">Interface IHostControl</span><span class="sxs-lookup"><span data-stu-id="0ea91-136">IHostControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostcontrol-interface.md)
