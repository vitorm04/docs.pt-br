---
title: Método IGCHost2::SetGCStartupLimitsEx
ms.date: 03/30/2017
api_name:
- IGCHost2.SetGCStartupLimitsEx
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IGCHost2::SetGCStartupLimitsEx
helpviewer_keywords:
- IGCHost2::SetGCStartupLimitsEx method [.NET Framework hosting]
- SetGCStartupLimitsEx method, IGCHost2 interface [.NET Framework hosting]
ms.assetid: bba941c2-1c57-46d3-bbf5-5fb92700c490
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: da5e90055a08227ea7cb7fa1b459fe6f5f3a81fc
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59127317"
---
# <a name="igchost2setgcstartuplimitsex-method"></a><span data-ttu-id="b297d-102">Método IGCHost2::SetGCStartupLimitsEx</span><span class="sxs-lookup"><span data-stu-id="b297d-102">IGCHost2::SetGCStartupLimitsEx Method</span></span>
<span data-ttu-id="b297d-103">Define o tamanho do segmento e o tamanho máximo para a geração 0.</span><span class="sxs-lookup"><span data-stu-id="b297d-103">Sets the segment size and the maximum size for generation 0.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b297d-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="b297d-104">Syntax</span></span>  
  
```  
HRESULT SetGCStartupLimitsEx (  
    [in] SIZE_T SegmentSize,  
    [in] SIZE_T MaxGen0Size  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b297d-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="b297d-105">Parameters</span></span>  
 `SegmentSize`  
 <span data-ttu-id="b297d-106">[in] O tamanho do segmento usado pelo sistema de coleta de lixo.</span><span class="sxs-lookup"><span data-stu-id="b297d-106">[in] The size of the segment used by the garbage collection system.</span></span>  
  
 `MaxGen0Size`  
 <span data-ttu-id="b297d-107">[in] O tamanho máximo para a geração 0.</span><span class="sxs-lookup"><span data-stu-id="b297d-107">[in] The maximum size for generation 0.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b297d-108">Comentários</span><span class="sxs-lookup"><span data-stu-id="b297d-108">Remarks</span></span>  
 <span data-ttu-id="b297d-109">Os valores que `SetGCStartupLimitsEx` conjuntos podem ser especificados apenas antes que o host é iniciado.</span><span class="sxs-lookup"><span data-stu-id="b297d-109">The values that `SetGCStartupLimitsEx` sets can be specified only before the host is started.</span></span> <span data-ttu-id="b297d-110">Esses valores não podem ser alterados posteriormente.</span><span class="sxs-lookup"><span data-stu-id="b297d-110">These values cannot be changed later.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b297d-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="b297d-111">Requirements</span></span>  
 <span data-ttu-id="b297d-112">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b297d-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b297d-113">**Cabeçalho:** GCHost.idl, GCHost.h</span><span class="sxs-lookup"><span data-stu-id="b297d-113">**Header:** GCHost.idl, GCHost.h</span></span>  
  
 <span data-ttu-id="b297d-114">**Biblioteca:** Incluído como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="b297d-114">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 **<span data-ttu-id="b297d-115">Versões do .NET Framework:</span><span class="sxs-lookup"><span data-stu-id="b297d-115">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="b297d-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b297d-116">See also</span></span>

- [<span data-ttu-id="b297d-117">Interface IGCHost2</span><span class="sxs-lookup"><span data-stu-id="b297d-117">IGCHost2 Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/igchost2-interface.md)
