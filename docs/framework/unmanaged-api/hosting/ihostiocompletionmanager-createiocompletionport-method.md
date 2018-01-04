---
title: "Método IHostIoCompletionManager::CreateIoCompletionPort"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IHostIoCompletionManager.CreateIoCompletionPort
api_location: mscoree.dll
api_type: COM
f1_keywords: IHostIoCompletionManager::CreateIoCompletionPort
helpviewer_keywords:
- IHostIoCompletionManager::CreateIoCompletionPort method [.NET Framework hosting]
- CreateIoCompletionPort method [.NET Framework hosting]
ms.assetid: 907a2b43-68db-44a7-acac-89e792e7bb3c
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 230d6446460af92dbc4356977c0df4556d0229a0
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="ihostiocompletionmanagercreateiocompletionport-method"></a><span data-ttu-id="e4175-102">Método IHostIoCompletionManager::CreateIoCompletionPort</span><span class="sxs-lookup"><span data-stu-id="e4175-102">IHostIoCompletionManager::CreateIoCompletionPort Method</span></span>
<span data-ttu-id="e4175-103">Solicita que o host de cria uma nova porta de conclusão de e/s.</span><span class="sxs-lookup"><span data-stu-id="e4175-103">Requests that the host create a new I/O completion port.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e4175-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="e4175-104">Syntax</span></span>  
  
```  
HRESULT CreateIoCompletionPort (  
    [out] HANDLE *phPort  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="e4175-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="e4175-105">Parameters</span></span>  
 `phPort`  
 <span data-ttu-id="e4175-106">[out] Um ponteiro para um identificador para a porta de conclusão de e/s recém-criado ou 0 (zero), se a porta não pôde ser criada.</span><span class="sxs-lookup"><span data-stu-id="e4175-106">[out] A pointer to a handle to the newly created I/O completion port, or 0 (zero), if the port could not be created.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e4175-107">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="e4175-107">Return Value</span></span>  
  
|<span data-ttu-id="e4175-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="e4175-108">HRESULT</span></span>|<span data-ttu-id="e4175-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="e4175-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="e4175-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="e4175-110">S_OK</span></span>|<span data-ttu-id="e4175-111">`CreateIoCompletionPort`retornou com êxito.</span><span class="sxs-lookup"><span data-stu-id="e4175-111">`CreateIoCompletionPort` returned successfully.</span></span>|  
|<span data-ttu-id="e4175-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="e4175-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="e4175-113">O common language runtime (CLR) não foi carregado em um processo ou o CLR está em um estado em que ele não pode executar código gerenciado ou processar a chamada com êxito.</span><span class="sxs-lookup"><span data-stu-id="e4175-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="e4175-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="e4175-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="e4175-115">A chamada foi atingido.</span><span class="sxs-lookup"><span data-stu-id="e4175-115">The call timed out.</span></span>|  
|<span data-ttu-id="e4175-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="e4175-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="e4175-117">O chamador não possui o bloqueio.</span><span class="sxs-lookup"><span data-stu-id="e4175-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="e4175-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="e4175-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="e4175-119">Um evento foi cancelado durante um thread bloqueado ou fibra estava aguardando nele.</span><span class="sxs-lookup"><span data-stu-id="e4175-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="e4175-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="e4175-120">E_FAIL</span></span>|<span data-ttu-id="e4175-121">Ocorreu uma falha catastrófica desconhecida.</span><span class="sxs-lookup"><span data-stu-id="e4175-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="e4175-122">Quando um método retornará E_FAIL, o CLR não será mais utilizável dentro do processo.</span><span class="sxs-lookup"><span data-stu-id="e4175-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="e4175-123">As chamadas subsequentes para hospedagem métodos retornam HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="e4175-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="e4175-124">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="e4175-124">E_OUTOFMEMORY</span></span>|<span data-ttu-id="e4175-125">Não havia memória suficiente disponível para alocar o recurso solicitado.</span><span class="sxs-lookup"><span data-stu-id="e4175-125">Not enough memory was available to allocate the requested resource.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e4175-126">Comentários</span><span class="sxs-lookup"><span data-stu-id="e4175-126">Remarks</span></span>  
 <span data-ttu-id="e4175-127">O CLR chama o `CreateIoCompletionPort` método para solicitar que o host de cria uma nova porta de conclusão de e/s.</span><span class="sxs-lookup"><span data-stu-id="e4175-127">The CLR calls the `CreateIoCompletionPort` method to request that the host create a new I/O completion port.</span></span> <span data-ttu-id="e4175-128">Operações de e/s ela está associada a essa porta por meio de uma chamada para o [Ihostiocompletionmanager](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-bind-method.md) método.</span><span class="sxs-lookup"><span data-stu-id="e4175-128">It binds I/O operations to this port through a call to the [IHostIoCompletionManager::Bind](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-bind-method.md) method.</span></span> <span data-ttu-id="e4175-129">O host relata o status novamente para o CLR chamando [Iclriocompletionmanager](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-oncomplete-method.md).</span><span class="sxs-lookup"><span data-stu-id="e4175-129">The host reports status back to the CLR by calling [ICLRIoCompletionManager::OnComplete](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-oncomplete-method.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e4175-130">Requisitos</span><span class="sxs-lookup"><span data-stu-id="e4175-130">Requirements</span></span>  
 <span data-ttu-id="e4175-131">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e4175-131">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e4175-132">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="e4175-132">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="e4175-133">**Biblioteca:** incluído como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="e4175-133">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="e4175-134">**Versões do .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e4175-134">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e4175-135">Consulte também</span><span class="sxs-lookup"><span data-stu-id="e4175-135">See Also</span></span>  
 [<span data-ttu-id="e4175-136">Interface ICLRIoCompletionManager</span><span class="sxs-lookup"><span data-stu-id="e4175-136">ICLRIoCompletionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-interface.md)  
 [<span data-ttu-id="e4175-137">Interface IHostIoCompletionManager</span><span class="sxs-lookup"><span data-stu-id="e4175-137">IHostIoCompletionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-interface.md)
