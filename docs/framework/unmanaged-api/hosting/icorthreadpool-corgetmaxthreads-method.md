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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 33cbbf5d9be682b82b7e21034b1db206f0ba4ec5
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54646182"
---
# <a name="icorthreadpoolcorgetmaxthreads-method"></a><span data-ttu-id="05a17-102">Método ICorThreadpool::CorGetMaxThreads</span><span class="sxs-lookup"><span data-stu-id="05a17-102">ICorThreadpool::CorGetMaxThreads Method</span></span>
<span data-ttu-id="05a17-103">Esse método oferece suporte a infraestrutura do .NET Framework e não se destina a ser usado diretamente do seu código.</span><span class="sxs-lookup"><span data-stu-id="05a17-103">This method supports the .NET Framework infrastructure and is not intended to be used directly from your code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="05a17-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="05a17-104">Syntax</span></span>  
  
```  
HRESULT CorGetMaxThreads (  
    [out] DWORD *MaxWorkerThreads,  
    [out] DWORD *MaxIOCompletionThreads  
);  
```  
  
## <a name="requirements"></a><span data-ttu-id="05a17-105">Requisitos</span><span class="sxs-lookup"><span data-stu-id="05a17-105">Requirements</span></span>  
 <span data-ttu-id="05a17-106">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="05a17-106">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="05a17-107">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="05a17-107">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="05a17-108">**Biblioteca:** Incluído como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="05a17-108">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="05a17-109">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="05a17-109">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="05a17-110">Consulte também</span><span class="sxs-lookup"><span data-stu-id="05a17-110">See also</span></span>
- [<span data-ttu-id="05a17-111">Interface ICorThreadpool</span><span class="sxs-lookup"><span data-stu-id="05a17-111">ICorThreadpool Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorthreadpool-interface.md)
