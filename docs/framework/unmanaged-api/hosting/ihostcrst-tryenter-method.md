---
title: Método IHostCrst::TryEnter
ms.date: 03/30/2017
api_name:
- IHostCrst.TryEnter
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostCrst::TryEnter
helpviewer_keywords:
- IHostCrst::TryEnter method [.NET Framework hosting]
- TryEnter method [.NET Framework hosting]
ms.assetid: a922fa98-beab-4f09-a342-cc94fc65687f
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d0b4074d9dab8ad46468930373ad44b0c72bd690
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67763745"
---
# <a name="ihostcrsttryenter-method"></a><span data-ttu-id="38e2e-102">Método IHostCrst::TryEnter</span><span class="sxs-lookup"><span data-stu-id="38e2e-102">IHostCrst::TryEnter Method</span></span>
<span data-ttu-id="38e2e-103">Tentativas de entrar na seção crítica representada pelo atual [IHostCrst](../../../../docs/framework/unmanaged-api/hosting/ihostcrst-interface.md) instância.</span><span class="sxs-lookup"><span data-stu-id="38e2e-103">Attempts to enter the critical section represented by the current [IHostCrst](../../../../docs/framework/unmanaged-api/hosting/ihostcrst-interface.md) instance.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="38e2e-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="38e2e-104">Syntax</span></span>  
  
```cpp  
HRESULT TryEnter (  
    [in]  DWORD  option,  
    [out] BOOL   *pbSucceeded  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="38e2e-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="38e2e-105">Parameters</span></span>  
 `option`  
 <span data-ttu-id="38e2e-106">[in] Um dos [WAIT_OPTION](../../../../docs/framework/unmanaged-api/hosting/wait-option-enumeration.md) valores, que indica qual ação o host deve executar se os blocos de operação.</span><span class="sxs-lookup"><span data-stu-id="38e2e-106">[in] One of the [WAIT_OPTION](../../../../docs/framework/unmanaged-api/hosting/wait-option-enumeration.md) values, indicating what action the host should take if the operation blocks.</span></span>  
  
 `pbSucceeded`  
 <span data-ttu-id="38e2e-107">[out] `true` se a seção crítica pode ser inseridas; caso contrário, `false`.</span><span class="sxs-lookup"><span data-stu-id="38e2e-107">[out] `true` if the critical section can be entered; otherwise, `false`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="38e2e-108">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="38e2e-108">Return Value</span></span>  
  
|<span data-ttu-id="38e2e-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="38e2e-109">HRESULT</span></span>|<span data-ttu-id="38e2e-110">Descrição</span><span class="sxs-lookup"><span data-stu-id="38e2e-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="38e2e-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="38e2e-111">S_OK</span></span>|<span data-ttu-id="38e2e-112">`TryEnter` retornado com êxito.</span><span class="sxs-lookup"><span data-stu-id="38e2e-112">`TryEnter` returned successfully.</span></span>|  
|<span data-ttu-id="38e2e-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="38e2e-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="38e2e-114">O common language runtime (CLR) não foi carregado em um processo ou o CLR está em um estado em que ele não pode executar o código gerenciado ou processar a chamada com êxito.</span><span class="sxs-lookup"><span data-stu-id="38e2e-114">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="38e2e-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="38e2e-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="38e2e-116">A chamada atingiu o tempo limite.</span><span class="sxs-lookup"><span data-stu-id="38e2e-116">The call timed out.</span></span>|  
|<span data-ttu-id="38e2e-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="38e2e-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="38e2e-118">O chamador não é proprietário do bloqueio.</span><span class="sxs-lookup"><span data-stu-id="38e2e-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="38e2e-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="38e2e-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="38e2e-120">Um evento foi cancelado enquanto um thread bloqueado ou fibra estava esperando por ele.</span><span class="sxs-lookup"><span data-stu-id="38e2e-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="38e2e-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="38e2e-121">E_FAIL</span></span>|<span data-ttu-id="38e2e-122">Ocorreu uma falha catastrófica desconhecida.</span><span class="sxs-lookup"><span data-stu-id="38e2e-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="38e2e-123">Quando um método retornar E_FAIL, o CLR não é mais utilizável dentro do processo.</span><span class="sxs-lookup"><span data-stu-id="38e2e-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="38e2e-124">As chamadas subsequentes à hospedagem de métodos de retorno HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="38e2e-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="38e2e-125">Comentários</span><span class="sxs-lookup"><span data-stu-id="38e2e-125">Remarks</span></span>  
 <span data-ttu-id="38e2e-126">`TryEnter` retorna imediatamente e indica se o thread de chamada inserida na seção crítica.</span><span class="sxs-lookup"><span data-stu-id="38e2e-126">`TryEnter` returns immediately and indicates whether the calling thread entered the critical section.</span></span> <span data-ttu-id="38e2e-127">Esse método espelha o Wind32 `TryEnterCriticalSection` função.</span><span class="sxs-lookup"><span data-stu-id="38e2e-127">This method mirrors the Wind32 `TryEnterCriticalSection` function.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="38e2e-128">Requisitos</span><span class="sxs-lookup"><span data-stu-id="38e2e-128">Requirements</span></span>  
 <span data-ttu-id="38e2e-129">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="38e2e-129">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="38e2e-130">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="38e2e-130">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="38e2e-131">**Biblioteca:** Incluído como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="38e2e-131">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="38e2e-132">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="38e2e-132">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="38e2e-133">Consulte também</span><span class="sxs-lookup"><span data-stu-id="38e2e-133">See also</span></span>

- [<span data-ttu-id="38e2e-134">Interface ICLRSyncManager</span><span class="sxs-lookup"><span data-stu-id="38e2e-134">ICLRSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)
- [<span data-ttu-id="38e2e-135">Interface IHostCrst</span><span class="sxs-lookup"><span data-stu-id="38e2e-135">IHostCrst Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostcrst-interface.md)
- [<span data-ttu-id="38e2e-136">Interface IHostSyncManager</span><span class="sxs-lookup"><span data-stu-id="38e2e-136">IHostSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)
