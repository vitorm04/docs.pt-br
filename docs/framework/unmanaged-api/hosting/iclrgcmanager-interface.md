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
ms.openlocfilehash: 6e284f94ad0dac9523bd6267e7bc1034a079503d
ms.sourcegitcommit: 4735bb7741555bcb870d7b42964d3774f4897a6e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/30/2019
ms.locfileid: "66380292"
---
# <a name="iclrgcmanager-interface"></a><span data-ttu-id="c5d11-102">Interface ICLRGCManager</span><span class="sxs-lookup"><span data-stu-id="c5d11-102">ICLRGCManager Interface</span></span>
<span data-ttu-id="c5d11-103">Fornece métodos que permitem que um host interagir com o sistema de coleta de lixo do common language runtime.</span><span class="sxs-lookup"><span data-stu-id="c5d11-103">Provides methods that allow a host to interact with the common language runtime's garbage collection system.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="c5d11-104">Começando com o .NET Framework 4.5, você pode usar o [ICLRGCManager2::SetGCStartupLimitsEx](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager2-setgcstartuplimitsex-method.md) método para definir o tamanho de um segmento de coleta de lixo e o tamanho máximo da geração do sistema de coleta de lixo 0 para valores maior que o `DWORD` limite imposto pelo [SetGCStartupLimits](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager-setgcstartuplimits-method.md) método.</span><span class="sxs-lookup"><span data-stu-id="c5d11-104">Starting with the .NET Framework 4.5, you can use the [ICLRGCManager2::SetGCStartupLimitsEx](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager2-setgcstartuplimitsex-method.md) method to set the size of a garbage collection segment and the maximum size of the garbage collection system's generation 0 to values greater than the `DWORD` limit that is imposed by the [SetGCStartupLimits](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager-setgcstartuplimits-method.md) method.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="c5d11-105">Métodos</span><span class="sxs-lookup"><span data-stu-id="c5d11-105">Methods</span></span>  
  
|<span data-ttu-id="c5d11-106">Método</span><span class="sxs-lookup"><span data-stu-id="c5d11-106">Method</span></span>|<span data-ttu-id="c5d11-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="c5d11-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="c5d11-108">Método Collect</span><span class="sxs-lookup"><span data-stu-id="c5d11-108">Collect Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager-collect-method.md)|<span data-ttu-id="c5d11-109">Força uma coleta de lixo para a geração especificada.</span><span class="sxs-lookup"><span data-stu-id="c5d11-109">Forces a garbage collection for the specified generation.</span></span>|  
|[<span data-ttu-id="c5d11-110">Método GetStats</span><span class="sxs-lookup"><span data-stu-id="c5d11-110">GetStats Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager-getstats-method.md)|<span data-ttu-id="c5d11-111">Obtém um conjunto de estatísticas atuais sobre o sistema de coleta de lixo.</span><span class="sxs-lookup"><span data-stu-id="c5d11-111">Gets a set of current statistics about the garbage collection system.</span></span>|  
|[<span data-ttu-id="c5d11-112">Método SetGCStartupLimits</span><span class="sxs-lookup"><span data-stu-id="c5d11-112">SetGCStartupLimits Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager-setgcstartuplimits-method.md)|<span data-ttu-id="c5d11-113">Define o tamanho de um segmento de coleta de lixo e o tamanho máximo da geração do sistema de coleta de lixo 0.</span><span class="sxs-lookup"><span data-stu-id="c5d11-113">Sets the size of a garbage collection segment and the maximum size of the garbage collection system's generation 0.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c5d11-114">Comentários</span><span class="sxs-lookup"><span data-stu-id="c5d11-114">Remarks</span></span>  
 <span data-ttu-id="c5d11-115">O common language runtime (CLR) implementa seu mecanismo de coleta de lixo com gerenciado <xref:System.GC> tipo.</span><span class="sxs-lookup"><span data-stu-id="c5d11-115">The common language runtime (CLR) implements its garbage collection mechanism with the managed <xref:System.GC> type.</span></span> <span data-ttu-id="c5d11-116">Para obter mais informações sobre o sistema de coleta de lixo, consulte [coleta de lixo](../../../../docs/standard/garbage-collection/index.md).</span><span class="sxs-lookup"><span data-stu-id="c5d11-116">For more information about the garbage collection system, see [Garbage Collection](../../../../docs/standard/garbage-collection/index.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c5d11-117">Requisitos</span><span class="sxs-lookup"><span data-stu-id="c5d11-117">Requirements</span></span>  
 <span data-ttu-id="c5d11-118">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c5d11-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c5d11-119">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="c5d11-119">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="c5d11-120">**Biblioteca:** Incluído como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="c5d11-120">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="c5d11-121">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c5d11-121">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c5d11-122">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c5d11-122">See also</span></span>

- [<span data-ttu-id="c5d11-123">Gerenciamento Automático de Memória</span><span class="sxs-lookup"><span data-stu-id="c5d11-123">Automatic Memory Management</span></span>](../../../../docs/standard/automatic-memory-management.md)
- [<span data-ttu-id="c5d11-124">Estrutura COR_GC_STATS</span><span class="sxs-lookup"><span data-stu-id="c5d11-124">COR_GC_STATS Structure</span></span>](../../../../docs/framework/unmanaged-api/hosting/cor-gc-stats-structure.md)
- [<span data-ttu-id="c5d11-125">Interface ICLRControl</span><span class="sxs-lookup"><span data-stu-id="c5d11-125">ICLRControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)
- [<span data-ttu-id="c5d11-126">Interfaces de hospedagem CLR</span><span class="sxs-lookup"><span data-stu-id="c5d11-126">CLR Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/clr-hosting-interfaces.md)
- [<span data-ttu-id="c5d11-127">Hospedagem de Interfaces</span><span class="sxs-lookup"><span data-stu-id="c5d11-127">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
- [<span data-ttu-id="c5d11-128">Hospedagem</span><span class="sxs-lookup"><span data-stu-id="c5d11-128">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)
