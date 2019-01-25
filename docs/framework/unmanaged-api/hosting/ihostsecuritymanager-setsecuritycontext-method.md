---
title: Método IHostSecurityManager::SetSecurityContext
ms.date: 03/30/2017
api_name:
- IHostSecurityManager.SetSecurityContext
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostSecurityManager::SetSecurityContext
helpviewer_keywords:
- SetSecurityContext method [.NET Framework hosting]
- IHostSecurityManager::SetSecurityContext method [.NET Framework hosting]
ms.assetid: e4372384-ee69-48d7-97e0-8fab7866597a
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 41b472d96c4db088c7ab34d9abb0940f3461c844
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54734549"
---
# <a name="ihostsecuritymanagersetsecuritycontext-method"></a><span data-ttu-id="b675c-102">Método IHostSecurityManager::SetSecurityContext</span><span class="sxs-lookup"><span data-stu-id="b675c-102">IHostSecurityManager::SetSecurityContext Method</span></span>
<span data-ttu-id="b675c-103">Define o contexto de segurança do thread em execução no momento.</span><span class="sxs-lookup"><span data-stu-id="b675c-103">Sets the security context of the currently executing thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b675c-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="b675c-104">Syntax</span></span>  
  
```  
HRESULT SetSecurityContext (  
    [in]  EContextType eContextType,  
    [out] IHostSecurityContext** ppSecurityContext  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="b675c-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="b675c-105">Parameters</span></span>  
 `eContextType`  
 <span data-ttu-id="b675c-106">[in] Um dos [EContextType](../../../../docs/framework/unmanaged-api/hosting/econtexttype-enumeration.md) valores, que indica o tipo de contexto que o common language runtime (CLR) está colocando no host.</span><span class="sxs-lookup"><span data-stu-id="b675c-106">[in] One of the [EContextType](../../../../docs/framework/unmanaged-api/hosting/econtexttype-enumeration.md) values, indicating what type of context the common language runtime (CLR) is placing on the host.</span></span>  
  
 `ppSecurityContext`  
 <span data-ttu-id="b675c-107">[out] Um ponteiro para o endereço de uma nova [IHostSecurityContext](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritycontext-interface.md) objeto.</span><span class="sxs-lookup"><span data-stu-id="b675c-107">[out] A pointer to the address of a new [IHostSecurityContext](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritycontext-interface.md) object.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="b675c-108">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="b675c-108">Return Value</span></span>  
  
|<span data-ttu-id="b675c-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="b675c-109">HRESULT</span></span>|<span data-ttu-id="b675c-110">Descrição</span><span class="sxs-lookup"><span data-stu-id="b675c-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="b675c-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="b675c-111">S_OK</span></span>|<span data-ttu-id="b675c-112">`SetSecurityContext` retornado com êxito.</span><span class="sxs-lookup"><span data-stu-id="b675c-112">`SetSecurityContext` returned successfully.</span></span>|  
|<span data-ttu-id="b675c-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="b675c-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="b675c-114">O CLR não tenha sido carregado em um processo ou o CLR está em um estado em que ele não pode executar o código gerenciado ou processar a chamada com êxito.</span><span class="sxs-lookup"><span data-stu-id="b675c-114">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="b675c-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="b675c-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="b675c-116">A chamada atingiu o tempo limite.</span><span class="sxs-lookup"><span data-stu-id="b675c-116">The call timed out.</span></span>|  
|<span data-ttu-id="b675c-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="b675c-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="b675c-118">O chamador não é proprietário do bloqueio.</span><span class="sxs-lookup"><span data-stu-id="b675c-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="b675c-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="b675c-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="b675c-120">Um evento foi cancelado enquanto um thread bloqueado ou fibra estava esperando por ele.</span><span class="sxs-lookup"><span data-stu-id="b675c-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="b675c-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="b675c-121">E_FAIL</span></span>|<span data-ttu-id="b675c-122">Ocorreu uma falha catastrófica desconhecida.</span><span class="sxs-lookup"><span data-stu-id="b675c-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="b675c-123">Quando um método retornar E_FAIL, o CLR não é mais utilizável dentro do processo.</span><span class="sxs-lookup"><span data-stu-id="b675c-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="b675c-124">As chamadas subsequentes à hospedagem de métodos de retorno HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="b675c-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b675c-125">Comentários</span><span class="sxs-lookup"><span data-stu-id="b675c-125">Remarks</span></span>  
 <span data-ttu-id="b675c-126">O CLR chama `SetSecurityContext` em vários cenários.</span><span class="sxs-lookup"><span data-stu-id="b675c-126">The CLR calls `SetSecurityContext` in several scenarios.</span></span> <span data-ttu-id="b675c-127">Antes que ele executa a classe e construtores de módulo e finalizadores, o CLR chama `SetSecurityContext` para proteger o host de falhas de execução.</span><span class="sxs-lookup"><span data-stu-id="b675c-127">Before it executes class and module constructors and finalizers, the CLR calls `SetSecurityContext` to protect the host from execution failures.</span></span> <span data-ttu-id="b675c-128">Ele, em seguida, redefine o contexto de segurança para seu estado original após a execução do construtor ou um finalizador, por meio de outra chamada para `SetSecurityContext`.</span><span class="sxs-lookup"><span data-stu-id="b675c-128">It then resets the security context to its original state after execution of the constructor or finalizer, by using another call to `SetSecurityContext`.</span></span> <span data-ttu-id="b675c-129">Um padrão semelhante ocorre com a conclusão de e/s.</span><span class="sxs-lookup"><span data-stu-id="b675c-129">A similar pattern occurs with I/O completion.</span></span> <span data-ttu-id="b675c-130">Se o host implementa [IHostIoCompletionManager](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-interface.md), o CLR chama `SetSecurityContext` após o host chama [iclriocompletionmanager:: onComplete](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-oncomplete-method.md).</span><span class="sxs-lookup"><span data-stu-id="b675c-130">If the host implements [IHostIoCompletionManager](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-interface.md), the CLR calls `SetSecurityContext` after the host calls [ICLRIoCompletionManager::OnComplete](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-oncomplete-method.md).</span></span>  
  
 <span data-ttu-id="b675c-131">Em pontos assíncronos nos threads de trabalho, o CLR chama `SetSecurityContext` dentro de <xref:System.Threading.ThreadPool.QueueUserWorkItem%2A?displayProperty=nameWithType> ou dentro [ihostthreadpoolmanager:: QueueUserWorkItem](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-queueuserworkitem-method.md), dependendo se o host ou o CLR está implementando o pool de threads.</span><span class="sxs-lookup"><span data-stu-id="b675c-131">At asynchronous points in worker threads, the CLR calls `SetSecurityContext` within <xref:System.Threading.ThreadPool.QueueUserWorkItem%2A?displayProperty=nameWithType> or within [IHostThreadPoolManager::QueueUserWorkItem](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-queueuserworkitem-method.md), depending on whether the host or the CLR is implementing the thread pool.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b675c-132">Requisitos</span><span class="sxs-lookup"><span data-stu-id="b675c-132">Requirements</span></span>  
 <span data-ttu-id="b675c-133">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b675c-133">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b675c-134">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="b675c-134">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="b675c-135">**Biblioteca:** Incluído como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="b675c-135">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="b675c-136">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b675c-136">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b675c-137">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b675c-137">See also</span></span>
- <xref:System.Threading.ThreadPool?displayProperty=nameWithType>
- [<span data-ttu-id="b675c-138">Enumeração EContextType</span><span class="sxs-lookup"><span data-stu-id="b675c-138">EContextType Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/econtexttype-enumeration.md)
- [<span data-ttu-id="b675c-139">Interface ICLRIoCompletionManager</span><span class="sxs-lookup"><span data-stu-id="b675c-139">ICLRIoCompletionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-interface.md)
- [<span data-ttu-id="b675c-140">Interface IHostIoCompletionManager</span><span class="sxs-lookup"><span data-stu-id="b675c-140">IHostIoCompletionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-interface.md)
- [<span data-ttu-id="b675c-141">Interface IHostSecurityContext</span><span class="sxs-lookup"><span data-stu-id="b675c-141">IHostSecurityContext Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritycontext-interface.md)
- [<span data-ttu-id="b675c-142">Interface IHostSecurityManager</span><span class="sxs-lookup"><span data-stu-id="b675c-142">IHostSecurityManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-interface.md)
- [<span data-ttu-id="b675c-143">Interface IHostThreadPoolManager</span><span class="sxs-lookup"><span data-stu-id="b675c-143">IHostThreadPoolManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-interface.md)
