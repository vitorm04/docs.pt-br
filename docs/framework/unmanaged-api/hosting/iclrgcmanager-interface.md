---
title: Interface ICLRGCManager
ms.date: 03/30/2017
api_name:
- ICLRGCManager
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRGCManager
helpviewer_keywords:
- ICLRGCManager interface [.NET Framework hosting]
ms.assetid: fb511c9b-3fe4-41b0-822a-6ba4a079d1f5
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 76d1071ddde1509f16fd786afa4c05c05224d051
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69966219"
---
# <a name="iclrgcmanager-interface"></a><span data-ttu-id="493ce-102">Interface ICLRGCManager</span><span class="sxs-lookup"><span data-stu-id="493ce-102">ICLRGCManager Interface</span></span>
<span data-ttu-id="493ce-103">Fornece métodos que permitem que um host interaja com o sistema de coleta de lixo do Common Language Runtime.</span><span class="sxs-lookup"><span data-stu-id="493ce-103">Provides methods that allow a host to interact with the common language runtime's garbage collection system.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="493ce-104">Começando com o .NET Framework 4,5, você pode usar o método [ICLRGCManager2:: SetGCStartupLimitsEx](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager2-setgcstartuplimitsex-method.md) para definir o tamanho de um segmento de coleta de lixo e o tamanho máximo da geração 0 do sistema de coleta de lixo para valores maiores que o `DWORD`limite imposto pelo método [SetGCStartupLimits](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager-setgcstartuplimits-method.md) .</span><span class="sxs-lookup"><span data-stu-id="493ce-104">Starting with the .NET Framework 4.5, you can use the [ICLRGCManager2::SetGCStartupLimitsEx](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager2-setgcstartuplimitsex-method.md) method to set the size of a garbage collection segment and the maximum size of the garbage collection system's generation 0 to values greater than the `DWORD` limit that is imposed by the [SetGCStartupLimits](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager-setgcstartuplimits-method.md) method.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="493ce-105">Métodos</span><span class="sxs-lookup"><span data-stu-id="493ce-105">Methods</span></span>  
  
|<span data-ttu-id="493ce-106">Método</span><span class="sxs-lookup"><span data-stu-id="493ce-106">Method</span></span>|<span data-ttu-id="493ce-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="493ce-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="493ce-108">Método Collect</span><span class="sxs-lookup"><span data-stu-id="493ce-108">Collect Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager-collect-method.md)|<span data-ttu-id="493ce-109">Força uma coleta de lixo para a geração especificada.</span><span class="sxs-lookup"><span data-stu-id="493ce-109">Forces a garbage collection for the specified generation.</span></span>|  
|[<span data-ttu-id="493ce-110">Método GetStats</span><span class="sxs-lookup"><span data-stu-id="493ce-110">GetStats Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager-getstats-method.md)|<span data-ttu-id="493ce-111">Obtém um conjunto de estatísticas atuais sobre o sistema de coleta de lixo.</span><span class="sxs-lookup"><span data-stu-id="493ce-111">Gets a set of current statistics about the garbage collection system.</span></span>|  
|[<span data-ttu-id="493ce-112">Método SetGCStartupLimits</span><span class="sxs-lookup"><span data-stu-id="493ce-112">SetGCStartupLimits Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager-setgcstartuplimits-method.md)|<span data-ttu-id="493ce-113">Define o tamanho de um segmento de coleta de lixo e o tamanho máximo da geração 0 do sistema de coleta de lixo.</span><span class="sxs-lookup"><span data-stu-id="493ce-113">Sets the size of a garbage collection segment and the maximum size of the garbage collection system's generation 0.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="493ce-114">Comentários</span><span class="sxs-lookup"><span data-stu-id="493ce-114">Remarks</span></span>  
 <span data-ttu-id="493ce-115">O Common Language Runtime (CLR) implementa seu mecanismo de coleta de lixo com <xref:System.GC> o tipo gerenciado.</span><span class="sxs-lookup"><span data-stu-id="493ce-115">The common language runtime (CLR) implements its garbage collection mechanism with the managed <xref:System.GC> type.</span></span> <span data-ttu-id="493ce-116">Para obter mais informações sobre o sistema de coleta de lixo, consulte [coleta de lixo](../../../standard/garbage-collection/index.md).</span><span class="sxs-lookup"><span data-stu-id="493ce-116">For more information about the garbage collection system, see [Garbage Collection](../../../standard/garbage-collection/index.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="493ce-117">Requisitos</span><span class="sxs-lookup"><span data-stu-id="493ce-117">Requirements</span></span>  
 <span data-ttu-id="493ce-118">**Compatíveis** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="493ce-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="493ce-119">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="493ce-119">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="493ce-120">**Biblioteca** Incluído como um recurso em MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="493ce-120">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="493ce-121">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="493ce-121">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="493ce-122">Consulte também</span><span class="sxs-lookup"><span data-stu-id="493ce-122">See also</span></span>

- [<span data-ttu-id="493ce-123">Gerenciamento Automático de Memória</span><span class="sxs-lookup"><span data-stu-id="493ce-123">Automatic Memory Management</span></span>](../../../standard/automatic-memory-management.md)
- [<span data-ttu-id="493ce-124">Estrutura COR_GC_STATS</span><span class="sxs-lookup"><span data-stu-id="493ce-124">COR_GC_STATS Structure</span></span>](../../../../docs/framework/unmanaged-api/hosting/cor-gc-stats-structure.md)
- [<span data-ttu-id="493ce-125">Interface ICLRControl</span><span class="sxs-lookup"><span data-stu-id="493ce-125">ICLRControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)
- [<span data-ttu-id="493ce-126">Interfaces de hospedagem CLR</span><span class="sxs-lookup"><span data-stu-id="493ce-126">CLR Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/clr-hosting-interfaces.md)
- [<span data-ttu-id="493ce-127">Hospedagem de Interfaces</span><span class="sxs-lookup"><span data-stu-id="493ce-127">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
- [<span data-ttu-id="493ce-128">Hospedagem</span><span class="sxs-lookup"><span data-stu-id="493ce-128">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)
