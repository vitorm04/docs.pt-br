---
title: Método IHostThreadPoolManager::QueueUserWorkItem
ms.date: 03/30/2017
api_name:
- IHostThreadPoolManager.QueueUserWorkItem
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostThreadPoolManager::QueueUserWorkItem
helpviewer_keywords:
- IHostThreadPoolManager::QueueUserWorkItem method [.NET Framework hosting]
- QueueUserWorkItem method [.NET Framework hosting]
ms.assetid: 41602053-8670-4827-9d61-cbfcba509b9c
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1c548ae7f8d605ff84da2046d057e436c8e95721
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61796557"
---
# <a name="ihostthreadpoolmanagerqueueuserworkitem-method"></a><span data-ttu-id="503a1-102">Método IHostThreadPoolManager::QueueUserWorkItem</span><span class="sxs-lookup"><span data-stu-id="503a1-102">IHostThreadPoolManager::QueueUserWorkItem Method</span></span>
<span data-ttu-id="503a1-103">Enfileira uma função para a execução e especifica um objeto que contém dados a serem usados por essa função.</span><span class="sxs-lookup"><span data-stu-id="503a1-103">Queues a function for execution, and specifies an object containing data to be used by that function.</span></span> <span data-ttu-id="503a1-104">A função é executada quando um thread fique disponível.</span><span class="sxs-lookup"><span data-stu-id="503a1-104">The function executes when a thread becomes available.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="503a1-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="503a1-105">Syntax</span></span>  
  
```  
HRESULT QueueUserWorkItem (  
    [in] LPTHREAD_START_ROUTINE Function,  
    [in] PVOID Context,  
    [in] ULONG Flags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="503a1-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="503a1-106">Parameters</span></span>  
 `Function`  
 <span data-ttu-id="503a1-107">[in] Um ponteiro de função que representa a função a ser executada.</span><span class="sxs-lookup"><span data-stu-id="503a1-107">[in] A function pointer that represents the function to execute.</span></span>  
  
 `Context`  
 <span data-ttu-id="503a1-108">[in] Um objeto que contém dados a serem usados pelo `Function`.</span><span class="sxs-lookup"><span data-stu-id="503a1-108">[in] An object that contains data to be used by `Function`.</span></span>  
  
 `Flags`  
 <span data-ttu-id="503a1-109">[in] Um dos sinalizadores de valores, conforme definido para o Win32 `QueueUserWorkItem` método, que controlam a execução.</span><span class="sxs-lookup"><span data-stu-id="503a1-109">[in] One of the flags values, as defined for the Win32 `QueueUserWorkItem` method, that control execution.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="503a1-110">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="503a1-110">Return Value</span></span>  
  
|<span data-ttu-id="503a1-111">HRESULT</span><span class="sxs-lookup"><span data-stu-id="503a1-111">HRESULT</span></span>|<span data-ttu-id="503a1-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="503a1-112">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="503a1-113">S_OK</span><span class="sxs-lookup"><span data-stu-id="503a1-113">S_OK</span></span>|<span data-ttu-id="503a1-114">`QueueUserWorkItem` retornado com êxito.</span><span class="sxs-lookup"><span data-stu-id="503a1-114">`QueueUserWorkItem` returned successfully.</span></span>|  
|<span data-ttu-id="503a1-115">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="503a1-115">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="503a1-116">O common language runtime (CLR) não foi carregado em um processo ou o CLR está em um estado em que ele não pode executar o código gerenciado ou processar a chamada com êxito.</span><span class="sxs-lookup"><span data-stu-id="503a1-116">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="503a1-117">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="503a1-117">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="503a1-118">A chamada atingiu o tempo limite.</span><span class="sxs-lookup"><span data-stu-id="503a1-118">The call timed out.</span></span>|  
|<span data-ttu-id="503a1-119">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="503a1-119">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="503a1-120">O chamador não é proprietário do bloqueio.</span><span class="sxs-lookup"><span data-stu-id="503a1-120">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="503a1-121">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="503a1-121">HOST_E_ABANDONED</span></span>|<span data-ttu-id="503a1-122">Um evento foi cancelado enquanto um thread bloqueado ou fibra estava esperando por ele.</span><span class="sxs-lookup"><span data-stu-id="503a1-122">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="503a1-123">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="503a1-123">E_FAIL</span></span>|<span data-ttu-id="503a1-124">Ocorreu uma falha catastrófica desconhecida.</span><span class="sxs-lookup"><span data-stu-id="503a1-124">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="503a1-125">Quando um método retornar E_FAIL, o CLR não é mais utilizável dentro do processo.</span><span class="sxs-lookup"><span data-stu-id="503a1-125">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="503a1-126">As chamadas subsequentes à hospedagem de métodos de retorno HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="503a1-126">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="503a1-127">Comentários</span><span class="sxs-lookup"><span data-stu-id="503a1-127">Remarks</span></span>  
 <span data-ttu-id="503a1-128">`QueueUserWorkItem` Enfileira um item de trabalho para um thread de trabalho no pool de threads.</span><span class="sxs-lookup"><span data-stu-id="503a1-128">`QueueUserWorkItem` queues a work item to a worker thread in the thread pool.</span></span> <span data-ttu-id="503a1-129">Seus tipos de assinatura e de parâmetro são idênticos da função do Win32 correspondente, que tem o mesmo nome.</span><span class="sxs-lookup"><span data-stu-id="503a1-129">Its signature and parameter types are identical to those of the corresponding Win32 function, which has the same name.</span></span> <span data-ttu-id="503a1-130">Para obter mais informações, consulte a documentação da plataforma Windows.</span><span class="sxs-lookup"><span data-stu-id="503a1-130">For more information, see the Windows Platform documentation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="503a1-131">Requisitos</span><span class="sxs-lookup"><span data-stu-id="503a1-131">Requirements</span></span>  
 <span data-ttu-id="503a1-132">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="503a1-132">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="503a1-133">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="503a1-133">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="503a1-134">**Biblioteca:** Incluído como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="503a1-134">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="503a1-135">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="503a1-135">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="503a1-136">Consulte também</span><span class="sxs-lookup"><span data-stu-id="503a1-136">See also</span></span>

- <xref:System.Threading.ThreadPool.QueueUserWorkItem%2A>
- <xref:System.Threading.ThreadPool>
- [<span data-ttu-id="503a1-137">Interface IHostThreadPoolManager</span><span class="sxs-lookup"><span data-stu-id="503a1-137">IHostThreadPoolManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-interface.md)
