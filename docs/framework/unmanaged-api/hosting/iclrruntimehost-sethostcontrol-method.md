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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 46cfaa5870d7bbc7edcbe438ddf57fe5f70ad938
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33434959"
---
# <a name="iclrruntimehostsethostcontrol-method"></a><span data-ttu-id="b7509-102">Método ICLRRuntimeHost::SetHostControl</span><span class="sxs-lookup"><span data-stu-id="b7509-102">ICLRRuntimeHost::SetHostControl Method</span></span>
<span data-ttu-id="b7509-103">Define o ponteiro de interface que o common language runtime (CLR) pode usar para obter a implementação do host de [IHostControl Interface](../../../../docs/framework/unmanaged-api/hosting/ihostcontrol-interface.md).</span><span class="sxs-lookup"><span data-stu-id="b7509-103">Sets the interface pointer that the common language runtime (CLR) can use to get the host's implementation of [IHostControl Interface](../../../../docs/framework/unmanaged-api/hosting/ihostcontrol-interface.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b7509-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="b7509-104">Syntax</span></span>  
  
```  
HRESULT SetHostControl(  
    [in] IHostControl* pHostControl  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="b7509-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="b7509-105">Parameters</span></span>  
 `pHostControl`  
 <span data-ttu-id="b7509-106">[in] Um ponteiro de interface para a implementação do host de [IHostControl Interface](../../../../docs/framework/unmanaged-api/hosting/ihostcontrol-interface.md).</span><span class="sxs-lookup"><span data-stu-id="b7509-106">[in] An interface pointer to the host's implementation of [IHostControl Interface](../../../../docs/framework/unmanaged-api/hosting/ihostcontrol-interface.md).</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="b7509-107">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="b7509-107">Return Value</span></span>  
  
|<span data-ttu-id="b7509-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="b7509-108">HRESULT</span></span>|<span data-ttu-id="b7509-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="b7509-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="b7509-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="b7509-110">S_OK</span></span>|<span data-ttu-id="b7509-111">`SetHostControl` retornou com êxito.</span><span class="sxs-lookup"><span data-stu-id="b7509-111">`SetHostControl` returned successfully.</span></span>|  
|<span data-ttu-id="b7509-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="b7509-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="b7509-113">O CLR não foi carregado em um processo ou o CLR está em um estado em que ele não pode executar código gerenciado ou processar a chamada com êxito.</span><span class="sxs-lookup"><span data-stu-id="b7509-113">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="b7509-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="b7509-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="b7509-115">A chamada foi atingido.</span><span class="sxs-lookup"><span data-stu-id="b7509-115">The call timed out.</span></span>|  
|<span data-ttu-id="b7509-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="b7509-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="b7509-117">O chamador não possui o bloqueio.</span><span class="sxs-lookup"><span data-stu-id="b7509-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="b7509-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="b7509-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="b7509-119">Um evento foi cancelado durante um thread bloqueado ou fibra estava aguardando nele.</span><span class="sxs-lookup"><span data-stu-id="b7509-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="b7509-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="b7509-120">E_FAIL</span></span>|<span data-ttu-id="b7509-121">Ocorreu uma falha catastrófica desconhecida.</span><span class="sxs-lookup"><span data-stu-id="b7509-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="b7509-122">Se um método retornará E_FAIL, o CLR não será mais utilizável dentro do processo.</span><span class="sxs-lookup"><span data-stu-id="b7509-122">If a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="b7509-123">As chamadas subsequentes para hospedagem métodos retornam HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="b7509-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="b7509-124">E_CLR_ALREADY_STARTED</span><span class="sxs-lookup"><span data-stu-id="b7509-124">E_CLR_ALREADY_STARTED</span></span>|<span data-ttu-id="b7509-125">O CLR já foi inicializado.</span><span class="sxs-lookup"><span data-stu-id="b7509-125">The CLR has already been initialized.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b7509-126">Comentários</span><span class="sxs-lookup"><span data-stu-id="b7509-126">Remarks</span></span>  
 <span data-ttu-id="b7509-127">Você deve chamar `SetHostControl` antes que o CLR é inicializado, ou seja, antes de chamar [método Start](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-start-method.md) ou usar qualquer uma da [Interfaces de metadados](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md).</span><span class="sxs-lookup"><span data-stu-id="b7509-127">You must call `SetHostControl` before the CLR is initialized, that is, before you call [Start Method](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-start-method.md) or use any of the [Metadata Interfaces](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md).</span></span> <span data-ttu-id="b7509-128">É recomendável que você chamar `SetHostControl` imediatamente depois de chamar [função CorBindToCurrentRuntime](../../../../docs/framework/unmanaged-api/hosting/corbindtocurrentruntime-function.md) ou [função CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md).</span><span class="sxs-lookup"><span data-stu-id="b7509-128">It is recommended that you call `SetHostControl` immediately after calling [CorBindToCurrentRuntime Function](../../../../docs/framework/unmanaged-api/hosting/corbindtocurrentruntime-function.md) or [CorBindToRuntimeEx Function](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b7509-129">Requisitos</span><span class="sxs-lookup"><span data-stu-id="b7509-129">Requirements</span></span>  
 <span data-ttu-id="b7509-130">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b7509-130">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b7509-131">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="b7509-131">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="b7509-132">**Biblioteca:** incluído como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="b7509-132">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="b7509-133">**Versões do .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b7509-133">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b7509-134">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b7509-134">See Also</span></span>  
 [<span data-ttu-id="b7509-135">Interface ICLRRuntimeHost</span><span class="sxs-lookup"><span data-stu-id="b7509-135">ICLRRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md)  
 [<span data-ttu-id="b7509-136">Interface IHostControl</span><span class="sxs-lookup"><span data-stu-id="b7509-136">IHostControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostcontrol-interface.md)
