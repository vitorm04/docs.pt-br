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
ms.openlocfilehash: cbe94aa67c9cf9ac587b7fca9f5cbeca4870506b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33437203"
---
# <a name="igchostsetgcstartuplimits-method"></a><span data-ttu-id="d45ea-102">Método IGCHost::SetGCStartupLimits</span><span class="sxs-lookup"><span data-stu-id="d45ea-102">IGCHost::SetGCStartupLimits Method</span></span>
<span data-ttu-id="d45ea-103">Define o tamanho do segmento e o tamanho máximo de geração 0.</span><span class="sxs-lookup"><span data-stu-id="d45ea-103">Sets the segment size and the maximum size for generation 0.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="d45ea-104">Começando com o [!INCLUDE[net_v45](../../../../includes/net-v45-md.md)], você pode definir o tamanho do segmento e o tamanho máximo de geração 0 para valores maior `DWORD` usando o [Igchost2](../../../../docs/framework/unmanaged-api/hosting/igchost2-setgcstartuplimitsex-method.md) método.</span><span class="sxs-lookup"><span data-stu-id="d45ea-104">Starting with the [!INCLUDE[net_v45](../../../../includes/net-v45-md.md)], you can set segment size and maximum generation 0 size to values greater than `DWORD` by using the [IGCHost2::SetGCStartupLimitsEx](../../../../docs/framework/unmanaged-api/hosting/igchost2-setgcstartuplimitsex-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d45ea-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="d45ea-105">Syntax</span></span>  
  
```  
HRESULT SetGCStartupLimits (  
    [in] DWORD SegmentSize,  
    [in] DWORD MaxGen0Size  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="d45ea-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="d45ea-106">Parameters</span></span>  
 `SegmentSize`  
 <span data-ttu-id="d45ea-107">[in] O tamanho do segmento usado pelo sistema de coleta de lixo.</span><span class="sxs-lookup"><span data-stu-id="d45ea-107">[in] The size of the segment used by the garbage collection system.</span></span>  
  
 `MaxGen0Size`  
 <span data-ttu-id="d45ea-108">[in] O tamanho máximo de geração 0.</span><span class="sxs-lookup"><span data-stu-id="d45ea-108">[in] The maximum size for generation 0.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d45ea-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="d45ea-109">Remarks</span></span>  
 <span data-ttu-id="d45ea-110">O `SetGCStartupLimits` método pode ser chamado apenas uma vez.</span><span class="sxs-lookup"><span data-stu-id="d45ea-110">The `SetGCStartupLimits` method may be called only once.</span></span> <span data-ttu-id="d45ea-111">Esses valores não podem ser alterados posteriormente.</span><span class="sxs-lookup"><span data-stu-id="d45ea-111">These values cannot be changed later.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d45ea-112">Requisitos</span><span class="sxs-lookup"><span data-stu-id="d45ea-112">Requirements</span></span>  
 <span data-ttu-id="d45ea-113">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d45ea-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d45ea-114">**Cabeçalho:** GCHost.idl, GCHost.h</span><span class="sxs-lookup"><span data-stu-id="d45ea-114">**Header:** GCHost.idl, GCHost.h</span></span>  
  
 <span data-ttu-id="d45ea-115">**Biblioteca:** incluído como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="d45ea-115">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="d45ea-116">**Versões do .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d45ea-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d45ea-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="d45ea-117">See Also</span></span>  
 [<span data-ttu-id="d45ea-118">Interface IGCHost</span><span class="sxs-lookup"><span data-stu-id="d45ea-118">IGCHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/igchost-interface.md)
