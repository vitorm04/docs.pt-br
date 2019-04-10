---
title: Método IGCHost::GetStats
ms.date: 03/30/2017
api_name:
- IGCHost.GetStats
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- GetStats
helpviewer_keywords:
- GetStats method, IGCHost interface [.NET Framework hosting]
- IGCHost::GetStats method [.NET Framework hosting]
ms.assetid: c4ae022c-46ac-4f19-9ddd-09b955f19412
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 14751b41809eeda5e6bd990fae368879d0f30492
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59227828"
---
# <a name="igchostgetstats-method"></a><span data-ttu-id="cc44c-102">Método IGCHost::GetStats</span><span class="sxs-lookup"><span data-stu-id="cc44c-102">IGCHost::GetStats Method</span></span>
<span data-ttu-id="cc44c-103">Obtém as estatísticas para o estado atual do sistema de coleta de lixo.</span><span class="sxs-lookup"><span data-stu-id="cc44c-103">Gets the statistics for the current state of the garbage collection system.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cc44c-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="cc44c-104">Syntax</span></span>  
  
```  
HRESULT GetStats (  
    [in, out] COR_GC_STATS *pStats  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="cc44c-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="cc44c-105">Parameters</span></span>  
 `pStats`  
 <span data-ttu-id="cc44c-106">[no, out] Um ponteiro para um [COR_GC_STATS](../../../../docs/framework/unmanaged-api/hosting/cor-gc-stats-structure.md) estrutura que contém as estatísticas para o estado atual do sistema de coleta de lixo.</span><span class="sxs-lookup"><span data-stu-id="cc44c-106">[in, out] A pointer to a [COR_GC_STATS](../../../../docs/framework/unmanaged-api/hosting/cor-gc-stats-structure.md) structure that contains the statistics for the current state of the garbage collection system.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="cc44c-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="cc44c-107">Remarks</span></span>  
 <span data-ttu-id="cc44c-108">As estatísticas podem ser usadas por um sistema inteligente de alocação para ajudar o sistema de coleta de lixo funcionar.</span><span class="sxs-lookup"><span data-stu-id="cc44c-108">The statistics can be used by a smart allocation system to help the garbage collection system operate.</span></span> <span data-ttu-id="cc44c-109">Por exemplo, o sistema de alocação pode determinar, depois de revisar as estatísticas, o que ele precisa adicionar mais memória ou forçar uma coleta.</span><span class="sxs-lookup"><span data-stu-id="cc44c-109">For example, the allocation system may determine, after reviewing the statistics, that it needs to add more memory or force a collection.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cc44c-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="cc44c-110">Requirements</span></span>  
 <span data-ttu-id="cc44c-111">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cc44c-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cc44c-112">**Cabeçalho:** GCHost.idl, GCHost.h</span><span class="sxs-lookup"><span data-stu-id="cc44c-112">**Header:** GCHost.idl, GCHost.h</span></span>  
  
 <span data-ttu-id="cc44c-113">**Biblioteca:** Incluído como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="cc44c-113">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 **<span data-ttu-id="cc44c-114">Versões do .NET Framework:</span><span class="sxs-lookup"><span data-stu-id="cc44c-114">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="cc44c-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="cc44c-115">See also</span></span>

- [<span data-ttu-id="cc44c-116">Interface IGCHost</span><span class="sxs-lookup"><span data-stu-id="cc44c-116">IGCHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/igchost-interface.md)
