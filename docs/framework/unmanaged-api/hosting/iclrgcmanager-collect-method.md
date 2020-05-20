---
title: Método ICLRGCManager::Collect
ms.date: 03/30/2017
api_name:
- ICLRGCManager.Collect
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRGCManager::Collect
helpviewer_keywords:
- ICLRGCManager::Collect method [.NET Framework hosting]
- Collect method, ICLRGCManager interface [.NET Framework hosting]
ms.assetid: 0c6cbbea-c27c-4695-bda3-17c1910d8ddb
topic_type:
- apiref
ms.openlocfilehash: aa906e314c408b7653e611b07d7ad21d4519b715
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83616977"
---
# <a name="iclrgcmanagercollect-method"></a><span data-ttu-id="85417-102">Método ICLRGCManager::Collect</span><span class="sxs-lookup"><span data-stu-id="85417-102">ICLRGCManager::Collect Method</span></span>
<span data-ttu-id="85417-103">Força uma coleta de lixo para a geração especificada.</span><span class="sxs-lookup"><span data-stu-id="85417-103">Forces a garbage collection for the specified generation.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="85417-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="85417-104">Syntax</span></span>  
  
```cpp  
HRESULT Collect (  
    [in] LONG Generation  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="85417-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="85417-105">Parameters</span></span>  
 `Generation`  
 <span data-ttu-id="85417-106">no A geração a ser coletada.</span><span class="sxs-lookup"><span data-stu-id="85417-106">[in] The generation to collect.</span></span> <span data-ttu-id="85417-107">Um valor de-1 força uma coleção de todas as gerações.</span><span class="sxs-lookup"><span data-stu-id="85417-107">A value of -1 forces a collection of all generations.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="85417-108">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="85417-108">Return Value</span></span>  
  
|<span data-ttu-id="85417-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="85417-109">HRESULT</span></span>|<span data-ttu-id="85417-110">Descrição</span><span class="sxs-lookup"><span data-stu-id="85417-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="85417-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="85417-111">S_OK</span></span>|<span data-ttu-id="85417-112">`Collect`retornado com êxito.</span><span class="sxs-lookup"><span data-stu-id="85417-112">`Collect` returned successfully.</span></span>|  
|<span data-ttu-id="85417-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="85417-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="85417-114">O Common Language Runtime (CLR) não foi carregado em um processo ou o CLR está em um estado no qual não pode executar código gerenciado ou processar a chamada com êxito.</span><span class="sxs-lookup"><span data-stu-id="85417-114">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="85417-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="85417-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="85417-116">A chamada atingiu o tempo limite.</span><span class="sxs-lookup"><span data-stu-id="85417-116">The call timed out.</span></span>|  
|<span data-ttu-id="85417-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="85417-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="85417-118">O chamador não possui o bloqueio.</span><span class="sxs-lookup"><span data-stu-id="85417-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="85417-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="85417-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="85417-120">Um evento foi cancelado enquanto um thread ou uma fibra bloqueada estava esperando.</span><span class="sxs-lookup"><span data-stu-id="85417-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="85417-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="85417-121">E_FAIL</span></span>|<span data-ttu-id="85417-122">Ocorreu uma falha catastrófica desconhecida.</span><span class="sxs-lookup"><span data-stu-id="85417-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="85417-123">Depois que um método retorna E_FAIL, o CLR não pode mais ser usado no processo.</span><span class="sxs-lookup"><span data-stu-id="85417-123">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="85417-124">As chamadas subsequentes para métodos de hospedagem retornam HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="85417-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="85417-125">Comentários</span><span class="sxs-lookup"><span data-stu-id="85417-125">Remarks</span></span>  
 <span data-ttu-id="85417-126">O `Collect` método força o coletor de lixo do CLR a executar uma coleção, independentemente de seu estado atual.</span><span class="sxs-lookup"><span data-stu-id="85417-126">The `Collect` method forces the CLR's garbage collector to perform a collection regardless of its current state.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="85417-127">Requisitos</span><span class="sxs-lookup"><span data-stu-id="85417-127">Requirements</span></span>  
 <span data-ttu-id="85417-128">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="85417-128">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="85417-129">**Cabeçalho:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="85417-129">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="85417-130">**Biblioteca:** Incluído como um recurso em MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="85417-130">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="85417-131">**.NET Framework versões:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="85417-131">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="85417-132">Veja também</span><span class="sxs-lookup"><span data-stu-id="85417-132">See also</span></span>

- [<span data-ttu-id="85417-133">Gerenciamento automático de memória</span><span class="sxs-lookup"><span data-stu-id="85417-133">Automatic Memory Management</span></span>](../../../standard/automatic-memory-management.md)
- [<span data-ttu-id="85417-134">Coleta de lixo</span><span class="sxs-lookup"><span data-stu-id="85417-134">Garbage Collection</span></span>](../../../standard/garbage-collection/index.md)
- [<span data-ttu-id="85417-135">Interface ICLRControl</span><span class="sxs-lookup"><span data-stu-id="85417-135">ICLRControl Interface</span></span>](iclrcontrol-interface.md)
- [<span data-ttu-id="85417-136">Interface ICLRGCManager</span><span class="sxs-lookup"><span data-stu-id="85417-136">ICLRGCManager Interface</span></span>](iclrgcmanager-interface.md)
- [<span data-ttu-id="85417-137">Interfaces de hospedagem CLR</span><span class="sxs-lookup"><span data-stu-id="85417-137">CLR Hosting Interfaces</span></span>](clr-hosting-interfaces.md)
- [<span data-ttu-id="85417-138">Interfaces de hospedagem</span><span class="sxs-lookup"><span data-stu-id="85417-138">Hosting Interfaces</span></span>](hosting-interfaces.md)
- [<span data-ttu-id="85417-139">Hospedagem</span><span class="sxs-lookup"><span data-stu-id="85417-139">Hosting</span></span>](index.md)
