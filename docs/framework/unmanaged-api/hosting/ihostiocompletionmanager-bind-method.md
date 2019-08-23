---
title: Método IHostIoCompletionManager::Bind
ms.date: 03/30/2017
api_name:
- IHostIoCompletionManager.Bind
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostIoCompletionManager::Bind
helpviewer_keywords:
- IHostIoCompletionManager::Bind method [.NET Framework hosting]
- Bind method [.NET Framework hosting]
ms.assetid: acd74cb5-7e22-4a07-83c3-82288e1abd9f
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: de39de96cd7c7ba0be2dc1bea78f79cfe996575c
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69937560"
---
# <a name="ihostiocompletionmanagerbind-method"></a><span data-ttu-id="981af-102">Método IHostIoCompletionManager::Bind</span><span class="sxs-lookup"><span data-stu-id="981af-102">IHostIoCompletionManager::Bind Method</span></span>
<span data-ttu-id="981af-103">Associa o identificador especificado a uma porta de conclusão de e/s que foi criada por uma chamada anterior ao [CreateIoCompletionPort](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-createiocompletionport-method.md).</span><span class="sxs-lookup"><span data-stu-id="981af-103">Binds the specified handle to an I/O completion port that has been created by an earlier call to [CreateIoCompletionPort](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-createiocompletionport-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="981af-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="981af-104">Syntax</span></span>  
  
```cpp  
HRESULT Bind (  
    [in] HANDLE hPort,  
    [in] HANDLE hHandle  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="981af-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="981af-105">Parameters</span></span>  
 `hPort`  
 <span data-ttu-id="981af-106">no A porta de conclusão de e/s à qual `hHandle`associar.</span><span class="sxs-lookup"><span data-stu-id="981af-106">[in] The I/O completion port to which to bind `hHandle`.</span></span> <span data-ttu-id="981af-107">Se o valor de `hPort` for NULL, `hHandle` será associado à porta de conclusão de e/s padrão.</span><span class="sxs-lookup"><span data-stu-id="981af-107">If the value of `hPort` is null, `hHandle` is bound to the default I/O completion port.</span></span>  
  
 `hHandle`  
 <span data-ttu-id="981af-108">no O identificador do sistema operacional a ser `hPort`associado.</span><span class="sxs-lookup"><span data-stu-id="981af-108">[in] The operating system handle to bind to `hPort`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="981af-109">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="981af-109">Return Value</span></span>  
  
|<span data-ttu-id="981af-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="981af-110">HRESULT</span></span>|<span data-ttu-id="981af-111">Descrição</span><span class="sxs-lookup"><span data-stu-id="981af-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="981af-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="981af-112">S_OK</span></span>|<span data-ttu-id="981af-113">`Bind`retornado com êxito.</span><span class="sxs-lookup"><span data-stu-id="981af-113">`Bind` returned successfully.</span></span>|  
|<span data-ttu-id="981af-114">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="981af-114">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="981af-115">O Common Language Runtime (CLR) não foi carregado em um processo ou o CLR está em um estado no qual não pode executar código gerenciado ou processar a chamada com êxito.</span><span class="sxs-lookup"><span data-stu-id="981af-115">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="981af-116">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="981af-116">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="981af-117">A chamada atingiu o tempo limite.</span><span class="sxs-lookup"><span data-stu-id="981af-117">The call timed out.</span></span>|  
|<span data-ttu-id="981af-118">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="981af-118">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="981af-119">O chamador não possui o bloqueio.</span><span class="sxs-lookup"><span data-stu-id="981af-119">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="981af-120">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="981af-120">HOST_E_ABANDONED</span></span>|<span data-ttu-id="981af-121">Um evento foi cancelado enquanto um thread ou uma fibra bloqueada estava esperando.</span><span class="sxs-lookup"><span data-stu-id="981af-121">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="981af-122">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="981af-122">E_FAIL</span></span>|<span data-ttu-id="981af-123">Ocorreu uma falha catastrófica desconhecida.</span><span class="sxs-lookup"><span data-stu-id="981af-123">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="981af-124">Quando um método retorna E_FAIL, o CLR não é mais utilizável no processo.</span><span class="sxs-lookup"><span data-stu-id="981af-124">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="981af-125">As chamadas subsequentes para métodos de hospedagem retornam HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="981af-125">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="981af-126">Comentários</span><span class="sxs-lookup"><span data-stu-id="981af-126">Remarks</span></span>  
 <span data-ttu-id="981af-127">Uma porta de conclusão de e/s é criada usando uma chamada `CreateIoCompletionPort`para.</span><span class="sxs-lookup"><span data-stu-id="981af-127">An I/O completion port is created by using a call to `CreateIoCompletionPort`.</span></span> <span data-ttu-id="981af-128">O CLR chama `Bind` para associar um identificador a essa porta.</span><span class="sxs-lookup"><span data-stu-id="981af-128">The CLR calls `Bind` to bind a handle to that port.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="981af-129">Quando uma solicitação de e/s é concluída, o host deve chamar o método [ICLRIoCompletionManager:: OnComplete](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-oncomplete-method.md) .</span><span class="sxs-lookup"><span data-stu-id="981af-129">When an I/O request completes, the host must call the [ICLRIoCompletionManager::OnComplete](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-oncomplete-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="981af-130">Requisitos</span><span class="sxs-lookup"><span data-stu-id="981af-130">Requirements</span></span>  
 <span data-ttu-id="981af-131">**Compatíveis** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="981af-131">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="981af-132">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="981af-132">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="981af-133">**Biblioteca** Incluído como um recurso em MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="981af-133">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="981af-134">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="981af-134">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="981af-135">Consulte também</span><span class="sxs-lookup"><span data-stu-id="981af-135">See also</span></span>

- [<span data-ttu-id="981af-136">Interface ICLRIoCompletionManager</span><span class="sxs-lookup"><span data-stu-id="981af-136">ICLRIoCompletionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-interface.md)
