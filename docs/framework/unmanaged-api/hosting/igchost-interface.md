---
title: Interface IGCHost
ms.date: 03/30/2017
api_name:
- IGCHost
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IGCHost
helpviewer_keywords:
- IGCHost interface [.NET Framework hosting]
ms.assetid: 9ad70ffd-6963-4ab2-8c84-3d86c3fb8deb
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1d3f588bfc9799ed4591114b28d081ab417678b1
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69914803"
---
# <a name="igchost-interface"></a><span data-ttu-id="0de2b-102">Interface IGCHost</span><span class="sxs-lookup"><span data-stu-id="0de2b-102">IGCHost Interface</span></span>
<span data-ttu-id="0de2b-103">Fornece métodos para obter informações sobre o sistema de coleta de lixo e para controlar alguns aspectos da coleta de lixo.</span><span class="sxs-lookup"><span data-stu-id="0de2b-103">Provides methods for obtaining information about the garbage collection system and for controlling some aspects of garbage collection.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="0de2b-104">Começando com o .NET Framework 4,5, você pode usar o método [IGCHost2:: SetGCStartupLimitsEx](../../../../docs/framework/unmanaged-api/hosting/igchost2-setgcstartuplimitsex-method.md) para definir o tamanho de um segmento de coleta de lixo e o tamanho máximo da geração 0 do sistema de coleta de lixo para valores `DWORD` maiores que o limite imposto pelo método [SetGCStartupLimits](../../../../docs/framework/unmanaged-api/hosting/igchost-setgcstartuplimits-method.md) .</span><span class="sxs-lookup"><span data-stu-id="0de2b-104">Starting with the .NET Framework 4.5, you can use the [IGCHost2::SetGCStartupLimitsEx](../../../../docs/framework/unmanaged-api/hosting/igchost2-setgcstartuplimitsex-method.md) method to set the size of a garbage collection segment and the maximum size of the garbage collection system's generation 0 to values greater than the `DWORD` limit that is imposed by the [SetGCStartupLimits](../../../../docs/framework/unmanaged-api/hosting/igchost-setgcstartuplimits-method.md) method.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="0de2b-105">Essa interface é apenas para uso de especialistas.</span><span class="sxs-lookup"><span data-stu-id="0de2b-105">This interface is for expert usage only.</span></span> <span data-ttu-id="0de2b-106">Ele pode afetar o desempenho de um aplicativo se for usado de forma inadequada.</span><span class="sxs-lookup"><span data-stu-id="0de2b-106">It can affect the performance of an application if used improperly.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="0de2b-107">Métodos</span><span class="sxs-lookup"><span data-stu-id="0de2b-107">Methods</span></span>  
  
|<span data-ttu-id="0de2b-108">Método</span><span class="sxs-lookup"><span data-stu-id="0de2b-108">Method</span></span>|<span data-ttu-id="0de2b-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="0de2b-109">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="0de2b-110">Método Collect</span><span class="sxs-lookup"><span data-stu-id="0de2b-110">Collect Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/igchost-collect-method.md)|<span data-ttu-id="0de2b-111">Força a ocorrência de uma coleção para a geração determinada, independentemente do estado da coleta de lixo atual.</span><span class="sxs-lookup"><span data-stu-id="0de2b-111">Forces a collection to occur for the given generation, regardless of the state of the current garbage collection.</span></span>|  
|[<span data-ttu-id="0de2b-112">Método GetStats</span><span class="sxs-lookup"><span data-stu-id="0de2b-112">GetStats Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/igchost-getstats-method.md)|<span data-ttu-id="0de2b-113">Obtém as estatísticas do estado atual do sistema de coleta de lixo.</span><span class="sxs-lookup"><span data-stu-id="0de2b-113">Gets the statistics for the current state of the garbage collection system.</span></span>|  
|[<span data-ttu-id="0de2b-114">Método GetThreadStats</span><span class="sxs-lookup"><span data-stu-id="0de2b-114">GetThreadStats Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/igchost-getthreadstats-method.md)|<span data-ttu-id="0de2b-115">Obtém as estatísticas por thread para a coleta de lixo.</span><span class="sxs-lookup"><span data-stu-id="0de2b-115">Gets the per-thread statistics for garbage collection.</span></span>|  
|[<span data-ttu-id="0de2b-116">Método SetGCStartupLimits</span><span class="sxs-lookup"><span data-stu-id="0de2b-116">SetGCStartupLimits Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/igchost-setgcstartuplimits-method.md)|<span data-ttu-id="0de2b-117">Define o tamanho do segmento e o tamanho máximo para a geração 0.</span><span class="sxs-lookup"><span data-stu-id="0de2b-117">Sets the segment size and the maximum size for generation 0.</span></span>|  
|[<span data-ttu-id="0de2b-118">Método SetVirtualMemLimit</span><span class="sxs-lookup"><span data-stu-id="0de2b-118">SetVirtualMemLimit Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/igchost-setvirtualmemlimit-method.md)|<span data-ttu-id="0de2b-119">Define o tamanho máximo da memória virtual do tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="0de2b-119">Sets the maximum size of the runtime's virtual memory.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="0de2b-120">Requisitos</span><span class="sxs-lookup"><span data-stu-id="0de2b-120">Requirements</span></span>  
 <span data-ttu-id="0de2b-121">**Compatíveis** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0de2b-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0de2b-122">**Cabeçalho:** GCHost.idl, GCHost.h</span><span class="sxs-lookup"><span data-stu-id="0de2b-122">**Header:** GCHost.idl, GCHost.h</span></span>  
  
 <span data-ttu-id="0de2b-123">**Biblioteca** Incluído como um recurso em MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="0de2b-123">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="0de2b-124">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0de2b-124">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0de2b-125">Consulte também</span><span class="sxs-lookup"><span data-stu-id="0de2b-125">See also</span></span>

- [<span data-ttu-id="0de2b-126">Hospedagem de Interfaces</span><span class="sxs-lookup"><span data-stu-id="0de2b-126">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
- [<span data-ttu-id="0de2b-127">Coclass CorRuntimeHost</span><span class="sxs-lookup"><span data-stu-id="0de2b-127">CorRuntimeHost Coclass</span></span>](../../../../docs/framework/unmanaged-api/hosting/corruntimehost-coclass.md)
