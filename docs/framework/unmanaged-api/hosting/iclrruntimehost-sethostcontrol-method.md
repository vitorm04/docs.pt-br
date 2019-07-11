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
ms.openlocfilehash: 1cf6255bfd23b38be63cd609798643f9fa1e1f93
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67765775"
---
# <a name="iclrruntimehostsethostcontrol-method"></a><span data-ttu-id="f50bf-102">Método ICLRRuntimeHost::SetHostControl</span><span class="sxs-lookup"><span data-stu-id="f50bf-102">ICLRRuntimeHost::SetHostControl Method</span></span>
<span data-ttu-id="f50bf-103">Define o ponteiro de interface que o common language runtime (CLR) pode usar para obter a implementação do host do [IHostControl Interface](../../../../docs/framework/unmanaged-api/hosting/ihostcontrol-interface.md).</span><span class="sxs-lookup"><span data-stu-id="f50bf-103">Sets the interface pointer that the common language runtime (CLR) can use to get the host's implementation of [IHostControl Interface](../../../../docs/framework/unmanaged-api/hosting/ihostcontrol-interface.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f50bf-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="f50bf-104">Syntax</span></span>  
  
```cpp  
HRESULT SetHostControl(  
    [in] IHostControl* pHostControl  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f50bf-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="f50bf-105">Parameters</span></span>  
 `pHostControl`  
 <span data-ttu-id="f50bf-106">[in] Um ponteiro de interface para a implementação do host de [IHostControl Interface](../../../../docs/framework/unmanaged-api/hosting/ihostcontrol-interface.md).</span><span class="sxs-lookup"><span data-stu-id="f50bf-106">[in] An interface pointer to the host's implementation of [IHostControl Interface](../../../../docs/framework/unmanaged-api/hosting/ihostcontrol-interface.md).</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="f50bf-107">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="f50bf-107">Return Value</span></span>  
  
|<span data-ttu-id="f50bf-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="f50bf-108">HRESULT</span></span>|<span data-ttu-id="f50bf-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="f50bf-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="f50bf-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="f50bf-110">S_OK</span></span>|<span data-ttu-id="f50bf-111">`SetHostControl` retornado com êxito.</span><span class="sxs-lookup"><span data-stu-id="f50bf-111">`SetHostControl` returned successfully.</span></span>|  
|<span data-ttu-id="f50bf-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="f50bf-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="f50bf-113">O CLR não tenha sido carregado em um processo ou o CLR está em um estado em que ele não pode executar o código gerenciado ou processar a chamada com êxito.</span><span class="sxs-lookup"><span data-stu-id="f50bf-113">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="f50bf-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="f50bf-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="f50bf-115">A chamada atingiu o tempo limite.</span><span class="sxs-lookup"><span data-stu-id="f50bf-115">The call timed out.</span></span>|  
|<span data-ttu-id="f50bf-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="f50bf-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="f50bf-117">O chamador não é proprietário do bloqueio.</span><span class="sxs-lookup"><span data-stu-id="f50bf-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="f50bf-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="f50bf-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="f50bf-119">Um evento foi cancelado enquanto um thread bloqueado ou fibra estava esperando por ele.</span><span class="sxs-lookup"><span data-stu-id="f50bf-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="f50bf-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="f50bf-120">E_FAIL</span></span>|<span data-ttu-id="f50bf-121">Ocorreu uma falha catastrófica desconhecida.</span><span class="sxs-lookup"><span data-stu-id="f50bf-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="f50bf-122">Se um método retornar E_FAIL, o CLR não é mais utilizável dentro do processo.</span><span class="sxs-lookup"><span data-stu-id="f50bf-122">If a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="f50bf-123">As chamadas subsequentes à hospedagem de métodos de retorno HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="f50bf-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="f50bf-124">E_CLR_ALREADY_STARTED</span><span class="sxs-lookup"><span data-stu-id="f50bf-124">E_CLR_ALREADY_STARTED</span></span>|<span data-ttu-id="f50bf-125">O CLR já foi inicializado.</span><span class="sxs-lookup"><span data-stu-id="f50bf-125">The CLR has already been initialized.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f50bf-126">Comentários</span><span class="sxs-lookup"><span data-stu-id="f50bf-126">Remarks</span></span>  
 <span data-ttu-id="f50bf-127">Você deve chamar `SetHostControl` antes do CLR é inicializado, ou seja, antes de chamar [método Start](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-start-method.md) ou usar qualquer um dos [Interfaces de metadados](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md).</span><span class="sxs-lookup"><span data-stu-id="f50bf-127">You must call `SetHostControl` before the CLR is initialized, that is, before you call [Start Method](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-start-method.md) or use any of the [Metadata Interfaces](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md).</span></span> <span data-ttu-id="f50bf-128">É recomendável que você chame `SetHostControl` imediatamente depois de chamar [função CorBindToCurrentRuntime](../../../../docs/framework/unmanaged-api/hosting/corbindtocurrentruntime-function.md) ou [função CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md).</span><span class="sxs-lookup"><span data-stu-id="f50bf-128">It is recommended that you call `SetHostControl` immediately after calling [CorBindToCurrentRuntime Function](../../../../docs/framework/unmanaged-api/hosting/corbindtocurrentruntime-function.md) or [CorBindToRuntimeEx Function](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f50bf-129">Requisitos</span><span class="sxs-lookup"><span data-stu-id="f50bf-129">Requirements</span></span>  
 <span data-ttu-id="f50bf-130">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f50bf-130">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f50bf-131">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="f50bf-131">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="f50bf-132">**Biblioteca:** Incluído como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="f50bf-132">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="f50bf-133">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f50bf-133">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f50bf-134">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f50bf-134">See also</span></span>

- [<span data-ttu-id="f50bf-135">Interface ICLRRuntimeHost</span><span class="sxs-lookup"><span data-stu-id="f50bf-135">ICLRRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md)
- [<span data-ttu-id="f50bf-136">Interface IHostControl</span><span class="sxs-lookup"><span data-stu-id="f50bf-136">IHostControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostcontrol-interface.md)
