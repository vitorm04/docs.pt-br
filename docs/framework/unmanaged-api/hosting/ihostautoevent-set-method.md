---
title: Método IHostAutoEvent::Set
ms.date: 03/30/2017
api_name:
- IHostAutoEvent.Set
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostAutoEvent::Set
helpviewer_keywords:
- Set method, IHostAutoEvent interface [.NET Framework hosting]
- IHostAutoEvent::Set method [.NET Framework hosting]
ms.assetid: 46becf3e-bc0e-4338-85c0-9ab0df76a1d0
topic_type:
- apiref
ms.openlocfilehash: 55fd858927743b097e5e842c0897a16d36b76733
ms.sourcegitcommit: d223616e7e6fe2139079052e6fcbe25413fb9900
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/22/2020
ms.locfileid: "83804980"
---
# <a name="ihostautoeventset-method"></a><span data-ttu-id="7bf75-102">Método IHostAutoEvent::Set</span><span class="sxs-lookup"><span data-stu-id="7bf75-102">IHostAutoEvent::Set Method</span></span>
<span data-ttu-id="7bf75-103">Define a instância de [IHostAutoEvent](ihostautoevent-interface.md) atual para um estado sinalizado.</span><span class="sxs-lookup"><span data-stu-id="7bf75-103">Sets the current [IHostAutoEvent](ihostautoevent-interface.md) instance to a signaled state.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7bf75-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="7bf75-104">Syntax</span></span>  
  
```cpp  
HRESULT Set ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="7bf75-105">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="7bf75-105">Return Value</span></span>  
  
|<span data-ttu-id="7bf75-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="7bf75-106">HRESULT</span></span>|<span data-ttu-id="7bf75-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="7bf75-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="7bf75-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="7bf75-108">S_OK</span></span>|<span data-ttu-id="7bf75-109">`Set`retornado com êxito.</span><span class="sxs-lookup"><span data-stu-id="7bf75-109">`Set` returned successfully.</span></span>|  
|<span data-ttu-id="7bf75-110">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="7bf75-110">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="7bf75-111">O Common Language Runtime (CLR) não foi carregado em um processo ou o CLR está em um estado no qual não pode executar código gerenciado ou processar a chamada com êxito.</span><span class="sxs-lookup"><span data-stu-id="7bf75-111">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="7bf75-112">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="7bf75-112">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="7bf75-113">A chamada atingiu o tempo limite.</span><span class="sxs-lookup"><span data-stu-id="7bf75-113">The call timed out.</span></span>|  
|<span data-ttu-id="7bf75-114">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="7bf75-114">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="7bf75-115">O chamador não possui o bloqueio.</span><span class="sxs-lookup"><span data-stu-id="7bf75-115">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="7bf75-116">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="7bf75-116">HOST_E_ABANDONED</span></span>|<span data-ttu-id="7bf75-117">Um evento foi cancelado enquanto um thread ou uma fibra bloqueada estava esperando.</span><span class="sxs-lookup"><span data-stu-id="7bf75-117">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="7bf75-118">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="7bf75-118">E_FAIL</span></span>|<span data-ttu-id="7bf75-119">Ocorreu uma falha catastrófica desconhecida.</span><span class="sxs-lookup"><span data-stu-id="7bf75-119">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="7bf75-120">Quando um método retorna E_FAIL, o CLR não é mais utilizável no processo.</span><span class="sxs-lookup"><span data-stu-id="7bf75-120">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="7bf75-121">As chamadas subsequentes para métodos de hospedagem retornam HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="7bf75-121">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="7bf75-122">Requisitos</span><span class="sxs-lookup"><span data-stu-id="7bf75-122">Requirements</span></span>  
 <span data-ttu-id="7bf75-123">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7bf75-123">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7bf75-124">**Cabeçalho:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="7bf75-124">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="7bf75-125">**Biblioteca:** Incluído como um recurso em MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="7bf75-125">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="7bf75-126">**.NET Framework versões:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7bf75-126">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7bf75-127">Confira também</span><span class="sxs-lookup"><span data-stu-id="7bf75-127">See also</span></span>

- [<span data-ttu-id="7bf75-128">Interface ICLRSyncManager</span><span class="sxs-lookup"><span data-stu-id="7bf75-128">ICLRSyncManager Interface</span></span>](iclrsyncmanager-interface.md)
- [<span data-ttu-id="7bf75-129">Interface IHostAutoEvent</span><span class="sxs-lookup"><span data-stu-id="7bf75-129">IHostAutoEvent Interface</span></span>](ihostautoevent-interface.md)
- [<span data-ttu-id="7bf75-130">Interface IHostManualEvent</span><span class="sxs-lookup"><span data-stu-id="7bf75-130">IHostManualEvent Interface</span></span>](ihostmanualevent-interface.md)
- [<span data-ttu-id="7bf75-131">Interface IHostSyncManager</span><span class="sxs-lookup"><span data-stu-id="7bf75-131">IHostSyncManager Interface</span></span>](ihostsyncmanager-interface.md)
