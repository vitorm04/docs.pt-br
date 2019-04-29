---
title: Método ICLRGCManager2::SetGCStartupLimitsEx
ms.date: 03/30/2017
api_name:
- ICLRGCManager2.SetGCStartupLimitsEx
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRGCManager2::SetCLRGCStartupLimitsEx
helpviewer_keywords:
- ICLRGCManager2::SetGCStartupLimitsEx method [.NET Framework hosting]
- SetGCStartupLimitsEx method, ICLRGCManager2 interface [.NET Framework hosting]
ms.assetid: 6c3a08a9-5d65-48d4-8bbf-2a86ed7d356a
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6cba7b4a34835eb2f394aa71be8b907973cb1cd6
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61700183"
---
# <a name="iclrgcmanager2setgcstartuplimitsex-method"></a><span data-ttu-id="81853-102">Método ICLRGCManager2::SetGCStartupLimitsEx</span><span class="sxs-lookup"><span data-stu-id="81853-102">ICLRGCManager2::SetGCStartupLimitsEx Method</span></span>
<span data-ttu-id="81853-103">Define o tamanho de um segmento de coleta de lixo e o tamanho máximo da geração do sistema de coleta de lixo 0.</span><span class="sxs-lookup"><span data-stu-id="81853-103">Sets the size of a garbage collection segment and the maximum size of the garbage collection system's generation 0.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="81853-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="81853-104">Syntax</span></span>  
  
```  
HRESULT SetGCStartupLimitsEx (  
    [in] SIZE_T SegmentSize,   
    [in] SIZE_T MaxGen0Size  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="81853-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="81853-105">Parameters</span></span>  
 `SegmentSize`  
 <span data-ttu-id="81853-106">[in] O tamanho especificado de um segmento de coleta de lixo.</span><span class="sxs-lookup"><span data-stu-id="81853-106">[in] The specified size of a garbage collection segment.</span></span>  
  
 <span data-ttu-id="81853-107">O tamanho do segmento mínimo é de 4 MB.</span><span class="sxs-lookup"><span data-stu-id="81853-107">The minimum segment size is 4 MB.</span></span> <span data-ttu-id="81853-108">Segmentos podem ser aumentado em incrementos de 1 MB ou maiores.</span><span class="sxs-lookup"><span data-stu-id="81853-108">Segments can be increased in increments of 1 MB or larger.</span></span>  
  
 `MaxGen0Size`  
 <span data-ttu-id="81853-109">[in] O tamanho máximo especificado para a geração 0.</span><span class="sxs-lookup"><span data-stu-id="81853-109">[in] The specified maximum size for generation 0.</span></span>  
  
 <span data-ttu-id="81853-110">O tamanho mínimo de geração 0 é 64 KB.</span><span class="sxs-lookup"><span data-stu-id="81853-110">The minimum generation 0 size is 64 KB.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="81853-111">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="81853-111">Return Value</span></span>  
  
|<span data-ttu-id="81853-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="81853-112">HRESULT</span></span>|<span data-ttu-id="81853-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="81853-113">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="81853-114">S_OK</span><span class="sxs-lookup"><span data-stu-id="81853-114">S_OK</span></span>|<span data-ttu-id="81853-115">`SetGCStartupLimitsEx` retornado com êxito.</span><span class="sxs-lookup"><span data-stu-id="81853-115">`SetGCStartupLimitsEx` returned successfully.</span></span>|  
|<span data-ttu-id="81853-116">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="81853-116">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="81853-117">O common language runtime (CLR) não foi carregado em um processo ou o CLR está em um estado em que ele não pode executar o código gerenciado ou processar a chamada com êxito.</span><span class="sxs-lookup"><span data-stu-id="81853-117">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="81853-118">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="81853-118">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="81853-119">A chamada atingiu o tempo limite.</span><span class="sxs-lookup"><span data-stu-id="81853-119">The call timed out.</span></span>|  
|<span data-ttu-id="81853-120">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="81853-120">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="81853-121">O chamador não é proprietário do bloqueio.</span><span class="sxs-lookup"><span data-stu-id="81853-121">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="81853-122">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="81853-122">HOST_E_ABANDONED</span></span>|<span data-ttu-id="81853-123">Um evento foi cancelado enquanto um thread bloqueado ou fibra estava esperando por ele.</span><span class="sxs-lookup"><span data-stu-id="81853-123">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="81853-124">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="81853-124">E_FAIL</span></span>|<span data-ttu-id="81853-125">Ocorreu uma falha catastrófica desconhecida.</span><span class="sxs-lookup"><span data-stu-id="81853-125">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="81853-126">Depois que um método retorna E_FAIL, o CLR não é mais utilizável dentro do processo.</span><span class="sxs-lookup"><span data-stu-id="81853-126">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="81853-127">As chamadas subsequentes à hospedagem de métodos de retorno HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="81853-127">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="81853-128">Comentários</span><span class="sxs-lookup"><span data-stu-id="81853-128">Remarks</span></span>  
 <span data-ttu-id="81853-129">Os valores que `SetGCStartupLimitsEx` conjuntos podem ser especificados apenas antes que o host é iniciado.</span><span class="sxs-lookup"><span data-stu-id="81853-129">The values that `SetGCStartupLimitsEx` sets can be specified only before the host is started.</span></span> <span data-ttu-id="81853-130">Chamadas posteriores para `SetGCStartupLimitsEx` são ignorados.</span><span class="sxs-lookup"><span data-stu-id="81853-130">Later calls to `SetGCStartupLimitsEx` are ignored.</span></span>  
  
 <span data-ttu-id="81853-131">Para definir um parâmetro sem afetar o outro, especifique 0 (zero) para o parâmetro que você não deseja alterar.</span><span class="sxs-lookup"><span data-stu-id="81853-131">To set either parameter without affecting the other, specify 0 (zero) for the parameter you don't want to change.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="81853-132">Requisitos</span><span class="sxs-lookup"><span data-stu-id="81853-132">Requirements</span></span>  
 <span data-ttu-id="81853-133">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="81853-133">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="81853-134">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="81853-134">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="81853-135">**Biblioteca:** Incluído como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="81853-135">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="81853-136">**Versões do .NET Framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="81853-136">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="81853-137">Consulte também</span><span class="sxs-lookup"><span data-stu-id="81853-137">See also</span></span>

- [<span data-ttu-id="81853-138">Gerenciamento Automático de Memória</span><span class="sxs-lookup"><span data-stu-id="81853-138">Automatic Memory Management</span></span>](../../../../docs/standard/automatic-memory-management.md)
- [<span data-ttu-id="81853-139">Coleta de lixo</span><span class="sxs-lookup"><span data-stu-id="81853-139">Garbage Collection</span></span>](../../../../docs/standard/garbage-collection/index.md)
- [<span data-ttu-id="81853-140">Interface ICLRControl</span><span class="sxs-lookup"><span data-stu-id="81853-140">ICLRControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)
- [<span data-ttu-id="81853-141">Interface ICLRGCManager2</span><span class="sxs-lookup"><span data-stu-id="81853-141">ICLRGCManager2 Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager2-interface.md)
