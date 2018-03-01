---
title: Interface ICLRGCManager2
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- ICLRGCManager2
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRGCManager2
helpviewer_keywords:
- ICLRGCManager2 interface [.NET Framework hosting]
ms.assetid: 4b5ffd7b-9ad7-41cd-9bba-34030ae3da7e
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 4a8b51cf4297c1ccadbef8730c06148263d310e2
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="iclrgcmanager2-interface"></a><span data-ttu-id="70bd7-102">Interface ICLRGCManager2</span><span class="sxs-lookup"><span data-stu-id="70bd7-102">ICLRGCManager2 Interface</span></span>
<span data-ttu-id="70bd7-103">Fornece métodos que permitem que um host interagir com o sistema de coleta de lixo do common language runtime.</span><span class="sxs-lookup"><span data-stu-id="70bd7-103">Provides methods that allow a host to interact with the common language runtime's garbage collection system.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="70bd7-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="70bd7-104">Methods</span></span>  
  
|<span data-ttu-id="70bd7-105">Método</span><span class="sxs-lookup"><span data-stu-id="70bd7-105">Method</span></span>|<span data-ttu-id="70bd7-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="70bd7-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="70bd7-107">Método SetGCStartupLimitsEx</span><span class="sxs-lookup"><span data-stu-id="70bd7-107">SetGCStartupLimitsEx Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager2-setgcstartuplimitsex-method.md)|<span data-ttu-id="70bd7-108">Define o tamanho de um segmento de coleta de lixo e o tamanho máximo da geração do sistema de coleta de lixo 0.</span><span class="sxs-lookup"><span data-stu-id="70bd7-108">Sets the size of a garbage collection segment and the maximum size of the garbage collection system's generation 0.</span></span> <span data-ttu-id="70bd7-109">Habilita a geração 0 e tamanhos de segmento maior do que `DWORD`.</span><span class="sxs-lookup"><span data-stu-id="70bd7-109">Enables generation 0 and segment sizes larger than `DWORD`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="70bd7-110">Comentários</span><span class="sxs-lookup"><span data-stu-id="70bd7-110">Remarks</span></span>  
 <span data-ttu-id="70bd7-111">Essa interface herda o [ICLRGCManager Interface](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager-interface.md).</span><span class="sxs-lookup"><span data-stu-id="70bd7-111">This interface inherits from the [ICLRGCManager Interface](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager-interface.md).</span></span>  
  
 <span data-ttu-id="70bd7-112">O common language runtime (CLR) implementa seu mecanismo de coleta de lixo com gerenciado <xref:System.GC> tipo.</span><span class="sxs-lookup"><span data-stu-id="70bd7-112">The common language runtime (CLR) implements its garbage collection mechanism with the managed <xref:System.GC> type.</span></span> <span data-ttu-id="70bd7-113">Para obter mais informações sobre o sistema de coleta de lixo, consulte [coleta de lixo](../../../../docs/standard/garbage-collection/index.md).</span><span class="sxs-lookup"><span data-stu-id="70bd7-113">For more information about the garbage collection system, see [Garbage Collection](../../../../docs/standard/garbage-collection/index.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="70bd7-114">Requisitos</span><span class="sxs-lookup"><span data-stu-id="70bd7-114">Requirements</span></span>  
 <span data-ttu-id="70bd7-115">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="70bd7-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="70bd7-116">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="70bd7-116">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="70bd7-117">**Biblioteca:** incluído como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="70bd7-117">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="70bd7-118">**Versões do .NET framework:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="70bd7-118">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="70bd7-119">Consulte também</span><span class="sxs-lookup"><span data-stu-id="70bd7-119">See Also</span></span>  
 [<span data-ttu-id="70bd7-120">Gerenciamento Automático de Memória</span><span class="sxs-lookup"><span data-stu-id="70bd7-120">Automatic Memory Management</span></span>](../../../../docs/standard/automatic-memory-management.md)  
 [<span data-ttu-id="70bd7-121">Estrutura COR_GC_STATS</span><span class="sxs-lookup"><span data-stu-id="70bd7-121">COR_GC_STATS Structure</span></span>](../../../../docs/framework/unmanaged-api/hosting/cor-gc-stats-structure.md)  
 [<span data-ttu-id="70bd7-122">Interface ICLRControl</span><span class="sxs-lookup"><span data-stu-id="70bd7-122">ICLRControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)  
 [<span data-ttu-id="70bd7-123">Interfaces de hospedagem CLR adicionadas ao .NET Framework 4 e 4.5</span><span class="sxs-lookup"><span data-stu-id="70bd7-123">CLR Hosting Interfaces Added in the .NET Framework 4 and 4.5</span></span>](../../../../docs/framework/unmanaged-api/hosting/clr-hosting-interfaces-added-in-the-net-framework-4-and-4-5.md)  
 [<span data-ttu-id="70bd7-124">Hospedagem de Interfaces</span><span class="sxs-lookup"><span data-stu-id="70bd7-124">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)  
 [<span data-ttu-id="70bd7-125">Hospedagem</span><span class="sxs-lookup"><span data-stu-id="70bd7-125">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)
