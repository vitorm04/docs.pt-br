---
title: "Método IGCHost::SetVirtualMemLimit"
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
- IGCHost.SetVirtualMemLimit
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- SetVirtualMemLimit
helpviewer_keywords:
- IGCHost::SetVirtualMemLimit method [.NET Framework hosting]
- SetVirtualMemLimit method [.NET Framework hosting]
ms.assetid: c7e7c2d0-e58c-4650-b40c-47b2be2cda45
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 5fca9ee8473ed70ca5da3b5607d38f4123fd47e2
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="igchostsetvirtualmemlimit-method"></a><span data-ttu-id="bd131-102">Método IGCHost::SetVirtualMemLimit</span><span class="sxs-lookup"><span data-stu-id="bd131-102">IGCHost::SetVirtualMemLimit Method</span></span>
<span data-ttu-id="bd131-103">Define o tamanho máximo de memória virtual do tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="bd131-103">Sets the maximum size of the runtime's virtual memory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bd131-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="bd131-104">Syntax</span></span>  
  
```  
HRESULT SetVirtualMemLimit (  
    [in] SIZE_T sztMaxVirtualMemMB  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="bd131-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="bd131-105">Parameters</span></span>  
 `sztMaxVirtualMemMB`  
 <span data-ttu-id="bd131-106">[in] O tamanho máximo, em megabytes, da memória virtual do tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="bd131-106">[in] The maximum size, in megabytes, of the runtime's virtual memory.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="bd131-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="bd131-107">Remarks</span></span>  
 <span data-ttu-id="bd131-108">O tamanho máximo de memória virtual do tempo de execução pode ser alterado dinamicamente.</span><span class="sxs-lookup"><span data-stu-id="bd131-108">The maximum size of the runtime's virtual memory can be changed dynamically.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bd131-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="bd131-109">Requirements</span></span>  
 <span data-ttu-id="bd131-110">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bd131-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bd131-111">**Cabeçalho:** GCHost.idl, GCHost.h</span><span class="sxs-lookup"><span data-stu-id="bd131-111">**Header:** GCHost.idl, GCHost.h</span></span>  
  
 <span data-ttu-id="bd131-112">**Biblioteca:** incluído como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="bd131-112">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="bd131-113">**Versões do .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bd131-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bd131-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="bd131-114">See Also</span></span>  
 [<span data-ttu-id="bd131-115">Interface IGCHost</span><span class="sxs-lookup"><span data-stu-id="bd131-115">IGCHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/igchost-interface.md)
