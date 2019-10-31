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
ms.openlocfilehash: 40da8e67c705378c9e44398f6a0f519296da03e4
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73133270"
---
# <a name="icorthreadpoolcorgetavailablethreads-method"></a><span data-ttu-id="4ee3e-102">Método ICorThreadpool::CorGetAvailableThreads</span><span class="sxs-lookup"><span data-stu-id="4ee3e-102">ICorThreadpool::CorGetAvailableThreads Method</span></span>
<span data-ttu-id="4ee3e-103">Esse método oferece suporte a infraestrutura do .NET Framework e não se destina a ser usado diretamente do seu código.</span><span class="sxs-lookup"><span data-stu-id="4ee3e-103">This method supports the .NET Framework infrastructure and is not intended to be used directly from your code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4ee3e-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="4ee3e-104">Syntax</span></span>  
  
```cpp  
HRESULT CorGetAvailableThreads (  
    [out] DWORD *AvailableWorkerThreads,  
    [out] DWORD *AvailableIOCompletionThreads  
);  
```  
  
## <a name="requirements"></a><span data-ttu-id="4ee3e-105">Requisitos</span><span class="sxs-lookup"><span data-stu-id="4ee3e-105">Requirements</span></span>  
 <span data-ttu-id="4ee3e-106">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4ee3e-106">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4ee3e-107">**Cabeçalho:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="4ee3e-107">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="4ee3e-108">**Biblioteca:** Incluído como um recurso em MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="4ee3e-108">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="4ee3e-109">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4ee3e-109">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4ee3e-110">Consulte também</span><span class="sxs-lookup"><span data-stu-id="4ee3e-110">See also</span></span>

- [<span data-ttu-id="4ee3e-111">Interface ICorThreadpool</span><span class="sxs-lookup"><span data-stu-id="4ee3e-111">ICorThreadpool Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorthreadpool-interface.md)
