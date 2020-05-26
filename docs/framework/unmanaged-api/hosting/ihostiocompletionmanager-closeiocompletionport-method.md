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
ms.openlocfilehash: 5e2e49b4c993e127a31b54d40f721e0714198780
ms.sourcegitcommit: d223616e7e6fe2139079052e6fcbe25413fb9900
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/22/2020
ms.locfileid: "83804772"
---
# <a name="ihostiocompletionmanagercloseiocompletionport-method"></a><span data-ttu-id="e3333-102">Método IHostIoCompletionManager::CloseIoCompletionPort</span><span class="sxs-lookup"><span data-stu-id="e3333-102">IHostIoCompletionManager::CloseIoCompletionPort Method</span></span>
<span data-ttu-id="e3333-103">Solicita que o host feche uma porta que foi aberta por meio de uma chamada anterior para [CreateIoCompletionPort](ihostiocompletionmanager-createiocompletionport-method.md).</span><span class="sxs-lookup"><span data-stu-id="e3333-103">Requests that the host close a port that was opened through an earlier call to [CreateIoCompletionPort](ihostiocompletionmanager-createiocompletionport-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e3333-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="e3333-104">Syntax</span></span>  
  
```cpp  
HRESULT CloseIoCompletionPort (  
    [in] HANDLE hPort  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e3333-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="e3333-105">Parameters</span></span>  
 `hPort`  
 <span data-ttu-id="e3333-106">no O identificador da porta a ser fechada.</span><span class="sxs-lookup"><span data-stu-id="e3333-106">[in] The handle of the port to close.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e3333-107">Valor Retornado</span><span class="sxs-lookup"><span data-stu-id="e3333-107">Return Value</span></span>  
  
|<span data-ttu-id="e3333-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="e3333-108">HRESULT</span></span>|<span data-ttu-id="e3333-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="e3333-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="e3333-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="e3333-110">S_OK</span></span>|<span data-ttu-id="e3333-111">`CloseIoCompletionPort`retornado com êxito.</span><span class="sxs-lookup"><span data-stu-id="e3333-111">`CloseIoCompletionPort` returned successfully.</span></span>|  
|<span data-ttu-id="e3333-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="e3333-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="e3333-113">O Common Language Runtime (CLR) não foi carregado em um processo ou o CLR está em um estado no qual não pode executar código gerenciado ou processar a chamada com êxito.</span><span class="sxs-lookup"><span data-stu-id="e3333-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="e3333-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="e3333-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="e3333-115">A chamada atingiu o tempo limite.</span><span class="sxs-lookup"><span data-stu-id="e3333-115">The call timed out.</span></span>|  
|<span data-ttu-id="e3333-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="e3333-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="e3333-117">O chamador não possui o bloqueio.</span><span class="sxs-lookup"><span data-stu-id="e3333-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="e3333-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="e3333-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="e3333-119">Um evento foi cancelado enquanto um thread ou uma fibra bloqueada estava esperando.</span><span class="sxs-lookup"><span data-stu-id="e3333-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="e3333-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="e3333-120">E_FAIL</span></span>|<span data-ttu-id="e3333-121">Ocorreu uma falha catastrófica desconhecida.</span><span class="sxs-lookup"><span data-stu-id="e3333-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="e3333-122">Quando um método retorna E_FAIL, o CLR não é mais utilizável no processo.</span><span class="sxs-lookup"><span data-stu-id="e3333-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="e3333-123">As chamadas subsequentes para métodos de hospedagem retornam HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="e3333-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="e3333-124">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="e3333-124">E_INVALIDARG</span></span>|<span data-ttu-id="e3333-125">Um identificador de porta inválido foi passado.</span><span class="sxs-lookup"><span data-stu-id="e3333-125">An invalid port handle was passed.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e3333-126">Comentários</span><span class="sxs-lookup"><span data-stu-id="e3333-126">Remarks</span></span>  
 <span data-ttu-id="e3333-127">`hPort`deve ser um identificador para uma porta que foi criada por uma chamada anterior para `CreateIoCompletionPort` .</span><span class="sxs-lookup"><span data-stu-id="e3333-127">`hPort` must be a handle to a port that was created by an earlier call to `CreateIoCompletionPort`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e3333-128">Requisitos</span><span class="sxs-lookup"><span data-stu-id="e3333-128">Requirements</span></span>  
 <span data-ttu-id="e3333-129">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e3333-129">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e3333-130">**Cabeçalho:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="e3333-130">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="e3333-131">**Biblioteca:** Incluído como um recurso em MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="e3333-131">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="e3333-132">**.NET Framework versões:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e3333-132">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e3333-133">Confira também</span><span class="sxs-lookup"><span data-stu-id="e3333-133">See also</span></span>

- [<span data-ttu-id="e3333-134">Interface ICLRIoCompletionManager</span><span class="sxs-lookup"><span data-stu-id="e3333-134">ICLRIoCompletionManager Interface</span></span>](iclriocompletionmanager-interface.md)
- [<span data-ttu-id="e3333-135">Interface IHostIoCompletionManager</span><span class="sxs-lookup"><span data-stu-id="e3333-135">IHostIoCompletionManager Interface</span></span>](ihostiocompletionmanager-interface.md)
