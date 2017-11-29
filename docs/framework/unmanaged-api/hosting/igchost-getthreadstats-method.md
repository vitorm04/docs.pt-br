---
title: "Método IGCHost::GetThreadStats"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IGCHost.GetThreadStats
api_location: mscoree.dll
api_type: COM
f1_keywords: GetThreadStats
helpviewer_keywords:
- IGCHost::GetThreadStats method [.NET Framework hosting]
- GetThreadStats method [.NET Framework hosting]
ms.assetid: 826baa9b-9218-4736-a509-7ab193b125a0
topic_type: apiref
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 7bfd6b89c3220e071a477e0c5b85e4ee57289762
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="igchostgetthreadstats-method"></a><span data-ttu-id="5b894-102">Método IGCHost::GetThreadStats</span><span class="sxs-lookup"><span data-stu-id="5b894-102">IGCHost::GetThreadStats Method</span></span>
<span data-ttu-id="5b894-103">Obtém as estatísticas por thread de coleta de lixo.</span><span class="sxs-lookup"><span data-stu-id="5b894-103">Gets the per-thread statistics for garbage collection.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5b894-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="5b894-104">Syntax</span></span>  
  
```  
HRESULT GetThreadStats (  
    [in] DWORD *pFiberCookie,  
    [in, out] COR_GC_THREAD_STATS *pStats  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="5b894-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="5b894-105">Parameters</span></span>  
 `pFiberCookie`  
 <span data-ttu-id="5b894-106">[in] Um ponteiro para um cookie de fibra que especifica o thread para o qual recuperar as estatísticas.</span><span class="sxs-lookup"><span data-stu-id="5b894-106">[in] A pointer to a fiber cookie that specifies the thread for which to retrieve the statistics.</span></span>  
  
 `pStats`  
 <span data-ttu-id="5b894-107">[out no] Um ponteiro para um [COR_GC_THREAD_STATS](../../../../docs/framework/unmanaged-api/hosting/cor-gc-thread-stats-structure.md) estrutura que contém as estatísticas de coleta de lixo para o segmento especificado.</span><span class="sxs-lookup"><span data-stu-id="5b894-107">[in, out] A pointer to a [COR_GC_THREAD_STATS](../../../../docs/framework/unmanaged-api/hosting/cor-gc-thread-stats-structure.md) structure that contains the garbage collection statistics for the specified thread.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5b894-108">Requisitos</span><span class="sxs-lookup"><span data-stu-id="5b894-108">Requirements</span></span>  
 <span data-ttu-id="5b894-109">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5b894-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5b894-110">**Cabeçalho:** GCHost.idl, GCHost.h</span><span class="sxs-lookup"><span data-stu-id="5b894-110">**Header:** GCHost.idl, GCHost.h</span></span>  
  
 <span data-ttu-id="5b894-111">**Biblioteca:** incluído como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="5b894-111">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="5b894-112">**Versões do .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5b894-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5b894-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="5b894-113">See Also</span></span>  
 [<span data-ttu-id="5b894-114">Interface IGCHost</span><span class="sxs-lookup"><span data-stu-id="5b894-114">IGCHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/igchost-interface.md)
