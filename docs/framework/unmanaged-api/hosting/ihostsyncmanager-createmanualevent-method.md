---
title: Método IHostSyncManager::CreateManualEvent
ms.date: 03/30/2017
api_name:
- IHostSyncManager.CreateManualEvent
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostSyncManager::CreateManualEvent
helpviewer_keywords:
- CreateManualEvent method [.NET Framework hosting]
- IHostSyncManager::CreateManualEvent method [.NET Framework hosting]
ms.assetid: 68661fbd-09cf-46dc-890b-e694f8a3880a
topic_type:
- apiref
ms.openlocfilehash: 334520df749ba428e6480188cd0655bb734725a6
ms.sourcegitcommit: d223616e7e6fe2139079052e6fcbe25413fb9900
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/22/2020
ms.locfileid: "83803305"
---
# <a name="ihostsyncmanagercreatemanualevent-method"></a><span data-ttu-id="27a96-102">Método IHostSyncManager::CreateManualEvent</span><span class="sxs-lookup"><span data-stu-id="27a96-102">IHostSyncManager::CreateManualEvent Method</span></span>
<span data-ttu-id="27a96-103">Cria um objeto de evento de redefinição manual.</span><span class="sxs-lookup"><span data-stu-id="27a96-103">Creates a manual-reset event object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="27a96-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="27a96-104">Syntax</span></span>  
  
```cpp  
HRESULT CreateManualEvent (  
    [in]  BOOL bInitialState,  
    [out] IHostManualEvent **ppEvent  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="27a96-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="27a96-105">Parameters</span></span>  
 `bInitialState`  
 <span data-ttu-id="27a96-106">[in] `true` , se o objeto for sinalizado; caso contrário, `false` .</span><span class="sxs-lookup"><span data-stu-id="27a96-106">[in] `true`, if the object is signaled; otherwise, `false`.</span></span>  
  
 `ppEvent`  
 <span data-ttu-id="27a96-107">fora Um ponteiro para o endereço de uma instância de [IHostManualEvent](ihostmanualevent-interface.md) ou NULL se o evento não pôde ser criado.</span><span class="sxs-lookup"><span data-stu-id="27a96-107">[out] A pointer to the address of an [IHostManualEvent](ihostmanualevent-interface.md) instance, or null if the event could not be created.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="27a96-108">Valor Retornado</span><span class="sxs-lookup"><span data-stu-id="27a96-108">Return Value</span></span>  
  
|<span data-ttu-id="27a96-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="27a96-109">HRESULT</span></span>|<span data-ttu-id="27a96-110">Descrição</span><span class="sxs-lookup"><span data-stu-id="27a96-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="27a96-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="27a96-111">S_OK</span></span>|<span data-ttu-id="27a96-112">`CreateManualEvent`retornado com êxito.</span><span class="sxs-lookup"><span data-stu-id="27a96-112">`CreateManualEvent` returned successfully.</span></span>|  
|<span data-ttu-id="27a96-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="27a96-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="27a96-114">O Common Language Runtime (CLR) não foi carregado em um processo ou o CLR está em um estado no qual não pode executar código gerenciado ou processar a chamada com êxito.</span><span class="sxs-lookup"><span data-stu-id="27a96-114">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="27a96-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="27a96-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="27a96-116">A chamada atingiu o tempo limite.</span><span class="sxs-lookup"><span data-stu-id="27a96-116">The call timed out.</span></span>|  
|<span data-ttu-id="27a96-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="27a96-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="27a96-118">O chamador não possui o bloqueio.</span><span class="sxs-lookup"><span data-stu-id="27a96-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="27a96-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="27a96-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="27a96-120">Um evento foi cancelado enquanto um thread ou uma fibra bloqueada estava esperando.</span><span class="sxs-lookup"><span data-stu-id="27a96-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="27a96-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="27a96-121">E_FAIL</span></span>|<span data-ttu-id="27a96-122">Ocorreu uma falha catastrófica desconhecida.</span><span class="sxs-lookup"><span data-stu-id="27a96-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="27a96-123">Quando um método retorna E_FAIL, o CLR não é mais utilizável no processo.</span><span class="sxs-lookup"><span data-stu-id="27a96-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="27a96-124">As chamadas subsequentes para métodos de hospedagem retornam HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="27a96-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="27a96-125">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="27a96-125">E_OUTOFMEMORY</span></span>|<span data-ttu-id="27a96-126">Não havia memória suficiente disponível para criar o objeto de evento solicitado.</span><span class="sxs-lookup"><span data-stu-id="27a96-126">Not enough memory was available to create the requested event object.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="27a96-127">Comentários</span><span class="sxs-lookup"><span data-stu-id="27a96-127">Remarks</span></span>  
 <span data-ttu-id="27a96-128">`CreateManualEvent`Cria um `IHostManualEvent` , um objeto de evento de redefinição manual que requer uma chamada para o método [IHostManualEvent:: Reset](ihostmanualevent-reset-method.md) para defini-lo como um estado não sinalizado.</span><span class="sxs-lookup"><span data-stu-id="27a96-128">`CreateManualEvent` creates an `IHostManualEvent`, a manual-reset event object that requires a call to the [IHostManualEvent::Reset](ihostmanualevent-reset-method.md) method to set it to a non-signaled state.</span></span> <span data-ttu-id="27a96-129">`CreateManualEvent`espelha a função do Win32 `CreateEvent` com um valor de `true` especificado para o `bManualReset` parâmetro.</span><span class="sxs-lookup"><span data-stu-id="27a96-129">`CreateManualEvent` mirrors the Win32 `CreateEvent` function with a value of `true` specified for the `bManualReset` parameter.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="27a96-130">Requisitos</span><span class="sxs-lookup"><span data-stu-id="27a96-130">Requirements</span></span>  
 <span data-ttu-id="27a96-131">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="27a96-131">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="27a96-132">**Cabeçalho:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="27a96-132">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="27a96-133">**Biblioteca:** Incluído como um recurso em MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="27a96-133">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="27a96-134">**.NET Framework versões:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="27a96-134">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="27a96-135">Confira também</span><span class="sxs-lookup"><span data-stu-id="27a96-135">See also</span></span>

- [<span data-ttu-id="27a96-136">Interface ICLRSyncManager</span><span class="sxs-lookup"><span data-stu-id="27a96-136">ICLRSyncManager Interface</span></span>](iclrsyncmanager-interface.md)
- [<span data-ttu-id="27a96-137">Interface IHostManualEvent</span><span class="sxs-lookup"><span data-stu-id="27a96-137">IHostManualEvent Interface</span></span>](ihostmanualevent-interface.md)
- [<span data-ttu-id="27a96-138">Interface IHostSyncManager</span><span class="sxs-lookup"><span data-stu-id="27a96-138">IHostSyncManager Interface</span></span>](ihostsyncmanager-interface.md)
