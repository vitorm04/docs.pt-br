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
ms.openlocfilehash: e4e6ad42c442d535e10432af099e51ca0d536729
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54572793"
---
# <a name="iclrdebugmanagerisdebuggerattached-method"></a><span data-ttu-id="30cb7-102">Método ICLRDebugManager::IsDebuggerAttached</span><span class="sxs-lookup"><span data-stu-id="30cb7-102">ICLRDebugManager::IsDebuggerAttached Method</span></span>
<span data-ttu-id="30cb7-103">Obtém um valor que indica se um depurador está anexado ao processo.</span><span class="sxs-lookup"><span data-stu-id="30cb7-103">Gets a value that indicates whether a debugger is attached to the process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="30cb7-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="30cb7-104">Syntax</span></span>  
  
```  
HRESULT IsDebuggerAttached (  
    [out] BOOL *pbAttached  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="30cb7-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="30cb7-105">Parameters</span></span>  
 `pbAttached`  
 <span data-ttu-id="30cb7-106">[out] `true` se um depurador estiver anexado ao processo; caso contrário, `false`.</span><span class="sxs-lookup"><span data-stu-id="30cb7-106">[out] `true` if a debugger is attached to the process; otherwise, `false`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="30cb7-107">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="30cb7-107">Return Value</span></span>  
  
|<span data-ttu-id="30cb7-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="30cb7-108">HRESULT</span></span>|<span data-ttu-id="30cb7-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="30cb7-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="30cb7-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="30cb7-110">S_OK</span></span>|<span data-ttu-id="30cb7-111">`IsDebuggerAttached` retornado com êxito.</span><span class="sxs-lookup"><span data-stu-id="30cb7-111">`IsDebuggerAttached` returned successfully.</span></span>|  
|<span data-ttu-id="30cb7-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="30cb7-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="30cb7-113">O common language runtime (CLR) não foi carregado em um processo ou o CLR está em um estado em que ele não pode executar o código gerenciado ou processar a chamada com êxito.</span><span class="sxs-lookup"><span data-stu-id="30cb7-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="30cb7-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="30cb7-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="30cb7-115">A chamada atingiu o tempo limite.</span><span class="sxs-lookup"><span data-stu-id="30cb7-115">The call timed out.</span></span>|  
|<span data-ttu-id="30cb7-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="30cb7-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="30cb7-117">O chamador não é proprietário do bloqueio.</span><span class="sxs-lookup"><span data-stu-id="30cb7-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="30cb7-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="30cb7-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="30cb7-119">Um evento foi cancelado enquanto um thread bloqueado ou fibra estava esperando por ele.</span><span class="sxs-lookup"><span data-stu-id="30cb7-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="30cb7-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="30cb7-120">E_FAIL</span></span>|<span data-ttu-id="30cb7-121">Ocorreu uma falha catastrófica desconhecida.</span><span class="sxs-lookup"><span data-stu-id="30cb7-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="30cb7-122">Depois que um método retorna E_FAIL, o CLR não é mais utilizável dentro do processo.</span><span class="sxs-lookup"><span data-stu-id="30cb7-122">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="30cb7-123">As chamadas subsequentes à hospedagem de métodos de retorno HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="30cb7-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="30cb7-124">Comentários</span><span class="sxs-lookup"><span data-stu-id="30cb7-124">Remarks</span></span>  
 <span data-ttu-id="30cb7-125">`IsDebuggerAttached` permite que o host do CLR para determinar se um depurador está anexado ao processo de consulta.</span><span class="sxs-lookup"><span data-stu-id="30cb7-125">`IsDebuggerAttached` allows the host to query the CLR to determine whether a debugger is attached to the process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="30cb7-126">Requisitos</span><span class="sxs-lookup"><span data-stu-id="30cb7-126">Requirements</span></span>  
 <span data-ttu-id="30cb7-127">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="30cb7-127">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="30cb7-128">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="30cb7-128">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="30cb7-129">**Biblioteca:** Incluído como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="30cb7-129">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="30cb7-130">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="30cb7-130">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="30cb7-131">Consulte também</span><span class="sxs-lookup"><span data-stu-id="30cb7-131">See also</span></span>
- [<span data-ttu-id="30cb7-132">Interface ICLRControl</span><span class="sxs-lookup"><span data-stu-id="30cb7-132">ICLRControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)
- [<span data-ttu-id="30cb7-133">Interface ICLRDebugManager</span><span class="sxs-lookup"><span data-stu-id="30cb7-133">ICLRDebugManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-interface.md)
- [<span data-ttu-id="30cb7-134">Interface IHostControl</span><span class="sxs-lookup"><span data-stu-id="30cb7-134">IHostControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostcontrol-interface.md)
