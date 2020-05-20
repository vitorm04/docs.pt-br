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
ms.openlocfilehash: 8d6a4e1ca934c748352b0c4f5120536a4dd24e0b
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/20/2020
ms.locfileid: "83703962"
---
# <a name="iclrruntimehostsethostcontrol-method"></a><span data-ttu-id="ed211-102">Método ICLRRuntimeHost::SetHostControl</span><span class="sxs-lookup"><span data-stu-id="ed211-102">ICLRRuntimeHost::SetHostControl Method</span></span>
<span data-ttu-id="ed211-103">Define o ponteiro de interface que o Common Language Runtime (CLR) pode usar para obter a implementação do host da [interface IHostControl](ihostcontrol-interface.md).</span><span class="sxs-lookup"><span data-stu-id="ed211-103">Sets the interface pointer that the common language runtime (CLR) can use to get the host's implementation of [IHostControl Interface](ihostcontrol-interface.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ed211-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="ed211-104">Syntax</span></span>  
  
```cpp  
HRESULT SetHostControl(  
    [in] IHostControl* pHostControl  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ed211-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="ed211-105">Parameters</span></span>  
 `pHostControl`  
 <span data-ttu-id="ed211-106">no Um ponteiro de interface para a implementação do host da [interface IHostControl](ihostcontrol-interface.md).</span><span class="sxs-lookup"><span data-stu-id="ed211-106">[in] An interface pointer to the host's implementation of [IHostControl Interface](ihostcontrol-interface.md).</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="ed211-107">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="ed211-107">Return Value</span></span>  
  
|<span data-ttu-id="ed211-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="ed211-108">HRESULT</span></span>|<span data-ttu-id="ed211-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="ed211-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="ed211-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="ed211-110">S_OK</span></span>|<span data-ttu-id="ed211-111">`SetHostControl`retornado com êxito.</span><span class="sxs-lookup"><span data-stu-id="ed211-111">`SetHostControl` returned successfully.</span></span>|  
|<span data-ttu-id="ed211-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="ed211-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="ed211-113">O CLR não foi carregado em um processo ou o CLR está em um estado no qual não pode executar código gerenciado ou processar a chamada com êxito.</span><span class="sxs-lookup"><span data-stu-id="ed211-113">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="ed211-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="ed211-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="ed211-115">A chamada atingiu o tempo limite.</span><span class="sxs-lookup"><span data-stu-id="ed211-115">The call timed out.</span></span>|  
|<span data-ttu-id="ed211-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="ed211-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="ed211-117">O chamador não possui o bloqueio.</span><span class="sxs-lookup"><span data-stu-id="ed211-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="ed211-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="ed211-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="ed211-119">Um evento foi cancelado enquanto um thread ou uma fibra bloqueada estava esperando.</span><span class="sxs-lookup"><span data-stu-id="ed211-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="ed211-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="ed211-120">E_FAIL</span></span>|<span data-ttu-id="ed211-121">Ocorreu uma falha catastrófica desconhecida.</span><span class="sxs-lookup"><span data-stu-id="ed211-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="ed211-122">Se um método retornar E_FAIL, o CLR não poderá mais ser usado no processo.</span><span class="sxs-lookup"><span data-stu-id="ed211-122">If a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="ed211-123">As chamadas subsequentes para métodos de hospedagem retornam HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="ed211-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="ed211-124">E_CLR_ALREADY_STARTED</span><span class="sxs-lookup"><span data-stu-id="ed211-124">E_CLR_ALREADY_STARTED</span></span>|<span data-ttu-id="ed211-125">O CLR já foi inicializado.</span><span class="sxs-lookup"><span data-stu-id="ed211-125">The CLR has already been initialized.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ed211-126">Comentários</span><span class="sxs-lookup"><span data-stu-id="ed211-126">Remarks</span></span>  
 <span data-ttu-id="ed211-127">Você deve chamar `SetHostControl` antes que o CLR seja inicializado, ou seja, antes de chamar o [método Start](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-start-method.md) ou usar qualquer uma das [interfaces de metadados](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md).</span><span class="sxs-lookup"><span data-stu-id="ed211-127">You must call `SetHostControl` before the CLR is initialized, that is, before you call [Start Method](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-start-method.md) or use any of the [Metadata Interfaces](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md).</span></span> <span data-ttu-id="ed211-128">É recomendável que você chame `SetHostControl` imediatamente depois de chamar a [função CorBindToCurrentRuntime](../../../../docs/framework/unmanaged-api/hosting/corbindtocurrentruntime-function.md) ou a [função CorBindToRuntimeEx](corbindtoruntimeex-function.md).</span><span class="sxs-lookup"><span data-stu-id="ed211-128">It is recommended that you call `SetHostControl` immediately after calling [CorBindToCurrentRuntime Function](../../../../docs/framework/unmanaged-api/hosting/corbindtocurrentruntime-function.md) or [CorBindToRuntimeEx Function](corbindtoruntimeex-function.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ed211-129">Requisitos</span><span class="sxs-lookup"><span data-stu-id="ed211-129">Requirements</span></span>  
 <span data-ttu-id="ed211-130">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ed211-130">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ed211-131">**Cabeçalho:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="ed211-131">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="ed211-132">**Biblioteca:** Incluído como um recurso em MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="ed211-132">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="ed211-133">**.NET Framework versões:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ed211-133">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ed211-134">Veja também</span><span class="sxs-lookup"><span data-stu-id="ed211-134">See also</span></span>

- [<span data-ttu-id="ed211-135">Interface ICLRRuntimeHost</span><span class="sxs-lookup"><span data-stu-id="ed211-135">ICLRRuntimeHost Interface</span></span>](iclrruntimehost-interface.md)
- [<span data-ttu-id="ed211-136">Interface IHostControl</span><span class="sxs-lookup"><span data-stu-id="ed211-136">IHostControl Interface</span></span>](ihostcontrol-interface.md)
