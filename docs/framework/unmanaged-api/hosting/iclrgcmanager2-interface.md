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
ms.openlocfilehash: a89a7ef34418163d790fd055de681c1cdf989e57
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59226905"
---
# <a name="iclrgcmanager2-interface"></a><span data-ttu-id="b0e37-102">Interface ICLRGCManager2</span><span class="sxs-lookup"><span data-stu-id="b0e37-102">ICLRGCManager2 Interface</span></span>
<span data-ttu-id="b0e37-103">Fornece métodos que permitem que um host interagir com o sistema de coleta de lixo do common language runtime.</span><span class="sxs-lookup"><span data-stu-id="b0e37-103">Provides methods that allow a host to interact with the common language runtime's garbage collection system.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="b0e37-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="b0e37-104">Methods</span></span>  
  
|<span data-ttu-id="b0e37-105">Método</span><span class="sxs-lookup"><span data-stu-id="b0e37-105">Method</span></span>|<span data-ttu-id="b0e37-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="b0e37-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="b0e37-107">Método SetGCStartupLimitsEx</span><span class="sxs-lookup"><span data-stu-id="b0e37-107">SetGCStartupLimitsEx Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager2-setgcstartuplimitsex-method.md)|<span data-ttu-id="b0e37-108">Define o tamanho de um segmento de coleta de lixo e o tamanho máximo da geração do sistema de coleta de lixo 0.</span><span class="sxs-lookup"><span data-stu-id="b0e37-108">Sets the size of a garbage collection segment and the maximum size of the garbage collection system's generation 0.</span></span> <span data-ttu-id="b0e37-109">Habilita a geração 0 e tamanhos de segmento maiores do que `DWORD`.</span><span class="sxs-lookup"><span data-stu-id="b0e37-109">Enables generation 0 and segment sizes larger than `DWORD`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b0e37-110">Comentários</span><span class="sxs-lookup"><span data-stu-id="b0e37-110">Remarks</span></span>  
 <span data-ttu-id="b0e37-111">Essa interface herda de [ICLRGCManager Interface](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager-interface.md).</span><span class="sxs-lookup"><span data-stu-id="b0e37-111">This interface inherits from the [ICLRGCManager Interface](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager-interface.md).</span></span>  
  
 <span data-ttu-id="b0e37-112">O common language runtime (CLR) implementa seu mecanismo de coleta de lixo com gerenciado <xref:System.GC> tipo.</span><span class="sxs-lookup"><span data-stu-id="b0e37-112">The common language runtime (CLR) implements its garbage collection mechanism with the managed <xref:System.GC> type.</span></span> <span data-ttu-id="b0e37-113">Para obter mais informações sobre o sistema de coleta de lixo, consulte [coleta de lixo](../../../../docs/standard/garbage-collection/index.md).</span><span class="sxs-lookup"><span data-stu-id="b0e37-113">For more information about the garbage collection system, see [Garbage Collection](../../../../docs/standard/garbage-collection/index.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b0e37-114">Requisitos</span><span class="sxs-lookup"><span data-stu-id="b0e37-114">Requirements</span></span>  
 <span data-ttu-id="b0e37-115">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b0e37-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b0e37-116">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="b0e37-116">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="b0e37-117">**Biblioteca:** Incluído como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="b0e37-117">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 **<span data-ttu-id="b0e37-118">Versões do .NET Framework:</span><span class="sxs-lookup"><span data-stu-id="b0e37-118">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="b0e37-119">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b0e37-119">See also</span></span>

- [<span data-ttu-id="b0e37-120">Gerenciamento automático de memória</span><span class="sxs-lookup"><span data-stu-id="b0e37-120">Automatic Memory Management</span></span>](../../../../docs/standard/automatic-memory-management.md)
- [<span data-ttu-id="b0e37-121">Estrutura COR_GC_STATS</span><span class="sxs-lookup"><span data-stu-id="b0e37-121">COR_GC_STATS Structure</span></span>](../../../../docs/framework/unmanaged-api/hosting/cor-gc-stats-structure.md)
- [<span data-ttu-id="b0e37-122">Interface ICLRControl</span><span class="sxs-lookup"><span data-stu-id="b0e37-122">ICLRControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)
- [<span data-ttu-id="b0e37-123">Interfaces de hospedagem CLR adicionadas no .NET Framework 4 e 4.5</span><span class="sxs-lookup"><span data-stu-id="b0e37-123">CLR Hosting Interfaces Added in the .NET Framework 4 and 4.5</span></span>](../../../../docs/framework/unmanaged-api/hosting/clr-hosting-interfaces-added-in-the-net-framework-4-and-4-5.md)
- [<span data-ttu-id="b0e37-124">Interfaces de hospedagem</span><span class="sxs-lookup"><span data-stu-id="b0e37-124">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
- [<span data-ttu-id="b0e37-125">Hospedagem</span><span class="sxs-lookup"><span data-stu-id="b0e37-125">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)
