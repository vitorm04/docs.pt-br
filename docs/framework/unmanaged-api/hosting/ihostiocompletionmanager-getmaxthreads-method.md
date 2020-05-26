---
title: Método IHostIoCompletionManager::GetMaxThreads
ms.date: 03/30/2017
api_name:
- IHostIoCompletionManager.GetMaxThreads
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostIoCompletionManager::GetMaxThreads
helpviewer_keywords:
- IHostIoCompletionManager::GetMaxThreads method [.NET Framework hosting]
- GetMaxThreads method, IHostIoCompletionManager interface [.NET Framework hosting]
ms.assetid: e7a6cadc-2433-4472-a701-58891abcde45
topic_type:
- apiref
ms.openlocfilehash: a97a7abf4f561a5aba41d8019f2ba5bd8e879acd
ms.sourcegitcommit: d223616e7e6fe2139079052e6fcbe25413fb9900
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/22/2020
ms.locfileid: "83804733"
---
# <a name="ihostiocompletionmanagergetmaxthreads-method"></a><span data-ttu-id="a7d4b-102">Método IHostIoCompletionManager::GetMaxThreads</span><span class="sxs-lookup"><span data-stu-id="a7d4b-102">IHostIoCompletionManager::GetMaxThreads Method</span></span>
<span data-ttu-id="a7d4b-103">Obtém o número máximo de threads que o host pode alocar para solicitações de e/s de serviço.</span><span class="sxs-lookup"><span data-stu-id="a7d4b-103">Gets the maximum number of threads that the host can allot to service I/O requests.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a7d4b-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="a7d4b-104">Syntax</span></span>  
  
```cpp  
HRESULT GetMaxThreads (  
    [out] DWORD *pdwMaxIoCompletionThreads  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a7d4b-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="a7d4b-105">Parameters</span></span>  
 `pdwMaxIoCompletionThreads`  
 <span data-ttu-id="a7d4b-106">fora Um ponteiro para o número máximo de threads no pool de threads que o host pode alocar para solicitações de e/s de serviço.</span><span class="sxs-lookup"><span data-stu-id="a7d4b-106">[out] A pointer to the maximum number of threads in the thread pool that the host can allot to service I/O requests.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="a7d4b-107">Valor Retornado</span><span class="sxs-lookup"><span data-stu-id="a7d4b-107">Return Value</span></span>  
  
|<span data-ttu-id="a7d4b-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="a7d4b-108">HRESULT</span></span>|<span data-ttu-id="a7d4b-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="a7d4b-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="a7d4b-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="a7d4b-110">S_OK</span></span>|<span data-ttu-id="a7d4b-111">`GetMaxThreads`retornado com êxito.</span><span class="sxs-lookup"><span data-stu-id="a7d4b-111">`GetMaxThreads` returned successfully.</span></span>|  
|<span data-ttu-id="a7d4b-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="a7d4b-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="a7d4b-113">O Common Language Runtime (CLR) não foi carregado em um processo ou o CLR está em um estado no qual não pode executar código gerenciado ou processar a chamada com êxito.</span><span class="sxs-lookup"><span data-stu-id="a7d4b-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="a7d4b-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="a7d4b-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="a7d4b-115">A chamada atingiu o tempo limite.</span><span class="sxs-lookup"><span data-stu-id="a7d4b-115">The call timed out.</span></span>|  
|<span data-ttu-id="a7d4b-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="a7d4b-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="a7d4b-117">O chamador não possui o bloqueio.</span><span class="sxs-lookup"><span data-stu-id="a7d4b-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="a7d4b-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="a7d4b-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="a7d4b-119">Um evento foi cancelado enquanto um thread ou uma fibra bloqueada estava esperando.</span><span class="sxs-lookup"><span data-stu-id="a7d4b-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="a7d4b-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="a7d4b-120">E_FAIL</span></span>|<span data-ttu-id="a7d4b-121">Ocorreu uma falha catastrófica desconhecida.</span><span class="sxs-lookup"><span data-stu-id="a7d4b-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="a7d4b-122">Quando um método retorna E_FAIL, o CLR não é mais utilizável no processo.</span><span class="sxs-lookup"><span data-stu-id="a7d4b-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="a7d4b-123">As chamadas subsequentes para métodos de hospedagem retornam HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="a7d4b-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="a7d4b-124">E_NOTIMPL</span><span class="sxs-lookup"><span data-stu-id="a7d4b-124">E_NOTIMPL</span></span>|<span data-ttu-id="a7d4b-125">O host não fornece uma implementação de `GetMaxThreads` .</span><span class="sxs-lookup"><span data-stu-id="a7d4b-125">The host does not provide an implementation of `GetMaxThreads`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a7d4b-126">Comentários</span><span class="sxs-lookup"><span data-stu-id="a7d4b-126">Remarks</span></span>  
 <span data-ttu-id="a7d4b-127">Um host pode querer um controle exclusivo sobre o número de threads que podem ser alocados para processar solicitações de e/s, por motivos como implementação, desempenho ou escalabilidade.</span><span class="sxs-lookup"><span data-stu-id="a7d4b-127">A host might want exclusive control over the number of threads that can be allotted to process I/O requests, for reasons such as implementation, performance, or scalability.</span></span> <span data-ttu-id="a7d4b-128">Por esse motivo, o host não precisa implementar `GetMaxThreads` .</span><span class="sxs-lookup"><span data-stu-id="a7d4b-128">For this reason, the host is not required to implement `GetMaxThreads`.</span></span> <span data-ttu-id="a7d4b-129">Nesse caso, o host deve retornar E_NOTIMPL desse método.</span><span class="sxs-lookup"><span data-stu-id="a7d4b-129">In this case, the host should return E_NOTIMPL from this method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a7d4b-130">Requisitos</span><span class="sxs-lookup"><span data-stu-id="a7d4b-130">Requirements</span></span>  
 <span data-ttu-id="a7d4b-131">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a7d4b-131">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a7d4b-132">**Cabeçalho:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="a7d4b-132">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="a7d4b-133">**Biblioteca:** Incluído como um recurso em MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="a7d4b-133">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="a7d4b-134">**.NET Framework versões:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a7d4b-134">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a7d4b-135">Confira também</span><span class="sxs-lookup"><span data-stu-id="a7d4b-135">See also</span></span>

- [<span data-ttu-id="a7d4b-136">Interface ICLRIoCompletionManager</span><span class="sxs-lookup"><span data-stu-id="a7d4b-136">ICLRIoCompletionManager Interface</span></span>](iclriocompletionmanager-interface.md)
- [<span data-ttu-id="a7d4b-137">Interface IHostIoCompletionManager</span><span class="sxs-lookup"><span data-stu-id="a7d4b-137">IHostIoCompletionManager Interface</span></span>](ihostiocompletionmanager-interface.md)
