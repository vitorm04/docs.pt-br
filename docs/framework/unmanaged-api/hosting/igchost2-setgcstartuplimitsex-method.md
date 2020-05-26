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
ms.openlocfilehash: ca9566168b8aae361af8d61539066624697a2d04
ms.sourcegitcommit: d223616e7e6fe2139079052e6fcbe25413fb9900
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/22/2020
ms.locfileid: "83805151"
---
# <a name="igchost2setgcstartuplimitsex-method"></a><span data-ttu-id="3fa7f-102">Método IGCHost2::SetGCStartupLimitsEx</span><span class="sxs-lookup"><span data-stu-id="3fa7f-102">IGCHost2::SetGCStartupLimitsEx Method</span></span>
<span data-ttu-id="3fa7f-103">Define o tamanho do segmento e o tamanho máximo para a geração 0.</span><span class="sxs-lookup"><span data-stu-id="3fa7f-103">Sets the segment size and the maximum size for generation 0.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3fa7f-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="3fa7f-104">Syntax</span></span>  
  
```cpp  
HRESULT SetGCStartupLimitsEx (  
    [in] SIZE_T SegmentSize,  
    [in] SIZE_T MaxGen0Size  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3fa7f-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="3fa7f-105">Parameters</span></span>  
 `SegmentSize`  
 <span data-ttu-id="3fa7f-106">no O tamanho do segmento usado pelo sistema de coleta de lixo.</span><span class="sxs-lookup"><span data-stu-id="3fa7f-106">[in] The size of the segment used by the garbage collection system.</span></span>  
  
 `MaxGen0Size`  
 <span data-ttu-id="3fa7f-107">no O tamanho máximo para a geração 0.</span><span class="sxs-lookup"><span data-stu-id="3fa7f-107">[in] The maximum size for generation 0.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3fa7f-108">Comentários</span><span class="sxs-lookup"><span data-stu-id="3fa7f-108">Remarks</span></span>  
 <span data-ttu-id="3fa7f-109">Os valores que `SetGCStartupLimitsEx` conjuntos só podem ser especificados antes do host ser iniciado.</span><span class="sxs-lookup"><span data-stu-id="3fa7f-109">The values that `SetGCStartupLimitsEx` sets can be specified only before the host is started.</span></span> <span data-ttu-id="3fa7f-110">Esses valores não podem ser alterados posteriormente.</span><span class="sxs-lookup"><span data-stu-id="3fa7f-110">These values cannot be changed later.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3fa7f-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="3fa7f-111">Requirements</span></span>  
 <span data-ttu-id="3fa7f-112">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3fa7f-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3fa7f-113">**Cabeçalho:** GCHost. idl, GCHost. h</span><span class="sxs-lookup"><span data-stu-id="3fa7f-113">**Header:** GCHost.idl, GCHost.h</span></span>  
  
 <span data-ttu-id="3fa7f-114">**Biblioteca:** Incluído como um recurso em MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="3fa7f-114">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="3fa7f-115">**.NET Framework versões:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3fa7f-115">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3fa7f-116">Confira também</span><span class="sxs-lookup"><span data-stu-id="3fa7f-116">See also</span></span>

- [<span data-ttu-id="3fa7f-117">Interface IGCHost2</span><span class="sxs-lookup"><span data-stu-id="3fa7f-117">IGCHost2 Interface</span></span>](igchost2-interface.md)
