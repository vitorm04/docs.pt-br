---
title: Método IHostIoCompletionManager::SetMinThreads
ms.date: 03/30/2017
api_name:
- IHostIoCompletionManager.SetMinThreads
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostIoCompletionManager::SetMinThreads
helpviewer_keywords:
- SetMinThreads method, IHostIoCompletionManager interface [.NET Framework hosting]
- IHostIoCompletionManager::SetMinThreads method [.NET Framework hosting]
ms.assetid: dea34b81-8d2b-4cc3-8696-0ad4291d8a92
topic_type:
- apiref
ms.openlocfilehash: 29a2fc5652badcc00378192debccba0356f5339e
ms.sourcegitcommit: d223616e7e6fe2139079052e6fcbe25413fb9900
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/22/2020
ms.locfileid: "83804664"
---
# <a name="ihostiocompletionmanagersetminthreads-method"></a><span data-ttu-id="9a2de-102">Método IHostIoCompletionManager::SetMinThreads</span><span class="sxs-lookup"><span data-stu-id="9a2de-102">IHostIoCompletionManager::SetMinThreads Method</span></span>
<span data-ttu-id="9a2de-103">Define o número mínimo de threads que o host deve alocar para a conclusão de e/s.</span><span class="sxs-lookup"><span data-stu-id="9a2de-103">Sets the minimum number of threads that the host should allot to I/O completion.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9a2de-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="9a2de-104">Syntax</span></span>  
  
```cpp  
HRESULT SetMinThreads (  
    [in] DWORD dwMinIoCompletionThreads  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9a2de-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="9a2de-105">Parameters</span></span>  
 `dwMinIoCompletionThreads`  
 <span data-ttu-id="9a2de-106">no O número mínimo de threads de conclusão de e/s que o host deve criar.</span><span class="sxs-lookup"><span data-stu-id="9a2de-106">[in] The minimum number of I/O completion threads that the host should create.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="9a2de-107">Valor Retornado</span><span class="sxs-lookup"><span data-stu-id="9a2de-107">Return Value</span></span>  
  
|<span data-ttu-id="9a2de-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="9a2de-108">HRESULT</span></span>|<span data-ttu-id="9a2de-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="9a2de-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="9a2de-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="9a2de-110">S_OK</span></span>|<span data-ttu-id="9a2de-111">`SetMinThreads`retornado com êxito.</span><span class="sxs-lookup"><span data-stu-id="9a2de-111">`SetMinThreads` returned successfully.</span></span>|  
|<span data-ttu-id="9a2de-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="9a2de-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="9a2de-113">O Common Language Runtime (CLR) não foi carregado em um processo ou o CLR está em um estado no qual não pode executar código gerenciado ou processar a chamada com êxito.</span><span class="sxs-lookup"><span data-stu-id="9a2de-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="9a2de-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="9a2de-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="9a2de-115">A chamada atingiu o tempo limite.</span><span class="sxs-lookup"><span data-stu-id="9a2de-115">The call timed out.</span></span>|  
|<span data-ttu-id="9a2de-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="9a2de-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="9a2de-117">O chamador não possui o bloqueio.</span><span class="sxs-lookup"><span data-stu-id="9a2de-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="9a2de-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="9a2de-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="9a2de-119">Um evento foi cancelado enquanto um thread ou uma fibra bloqueada estava esperando.</span><span class="sxs-lookup"><span data-stu-id="9a2de-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="9a2de-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="9a2de-120">E_FAIL</span></span>|<span data-ttu-id="9a2de-121">Ocorreu uma falha catastrófica desconhecida.</span><span class="sxs-lookup"><span data-stu-id="9a2de-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="9a2de-122">Quando um método retorna E_FAIL, o CLR não é mais utilizável no processo.</span><span class="sxs-lookup"><span data-stu-id="9a2de-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="9a2de-123">As chamadas subsequentes para métodos de hospedagem retornam HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="9a2de-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="9a2de-124">E_NOTIMPL</span><span class="sxs-lookup"><span data-stu-id="9a2de-124">E_NOTIMPL</span></span>|<span data-ttu-id="9a2de-125">O host não fornece uma implementação de `SetMinThreads` .</span><span class="sxs-lookup"><span data-stu-id="9a2de-125">The host does not provide an implementation of `SetMinThreads`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9a2de-126">Comentários</span><span class="sxs-lookup"><span data-stu-id="9a2de-126">Remarks</span></span>  
 <span data-ttu-id="9a2de-127">Um host pode querer um controle exclusivo sobre o número de threads que podem ser alocados para processar solicitações de e/s, por motivos como implementação, desempenho ou escalabilidade.</span><span class="sxs-lookup"><span data-stu-id="9a2de-127">A host might want exclusive control over the number of threads that can be allotted to process I/O requests, for reasons such as implementation, performance, or scalability.</span></span> <span data-ttu-id="9a2de-128">Por esse motivo, o host não precisa implementar `SetMinThreads` .</span><span class="sxs-lookup"><span data-stu-id="9a2de-128">For this reason, the host is not required to implement `SetMinThreads`.</span></span> <span data-ttu-id="9a2de-129">Nesse caso, o host deve retornar E_NOTIMPL desse método.</span><span class="sxs-lookup"><span data-stu-id="9a2de-129">In this case, the host should return E_NOTIMPL from this method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9a2de-130">Requisitos</span><span class="sxs-lookup"><span data-stu-id="9a2de-130">Requirements</span></span>  
 <span data-ttu-id="9a2de-131">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9a2de-131">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9a2de-132">**Cabeçalho:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="9a2de-132">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="9a2de-133">**Biblioteca:** Incluído como um recurso em MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="9a2de-133">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="9a2de-134">**.NET Framework versões:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9a2de-134">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9a2de-135">Confira também</span><span class="sxs-lookup"><span data-stu-id="9a2de-135">See also</span></span>

- [<span data-ttu-id="9a2de-136">Interface ICLRIoCompletionManager</span><span class="sxs-lookup"><span data-stu-id="9a2de-136">ICLRIoCompletionManager Interface</span></span>](iclriocompletionmanager-interface.md)
- [<span data-ttu-id="9a2de-137">Método SetMaxThreads</span><span class="sxs-lookup"><span data-stu-id="9a2de-137">SetMaxThreads Method</span></span>](ihostiocompletionmanager-setmaxthreads-method.md)
- [<span data-ttu-id="9a2de-138">Interface IHostIoCompletionManager</span><span class="sxs-lookup"><span data-stu-id="9a2de-138">IHostIoCompletionManager Interface</span></span>](ihostiocompletionmanager-interface.md)
