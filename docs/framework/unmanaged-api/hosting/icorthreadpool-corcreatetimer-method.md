---
title: "Método ICorThreadpool::CorCreateTimer"
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
- ICorThreadpool.CorCreateTimer
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorCreateTimer
helpviewer_keywords:
- CorCreateTimer method [.NET Framework hosting]
- ICorThreadpool::CorCreateTimer method [.NET Framework hosting]
ms.assetid: 0d56ef25-30f1-4499-8a1f-76e7654ec614
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: e7a427396158fda7d387eecbeff58e6c1ef591dd
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="icorthreadpoolcorcreatetimer-method"></a><span data-ttu-id="6b349-102">Método ICorThreadpool::CorCreateTimer</span><span class="sxs-lookup"><span data-stu-id="6b349-102">ICorThreadpool::CorCreateTimer Method</span></span>
<span data-ttu-id="6b349-103">Esse método oferece suporte a infraestrutura do .NET Framework e não se destina a ser usado diretamente do seu código.</span><span class="sxs-lookup"><span data-stu-id="6b349-103">This method supports the .NET Framework infrastructure and is not intended to be used directly from your code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6b349-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="6b349-104">Syntax</span></span>  
  
```  
HRESULT CorCreateTimer (  
    [in]  HANDLE*             phNewTimer,  
    [in]  WAITORTIMERCALLBACK Callback,  
    [in]  PVOID               Parameter,  
    [in]  DWORD               DueTime,  
    [in]  DWORD               Period,  
    [out] BOOL*               result  
);  
```  
  
## <a name="requirements"></a><span data-ttu-id="6b349-105">Requisitos</span><span class="sxs-lookup"><span data-stu-id="6b349-105">Requirements</span></span>  
 <span data-ttu-id="6b349-106">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6b349-106">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6b349-107">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="6b349-107">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="6b349-108">**Biblioteca:** incluído como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="6b349-108">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="6b349-109">**Versões do .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6b349-109">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6b349-110">Consulte também</span><span class="sxs-lookup"><span data-stu-id="6b349-110">See Also</span></span>  
 [<span data-ttu-id="6b349-111">Interface ICorThreadpool</span><span class="sxs-lookup"><span data-stu-id="6b349-111">ICorThreadpool Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorthreadpool-interface.md)
