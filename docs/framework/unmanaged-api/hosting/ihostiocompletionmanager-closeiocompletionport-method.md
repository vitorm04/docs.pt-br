---
title: Método IHostIoCompletionManager::CloseIoCompletionPort
ms.date: 03/30/2017
api_name:
- IHostIoCompletionManager.CloseIoCompletionPort
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostIoCompletionManager::CloseIoCompletionPort
helpviewer_keywords:
- IHostIoCompletionManager::CloseIoCompletionPort method [.NET Framework hosting]
- CloseIoCompletionPort method [.NET Framework hosting]
ms.assetid: e86ad7be-3758-498a-a972-5522d69dfbb3
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 761e3b22014bdd628ffc6763615a285a16a86309
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33441763"
---
# <a name="ihostiocompletionmanagercloseiocompletionport-method"></a><span data-ttu-id="c4b94-102">Método IHostIoCompletionManager::CloseIoCompletionPort</span><span class="sxs-lookup"><span data-stu-id="c4b94-102">IHostIoCompletionManager::CloseIoCompletionPort Method</span></span>
<span data-ttu-id="c4b94-103">Solicita que o host fecha uma porta que foi aberta por meio de uma chamada anterior para [CreateIoCompletionPort](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-createiocompletionport-method.md).</span><span class="sxs-lookup"><span data-stu-id="c4b94-103">Requests that the host close a port that was opened through an earlier call to [CreateIoCompletionPort](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-createiocompletionport-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c4b94-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="c4b94-104">Syntax</span></span>  
  
```  
HRESULT CloseIoCompletionPort (  
    [in] HANDLE hPort  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="c4b94-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="c4b94-105">Parameters</span></span>  
 `hPort`  
 <span data-ttu-id="c4b94-106">[in] O identificador da porta para fechar.</span><span class="sxs-lookup"><span data-stu-id="c4b94-106">[in] The handle of the port to close.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="c4b94-107">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="c4b94-107">Return Value</span></span>  
  
|<span data-ttu-id="c4b94-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="c4b94-108">HRESULT</span></span>|<span data-ttu-id="c4b94-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="c4b94-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="c4b94-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="c4b94-110">S_OK</span></span>|<span data-ttu-id="c4b94-111">`CloseIoCompletionPort` retornou com êxito.</span><span class="sxs-lookup"><span data-stu-id="c4b94-111">`CloseIoCompletionPort` returned successfully.</span></span>|  
|<span data-ttu-id="c4b94-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="c4b94-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="c4b94-113">O common language runtime (CLR) não foi carregado em um processo ou o CLR está em um estado em que ele não pode executar código gerenciado ou processar a chamada com êxito.</span><span class="sxs-lookup"><span data-stu-id="c4b94-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="c4b94-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="c4b94-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="c4b94-115">A chamada foi atingido.</span><span class="sxs-lookup"><span data-stu-id="c4b94-115">The call timed out.</span></span>|  
|<span data-ttu-id="c4b94-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="c4b94-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="c4b94-117">O chamador não possui o bloqueio.</span><span class="sxs-lookup"><span data-stu-id="c4b94-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="c4b94-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="c4b94-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="c4b94-119">Um evento foi cancelado durante um thread bloqueado ou fibra estava aguardando nele.</span><span class="sxs-lookup"><span data-stu-id="c4b94-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="c4b94-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="c4b94-120">E_FAIL</span></span>|<span data-ttu-id="c4b94-121">Ocorreu uma falha catastrófica desconhecida.</span><span class="sxs-lookup"><span data-stu-id="c4b94-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="c4b94-122">Quando um método retornará E_FAIL, o CLR não será mais utilizável dentro do processo.</span><span class="sxs-lookup"><span data-stu-id="c4b94-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="c4b94-123">As chamadas subsequentes para hospedagem métodos retornam HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="c4b94-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="c4b94-124">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="c4b94-124">E_INVALIDARG</span></span>|<span data-ttu-id="c4b94-125">Um identificador de porta inválido foi passado.</span><span class="sxs-lookup"><span data-stu-id="c4b94-125">An invalid port handle was passed.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c4b94-126">Comentários</span><span class="sxs-lookup"><span data-stu-id="c4b94-126">Remarks</span></span>  
 <span data-ttu-id="c4b94-127">`hPort` deve ser um identificador para uma porta que foi criado por uma chamada anterior para `CreateIoCompletionPort`.</span><span class="sxs-lookup"><span data-stu-id="c4b94-127">`hPort` must be a handle to a port that was created by an earlier call to `CreateIoCompletionPort`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c4b94-128">Requisitos</span><span class="sxs-lookup"><span data-stu-id="c4b94-128">Requirements</span></span>  
 <span data-ttu-id="c4b94-129">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c4b94-129">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c4b94-130">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="c4b94-130">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="c4b94-131">**Biblioteca:** incluído como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="c4b94-131">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="c4b94-132">**Versões do .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c4b94-132">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c4b94-133">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c4b94-133">See Also</span></span>  
 [<span data-ttu-id="c4b94-134">Interface ICLRIoCompletionManager</span><span class="sxs-lookup"><span data-stu-id="c4b94-134">ICLRIoCompletionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-interface.md)  
 [<span data-ttu-id="c4b94-135">Interface IHostIoCompletionManager</span><span class="sxs-lookup"><span data-stu-id="c4b94-135">IHostIoCompletionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-interface.md)
