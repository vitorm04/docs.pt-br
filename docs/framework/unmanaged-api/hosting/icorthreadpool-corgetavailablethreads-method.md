---
title: Método ICorThreadpool::CorGetAvailableThreads
ms.date: 03/30/2017
api_name:
- ICorThreadpool.CorGetAvailableThreads
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorGetAvailableThreads
helpviewer_keywords:
- CorGetAvailableThreads method [.NET Framework hosting]
- ICorThreadpool::CorGetAvailableThreads method [.NET Framework hosting]
ms.assetid: 0b09b750-0b86-4ba4-9621-041857cfe8ba
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 0c929b9434507ea7cce936767f2ac72ff98fda7b
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59215788"
---
# <a name="icorthreadpoolcorgetavailablethreads-method"></a><span data-ttu-id="c28cf-102">Método ICorThreadpool::CorGetAvailableThreads</span><span class="sxs-lookup"><span data-stu-id="c28cf-102">ICorThreadpool::CorGetAvailableThreads Method</span></span>
<span data-ttu-id="c28cf-103">Esse método oferece suporte a infraestrutura do .NET Framework e não se destina a ser usado diretamente do seu código.</span><span class="sxs-lookup"><span data-stu-id="c28cf-103">This method supports the .NET Framework infrastructure and is not intended to be used directly from your code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c28cf-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="c28cf-104">Syntax</span></span>  
  
```  
HRESULT CorGetAvailableThreads (  
    [out] DWORD *AvailableWorkerThreads,  
    [out] DWORD *AvailableIOCompletionThreads  
);  
```  
  
## <a name="requirements"></a><span data-ttu-id="c28cf-105">Requisitos</span><span class="sxs-lookup"><span data-stu-id="c28cf-105">Requirements</span></span>  
 <span data-ttu-id="c28cf-106">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c28cf-106">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c28cf-107">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="c28cf-107">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="c28cf-108">**Biblioteca:** Incluído como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="c28cf-108">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 **<span data-ttu-id="c28cf-109">Versões do .NET Framework:</span><span class="sxs-lookup"><span data-stu-id="c28cf-109">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="c28cf-110">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c28cf-110">See also</span></span>

- [<span data-ttu-id="c28cf-111">Interface ICorThreadpool</span><span class="sxs-lookup"><span data-stu-id="c28cf-111">ICorThreadpool Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorthreadpool-interface.md)
