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
ms.openlocfilehash: 30159748c1103cbc8efaf8929387052bbe5c3ec7
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67773131"
---
# <a name="iclrdebugmanagerisdebuggerattached-method"></a><span data-ttu-id="93f98-102">Método ICLRDebugManager::IsDebuggerAttached</span><span class="sxs-lookup"><span data-stu-id="93f98-102">ICLRDebugManager::IsDebuggerAttached Method</span></span>
<span data-ttu-id="93f98-103">Obtém um valor que indica se um depurador está anexado ao processo.</span><span class="sxs-lookup"><span data-stu-id="93f98-103">Gets a value that indicates whether a debugger is attached to the process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="93f98-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="93f98-104">Syntax</span></span>  
  
```cpp  
HRESULT IsDebuggerAttached (  
    [out] BOOL *pbAttached  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="93f98-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="93f98-105">Parameters</span></span>  
 `pbAttached`  
 <span data-ttu-id="93f98-106">[out] `true` se um depurador estiver anexado ao processo; caso contrário, `false`.</span><span class="sxs-lookup"><span data-stu-id="93f98-106">[out] `true` if a debugger is attached to the process; otherwise, `false`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="93f98-107">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="93f98-107">Return Value</span></span>  
  
|<span data-ttu-id="93f98-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="93f98-108">HRESULT</span></span>|<span data-ttu-id="93f98-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="93f98-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="93f98-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="93f98-110">S_OK</span></span>|<span data-ttu-id="93f98-111">`IsDebuggerAttached` retornado com êxito.</span><span class="sxs-lookup"><span data-stu-id="93f98-111">`IsDebuggerAttached` returned successfully.</span></span>|  
|<span data-ttu-id="93f98-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="93f98-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="93f98-113">O common language runtime (CLR) não foi carregado em um processo ou o CLR está em um estado em que ele não pode executar o código gerenciado ou processar a chamada com êxito.</span><span class="sxs-lookup"><span data-stu-id="93f98-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="93f98-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="93f98-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="93f98-115">A chamada atingiu o tempo limite.</span><span class="sxs-lookup"><span data-stu-id="93f98-115">The call timed out.</span></span>|  
|<span data-ttu-id="93f98-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="93f98-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="93f98-117">O chamador não é proprietário do bloqueio.</span><span class="sxs-lookup"><span data-stu-id="93f98-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="93f98-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="93f98-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="93f98-119">Um evento foi cancelado enquanto um thread bloqueado ou fibra estava esperando por ele.</span><span class="sxs-lookup"><span data-stu-id="93f98-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="93f98-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="93f98-120">E_FAIL</span></span>|<span data-ttu-id="93f98-121">Ocorreu uma falha catastrófica desconhecida.</span><span class="sxs-lookup"><span data-stu-id="93f98-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="93f98-122">Depois que um método retorna E_FAIL, o CLR não é mais utilizável dentro do processo.</span><span class="sxs-lookup"><span data-stu-id="93f98-122">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="93f98-123">As chamadas subsequentes à hospedagem de métodos de retorno HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="93f98-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="93f98-124">Comentários</span><span class="sxs-lookup"><span data-stu-id="93f98-124">Remarks</span></span>  
 <span data-ttu-id="93f98-125">`IsDebuggerAttached` permite que o host do CLR para determinar se um depurador está anexado ao processo de consulta.</span><span class="sxs-lookup"><span data-stu-id="93f98-125">`IsDebuggerAttached` allows the host to query the CLR to determine whether a debugger is attached to the process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="93f98-126">Requisitos</span><span class="sxs-lookup"><span data-stu-id="93f98-126">Requirements</span></span>  
 <span data-ttu-id="93f98-127">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="93f98-127">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="93f98-128">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="93f98-128">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="93f98-129">**Biblioteca:** Incluído como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="93f98-129">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="93f98-130">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="93f98-130">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="93f98-131">Consulte também</span><span class="sxs-lookup"><span data-stu-id="93f98-131">See also</span></span>

- [<span data-ttu-id="93f98-132">Interface ICLRControl</span><span class="sxs-lookup"><span data-stu-id="93f98-132">ICLRControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)
- [<span data-ttu-id="93f98-133">Interface ICLRDebugManager</span><span class="sxs-lookup"><span data-stu-id="93f98-133">ICLRDebugManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-interface.md)
- [<span data-ttu-id="93f98-134">Interface IHostControl</span><span class="sxs-lookup"><span data-stu-id="93f98-134">IHostControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostcontrol-interface.md)
