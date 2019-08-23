---
title: Método IHostCrst::Enter
ms.date: 03/30/2017
api_name:
- IHostCrst.Enter
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostCrst::Enter
helpviewer_keywords:
- Enter method [.NET Framework hosting]
- IHostCrst::Enter method [.NET Framework hosting]
ms.assetid: 100dd7eb-7053-4295-9bb3-32ba47f6ec79
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: bdc597e741023af1c7cc1f48e378083157dd4a5d
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69937746"
---
# <a name="ihostcrstenter-method"></a><span data-ttu-id="1b50a-102">Método IHostCrst::Enter</span><span class="sxs-lookup"><span data-stu-id="1b50a-102">IHostCrst::Enter Method</span></span>
<span data-ttu-id="1b50a-103">Insere a seção crítica que é representada pela instância de [IHostCrst](../../../../docs/framework/unmanaged-api/hosting/ihostcrst-interface.md) atual.</span><span class="sxs-lookup"><span data-stu-id="1b50a-103">Enters the critical section that is represented by the current [IHostCrst](../../../../docs/framework/unmanaged-api/hosting/ihostcrst-interface.md) instance.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1b50a-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="1b50a-104">Syntax</span></span>  
  
```cpp  
HRESULT Enter (  
    [in] DWORD option  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1b50a-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="1b50a-105">Parameters</span></span>  
 `option`  
 <span data-ttu-id="1b50a-106">no Um dos valores de [WAIT_OPTION](../../../../docs/framework/unmanaged-api/hosting/wait-option-enumeration.md) , que indica a ação que o host deve executar se a operação for bloqueada.</span><span class="sxs-lookup"><span data-stu-id="1b50a-106">[in] One of the [WAIT_OPTION](../../../../docs/framework/unmanaged-api/hosting/wait-option-enumeration.md) values, indicating what action the host should take if the operation blocks.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="1b50a-107">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="1b50a-107">Return Value</span></span>  
  
|<span data-ttu-id="1b50a-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="1b50a-108">HRESULT</span></span>|<span data-ttu-id="1b50a-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="1b50a-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="1b50a-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="1b50a-110">S_OK</span></span>|<span data-ttu-id="1b50a-111">`Enter`retornado com êxito.</span><span class="sxs-lookup"><span data-stu-id="1b50a-111">`Enter` returned successfully.</span></span>|  
|<span data-ttu-id="1b50a-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="1b50a-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="1b50a-113">O Common Language Runtime (CLR) não foi carregado em um processo ou o CLR está em um estado no qual não pode executar código gerenciado ou processar a chamada com êxito.</span><span class="sxs-lookup"><span data-stu-id="1b50a-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="1b50a-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="1b50a-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="1b50a-115">A chamada atingiu o tempo limite.</span><span class="sxs-lookup"><span data-stu-id="1b50a-115">The call timed out.</span></span>|  
|<span data-ttu-id="1b50a-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="1b50a-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="1b50a-117">O chamador não possui o bloqueio.</span><span class="sxs-lookup"><span data-stu-id="1b50a-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="1b50a-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="1b50a-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="1b50a-119">Um evento foi cancelado enquanto um thread ou uma fibra bloqueada estava esperando.</span><span class="sxs-lookup"><span data-stu-id="1b50a-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="1b50a-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="1b50a-120">E_FAIL</span></span>|<span data-ttu-id="1b50a-121">Ocorreu uma falha catastrófica desconhecida.</span><span class="sxs-lookup"><span data-stu-id="1b50a-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="1b50a-122">Quando um método retorna E_FAIL, o CLR não é mais utilizável no processo.</span><span class="sxs-lookup"><span data-stu-id="1b50a-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="1b50a-123">As chamadas subsequentes para métodos de hospedagem retornam HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="1b50a-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1b50a-124">Comentários</span><span class="sxs-lookup"><span data-stu-id="1b50a-124">Remarks</span></span>  
 <span data-ttu-id="1b50a-125">`Enter`espelha a função `EnterCriticalSection` do Win32.</span><span class="sxs-lookup"><span data-stu-id="1b50a-125">`Enter` mirrors the Win32 `EnterCriticalSection` function.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="1b50a-126">Esse método não retorna até que a seção crítica seja inserida.</span><span class="sxs-lookup"><span data-stu-id="1b50a-126">This method does not return until the critical section is entered.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1b50a-127">Requisitos</span><span class="sxs-lookup"><span data-stu-id="1b50a-127">Requirements</span></span>  
 <span data-ttu-id="1b50a-128">**Compatíveis** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1b50a-128">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1b50a-129">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="1b50a-129">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="1b50a-130">**Biblioteca** Incluído como um recurso em MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="1b50a-130">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="1b50a-131">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1b50a-131">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1b50a-132">Consulte também</span><span class="sxs-lookup"><span data-stu-id="1b50a-132">See also</span></span>

- [<span data-ttu-id="1b50a-133">Interface ICLRSyncManager</span><span class="sxs-lookup"><span data-stu-id="1b50a-133">ICLRSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)
- [<span data-ttu-id="1b50a-134">Interface IHostCrst</span><span class="sxs-lookup"><span data-stu-id="1b50a-134">IHostCrst Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostcrst-interface.md)
- [<span data-ttu-id="1b50a-135">Interface IHostSyncManager</span><span class="sxs-lookup"><span data-stu-id="1b50a-135">IHostSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)
