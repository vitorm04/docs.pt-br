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
ms.openlocfilehash: 5c772f67b8ac09e2383aff335d9f164c2e048cbd
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61984393"
---
# <a name="ihostcrstenter-method"></a><span data-ttu-id="0eba8-102">Método IHostCrst::Enter</span><span class="sxs-lookup"><span data-stu-id="0eba8-102">IHostCrst::Enter Method</span></span>
<span data-ttu-id="0eba8-103">Entrar na seção crítica que é representada pela atual [IHostCrst](../../../../docs/framework/unmanaged-api/hosting/ihostcrst-interface.md) instância.</span><span class="sxs-lookup"><span data-stu-id="0eba8-103">Enters the critical section that is represented by the current [IHostCrst](../../../../docs/framework/unmanaged-api/hosting/ihostcrst-interface.md) instance.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0eba8-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="0eba8-104">Syntax</span></span>  
  
```  
HRESULT Enter (  
    [in] DWORD option  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0eba8-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="0eba8-105">Parameters</span></span>  
 `option`  
 <span data-ttu-id="0eba8-106">[in] Um dos [WAIT_OPTION](../../../../docs/framework/unmanaged-api/hosting/wait-option-enumeration.md) valores, que indica qual ação o host deve executar se os blocos de operação.</span><span class="sxs-lookup"><span data-stu-id="0eba8-106">[in] One of the [WAIT_OPTION](../../../../docs/framework/unmanaged-api/hosting/wait-option-enumeration.md) values, indicating what action the host should take if the operation blocks.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="0eba8-107">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="0eba8-107">Return Value</span></span>  
  
|<span data-ttu-id="0eba8-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="0eba8-108">HRESULT</span></span>|<span data-ttu-id="0eba8-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="0eba8-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="0eba8-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="0eba8-110">S_OK</span></span>|<span data-ttu-id="0eba8-111">`Enter` retornado com êxito.</span><span class="sxs-lookup"><span data-stu-id="0eba8-111">`Enter` returned successfully.</span></span>|  
|<span data-ttu-id="0eba8-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="0eba8-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="0eba8-113">O common language runtime (CLR) não foi carregado em um processo ou o CLR está em um estado em que ele não pode executar o código gerenciado ou processar a chamada com êxito.</span><span class="sxs-lookup"><span data-stu-id="0eba8-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="0eba8-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="0eba8-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="0eba8-115">A chamada atingiu o tempo limite.</span><span class="sxs-lookup"><span data-stu-id="0eba8-115">The call timed out.</span></span>|  
|<span data-ttu-id="0eba8-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="0eba8-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="0eba8-117">O chamador não é proprietário do bloqueio.</span><span class="sxs-lookup"><span data-stu-id="0eba8-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="0eba8-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="0eba8-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="0eba8-119">Um evento foi cancelado enquanto um thread bloqueado ou fibra estava esperando por ele.</span><span class="sxs-lookup"><span data-stu-id="0eba8-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="0eba8-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="0eba8-120">E_FAIL</span></span>|<span data-ttu-id="0eba8-121">Ocorreu uma falha catastrófica desconhecida.</span><span class="sxs-lookup"><span data-stu-id="0eba8-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="0eba8-122">Quando um método retornar E_FAIL, o CLR não é mais utilizável dentro do processo.</span><span class="sxs-lookup"><span data-stu-id="0eba8-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="0eba8-123">As chamadas subsequentes à hospedagem de métodos de retorno HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="0eba8-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0eba8-124">Comentários</span><span class="sxs-lookup"><span data-stu-id="0eba8-124">Remarks</span></span>  
 <span data-ttu-id="0eba8-125">`Enter` espelha o Win32 `EnterCriticalSection` função.</span><span class="sxs-lookup"><span data-stu-id="0eba8-125">`Enter` mirrors the Win32 `EnterCriticalSection` function.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="0eba8-126">Esse método não retorna até que a seção crítica é inserida.</span><span class="sxs-lookup"><span data-stu-id="0eba8-126">This method does not return until the critical section is entered.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0eba8-127">Requisitos</span><span class="sxs-lookup"><span data-stu-id="0eba8-127">Requirements</span></span>  
 <span data-ttu-id="0eba8-128">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0eba8-128">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0eba8-129">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="0eba8-129">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="0eba8-130">**Biblioteca:** Incluído como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="0eba8-130">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="0eba8-131">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0eba8-131">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0eba8-132">Consulte também</span><span class="sxs-lookup"><span data-stu-id="0eba8-132">See also</span></span>

- [<span data-ttu-id="0eba8-133">Interface ICLRSyncManager</span><span class="sxs-lookup"><span data-stu-id="0eba8-133">ICLRSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)
- [<span data-ttu-id="0eba8-134">Interface IHostCrst</span><span class="sxs-lookup"><span data-stu-id="0eba8-134">IHostCrst Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostcrst-interface.md)
- [<span data-ttu-id="0eba8-135">Interface IHostSyncManager</span><span class="sxs-lookup"><span data-stu-id="0eba8-135">IHostSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)
