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
ms.openlocfilehash: 88acd50c83eb1ff4d59aa50d677db2383912659a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176273"
---
# <a name="ihostmemorymanagergetmemoryload-method"></a><span data-ttu-id="d490c-102">Método IHostMemoryManager::GetMemoryLoad</span><span class="sxs-lookup"><span data-stu-id="d490c-102">IHostMemoryManager::GetMemoryLoad Method</span></span>
<span data-ttu-id="d490c-103">Obtém a quantidade de memória física que está atualmente em uso e, portanto, indisponível, conforme relatado pelo host.</span><span class="sxs-lookup"><span data-stu-id="d490c-103">Gets the amount of physical memory that is currently in use, and therefore unavailable, as reported by the host.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d490c-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="d490c-104">Syntax</span></span>  
  
```cpp  
HRESULT GetMemoryLoad (  
    [out] DWORD*  pMemoryLoad,
    [out] SIZE_T  *pAvailableBytes  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d490c-105">parâmetros</span><span class="sxs-lookup"><span data-stu-id="d490c-105">Parameters</span></span>  
 `pMemoryLoad`  
 <span data-ttu-id="d490c-106">[fora] Um ponteiro para a porcentagem aproximada da memória física total que está atualmente em uso.</span><span class="sxs-lookup"><span data-stu-id="d490c-106">[out] A pointer to the approximate percentage of total physical memory that is currently in use.</span></span>  
  
 `pAvailableBytes`  
 <span data-ttu-id="d490c-107">[fora] Um ponteiro para o número de bytes disponíveis para o tempo de execução do idioma comum (CLR).</span><span class="sxs-lookup"><span data-stu-id="d490c-107">[out] A pointer to the number of bytes available to the common language runtime (CLR).</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d490c-108">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="d490c-108">Return Value</span></span>  
  
|<span data-ttu-id="d490c-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="d490c-109">HRESULT</span></span>|<span data-ttu-id="d490c-110">Descrição</span><span class="sxs-lookup"><span data-stu-id="d490c-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="d490c-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="d490c-111">S_OK</span></span>|<span data-ttu-id="d490c-112">`GetMemoryLoad`retornou com sucesso.</span><span class="sxs-lookup"><span data-stu-id="d490c-112">`GetMemoryLoad` returned successfully.</span></span>|  
|<span data-ttu-id="d490c-113">Host_e_clrnotavailable</span><span class="sxs-lookup"><span data-stu-id="d490c-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="d490c-114">A CLR não foi carregada em um processo, ou a CLR está em um estado no qual não pode executar código gerenciado ou processar a chamada com sucesso.</span><span class="sxs-lookup"><span data-stu-id="d490c-114">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="d490c-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="d490c-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="d490c-116">A chamada acabou.</span><span class="sxs-lookup"><span data-stu-id="d490c-116">The call timed out.</span></span>|  
|<span data-ttu-id="d490c-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="d490c-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="d490c-118">O interlocutor não é dono da fechadura.</span><span class="sxs-lookup"><span data-stu-id="d490c-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="d490c-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="d490c-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="d490c-120">Um evento foi cancelado enquanto um fio ou fibra bloqueado estava esperando por ele.</span><span class="sxs-lookup"><span data-stu-id="d490c-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="d490c-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="d490c-121">E_FAIL</span></span>|<span data-ttu-id="d490c-122">Uma falha catastrófica desconhecida ocorreu.</span><span class="sxs-lookup"><span data-stu-id="d490c-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="d490c-123">Quando um método retorna E_FAIL, a CLR não é mais utilizável dentro do processo.</span><span class="sxs-lookup"><span data-stu-id="d490c-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="d490c-124">Chamadas subseqüentes para métodos de hospedagem retornam HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="d490c-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d490c-125">Comentários</span><span class="sxs-lookup"><span data-stu-id="d490c-125">Remarks</span></span>  
 <span data-ttu-id="d490c-126">`GetMemoryLoad`envolve a função `GlobalMemoryStatus` Win32.</span><span class="sxs-lookup"><span data-stu-id="d490c-126">`GetMemoryLoad` wraps the Win32 `GlobalMemoryStatus` function.</span></span> <span data-ttu-id="d490c-127">O valor `pMemoryLoad` é o `dwMemoryLoad` equivalente ao `MEMORYSTATUS` campo na `GlobalMemoryStatus`estrutura devolvida de .</span><span class="sxs-lookup"><span data-stu-id="d490c-127">The value of `pMemoryLoad` is the equivalent of the `dwMemoryLoad` field in the `MEMORYSTATUS` structure returned from `GlobalMemoryStatus`.</span></span>  
  
 <span data-ttu-id="d490c-128">O tempo de execução usa o valor de retorno como uma heurística para o coletor de lixo.</span><span class="sxs-lookup"><span data-stu-id="d490c-128">The runtime uses the return value as a heuristic for the garbage collector.</span></span> <span data-ttu-id="d490c-129">Por exemplo, se o host relatar que a maioria da memória está em uso, o coletor de lixo pode optar por coletar de várias gerações para aumentar a quantidade de memória que pode potencialmente ficar disponível.</span><span class="sxs-lookup"><span data-stu-id="d490c-129">For example, if the host reports that the majority of memory is in use, the garbage collector may elect to collect from multiple generations to increase the amount of memory that can potentially become available.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d490c-130">Requisitos</span><span class="sxs-lookup"><span data-stu-id="d490c-130">Requirements</span></span>  
 <span data-ttu-id="d490c-131">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d490c-131">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d490c-132">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="d490c-132">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="d490c-133">**Biblioteca:** Incluído como um recurso em MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="d490c-133">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="d490c-134">**.NET Framework Versions:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d490c-134">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d490c-135">Confira também</span><span class="sxs-lookup"><span data-stu-id="d490c-135">See also</span></span>

- <xref:System.GC?displayProperty=nameWithType>
- [<span data-ttu-id="d490c-136">Interface IHostMemoryManager</span><span class="sxs-lookup"><span data-stu-id="d490c-136">IHostMemoryManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-interface.md)
