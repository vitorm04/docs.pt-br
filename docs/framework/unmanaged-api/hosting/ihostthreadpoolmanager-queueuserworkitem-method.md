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
ms.openlocfilehash: b458739db024bdbe8cf0fb5a12a5d5f508d332da
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33441715"
---
# <a name="ihostthreadpoolmanagerqueueuserworkitem-method"></a><span data-ttu-id="7b8aa-102">Método IHostThreadPoolManager::QueueUserWorkItem</span><span class="sxs-lookup"><span data-stu-id="7b8aa-102">IHostThreadPoolManager::QueueUserWorkItem Method</span></span>
<span data-ttu-id="7b8aa-103">Uma função para a execução de filas e especifica um objeto que contém dados a serem usados por essa função.</span><span class="sxs-lookup"><span data-stu-id="7b8aa-103">Queues a function for execution, and specifies an object containing data to be used by that function.</span></span> <span data-ttu-id="7b8aa-104">A função é executada quando um thread estiver disponível.</span><span class="sxs-lookup"><span data-stu-id="7b8aa-104">The function executes when a thread becomes available.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7b8aa-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="7b8aa-105">Syntax</span></span>  
  
```  
HRESULT QueueUserWorkItem (  
    [in] LPTHREAD_START_ROUTINE Function,  
    [in] PVOID Context,  
    [in] ULONG Flags  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="7b8aa-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="7b8aa-106">Parameters</span></span>  
 `Function`  
 <span data-ttu-id="7b8aa-107">[in] Um ponteiro de função que representa a função a ser executada.</span><span class="sxs-lookup"><span data-stu-id="7b8aa-107">[in] A function pointer that represents the function to execute.</span></span>  
  
 `Context`  
 <span data-ttu-id="7b8aa-108">[in] Um objeto que contém dados a serem usados pelo `Function`.</span><span class="sxs-lookup"><span data-stu-id="7b8aa-108">[in] An object that contains data to be used by `Function`.</span></span>  
  
 `Flags`  
 <span data-ttu-id="7b8aa-109">[in] Um dos sinalizadores valores, conforme definido para o Win32 `QueueUserWorkItem` método, que controlam a execução.</span><span class="sxs-lookup"><span data-stu-id="7b8aa-109">[in] One of the flags values, as defined for the Win32 `QueueUserWorkItem` method, that control execution.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="7b8aa-110">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="7b8aa-110">Return Value</span></span>  
  
|<span data-ttu-id="7b8aa-111">HRESULT</span><span class="sxs-lookup"><span data-stu-id="7b8aa-111">HRESULT</span></span>|<span data-ttu-id="7b8aa-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="7b8aa-112">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="7b8aa-113">S_OK</span><span class="sxs-lookup"><span data-stu-id="7b8aa-113">S_OK</span></span>|<span data-ttu-id="7b8aa-114">`QueueUserWorkItem` retornou com êxito.</span><span class="sxs-lookup"><span data-stu-id="7b8aa-114">`QueueUserWorkItem` returned successfully.</span></span>|  
|<span data-ttu-id="7b8aa-115">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="7b8aa-115">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="7b8aa-116">O common language runtime (CLR) não foi carregado em um processo ou o CLR está em um estado em que ele não pode executar código gerenciado ou processar a chamada com êxito.</span><span class="sxs-lookup"><span data-stu-id="7b8aa-116">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="7b8aa-117">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="7b8aa-117">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="7b8aa-118">A chamada foi atingido.</span><span class="sxs-lookup"><span data-stu-id="7b8aa-118">The call timed out.</span></span>|  
|<span data-ttu-id="7b8aa-119">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="7b8aa-119">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="7b8aa-120">O chamador não possui o bloqueio.</span><span class="sxs-lookup"><span data-stu-id="7b8aa-120">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="7b8aa-121">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="7b8aa-121">HOST_E_ABANDONED</span></span>|<span data-ttu-id="7b8aa-122">Um evento foi cancelado durante um thread bloqueado ou fibra estava aguardando nele.</span><span class="sxs-lookup"><span data-stu-id="7b8aa-122">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="7b8aa-123">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="7b8aa-123">E_FAIL</span></span>|<span data-ttu-id="7b8aa-124">Ocorreu uma falha catastrófica desconhecida.</span><span class="sxs-lookup"><span data-stu-id="7b8aa-124">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="7b8aa-125">Quando um método retornará E_FAIL, o CLR não será mais utilizável dentro do processo.</span><span class="sxs-lookup"><span data-stu-id="7b8aa-125">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="7b8aa-126">As chamadas subsequentes para hospedagem métodos retornam HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="7b8aa-126">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7b8aa-127">Comentários</span><span class="sxs-lookup"><span data-stu-id="7b8aa-127">Remarks</span></span>  
 <span data-ttu-id="7b8aa-128">`QueueUserWorkItem` Enfileira um item de trabalho para um thread de trabalho no pool de threads.</span><span class="sxs-lookup"><span data-stu-id="7b8aa-128">`QueueUserWorkItem` queues a work item to a worker thread in the thread pool.</span></span> <span data-ttu-id="7b8aa-129">Tipos de assinatura e o parâmetro são idênticos da função Win32 correspondente, que tem o mesmo nome.</span><span class="sxs-lookup"><span data-stu-id="7b8aa-129">Its signature and parameter types are identical to those of the corresponding Win32 function, which has the same name.</span></span> <span data-ttu-id="7b8aa-130">Para obter mais informações, consulte a documentação da plataforma Windows.</span><span class="sxs-lookup"><span data-stu-id="7b8aa-130">For more information, see the Windows Platform documentation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7b8aa-131">Requisitos</span><span class="sxs-lookup"><span data-stu-id="7b8aa-131">Requirements</span></span>  
 <span data-ttu-id="7b8aa-132">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7b8aa-132">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7b8aa-133">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="7b8aa-133">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="7b8aa-134">**Biblioteca:** incluído como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="7b8aa-134">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="7b8aa-135">**Versões do .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7b8aa-135">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7b8aa-136">Consulte também</span><span class="sxs-lookup"><span data-stu-id="7b8aa-136">See Also</span></span>  
 <xref:System.Threading.ThreadPool.QueueUserWorkItem%2A>  
 <xref:System.Threading.ThreadPool>  
 [<span data-ttu-id="7b8aa-137">Interface IHostThreadPoolManager</span><span class="sxs-lookup"><span data-stu-id="7b8aa-137">IHostThreadPoolManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-interface.md)
