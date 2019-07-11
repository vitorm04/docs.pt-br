---
title: Método IHostCrst::Leave
ms.date: 03/30/2017
api_name:
- IHostCrst.Leave
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostCrst::Leave
helpviewer_keywords:
- IHostCrst::Leave method [.NET Framework hosting]
- Leave method [.NET Framework hosting]
ms.assetid: dfc51d9e-b36d-4dba-9ea1-4f63fa0601ae
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f260e1351c8aa14961a10e0f7087bd076752785d
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67763775"
---
# <a name="ihostcrstleave-method"></a><span data-ttu-id="c2f35-102">Método IHostCrst::Leave</span><span class="sxs-lookup"><span data-stu-id="c2f35-102">IHostCrst::Leave Method</span></span>
<span data-ttu-id="c2f35-103">Deixa a seção crítica que é representada pela instância atual do [IHostCrst](../../../../docs/framework/unmanaged-api/hosting/ihostcrst-interface.md).</span><span class="sxs-lookup"><span data-stu-id="c2f35-103">Leaves the critical section that is represented by the current instance of [IHostCrst](../../../../docs/framework/unmanaged-api/hosting/ihostcrst-interface.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c2f35-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="c2f35-104">Syntax</span></span>  
  
```cpp  
HRESULT Leave ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="c2f35-105">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="c2f35-105">Return Value</span></span>  
  
|<span data-ttu-id="c2f35-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="c2f35-106">HRESULT</span></span>|<span data-ttu-id="c2f35-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="c2f35-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="c2f35-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="c2f35-108">S_OK</span></span>|<span data-ttu-id="c2f35-109">`Leave` retornado com êxito.</span><span class="sxs-lookup"><span data-stu-id="c2f35-109">`Leave` returned successfully.</span></span>|  
|<span data-ttu-id="c2f35-110">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="c2f35-110">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="c2f35-111">O common language runtime (CLR) não foi carregado em um processo ou o CLR está em um estado em que ele não pode executar o código gerenciado ou processar a chamada com êxito.</span><span class="sxs-lookup"><span data-stu-id="c2f35-111">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="c2f35-112">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="c2f35-112">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="c2f35-113">A chamada atingiu o tempo limite.</span><span class="sxs-lookup"><span data-stu-id="c2f35-113">The call timed out.</span></span>|  
|<span data-ttu-id="c2f35-114">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="c2f35-114">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="c2f35-115">O chamador não é proprietário do bloqueio.</span><span class="sxs-lookup"><span data-stu-id="c2f35-115">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="c2f35-116">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="c2f35-116">HOST_E_ABANDONED</span></span>|<span data-ttu-id="c2f35-117">Um evento foi cancelado enquanto um thread bloqueado ou fibra estava esperando por ele.</span><span class="sxs-lookup"><span data-stu-id="c2f35-117">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="c2f35-118">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="c2f35-118">E_FAIL</span></span>|<span data-ttu-id="c2f35-119">Ocorreu uma falha catastrófica desconhecida.</span><span class="sxs-lookup"><span data-stu-id="c2f35-119">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="c2f35-120">Quando um método retornar E_FAIL, o CLR não é mais utilizável dentro do processo.</span><span class="sxs-lookup"><span data-stu-id="c2f35-120">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="c2f35-121">As chamadas subsequentes à hospedagem de métodos de retorno HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="c2f35-121">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c2f35-122">Comentários</span><span class="sxs-lookup"><span data-stu-id="c2f35-122">Remarks</span></span>  
 <span data-ttu-id="c2f35-123">`Leave` permite que o CLR para se comunicar diretamente com implementação de threading, no host vez de usar o Win32 correspondente `LeaveCriticalSection` função.</span><span class="sxs-lookup"><span data-stu-id="c2f35-123">`Leave` allows the CLR to communicate directly with the host's threading implementation, rather than using the corresponding Win32 `LeaveCriticalSection` function.</span></span> <span data-ttu-id="c2f35-124">Um thread que se apropria de seção crítica, representada pelo atual `IHostCrst` instância deve chamar `Leave` depois de cada vez que entrar nessa seção crítica.</span><span class="sxs-lookup"><span data-stu-id="c2f35-124">A thread that takes ownership of the critical section represented by the current `IHostCrst` instance must call `Leave` once for each time it enters that critical section.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c2f35-125">Requisitos</span><span class="sxs-lookup"><span data-stu-id="c2f35-125">Requirements</span></span>  
 <span data-ttu-id="c2f35-126">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c2f35-126">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c2f35-127">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="c2f35-127">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="c2f35-128">**Biblioteca:** Incluído como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="c2f35-128">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="c2f35-129">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c2f35-129">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c2f35-130">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c2f35-130">See also</span></span>

- [<span data-ttu-id="c2f35-131">Interface ICLRSyncManager</span><span class="sxs-lookup"><span data-stu-id="c2f35-131">ICLRSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)
- [<span data-ttu-id="c2f35-132">Interface IHostCrst</span><span class="sxs-lookup"><span data-stu-id="c2f35-132">IHostCrst Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostcrst-interface.md)
- [<span data-ttu-id="c2f35-133">Interface IHostSyncManager</span><span class="sxs-lookup"><span data-stu-id="c2f35-133">IHostSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)
