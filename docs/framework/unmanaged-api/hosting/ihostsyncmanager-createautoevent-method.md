---
title: Método IHostSyncManager::CreateAutoEvent
ms.date: 03/30/2017
api_name:
- IHostSyncManager.CreateAutoEvent
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostSyncManager::CreateAutoEvent
helpviewer_keywords:
- IHostSyncManager::CreateAutoEvent method [.NET Framework hosting]
- CreateAutoEvent method [.NET Framework hosting]
ms.assetid: 3153643e-cf5c-4b44-8e0e-c2b22cb08208
topic_type:
- apiref
ms.openlocfilehash: ba221beaa0edce49e75f75edddaee72e1beb9747
ms.sourcegitcommit: d223616e7e6fe2139079052e6fcbe25413fb9900
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/22/2020
ms.locfileid: "83803496"
---
# <a name="ihostsyncmanagercreateautoevent-method"></a><span data-ttu-id="04307-102">Método IHostSyncManager::CreateAutoEvent</span><span class="sxs-lookup"><span data-stu-id="04307-102">IHostSyncManager::CreateAutoEvent Method</span></span>
<span data-ttu-id="04307-103">Cria um objeto de evento de redefinição automática.</span><span class="sxs-lookup"><span data-stu-id="04307-103">Creates an auto-reset event object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="04307-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="04307-104">Syntax</span></span>  
  
```cpp  
HRESULT CreateAutoEvent (  
    [out] IHostAutoEvent **ppEvent  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="04307-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="04307-105">Parameters</span></span>  
 `ppEvent`  
 <span data-ttu-id="04307-106">fora Um ponteiro para o endereço de uma instância de [IHostAutoEvent](ihostautoevent-interface.md) implementada pelo host ou NULL se o objeto de evento não pôde ser criado.</span><span class="sxs-lookup"><span data-stu-id="04307-106">[out] A pointer to the address of an [IHostAutoEvent](ihostautoevent-interface.md) instance implemented by the host, or null if the event object could not be created.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="04307-107">Valor Retornado</span><span class="sxs-lookup"><span data-stu-id="04307-107">Return Value</span></span>  
  
|<span data-ttu-id="04307-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="04307-108">HRESULT</span></span>|<span data-ttu-id="04307-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="04307-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="04307-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="04307-110">S_OK</span></span>|<span data-ttu-id="04307-111">`CreateAutoEvent`retornado com êxito.</span><span class="sxs-lookup"><span data-stu-id="04307-111">`CreateAutoEvent` returned successfully.</span></span>|  
|<span data-ttu-id="04307-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="04307-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="04307-113">O Common Language Runtime (CLR) não foi carregado em um processo ou o CLR está em um estado no qual não pode executar código gerenciado ou processar a chamada com êxito.</span><span class="sxs-lookup"><span data-stu-id="04307-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="04307-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="04307-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="04307-115">A chamada atingiu o tempo limite.</span><span class="sxs-lookup"><span data-stu-id="04307-115">The call timed out.</span></span>|  
|<span data-ttu-id="04307-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="04307-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="04307-117">O chamador não possui o bloqueio.</span><span class="sxs-lookup"><span data-stu-id="04307-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="04307-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="04307-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="04307-119">Um evento foi cancelado enquanto um thread ou uma fibra bloqueada estava esperando.</span><span class="sxs-lookup"><span data-stu-id="04307-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="04307-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="04307-120">E_FAIL</span></span>|<span data-ttu-id="04307-121">Ocorreu uma falha catastrófica desconhecida.</span><span class="sxs-lookup"><span data-stu-id="04307-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="04307-122">Quando um método retorna E_FAIL, o CLR não é mais utilizável no processo.</span><span class="sxs-lookup"><span data-stu-id="04307-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="04307-123">As chamadas subsequentes para métodos de hospedagem retornam HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="04307-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="04307-124">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="04307-124">E_OUTOFMEMORY</span></span>|<span data-ttu-id="04307-125">Não havia memória suficiente disponível para criar o objeto de evento solicitado.</span><span class="sxs-lookup"><span data-stu-id="04307-125">Not enough memory was available to create the requested event object.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="04307-126">Comentários</span><span class="sxs-lookup"><span data-stu-id="04307-126">Remarks</span></span>  
 <span data-ttu-id="04307-127">`CreateAutoEvent`Cria um objeto de evento automático cujo estado é alterado automaticamente para não sinalizado após o lançamento do thread em espera.</span><span class="sxs-lookup"><span data-stu-id="04307-127">`CreateAutoEvent` creates an auto-event object whose state is automatically changed to non-signaled after the waiting thread has been released.</span></span> <span data-ttu-id="04307-128">Esse método espelha a função do Win32 `CreateEvent` com um valor de `false` especificado para o `bManualReset` parâmetro</span><span class="sxs-lookup"><span data-stu-id="04307-128">This method mirrors the Win32 `CreateEvent` function with a value of `false` specified for the `bManualReset` parameter</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="04307-129">Requisitos</span><span class="sxs-lookup"><span data-stu-id="04307-129">Requirements</span></span>  
 <span data-ttu-id="04307-130">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="04307-130">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="04307-131">**Cabeçalho:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="04307-131">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="04307-132">**Biblioteca:** Incluído como um recurso em MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="04307-132">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="04307-133">**.NET Framework versões:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="04307-133">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="04307-134">Confira também</span><span class="sxs-lookup"><span data-stu-id="04307-134">See also</span></span>

- [<span data-ttu-id="04307-135">Interface ICLRSyncManager</span><span class="sxs-lookup"><span data-stu-id="04307-135">ICLRSyncManager Interface</span></span>](iclrsyncmanager-interface.md)
- [<span data-ttu-id="04307-136">Interface IHostAutoEvent</span><span class="sxs-lookup"><span data-stu-id="04307-136">IHostAutoEvent Interface</span></span>](ihostautoevent-interface.md)
- [<span data-ttu-id="04307-137">Interface IHostControl</span><span class="sxs-lookup"><span data-stu-id="04307-137">IHostControl Interface</span></span>](ihostcontrol-interface.md)
- [<span data-ttu-id="04307-138">Interface IHostSyncManager</span><span class="sxs-lookup"><span data-stu-id="04307-138">IHostSyncManager Interface</span></span>](ihostsyncmanager-interface.md)
