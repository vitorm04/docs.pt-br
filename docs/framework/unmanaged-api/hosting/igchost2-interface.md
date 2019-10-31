---
title: Interface IGCHost2
ms.date: 03/30/2017
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
ms.openlocfilehash: 43c16415c91521194e0d88be84dd176c3fdadad1
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73134845"
---
# <a name="igchost2-interface"></a><span data-ttu-id="6afe4-102">Interface IGCHost2</span><span class="sxs-lookup"><span data-stu-id="6afe4-102">IGCHost2 Interface</span></span>
<span data-ttu-id="6afe4-103">Fornece métodos para obter informações sobre o sistema de coleta de lixo e para controlar alguns aspectos da coleta de lixo.</span><span class="sxs-lookup"><span data-stu-id="6afe4-103">Provides methods for obtaining information about the garbage collection system and for controlling some aspects of garbage collection.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="6afe4-104">Para um novo desenvolvimento, recomendamos que você use a interface [ICLRGCManager2](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager2-interface.md) em vez disso.</span><span class="sxs-lookup"><span data-stu-id="6afe4-104">For new development, we recommend that you use the [ICLRGCManager2](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager2-interface.md) interface instead.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="6afe4-105">Métodos</span><span class="sxs-lookup"><span data-stu-id="6afe4-105">Methods</span></span>  
  
|<span data-ttu-id="6afe4-106">Método</span><span class="sxs-lookup"><span data-stu-id="6afe4-106">Method</span></span>|<span data-ttu-id="6afe4-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="6afe4-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="6afe4-108">Método SetGCStartupLimitsEx</span><span class="sxs-lookup"><span data-stu-id="6afe4-108">SetGCStartupLimitsEx Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/igchost2-setgcstartuplimitsex-method.md)|<span data-ttu-id="6afe4-109">Define o tamanho do segmento e o tamanho máximo para a geração 0.</span><span class="sxs-lookup"><span data-stu-id="6afe4-109">Sets the segment size and the maximum size for generation 0.</span></span> <span data-ttu-id="6afe4-110">Habilita a geração 0 e os tamanhos de segmento maiores que `DWORD`.</span><span class="sxs-lookup"><span data-stu-id="6afe4-110">Enables generation 0 and segment sizes larger than `DWORD`.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="6afe4-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="6afe4-111">Requirements</span></span>  
 <span data-ttu-id="6afe4-112">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6afe4-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6afe4-113">**Cabeçalho:** GCHost. idl, GCHost. h</span><span class="sxs-lookup"><span data-stu-id="6afe4-113">**Header:** GCHost.idl, GCHost.h</span></span>  
  
 <span data-ttu-id="6afe4-114">**Biblioteca:** Incluído como um recurso em MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="6afe4-114">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="6afe4-115">**Versões do .NET Framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6afe4-115">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6afe4-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="6afe4-116">See also</span></span>

- [<span data-ttu-id="6afe4-117">Hospedagem de Interfaces</span><span class="sxs-lookup"><span data-stu-id="6afe4-117">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
- [<span data-ttu-id="6afe4-118">Interfaces de hospedagem CLR</span><span class="sxs-lookup"><span data-stu-id="6afe4-118">CLR Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/clr-hosting-interfaces.md)
- [<span data-ttu-id="6afe4-119">Coclass CorRuntimeHost</span><span class="sxs-lookup"><span data-stu-id="6afe4-119">CorRuntimeHost Coclass</span></span>](../../../../docs/framework/unmanaged-api/hosting/corruntimehost-coclass.md)
