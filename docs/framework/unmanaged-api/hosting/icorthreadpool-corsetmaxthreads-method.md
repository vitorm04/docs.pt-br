---
title: Método ICorThreadpool::CorSetMaxThreads
ms.date: 03/30/2017
api_name:
- ICorThreadpool.CorSetMaxThreads
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorSetMaxThreads
helpviewer_keywords:
- ICorThreadpool::CorSetMaxThreads method [.NET Framework hosting]
- CorSetMaxThreads method [.NET Framework hosting]
ms.assetid: 4a846238-df4e-4060-ba3b-5173f6a51e85
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6c7cb97acbf089221f498ce9edcafb114ddeef27
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54496892"
---
# <a name="icorthreadpoolcorsetmaxthreads-method"></a><span data-ttu-id="fede0-102">Método ICorThreadpool::CorSetMaxThreads</span><span class="sxs-lookup"><span data-stu-id="fede0-102">ICorThreadpool::CorSetMaxThreads Method</span></span>
<span data-ttu-id="fede0-103">Esse método oferece suporte a infraestrutura do .NET Framework e não se destina a ser usado diretamente do seu código.</span><span class="sxs-lookup"><span data-stu-id="fede0-103">This method supports the .NET Framework infrastructure and is not intended to be used directly from your code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fede0-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="fede0-104">Syntax</span></span>  
  
```  
HRESULT CorSetMaxThreads (  
    [in] DWORD MaxWorkerThreads,  
    [in] DWORD MaxIOCompletionThreads  
);  
```  
  
## <a name="requirements"></a><span data-ttu-id="fede0-105">Requisitos</span><span class="sxs-lookup"><span data-stu-id="fede0-105">Requirements</span></span>  
 <span data-ttu-id="fede0-106">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fede0-106">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fede0-107">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="fede0-107">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="fede0-108">**Biblioteca:** Incluído como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="fede0-108">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="fede0-109">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fede0-109">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fede0-110">Consulte também</span><span class="sxs-lookup"><span data-stu-id="fede0-110">See also</span></span>
- [<span data-ttu-id="fede0-111">Interface ICorThreadpool</span><span class="sxs-lookup"><span data-stu-id="fede0-111">ICorThreadpool Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorthreadpool-interface.md)
