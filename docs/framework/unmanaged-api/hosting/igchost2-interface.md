---
title: Interface IGCHost2
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
- IGCHost2
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IGCHost2
helpviewer_keywords:
- IGCHost2 interface [.NET Framework hosting]
ms.assetid: e5323fa4-18ac-424d-859d-a65a550d08d9
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: a616e724d6fb26734fcda48d6a9b39605e0284a5
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="igchost2-interface"></a><span data-ttu-id="d80ed-102">Interface IGCHost2</span><span class="sxs-lookup"><span data-stu-id="d80ed-102">IGCHost2 Interface</span></span>
<span data-ttu-id="d80ed-103">Fornece métodos para obter informações sobre o sistema de coleta de lixo e para controlar alguns aspectos da coleta de lixo.</span><span class="sxs-lookup"><span data-stu-id="d80ed-103">Provides methods for obtaining information about the garbage collection system and for controlling some aspects of garbage collection.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d80ed-104">Para novos desenvolvimentos, recomendamos que você use o [ICLRGCManager2](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager2-interface.md) interface em vez disso.</span><span class="sxs-lookup"><span data-stu-id="d80ed-104">For new development, we recommend that you use the [ICLRGCManager2](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager2-interface.md) interface instead.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="d80ed-105">Métodos</span><span class="sxs-lookup"><span data-stu-id="d80ed-105">Methods</span></span>  
  
|<span data-ttu-id="d80ed-106">Método</span><span class="sxs-lookup"><span data-stu-id="d80ed-106">Method</span></span>|<span data-ttu-id="d80ed-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="d80ed-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="d80ed-108">Método SetGCStartupLimitsEx</span><span class="sxs-lookup"><span data-stu-id="d80ed-108">SetGCStartupLimitsEx Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/igchost2-setgcstartuplimitsex-method.md)|<span data-ttu-id="d80ed-109">Define o tamanho do segmento e o tamanho máximo de geração 0.</span><span class="sxs-lookup"><span data-stu-id="d80ed-109">Sets the segment size and the maximum size for generation 0.</span></span> <span data-ttu-id="d80ed-110">Habilita a geração 0 e tamanhos de segmento maior do que `DWORD`.</span><span class="sxs-lookup"><span data-stu-id="d80ed-110">Enables generation 0 and segment sizes larger than `DWORD`.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="d80ed-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="d80ed-111">Requirements</span></span>  
 <span data-ttu-id="d80ed-112">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d80ed-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d80ed-113">**Cabeçalho:** GCHost.idl, GCHost.h</span><span class="sxs-lookup"><span data-stu-id="d80ed-113">**Header:** GCHost.idl, GCHost.h</span></span>  
  
 <span data-ttu-id="d80ed-114">**Biblioteca:** incluído como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="d80ed-114">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="d80ed-115">**Versões do .NET framework:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d80ed-115">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d80ed-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="d80ed-116">See Also</span></span>  
 [<span data-ttu-id="d80ed-117">Hospedagem de Interfaces</span><span class="sxs-lookup"><span data-stu-id="d80ed-117">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)  
 [<span data-ttu-id="d80ed-118">Interfaces de hospedagem CLR</span><span class="sxs-lookup"><span data-stu-id="d80ed-118">CLR Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/clr-hosting-interfaces.md)  
 [<span data-ttu-id="d80ed-119">Coclass CorRuntimeHost</span><span class="sxs-lookup"><span data-stu-id="d80ed-119">CorRuntimeHost Coclass</span></span>](../../../../docs/framework/unmanaged-api/hosting/corruntimehost-coclass.md)
