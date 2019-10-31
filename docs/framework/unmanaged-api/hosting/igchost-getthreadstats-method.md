---
title: Método IGCHost::GetThreadStats
ms.date: 03/30/2017
api_name:
- IGCHost.GetThreadStats
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- GetThreadStats
helpviewer_keywords:
- IGCHost::GetThreadStats method [.NET Framework hosting]
- GetThreadStats method [.NET Framework hosting]
ms.assetid: 826baa9b-9218-4736-a509-7ab193b125a0
topic_type:
- apiref
ms.openlocfilehash: 36eeb7ed4f80979ef2edb930e65963a1db0c894f
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73134900"
---
# <a name="igchostgetthreadstats-method"></a><span data-ttu-id="cf515-102">Método IGCHost::GetThreadStats</span><span class="sxs-lookup"><span data-stu-id="cf515-102">IGCHost::GetThreadStats Method</span></span>
<span data-ttu-id="cf515-103">Obtém as estatísticas por thread para a coleta de lixo.</span><span class="sxs-lookup"><span data-stu-id="cf515-103">Gets the per-thread statistics for garbage collection.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cf515-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="cf515-104">Syntax</span></span>  
  
```cpp  
HRESULT GetThreadStats (  
    [in] DWORD *pFiberCookie,  
    [in, out] COR_GC_THREAD_STATS *pStats  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="cf515-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="cf515-105">Parameters</span></span>  
 `pFiberCookie`  
 <span data-ttu-id="cf515-106">no Um ponteiro para um cookie de fibra que especifica o thread para o qual recuperar as estatísticas.</span><span class="sxs-lookup"><span data-stu-id="cf515-106">[in] A pointer to a fiber cookie that specifies the thread for which to retrieve the statistics.</span></span>  
  
 `pStats`  
 <span data-ttu-id="cf515-107">[entrada, saída] Um ponteiro para uma estrutura [COR_GC_THREAD_STATS](../../../../docs/framework/unmanaged-api/hosting/cor-gc-thread-stats-structure.md) que contém as estatísticas de coleta de lixo para o thread especificado.</span><span class="sxs-lookup"><span data-stu-id="cf515-107">[in, out] A pointer to a [COR_GC_THREAD_STATS](../../../../docs/framework/unmanaged-api/hosting/cor-gc-thread-stats-structure.md) structure that contains the garbage collection statistics for the specified thread.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cf515-108">Requisitos</span><span class="sxs-lookup"><span data-stu-id="cf515-108">Requirements</span></span>  
 <span data-ttu-id="cf515-109">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cf515-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cf515-110">**Cabeçalho:** GCHost. idl, GCHost. h</span><span class="sxs-lookup"><span data-stu-id="cf515-110">**Header:** GCHost.idl, GCHost.h</span></span>  
  
 <span data-ttu-id="cf515-111">**Biblioteca:** Incluído como um recurso em MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="cf515-111">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="cf515-112">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cf515-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cf515-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="cf515-113">See also</span></span>

- [<span data-ttu-id="cf515-114">Interface IGCHost</span><span class="sxs-lookup"><span data-stu-id="cf515-114">IGCHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/igchost-interface.md)
