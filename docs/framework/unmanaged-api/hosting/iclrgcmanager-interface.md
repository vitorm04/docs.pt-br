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
ms.openlocfilehash: 76a50be6da790ed7bd193c489d36e2823cdbe587
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83616951"
---
# <a name="iclrgcmanager-interface"></a><span data-ttu-id="4f1e7-102">Interface ICLRGCManager</span><span class="sxs-lookup"><span data-stu-id="4f1e7-102">ICLRGCManager Interface</span></span>
<span data-ttu-id="4f1e7-103">Fornece métodos que permitem que um host interaja com o sistema de coleta de lixo do Common Language Runtime.</span><span class="sxs-lookup"><span data-stu-id="4f1e7-103">Provides methods that allow a host to interact with the common language runtime's garbage collection system.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="4f1e7-104">Começando com o .NET Framework 4,5, você pode usar o método [ICLRGCManager2:: SetGCStartupLimitsEx](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager2-setgcstartuplimitsex-method.md) para definir o tamanho de um segmento de coleta de lixo e o tamanho máximo da geração 0 do sistema de coleta de lixo para valores maiores que o `DWORD` limite imposto pelo método [SetGCStartupLimits](iclrgcmanager-setgcstartuplimits-method.md) .</span><span class="sxs-lookup"><span data-stu-id="4f1e7-104">Starting with the .NET Framework 4.5, you can use the [ICLRGCManager2::SetGCStartupLimitsEx](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager2-setgcstartuplimitsex-method.md) method to set the size of a garbage collection segment and the maximum size of the garbage collection system's generation 0 to values greater than the `DWORD` limit that is imposed by the [SetGCStartupLimits](iclrgcmanager-setgcstartuplimits-method.md) method.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="4f1e7-105">Métodos</span><span class="sxs-lookup"><span data-stu-id="4f1e7-105">Methods</span></span>  
  
|<span data-ttu-id="4f1e7-106">Método</span><span class="sxs-lookup"><span data-stu-id="4f1e7-106">Method</span></span>|<span data-ttu-id="4f1e7-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="4f1e7-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="4f1e7-108">Método Collect</span><span class="sxs-lookup"><span data-stu-id="4f1e7-108">Collect Method</span></span>](iclrgcmanager-collect-method.md)|<span data-ttu-id="4f1e7-109">Força uma coleta de lixo para a geração especificada.</span><span class="sxs-lookup"><span data-stu-id="4f1e7-109">Forces a garbage collection for the specified generation.</span></span>|  
|[<span data-ttu-id="4f1e7-110">Método GetStats</span><span class="sxs-lookup"><span data-stu-id="4f1e7-110">GetStats Method</span></span>](iclrgcmanager-getstats-method.md)|<span data-ttu-id="4f1e7-111">Obtém um conjunto de estatísticas atuais sobre o sistema de coleta de lixo.</span><span class="sxs-lookup"><span data-stu-id="4f1e7-111">Gets a set of current statistics about the garbage collection system.</span></span>|  
|[<span data-ttu-id="4f1e7-112">Método SetGCStartupLimits</span><span class="sxs-lookup"><span data-stu-id="4f1e7-112">SetGCStartupLimits Method</span></span>](iclrgcmanager-setgcstartuplimits-method.md)|<span data-ttu-id="4f1e7-113">Define o tamanho de um segmento de coleta de lixo e o tamanho máximo da geração 0 do sistema de coleta de lixo.</span><span class="sxs-lookup"><span data-stu-id="4f1e7-113">Sets the size of a garbage collection segment and the maximum size of the garbage collection system's generation 0.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4f1e7-114">Comentários</span><span class="sxs-lookup"><span data-stu-id="4f1e7-114">Remarks</span></span>  
 <span data-ttu-id="4f1e7-115">O Common Language Runtime (CLR) implementa seu mecanismo de coleta de lixo com o <xref:System.GC> tipo gerenciado.</span><span class="sxs-lookup"><span data-stu-id="4f1e7-115">The common language runtime (CLR) implements its garbage collection mechanism with the managed <xref:System.GC> type.</span></span> <span data-ttu-id="4f1e7-116">Para obter mais informações sobre o sistema de coleta de lixo, consulte [coleta de lixo](../../../standard/garbage-collection/index.md).</span><span class="sxs-lookup"><span data-stu-id="4f1e7-116">For more information about the garbage collection system, see [Garbage Collection](../../../standard/garbage-collection/index.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4f1e7-117">Requisitos</span><span class="sxs-lookup"><span data-stu-id="4f1e7-117">Requirements</span></span>  
 <span data-ttu-id="4f1e7-118">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4f1e7-118">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4f1e7-119">**Cabeçalho:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="4f1e7-119">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="4f1e7-120">**Biblioteca:** Incluído como um recurso em MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="4f1e7-120">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="4f1e7-121">**.NET Framework versões:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4f1e7-121">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4f1e7-122">Veja também</span><span class="sxs-lookup"><span data-stu-id="4f1e7-122">See also</span></span>

- [<span data-ttu-id="4f1e7-123">Gerenciamento automático de memória</span><span class="sxs-lookup"><span data-stu-id="4f1e7-123">Automatic Memory Management</span></span>](../../../standard/automatic-memory-management.md)
- [<span data-ttu-id="4f1e7-124">Estrutura COR_GC_STATS</span><span class="sxs-lookup"><span data-stu-id="4f1e7-124">COR_GC_STATS Structure</span></span>](cor-gc-stats-structure.md)
- [<span data-ttu-id="4f1e7-125">Interface ICLRControl</span><span class="sxs-lookup"><span data-stu-id="4f1e7-125">ICLRControl Interface</span></span>](iclrcontrol-interface.md)
- [<span data-ttu-id="4f1e7-126">Interfaces de hospedagem CLR</span><span class="sxs-lookup"><span data-stu-id="4f1e7-126">CLR Hosting Interfaces</span></span>](clr-hosting-interfaces.md)
- [<span data-ttu-id="4f1e7-127">Interfaces de hospedagem</span><span class="sxs-lookup"><span data-stu-id="4f1e7-127">Hosting Interfaces</span></span>](hosting-interfaces.md)
- [<span data-ttu-id="4f1e7-128">Hospedagem</span><span class="sxs-lookup"><span data-stu-id="4f1e7-128">Hosting</span></span>](index.md)
