---
title: Interface ICLRGCManager2
ms.date: 03/30/2017
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c54707d4c767fbb644ed892767be8351d2fd95b5
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69966183"
---
# <a name="iclrgcmanager2-interface"></a><span data-ttu-id="9ce18-102">Interface ICLRGCManager2</span><span class="sxs-lookup"><span data-stu-id="9ce18-102">ICLRGCManager2 Interface</span></span>
<span data-ttu-id="9ce18-103">Fornece métodos que permitem que um host interaja com o sistema de coleta de lixo do Common Language Runtime.</span><span class="sxs-lookup"><span data-stu-id="9ce18-103">Provides methods that allow a host to interact with the common language runtime's garbage collection system.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="9ce18-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="9ce18-104">Methods</span></span>  
  
|<span data-ttu-id="9ce18-105">Método</span><span class="sxs-lookup"><span data-stu-id="9ce18-105">Method</span></span>|<span data-ttu-id="9ce18-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="9ce18-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="9ce18-107">Método SetGCStartupLimitsEx</span><span class="sxs-lookup"><span data-stu-id="9ce18-107">SetGCStartupLimitsEx Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager2-setgcstartuplimitsex-method.md)|<span data-ttu-id="9ce18-108">Define o tamanho de um segmento de coleta de lixo e o tamanho máximo da geração 0 do sistema de coleta de lixo.</span><span class="sxs-lookup"><span data-stu-id="9ce18-108">Sets the size of a garbage collection segment and the maximum size of the garbage collection system's generation 0.</span></span> <span data-ttu-id="9ce18-109">Habilita a geração 0 e os tamanhos de `DWORD`segmento maiores que.</span><span class="sxs-lookup"><span data-stu-id="9ce18-109">Enables generation 0 and segment sizes larger than `DWORD`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9ce18-110">Comentários</span><span class="sxs-lookup"><span data-stu-id="9ce18-110">Remarks</span></span>  
 <span data-ttu-id="9ce18-111">Essa interface herda da [interface ICLRGCManager](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager-interface.md).</span><span class="sxs-lookup"><span data-stu-id="9ce18-111">This interface inherits from the [ICLRGCManager Interface](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager-interface.md).</span></span>  
  
 <span data-ttu-id="9ce18-112">O Common Language Runtime (CLR) implementa seu mecanismo de coleta de lixo com <xref:System.GC> o tipo gerenciado.</span><span class="sxs-lookup"><span data-stu-id="9ce18-112">The common language runtime (CLR) implements its garbage collection mechanism with the managed <xref:System.GC> type.</span></span> <span data-ttu-id="9ce18-113">Para obter mais informações sobre o sistema de coleta de lixo, consulte [coleta de lixo](../../../standard/garbage-collection/index.md).</span><span class="sxs-lookup"><span data-stu-id="9ce18-113">For more information about the garbage collection system, see [Garbage Collection](../../../standard/garbage-collection/index.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9ce18-114">Requisitos</span><span class="sxs-lookup"><span data-stu-id="9ce18-114">Requirements</span></span>  
 <span data-ttu-id="9ce18-115">**Compatíveis** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9ce18-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9ce18-116">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="9ce18-116">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="9ce18-117">**Biblioteca** Incluído como um recurso em MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="9ce18-117">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="9ce18-118">**Versões do .NET Framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9ce18-118">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9ce18-119">Consulte também</span><span class="sxs-lookup"><span data-stu-id="9ce18-119">See also</span></span>

- [<span data-ttu-id="9ce18-120">Gerenciamento Automático de Memória</span><span class="sxs-lookup"><span data-stu-id="9ce18-120">Automatic Memory Management</span></span>](../../../standard/automatic-memory-management.md)
- [<span data-ttu-id="9ce18-121">Estrutura COR_GC_STATS</span><span class="sxs-lookup"><span data-stu-id="9ce18-121">COR_GC_STATS Structure</span></span>](../../../../docs/framework/unmanaged-api/hosting/cor-gc-stats-structure.md)
- [<span data-ttu-id="9ce18-122">Interface ICLRControl</span><span class="sxs-lookup"><span data-stu-id="9ce18-122">ICLRControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)
- [<span data-ttu-id="9ce18-123">Interfaces de hospedagem CLR adicionadas ao .NET Framework 4 e 4.5</span><span class="sxs-lookup"><span data-stu-id="9ce18-123">CLR Hosting Interfaces Added in the .NET Framework 4 and 4.5</span></span>](../../../../docs/framework/unmanaged-api/hosting/clr-hosting-interfaces-added-in-the-net-framework-4-and-4-5.md)
- [<span data-ttu-id="9ce18-124">Hospedagem de Interfaces</span><span class="sxs-lookup"><span data-stu-id="9ce18-124">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
- [<span data-ttu-id="9ce18-125">Hospedagem</span><span class="sxs-lookup"><span data-stu-id="9ce18-125">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)
