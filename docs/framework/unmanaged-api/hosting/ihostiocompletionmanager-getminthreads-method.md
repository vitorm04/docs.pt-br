---
title: Método IHostIoCompletionManager::GetMinThreads
ms.date: 03/30/2017
api_name:
- IHostIoCompletionManager.GetMinThreads
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostIoCompletionManager::GetMinThreads
helpviewer_keywords:
- GetMinThreads method, IHostIoCompletionManager interface [.NET Framework hosting]
- IHostIoCompletionManager::GetMinThreads method [.NET Framework hosting]
ms.assetid: d7a7f733-677d-481c-b3d5-444fcc502b8e
topic_type:
- apiref
ms.openlocfilehash: e748a731f2c6934f58a1cd838cc40ce4fd0e4652
ms.sourcegitcommit: d223616e7e6fe2139079052e6fcbe25413fb9900
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/22/2020
ms.locfileid: "83804727"
---
# <a name="ihostiocompletionmanagergetminthreads-method"></a><span data-ttu-id="144ff-102">Método IHostIoCompletionManager::GetMinThreads</span><span class="sxs-lookup"><span data-stu-id="144ff-102">IHostIoCompletionManager::GetMinThreads Method</span></span>
<span data-ttu-id="144ff-103">Obtém o número mínimo de threads que o host fornece para processar solicitações de e/s.</span><span class="sxs-lookup"><span data-stu-id="144ff-103">Gets the minimum number of threads that the host provides for processing I/O requests.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="144ff-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="144ff-104">Syntax</span></span>  
  
```cpp  
HRESULT GetMinThreads (  
    [out] DWORD *pdwMinIOCompletionThreads  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="144ff-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="144ff-105">Parameters</span></span>  
 `pdwMinIOCompletionThreads`  
 <span data-ttu-id="144ff-106">fora Um ponteiro para o número mínimo de threads que o host fornece para processar solicitações de e/s.</span><span class="sxs-lookup"><span data-stu-id="144ff-106">[out] A pointer to the minimum number of threads that the host provides to process I/O requests.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="144ff-107">Valor Retornado</span><span class="sxs-lookup"><span data-stu-id="144ff-107">Return Value</span></span>  
  
|<span data-ttu-id="144ff-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="144ff-108">HRESULT</span></span>|<span data-ttu-id="144ff-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="144ff-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="144ff-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="144ff-110">S_OK</span></span>|<span data-ttu-id="144ff-111">`GetMinThreads`retornado com êxito.</span><span class="sxs-lookup"><span data-stu-id="144ff-111">`GetMinThreads` returned successfully.</span></span>|  
|<span data-ttu-id="144ff-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="144ff-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="144ff-113">O Common Language Runtime (CLR) não foi carregado em um processo ou o CLR está em um estado no qual não pode executar código gerenciado ou processar a chamada com êxito.</span><span class="sxs-lookup"><span data-stu-id="144ff-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="144ff-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="144ff-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="144ff-115">A chamada atingiu o tempo limite.</span><span class="sxs-lookup"><span data-stu-id="144ff-115">The call timed out.</span></span>|  
|<span data-ttu-id="144ff-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="144ff-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="144ff-117">O chamador não possui o bloqueio.</span><span class="sxs-lookup"><span data-stu-id="144ff-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="144ff-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="144ff-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="144ff-119">Um evento foi cancelado enquanto um thread ou uma fibra bloqueada estava esperando.</span><span class="sxs-lookup"><span data-stu-id="144ff-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="144ff-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="144ff-120">E_FAIL</span></span>|<span data-ttu-id="144ff-121">Ocorreu uma falha catastrófica desconhecida.</span><span class="sxs-lookup"><span data-stu-id="144ff-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="144ff-122">Quando um método retorna E_FAIL, o CLR não é mais utilizável no processo.</span><span class="sxs-lookup"><span data-stu-id="144ff-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="144ff-123">As chamadas subsequentes para métodos de hospedagem retornam HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="144ff-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="144ff-124">E_NOTIMPL</span><span class="sxs-lookup"><span data-stu-id="144ff-124">E_NOTIMPL</span></span>|<span data-ttu-id="144ff-125">O host não fornece uma implementação de `GetMinThreads` .</span><span class="sxs-lookup"><span data-stu-id="144ff-125">The host does not provide an implementation of `GetMinThreads`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="144ff-126">Comentários</span><span class="sxs-lookup"><span data-stu-id="144ff-126">Remarks</span></span>  
 <span data-ttu-id="144ff-127">Um host pode querer um controle exclusivo sobre o número de threads alocados para solicitações de e/s de serviço, por motivos como implementação, desempenho ou escalabilidade.</span><span class="sxs-lookup"><span data-stu-id="144ff-127">A host might want exclusive control over the number of threads allotted to service I/O requests, for reasons such as implementation, performance, or scalability.</span></span> <span data-ttu-id="144ff-128">Por esse motivo, o host não precisa implementar `GetMinThreads` .</span><span class="sxs-lookup"><span data-stu-id="144ff-128">For this reason, the host is not required to implement `GetMinThreads`.</span></span> <span data-ttu-id="144ff-129">Nesse caso, o host deve retornar E_NOTIMPL desse método.</span><span class="sxs-lookup"><span data-stu-id="144ff-129">In this case, the host should return E_NOTIMPL from this method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="144ff-130">Requisitos</span><span class="sxs-lookup"><span data-stu-id="144ff-130">Requirements</span></span>  
 <span data-ttu-id="144ff-131">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="144ff-131">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="144ff-132">**Cabeçalho:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="144ff-132">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="144ff-133">**Biblioteca:** Incluído como um recurso em MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="144ff-133">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="144ff-134">**.NET Framework versões:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="144ff-134">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="144ff-135">Confira também</span><span class="sxs-lookup"><span data-stu-id="144ff-135">See also</span></span>

- [<span data-ttu-id="144ff-136">Interface ICLRIoCompletionManager</span><span class="sxs-lookup"><span data-stu-id="144ff-136">ICLRIoCompletionManager Interface</span></span>](iclriocompletionmanager-interface.md)
- [<span data-ttu-id="144ff-137">Interface IHostIoCompletionManager</span><span class="sxs-lookup"><span data-stu-id="144ff-137">IHostIoCompletionManager Interface</span></span>](ihostiocompletionmanager-interface.md)
