---
title: Método ICorThreadpool::CorGetMaxThreads
ms.date: 03/30/2017
api_name:
- ICorThreadpool.CorGetMaxThreads
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorGetMaxThreads
helpviewer_keywords:
- CorGetMaxThreads method [.NET Framework hosting]
- ICorThreadpool::CorGetMaxThreads method [.NET Framework hosting]
ms.assetid: 2861533a-cda0-47b3-b716-0d363505289b
topic_type:
- apiref
ms.openlocfilehash: c3de2a063030d5169c6ff69e8db72e8be3ae22a3
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73133279"
---
# <a name="icorthreadpoolcorgetmaxthreads-method"></a><span data-ttu-id="d6977-102">Método ICorThreadpool::CorGetMaxThreads</span><span class="sxs-lookup"><span data-stu-id="d6977-102">ICorThreadpool::CorGetMaxThreads Method</span></span>
<span data-ttu-id="d6977-103">Esse método oferece suporte a infraestrutura do .NET Framework e não se destina a ser usado diretamente do seu código.</span><span class="sxs-lookup"><span data-stu-id="d6977-103">This method supports the .NET Framework infrastructure and is not intended to be used directly from your code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d6977-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="d6977-104">Syntax</span></span>  
  
```cpp  
HRESULT CorGetMaxThreads (  
    [out] DWORD *MaxWorkerThreads,  
    [out] DWORD *MaxIOCompletionThreads  
);  
```  
  
## <a name="requirements"></a><span data-ttu-id="d6977-105">Requisitos</span><span class="sxs-lookup"><span data-stu-id="d6977-105">Requirements</span></span>  
 <span data-ttu-id="d6977-106">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d6977-106">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d6977-107">**Cabeçalho:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="d6977-107">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="d6977-108">**Biblioteca:** Incluído como um recurso em MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="d6977-108">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="d6977-109">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d6977-109">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d6977-110">Consulte também</span><span class="sxs-lookup"><span data-stu-id="d6977-110">See also</span></span>

- [<span data-ttu-id="d6977-111">Interface ICorThreadpool</span><span class="sxs-lookup"><span data-stu-id="d6977-111">ICorThreadpool Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorthreadpool-interface.md)
