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
ms.openlocfilehash: 254254af705f93793b030882e0ac79d0372ca55f
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73133889"
---
# <a name="ihostiocompletionmanagercloseiocompletionport-method"></a><span data-ttu-id="1b338-102">Método IHostIoCompletionManager::CloseIoCompletionPort</span><span class="sxs-lookup"><span data-stu-id="1b338-102">IHostIoCompletionManager::CloseIoCompletionPort Method</span></span>
<span data-ttu-id="1b338-103">Solicita que o host feche uma porta que foi aberta por meio de uma chamada anterior para [CreateIoCompletionPort](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-createiocompletionport-method.md).</span><span class="sxs-lookup"><span data-stu-id="1b338-103">Requests that the host close a port that was opened through an earlier call to [CreateIoCompletionPort](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-createiocompletionport-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1b338-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="1b338-104">Syntax</span></span>  
  
```cpp  
HRESULT CloseIoCompletionPort (  
    [in] HANDLE hPort  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1b338-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="1b338-105">Parameters</span></span>  
 `hPort`  
 <span data-ttu-id="1b338-106">no O identificador da porta a ser fechada.</span><span class="sxs-lookup"><span data-stu-id="1b338-106">[in] The handle of the port to close.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="1b338-107">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="1b338-107">Return Value</span></span>  
  
|<span data-ttu-id="1b338-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="1b338-108">HRESULT</span></span>|<span data-ttu-id="1b338-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="1b338-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="1b338-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="1b338-110">S_OK</span></span>|<span data-ttu-id="1b338-111">`CloseIoCompletionPort` retornado com êxito.</span><span class="sxs-lookup"><span data-stu-id="1b338-111">`CloseIoCompletionPort` returned successfully.</span></span>|  
|<span data-ttu-id="1b338-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="1b338-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="1b338-113">O Common Language Runtime (CLR) não foi carregado em um processo ou o CLR está em um estado no qual não pode executar código gerenciado ou processar a chamada com êxito.</span><span class="sxs-lookup"><span data-stu-id="1b338-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="1b338-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="1b338-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="1b338-115">A chamada atingiu o tempo limite.</span><span class="sxs-lookup"><span data-stu-id="1b338-115">The call timed out.</span></span>|  
|<span data-ttu-id="1b338-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="1b338-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="1b338-117">O chamador não possui o bloqueio.</span><span class="sxs-lookup"><span data-stu-id="1b338-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="1b338-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="1b338-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="1b338-119">Um evento foi cancelado enquanto um thread ou uma fibra bloqueada estava esperando.</span><span class="sxs-lookup"><span data-stu-id="1b338-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="1b338-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="1b338-120">E_FAIL</span></span>|<span data-ttu-id="1b338-121">Ocorreu uma falha catastrófica desconhecida.</span><span class="sxs-lookup"><span data-stu-id="1b338-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="1b338-122">Quando um método retorna E_FAIL, o CLR não é mais utilizável no processo.</span><span class="sxs-lookup"><span data-stu-id="1b338-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="1b338-123">As chamadas subsequentes para métodos de hospedagem retornam HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="1b338-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="1b338-124">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="1b338-124">E_INVALIDARG</span></span>|<span data-ttu-id="1b338-125">Um identificador de porta inválido foi passado.</span><span class="sxs-lookup"><span data-stu-id="1b338-125">An invalid port handle was passed.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1b338-126">Comentários</span><span class="sxs-lookup"><span data-stu-id="1b338-126">Remarks</span></span>  
 <span data-ttu-id="1b338-127">`hPort` deve ser um identificador para uma porta que foi criada por uma chamada anterior para `CreateIoCompletionPort`.</span><span class="sxs-lookup"><span data-stu-id="1b338-127">`hPort` must be a handle to a port that was created by an earlier call to `CreateIoCompletionPort`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1b338-128">Requisitos</span><span class="sxs-lookup"><span data-stu-id="1b338-128">Requirements</span></span>  
 <span data-ttu-id="1b338-129">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1b338-129">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1b338-130">**Cabeçalho:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="1b338-130">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="1b338-131">**Biblioteca:** Incluído como um recurso em MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="1b338-131">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="1b338-132">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1b338-132">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1b338-133">Consulte também</span><span class="sxs-lookup"><span data-stu-id="1b338-133">See also</span></span>

- [<span data-ttu-id="1b338-134">Interface ICLRIoCompletionManager</span><span class="sxs-lookup"><span data-stu-id="1b338-134">ICLRIoCompletionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-interface.md)
- [<span data-ttu-id="1b338-135">Interface IHostIoCompletionManager</span><span class="sxs-lookup"><span data-stu-id="1b338-135">IHostIoCompletionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-interface.md)
