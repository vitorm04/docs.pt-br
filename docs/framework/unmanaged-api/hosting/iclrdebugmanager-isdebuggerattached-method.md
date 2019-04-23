---
title: Método ICLRDebugManager::IsDebuggerAttached
ms.date: 03/30/2017
api_name:
- ICLRDebugManager.IsDebuggerAttached
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRDebugManager::IsDebuggerAttached
helpviewer_keywords:
- IsDebuggerAttached method, ICLRDebugManager interface [.NET Framework hosting]
- ICLRDebugManager::IsDebuggerAttached method [.NET Framework hosting]
ms.assetid: 2f105fe0-f52d-49c5-bda5-583fb27e3aa6
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1d6c071b3ac68cb38fc85aff65fff49a71ea4275
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59095381"
---
# <a name="iclrdebugmanagerisdebuggerattached-method"></a><span data-ttu-id="f394a-102">Método ICLRDebugManager::IsDebuggerAttached</span><span class="sxs-lookup"><span data-stu-id="f394a-102">ICLRDebugManager::IsDebuggerAttached Method</span></span>
<span data-ttu-id="f394a-103">Obtém um valor que indica se um depurador está anexado ao processo.</span><span class="sxs-lookup"><span data-stu-id="f394a-103">Gets a value that indicates whether a debugger is attached to the process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f394a-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="f394a-104">Syntax</span></span>  
  
```  
HRESULT IsDebuggerAttached (  
    [out] BOOL *pbAttached  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f394a-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="f394a-105">Parameters</span></span>  
 `pbAttached`  
 <span data-ttu-id="f394a-106">[out] `true` se um depurador estiver anexado ao processo; caso contrário, `false`.</span><span class="sxs-lookup"><span data-stu-id="f394a-106">[out] `true` if a debugger is attached to the process; otherwise, `false`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="f394a-107">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="f394a-107">Return Value</span></span>  
  
|<span data-ttu-id="f394a-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="f394a-108">HRESULT</span></span>|<span data-ttu-id="f394a-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="f394a-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="f394a-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="f394a-110">S_OK</span></span>|<span data-ttu-id="f394a-111">`IsDebuggerAttached` retornado com êxito.</span><span class="sxs-lookup"><span data-stu-id="f394a-111">`IsDebuggerAttached` returned successfully.</span></span>|  
|<span data-ttu-id="f394a-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="f394a-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="f394a-113">O common language runtime (CLR) não foi carregado em um processo ou o CLR está em um estado em que ele não pode executar o código gerenciado ou processar a chamada com êxito.</span><span class="sxs-lookup"><span data-stu-id="f394a-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="f394a-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="f394a-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="f394a-115">A chamada atingiu o tempo limite.</span><span class="sxs-lookup"><span data-stu-id="f394a-115">The call timed out.</span></span>|  
|<span data-ttu-id="f394a-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="f394a-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="f394a-117">O chamador não é proprietário do bloqueio.</span><span class="sxs-lookup"><span data-stu-id="f394a-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="f394a-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="f394a-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="f394a-119">Um evento foi cancelado enquanto um thread bloqueado ou fibra estava esperando por ele.</span><span class="sxs-lookup"><span data-stu-id="f394a-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="f394a-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="f394a-120">E_FAIL</span></span>|<span data-ttu-id="f394a-121">Ocorreu uma falha catastrófica desconhecida.</span><span class="sxs-lookup"><span data-stu-id="f394a-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="f394a-122">Depois que um método retorna E_FAIL, o CLR não é mais utilizável dentro do processo.</span><span class="sxs-lookup"><span data-stu-id="f394a-122">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="f394a-123">As chamadas subsequentes à hospedagem de métodos de retorno HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="f394a-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f394a-124">Comentários</span><span class="sxs-lookup"><span data-stu-id="f394a-124">Remarks</span></span>  
 <span data-ttu-id="f394a-125">`IsDebuggerAttached` permite que o host do CLR para determinar se um depurador está anexado ao processo de consulta.</span><span class="sxs-lookup"><span data-stu-id="f394a-125">`IsDebuggerAttached` allows the host to query the CLR to determine whether a debugger is attached to the process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f394a-126">Requisitos</span><span class="sxs-lookup"><span data-stu-id="f394a-126">Requirements</span></span>  
 <span data-ttu-id="f394a-127">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f394a-127">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f394a-128">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="f394a-128">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="f394a-129">**Biblioteca:** Incluído como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="f394a-129">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="f394a-130">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f394a-130">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f394a-131">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f394a-131">See also</span></span>

- [<span data-ttu-id="f394a-132">Interface ICLRControl</span><span class="sxs-lookup"><span data-stu-id="f394a-132">ICLRControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)
- [<span data-ttu-id="f394a-133">Interface ICLRDebugManager</span><span class="sxs-lookup"><span data-stu-id="f394a-133">ICLRDebugManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-interface.md)
- [<span data-ttu-id="f394a-134">Interface IHostControl</span><span class="sxs-lookup"><span data-stu-id="f394a-134">IHostControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostcontrol-interface.md)
