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
ms.openlocfilehash: 32a7c8b1c1c61eddb18ade1e77af5ea973fbaadc
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59107556"
---
# <a name="ihostiocompletionmanagercloseiocompletionport-method"></a><span data-ttu-id="678d7-102">Método IHostIoCompletionManager::CloseIoCompletionPort</span><span class="sxs-lookup"><span data-stu-id="678d7-102">IHostIoCompletionManager::CloseIoCompletionPort Method</span></span>
<span data-ttu-id="678d7-103">Solicita que o host Feche uma porta que foi aberta por meio de uma chamada anterior para [CreateIoCompletionPort](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-createiocompletionport-method.md).</span><span class="sxs-lookup"><span data-stu-id="678d7-103">Requests that the host close a port that was opened through an earlier call to [CreateIoCompletionPort](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-createiocompletionport-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="678d7-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="678d7-104">Syntax</span></span>  
  
```  
HRESULT CloseIoCompletionPort (  
    [in] HANDLE hPort  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="678d7-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="678d7-105">Parameters</span></span>  
 `hPort`  
 <span data-ttu-id="678d7-106">[in] O identificador da porta para fechar.</span><span class="sxs-lookup"><span data-stu-id="678d7-106">[in] The handle of the port to close.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="678d7-107">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="678d7-107">Return Value</span></span>  
  
|<span data-ttu-id="678d7-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="678d7-108">HRESULT</span></span>|<span data-ttu-id="678d7-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="678d7-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="678d7-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="678d7-110">S_OK</span></span>|`CloseIoCompletionPort` <span data-ttu-id="678d7-111">retornado com êxito.</span><span class="sxs-lookup"><span data-stu-id="678d7-111">returned successfully.</span></span>|  
|<span data-ttu-id="678d7-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="678d7-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="678d7-113">O common language runtime (CLR) não foi carregado em um processo ou o CLR está em um estado em que ele não pode executar o código gerenciado ou processar a chamada com êxito.</span><span class="sxs-lookup"><span data-stu-id="678d7-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="678d7-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="678d7-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="678d7-115">A chamada atingiu o tempo limite.</span><span class="sxs-lookup"><span data-stu-id="678d7-115">The call timed out.</span></span>|  
|<span data-ttu-id="678d7-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="678d7-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="678d7-117">O chamador não é proprietário do bloqueio.</span><span class="sxs-lookup"><span data-stu-id="678d7-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="678d7-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="678d7-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="678d7-119">Um evento foi cancelado enquanto um thread bloqueado ou fibra estava esperando por ele.</span><span class="sxs-lookup"><span data-stu-id="678d7-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="678d7-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="678d7-120">E_FAIL</span></span>|<span data-ttu-id="678d7-121">Ocorreu uma falha catastrófica desconhecida.</span><span class="sxs-lookup"><span data-stu-id="678d7-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="678d7-122">Quando um método retornar E_FAIL, o CLR não é mais utilizável dentro do processo.</span><span class="sxs-lookup"><span data-stu-id="678d7-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="678d7-123">As chamadas subsequentes à hospedagem de métodos de retorno HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="678d7-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="678d7-124">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="678d7-124">E_INVALIDARG</span></span>|<span data-ttu-id="678d7-125">Um identificador de porta inválido foi passado.</span><span class="sxs-lookup"><span data-stu-id="678d7-125">An invalid port handle was passed.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="678d7-126">Comentários</span><span class="sxs-lookup"><span data-stu-id="678d7-126">Remarks</span></span>  
 `hPort` <span data-ttu-id="678d7-127">deve ser um identificador para uma porta que foi criado por uma chamada anterior para `CreateIoCompletionPort`.</span><span class="sxs-lookup"><span data-stu-id="678d7-127">must be a handle to a port that was created by an earlier call to `CreateIoCompletionPort`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="678d7-128">Requisitos</span><span class="sxs-lookup"><span data-stu-id="678d7-128">Requirements</span></span>  
 <span data-ttu-id="678d7-129">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="678d7-129">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="678d7-130">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="678d7-130">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="678d7-131">**Biblioteca:** Incluído como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="678d7-131">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 **<span data-ttu-id="678d7-132">Versões do .NET Framework:</span><span class="sxs-lookup"><span data-stu-id="678d7-132">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="678d7-133">Consulte também</span><span class="sxs-lookup"><span data-stu-id="678d7-133">See also</span></span>

- [<span data-ttu-id="678d7-134">Interface ICLRIoCompletionManager</span><span class="sxs-lookup"><span data-stu-id="678d7-134">ICLRIoCompletionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-interface.md)
- [<span data-ttu-id="678d7-135">Interface IHostIoCompletionManager</span><span class="sxs-lookup"><span data-stu-id="678d7-135">IHostIoCompletionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-interface.md)
