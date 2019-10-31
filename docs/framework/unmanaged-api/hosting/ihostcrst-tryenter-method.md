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
ms.openlocfilehash: f4b40a595bbdea4dd390a42af6a0d4b1a5efa2f2
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73130500"
---
# <a name="ihostcrsttryenter-method"></a><span data-ttu-id="0f851-102">Método IHostCrst::TryEnter</span><span class="sxs-lookup"><span data-stu-id="0f851-102">IHostCrst::TryEnter Method</span></span>
<span data-ttu-id="0f851-103">Tenta inserir a seção crítica representada pela instância de [IHostCrst](../../../../docs/framework/unmanaged-api/hosting/ihostcrst-interface.md) atual.</span><span class="sxs-lookup"><span data-stu-id="0f851-103">Attempts to enter the critical section represented by the current [IHostCrst](../../../../docs/framework/unmanaged-api/hosting/ihostcrst-interface.md) instance.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0f851-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="0f851-104">Syntax</span></span>  
  
```cpp  
HRESULT TryEnter (  
    [in]  DWORD  option,  
    [out] BOOL   *pbSucceeded  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0f851-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="0f851-105">Parameters</span></span>  
 `option`  
 <span data-ttu-id="0f851-106">no Um dos valores de [WAIT_OPTION](../../../../docs/framework/unmanaged-api/hosting/wait-option-enumeration.md) , que indica a ação que o host deve executar se a operação for bloqueada.</span><span class="sxs-lookup"><span data-stu-id="0f851-106">[in] One of the [WAIT_OPTION](../../../../docs/framework/unmanaged-api/hosting/wait-option-enumeration.md) values, indicating what action the host should take if the operation blocks.</span></span>  
  
 `pbSucceeded`  
 <span data-ttu-id="0f851-107">[fora] `true` se a seção crítica puder ser inserida; caso contrário, `false`.</span><span class="sxs-lookup"><span data-stu-id="0f851-107">[out] `true` if the critical section can be entered; otherwise, `false`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="0f851-108">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="0f851-108">Return Value</span></span>  
  
|<span data-ttu-id="0f851-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="0f851-109">HRESULT</span></span>|<span data-ttu-id="0f851-110">Descrição</span><span class="sxs-lookup"><span data-stu-id="0f851-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="0f851-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="0f851-111">S_OK</span></span>|<span data-ttu-id="0f851-112">`TryEnter` retornado com êxito.</span><span class="sxs-lookup"><span data-stu-id="0f851-112">`TryEnter` returned successfully.</span></span>|  
|<span data-ttu-id="0f851-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="0f851-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="0f851-114">O Common Language Runtime (CLR) não foi carregado em um processo ou o CLR está em um estado no qual não pode executar código gerenciado ou processar a chamada com êxito.</span><span class="sxs-lookup"><span data-stu-id="0f851-114">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="0f851-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="0f851-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="0f851-116">A chamada atingiu o tempo limite.</span><span class="sxs-lookup"><span data-stu-id="0f851-116">The call timed out.</span></span>|  
|<span data-ttu-id="0f851-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="0f851-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="0f851-118">O chamador não possui o bloqueio.</span><span class="sxs-lookup"><span data-stu-id="0f851-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="0f851-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="0f851-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="0f851-120">Um evento foi cancelado enquanto um thread ou uma fibra bloqueada estava esperando.</span><span class="sxs-lookup"><span data-stu-id="0f851-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="0f851-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="0f851-121">E_FAIL</span></span>|<span data-ttu-id="0f851-122">Ocorreu uma falha catastrófica desconhecida.</span><span class="sxs-lookup"><span data-stu-id="0f851-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="0f851-123">Quando um método retorna E_FAIL, o CLR não é mais utilizável no processo.</span><span class="sxs-lookup"><span data-stu-id="0f851-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="0f851-124">As chamadas subsequentes para métodos de hospedagem retornam HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="0f851-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0f851-125">Comentários</span><span class="sxs-lookup"><span data-stu-id="0f851-125">Remarks</span></span>  
 <span data-ttu-id="0f851-126">`TryEnter` retorna imediatamente e indica se o thread de chamada entrou na seção crítica.</span><span class="sxs-lookup"><span data-stu-id="0f851-126">`TryEnter` returns immediately and indicates whether the calling thread entered the critical section.</span></span> <span data-ttu-id="0f851-127">Esse método espelha a função de `TryEnterCriticalSection` Wind32.</span><span class="sxs-lookup"><span data-stu-id="0f851-127">This method mirrors the Wind32 `TryEnterCriticalSection` function.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0f851-128">Requisitos</span><span class="sxs-lookup"><span data-stu-id="0f851-128">Requirements</span></span>  
 <span data-ttu-id="0f851-129">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0f851-129">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0f851-130">**Cabeçalho:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="0f851-130">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="0f851-131">**Biblioteca:** Incluído como um recurso em MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="0f851-131">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="0f851-132">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0f851-132">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0f851-133">Consulte também</span><span class="sxs-lookup"><span data-stu-id="0f851-133">See also</span></span>

- [<span data-ttu-id="0f851-134">Interface ICLRSyncManager</span><span class="sxs-lookup"><span data-stu-id="0f851-134">ICLRSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)
- [<span data-ttu-id="0f851-135">Interface IHostCrst</span><span class="sxs-lookup"><span data-stu-id="0f851-135">IHostCrst Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostcrst-interface.md)
- [<span data-ttu-id="0f851-136">Interface IHostSyncManager</span><span class="sxs-lookup"><span data-stu-id="0f851-136">IHostSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)
