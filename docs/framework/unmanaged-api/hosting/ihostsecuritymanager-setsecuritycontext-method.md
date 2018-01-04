---
title: "Método IHostSecurityManager::SetSecurityContext"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IHostSecurityManager.SetSecurityContext
api_location: mscoree.dll
api_type: COM
f1_keywords: IHostSecurityManager::SetSecurityContext
helpviewer_keywords:
- SetSecurityContext method [.NET Framework hosting]
- IHostSecurityManager::SetSecurityContext method [.NET Framework hosting]
ms.assetid: e4372384-ee69-48d7-97e0-8fab7866597a
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 29a7652e20c08b9de584a9e11ac343ad92f40653
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="ihostsecuritymanagersetsecuritycontext-method"></a><span data-ttu-id="b2ba7-102">Método IHostSecurityManager::SetSecurityContext</span><span class="sxs-lookup"><span data-stu-id="b2ba7-102">IHostSecurityManager::SetSecurityContext Method</span></span>
<span data-ttu-id="b2ba7-103">Define o contexto de segurança do thread em execução no momento.</span><span class="sxs-lookup"><span data-stu-id="b2ba7-103">Sets the security context of the currently executing thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b2ba7-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="b2ba7-104">Syntax</span></span>  
  
```  
HRESULT SetSecurityContext (  
    [in]  EContextType eContextType,  
    [out] IHostSecurityContext** ppSecurityContext  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="b2ba7-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="b2ba7-105">Parameters</span></span>  
 `eContextType`  
 <span data-ttu-id="b2ba7-106">[in] Uma da [EContextType](../../../../docs/framework/unmanaged-api/hosting/econtexttype-enumeration.md) valores, que indica o tipo de contexto que o common language runtime (CLR) está colocando no host.</span><span class="sxs-lookup"><span data-stu-id="b2ba7-106">[in] One of the [EContextType](../../../../docs/framework/unmanaged-api/hosting/econtexttype-enumeration.md) values, indicating what type of context the common language runtime (CLR) is placing on the host.</span></span>  
  
 `ppSecurityContext`  
 <span data-ttu-id="b2ba7-107">[out] Um ponteiro para o endereço de uma nova [IHostSecurityContext](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritycontext-interface.md) objeto.</span><span class="sxs-lookup"><span data-stu-id="b2ba7-107">[out] A pointer to the address of a new [IHostSecurityContext](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritycontext-interface.md) object.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="b2ba7-108">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="b2ba7-108">Return Value</span></span>  
  
|<span data-ttu-id="b2ba7-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="b2ba7-109">HRESULT</span></span>|<span data-ttu-id="b2ba7-110">Descrição</span><span class="sxs-lookup"><span data-stu-id="b2ba7-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="b2ba7-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="b2ba7-111">S_OK</span></span>|<span data-ttu-id="b2ba7-112">`SetSecurityContext`retornou com êxito.</span><span class="sxs-lookup"><span data-stu-id="b2ba7-112">`SetSecurityContext` returned successfully.</span></span>|  
|<span data-ttu-id="b2ba7-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="b2ba7-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="b2ba7-114">O CLR não foi carregado em um processo ou o CLR está em um estado em que ele não pode executar código gerenciado ou processar a chamada com êxito.</span><span class="sxs-lookup"><span data-stu-id="b2ba7-114">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="b2ba7-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="b2ba7-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="b2ba7-116">A chamada foi atingido.</span><span class="sxs-lookup"><span data-stu-id="b2ba7-116">The call timed out.</span></span>|  
|<span data-ttu-id="b2ba7-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="b2ba7-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="b2ba7-118">O chamador não possui o bloqueio.</span><span class="sxs-lookup"><span data-stu-id="b2ba7-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="b2ba7-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="b2ba7-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="b2ba7-120">Um evento foi cancelado durante um thread bloqueado ou fibra estava aguardando nele.</span><span class="sxs-lookup"><span data-stu-id="b2ba7-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="b2ba7-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="b2ba7-121">E_FAIL</span></span>|<span data-ttu-id="b2ba7-122">Ocorreu uma falha catastrófica desconhecida.</span><span class="sxs-lookup"><span data-stu-id="b2ba7-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="b2ba7-123">Quando um método retornará E_FAIL, o CLR não será mais utilizável dentro do processo.</span><span class="sxs-lookup"><span data-stu-id="b2ba7-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="b2ba7-124">As chamadas subsequentes para hospedagem métodos retornam HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="b2ba7-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b2ba7-125">Comentários</span><span class="sxs-lookup"><span data-stu-id="b2ba7-125">Remarks</span></span>  
 <span data-ttu-id="b2ba7-126">O CLR chama `SetSecurityContext` em diversos cenários.</span><span class="sxs-lookup"><span data-stu-id="b2ba7-126">The CLR calls `SetSecurityContext` in several scenarios.</span></span> <span data-ttu-id="b2ba7-127">Antes de executar classe e construtores de módulo e finalizadores, o CLR chama `SetSecurityContext` para proteger o host de falhas de execução.</span><span class="sxs-lookup"><span data-stu-id="b2ba7-127">Before it executes class and module constructors and finalizers, the CLR calls `SetSecurityContext` to protect the host from execution failures.</span></span> <span data-ttu-id="b2ba7-128">Ele redefine o contexto de segurança para seu estado original após a execução do construtor ou finalizador, usando outra chamada para `SetSecurityContext`.</span><span class="sxs-lookup"><span data-stu-id="b2ba7-128">It then resets the security context to its original state after execution of the constructor or finalizer, by using another call to `SetSecurityContext`.</span></span> <span data-ttu-id="b2ba7-129">Um padrão semelhante ocorre com conclusão de e/s.</span><span class="sxs-lookup"><span data-stu-id="b2ba7-129">A similar pattern occurs with I/O completion.</span></span> <span data-ttu-id="b2ba7-130">Se o host implementa [IHostIoCompletionManager](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-interface.md), o CLR chama `SetSecurityContext` depois das chamadas de host [Iclriocompletionmanager](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-oncomplete-method.md).</span><span class="sxs-lookup"><span data-stu-id="b2ba7-130">If the host implements [IHostIoCompletionManager](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-interface.md), the CLR calls `SetSecurityContext` after the host calls [ICLRIoCompletionManager::OnComplete](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-oncomplete-method.md).</span></span>  
  
 <span data-ttu-id="b2ba7-131">Nos threads de trabalho assíncrono pontos, o CLR chama `SetSecurityContext` em <xref:System.Threading.ThreadPool.QueueUserWorkItem%2A?displayProperty=nameWithType> ou em [Ihostthreadpoolmanager](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-queueuserworkitem-method.md), dependendo se o host ou o CLR está implementando o pool de threads.</span><span class="sxs-lookup"><span data-stu-id="b2ba7-131">At asynchronous points in worker threads, the CLR calls `SetSecurityContext` within <xref:System.Threading.ThreadPool.QueueUserWorkItem%2A?displayProperty=nameWithType> or within [IHostThreadPoolManager::QueueUserWorkItem](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-queueuserworkitem-method.md), depending on whether the host or the CLR is implementing the thread pool.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b2ba7-132">Requisitos</span><span class="sxs-lookup"><span data-stu-id="b2ba7-132">Requirements</span></span>  
 <span data-ttu-id="b2ba7-133">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b2ba7-133">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b2ba7-134">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="b2ba7-134">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="b2ba7-135">**Biblioteca:** incluído como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="b2ba7-135">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="b2ba7-136">**Versões do .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b2ba7-136">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b2ba7-137">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b2ba7-137">See Also</span></span>  
 <xref:System.Threading.ThreadPool?displayProperty=nameWithType>  
 [<span data-ttu-id="b2ba7-138">Enumeração EContextType</span><span class="sxs-lookup"><span data-stu-id="b2ba7-138">EContextType Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/econtexttype-enumeration.md)  
 [<span data-ttu-id="b2ba7-139">Interface ICLRIoCompletionManager</span><span class="sxs-lookup"><span data-stu-id="b2ba7-139">ICLRIoCompletionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-interface.md)  
 [<span data-ttu-id="b2ba7-140">Interface IHostIoCompletionManager</span><span class="sxs-lookup"><span data-stu-id="b2ba7-140">IHostIoCompletionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-interface.md)  
 [<span data-ttu-id="b2ba7-141">Interface IHostSecurityContext</span><span class="sxs-lookup"><span data-stu-id="b2ba7-141">IHostSecurityContext Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritycontext-interface.md)  
 [<span data-ttu-id="b2ba7-142">Interface IHostSecurityManager</span><span class="sxs-lookup"><span data-stu-id="b2ba7-142">IHostSecurityManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-interface.md)  
 [<span data-ttu-id="b2ba7-143">Interface IHostThreadPoolManager</span><span class="sxs-lookup"><span data-stu-id="b2ba7-143">IHostThreadPoolManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-interface.md)
