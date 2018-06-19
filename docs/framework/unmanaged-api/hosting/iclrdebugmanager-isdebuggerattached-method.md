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
ms.openlocfilehash: aaa085d9883f2a94a623f7800278c74a88e6a69a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33432902"
---
# <a name="iclrdebugmanagerisdebuggerattached-method"></a><span data-ttu-id="01413-102">Método ICLRDebugManager::IsDebuggerAttached</span><span class="sxs-lookup"><span data-stu-id="01413-102">ICLRDebugManager::IsDebuggerAttached Method</span></span>
<span data-ttu-id="01413-103">Obtém um valor que indica se um depurador está anexado ao processo.</span><span class="sxs-lookup"><span data-stu-id="01413-103">Gets a value that indicates whether a debugger is attached to the process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="01413-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="01413-104">Syntax</span></span>  
  
```  
HRESULT IsDebuggerAttached (  
    [out] BOOL *pbAttached  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="01413-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="01413-105">Parameters</span></span>  
 `pbAttached`  
 <span data-ttu-id="01413-106">[out] `true` se um depurador estiver anexado ao processo; caso contrário, `false`.</span><span class="sxs-lookup"><span data-stu-id="01413-106">[out] `true` if a debugger is attached to the process; otherwise, `false`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="01413-107">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="01413-107">Return Value</span></span>  
  
|<span data-ttu-id="01413-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="01413-108">HRESULT</span></span>|<span data-ttu-id="01413-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="01413-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="01413-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="01413-110">S_OK</span></span>|<span data-ttu-id="01413-111">`IsDebuggerAttached` retornou com êxito.</span><span class="sxs-lookup"><span data-stu-id="01413-111">`IsDebuggerAttached` returned successfully.</span></span>|  
|<span data-ttu-id="01413-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="01413-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="01413-113">O common language runtime (CLR) não foi carregado em um processo ou o CLR está em um estado em que ele não pode executar código gerenciado ou processar a chamada com êxito.</span><span class="sxs-lookup"><span data-stu-id="01413-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="01413-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="01413-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="01413-115">A chamada foi atingido.</span><span class="sxs-lookup"><span data-stu-id="01413-115">The call timed out.</span></span>|  
|<span data-ttu-id="01413-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="01413-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="01413-117">O chamador não possui o bloqueio.</span><span class="sxs-lookup"><span data-stu-id="01413-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="01413-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="01413-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="01413-119">Um evento foi cancelado durante um thread bloqueado ou fibra estava aguardando nele.</span><span class="sxs-lookup"><span data-stu-id="01413-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="01413-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="01413-120">E_FAIL</span></span>|<span data-ttu-id="01413-121">Ocorreu uma falha catastrófica desconhecida.</span><span class="sxs-lookup"><span data-stu-id="01413-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="01413-122">Depois que um método retornará E_FAIL, o CLR não será mais utilizável dentro do processo.</span><span class="sxs-lookup"><span data-stu-id="01413-122">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="01413-123">As chamadas subsequentes para hospedagem métodos retornam HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="01413-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="01413-124">Comentários</span><span class="sxs-lookup"><span data-stu-id="01413-124">Remarks</span></span>  
 <span data-ttu-id="01413-125">`IsDebuggerAttached` permite que o host do CLR para determinar se um depurador é anexado ao processo de consulta.</span><span class="sxs-lookup"><span data-stu-id="01413-125">`IsDebuggerAttached` allows the host to query the CLR to determine whether a debugger is attached to the process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="01413-126">Requisitos</span><span class="sxs-lookup"><span data-stu-id="01413-126">Requirements</span></span>  
 <span data-ttu-id="01413-127">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="01413-127">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="01413-128">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="01413-128">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="01413-129">**Biblioteca:** incluído como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="01413-129">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="01413-130">**Versões do .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="01413-130">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="01413-131">Consulte também</span><span class="sxs-lookup"><span data-stu-id="01413-131">See Also</span></span>  
 [<span data-ttu-id="01413-132">Interface ICLRControl</span><span class="sxs-lookup"><span data-stu-id="01413-132">ICLRControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)  
 [<span data-ttu-id="01413-133">Interface ICLRDebugManager</span><span class="sxs-lookup"><span data-stu-id="01413-133">ICLRDebugManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-interface.md)  
 [<span data-ttu-id="01413-134">Interface IHostControl</span><span class="sxs-lookup"><span data-stu-id="01413-134">IHostControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostcontrol-interface.md)
