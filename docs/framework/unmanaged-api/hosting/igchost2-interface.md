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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 21ce9cbd007858c0f39e12622eff819154ab83f0
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69928612"
---
# <a name="igchost2-interface"></a><span data-ttu-id="88556-102">Interface IGCHost2</span><span class="sxs-lookup"><span data-stu-id="88556-102">IGCHost2 Interface</span></span>
<span data-ttu-id="88556-103">Fornece métodos para obter informações sobre o sistema de coleta de lixo e para controlar alguns aspectos da coleta de lixo.</span><span class="sxs-lookup"><span data-stu-id="88556-103">Provides methods for obtaining information about the garbage collection system and for controlling some aspects of garbage collection.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="88556-104">Para um novo desenvolvimento, recomendamos que você use a interface [ICLRGCManager2](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager2-interface.md) em vez disso.</span><span class="sxs-lookup"><span data-stu-id="88556-104">For new development, we recommend that you use the [ICLRGCManager2](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager2-interface.md) interface instead.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="88556-105">Métodos</span><span class="sxs-lookup"><span data-stu-id="88556-105">Methods</span></span>  
  
|<span data-ttu-id="88556-106">Método</span><span class="sxs-lookup"><span data-stu-id="88556-106">Method</span></span>|<span data-ttu-id="88556-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="88556-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="88556-108">Método SetGCStartupLimitsEx</span><span class="sxs-lookup"><span data-stu-id="88556-108">SetGCStartupLimitsEx Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/igchost2-setgcstartuplimitsex-method.md)|<span data-ttu-id="88556-109">Define o tamanho do segmento e o tamanho máximo para a geração 0.</span><span class="sxs-lookup"><span data-stu-id="88556-109">Sets the segment size and the maximum size for generation 0.</span></span> <span data-ttu-id="88556-110">Habilita a geração 0 e os tamanhos de `DWORD`segmento maiores que.</span><span class="sxs-lookup"><span data-stu-id="88556-110">Enables generation 0 and segment sizes larger than `DWORD`.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="88556-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="88556-111">Requirements</span></span>  
 <span data-ttu-id="88556-112">**Compatíveis** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="88556-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="88556-113">**Cabeçalho:** GCHost.idl, GCHost.h</span><span class="sxs-lookup"><span data-stu-id="88556-113">**Header:** GCHost.idl, GCHost.h</span></span>  
  
 <span data-ttu-id="88556-114">**Biblioteca** Incluído como um recurso em MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="88556-114">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="88556-115">**Versões do .NET Framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="88556-115">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="88556-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="88556-116">See also</span></span>

- [<span data-ttu-id="88556-117">Hospedagem de Interfaces</span><span class="sxs-lookup"><span data-stu-id="88556-117">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
- [<span data-ttu-id="88556-118">Interfaces de hospedagem CLR</span><span class="sxs-lookup"><span data-stu-id="88556-118">CLR Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/clr-hosting-interfaces.md)
- [<span data-ttu-id="88556-119">Coclass CorRuntimeHost</span><span class="sxs-lookup"><span data-stu-id="88556-119">CorRuntimeHost Coclass</span></span>](../../../../docs/framework/unmanaged-api/hosting/corruntimehost-coclass.md)
