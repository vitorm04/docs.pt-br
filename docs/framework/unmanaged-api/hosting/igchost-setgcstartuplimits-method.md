---
title: Método IGCHost::SetGCStartupLimits
ms.date: 03/30/2017
api_name:
- IGCHost.SetGCStartupLimits
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- SetGCStartupLimits
helpviewer_keywords:
- SetGCStartupLimits method, IGCHost interface [.NET Framework hosting]
- IGCHost::SetGCStartupLimits method [.NET Framework hosting]
ms.assetid: cae53926-82ac-4d1d-b297-0bde0bd1bebb
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e65a83d1da0580436babd15e4f27e2db7a698668
ms.sourcegitcommit: 4735bb7741555bcb870d7b42964d3774f4897a6e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/30/2019
ms.locfileid: "66377606"
---
# <a name="igchostsetgcstartuplimits-method"></a><span data-ttu-id="8addf-102">Método IGCHost::SetGCStartupLimits</span><span class="sxs-lookup"><span data-stu-id="8addf-102">IGCHost::SetGCStartupLimits Method</span></span>
<span data-ttu-id="8addf-103">Define o tamanho do segmento e o tamanho máximo para a geração 0.</span><span class="sxs-lookup"><span data-stu-id="8addf-103">Sets the segment size and the maximum size for generation 0.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="8addf-104">Começando com o .NET Framework 4.5, você pode definir tamanho do segmento e o tamanho máximo de geração 0 para valores maior `DWORD` usando o [IGCHost2::SetGCStartupLimitsEx](../../../../docs/framework/unmanaged-api/hosting/igchost2-setgcstartuplimitsex-method.md) método.</span><span class="sxs-lookup"><span data-stu-id="8addf-104">Starting with the .NET Framework 4.5, you can set segment size and maximum generation 0 size to values greater than `DWORD` by using the [IGCHost2::SetGCStartupLimitsEx](../../../../docs/framework/unmanaged-api/hosting/igchost2-setgcstartuplimitsex-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8addf-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="8addf-105">Syntax</span></span>  
  
```  
HRESULT SetGCStartupLimits (  
    [in] DWORD SegmentSize,  
    [in] DWORD MaxGen0Size  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8addf-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="8addf-106">Parameters</span></span>  
 `SegmentSize`  
 <span data-ttu-id="8addf-107">[in] O tamanho do segmento usado pelo sistema de coleta de lixo.</span><span class="sxs-lookup"><span data-stu-id="8addf-107">[in] The size of the segment used by the garbage collection system.</span></span>  
  
 `MaxGen0Size`  
 <span data-ttu-id="8addf-108">[in] O tamanho máximo para a geração 0.</span><span class="sxs-lookup"><span data-stu-id="8addf-108">[in] The maximum size for generation 0.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8addf-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="8addf-109">Remarks</span></span>  
 <span data-ttu-id="8addf-110">O `SetGCStartupLimits` método pode ser chamado apenas uma vez.</span><span class="sxs-lookup"><span data-stu-id="8addf-110">The `SetGCStartupLimits` method may be called only once.</span></span> <span data-ttu-id="8addf-111">Esses valores não podem ser alterados posteriormente.</span><span class="sxs-lookup"><span data-stu-id="8addf-111">These values cannot be changed later.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8addf-112">Requisitos</span><span class="sxs-lookup"><span data-stu-id="8addf-112">Requirements</span></span>  
 <span data-ttu-id="8addf-113">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8addf-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8addf-114">**Cabeçalho:** GCHost.idl, GCHost.h</span><span class="sxs-lookup"><span data-stu-id="8addf-114">**Header:** GCHost.idl, GCHost.h</span></span>  
  
 <span data-ttu-id="8addf-115">**Biblioteca:** Incluído como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="8addf-115">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="8addf-116">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8addf-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8addf-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="8addf-117">See also</span></span>

- [<span data-ttu-id="8addf-118">Interface IGCHost</span><span class="sxs-lookup"><span data-stu-id="8addf-118">IGCHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/igchost-interface.md)
