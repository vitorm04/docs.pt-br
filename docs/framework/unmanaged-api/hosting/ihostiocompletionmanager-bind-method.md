---
title: "Método IHostIoCompletionManager::Bind"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
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
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: a34de8c04e248d2973e9b27c10da9313db5077ff
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="ihostiocompletionmanagerbind-method"></a><span data-ttu-id="f37a4-102">Método IHostIoCompletionManager::Bind</span><span class="sxs-lookup"><span data-stu-id="f37a4-102">IHostIoCompletionManager::Bind Method</span></span>
<span data-ttu-id="f37a4-103">Associa o identificador especificado para uma porta de conclusão de e/s que foi criada por uma chamada anterior para [CreateIoCompletionPort](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-createiocompletionport-method.md).</span><span class="sxs-lookup"><span data-stu-id="f37a4-103">Binds the specified handle to an I/O completion port that has been created by an earlier call to [CreateIoCompletionPort](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-createiocompletionport-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f37a4-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="f37a4-104">Syntax</span></span>  
  
```  
HRESULT Bind (  
    [in] HANDLE hPort,  
    [in] HANDLE hHandle  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="f37a4-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="f37a4-105">Parameters</span></span>  
 `hPort`  
 <span data-ttu-id="f37a4-106">[in] A porta de conclusão de e/s à qual associar `hHandle`.</span><span class="sxs-lookup"><span data-stu-id="f37a4-106">[in] The I/O completion port to which to bind `hHandle`.</span></span> <span data-ttu-id="f37a4-107">Se o valor de `hPort` for nulo, `hHandle` está associado à porta de conclusão de e/s padrão.</span><span class="sxs-lookup"><span data-stu-id="f37a4-107">If the value of `hPort` is null, `hHandle` is bound to the default I/O completion port.</span></span>  
  
 `hHandle`  
 <span data-ttu-id="f37a4-108">[in] O identificador de sistema operacional para associar a `hPort`.</span><span class="sxs-lookup"><span data-stu-id="f37a4-108">[in] The operating system handle to bind to `hPort`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="f37a4-109">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="f37a4-109">Return Value</span></span>  
  
|<span data-ttu-id="f37a4-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="f37a4-110">HRESULT</span></span>|<span data-ttu-id="f37a4-111">Descrição</span><span class="sxs-lookup"><span data-stu-id="f37a4-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="f37a4-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="f37a4-112">S_OK</span></span>|<span data-ttu-id="f37a4-113">`Bind`retornou com êxito.</span><span class="sxs-lookup"><span data-stu-id="f37a4-113">`Bind` returned successfully.</span></span>|  
|<span data-ttu-id="f37a4-114">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="f37a4-114">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="f37a4-115">O common language runtime (CLR) não foi carregado em um processo ou o CLR está em um estado em que ele não pode executar código gerenciado ou processar a chamada com êxito.</span><span class="sxs-lookup"><span data-stu-id="f37a4-115">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="f37a4-116">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="f37a4-116">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="f37a4-117">A chamada foi atingido.</span><span class="sxs-lookup"><span data-stu-id="f37a4-117">The call timed out.</span></span>|  
|<span data-ttu-id="f37a4-118">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="f37a4-118">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="f37a4-119">O chamador não possui o bloqueio.</span><span class="sxs-lookup"><span data-stu-id="f37a4-119">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="f37a4-120">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="f37a4-120">HOST_E_ABANDONED</span></span>|<span data-ttu-id="f37a4-121">Um evento foi cancelado durante um thread bloqueado ou fibra estava aguardando nele.</span><span class="sxs-lookup"><span data-stu-id="f37a4-121">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="f37a4-122">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="f37a4-122">E_FAIL</span></span>|<span data-ttu-id="f37a4-123">Ocorreu uma falha catastrófica desconhecida.</span><span class="sxs-lookup"><span data-stu-id="f37a4-123">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="f37a4-124">Quando um método retornará E_FAIL, o CLR não será mais utilizável dentro do processo.</span><span class="sxs-lookup"><span data-stu-id="f37a4-124">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="f37a4-125">As chamadas subsequentes para hospedagem métodos retornam HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="f37a4-125">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f37a4-126">Comentários</span><span class="sxs-lookup"><span data-stu-id="f37a4-126">Remarks</span></span>  
 <span data-ttu-id="f37a4-127">Uma porta de conclusão de e/s é criada usando uma chamada para `CreateIoCompletionPort`.</span><span class="sxs-lookup"><span data-stu-id="f37a4-127">An I/O completion port is created by using a call to `CreateIoCompletionPort`.</span></span> <span data-ttu-id="f37a4-128">O CLR chama `Bind` para associar um identificador para essa porta.</span><span class="sxs-lookup"><span data-stu-id="f37a4-128">The CLR calls `Bind` to bind a handle to that port.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="f37a4-129">Quando uma solicitação de e/s é concluída, o host deve chamar o [Iclriocompletionmanager](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-oncomplete-method.md) método.</span><span class="sxs-lookup"><span data-stu-id="f37a4-129">When an I/O request completes, the host must call the [ICLRIoCompletionManager::OnComplete](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-oncomplete-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f37a4-130">Requisitos</span><span class="sxs-lookup"><span data-stu-id="f37a4-130">Requirements</span></span>  
 <span data-ttu-id="f37a4-131">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f37a4-131">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f37a4-132">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="f37a4-132">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="f37a4-133">**Biblioteca:** incluído como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="f37a4-133">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="f37a4-134">**Versões do .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f37a4-134">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f37a4-135">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f37a4-135">See Also</span></span>  
 [<span data-ttu-id="f37a4-136">Interface ICLRIoCompletionManager</span><span class="sxs-lookup"><span data-stu-id="f37a4-136">ICLRIoCompletionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-interface.md)
