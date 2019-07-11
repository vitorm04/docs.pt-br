---
title: Método IHostMemoryManager::GetMemoryLoad
ms.date: 03/30/2017
api_name:
- IHostMemoryManager.GetMemoryLoad
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostMemoryManager::GetMemoryLoad
helpviewer_keywords:
- IHostMemoryManager::GetMemoryLoad method [.NET Framework hosting]
- GetMemoryLoad method [.NET Framework hosting]
ms.assetid: e8138f6e-a0a4-48d4-8dae-9466b4dc6180
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 917ebe3c2001a9bc87978685d7f9a19eb3d98220
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67767204"
---
# <a name="ihostmemorymanagergetmemoryload-method"></a><span data-ttu-id="e7d5a-102">Método IHostMemoryManager::GetMemoryLoad</span><span class="sxs-lookup"><span data-stu-id="e7d5a-102">IHostMemoryManager::GetMemoryLoad Method</span></span>
<span data-ttu-id="e7d5a-103">Obtém a quantidade de memória física que está atualmente em uso e, portanto, indisponível, conforme informado pelo host.</span><span class="sxs-lookup"><span data-stu-id="e7d5a-103">Gets the amount of physical memory that is currently in use, and therefore unavailable, as reported by the host.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e7d5a-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="e7d5a-104">Syntax</span></span>  
  
```cpp  
HRESULT GetMemoryLoad (  
    [out] DWORD*  pMemoryLoad,   
    [out] SIZE_T  *pAvailableBytes  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e7d5a-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="e7d5a-105">Parameters</span></span>  
 `pMemoryLoad`  
 <span data-ttu-id="e7d5a-106">[out] Um ponteiro para a porcentagem aproximada de memória física total que está atualmente em uso.</span><span class="sxs-lookup"><span data-stu-id="e7d5a-106">[out] A pointer to the approximate percentage of total physical memory that is currently in use.</span></span>  
  
 `pAvailableBytes`  
 <span data-ttu-id="e7d5a-107">[out] Um ponteiro para o número de bytes disponíveis para o common language runtime (CLR).</span><span class="sxs-lookup"><span data-stu-id="e7d5a-107">[out] A pointer to the number of bytes available to the common language runtime (CLR).</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e7d5a-108">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="e7d5a-108">Return Value</span></span>  
  
|<span data-ttu-id="e7d5a-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="e7d5a-109">HRESULT</span></span>|<span data-ttu-id="e7d5a-110">Descrição</span><span class="sxs-lookup"><span data-stu-id="e7d5a-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="e7d5a-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="e7d5a-111">S_OK</span></span>|<span data-ttu-id="e7d5a-112">`GetMemoryLoad` retornado com êxito.</span><span class="sxs-lookup"><span data-stu-id="e7d5a-112">`GetMemoryLoad` returned successfully.</span></span>|  
|<span data-ttu-id="e7d5a-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="e7d5a-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="e7d5a-114">O CLR não tenha sido carregado em um processo ou o CLR está em um estado em que ele não pode executar o código gerenciado ou processar a chamada com êxito.</span><span class="sxs-lookup"><span data-stu-id="e7d5a-114">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="e7d5a-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="e7d5a-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="e7d5a-116">A chamada atingiu o tempo limite.</span><span class="sxs-lookup"><span data-stu-id="e7d5a-116">The call timed out.</span></span>|  
|<span data-ttu-id="e7d5a-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="e7d5a-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="e7d5a-118">O chamador não é proprietário do bloqueio.</span><span class="sxs-lookup"><span data-stu-id="e7d5a-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="e7d5a-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="e7d5a-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="e7d5a-120">Um evento foi cancelado enquanto um thread bloqueado ou fibra estava esperando por ele.</span><span class="sxs-lookup"><span data-stu-id="e7d5a-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="e7d5a-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="e7d5a-121">E_FAIL</span></span>|<span data-ttu-id="e7d5a-122">Ocorreu uma falha catastrófica desconhecida.</span><span class="sxs-lookup"><span data-stu-id="e7d5a-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="e7d5a-123">Quando um método retornar E_FAIL, o CLR não é mais utilizável dentro do processo.</span><span class="sxs-lookup"><span data-stu-id="e7d5a-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="e7d5a-124">As chamadas subsequentes à hospedagem de métodos de retorno HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="e7d5a-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e7d5a-125">Comentários</span><span class="sxs-lookup"><span data-stu-id="e7d5a-125">Remarks</span></span>  
 <span data-ttu-id="e7d5a-126">`GetMemoryLoad` encapsula o Win32 `GlobalMemoryStatus` função.</span><span class="sxs-lookup"><span data-stu-id="e7d5a-126">`GetMemoryLoad` wraps the Win32 `GlobalMemoryStatus` function.</span></span> <span data-ttu-id="e7d5a-127">O valor de `pMemoryLoad` é o equivalente a `dwMemoryLoad` campo o `MEMORYSTATUS` estrutura retornada de `GlobalMemoryStatus`.</span><span class="sxs-lookup"><span data-stu-id="e7d5a-127">The value of `pMemoryLoad` is the equivalent of the `dwMemoryLoad` field in the `MEMORYSTATUS` structure returned from `GlobalMemoryStatus`.</span></span>  
  
 <span data-ttu-id="e7d5a-128">O tempo de execução usa o valor de retorno como uma heurística para o coletor de lixo.</span><span class="sxs-lookup"><span data-stu-id="e7d5a-128">The runtime uses the return value as a heuristic for the garbage collector.</span></span> <span data-ttu-id="e7d5a-129">Por exemplo, se o host informa que a maioria de memória em uso, o coletor de lixo pode optar por coletar de várias gerações para aumentar a quantidade de memória que potencialmente pode se tornar disponível.</span><span class="sxs-lookup"><span data-stu-id="e7d5a-129">For example, if the host reports that the majority of memory is in use, the garbage collector may elect to collect from multiple generations to increase the amount of memory that can potentially become available.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e7d5a-130">Requisitos</span><span class="sxs-lookup"><span data-stu-id="e7d5a-130">Requirements</span></span>  
 <span data-ttu-id="e7d5a-131">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e7d5a-131">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e7d5a-132">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="e7d5a-132">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="e7d5a-133">**Biblioteca:** Incluído como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="e7d5a-133">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="e7d5a-134">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e7d5a-134">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e7d5a-135">Consulte também</span><span class="sxs-lookup"><span data-stu-id="e7d5a-135">See also</span></span>

- <xref:System.GC?displayProperty=nameWithType>
- [<span data-ttu-id="e7d5a-136">Interface IHostMemoryManager</span><span class="sxs-lookup"><span data-stu-id="e7d5a-136">IHostMemoryManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-interface.md)
